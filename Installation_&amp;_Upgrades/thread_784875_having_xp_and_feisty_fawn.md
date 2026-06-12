---
title: "having xp and feisty fawn"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by etep513 on 2008-05-06
What installation option do I choose in order to install feisty fawn without deleting xp home edition?

---

### Post by Pumalite on 2008-05-06
This might help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

---

### Post by etep513 on 2008-05-08
> **Pumalite said:**
> This might help:
[http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?](http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty_p2?)

Those instructions didn't do the trick.  It was telling me to create some sort of manual partition, but I couldn't do it since there was only an 8mb segment.  I don't know what's going on.  I have about 45gb of free space on my hard drive (windows xp partition takes up the other 30gb.  What should I do?  When I clicked resize the partition, it just said that it was resizing and it stayed at 0%.  What should I do?  Is the newer version easier to install alongside xp???

---

### Post by damis648 on 2008-05-08
It pretty much is. Just download hardy and boot the disc. The installer will guide you through the partitioning process.

---

### Post by Pumalite on 2008-05-08
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
And 'shrink' XP. Right click on XP and choose 'resize from the menu. Make 3 'New partitions in the space created:
10 GB for '/'
1 GB for /swap
The rest for /home. Then install Ubuntu, go Manual and choose the partitions already prepared.

---

### Post by etep513 on 2008-05-08
> **damis648 said:**
> It pretty much is. Just download hardy and boot the disc. The installer will guide you through the partitioning process.

I just have one question about the partitioning process.  How long does it normally take?  When I tried to resize the partition for feisty fawn, I let it sit for about 20 minutes but it was still at 0%.  Was there something wrong with what I was trying to do?  Or am I being too impatient?  If so, how much more time would it need?  I'll give hardy a try.

---

### Post by Pumalite on 2008-05-08
With Gparted Live CD, resizing might take 15 to 20 min, depending on the size of your drive and the number of your files. Making the new partitions might take 5 to 10 min. max.

---

### Post by etep513 on 2008-05-08
Thanks, I'll try that.

---

### Post by Pumalite on 2008-05-08
Good luck.

---

### Post by etep513 on 2008-05-08
> **Pumalite said:**
> Good luck.

I used that tool to make new partitions, but...while I was installing ubuntu, it said that it ran out of space and the installation stopped.  When I tried to restart in xp home edition, it said that there was an error starting the operating system.  I checked the hard drive and all of the data for the operating system is still there.  What do I do to get xp to work again?

---

### Post by Pumalite on 2008-05-08
Super Grub will fix your XP's MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

---

### Post by etep513 on 2008-05-08
> **Pumalite said:**
> Super Grub will fix your XP's MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

Is there a simpler way to do it?  I've never used any of these programs.

---

### Post by Pumalite on 2008-05-08
XP Installation Disk
Hit 'r' for Recovery>FIXMBR>FIXBOOT

---

### Post by etep513 on 2008-05-08
> **Pumalite said:**
> Super Grub will fix your XP's MBR:
[http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html](http://users.bigpond.net.au/hermanzone/supergrubdiskpage.html)
Burn to disk and boot from it.

How can I solve the problem without using supergrub.  I can't even burn it!  Please tell me how to fix the problem through the live cd.

---

