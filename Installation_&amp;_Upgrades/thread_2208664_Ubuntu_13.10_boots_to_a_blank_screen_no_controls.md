---
title: "Ubuntu 13.10 boots to a blank screen no controls"
date: 2014-03-01
forum: Installation &amp; Upgrades
---

### Post by kevrick25 on 2014-03-01
I recently updated to ubuntu 13.10 from 12.10 (second time I've ever updated) but when it was done and restarted, the computer boots, passes the buntu splash and goes into a black screen that has absolutely nothing, and no keyboard commands will work.

I have assumed it was fault of unity because my NVIDIA GeForce fx 5200 can't run Unity 3D which I discovered after updating from 12.04 to 12.10. At that time however I was still able to use the keyboard to log out and/or access terminal then change to gnome fallback. Using my assumption I tried to edit the GDE and LightDM to either stop the auto login process or use gnome fallback by default. 

Alas, it didn't work and still boots to a black screen. 

I've searched far and wide and see nothing that seems to be helpfull to my situation, not that I can easily interpret anyways ie. Step by step help. I don't even know which DM the system is trying to use. 

My only available usage of the system is the group as it won't boot to recovery either.

Anyone who can walk me though personally I'd gladly appreciate it.

---

### Post by leo_mancini on 2014-03-02
'm also experiencing the same thing. 
For the moment, I'm holding down the shift key each time I boot and select an earlier version of the kernel - 3.11.0-14-generic
which I am finding annoying.

>  paul@paulspc:/var/log$ cat Xorg.1.log |grep EE	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[  1838.981] Initializing built-in extension MIT-SCREEN-SAVER
[  1839.127] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1839.127] (EE) NVIDIA:     system's kernel log for additional error messages.
[  1839.128] (EE) Failed to load module "nvidia" (module-specific error, 0)
[  1839.146] (EE) NVIDIA: Failed to load the NVIDIA kernel module. Please check your
[  1839.146] (EE) NVIDIA:     system's kernel log for additional error messages.
[  1839.146] (EE) Failed to load module "nvidia" (module-specific error, 0)
[  1839.164] (EE) [drm] KMS not enabled
[  1839.164] (EE) open /dev/dri/card0: No such file or directory
[  1839.169] (EE) open /dev/fb0: No such file or directory
[  1839.811] (EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
[  1847.874] (EE) Server terminated successfully (0). Closing log file.




---

### Post by kevrick25 on 2014-03-04
> **leo_mancini said:**
> 'm also experiencing the same thing. 
For the moment, I'm holding down the shift key each time I boot and select an earlier version of the kernel - 3.11.0-14-generic
which I am finding annoying.

I should probably try changing the kernel version, not sure if it would help no do I know how to....

---

### Post by kevrick25 on 2014-03-14
Can anyone help with this please, I'd really like my computer usable again

---

### Post by evan8 on 2014-03-14
Happened to me awhile back the first an donly timed I upgraded. I figure it was a driver display issue. BUt I have heard it's best to avoid upgrading that way and just do clean reinstalls to avoid such conflicts

---

### Post by kevrick25 on 2014-03-19
> **evan8 said:**
> Happened to me awhile back the first an donly timed I upgraded. I figure it was a driver display issue. BUt I have heard it's best to avoid upgrading that way and just do clean reinstalls to avoid such conflicts
Guess that's my only option, going to be difficult though, seeing as my Disc drives refuse to read my boot disks

---

