---
title: "Samba daemon not starting on &quot;apt upgrade&quot; on 18.04"
date: 2018-08-17
forum: Installation &amp; Upgrades
---

### Post by johnaaronrose on 2018-08-17
I've done a 'clean' install of 18.04. On 'apt upgrade' (whether or not there are packages to upgrade/install) or 'apt install' for any package:
 ```
root@JohnPC:/home/john# apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-08-17 08:13:54 BST; 27ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 28404 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 28404 (code=exited, status=1/FAILURE)


Aug 17 08:13:54 JohnPC systemd[1]: Starting Samba SMB Daemon...
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Failed with result 'exit-code'.
Aug 17 08:13:54 JohnPC systemd[1]: Failed to start Samba SMB Daemon.
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
```
root@JohnPC:/home/john# systemctl status smbd.service
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-08-17 08:13:54 BST; 43s ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 28404 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, st
 Main PID: 28404 (code=exited, status=1/FAILURE)


Aug 17 08:13:54 JohnPC systemd[1]: Starting Samba SMB Daemon...
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Failed with result 'exit-code'.
Aug 17 08:13:54 JohnPC systemd[1]: Failed to start Samba SMB Daemon.
```

---

### Post by Morbius1 on 2018-08-18
AskUbuntu doesn't like a lot of chatter ( comments ) so I will try to answer some of your questions here:

> Directory /etc/samba is empty: therefore no  /usr/share/smb.conf. Could this be due to my 'apt purge samba' followed  by 'apt install samba'
It may have because smb.conf doesn't come from the "samba" package it comes from the samba-common package.
> I have 3 files (smb.conf, gdbcommands and  smbusers) in /etc/samba on a Ubuntu 16.04 PC. So would it be a good idea  to copy them over to my 18.04 machine?
You can but gdbcommands is used by samba itself to report a samba crash. You could run a samba server for a decade and nothing will ever be added to that file. Unless you added it yourself smbusers is added when you use the system-config-samba application in 16.04. system-config-samba no longer works in 18.04 so you can forget about it.
> 'testparm -s' gave: Load smb config files  from /etc/samba/smb.conf rlimit_max: increasing rlimit_max (1024) to  minimum Windows limit (16384) WARNING: The "syslog" option is deprecated  Processing section "[printers]" Processing section "[print$]" Loaded  services file OK. Server role: ROLE_STANDALONE plus a number of  parameter values
That looks like it should.
I did not understand you last comment at AskUbuntu so I'm not sure if everything is OK now or not.

---

### Post by johnaaronrose on 2018-08-18
@Morbius1

Thanks for your answer & informative help.I dislike using AskUbuntu due to the way it limits the size of comments e.g. when posting Terminal output. The 'funny' on[COLOR=#242729][FONT=Arial] 'apt upgrade' went away after I did it again. Below is the relevant part of the output that came out on the first time for it:

[/FONT][/COLOR]> Calculating upgrade... Done0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
2 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Created symlink /etc/systemd/system/multi-user.target.wants/nmbd.service &#8594; /lib/systemd/system/nmbd.service.
Failed to preset unit: Unit file /etc/systemd/system/samba-ad-dc.service is masked.
/usr/bin/deb-systemd-helper: error: systemctl preset failed on samba-ad-dc.service: No such file or directory
Created symlink /etc/systemd/system/multi-user.target.wants/smbd.service &#8594; /lib/systemd/system/smbd.service.
Setting up system-config-samba (1.2.63-0ubuntu6) ...
Processing triggers for libc-bin (2.27-3ubuntu1) ...
W: APT had planned for dpkg to do more than it reported back (3 vs 7).
   Affected packages: samba:amd64


Interestingly. it says that system-config-samba is being setup. I used to find it useful for sharing a printer attached to another PC on the LAN. As you say, it does not work in 18.04 as I get:
> Gtk-Message: 15:30:33.059: Failed to load module "canberra-gtk-module"
Traceback (most recent call last):
  File "/usr/sbin/system-config-samba", line 45, in <module>
    mainWindow.MainWindow(debug_flag)
  File "/usr/share/system-config-samba/mainWindow.py", line 121, in __init__
    self.basic_preferences_win = basicPreferencesWin.BasicPreferencesWin(self, self.xml, self.samba_data, self.samba_backend, self.main_window)
  File "/usr/share/system-config-samba/basicPreferencesWin.py", line 97, in __init__
    self.admin = libuser.admin()
SystemError: could not open configuration file `/etc/libuser.conf': No such file or directory



At the moment I rather regret going to 18.04 from 16.04 on one PC. I'm very unsure whether to wait for the 18.04.2 release before upgrading to 18.04 on my other 2 PCs. When I tried to upgrade from 16.04 to 18.04, it came up with a message about a file being changed with options of Keep, Discard, Show difference (may be slightly wrong in options as memory not what it was). I selected Show difference, and it 'left' the update and would not reboot. So I had to do a 'clean install of 18.04. A really annoying glitch in 18.04 is that it locks the screen very quickly after 'leaving' the PC even if I set the Lock time to 30 minutes or 1 hour. I also don't like it seemingly no longer having the facility to display the Login user on the screen's top right. What are your top gripes in 18.04?

---

### Post by Morbius1 on 2018-08-18
There are 2 ... um ... 3 problems with system-config-samba:

** The first one is easy to fix - add the file that it can't find - it will be blank but it doesn't matter:
```
sudo touch /etc/libuser.conf
```
** The second problem is that it uses gksu to launch the application but there is no gksu in 18.04. That can also be fixed but since you really don't use it on a daily basis I would suggest you just open it from the terminal with a:
```
sudo -H system-config-samba
```
** The third problem is that system-config-samba's days are numbered: [https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1740419](https://bugs.launchpad.net/ubuntu/+source/system-config-samba/+bug/1740419)

---

### Post by twakuu on 2019-03-05
> **johnaaronrose said:**
> I've done a 'clean' install of 18.04. On 'apt upgrade' (whether or not there are packages to upgrade/install) or 'apt install' for any package:
 root@JohnPC:/home/john# apt upgradeReading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.2) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-08-17 08:13:54 BST; 27ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 28404 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, status=1/FAILURE)
 Main PID: 28404 (code=exited, status=1/FAILURE)


Aug 17 08:13:54 JohnPC systemd[1]: Starting Samba SMB Daemon...
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Failed with result 'exit-code'.
Aug 17 08:13:54 JohnPC systemd[1]: Failed to start Samba SMB Daemon.
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@JohnPC:/home/john# systemctl status smbd.service
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: failed (Result: exit-code) since Fri 2018-08-17 08:13:54 BST; 43s ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 28404 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS (code=exited, st
 Main PID: 28404 (code=exited, status=1/FAILURE)


Aug 17 08:13:54 JohnPC systemd[1]: Starting Samba SMB Daemon...
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Aug 17 08:13:54 JohnPC systemd[1]: smbd.service: Failed with result 'exit-code'.
Aug 17 08:13:54 JohnPC systemd[1]: Failed to start Samba SMB Daemon.

[SIZE=2][FONT=arial]This reason this error is occurring is because there are more background services utilizing samba's configuration.

To remove this error, Try This:

sudo systemctl stop nmbd
sudo systemctl disable nmbd

Then run: 

sudo apt-get install --reinstall samba-libs:amd64
[/FONT][FONT=arial]
[/FONT][/SIZE][FONT=arial][SIZE=2]amd64 is your processor architecture (armhf for RBP).

Apt should be good to go from there.

:guitar:-giga[/SIZE][/FONT]

---

