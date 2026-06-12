---
title: "&quot;Operating system not found&quot;"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by james_uo on 2014-07-12
Hello,

I have just installed Ubuntu 14.04, as the only one operating system, on my laptop from flash disk. I restarted my computer, which then indicated "Operating system not found". Where is the problem? I made boot info script.

Thanks a lot.

---

### Post by patsev-anton on 2014-07-12
Whats first boot on the BIOS?

---

### Post by yancek on 2014-07-12
I don't see any problems with the bootinfoscript.  Have you changed the boot priority back to boot first from the hard drive?

---

### Post by james_uo on 2014-07-12
No, the first boot on the BIOS was USB KEY. Why is that wrong? Anyway, I changed the priority and put HDD first. That is the same story.

---

### Post by oldfred on 2014-07-12
I do not see anything wrong with install, other than a few BIOS need boot files to be within the first 100GB of a drive. For those systems, a 25GB / (root) partition and then rest of drive as data or /home works.

But your error is from BIOS before even grub starts to load.

What computer, model & video card?

If newer computer is CSM/Legacy/BIOS mode on?

---

### Post by james_uo on 2014-07-12
The computer is Fujitsu Siemens Amilo Si 3655, graphics Mobile Intel® GM45 Express Chipset x86/MMX/SSE2. It is about 6 years old.

I did boot-repair but it didn't fix up.

Before this Ubuntu 14.04 as the only operating system I had Windows Vista and Ubuntu 13.04, which worked. Now, I tried to install Ubuntu 13.04 and it's the same problem.

---

### Post by oldfred on 2014-07-12
Is BIOS seeing hard drive correctly?

Were old installs 32 bit or 64 bit? Full Ubuntu or one of the other flavors - Xubuntu, Lubuntu?

My Toshiba is from 2006 and does not really run full Ubuntu as Unity requires more video horsepower than internal Intel chip has. But if I install fallback it works fine. Most suggest a lighter weight version.

---

### Post by james_uo on 2014-07-12
Yes, BIOS can see hard drive correctly.

The old install was 32 bit, full Ubuntu.

Ok, I try an other flavor.

---

### Post by james_uo on 2014-07-13
I installed Xubuntu and I got the same problem. Now I have Ubuntu again.

I ran BootPartition exactly by the manual here: [https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition) but I had trouble with the separating /boot partition. "Please enable a repository containing the [linux] packages in the software sources of Ubuntu 14.04 LTS (sda1). Then try again." Here is the thing: [http://paste.ubuntu.com/7787792/](http://paste.ubuntu.com/7787792/).

---

### Post by james_uo on 2014-07-13
Ok, I am over that.

No it is like that. First partition is swap (6GB), second root (4GB), third the rest. But my computer still does not recognise the operating system...

---

### Post by yancek on 2014-07-13
> First partition is swap (6GB), second root (4GB

4GB is not enough for the root filesystem as you can see at the "Preparing to Install Ubuntu" window.  According to the site below, it needs over 6GB and if you want to install any software later, you will need more.  I thought it was over 7GB from my installation but I doubt 4GB will work.  

[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)

---

### Post by james_uo on 2014-07-13
Yes, I already know now. Now I have the first for root (93GB), the second for home (200GB), the third for swap (6GB).

Thank you.

---

