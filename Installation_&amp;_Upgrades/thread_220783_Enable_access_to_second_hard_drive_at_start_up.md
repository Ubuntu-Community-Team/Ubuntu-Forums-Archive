---
title: "Enable access to second hard drive at start up"
date: 2006-07-22
forum: Installation &amp; Upgrades
---

### Post by afbase on 2006-07-22
I installed a second hard drive to my ubuntu server not too long ago.  I gave it an access folder and everything worked out just fine.  I could write and read files to and from it.  

I noticed when I restarted my server today that the second hard drive was not accessible at startup.  I had to manually enable the access through the disk Control Panel through gnome.  

I was wondering how to enable my 2nd hard drive at start up.
my second hard drive is
/dev/hdd
the access folder is:
/home/clinton/secondharddrive


If possible I would prefer terminal commands since I putty to my server 99% of the time unless i really don't know what i'm doing

---

### Post by bLaDeY on 2006-07-22
Now I am a very basic user although was am proud to say everything I did recently what CLI which almost bought tears to my eye's.

To get it appearing all the time at startup edit ie vi /etc/fstab and place something along the lines of:

/dev/hddx        /home/clinton/secondharddrive           ext3    suid,dev,exec   0       0

x being partition, see fdisk -l for more info.

I hope this helps and I hope it didn't break anything.

Cheers

---

### Post by afbase on 2006-07-22
> **bLaDeY said:**
> Now I am a very basic user although was am proud to say everything I did recently what CLI which almost bought tears to my eye's.

To get it appearing all the time at startup edit ie vi /etc/fstab and place something along the lines of:

/dev/hddx        /home/clinton/secondharddrive           ext3    suid,dev,exec   0       0

x being partition, see fdisk -l for more info.

I hope this helps and I hope it didn't break anything.

Cheers

Many thanks my friend!!!!

CLI is my preferred way.  I putty to my server

---

### Post by bLaDeY on 2006-07-22
Great to hear it worked :)

CLI I have found is the best way, it's all very well using the GUI but you don't really learn too much, knowing someone who know's linux well does help a lot also :-D 

As that old saying goes you learn from your mistakes.

---

