---
title: "Upgrade to 11.04 on Virtual Box"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by tooCanad on 2011-04-29
I am running Ubuntu inside of Virtual Box 4.06 on a Dell e4310 with 4GB of ram.
I did the upgrade. It went smoothly enough. However, at first login on reboot following the upgrade an error message indicated I did not have the have the correct hardware to run Unity and it switched to Ubuntu Classic (Gnome) UI.

Any thoughts are appreciated.

---

### Post by CHFFriday on 2011-04-29
tooCanad,
I'm haviing the same problem.I think it has something to do with VM's video. If I get a fix I will let you know. I have seen two other post here that the users had it running but did not state if Unity was running. I ask them for their VB setting.

CHFFriday

---

### Post by tooCanad on 2011-04-29
Thanks I was thinking something along those lines but did not have a chance to bang away at it.

TC

---

### Post by uidb4056 on 2011-04-29
> **tooCanad said:**
> I am running Ubuntu inside of Virtual Box 4.06 on a Dell e4310 with 4GB of ram.
I did the upgrade. It went smoothly enough. However, at first login on reboot following the upgrade an error message indicated I did not have the have the correct hardware to run Unity and it switched to Ubuntu Classic (Gnome) UI.

Any thoughts are appreciated.
In the settings of your virtual machine you need to enable 3D aceleration and give enough video Ram, after that you have to install on your VM the Guest Additions. Then after reboot you get the Unity interface.

---

### Post by tooCanad on 2011-04-29
Tried enabling 3D Acceleration. Increased the video memory from 8MB to 40MB of 128MB max.

Ubuntu crashes on login using Ubuntu and Ubuntu classic.

Ran the command ```
/usr/lib/nux/unity_support_test -p
``` in terminal and it had identified the 3D acceleration as an issue.

Turned off 3D acceleration and it booted into classic Ubuntu no issue.

---

### Post by uidb4056 on 2011-04-29
Have you installed Guest Additions?, wich version of Virtualbox are you running?

---

### Post by tooCanad on 2011-05-02
Guest Additions installed. Virtual box version 4.0.6  r71416

Seems to be an issue with 3D support/ resources.

---

### Post by YesWeCan on 2011-05-02
I can get 11.04/Unity working in VirtualBox. But it is unstable when I try to resize the VB window. The machine freezes and has to be "powered off". So I am not surprised you are having problems. We shall have to wait until Unity is out of beta. ;)
```
**General**
Name: Ubuntu 11.04 32 bit
OS Type: Ubuntu
 
**System**
Base Memory: 2048 MB
Processor(s): 1
Boot Order: Floppy, CD/DVD-ROM, Hard Disk
VT-x/AMD-V: Enabled
Nested Paging: Enabled
 
**Display**
Video Memory: 128 MB
3D Acceleration: Enabled
2D Video Acceleration: Disabled
Remote Desktop Server: Disabled

```

---

### Post by tooCanad on 2011-05-05
YesWeCan:

You are a step ahead of me. What hardware are you running Virtual Box on?

---

### Post by YesWeCan on 2011-05-05
Below.
In theory the hardware shouldn't matter much, but I think VB's 3D emulator is still "experimental" and so that may explain the differences we are seeing. I don't know how VB works tho so this is just a guess.
In VB I tried using SUSE 11.4 with Gnome Shell demo and it didn't really work at all.

It might be worth keeping an eye on the VB forum: [http://forums.virtualbox.org/viewtopic.php?f=3&t=40972](http://forums.virtualbox.org/viewtopic.php?f=3&t=40972)

---

