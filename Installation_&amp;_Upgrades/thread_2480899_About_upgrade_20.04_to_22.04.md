---
title: "About upgrade 20.04 to 22.04"
date: 2022-11-14
forum: Installation &amp; Upgrades
---

### Post by satimis on 2022-11-14
Hi all,

During upgrade Ubuntu 20.04 desktop to 22.04 desktop following warning popup;
```

upgrade to Ubuntu 22.04 your system unable reach snap store

```
Please advise what is this problem and how to fix this problem?

After upgrade finished on Terminal;
$ sudo snap install firefox```

Setup snap "firefox" (2067) security profiles                                  |
firefox 106.0.5-1 from Mozilla&#10003; installed

```

I can install and start Firefox without problem.

I made this upgrade-test on a cloned Ubuntu 20.04 VM of VirtualBox. I can clone another Ubuntu 20.04 VM to test again.

Please advise.  Thanks in advance.

Regards

---

### Post by MAFoElffen on 2022-11-15
Yesterday morning I noticed that there was problem with both the Snap Store being offline... and with Ubuntu Forums. I don't believe those are in any way connected, but just a weird coincidence.

It came back up after a few hours. It is fine now.

---

### Post by satimis on 2022-11-16
> **MAFoElffen said:**
> Yesterday morning I noticed that there was problem with both the Snap Store being offline... and with Ubuntu Forums. I don't believe those are in any way connected, but just a weird coincidence.

It came back up after a few hours. It is fine now.
Hi,

Thanks for your advice.

Just made another test upgrading an Ubuntu 20.04 VM to 22.04.  A warning still pop-up (please see attached screenshot)

After finish Firefox is still there.  Starting it results in freeze the VM.

Ran;```

sudo apt remove firefox

```
saying Firefox not installed.  It is very strange to me.

$ sudo snap install firefox```

snap "firefox" is already installed, see 'snap help refresh'

```

Any advice?  Thanks

Regards

---

### Post by Dennis N on 2022-11-16
The "not installed" message is only telling you that no .deb package of Firefox is installed. The .deb package of Firefox was automatically removed and replaced by the snap package of Firefox when you upgrade to 22.04. That's Ubuntu's choice for 22.04 and later.

---

### Post by satimis on 2022-11-16
> **Dennis N said:**
> The "not installed" message is only telling you that no .deb package of Firefox is installed. The .deb package of Firefox was automatically removed and replaced by the snap package of Firefox when you upgrade to 22.04. That's Ubuntu's choice for 22.04 and later.
Hi,

Thanks for your advice.

Firefox is automatically installed during upgrade to Ubuntu 22.04.  But it is not stable.  Dragging its window spreading to several windows.  Please refer to screenshot attached.

Besides this VM freezes from time to time,  Any remedy?  Thanks

Regards

---

### Post by Dennis N on 2022-11-16
I launched the Firefox snap and opened several windows, but I saw no problem when dragging windows. Maybe I don't correctly understand your problem. I am also using a VM, but my 22.04 are new installs, not upgrades from 20.04, so not directly comparable. I've never seen the freezing on my computers.

You don't need to use the snap. Some users use a PPA which offers the .deb version. Other users download a tar.gz file of Firefox from Mozilla. Other users (including me) install the Flatpak. I don't even bother to remove the snap Firefox. Everyone has their own reasons for their choices.  

So you might try an alternative.

---

### Post by satimis on 2022-11-16
> **Dennis N said:**
> I launched the Firefox snap and opened several windows, but I saw no problem when dragging windows. Maybe I don't correctly understand your problem. I am also using a VM, but my 22.04 are new installs, not upgrades from 20.04, so not directly comparable. I've never seen the freezing on my computers.
Dragging Firefox window, it displays several Firefox windows at the same time

> 
You don't need to use the snap. Some users use a PPA which offers the .deb version. Other users download a tar.gz file of Firefox from Mozilla. Other users (including me) install the Flatpak. I don't even bother to remove the snap Firefox. Everyone has their own reasons for their choices.  

So you might try an alternative.
Thanks

Performed following test:
Clone a new Ubuntu 20.04 VM

Start it and on Terminal run following commands;
sudo apt update ; sudo apt upgrade
sudo apt autoremove
sudo apt remove firefox
reboot

After reboot;
Activities -> update software
Upgrade to Ubuntu 22.04

Installation went through without complaint

After finish start Ubuntu 22.04 VM
on Terminal run;```

sudo snap install firefox

```

Now it works.  VM is not freezing

Regards

---

### Post by Dennis N on 2022-11-16
Removing Firefox BEFORE starting the upgrade appears to avoid the snap getting installed during the upgrade. Good idea. 
But you installed the snap afterwards. Did you want the snap?

If I were doing an upgrade, I think I would do the same (remove Firefox before upgrading), then just install the Flatpak (just my preference) after completion. The snap package would be gone for good.  
The Snap is OK, if you accept the limitations - like being able to access only some locations in your file system, and only able to use themes in the "gtk-common-themes" snap package.

---

### Post by satimis on 2022-11-16
> **Dennis N said:**
> Removing Firefox BEFORE starting the upgrade appears to avoid the snap getting installed during the upgrade. Good idea. 
But you installed the snap afterwards. Did you want the snap?

If I were doing an upgrade, I think I would do the same (remove Firefox before upgrading), then just install the Flatpak (just my preference) after completion. The snap package would be gone for good.  
The Snap is OK, if you accept the limitations - like being able to access only some locations in your file system, and only able to use themes in the "gtk-common-themes" snap package.
Hi,

Why I ran snap to install Firefox because it is already running on Ubuntu 22.04

Perform another test to upgrade Ubuntu 20.04 to Ubuntu 22.04

Steps:
Delete Ubuntu 22.04 on #5 above
Clone another Ubuntu 20.04 desktop VM
Start Ubuntu 20.04 VM and on Terminal run;```

$ sudo apt update and upgrade
$ sudo apt autoremove
$ sudo apt remove firefox
$ reboot

```

Activities -> Software updater
Upgrade VM to Ubuntu 22.04. Installation went through without complaint

Start Ubuntu 22.04 and on Terminal run;
$ sudo apt install flatpak
$ flatpak --version
Flatpak 1.12.7

$ sudo flatpak remote-add --if-not-exists flathub [https://flathub.org/repo/flathub.flatpakrepo](https://flathub.org/repo/flathub.flatpakrepo)
$ sudo flatpak install firefox```

Looking for matches…
Similar refs found for ‘firefox’ in remote ‘flathub’ (system):

   1) app/org.mozilla.firefox.BaseApp/x86_64/20.08
   2) app/org.mozilla.firefox.BaseApp/x86_64/21.08
   3) app/org.mozilla.firefox/x86_64/stable
   4) app/org.mozilla.firefox.BaseApp/x86_64/22.08

Which do you want to use (0 to abort)? [0-4]: 4

```

Firefox installed.  Now it is running without problem

Regards

---

