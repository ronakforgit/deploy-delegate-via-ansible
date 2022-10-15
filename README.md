![ansible-harness](https://user-images.githubusercontent.com/21008429/196006970-aa007493-cb3c-449d-a9e0-e908fd7e0936.svg)
# Up and Running Harness Delegate via Ansible in 5 mins
This repository contains Ansible playbooks that'll create Delegate Token and download the Delegate K8S Manifest file by making API calls to Harness NG REST API. You can also use the existing Delegate Token to download the manifest file.

## Requirements 
- ansible-core <= 2.12.0
```bash
pip3 install ansible-core
```

- Create Harness API Key and PAT (Click [here](https://docs.harness.io/article/f0aqiv3td7-api-quickstart#step_1_create_a_harness_api_key_and_pat) for details)

## Dependencies 
- Python 3.9.0 or higher

## Repo Structure
- tasks/
    - create_delegate_token.yml - Creates Delegate Token
    - download_delegate_k8s.yml - Download Delegate K8S Manifest file
- vars/
    - config.yml - Required variables to interact with the Harness NG API endpoint

## Usage
1. Use your favorite editor to open [vars/config.yml](vars/config.yml) and add Harness API PAT, Account Id, Org ID, Project ID, Delegate Token Name & Delegate Name values to respective variables.

2. Time for ***AUTOMATION!!⚡️***. Just run the below command:
```bash
ansible-playbook main.yml
```

The output of successful playbook run:
```
PLAY RECAP **************************************************************************
localhost                  : ok=7    changed=2    unreachable=0    failed=0    skipped=0    rescued=0    ignored=0
```

3. Yayy! _Harness Delegate K8S Manifest_ file is downloaded and available in `manifests/harness-delegate.yml`.

### Additional Details
The playbooks in this repo are designed dynamically so if you don't want to create a new Delegate Token and use the existing one, then all you need is to get the delegate token id from Harness NG UI, add it to `token_name:` variable in [vars/config.yml](vars/config.yml) and run the below command:
```bash
ansible-playbook main.yml --skip-tags delegate_token
```

## License

MIT License. See [COPYING](LICENSE) for more details.

## Author Information
This playbook was created in 2022 by [Ompragash](https://www.linkedin.com/in/ompragash/).
