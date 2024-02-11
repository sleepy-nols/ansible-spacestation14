# ansible-spacestation14
Ansible role to install and configure [Spacestation 14](https://jellyfin.org/) on Debian.

![ansible-lint](https://github.com/sleepy-nols/ansible-spacestation14/actions/workflows/ansible-lint.yml/badge.svg)
![push-galaxy](https://github.com/sleepy-nols/ansible-spacestation14/actions/workflows/ansible-galaxy-push-role.yml/badge.svg)
![Ansible Galaxy](https://img.shields.io/badge/Ansible_Galaxy-sleepy--nols.spacestation14-blue)


---
## Role Variables and Defaults

### General

```yml
ss14_unix_user: "{{ ss14_name }}"
ss14_unix_group: "{{ ss14_name }}"
```
Unix user and group the server runs as.

```yml
ss14_net_port: 1212
ss14_game_hostname: "Foo Station"
ss14_game_description: "Foo Description"
ss14_game_maxplayers: 64
ss14_log_enabled: true
ss14_log_path: "/var/log/ss14"
ss14_admin_log_enabled: true
```
Self explanatory.

```yml
ss14_skip_install_dotnet: false
```
Skip installing the dotnet runtime.

```yml
ss14_net_tickrate: 30
```
Reducing tickrate to 30 is basically unnoticeable but reduces server, client and network load dramatically.

```yml
ss14_game_lobby_enabled: true
```
Enables the lobby instead of straight up throwing clients into a game.

```yml
ss14_auth_mode: 1
```
Enforces authentication so that ALL connecting clients must have a proper account. Otherwise, guest logins are allowed.
Possible values here are: 0 (optional), 1 (required), 2 (disabled)

```yml
ss14_download_url: "https://cdn.centcomm.spacestation14.com/builds/wizards/builds/b59dc2911ca4ffb46e187a31a59cb930b3f1654e/SS14.Server_linux-x64.zip"
```
Url to download the server from. Must be bumped to update to a new version.
https://central.spacestation14.io/builds/wizards/builds.html

---
### Grafana Loki

```yml
ss14_loki_enabled: false
```
Whether to send the server log to Grafana Loki.

```yml
ss14_loki_name: *str*
```
The name of the current server, set as the value of the "Server" label in Loki.

```yml
ss14_loki_address: *str*
```
The address of the Loki server to send to.

```yml
ss14_loki_username: *str*
```
If set, a HTTP Basic auth username to use when talking to Loki.

```yml
ss14_loki_password: *str*
```
If set, a HTTP Basic auth password to use when talking to Loki.

---
## Installing

Install via Ansible Galaxy or clone the Repo
```
ansible-galaxy role install sleepy-nols.spacestation14

git clone git@github.com:sleepy-nols/ansible-spacestation14.git
```
---
## Example Playbook

```yml
- hosts: ss14
  roles:
    - sleepy-nols.spacestation14
```

---
## Contributing

Contributions on are welcome. :)

---
## License
GPLv3
