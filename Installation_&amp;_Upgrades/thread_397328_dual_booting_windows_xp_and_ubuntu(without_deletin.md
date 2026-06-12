---
title: "dual booting windows xp and ubuntu(without deleting everything off the harddrive)"
date: 2007-03-30
forum: Installation &amp; Upgrades
---

### Post by Electric.Koolaid on 2007-03-30
Hi everyone. I really would like to install ubuntu onto my dell inspiron b130, but i would like to 

keep my windows xp. I would like to do it without wiping everything off my harddrive, 

because i have some important programs that i do not want 2 get rid of such as my itunes 

because it will erase everything off of my ipod. I am not 2 familiar with messing around with a 

cpu's harddrive. If anyone has a newb easy way of installing ubuntu onto a dell laptop without 

deleting everything plz help me. Thanks in advance!!:popcorn:

---

### Post by matikz on 2007-03-30
Run defrag on your hdd to clean it up. Then boot the the LiveCD and manually resize the Partition to make room for your swap and linux partition.

---

### Post by Electric.Koolaid on 2007-03-30
thanks 4 the help. So are u saying that i will have 3 partions 1 for existing  xp another for ubuntu, and then another 4 the swap?

---

### Post by RaZer0r on 2007-03-30
jups, the swap partition should be more or less 2x the size of your ram
so if you'd have 512mb ram, make the swap partition 1gig (or more, but unneccesairy)
to not run into any problems you should make your linux partition more or less 7 gb.

Be aware, you wont be able to reach your linux partitions in linux without an external program!

---

### Post by confused57 on 2007-03-30
Maybe this will help:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

or see the first link in my signature

---

### Post by Electric.Koolaid on 2007-03-30
thanks 4 all the help everyone im gonna try this and hopefully everything goes well

---

### Post by Electric.Koolaid on 2007-03-31
im still having one problem. When i boot uuntu from the live cd, i chose the option to use the largest amonut of space that was left of my hddand as ubuntu was installing it said that there was not root chosen and that i should choose it in the partition menu how can i fix this?

---

### Post by FlyingIsFun1217 on 2007-03-31
> **Electric.Koolaid said:**
> im still having one problem. When i boot uuntu from the live cd, i chose the option to use the largest amonut of space that was left of my hddand as ubuntu was installing it said that there was not root chosen and that i should choose it in the partition menu how can i fix this?

I have found the easiest way to install it (and the method I used on two computers, including the one I'm using now) is to just choose the hard drive you want to install to, select the option that resizes and uses the extra space, and let it install.

This method will most likely work for you, and will probably be the easiest ;)

FlyingIsFun1217

---

### Post by confused57 on 2007-03-31
> **Electric.Koolaid said:**
> im still having one problem. When i boot uuntu from the live cd, i chose the option to use the largest amonut of space that was left of my hddand as ubuntu was installing it said that there was not root chosen and that i should choose it in the partition menu how can i fix this?
It may be this bug in the live cd installer:
[http://ubuntuforums.org/showpost.php?p=1700787&postcount=29](http://ubuntuforums.org/showpost.php?p=1700787&postcount=29)

---

### Post by Electric.Koolaid on 2007-03-31
this information helps alot. I have one final question. I have backed up my hard drive. If i leave the back up file on my harddrive after deleting everything off will the back be deleted as well?

---

### Post by confused57 on 2007-03-31
> **Electric.Koolaid said:**
> this information helps alot. I have one final question. I have backed up my hard drive. If i leave the back up file on my harddrive after deleting everything off will the back be deleted as well?
The best way to have a relatively "safe" backup is on separate media from the hard drive, e.g. cd, USB device(external hd or pendrive) or possibly a separate partition.  You're just resizing your Window's partition to create free space to install Ubuntu, any programs or whatever will still be with your Window's install...you're not really deleting anything.  You can't backup installed programs, but you can back up any install .exe files for programs that you may have stored on your pc.

Before you start installing Ubuntu, you might want to boot the live cd, open a terminal(Applications---Accessories---Terminal), post the output of:
```
sudo fdisk -l
```
the -l is a small "L"
This will show any hidden partitions on your hard drive that you might need to be aware of...such as pc manufacturer utilities or recovery partitions.

Also, I always recommend anyone to burn a copy of the Super Grub Disk(500 kb download) before installing Ubuntu:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

In case your Ubuntu is from Ship-it and you didn't burn an iso yourself, here's how to burn an iso(for the SGD):
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by Electric.Koolaid on 2007-04-01
I succesfully dual booted my cpu. It wasnt as difficult as i thought it was. I am actually 

on ubuntu right now. My next task is to install beryl, which hopefully will be just as easy. 

I will post my method later today so that hopefully anyone else who is having problems 

will be able to do a dual boot.

---

### Post by confused57 on 2007-04-01
> **Electric.Koolaid said:**
> I succesfully dual booted my cpu. It wasnt as difficult as i thought it was. I am actually 

on ubuntu right now. My next task is to install beryl, which hopefully will be just as easy. 

I will post my method later today so that hopefully anyone else who is having problems 

will be able to do a dual boot.
Thanks for the update.

It's really pretty easy, the apprehension of trying something new is a little unsettling...you did it the right way, read & make a plan, then go for it...glad it all worked out.

---

