---
title: "cannot upgrade from Ubuntu 18.04 to 20.04.1"
date: 2020-10-20
forum: Installation &amp; Upgrades
---

### Post by lennoxg on 2020-10-20
Tried to upgrade from ubuntu 18.04 to 20.04. 1 via command line and update manager 
Getting the same problem. following are some of my command line input and their responses.

i updated all installed packages using both the update manager and also the following command line commands

[B]sudo apt update
sudo apt list --upgradable
sudo apt upgrade[/B]

I removed all unused old kernels using the following command

**sudo apt --purge autoremove**


I tried reinstalling Update manager core packages using the following command

**sudo apt install update-manager-core**[COLOR=#ff0000]
[/COLOR]

Then i tried upgrading to ubuntu 20.04 using the following command

**sudo do-release-upgrade**

Following are the terminal output after some of the commands

```
**lennoxg@lennoxg-X510UAR:~$ sudo apt --purge autoremove**


Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.20) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: [COLOR=#ff0000]failed [/COLOR](Result: exit-code) since Tue 2020-10-20 15:01:09 AST; 6ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 32591 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS ([COLOR=#ff0000]code=exited, status=1/FAILURE[/COLOR])
 Main PID: 32591 (code=exited, status=1/FAILURE)


Oct 20 15:01:09 lennoxg-X510UAR systemd[1]: Starting Samba SMB Daemon...
Oct 20 15:01:09 lennoxg-X510UAR systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Oct 20 15:01:09 lennoxg-X510UAR systemd[1]: smbd.service: Failed with result 'exit-code'.
Oct 20 15:01:09 lennoxg-X510UAR systemd[1]: [COLOR=#ff0000]Failed to start Samba SMB Daemon.[/COLOR]
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

```
**lennoxg@lennoxg-X510UAR:~$ sudo apt install update-manager-core**


Reading package lists... Done
Building dependency tree       
Reading state information... Done
update-manager-core is already the newest version (1:18.04.11.13).
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.20) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: [COLOR=#ff0000]failed[/COLOR] (Result: exit-code) since Tue 2020-10-20 15:02:01 AST; 5ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 32759 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS ([COLOR=#ff0000]code=exited, status=1/FAILURE[/COLOR])
 Main PID: 32759 (code=exited, status=1/FAILURE)
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


```
**lennoxg@lennoxg-X510UAR:~$ sudo do-release-upgrade**


Checking for a new Ubuntu release
Get:1 Upgrade tool signature [1,554 B]                                         
Get:2 Upgrade tool [1,336 kB]                                                  
Fetched 1,338 kB in 0s (0 B/s)                                                 
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'


Reading cache


Checking package manager
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Hit [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic InRelease                      
Hit [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-updates InRelease              
Hit [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-backports InRelease            
Hit [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-security InRelease             
Hit [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease                       
Hit [http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu](http://ppa.launchpad.net/alexlarsson/flatpak/ubuntu) bionic InRelease       
Hit [http://ppa.launchpad.net/gezakovacs/ppa/ubuntu](http://ppa.launchpad.net/gezakovacs/ppa/ubuntu) bionic InRelease            
Hit [http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu](http://ppa.launchpad.net/nilarimogard/webupd8/ubuntu) bionic InRelease      
Hit [http://ppa.launchpad.net/ondrej/php/ubuntu](http://ppa.launchpad.net/ondrej/php/ubuntu) bionic InRelease                
Hit [http://ppa.launchpad.net/teejee2008/ppa/ubuntu](http://ppa.launchpad.net/teejee2008/ppa/ubuntu) bionic InRelease            
Hit [http://ppa.launchpad.net/tista/adapta/ubuntu](http://ppa.launchpad.net/tista/adapta/ubuntu) bionic InRelease              
Hit [http://ppa.launchpad.net/webupd8team/java/ubuntu](http://ppa.launchpad.net/webupd8team/java/ubuntu) bionic InRelease          
Fetched 0 B in 0s (0 B/s)                                                      
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


Restoring original system state


Aborting
Reading package lists... Done    
Building dependency tree          
Reading state information... Done


**lennoxg@lennoxg-X510UAR:~$ **

```

I am new to linux
I am running a dual boot consisting of windows 10 and ubuntu 18.04 on Asus Vivobook
64Bit OS

Thanks for all the help

---

### Post by grahammechanical on 2020-10-20
You started off correctly by updating/upgrading 18.04. What you need to do now is open Software & Updates>Other Software tab and uncheck those Bionic PPAs. They are pointing to repositories that do not exist in 20.04 (Focal).

The do-release-upgrade command is for server systems and you need to add what is called a switch. It is -d if we are upgrading from 18.04.

or you can follow the instructions in the 20.04 release notes.

[https://wiki.ubuntu.com/FocalFossa/ReleaseNotes](https://wiki.ubuntu.com/FocalFossa/ReleaseNotes)


> To upgrade on a desktop system: 


[LIST]
[*]Open the "Software & Updates" Setting in System Settings. 


[*]Select the 3rd Tab called "Updates". 
[*]Set  the "Notify me of a new Ubuntu version" drop down menu to "For any new  version" if you are using 19.10; set it to "For long-term support  versions" if you are using 18.04 LTS. 
[*]Press Alt+F2 and type update-manager -c into the command box if you are using 19.10; 
type update-manager -c -d if you are using 18.04 LTS. 


[*]Update Manager should open up and tell you that Ubuntu 20.04 LTS is now available. 
[*]Click Upgrade and follow the on-screen instructions.
[/LIST]


Regards

---

### Post by lennoxg on 2020-10-21
Thanks Graham for your response. I will do what you say and get bak to you later today

---

### Post by lennoxg on 2020-10-21
Hi Graham i did what u said but the problem is remains. I did a screen record of what i did with simple screen recorder, but i realize that i cant attach it to this reply as the forum does not support  .mkv files. i would have to copy the print out again and send it to you. will do so later tonight

thanks again

---

### Post by deadflowr on 2020-10-21
Unless something happened recently nothing changed to fix the broken package issue your having with samba.
Run
```
sudo apt update
sudo apt install -f
```
post the results.

Also a similar issue posted here: [https://askubuntu.com/questions/1090856/failed-to-start-samba-smb-daemon-failed-with-result-exit-code]("https://askubuntu.com/questions/1090856/failed-to-start-samba-smb-daemon-failed-with-result-exit-code")

But basically you need to fix that first before any upgrade are possible.

---

### Post by lennoxg on 2020-10-21
Thanks DeadFlowr
Here are the outputs from the two commands

```
**lennoxg@lennoxg-X510UAR:~$ sudo apt update**
[sudo] password for lennoxg: 
Hit:1 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic InRelease                    
Hit:2 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-updates InRelease            
Hit:3 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-backports InRelease
Hit:4 [http://es-mirrors.evowise.com/ubuntu](http://es-mirrors.evowise.com/ubuntu) bionic-security InRelease
Hit:5 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) bionic InRelease
Reading package lists... Done
Building dependency tree       
Reading state information... Done
All packages are up to date.
```


```
**lennoxg@lennoxg-X510UAR:~$ sudo apt install -f**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up samba (2:4.7.6+dfsg~ubuntu-0ubuntu2.20) ...
Samba is not being run as an AD Domain Controller.
Please ignore the following error about deb-systemd-helper not finding samba-ad-dc.service.
Job for smbd.service failed because the control process exited with error code.
See "systemctl status smbd.service" and "journalctl -xe" for details.
invoke-rc.d: initscript smbd, action "restart" failed.
&#9679; smbd.service - Samba SMB Daemon
   Loaded: loaded (/lib/systemd/system/smbd.service; enabled; vendor preset: enabled)
   Active: [COLOR=#ff0000]failed[/COLOR] (Result: exit-code) since Wed 2020-10-21 20:07:06 AST; 25ms ago
     Docs: man:smbd(8)
           man:samba(7)
           man:smb.conf(5)
  Process: 896 ExecStart=/usr/sbin/smbd --foreground --no-process-group $SMBDOPTIONS ([COLOR=#ff0000]code=exited, status=1/FAILURE[/COLOR])
 Main PID: 896 (code=exited, status=1/FAILURE)


Oct 21 20:07:03 lennoxg-X510UAR systemd[1]: Starting Samba SMB Daemon...
Oct 21 20:07:06 lennoxg-X510UAR systemd[1]: smbd.service: Main process exited, code=exited, status=1/FAILURE
Oct 21 20:07:06 lennoxg-X510UAR systemd[1]: smbd.service: Failed with result 'exit-code'.
Oct 21 20:07:06 lennoxg-X510UAR systemd[1]: [COLOR=#ff0000]Failed to start Samba SMB Daemon.[/COLOR]
dpkg: error processing package samba (--configure):
 installed samba package post-installation script subprocess returned error exit status 1
Processing triggers for libc-bin (2.27-3ubuntu1.2) ...
Errors were encountered while processing:
 samba
E: Sub-process /usr/bin/dpkg returned an error code (1)
lennoxg@lennoxg-X510UAR:~$
```

---

### Post by deadflowr on 2020-10-22
What I can gather is samba might have a configuration issue.
run
```
testparm
```
to see what's gong on with it.

---

### Post by lennoxg on 2020-10-23
Deadflowr
I ran testparm 
here are the results

**lennoxg@lennoxg-X510UAR:~$ testparm**


Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "netbios"
Ignoring unknown parameter "netbios"
WARNING: The "syslog" option is deprecated
Processing section "[MYSHARE]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
WARNING: state directory /var/lib/samba should have permissions 0755 for browsing to work


WARNING: cache directory /var/cache/samba should have permissions 0755 for browsing to work


Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
	dns proxy = No
	log file = /var/log/samba/log.%m
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	syslog = 0
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb




[MYSHARE]
	comment = Myshare
	guest ok = Yes
	path = /myshare
	read only = No




[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes




[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
lennoxg@lennoxg-X510UAR:~$

---

### Post by lennoxg on 2020-10-24
Hi Deadflowr

I changed the permission on directory /var/lib/samba to 0755
i also changed the permission on director /var/cache/samba to 0755

i tried the upgrade again but it still did not work

Here are the display of the directories after making the changes

**lennoxg@lennoxg-X510UAR:/var/lib/samba$ ls -l**
total 16
drwxr-xr-x 10 root root          4096 Jul 31  2019 printers
drwxr-xr-x  3 root root          4096 Jan 18  2019 private
drwxr-xr-x  2 root sambashare    4096 Feb 26  2019 usershares
drwxr-xr-x  2 root winbindd_priv 4096 Feb 26  2019 winbindd_privileged
lennoxg@lennoxg-X510UAR:/var/lib/samba$ cd /var/cache/samba
lennoxg@lennoxg-X510UAR:/var/cache/samba$ ls -l
total 40
-rwxr-xr-x 1 root root 40172 Jan 18  2019 gencache.tdb


[B]lennoxg@lennoxg-X510UAR:/var/cache/samba$ cd

[/B]
[B]lennoxg@lennoxg-X510UAR:~$ testparm

[/B]
Load smb config files from /etc/samba/smb.conf
rlimit_max: increasing rlimit_max (1024) to minimum Windows limit (16384)
Unknown parameter encountered: "netbios"
Ignoring unknown parameter "netbios"
WARNING: The "syslog" option is deprecated
Processing section "[MYSHARE]"
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE


Press enter to see a dump of your service definitions


# Global parameters
[global]
	dns proxy = No
	log file = /var/log/samba/log.%m
	map to guest = Bad User
	max log size = 1000
	obey pam restrictions = Yes
	pam password change = Yes
	panic action = /usr/share/samba/panic-action %d
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	passwd program = /usr/bin/passwd %u
	server role = standalone server
	server string = %h server (Samba, Ubuntu)
	syslog = 0
	unix password sync = Yes
	usershare allow guests = Yes
	idmap config * : backend = tdb




[MYSHARE]
	comment = Myshare
	guest ok = Yes
	path = /myshare
	read only = No




[printers]
	browseable = No
	comment = All Printers
	create mask = 0700
	path = /var/spool/samba
	printable = Yes




[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
lennoxg@lennoxg-X510UAR:~$ 


[COLOR=#000000][/COLOR]

---

### Post by lennoxg on 2020-10-25
Is there some bug fix for this.

---

### Post by wolfzrat on 2020-10-29
Hi @lennoxg, 

So just a quick question, you didn't configure samba when you installed 18.04?

Also here a link you can try and see if it helps you.
LINK: [https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today](https://ubuntu.com/blog/how-to-upgrade-from-ubuntu-18-04-lts-to-20-04-lts-today)

Let us know if this helps.

---

### Post by lennoxg on 2020-10-29
Hi Deadflowr

I tried upgrading the system again using the update manager. However the process never gets past the "preparing for upgrade stage"
I then checked the failed logs for the time when the system was attempting the up grade.

[B]cd /var/log
Less syslog

[/B]The following are the failed logs generated during the failed system upgrade


Oct 29 22:16:51 lennoxg-X510UAR canonical-livepatch.canonical-livepatchd[15728]:
 error: timeout waiting for snap system profiles to get updatedOct 29 22:16:52 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-l
ivepatchd.service: Main process exited, code=exited, status=1/FAILUREOct 29 22:16:52 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-l
ivepatchd.service: Failed with result 'exit-code'.Oct 29 22:16:52 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Service hold-off time over, scheduling restart.
Oct 29 22:16:52 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Scheduled restart job, restart counter is at 2.
Oct 29 22:16:52 lennoxg-X510UAR systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
Oct 29 22:16:52 lennoxg-X510UAR systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Oct 29 22:16:59 lennoxg-X510UAR do-release-upgr[17577]: GtkDialog mapped without a transient parent. This is discouraged.
Oct 29 22:17:01 lennoxg-X510UAR CRON[17655]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Oct 29 22:17:04 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager warning: Window 0x3a00003 (do-release) sets an MWM hint indicating it isn't resizable, but sets min size 182 x 215 and max size 2147483647 x 2147483647; this doesn't make much sense.
Oct 29 22:17:04 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager warning: Window 0x3a00003 (do-release) sets an MWM hint indicating it isn't resizable, but sets min size 182 x 215 and max size 2147483647 x 2147483647; this doesn't make much sense.
Oct 29 22:17:49 lennoxg-X510UAR wpa_supplicant[1347]: wlp2s0: WPA: Group rekeying completed with 90:03:25:56:b8:f8 [GTK=TKIP]

My Ubuntu canonical live patch is turned of and the setting says "livepatch is not available for this system"

What do i do next?

---

### Post by deadflowr on 2020-10-30
Yeah, I'm as stuck as you.
You might look at
```
journalctl -xe
```
as suggested in the original error posted.
See if that shows anything of use or value.

---

### Post by lennoxg on 2020-10-30
Here are the results

**lennoxg@lennoxg-X510UAR:~$ journalctl -xe**


Oct 30 14:26:39 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-l
Oct 30 14:26:39 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-l
-- Subject: Automatic restarting of a unit has been scheduled
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Automatic restarting of the unit snap.canonical-livepatch.canonical-livepatch
-- the configured Restart= setting for the unit.
Oct 30 14:26:39 lennoxg-X510UAR systemd[1]: Stopped Service for snap application
-- Subject: Unit snap.canonical-livepatch.canonical-livepatchd.service has finis
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit snap.canonical-livepatch.canonical-livepatchd.service has finished shutt
Oct 30 14:26:39 lennoxg-X510UAR systemd[1]: Started Service for snap application
-- Subject: Unit snap.canonical-livepatch.canonical-livepatchd.service has finis
-- Defined-By: systemd
-- Support: [http://www.ubuntu.com/support](http://www.ubuntu.com/support)
-- 
-- Unit snap.canonical-livepatch.canonical-livepatchd.service has finished start
-- 
-- The start-up result is RESULT.
Oct 30 14:27:39 lennoxg-X510UAR kernel: perf: interrupt took too long (6540 > 64
lines 2218-2240/2240 (END)

---

### Post by deadflowr on 2020-10-30
Hm, interesting.
If you're not currently using the livepatch try disabling it and removing the package
Disabling it frees the token and removing the livepatch package should stop it from trying to do whatever it is trying to do.

Commands should be
```
sudo snap run canonical-livepatch disable
snap remove canonical-livepatch
```

Disable reference here: [https://askubuntu.com/questions/958462/can-i-take-a-computer-off-of-ubuntu-livepatch]("https://askubuntu.com/questions/958462/can-i-take-a-computer-off-of-ubuntu-livepatch")

---

### Post by lennoxg on 2020-10-30
here are the results

[B]lennoxg@lennoxg-X510UAR:~$ sudo do-release-upgrade -d -f DistUpgradeViewGtk3

[/B]
Checking for a new Ubuntu release
/usr/lib/python3/dist-packages/DistUpgrade/DistUpgradeFetcher.py:23: PyGIWarning: Gtk was imported without specifying a version first. Use gi.require_version('Gtk', '3.0') before import to ensure that the right version gets loaded.
  from gi.repository import Gtk, Gdk
/usr/lib/python3/dist-packages/DistUpgrade/ReleaseNotesViewerWebkit.py:33: PyGIWarning: WebKit2 was imported without specifying a version first. Use gi.require_version('WebKit2', '4.0') before import to ensure that the right version gets loaded.
  from gi.repository import WebKit2 as WebKit
Gtk-Message: 15:39:24.510: GtkDialog mapped without a transient parent. This is discouraged.
authenticate 'focal.tar.gz' against 'focal.tar.gz.gpg' 
extracting 'focal.tar.gz'




**Here are the contents of /var/log/syslog  during the time the upgrade was being attempted**

Oct 30 15:38:07 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager w
arning: Window 0x4200003 (do-release) sets an MWM hint indicating it isn't resiz
able, but sets min size 182 x 215 and max size 2147483647 x 2147483647; this doe
sn't make much sense.
Oct 30 15:39:01 lennoxg-X510UAR CRON[8850]: (root) CMD (  [ -x /usr/lib/php/sess
ionclean ] && if [ ! -d /run/systemd/system ]; then /usr/lib/php/sessionclean; fi)
Oct 30 15:39:25 lennoxg-X510UAR canonical-livepatch.canonical-livepatchd[8352]: error: timeout waiting for snap system profiles to get updated
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Main process exited, code=exited, status=1/FAILURE
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Failed with result 'exit-code'.
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Service hold-off time over, scheduling restart.
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: snap.canonical-livepatch.canonical-livepatchd.service: Scheduled restart job, restart counter is at 45.
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: Stopped Service for snap application canonical-livepatch.canonical-livepatchd.
Oct 30 15:39:25 lennoxg-X510UAR systemd[1]: Started Service for snap application canonical-livepatch.canonical-livepatchd.
Oct 30 15:39:35 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager w:arning: Window 0x3800003 (do-release) sets an MWM hint indicating it isn't resizable, but sets min size 182 x 215 and max size 2147483647 x 2147483647; this doesn't make much sense.
Oct 30 15:39:35 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager warning: Window 0x3800003 (do-release) sets an MWM hint indicating it isn't resizable, but sets min size 182 x 215 and max size 2147483647 x 2147483647; this doesn't make much sense.
Oct 30 15:40:07 lennoxg-X510UAR gnome-shell[11073]: [night-light-slider] Setting night light schedule from 9 to 21
Oct 30 15:41:45 lennoxg-X510UAR gnome-shell[11073]: [night-light-slider] Setting night light schedule from 9 to 21
Oct 30 15:42:42 lennoxg-X510UAR /usr/lib/gdm3/gdm-x-session[10914]: (II) event5  - SIGMACHIP Usb Mouse: SYN_DROPPED event - some input events have been lost.
Oct 30 15:43:10 lennoxg-X510UAR opera.desktop[18854]: [18879:18879:1030/154310.403803:ERROR:buffer_manager.cc(488)] [.DisplayCompositor]GL ERROR :GL_INVALID_OPERATION : glBufferData: <- error from previous GL command
Oct 30 15:44:20 lennoxg-X510UAR org.gnome.Shell.desktop[11073]: Window manager w:

---

### Post by deadflowr on 2020-10-30
Try doing it from Software Updater.
Open Software Updater and let it run, then try installing any updates available and then it should give an Upgrade option.

Also, note that Focal release upgrades are in the stable upgrade channel now so running do-release-upgrade with the -d option is not needed.

---

### Post by lennoxg on 2020-10-30
**lennoxg@lennoxg-X510UAR:~$ sudo snap run canonical-livepatch disable**
[sudo] password for lennoxg: 

After putting my password, the command just hung. the cursor just kept blinking


Note that in my software & update live patch settings, Livepatch is off and it also says 

"Canonical Livepatch snap is not available."
and 
"Livepatch is not available for this system"

---

### Post by lennoxg on 2020-10-30
have tried that several times without success

---

