---
title: "Grub won't load...not normal grub problem, plz help!  =\"
date: 2006-03-04
forum: Installation &amp; Upgrades
---

### Post by dreborn on 2006-03-04
I am installing Ubuntu AMD64 DVD iso.  I have two hard drives:

1.  SATA drive with WinXP
2.  IDE drive for storage (that has two partitions ready for Ubunutu)

I can get through the install fine but when it comes to installing GRUB i start having issues.  My mobo, ASUS A8N-32, makes you select your default hardrive and for me thats my SATA drive with XP on it.  If i install GRUB to MBR of the SATA drive it won't find the linux install on the IDE drive.  If i install GRUB on the IDE drive my computer will never find it cause it won't even look on the ide drive during boot up.

My i would love to install GRUB just on the IDE but i don't know how that would work.  I know there must be a way to install GRUB on the SATA drive and then tell it to look at the IDE drive for linux.  

I really don't want to go into the BIOS and change the default hard drive everytime i want to boot into Linux...

Lastly, i was having trouble finding the correct location of my hard drives...would my sata drive be sd0, sda?  

I need some help...  =\

---

### Post by dreborn on 2006-03-04
any ideas?

---

### Post by dreborn on 2006-03-04
ok so i got grub to install on the mbr of my sata drive and it actually runs when i boot the computer but now i have a bigger problem.  it is not configured correctly so i cannot even boot into windows!

i know i have to edit the grub file so it looks for windows on my sata drive and it looks for linux on the second partition of my ide drive....but how??

please help, thanks

---

### Post by zXen on 2006-03-05
Just out of interest how did u get Grub installed on your HD?

---

### Post by dreborn on 2006-03-08
during the install i chose to install grub manuall at "dev/sda" 

worked like a charm...until i had to boot.  finally figured it out so i can boot into windows and ubuntu but it was a challenge.  =)

now i need to figure out how to install the ati drivers in ubuntu...sigh...

---

