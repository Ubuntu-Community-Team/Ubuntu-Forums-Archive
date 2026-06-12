---
title: "E: Sub-process /usr/bin/dpkg returned an error code (1)"
date: 2017-11-14
forum: Installation &amp; Upgrades
---

### Post by suryaprakashrokz on 2017-11-14
I am getting below error when I perform sudo apt-get upgrade

```
user@virtual-machine:/$ sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  libinput10 python3-cryptography xserver-xorg-core-hwe-16.04 xserver-xorg-hwe-16.04 xserver-xorg-input-evdev-hwe-16.04 xserver-xorg-input-synaptics-hwe-16.04 xserver-xorg-input-wacom-hwe-16.04
  xserver-xorg-video-amdgpu-hwe-16.04 xserver-xorg-video-ati-hwe-16.04 xserver-xorg-video-fbdev-hwe-16.04 xserver-xorg-video-intel-hwe-16.04 xserver-xorg-video-nouveau-hwe-16.04
  xserver-xorg-video-qxl-hwe-16.04 xserver-xorg-video-radeon-hwe-16.04 xserver-xorg-video-vesa-hwe-16.04 xserver-xorg-video-vmware-hwe-16.04
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] Y
Setting up mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Renaming removed key_buffer and myisam-recover options (if present)
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Tue 2017-11-14 00:26:44 PST; 5ms ago
  Process: 15083 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)


Nov 14 00:26:44 cmpeadmin-virtual-machine systemd[1]: Failed to start MySQL Community Server.
Nov 14 00:26:44 cmpeadmin-virtual-machine systemd[1]: mysql.service: Unit entered failed state.
Nov 14 00:26:44 cmpeadmin-virtual-machine systemd[1]: mysql.service: Failed with result 'exit-code'.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
user@virtual-machine:/$

```
Below are some findings:
```
user@virtual-machine:/$ sudo dpkg --configure -a
Setting up mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Renaming removed key_buffer and myisam-recover options (if present)
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Tue 2017-11-14 00:27:54 PST; 5ms ago
  Process: 15313 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)


Nov 14 00:27:54 cmpeadmin-virtual-machine systemd[1]: Failed to start MySQL Community Server.
Nov 14 00:27:54 cmpeadmin-virtual-machine systemd[1]: mysql.service: Unit entered failed state.
Nov 14 00:27:54 cmpeadmin-virtual-machine systemd[1]: mysql.service: Failed with result 'exit-code'.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
```
```
user@virtual-machine:/$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 16 not upgraded.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up mysql-server-5.7 (5.7.20-0ubuntu0.16.04.1) ...
Renaming removed key_buffer and myisam-recover options (if present)
Job for mysql.service failed because the control process exited with error code. See "systemctl status mysql.service" and "journalctl -xe" for details.
invoke-rc.d: initscript mysql, action "start" failed.
&#9679; mysql.service - MySQL Community Server
   Loaded: loaded (/lib/systemd/system/mysql.service; enabled; vendor preset: enabled)
   Active: activating (auto-restart) (Result: exit-code) since Tue 2017-11-14 00:28:22 PST; 5ms ago
  Process: 15516 ExecStartPre=/usr/share/mysql/mysql-systemd-start pre (code=exited, status=1/FAILURE)


Nov 14 00:28:22 cmpeadmin-virtual-machine systemd[1]: Failed to start MySQL Community Server.
Nov 14 00:28:22 cmpeadmin-virtual-machine systemd[1]: mysql.service: Unit entered failed state.
Nov 14 00:28:22 cmpeadmin-virtual-machine systemd[1]: mysql.service: Failed with result 'exit-code'.
dpkg: error processing package mysql-server-5.7 (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mysql-server:
 mysql-server depends on mysql-server-5.7; however:
  Package mysql-server-5.7 is not configured yet.


dpkg: error processing package mysql-server (--configure):
 dependency problems - leaving unconfigured
No apport report written because the error message indicates its a followup error from a previous failure.
                                                                                                          Errors were encountered while processing:
 mysql-server-5.7
 mysql-server
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
user@virtual-machine:/$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 16.04.2 LTS _Xenial Xerus_ - Release amd64 (20170215.2)]/ xenial main restricted


```

---

