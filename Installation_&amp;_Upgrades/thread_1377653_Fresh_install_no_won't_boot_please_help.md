---
title: "Fresh install no won't boot please help"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by theuke on 2010-01-10
OK, So i have been working on this for at least a day 

Fresh install of ubuntu 9.10 and Mint. they don't want to boot
LiveCD works nice just when i do the install it doesn't like it anymore

im not totally sure why its doing it but here are a few things that i have noticed
well after the install it just says 

no bootable dvice -- insert boot disk and press the any key (wheres the any key)

I have 1 HD (ide) and 1 cd drive in this computer for some strange reason the ide hard drive shows up as /dev/sda when i run the install it points the install to /dec/mapper/pdc ......
I have tried installing the boot loader to hd0, dev/sda, /dec/mapper/pdc ....... 

ANY IDEAS PLEASE PEOPLE

---

### Post by darkod on 2010-01-10
If it shows /dev/mapper/blabla then the disk was earlier used in raid setup and these remained settings get picked up by 9.10.
Since you have only one hdd and not using raid, boot with ubuntu cd, Try Ubuntu option, and in terminal execute:
sudo apt-get remove dmraid

Do the install once more after that, it's best to do another clean install if you don't mind.

---

### Post by theuke on 2010-01-10
Another install won't kill me i think im up to like 5 or 6 Im not sure if my motherboard is telling it i have raid I went over bios yesterday and was checking for that option nothing. I Will run this command and see what happends

edit 
Just to make sure do the sudo command then reinstall while running the same live session

---

### Post by darkod on 2010-01-10
> **theuke said:**
> Another install won't kill me i think im up to like 5 or 6 Im not sure if my motherboard is telling it i have raid I went over bios yesterday and was checking for that option nothing. I Will run this command and see what happends

edit 
Just to make sure do the sudo command then reinstall while running the same live session

I think you are allowed to restart but just in case simply hit the install icon on the live desktop.

---

### Post by theuke on 2010-01-10
I get an error of " the exta filesystem creation in partition #1 of scsi1 (0,0,0) (sda) failed

---

### Post by theuke on 2010-01-10
> **theuke said:**
> I get an error of " the exta filesystem creation in partition #1 of scsi1 (0,0,0) (sda) failed

NEVER MIND for some strange reason it just started working who knows but thanks darkod

---

### Post by Sef on 2010-01-10
> I get an error of " the exta filesystem creation in partition #1 of scsi1 (0,0,0) (sda) failed

How are you partitioning?

---

### Post by theuke on 2010-01-10
i was trying to let the partitioning happen by its self

---

### Post by llawwehttam on 2010-01-10
Depending on how big your hard drive is I recommend a 30GB - 50 GB / partition. A 5 -8GB swap partition and the rest as /home unless of course you hard drive is less than 120GB as that will leave you little space. If you have a separate /home partitio if you ever mess the ubuntu install up and need to reinstall you won't lose your documents.

---

### Post by theuke on 2010-01-10
wIll i got it to work but it was by the hiram boot cd send it to the correct place to boot 

when i realized that i nuked the drive with a format utility did the nodmraid option on the startup and used the sudo apt-get removed dmraid and its finally booted correctly now its time to do some updates

---

