---
title: "Multiple kernels &amp; multiple partitions ?"
date: 2008-07-10
forum: Installation &amp; Upgrades
---

### Post by Tony Flury on 2008-07-10
I want to be able to install a second kernel on my laptop - in a seperate partion (if possible) so i can help with testing of proposed fixes (and new kernels) without risking my current working environment.

I know that Linux supports multiple kernels in the same partition, but is there anywway to do it across multiple partitions - so that the kernels each have their own root directory.

---

### Post by overdrank on 2008-07-10
> **Tony Flury said:**
> I want to be able to install a second kernel on my laptop - in a seperate partion (if possible) so i can help with testing of proposed fixes (and new kernels) without risking my current working environment.

I know that Linux supports multiple kernels in the same partition, but is there anywway to do it across multiple partitions - so that the kernels each have their own root directory.

HI and if I understand what you are asking, it would be like me installing intrepid on a separate partition for testing and still have my hardy and Gutsy partitions intact and operating. Then yes it is possible.

---

### Post by Tony Flury on 2008-07-10
Overdrank - thank you - that is good confirmation.

Exactly how do i do this : 
I assume it would be something along these lines :

[LIST=1]
[*]Use Gpart to build another ext3 partition (i do have plenty of disk space)
[*]use my original live CD to install - using this new partition as root (an effectively telling install to ignore any existing partitions that happen to have other linux images). Will the install complain about building another Root partition ?
[*]Now when i reboot i will have GRUB offering me mutiple kernel choices (potentially several for each partition) - the question here is - how do i tell them apart - is there an easy was to tag them in /boot/grub.d/menu.lst (or whatever it is called - not on my Linux m/c at the moment).
[/LIST]

---

### Post by SkonesMickLoud on 2008-07-10
> **Tony Flury said:**
> Overdrank - thank you - that is good confirmation.

Exactly how do i do this : 
I assume it would be something along these lines :

[LIST=1]
[*]Use Gpart to build another ext3 partition (i do have plenty of disk space)
[*]use my original live CD to install - using this new partition as root (an effectively telling install to ignore any existing partitions that happen to have other linux images). Will the install complain about building another Root partition ?
[*]Now when i reboot i will have GRUB offering me mutiple kernel choices (potentially several for each partition) - the question here is - how do i tell them apart - is there an easy was to tag them in /boot/grub.d/menu.lst (or whatever it is called - not on my Linux m/c at the moment).
[/LIST]

Yes.  The LiveCD also has GParted on it, so no need for booting to 2 separate disks.
Yes.  And no, the installer won't complain about building another /root.
Yes.  When you boot into Ubuntu, simply edit your /boot/grub/menu.lst.  You can put anything you want under "title".  It doesn't matter one way or the other what it's called, as long as the root, kernel and initrd match up, you'll be good.

For safety's sake, you might want to let this ubuntu install live on it's own.  Meaning /root, /home and everything else in the same partition.  You can easily copy from partition to partition, but you wouldn't want to go messing up your real /home by accident...

---

### Post by overdrank on 2008-07-10
> **Tony Flury said:**
> Overdrank - thank you - that is good confirmation.

Exactly how do i do this : 
I assume it would be something along these lines :

[LIST=1]
[*]Use Gpart to build another ext3 partition (i do have plenty of disk space)
[*]use my original live CD to install - using this new partition as root (an effectively telling install to ignore any existing partitions that happen to have other linux images). Will the install complain about building another Root partition ?
[*]Now when i reboot i will have GRUB offering me mutiple kernel choices (potentially several for each partition) - the question here is - how do i tell them apart - is there an easy was to tag them in /boot/grub.d/menu.lst (or whatever it is called - not on my Linux m/c at the moment).
[/LIST]

Hi and to add to SkonesMickLoud, you will have to make a extended partition because you are limited to 4 primary partitions to a drive. From within the extended partition I believe you can have up to 64 partitions.
```
 how do i tell them apart - is there an easy was to tag them in /boot/grub.d/menu.lst (or whatever it is called - not on my Linux m/c at the moment).
```
Well the last install of ubuntu will be first on the list in the grub and will have a older kernel version than your previous install ( if you keep your system up to date :)  )
I have had at one time on the same system Kubuntu, Ubuntu, Xubuntu, Mandriva, and mint installed at the same time.

---

