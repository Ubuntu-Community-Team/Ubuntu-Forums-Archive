---
title: "Crash during Upgrade to 15.10 - AMD CPU and graphics"
date: 2016-06-15
forum: Installation &amp; Upgrades
---

### Post by hans12345 on 2016-06-15
My 2nd PC is still on 15.04 and I am upgrading to 15.10 (and later to 16.04).

This is an old (but solid) PC with AMD cpu and AMD graphics (HD5400).

The distribution upgrade crashes with a frozen screen during the "Installing the upgrades" stage. The last message is "Configuring pyhton-gi(amd64)".

How should I proceed?

Your advice appreciated.

---

### Post by hans12345 on 2016-06-15
More info on my upgrade failure:

The PC will not boot, I just get a black screen.

When I try to reboot in advanced mode, it gets to:
- Loading Linux ....  generic
- Loading initial ramdisk

and then stops.

When I try with recovery mode, I get my TTY login.

What should I try next?

---

### Post by hans12345 on 2016-06-15
I found this in AskUbuntu:

[I]Attempt to repair your current installation

Use the process in method 2 to get to the root shell prompt. At the prompt, type:

dpkg-reconfigure -a
apt-get update
apt-get dist-upgrade
reboot
[/I]
Good advice?

---

### Post by ajgreeny on 2016-06-15
> **hans12345 said:**
> I found this in AskUbuntu:

[I]Attempt to repair your current installation

Use the process in method 2 to get to the root shell prompt. At the prompt, type:

dpkg-reconfigure -a
apt-get update
apt-get dist-upgrade
reboot
[/I]
Good advice?
Yes, it's good advice.

Before the reboot you could also run command ```
apt-get install -f
``` to try to fix any broken packages, if there are any.

Those commands can not do any harm, and depending on what went wrong, they may solve it for you..

---

### Post by hans12345 on 2016-06-15
Thanks

I ran apt-get install -f 
and the message came back that I should run:
dpkg --configure -a
This completed, with the message:
Errors were encountered while processing:  resolvconf

Earlier, I saw this:
 resolvconf : Error: /run/ resolvconf/interface either does not exist or is not a directory

---

### Post by hans12345 on 2016-06-15
I re-ran apt-get install -f 
and the message came back just as before:
 resolvconf : Error: /run/ resolvconf/interface either does not exist or is not a directory 
and
Errors were encountered while processing:  resolvconf

---

### Post by Impavidus on 2016-06-15
I prefer release upgrades over fresh installs. It works very well most of the time. But you're upgrading from an obsolete release to an old release, and you'll have to upgrade again within a month. Upgrades from obsolete releases are more often problematic. I think you've already spent more time on this upgrade than you'd have needed for a fresh install of 16.04.

---

### Post by hans12345 on 2016-06-17
I persisted for a while with the upgrade path - I'm just stubborn.

I think the Errors while processing resolvconf were fixed. 

It partially worked and I now can use 15.10, but it is not right and I get error messages on start up.

I suspect the AMD/ATI graphics card is one problem.

So the next step will be a refresh install of 16.04.

---

### Post by ajgreeny on 2016-06-17
If you do a clean install of 16.04 **DO NOT** accept the offer to install third party packages or the system may attempt to add the proprietary driver, fglrx, to the graphics, and at present that will definitely cause you problems, as AMD proprietary drivers are incompatible with the kernel and version of xorg in 16.04

---

### Post by hans12345 on 2016-06-18
> **ajgreeny said:**
> If you do a clean install of 16.04 **DO NOT** accept the offer to install third party packages or the system may attempt to add the proprietary driver, fglrx, to the graphics, and at present that will definitely cause you problems, as AMD proprietary drivers are incompatible with the kernel and version of xorg in 16.04

Thanks, good advice but it is already done.

The PC, with a fresh install of 16.04:  Yesterday it was working OK.
I worked with it for some hours. It was good.


Today it will not boot.

Once it crashed before the Grub menu.

Usually, I get the Grub menu then it goes wrong. Various unexpected graphical effects appear quickly, different every time but one message stands out:
  Recovering journal
and then something about device descriptors.

Shall I try to post the logs?

Or refresh install again, but without the propriety option?

---

### Post by ajgreeny on 2016-06-18
If you can get to a terminal, even if command line from Ctrl+Alt+F1, run commands ```
dpkg -l | grep fglrx
```and if fglrx is shown as installed run
```
sudo dpkg -P fglrx
``` and see if that helps.

---

### Post by hans12345 on 2016-06-18
> **ajgreeny said:**
> If you can get to a terminal, even if command line from Ctrl+Alt+F1, run commands ```
dpkg -l | grep fglrx
```and if fglrx is shown as installed run
```
sudo dpkg -P fglrx
``` and see if that helps.

I ran  ```
dpkg -l | grep fglrx
```

and fglrx is not shown 

:(

---

### Post by hans12345 on 2016-06-19
On the 7th attempt, I managed to boot up today. This final time I did not speed up the grub menu step by hitting 'return' key. Can this be relevant?

I got errors "16.04 has experienced an internal error" but it seems to work fine.

Syslog:

Jun 19 11:59:06 Atlas rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="637" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Jun 19 11:59:43 Atlas com.canonical.Unity.Scope.Applications[1100]: Error loading package indexes: Couldn't stat '/var/cache/software-center/xapian'
Jun 19 11:59:43 Atlas com.canonical.Unity.Scope.Applications[1100]: (unity-scope-loader:4175): unity-applications-daemon-CRITICAL **: daemon.vala:144: Failed to load Software Center index. 'Apps Available for Download' will not be listed
Jun 19 11:59:44 Atlas com.canonical.Unity.Scope.Applications[1100]: (unity-scope-loader:4175): libunity-WARNING **: unity-appinfo-manager.vala:160: Error loading '/usr/share/app-install/desktop/wesnoth-1.10-core:wesnoth-1.10.desktop': No such file or directory
Jun 19 12:01:25 Atlas anacron[658]: Job `cron.daily' terminated
Jun 19 12:01:25 Atlas anacron[658]: Normal exit (1 job run)
Jun 19 12:01:55 Atlas dbus[587]: [system] Activating via systemd: service name='org.freedesktop.hostname1' unit='dbus-org.freedesktop.hostname1.service'
Jun 19 12:01:55 Atlas systemd[1]: Starting Hostname Service...
Jun 19 12:01:55 Atlas dbus[587]: [system] Successfully activated service 'org.freedesktop.hostname1'
Jun 19 12:01:55 Atlas systemd[1]: Started Hostname Service.
Jun 19 12:01:57 Atlas org.gtk.vfs.Daemon[1100]: ** (process:4298): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend
Jun 19 12:01:57 Atlas org.gtk.vfs.Daemon[1100]: ** (process:4294): WARNING **: Couldn't create directory monitor on smb://x-gnome-default-workgroup/. Error: Operation not supported by backend


On pastebin, Xorg.0.log:
[http://pastebin.com/N5byKHYk](http://pastebin.com/N5byKHYk)

---

### Post by hans12345 on 2016-06-21
I am closing this thread since the problem is different from the original one, and am opening a new one about boot problems after a fresh install of 16.04

Thanks to everyone for their advice.

---

