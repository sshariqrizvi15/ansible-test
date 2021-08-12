pipeline {
    agent { node { label 'master' } }
    parameters {
        string(name: 'your_var1', defaultValue: 'example1', description: '')
        string(name: 'your_var2', defaultValue: 'example2', description: '')
        string(name: 'your_var3', defaultValue: 'example3', description: '')
        choice(name: 'sample_condition', choices: ['role1', 'role2'], description: '')
    }
    stages {
        stage('Checkout Ansible Sample') {
            steps {
                git branch: 'main',
                    url: 'https://github.com/sshariqrizvi15/ansible-test.git'
            }
        }
        stage('Run Ansible') {
            steps {
                ansiblePlaybook( 
                    playbook: 'site.yml',
                    inventory: 'localhost', 
                    colorized:  true,
                    extras: "-e your_var1=${your_var1} -e your_var2=${your_var2}  -e your_var3=${your_var3} -e sample_condition=${sample_condition}")
            }
        }
    }
}
