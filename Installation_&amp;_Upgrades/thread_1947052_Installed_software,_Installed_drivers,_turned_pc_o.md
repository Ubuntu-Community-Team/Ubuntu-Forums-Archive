---
title: "Installed software, Installed drivers, turned pc off and reinstalled everything (Read"
date: 2012-03-26
forum: Installation &amp; Upgrades
---

### Post by liamhale on 2012-03-26
Hello Guys,
well i am new to Ubuntu, i have spent almost my entire sunday installing this etc.
i used the usb installer, but i used my 500gb external hard drive for this, a prompt did come up on first installation saying remove installation things now but my computer would not run Ubuntu without putting it in, so i have to keep it in in order to use it.
it doesn't run an entire wipe and then full installation evertime, but deletes everything i have done prevously and it is like stating from scratch again.
i cannot acces my hard drive under 'my computer' either, it just has my 80gb internal drive witch appears to have the system files already in there.
if i unplug my hard drive the screen will just go black.

thats everything i have tried and i have got nowhere, is there anyone able to help me?


thanks


Liam

---

### Post by darkod on 2012-03-26
Hold on.
How did you try to install, using an ubuntu cd or using a prepared bootable usb stick?

What are you trying to install as destination, the internal hdd or external usb hdd?

---

### Post by liamhale on 2012-03-26
> **darkod said:**
> Hold on.
How did you try to install, using an ubuntu cd or using a prepared bootable usb stick?

What are you trying to install as destination, the internal hdd or external usb hdd?
i installed using a hard drive, and the destination must be the hard drive, although it states it is using the 80gb hard drive witch is my internal hard drive?

---

### Post by oldfred on 2012-03-26
Lets see what is installed where, with external plugged in run the boot info script. Darko has the curent version in his signature and it has some instructions, but there is a newer git/test version that has some fixes.

You can directly download it:
The git/testing version has some fixes:
```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

Or you can download this gui app that can run the script and may be able to make some repairs.
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by liamhale on 2012-03-26
i am a begnner, so i am guessing i paste that into terminal?
well i tryed that but  nothing happens i will try to refrase my problem.

when i boot up i get the original boot menu with run ubuntu from usb
etc etc
i always click boot ubuntu from usb

then codes pop up and it loads BUT, everything i have done from the previous session is lost and it ut just a new version everytime, so if i will log into a website and click remember me, it will not because it would have deleted the cookie.

also, if my hard drive is not plugged into my pc it will not run ubuntu, it will just have a black page.

but then, my computer thinks the hard drive with everything installed is my internal hard drive, this isnt the case because my pc will freze and go black with out my external, but looking through after start up i cannot find the external hard drive as a option anywhere, it is asif the computer cannot see it

ths is the best i can explain, i am a newbie on this so everything even therminal and the things that may seem obvious to click i donot know.

thanks everyone for trying to help and being so kind, i know you guys dont get pad for it and i realy apprechiate it.

---

### Post by darkod on 2012-03-26
Are you trying to install onto the same ext hdd you are booting the install process from?

---

### Post by liamhale on 2012-03-26
> **darkod said:**
> Are you trying to install onto the same ext hdd you are booting the install process from?
no, when the option to install to what hard drive i only have the option to install to my internal hard drive, so it is suposed to be intalling to my internal drive?

---

### Post by oldfred on 2012-03-26
You should be able to just copy & paste commands into terminal. That will generate a results.txt or if using Boot-Repair it creates a link to an online copy of the results.txt plus some extra info that Boot-Repair creates.

But it sounds like you have not installed but just have the installer or liveCD/USB version on your external?

Post this if you cannot get boot script running. Again copy & paste into a terminal as the l is an el not a 1 one or capital I.
```

sudo fdisk -lu
```

---

### Post by liamhale on 2012-03-26
> **oldfred said:**
> You should be able to just copy & paste commands into terminal. That will generate a results.txt or if using Boot-Repair it creates a link to an online copy of the results.txt plus some extra info that Boot-Repair creates.

But it sounds like you have not installed but just have the installer or liveCD/USB version on your external?

Post this if you cannot get boot script running. Again copy & paste into a terminal as the l is an el not a 1 one or capital I.
```

sudo fdisk -lu
```
i have copied and pasted this into terminal and it has came out with results for my external hard drive, but i do not get what these results are for and what i should do with them?

---

### Post by darkod on 2012-03-26
Post the content of the created results.txt file. That will show more details.

I have re-read your posts and I still don't understand what are you trying to do and what is going on. In post #5 you say "you get the original boot menu with run ubuntu from usb".

Do you mean the Try Ubuntu option? In that case it is not even installed, or you are continuing to boot from the usb hdd. If you already installed it onto the internal hdd, try booting without the usb hdd, you don't need it any more.

If you do keep booting the Try Ubuntu live mode, of course everything you did in the last session is gone, it is not designed to remember it.

What exactly happens if you boot without the usb hdd? Blank screen? Any error messages? Windows boots directly (if you have windows on the computer)?

---

### Post by liamhale on 2012-03-26
> **darkod said:**
> Post the content of the created results.txt file. That will show more details.

I have re-read your posts and I still don't understand what are you trying to do and what is going on. In post #5 you say "you get the original boot menu with run ubuntu from usb".

Do you mean the Try Ubuntu option? In that case it is not even installed, or you are continuing to boot from the usb hdd. If you already installed it onto the internal hdd, try booting without the usb hdd, you don't need it any more.

If you do keep booting the Try Ubuntu live mode, of course everything you did in the last session is gone, it is not designed to remember it.

What exactly happens if you boot without the usb hdd? Blank screen? Any error messages? Windows boots directly (if you have windows on the computer)?


Right, i have installed Ubuntu, on the startup screen i have installed it and i have appeared to install it to my 80gb internal hard drive.

although, when i take my 500gb external hard drive out my pc will freeze and not work, so the files must be on my external hard drive

my bootup screen when taking my external hard drive out is just a black screen with a white underscore (when the computer is ready to do something but nothing is happening)


i have used the code 'sudo fdisk -lu' and this is what is came out with

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000ba395

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   154222591    77110272   83  Linux
/dev/sda2       154224638   156301311     1038337    5  Extended
/dev/sda5       154224640   156301311     1038336   82  Linux swap / Solaris

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x20ac7dda

This doesn't look like a partition table
Probably you selected the wrong device.

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   ?  3224498923  3657370039   216435558+   7  HPFS/NTFS/exFAT
/dev/sdb2   ?  3272020941   930513678   976730017   16  Hidden FAT16
/dev/sdb3   ?           0           0           0   6f  Unknown
/dev/sdb4        50200576   974536369   462167897    0  Empty

Partition table entries are not in disk order

i was also asked to post the results.txt contents, but i am very new to this, i cannot currently even find how to open applications once installed, i have been trying to do this for the past two hours, anyone could tell me how i have searched on dash home but cannot find them, and i have definately installed them

---

### Post by darkod on 2012-03-26
OK, we are getting somewhere. You definitely have it installed on /dev/sda, the 80GB disk.

Unplug your ext hdd and use the computer like that. Forget for the moment that it doesn't really boot. If you boot with the usb hdd it just goes into live mode and you are going in circles.

The blank screen with cursor sounds like video driver issues. On top of the threads list in the forum, there are "stickies" threads. One of them is for video issues. Go through the instructions there and see if you can make your computer boot and work without the usb hdd.

---

### Post by liamhale on 2012-03-27
starting again today to try and fix this, none of these are working
i can make a short video on my problems if that would help you understand my issues?

---

