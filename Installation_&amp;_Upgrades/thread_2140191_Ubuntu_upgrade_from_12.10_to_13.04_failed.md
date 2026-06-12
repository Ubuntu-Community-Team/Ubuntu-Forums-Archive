---
title: "Ubuntu upgrade from 12.10 to 13.04 failed"
date: 2013-04-28
forum: Installation &amp; Upgrades
---

### Post by fr33z0n3r on 2013-04-28
:(  I don't even know where to start.   This is unbelievable.  I'm not staying up to troubleshoot this, but I'll leave my PC on.  I'll follow up as time permits over the next few days.
I can provide logs if they will help.

_**Current state:**_
Still logged into Ubuntu, upgrade "completed".  It said I had errors during install.  It said the system may be in an unusable state.

**_System info:_**
New H77 based system with Samsung 840 Pro 256GB SSD
No major tweaks, just small stuff, including SSD recommendations to use "noatime" on the / volume.

_**What happened during install:**_
1. Install started fine.

1.5 Install halted to ask which services did I want to restart(?) for install of some package.  I left the default and clicked ok.

2. About 50% thru, got an error on the screen saying low disk space. (Absolutely not true - brand new drive, works fine (up till now) and about 150GB free during install) The rest of the popup box was litterly boxes instead of characters.

3. I started getting other errors, "could not install linux-image-extra-3.8.0-19-generic" - "subprocess installed post-installation script returned exit status 2".  Could only click Close.

4. Then at least 1 more similar error appeared for another "app".  Not immediately following the previous one.  Clicked Close.

5. Eventually install said there were errors and it was going to do something (revert? not sure) but I could only click Yes.

6.  Install said it completed but there were errors and the system may be unusable.

---

### Post by davidbaumann on 2013-04-29
I had the same problem - there is no space left on /boot.

I guess you should uninstall some older kernels (but leave one!!).
Then see what
```
apt-get install linux-image-extra-3.8.0-19-generic
```
Says.

David.

---

### Post by fr33z0n3r on 2013-04-29
Thanks David!  That got me a fully installed 3.8 kernel.

Now, what about the other errors I saw?  Could they have been critical errors based due no space on /boot?

Is there a way to say re-upgrade?  Will a "force re-upgrade" preserve all my config?

---

### Post by grahammechanical on 2013-04-29
Low disk space is not referring to the whole of the hard disk but to a specific partition. Do you have a separate /boot partition? What was your partition arrangements for Ubuntu 12.10.

---

### Post by mörgæs on 2013-04-29
> **fr33z0n3r said:**
> Can a mod please move this to "installs and upgrades"?  I'm guessing that is the correct forum for this?


Done.

---

### Post by fr33z0n3r on 2013-04-29
@grahammechanical - I have a 255MB boot partition, and a 250GB root partition.  The boot partition was filled.  I uninstalled old kernels to resolve the space issue there.  I just don't understand if I will have other issues, sicne I saw multiple errors. 

I didn't record them, since I thought the whole install was going to fail from the point of the first error on out.  It was only 2 or 3 more errors.  That makes it seem salvagable, but I have no idea how to determine what errored, and how/if to fix it.

---

### Post by fr33z0n3r on 2013-04-29
For next steps, what should I do?

1. Should I just reboot and see if its bootable?  Ignoring any other errors?
2.  Should I review/share the upgrade logs (which?) in order to isolate what errored out?
3.  Should I run commands like

```
apt-get install -f
apt-get install --reinstall ubuntu-desktop
```

OR 

4.  Run these - "To try to finish configuring all remaining packages, and fix any broken packages, open terminal and try:"

```
sudo dpkg --configure -a
sudo apt-get install -f 
```


I would appreciate help fom folks since I'm a noob at linux troubleshooting.

---

### Post by fr33z0n3r on 2013-04-29
I started with #4 and then also tried another command to upgrade.  It seems like it was quiet and therefore perhaps my issues are over?  :confused:

I have a backup from 12.10, but I'd rather not learn how to restore that (profile was encrypted).  I'm gonna try and reboot now.  If it fails I'll review info about  the liveCD recovery I've read about.  And try to post back here too.

```
user@desktop:~$ sudo dpkg --configure -a
[sudo] password for user: 
user@desktop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libaccounts-qt5-1 libblas3gf libdee-qt5-3 libmath-round-perl
  libqt5graphicaleffects5 libqt5network5 libqt5qml5 libqt5quick5 libqt5svg5
  libqt5v8-5 libqt5xml5 libsignon-qt5-1 libwebp2 libxmlrpc-core-c3
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
  qtdeclarative5-accounts-plugin qtdeclarative5-friends-plugin
  qtdeclarative5-qtquick2-plugin qtdeclarative5-ubuntu-ui-toolkit-plugin
  ubuntu-ui-toolkit-theme
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
user@desktop:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by fr33z0n3r on 2013-04-29
um, I made it back within minutes of my last post.  Forums were down.  The forums seem to be back now.

I think everything is fine as far as the upgrade.  I had an audio issue with Skype that I managed to find a fix for.

So I'm all set on this.  [FONT=franklin gothic medium]*[SIZE=6]**Thanks for the help!**[/SIZE]*[/FONT]

---

