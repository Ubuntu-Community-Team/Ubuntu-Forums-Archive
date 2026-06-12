---
title: "FAILED - to start Daemon for power management after upgrade reboot"
date: 2016-05-01
forum: Installation &amp; Upgrades
---

### Post by Blake_75 on 2016-05-01
Hi,

as by title after trying without prompts problem to upgrade a laptop Lenovo Essentials B5400 [mod.80B6QB0] from Ubuntu Desktop 15.10 64bit  to  16.04 64bit release (via terminal command), i receive on boot the following exact cyclic attempt to launch the daemon as you can see from attachment. 


```
[FAILED] Failed to start Daemon for power management. See 'systemctl status upower.service' for details.
```


[ATTACH=CONFIG]268746[/ATTACH]


Is there anyone who could help me to identify the reason, following me  through system logs or something else?


I can assure that during upgrade procedure i only consented to remove obsolete packages and to update the configuration files, the two times it asked me.
The setup of upgrade concluded without errors until reboot.

Launching Ubuntu 16.04 64bit in a Live Boot mode i have no problem in loading it correctly, and use it without any lack of functionality or warnings
for an exception when i do a verbose boot, obtaining as follows:

```
Error in parsing PCC subspaces from PCCT
```


- The Installed version of Ubuntu, launched in verbose mode, shows IN ADDITION the indicative line indicative of Fail as follows, and stops the attempt to load EXACTLY in correspodence of the line:

```
[FAILED] Failed to start LSB: this service starts and stops VMware services
See 'systemctl status vmware.service' for details
```

in relation to VMware Workstation Player, which was in 12.1.0 version before upgrading (12.1.1 was released from and probably more compatible to Ubuntu 16.04)



If you need some log or dmesg report, tell me. I can extract them only from a Live version, or from Win10 in other partition in dual boot. So I would need in these case the correct location to find them.

Thanks in advance for any useful contribution in help

---

### Post by Blake_75 on 2016-05-01
Update: 

Uninstalling VMware Workstation Player from recovery console wasn't enough to correct the boot problem

Waiting.

---

