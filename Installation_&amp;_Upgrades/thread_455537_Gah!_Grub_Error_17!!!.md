---
title: "Gah! Grub Error 17!!!"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by anonymous131 on 2007-05-26
I have this old Compaq Presario 5010 US Desktop PC (Under the 5000 Series) and I'm trying to put xUbuntu on it because it only has a Pentium III Processor and 128MB of RAM. Unfortunately, I'm having issues here. When I was finished installing xUbuntu, I got Grub Error 18 on startup. I didn't know what the problem was, so I reinstalled xUbuntu. This time, when I started the computer, I got Grub Error 17 and I still am. People say that it's a BIOS error on the internet and that it can't recognize the OS so I thought about upgrading the BIOS. Should I upgrade the BIOS or what? What am I doing wrong? By the way, the hard drive is a Western Digital 40GB hard drive. Oh yeah, and I'm trying to install the alternate installation of xUbuntu 7.04, (Feisty Fawn)

---

### Post by merlinus on 2007-05-26
Grub error 17 : Cannot mount selected partition
This error is returned if the partition requested exists, but the filesystem type cannot be recognized by GRUB.

How did you format the linux partition?  If you can boot from a live cd, go to a terminal and enter:

sudo fdisk -l  

(l is a lowercase L)

This will give you the partitions and formats.

-merlin

---

### Post by confused57 on 2007-05-26
Here's a description of grub error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

A bios update would probably work, but if you don't want to do that then try creating a separate /boot partition of approx 100 mb at the very beginning of the hard drive...you'll need to select manual partitioning.  Another possibility would be to create a smaller root partition of approx 8 Gb then a larger /home partition and a swap partition at the end of the drive.

I have seen other posters report a grub error 17, but Super Grub Disk reported it as error 18...don't know if that's the situation in your case.

---

### Post by anonymous131 on 2007-05-26
This is what came up:

[IMG]http://i198.photobucket.com/albums/aa140/anonymous131/snapshot1.png[/IMG]

Now What?

---

### Post by merlinus on 2007-05-26
It looks to me that, because you installed xubuntu twice, you have redundant partitions -- 2 /swap, 2 /.

If you do not have any data worth saving, why not start all over again.  When you get to the partitioning screen, tell it to use the entire disk.  Then you can have one large partition for / and one about 1.0G for /swap.

Before that, though, enter df -h in a terminal.  It will show you the various sizes and usages of everything.

Good luck!

-merlin

---

### Post by anonymous131 on 2007-05-27
This is how I reinstalled it:
[IMG]http://i198.photobucket.com/albums/aa140/anonymous131/DSC00003.jpg[/IMG]
[IMG]http://i198.photobucket.com/albums/aa140/anonymous131/DSC00004.jpg[/IMG]
[IMG]http://i198.photobucket.com/albums/aa140/anonymous131/DSC00005.jpg[/IMG]

When xUbuntu was done installing, I started up the system but this time got Error 18.
What am I doing wrong?!?!?!
(Please give me detailed instructions)

---

### Post by merlinus on 2007-05-27
I know you did this earlier, but try it again:

sudo fdisk -l

This will show details about your partitions.

It may be that since you are booting from the knoppix live cd, it is making another /swap partition for its own uses, in addition to the one used by Ubuntu.

Then:

blkid

and please post the results.

It may be that the UUIDs for your partitions got changed around when you re-installed, and therefore are listed incorrectly in /etc/fstab and perhaps even in /boot/grub/menu.lst

So post those as well.

-merlin

---

### Post by confused57 on 2007-05-27
There are other bios related solutions in this link for error 18:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18)

---

### Post by anonymous131 on 2007-05-31
FINALLLYYYYYY!!!! After a long, hard week of fighting Linux, I got it to work. You guys were right about the BIOS not recognizing the whole hard drive, so I kept on making partitions that boot first and made everything else swap space. That didn't work. Then, I tried to install Knoppix, which didn't work. Then I tried to install Damn Small Linux, which didn't work, then I tried to install Puppy. That did not work. I was just about to give up but then I thought of putting in my really old hard drive (only 700 mbs), as the master, and the 40gb hard drive as the slave, so I could boot something simple like DSL, or Puppy, and have the 40GB as swap space. Right? I turned on the computer, and there it was! Xubuntu loaded! So much satisfaction. This has made my day. Thanks for your help guys.

---

