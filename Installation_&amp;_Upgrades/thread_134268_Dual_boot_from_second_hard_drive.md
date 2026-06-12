---
title: "Dual boot from second hard drive"
date: 2006-02-21
forum: Installation &amp; Upgrades
---

### Post by reidypeidy on 2006-02-21
I've been wanting to try linux for awhile, so i finally decided to try Ubuntu because of the great things i heard about it. I ordered the free cds and decided to install on my Windows desktop since it had a large second hard drive. 

I start the installation and add a partition in the 2nd drive and install onto it. First I installed Grub to the master boot record but i would only get an "Error 22" everytime. So i booted into DOS and reset my MBR and tryed again. 

Next I tryed a boot manager called OSL2000, but it couldn't find the partition I made. Next I tryed installing LILO to the second hard drive, but the windows bootloader (NTLDR) couldn't detect it. I figured I would have to configure the boot.ini file to tell the bootloader that there is a bootable partition on my second hard drive, but I don't know how. 

I tryed bootpart for windows but i couldn't get it to work, then I tryed the dd command in the Live CD but I don't have permission to access my partition (BTW it's hdb2, if that matters). 

I really want to try Ubuntu and reformatting my hard drives is not an option. Please help in any way you can. If I was specific enough, tell me what other information you need to help me.

---

### Post by uopjohnson on 2006-02-21
Lets foucus on GRUB as that is your best bet.
You want to install grub onto the mbr of the primary hard drive /dev/hda.  Is this what you are doing?  When do you get the error 22?  on boot?  on install?  
Are you trying to install GRUB on your own, or are you using the ubuntu installer?

---

### Post by reidypeidy on 2006-02-21
When i get the error 22 message it's when I install it using the Ubuntu installer to hda, the "master" and I restart the computer. It goes through the BIOS the says GRUB Error 22, then freezes. I guess it's because the booter and the OS are on two different hard drives. Is there any way for Grub to boot if it's on my second hard drive? or is that not a good idea?

---

