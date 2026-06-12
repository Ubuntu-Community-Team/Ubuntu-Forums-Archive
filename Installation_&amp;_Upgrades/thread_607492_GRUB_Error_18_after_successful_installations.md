---
title: "GRUB Error 18 after successful installations"
date: 2007-11-09
forum: Installation &amp; Upgrades
---

### Post by sandman887 on 2007-11-09
Hey,

I have installed xubuntu/ubuntu over and over on my Compaq desktop (Pentium III @ 800 MHz, 240+ of RAM) and when it finishes and reboots, it keeps displaying 

GRUB Loading stage1.5.

GRUB loading, please wait...
Error 18

I have searched the boards and found a topic dealing with an issue similar to mine. Someone said that having too high cylinders causes it because the bios can't recognize it, and suggested making the first partition a few megs to put the bootloader there. I did that and then at the ---VERY END--- of installations in which I try this, it always says something like: 

When I choose to install the bootloader in the small meg partition, hda1, it says Executing Failed to install GRUB /dev/sda1 etc.

I've tried everything. This past time, I didn't make a small partition and it supposedly successfully installed, but I get that notorious Error 18. Is there any way to successfully install the GRUB bootloader to save this installation, or do I have to redo the whole thing again?

I've tried everything I can think of, even telling it to install to hda0, which didn't work also.

I've tried the following disk setups on my 500 gig ATA/IDE 7200 rpm Seagate hard drive:

hda0
hda1 16.8 MB ext3 /boot
hda2 499 GB ext3 /
hda3 1GB swap

I have even tried letting it do the whole thing automatically, same thing.

I've run out of ideas. Anyone know what to do? Thank you very much in advance.

---

### Post by sandman887 on 2007-11-09
Hi, 

After searching the boards for a solution, and not finding one, I decided to make this topic. After posting this topic, I found this one: [http://ubuntuforums.org/showthread.php?t=607047]("http://ubuntuforums.org/showthread.php?t=607047")

I found this link provided by Bulldog 
[http://users.bigpond.net.au/hermanzone/p15.htm#18]("http://users.bigpond.net.au/hermanzone/p15.htm#18"), and am going to try making a 20 GB partition and install xubuntu 7.10 there and see if it works. I'll post my results.

Thanks

---

### Post by sandman887 on 2007-11-09
I have solved the problem. I created a 20.3 GB ext3 partition with the mount point of / and turned on the Bootable flag.

I put the rest of the space as /home

Thanks to Bulldog for his excellent link he posted in the other topic.

---

