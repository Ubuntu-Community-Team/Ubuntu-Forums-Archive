---
title: "Manual Partition on Install"
date: 2008-11-08
forum: Installation &amp; Upgrades
---

### Post by Janherbergh on 2008-11-08
Hi, I'm having an extrange problem Installing Kubuntu 8.10 in my Pc. I've have a dual boot with WinXp, and several partitions on the 2 HD's I have.

The problem is that when I try to install Kubuntu, it didn't finds any of the 4 partitions I already have on the 2 Hd's. I select manual partition and there's nothing but 2 HD's perfectly empty for the installation program. The partitions have a lot of files I don't want to lose, of course. Intalling ubuntu 8.04 I didn't had this problem. There's some way to solve this problem? I would like to install Kubuntu without going to ubuntu first. Thanks in advance

PS: Sorry for the poor english.

---

### Post by SaltySurfer on 2008-11-08
are you trying to install it while booted in Windows (Wubi?) or are you booting into the live CD?

---

### Post by Janherbergh on 2008-11-08
I'm booted from Live CD. The other way, via Wubi can work?

---

### Post by Mr_JMM on 2008-11-08
Do you still have Ubuntu installed on one of the partitions?

I had similar when I had XP / Ubuntu dual boot on one HDD then installed Kubuntu on 2nd HDD. Kubuntu seemed to completely ignore everthing. I assumed it saw the Ubuntu Grub and just thought (hey ho, I'll leave it).

Although a Grub file was created in the Kubuntu install, it never saw the other HDD's. It wasn't a problem, I simply set the bios to boot from Ubuntu drive and added Kubuntu to the Grub Menu.lst in Ubuntu.

---

### Post by Janherbergh on 2008-11-08
In my case I don't think this could be the problem. All began because I had to format the windows partition. As that would screw grub, I said to myself, "Ey, why not try a fresh kubuntu install?". There was no grub when first tried to install Kubuntu 8.10. 

Even if that's the case, installing in hdb, which seems to be fine, will suppose formating it, as only has 1 ntfs partition for files.

Now, I have windows XP and ubuntu 8.04 running, both of them working fine with the HD's and are able to enter to all the partitions. The problem are the installation programs of Ubuntu and Kubuntu 8.04 and 8.10 (yeah, I tried all of them). Any ideas how to solve this?

---

