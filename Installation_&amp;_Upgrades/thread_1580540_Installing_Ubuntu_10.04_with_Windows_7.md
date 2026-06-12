---
title: "Installing Ubuntu 10.04 with Windows 7"
date: 2010-09-23
forum: Installation &amp; Upgrades
---

### Post by prahar on 2010-09-23
I am planning to do a dual boot of Ubuntu 10.04 with Windows 7. I have the following questions first.

I bought a brand new Dell Inspiron 14R, Core i5, 4GB RAM, 500GB HDD, with Windows 7 home premium 64 bit

Many of friends (rather friends of friends) have installed ubuntu with windows 7, but they have all run into the troubles. Many of them have Dell Laptops, preinstalled with windows 7. when they install ubuntu, windows 7 somehow gets corrupted (login screen does not load). They then fix that using the windows recovery disc, but on restart the problem occurs again. no way to start windows without the recovery disc. So they did a clean install of 7, and installed ubuntu through Wubi, which then worked fine.
(btw, they all installed ubuntu 10.04 64-bit)

I am sure my friends have not erred in the installation process as they are frequent ubuntu users (earlier with XP and vista).

I would prefer not using Wubi, would rather do the complete partitioning and stuff.

I just want to know if others have come across this problem. And if yes, what is the solution?

I have not yet installed ubuntu, but want to.

---

### Post by Praveen30 on 2010-09-23
[http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html]("http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html")

---

### Post by Rubi1200 on 2010-09-23
There have been a number of posts on the forum regarding dual-booting on Dell laptops/computers. The trouble seems, mostly, to do with the recovery partition.

Do a search on the forums for more about this, but there is no reason (if done properly) that you cannot happily dual-boot both systems.

See here for more information:
[https://help.ubuntu.com/community/DualBoot/Windows](https://help.ubuntu.com/community/DualBoot/Windows)

By the way, Wubi is not the way to go as it was always intended as a means of trying Ubuntu rather than being a dedicated install.

---

### Post by sikander3786 on 2010-09-23
> 
There have been a number of posts on the forum regarding dual-booting on Dell laptops/computers. The trouble seems, mostly, to do with the recovery partition.

Believe me. Exactly what I was typing and eventually refreshed and saw your post. So a big +1.

To the OP: Complete install is better than Wubi in many respects. Just go through some search and the link provided by Rubi and post any further queries.

---

### Post by uRock on 2010-09-23
> **Praveen30 said:**
> [http://http://http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html]("http://http//http://tricksfind.blogspot.com/2010/09/ubuntu-install-linux-quick-and-easy.html")
Your link is broken.

---

### Post by efflandt on 2010-09-23
Before you make any changes to the hard drive, record the output of **sudo fdisk -l** from live Ubuntu CD.

Something I was not aware of when I temporarily installed Ubuntu on a Dell laptop and put grub on the Linux partition (sda4) to avoid tampering with the MBR is that the original Win7 "boot" partition is sda2 (RECOVERY partition), not sda3 where Win7 is.  So when I removed Ubuntu and tried to set sda3 as boot partition, I had to use Win7 disk several times to sort that out because it said bootmgr was missing.  Other than that, everything worked fine until that removal glitch.

To be on the safe side, shrink Win7 with its own tools.  Somewhere in administration tools for drives is a selection to shrink the Win7 partition.  In my case there were already 3 partitions, so I just manually created 1 primary partition during installation for Ubuntu.  But if you want to be able to hibernate, you also need swap, so you would probably need an extended partition for at least a Linux partition and swap partition as logical partitions, and put grub in the MBR.

A peculiar thing with a new Dell desktop (Studio XPS 8100) it that for some reason it could not boot Lucid at the far end of a 500 GB USB drive (the USB drive boots fine on older Dell Inspiron laptop from 2006 and Toshiba laptop from 2006).  But the new PC booted Ubuntu fine at the far end of its 1 TB internal drive.  Although, my DVD/CD drive was defective, and in the process of replacing that, they also replaced my hard drive.  So I am currently running 64-bit Lucid on the new PC from a 160 GB USB drive until I get around to installing it again.

---

### Post by prahar on 2010-09-23
thank you all for the input, i will go through the link, and update.

---

