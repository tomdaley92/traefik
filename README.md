# proxy
Sets up Traefik on our clusters for each environment. This is where all of our TLS certificates are stored.

## Requirements
- Ansible 2.8.1+

## Usage 
1. [Installing external dependencies](#installing-external-dependencies) to update your shared roles.

2. [Updating the stack](#updating-the-stack) (optional, but required for `production` deployments).

## Installing External Dependencies
```bash
ansible-galaxy install -r roles/requirements.yaml -p ./roles --force
```

## Updating the Stack
By default, pushing code to the `development` or `test` branches will automatically re-deploy the stack on the `development` and `certification` environments respectfully, using the latest builds. For safety reasons, we have disabled this for the `release` branch so that **production** is not accidentally updated from an accidental merge. You can manually run the play below to deploy to the **production** by replacing `<env>` with `prod`:
```bash
ansible-playbook deploy.yaml -i inventories/<env>/hosts --vault-id ~/.tokens/master_id
```
