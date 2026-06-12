---
title: "Error 17: Cannot Mount Selected Partition"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by Sherlock19 on 2008-05-07
Hello i will do my best explaining my situation

I have a self built computer...and i am working on dual booting with ubuntu and windows xp pro.  I have ubuntu installed on my 250 gig hard drive and xp on my 160 gig hard drive. Here is where the problems come into play

when i turn on my pc a black and white screen comes up asking me which operating system i want to boot to, either ubuntu(three different modes?) or xp... i try to boot off of ubuntu and as soon as i try that i get Error 17: Cannot Mount Selected Partition, but if i boot my pc onto my ubuntu live cd, and choose the last option of the live cd when they come up which is something like boot from first disk... i can start up ubuntu perfectly fine with no problems.

I am curious to findout  why i cant just boot when i turn my computer on, i dont want to have to boot my computer from my live cd everytime. Thank you in advance for all of your help.

---

### Post by Pumalite on 2008-05-07
[http://users.bigpond.net.au/hermanzone/p15.htm#17](http://users.bigpond.net.au/hermanzone/p15.htm#17)
Post:
sudo fdisk -l
cat /boot/grub/menu.lst

---

### Post by panda726 on 2008-05-07
I may not be able to help you, but I have run into such issues.  I believe you may find the cause has to do with issues with drive/kernel specifications.  The last time I had this trouble, however, I got either error 21 or 22 after solving 17, the former referring to partition not found.  Try finding the *grub* drive/partition you want and edit for one boot to use hd0,1 (follow the prompts for how to do this; they are there, and do work.)  See below for the main entry in my grub menu for ubuntu.

```
title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=bdc88dda-3c9c-4675-9fca-ca8d5c0a86d0 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

```

This refers to the second partition on my first drive.  To find out where your partition is, get to the command prompt and search for "vmlinuz".  Yes, that is a Z.  Sorry, I will have to let you find your way to the command prompt and search command on your own.

If making this for a single boot works, then hardcode it into your menu.lst for grub.  This is in /boot/grub if you have ubuntu up and running.

---

### Post by Sherlock19 on 2008-05-07
i am sorry but i am unaware of what you would like me to do... i typed this part in my terminal:

sudo fdisk -l
cat /boot/grub/menu.lst

now i have a bunch of information in my terminal and i dont know where to go from there. would you like me to copy and paste what i have in my terminal now?

this response was to pumalite, panda i am going to respond to yours separatly simply because i havent read it yet.

---

### Post by panda726 on 2008-05-07
To edit the grub boot options for one boot, you do it from the grub menu.  See Pumalite's link for an excellent detailed description of all the errors.

Try rebooting your computer, and at the grub menu, press "c" for a command line.  Enter "find vmlinuz" (without quotes, of course!), and note the hdx,y that comes up.  Then exit to your grub menu and press "e" to edit your boot command for one boot.  Edit the root line to look like mine, replacing the two numbers with the ones appropriate to your system.  When that is done, try booting.  IIRC, use "b" to boot.

If this works, you can then edit your menu.lst ("gksudo gedit /boot/grub/menu.lst") from ubuntu, or it can be done via command line or from the grub command prompt.  The first is probably easiest, and you will find the entry at the bottom of the file.  Make a backup copy first ("cd /boot/grub"  "sudo cp menu.lst menu.lst.old")  This way if you make a mistake, you have something to come back to.

Tor

---

### Post by Pumalite on 2008-05-07
Copy and paste the output of my commands here.

---

