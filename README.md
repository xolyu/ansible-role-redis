# redis

<!-- [![CI](https://github.com/xolyu/ansible-role-redis/actions/workflows/ci.yml/badge.svg)](https://github.com/xolyu/ansible-role-redis/actions/workflows/ci.yml) -->

Installs Redis and configures a named instance.


## Requirements

None.


## Dependencies

None.


## Role Variables

* **`redis_main_instance`**  
  Configures the operation of state and activation of the Redis main instance.  
  `noop` means that the main instance's service is not touched, `disabled` forces the service is stopped and disabled, `disabled_if_instance` disables the main instance if a named instance is configured otherwise uses `redis_enabled` and `redis_state` for the main instance.  
  Choices: `noop`, `disabled`, `disabled_if_instance`  
  Default: `disabled_if_instance`

* **`redis_instance`**  
  Name of the named Redis instance. This name is used e.g. in path of the socket and pid file.  
  An undefined value means that no named instance is configured.  
  Type: str  
  Default: _undefined_

* **`redis_enabled`**  
  Defines the activation of the named Redis instance if defined, otherwise of the main instance.  
  Type: bool  
  Default: `yes`

* **`redis_state`**  
  Defines the state of the named Redis instance if defined, otherwise of the main instance.  
  Choices: `started`, `stopped`  
  Default: `started`

* **`redis_instance_config_defaults`**  
  Predefined defaults for the named Redis instance.  
  Type: dict  
  Default: _see defaults/main.yml_

* **`redis_instance_config`**  
  Config options for the named Redis instance.  
  Type: dict  
  Default: `{}`

  Dict configuration of an instance
  * the key is printed as directive name
  * the directive with the key is printed multiple times for every entry if the value is a list
  * special keys (stating with `$`)
    * `$include_base`: includes the Redis base config at the beginning of a named config (Type: bool; Default: `yes`)
    * `$state`: the named instance will be deleted if is `absent`, otherwise the named config is created (Default: `present`)
    * `$include_begin`: includes before the directives, but after include of base config (Type: list)
    * `$include_end`: includes after the directives (Type: list)

<!--
* **`VAR`**  
  DESC  
  Type: bool/str/dict/list/list of str/list of dicts/dict of dict  
  Default: `VAL`

* **`VAR`**  
  DESC  
  Choices: `VAL`, `ANOTHER`  
  Default: `VAL`
-->


## Example Playbook

Examples of playbooks using and configuring the role.


## License

GNU General Public License v3.0


## Author Information

Xolyu.
