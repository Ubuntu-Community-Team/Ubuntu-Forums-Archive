---
title: "Invalid Partition Table."
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by gpost3 on 2011-08-09
Hi Guys,

I made a boo boo the other day. I did a DD on my disk (sdc) which contains only one ntfs partition (sdc1). I did that to zero out the MBR to remove grub but I ended up zeroing first 13 Megabytes (yes Megabytes) instead of first 512 bytes which removed the partition table for the ntfs partition (sdc1). :KS

Now I am trying to get the partition to come back. I cannot read or write to this ntfs partition because there is no partition table. I know my data is still there. I used test disk with deeper search but test disk couldn't find anything. How do I go about this? I also tried gpart but no partitions were found.

---

### Post by Mark Phelps on 2011-08-11
It's going to take time, and ultimately cost money, but if you really want your NTFS stuff back, suggest you do the following:
1) Disconnect the hard drive from the current PC
2) Go to a working MS Windows PC, download and install the trial version of GetDataBack for NTFS from Runtime Software.
3) Hook up the hard drive to THAT PC
4) Run the GetDataBack app in the deepest discovery mode -- best to let it run overnight.
5) Check the results and see if it found what you need.
6) To do the actual recovery, you will have to purchase the app and activate it.

---

### Post by YesWeCan on 2011-08-11
> **gpost3 said:**
> I made a boo boo the other day. I did a DD on my disk (sdc) which contains only one ntfs partition (sdc1). I did that to zero out the MBR to remove grub but I ended up zeroing first 13 Megabytes (yes Megabytes) instead of first 512 bytes which removed the partition table for the ntfs partition (sdc1). :KS
BTW you would have wiped your partition table using 512 too. The PT starts at the 447th byte.

---

### Post by gpost3 on 2011-08-14
Thank you I realized my mistake. Boot sector is 446 bytes and the remaining is partition table. 

I have another question. How do I go about copying the entire windows partition into an external drive and booting it from there? I tried this the right way using DD by copying only the first 446 bytes, leaving the rest as it is to keep the partition table information and hard drive signature the same then copying all the windows files onto the new external drive partition. Windows boots up, loads but then gives an error and halts saying that boot device cannot be read.

---

### Post by gpost3 on 2011-08-14
common guys bump, how do I copy windows partition to external drive so that windows 7 can actually load from there?

---

### Post by oldfred on 2011-08-14
It is my understanding that windows will only boot from an internal hard drive. Not sure how they check but they do.

Ubuntu does not care and will boot from just about anything the BIOS says is bootable and with some effort somethings that BIOS does not let you boot.

---

### Post by gpost3 on 2011-08-14
See that's the interesting bit because I actually did get my Windows 7 to "Boot" from external hard drive. The boot manager is there, Windows starts to load, the logo shows up but half way through halts with an error. I think what I will try now is take out my external hard drive, put it inside my computer then boot. Hang on I'll report back.

---

