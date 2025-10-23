🤖 RHCE Ansible Project (EX294 Prep)

Repositório de Automação para Certificação Red Hat Certified Engineer

Este repositório contém todos os Playbooks, Roles e configurações de Inventário desenvolvidos como material de estudo e prática para o exame Red Hat Certified Engineer (RHCE - EX294), com foco em automação de tarefas de administração de sistemas usando o Red Hat Ansible Engine.

🔗 Link do Repositório

https://github.com/rpribeiro2022/RHCE_ANSIBLE_PROJECT.git

🎯 Objetivo

O objetivo principal deste projeto é demonstrar proficiência nas áreas de automação exigidas pelo exame RHCE, incluindo:

    Compreensão dos Componentes Core do Ansible: Inventários, Módulos, Variáveis, Facts, Plays e Playbooks.

    Configuração do Nó de Controle (Control Node): Instalação, ansible.cfg, e gerenciamento de inventário.

    Criação de Plays e Playbooks: Uso de módulos comuns (yum, copy, systemd, debug, firewalld, user, filesystem, etc.), manipulação de variáveis, condicionais e tratamento de erros.

    Utilização de Roles e Collections: Estruturação de Playbooks complexos usando a metodologia Role.

    Proteção de Dados Sensíveis: Uso do Ansible Vault.

🛠 Pré-requisitos e Setup do Ambiente

Para replicar este ambiente de estudo:

    Sistema Operacional: Red Hat Enterprise Linux (RHEL) 8 ou 9 (Recomendado).

    Control Node: Ansible instalado (ansible-core ou ansible-engine).

    Managed Nodes: Uma ou mais VMs RHEL configuradas com:

        Acesso SSH.

        Chave SSH do Control Node distribuída.

        Elevação de privilégios configurada (usuário capaz de usar sudo sem senha ou com senha conhecida).

⚙️ Configuração (Control Node)

    Clone o Repositório:
    Bash

git clone https://github.com/rpribeiro2022/RHCE_ANSIBLE_PROJECT.git
cd RHCE_ANSIBLE_PROJECT

Verifique a Conectividade e o Inventário:
Ajuste o arquivo inventory/hosts.ini para corresponder aos seus hosts de laboratório.

Exemplo de Inventário (inventory/hosts.ini):
Ini, TOML

[servers]
node1 ansible_host=192.168.1.10
node2 ansible_host=192.168.1.11

[control_node]
localhost ansible_connection=local

Teste de Conectividade Ad-Hoc:
Bash

    ansible servers -m ping -i inventory/hosts.ini

🚀 Execução dos Playbooks

Para executar os Playbooks do projeto, utilize o arquivo de configuração e o inventário corretos:

Descrição da Tarefa	Comando de Execução

Executar o Playbook Principal (Orquestração de todas as roles)	ansible-playbook playbooks/main.yml -i inventory/hosts.ini

Executar uma Role Específica (Ex: Configurar Firewall)	ansible-playbook playbooks/main.yml -i inventory/hosts.ini --limit webserver

Usar o Vault (se houver dados sensíveis)	ansible-playbook playbooks/security.yml -i inventory/hosts.ini --ask-vault-pass

Teste de Idempotência/Modo Check	ansible-playbook playbooks/main.yml -i inventory/hosts.ini --check

🔑 Segurança (Ansible Vault)

Todos os dados sensíveis (senhas, chaves de API, etc.) são armazenados de forma criptografada usando o Ansible Vault.

    Arquivo(s) Criptografado(s): secrets/vault_vars.yml (ou similar)

    Comando para Edição: ansible-vault edit secrets/vault_vars.yml

    Observação: A senha do Vault não está neste repositório. Lembre-se de praticar a criação, edição e utilização do Vault, pois este é um tópico frequente no exame RHCE.

📝 Referências do Exame RHCE (EX294)

    Versão do Exame: EX294 (RHEL 8/9 com foco em Ansible Automation).

    Tópicos Chave: Módulos de administração de sistema, uso de ansible.cfg, roles, vault, coleções (Collections), e solução de problemas (troubleshooting).

    Documentação: Consulte a documentação oficial do Ansible e os guias de estudo da Red Hat para detalhes específicos dos módulos e requisitos.

👥 Contribuição

Este é um projeto de estudo individual, mas pull requests ou sugestões de melhoria (especialmente boas práticas de Ansible) são sempre bem-vindas.

Rodolfo Ribeiro rpribeiro2022
