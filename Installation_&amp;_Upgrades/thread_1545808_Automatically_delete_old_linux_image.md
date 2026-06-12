---
title: "Automatically delete old linux image"
date: 2010-08-04
forum: Installation &amp; Upgrades
---

### Post by redconfusion on 2010-08-04
Is there a way to automatically remove the old linux image when a new one is updated?

When my system boots up it shows option 
Ubuntu kernel version x.x.x-21
Ubuntu kernel version x.x.x-22
Ubuntu kernel version x.x.x-23
Ubuntu kernel version x.x.x-24
memtest
memtest + console
Windows 7 loader

Ubuntu seems to boot up the exact same regardless if I choose version 21 or 24.

Dont recall the exact kernel since im not in front of my computer now.

---

### Post by tommcd on 2010-08-04
What version of Ubuntu are you running????
If you are running Ubuntu 10.04, which is the current version, then you are using grub2. See this from the Ubuntu wiki:
[https://wiki.ubuntu.com/Grub2#Removing%20Entries%20from%20Grub%202](https://wiki.ubuntu.com/Grub2#Removing%20Entries%20from%20Grub%202)
So if you remove the older kernels using synaptic or apt-get, and then run "*sudo update-grub*"; then the old kernels will be gone from your grub2 menu.
You should save at least one older kernel though. If the new kernel will not boot for some reason you will need a known working kernel to boot into to troubleshoot the problem.
I don't understand why so many people seem to have such a problem with this. I just leave those old kernels there in the grub menu. They don't bother me, so I don't bother them :) A lot of people seem to loose sleep over this though. Rest assured, you can easily remove the old kernels though if you want to.
> **redconfusion said:**
> 
Ubuntu seems to boot up the exact same regardless if I choose version 21 or 24. 
Yes it will. The kernel updates often include bug fixes and or security updates. So you should always use the newest kernel if you can.

---

### Post by Cavsfan on 2010-08-04
Don't mean to butt in, but I used to remove old kernels via Synaptic Package Manager and somehow I removed something I shouldn't have and could not boot into Ubuntu.

I have since learned that Ubuntu Tweak has a method of removing old kernels that will not cause you any damage.
You can put a password on something, but you can't fix stupid! I am talking about myself and rather than try to ask a bunch of questions on here, I just decided to do a clean install.
I lost some stuff I didn't really want to loose, but at least I learned a lesson.

If you do not have Ubuntu Tweak, it can be obtained via Applications > Ubuntu Software Center.
If you open Ubuntu Software Center and enter Ubuntu Tweak in the top right, it will appear as **config Ubuntu tool**.
Then once installed (if not already installed), Applications > System Tools < Ubuntu Tweak.
Then on the left click on Package Cleaner and old kernels will appear there. Just click on Clean Kernels on the right to remove the old ones.

This is the safest method I have noticed.
(Ron White has a DVD entitled You can't fix Stupid, which is where I got that from)

**sudo uname -a** will tell you what kernel you are using.

---

