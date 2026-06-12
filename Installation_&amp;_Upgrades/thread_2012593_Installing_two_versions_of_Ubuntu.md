---
title: "Installing two versions of Ubuntu"
date: 2012-06-29
forum: Installation &amp; Upgrades
---

### Post by Sigma1 on 2012-06-29
Hello,
I have a computer with two hard disks: the first has an old Windows on it, the second has Ubuntu 11.10. My question is: can I install Ubuntu 8.04 -- which I used fine for a year or two -- on free space on the Windows disk, without upsetting boot options etc.? I'd also like to keep a common /home partition for 8.04 and 11.10, though I realise this might prove difficult, given the changes in ./gnome and other settings folders.
The reason I want to do this is that this is old hardware, and I'd like to have a recovery solution -- apart from a live CD.
Thanks in advance.

P.S. Here's the breakdown:
/dev/sda1 fat32 PRESARIO_RP (recovery partition)
/dev/sda2 ntfs PRESARIO (Windows) [gparted flags this partition as boot.]
/dev/sda3 ext3 Free [I want to put 8.04 here.]

/dev/sdb1 ext1 /
/dev/sdb2 extended partition
    /sdb5 linux-swap
/dev/sdb3 ext3 /home

---

### Post by blackbird34 on 2012-06-29
I don't see why not. Although if your computer can run Ubuntu 11.10 Oneiric Ocelot, you should replace 8.04 with a supported version (Lucid, Oneiric or Precise)  -- 8.04 support has run out except for servers.

---

### Post by Sigma1 on 2012-06-29
Thanks for the answer, blackbird34. I'll give it a go... If I appear a little nervous, it's because I tried to install Precise on sda3 a day or two ago, and the thing crashed during installation... possible a graphics card issue. (I have an old nvidia card -- GeForce FX 5100 -- that's never been easy and is possibly no longer fully supported in the installation interface.)

---

### Post by Sigma1 on 2012-07-01
Well, things went more or less as planned. However, I could no longer boot on 11.10, after installing 8.04: Grub (8.04) had taken over from Grub2 (grub-pc on 11.10). So I booted from a Live-CD, installed boot-repair, and fixed the problem.
I might just have been able to avoid this if I'd been a little more careful installing 8.04, possibly choosing not to put grub anywhere, booting from 11.10 and running sudo update-grub from within 11.10 to get 8.04 there on the boot menu.
Thanks for the help. I can now travel four years back in time whenever I want. ;)

---

