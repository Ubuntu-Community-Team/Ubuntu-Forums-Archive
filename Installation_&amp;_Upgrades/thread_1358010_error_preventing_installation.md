---
title: "error preventing installation"
date: 2009-12-17
forum: Installation &amp; Upgrades
---

### Post by libihero on 2009-12-17
my friends laptop crashed and he asked me to put ubuntu on it
when i try to install i get an error popup that says:
input/output error on read on /dev/sda
when installing his laptop showed no operating system present

---

### Post by dhavalbbhatt on 2009-12-17
Did you make sure the CD you've burnt is OK? Check the CD for defects, check its MD5 checksum. Also make sure you can run the LiveCD environment.

---

### Post by libihero on 2009-12-17
it is free of defects and it does run on live cd :(

---

### Post by libihero on 2009-12-20
bump.. :(

---

### Post by raymondh on 2009-12-20
> **libihero said:**
> 
when installing his laptop showed no operating system present

In liveCD and in Live Session, access a terminal and type

```
sudo fdisk -l
```

That will give you a picture of what his HD contains.

If the other OS is still listed, and still in live session, type in terminal

```
sudo apt-get remove dmraid
```

Close terminal, try to install.  See if the partitions/OS are now recognized in step 4.  If yes, continue install.

---

### Post by darkod on 2009-12-20
When it crashed it might have left the hdd in some wierd error situation. If you don't need to extract data, and if you want only Ubuntu installed on it as only OS, boot with the ubuntu cd, Try Ubuntu option, open Gparted (in System-Administration) and delete all the partitions on the hdd. THIS WILL DESTROY ALL DATA!!!
Click on the big green tick mark button in Gparted toolbar to execute those commands.
Then again boot with the cd, select Install Ubuntu and see how it goes.

If you DO need to get some data from it, before doing the above, boot with Try Ubuntu option and see if you can copy what you need from the hdd to external usb hdd or similar.

---

### Post by libihero on 2009-12-21
now its even more jacked up
i tried turning it on this morning, and most the time it turns on but the screen is black
sometimes the screen will come on but the mouse doesnt work
i pressed alt-f2 to run gparted, and there are no file systems detected :S

---

### Post by darkod on 2009-12-21
> **libihero said:**
> now its even more jacked up
i tried turning it on this morning, and most the time it turns on but the screen is black
sometimes the screen will come on but the mouse doesnt work
i pressed alt-f2 to run gparted, and there are no file systems detected :S

What has Alt-F2 got to do with anything? I don't understand. Can you specify did you try booting from the ubuntu cd with Try Ubuntu option as suggested?
You already know the laptop crashed, you can't expect it to work right?

---

### Post by libihero on 2009-12-21
i did alt+f2 because the mouse wasnt being detected when i did the "try ubuntu"
the hard drive used to be detected, but i think my repetative attempts to install and just mess around has made it worse
now it does not even detect the hard drive, mouse, and sometimes screen

---

### Post by libihero on 2009-12-21
all in all:
hard drive used to be detected in bios
i prolly messed it up when i was trying to get the installation to work
now hard drive is not detected in bios :(

---

### Post by libihero on 2009-12-22
now the screen is completely black every time i try to boot the live cd
i tried putting the "safe graphics mode", but that didnt help at all

---

### Post by libihero on 2009-12-29
bump...
is it hopeless?

---

