---
title: "System doesn't see Ubuntu"
date: 2005-04-07
forum: Installation &amp; Upgrades
---

### Post by btgon on 2005-04-07
Hi all,

I just installed Ubuntu and when the installer reboots it just goes back into windows and doesn't even show the grub boot loader. I have a 20 gig master with windows and a 160 slave with 100 formatted for ntfs. I wanted to just install ubuntu on the last 60 gigs of the 2nd hard drive.

I originally installed grub on the mbr, but that failed on boot so I restored the windows mbr. I then tried making the / partition on the second hard drive bootable but that is when it would just reboot back into windows.

Any help would be greatly appreciated!

---

### Post by soul_rebel on 2005-04-07
you have to install grub in the first disk's mbr. that's the only way. Don't care to make the partition bootable.
bye

---

### Post by btgon on 2005-04-07
Thanks!

Now I know I am on the right track! I have installed grub on the MBR on the first disk but now I am getting a grub error 17. Atleast I see grub, I am getting closer!

---

### Post by soul_rebel on 2005-04-07
error 17 means that grub can't find its files. they are placed under /boot. Where is your /boot? on which filesystem?

---

### Post by btgon on 2005-04-07
I just had the installer automatically partition the free space on the second drive and it didn't create a /boot. Can I have a /boot on the second drive and still install grub on the mbr of the first one? And how large should I make /boot?

---

### Post by soul_rebel on 2005-04-08
You don't need to have a separate /boot partition. You just need to have boot on a normal filesystem which grub can read (no raid no encryption etc). Yes you can have /boot on a secondary disc. So the problem is in the way the grub mbr has been installed. I can't help you to set up grub in the correct way, you need a grub-guru or you need to read and become a little grub-guru. good luck! sorry i cant help

---

