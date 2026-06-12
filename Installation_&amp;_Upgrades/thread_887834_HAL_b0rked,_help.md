---
title: "HAL b0rked, help"
date: 2008-08-12
forum: Installation &amp; Upgrades
---

### Post by noarc on 2008-08-12
root@col-dhcp33-244-173:~# apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 11 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                       Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for uid 111 for the action org.freedesktop.policykit.read with constraint '' already exists
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 update-notifier

---

### Post by Partyboi2 on 2008-08-12
try reinstalling dbus
```
sudo aptitude reinstall dbus
```

---

### Post by noarc on 2008-08-13
Thanks for the tip Partyboi2.

Unfortunately, I don't have aptitude installed, and I can't install it while apt-get is stuck. However, I think this command is equivalent, and it's not helping:


```
$ apt-get --reinstall install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 11 not upgraded.
2 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? Y
Setting up hal (0.5.11~rc2-1ubuntu8.2) ...
 * Reloading system message bus config...                                       Failed to open connection to system message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory
invoke-rc.d: initscript dbus, action "force-reload" failed.
polkit-auth: This operation requires the system message bus and ConsoleKit to be running
polkit-auth: AuthorizationAlreadyExists: An authorization for uid 111 for the action org.freedesktop.policykit.read with constraint '' already exists
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of update-notifier:
 update-notifier depends on hal; however:
  Package hal is not configured yet.
dpkg: error processing update-notifier (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 hal
 update-notifier
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

