---
title: "cloud-init not configuring network-config file in datasource"
date: 2024-07-27
forum: Installation &amp; Upgrades
---

### Post by dj10023 on 2024-07-27
Running cloud-init: /usr/bin/cloud-init 22.4.2  on a Debian 12 instance.  The user-data processes fine, but it does not apply the network-config. 

I have run through the debug process and check the schema:


```
root@Deb99990:/mnt# cloud-init schema -c user-data --annotate
Valid cloud-config: user-data




root@Deb99990:/mnt# cloud-init schema -c network-config --annotate
Valid cloud-config: network-config

```
The cloud-init.log file is blank each run, so making it fun to try and troubleshoot.

root@Deb99990:~# cat /var/log/cloud-init.log
root@Deb99990:~#

More output:

```
root@Deb99990:~# systemctl status cloud-init-local.service cloud-init.service\
>    cloud-config.service cloud-final.service
× cloud-init-local.service - Initial cloud-init job (pre-networking)
     Loaded: loaded (/lib/systemd/system/cloud-init-local.service; enabled; preset: enabled)
     Active: failed (Result: exit-code) since Sat 2024-07-27 09:23:21 EDT; 7min ago
   Main PID: 248 (code=exited, status=1/FAILURE)
        CPU: 439ms


Jul 27 09:23:21 Deb99990 cloud-init[248]:                                           ~~~~~~^^^^^^^^^^
Jul 27 09:23:21 Deb99990 cloud-init[248]: KeyError: 'prefix'
Jul 27 09:23:21 Deb99990 cloud-init[248]: ------------------------------------------------------------
Jul 27 09:23:21 Deb99990 cloud-init[248]: 2024-07-27 13:23:21,533 - atomic_helper.py[DEBUG]: Atomically writing to file>Jul 27 09:23:21 Deb99990 cloud-init[248]: 2024-07-27 13:23:21,534 - util.py[DEBUG]: Reading from /proc/uptime (quiet=Fa>Jul 27 09:23:21 Deb99990 cloud-init[248]: 2024-07-27 13:23:21,534 - util.py[DEBUG]: Read 10 bytes from /proc/uptime
Jul 27 09:23:21 Deb99990 cloud-init[248]: 2024-07-27 13:23:21,534 - util.py[DEBUG]: cloud-init mode 'init' took 0.930 s>Jul 27 09:23:21 Deb99990 cloud-init[248]: 2024-07-27 13:23:21,534 - handlers.py[DEBUG]: finish: init-local: SUCCESS: se>Jul 27 09:23:21 Deb99990 systemd[1]: cloud-init-local.service: Failed with result 'exit-code'.
Jul 27 09:23:21 Deb99990 systemd[1]: Failed to start cloud-init-local.service - Initial cloud-init job (pre-networking).

```


I have tested the same configs in lxd containers and they run fine.  I have checked the files in the datasource and all checkout fine with "cloud-init schema -c <config> --annotate

Status output:
```
root@Deb99990:~# cloud-init status --long
status: error
boot_status_code: enabled-by-generator
last_update: Sat, 27 Jul 2024 13:23:29 +0000
detail:
'prefix'

```


Anyone else run into this? and know the fix?  I am not finding any of the files that would disable networking.  

I have allso copied the network-config file into /etc/cloud/cloud.cfg.d/ with a .cfg extension and it still does not run. 

What I ran:  cloud-init clean --logs --reboot after copying the file to /etc/cloud/cloud.cfg.d/

So nothing I do to try and force feed it the network-config makes it run. 

Open to ideas, this one has me stumped. 

Thanks

---

### Post by dj10023 on 2024-07-27
More output:

```
root@Deb99990:/etc/netplan# cloud-init query --all
{
 "_beta_keys": [
  "subplatform"
 ],
  //....//
  },
  "cloud_config_modules": [
   "snap",
   "ssh-import-id",
   "keyboard",
   "locale",
   "set-passwords",
   "grub-dpkg",
   "apt-pipelining",
   "apt-configure",
   "ntp",
   "timezone",
   "disable-ec2-metadata",
   "runcmd",
   "byobu"
  ],
  "cloud_final_modules": [
   "package-update-upgrade-install",
   "fan",
   "landscape",
   "lxd",
   "write-files-deferred",
   "puppet",
   "chef",
   "mcollective",
   "salt-minion",
   "reset_rmc",
   "refresh_rmc_and_interface",
   "rightscale_userdata",
   "scripts-vendor",
   "scripts-per-once",
   "scripts-per-boot",
   "scripts-per-instance",
   "scripts-user",
   "ssh-authkey-fingerprints",
   "keys-to-console",
   "install-hotplug",
   "phone-home",
   "final-message",
   "power-state-change"
  ],
  "cloud_init_modules": [
   "migrator",
   "seed_random",
   "bootcmd",
   "write-files",
   "growpart",
   "resizefs",
   "disk_setup",
   "mounts",
   "set_hostname",
   "update_hostname",
   "update_etc_hosts",
   "ca-certs",
   "rsyslog",
   "users-groups",
   "ssh"
  ],
  "datasource_list": [
   "NoCloud",
   "None"
  ],
  "def_log_file": "/var/log/cloud-init.log",
  "disable_root": true,
  "log_cfgs": [],
  "network": {
   "config": [
    {
     "name": "enX0",
     "subnets": [
      {
       "address": "192.168.0.122/24",
       "gateway": "192.168.0.1",
       "type": "static"
      },
      {
       "address": [
        "192.168.0.1",
        "192.168.50.50"
       ],
       "search": [
        "example.lan"
       ],
       "type": "nameserver"
      }
     ],
     "type": "physical"
    }
   ],
   "version": 1
  },
```

So it does appear to at least be rendering the network config,  just does not apply it to the instance.

---

### Post by dj10023 on 2024-07-27
This wound up being an issue with the syntax of the network-config on the nocloud source.  Had to dive into the nocloud source and checked the files with: "[COLOR=#000000][FONT=&quot]cloud-init devel schema --config-file network-config" and found my errors. [/FONT][/COLOR]

---

