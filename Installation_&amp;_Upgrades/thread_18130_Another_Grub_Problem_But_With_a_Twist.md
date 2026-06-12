---
title: "Another Grub Problem But With a Twist"
date: 2005-03-04
forum: Installation &amp; Upgrades
---

### Post by medw1974 on 2005-03-04
Hi

This is my first day with Ubuntu and so far I like what I see but I am having problems with grub. I've read through all the other grub problems but they mainly seem to deal with dual booting windows+Ubuntu.

My situation is as follows:

hda: 40gb Seagate IDE Fedora Core 3 all ext3 except for 512mb swap.(primary master)
hdd: 20gb Seagate IDE Ubuntu all ext3 except for 512mb swap.(secondary slave)

During installation I installed grub to (hd0) and on 1st reboot got the grub error 21 message so went into bios this showed that the ubuntu drive wasnt been seen so changed sec slave from none to auto and rebooted and got the grub menu but only with the ubuntu options no mention of fedora. Incidently I have to go through this bios procedure every reboot.

Once I get into Ubuntu I have no access to hda (with all my data on Fedora) although device manager shows hda as does cfdisk but no entry for it in fstab.

So basically I'm looking for 2 solutions:

1. Get the option to choose from Fedora or Ubuntu in Grub.
2. Access my Fedora disk from Ubuntu.

Many Thanks

Michael

---

### Post by medw1974 on 2005-03-05
I managed to sort this myself by doing the following:

$ sudo mkdir /mnt/fedora
$ sudo mount /dev/hda1 /mnt/fedora

I was then able to copy the relevant entries from the fedora's grub menu.lst over to ubuntus.

Still had the bios problem but have since reinstalled Ubuntu on its own on hda so thats not a problem now.

Regards,
Michael

---

### Post by pigpen on 2005-03-05
Glad you got it working. I also used a similiar method as you when I installed Ubuntu today  on a triple boot system. I had to copy the Ubuntu GRUB menu entries into my previous GRUB's menu.lst file and it worked as well.

---

