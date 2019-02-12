@Library('github.com/piyush1594/osio-pipeline@iss_74_2') _

config runtime: 'node'
  
plugins analytics : ["disabled": true, "logLevel": "info"]

plugins foobar : ["verbosity" : true]

osio {

  ci {

    def resources = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources

  }

  cd {

    def resources = processTemplate(params: [
          RELEASE_VERSION: "1.0.${env.BUILD_NUMBER}"
    ])

    build resources: resources

    deploy resources: resources, env: 'stage'

    deploy resources: resources, env: 'run', approval: 'manual'

  }
}
