pipeline {
    agent any

    stages {
        stage("setup local cluster") {
            steps {
                crc start
                eval $(crc oc-env)
                oc login -u developer https://api.crc.testing:6443
                
            }
        }
        stage("build") {
            steps {
                oc new-app openshift/ruby-23-centos7 --build-env HTTP_PROXY=http://myproxy.net:1337/ --build-env GEM_HOME=~/.gem
            }        
        }
        stage("deploy") {
            steps {
                echo 'Deploying the application'
            }
        }
    }
}
