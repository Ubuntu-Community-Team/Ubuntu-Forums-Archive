---
title: "Stuck on fsck after upgrading to 15.10"
date: 2016-04-07
forum: Installation &amp; Upgrades
---

### Post by pressst4rt on 2016-04-07
I'm not sure if this is the right place to ask this, but the forums aren't easily navigated from my phone.

I'm fairly new to Linux. I recently upgraded from 14.04 to 15.10. I rebooted just after the update. For some reason, I'm now stuck on a screen that says this:

'fsck from util-linux 2.26.2
/dev/sda1: clean, 312789/7561216 files, 10603427/30223872 blocks'

I tried going into tty1 and running 'startx' but then I get an error saying 'xinit' is currently not installed. 

Upon trying to install it, I get another error saying 'xinit' had no installation candidate.

Tried running a 'sudo apt-get update' just because that seems like a failsafe for some people but still getting the same error.

---

### Post by grahammechanical on 2016-04-07
All of us see that message. Especially if we are using proprietary video driver which for some reason prevents the Ubuntu purple splash screen from showing. Not all of us fail to load to a login screen. You can try this

At the boot menu select Advance options for Ubuntu and then select a recovery mode kernel. At the recovery menu select Resume. It should load to a working desktop using an open source video driver. If it does, go to System Settings>Software & Updates>Additional Drivers tab and change the video driver. You need to be connected to the internet and wait for the utility to find suitable drivers for your system. I would opt for an open source video driver first of all. 

You are aware are you not, that 15.10 will reach end of life during the summer and you will need to upgrade to 16.04? 

Regards.

---

### Post by pressst4rt on 2016-04-07
It doesn't take me to a working desktop, but instead takes me to tty1.

---

### Post by grahammechanical on 2016-04-07
So, you can get to the Recovery menu. Then select Network to establish an internet connection & put the file system into read/write mode which is needed if we are to make changes to the OS. Then select Root shell prompt & run

```
apt-get update
apt-get upgrade
apt-get dist-upgrade
```

To get out of the Root shell prompt type exit. Now try Resume. You may also need to use the Root shell prompt to remove the proprietary video driver if you had one installed before doing the upgrade.

Regards.

---

