---
title: "cant boot, says kernel not found"
date: 2006-08-26
forum: Installation &amp; Upgrades
---

### Post by omega_c on 2006-08-26
Ok, two days ago, i booted up, tried to watch a dvd, ended up listening to music and playing games or something. ubuntu worked fine.

i shut it off normally, didn't use it yesterday, booted it up today, and it doesnt work.

I haven't installed any updates since the video player (vlc?) that i installed on wednesday. I booted up and shut off at least twice perfectly fine since then. I can't connect to the internet for at least two days using my ubuntu laptop, but i'd like some help.....

It says that the kernel isn't there...

help?


[I]**EDIT:** I just booted it up again, and it came up with another message. Still white text on black screen.
Ubuntu 6.06.1 LTS [computername] tty1

[computername] login:[/I]

Ok, so I typed in my username, and hit enter. Came up with:

*Password:*

But i can't type anything in there. I hit any key except enter and nothing happens. I hit enter, it says incorrect password, and starts over...HELPPPP

---

### Post by matthew on 2006-08-26
Okay, first off I have good news for you. Your computer is booting.

Enter your username.
When prompted for your password, type it. It will not show up as you do, this is a security feature and is standard in the text interface. Hit enter.

Once that is done and you confirm it works tell us what you see.

---

### Post by omega_c on 2006-08-26
ok, i did that

it comes up with a screen about how there's no warranty and ubuntu is free software, then it says 'module is unknown' and goes back to the screen i first posted.

---

### Post by matthew on 2006-08-26
> **omega_c said:**
> ok, i did that

it comes up with a screen about how there's no warranty and ubuntu is free software, then it says 'module is unknown' and goes back to the screen i first posted.Sorry, I'm a little unclear. Do you mean that the login was successful and now you have something that looks like this?```
login@computername:~$
```

---

### Post by omega_c on 2006-08-26
no

i log in, it scrolls thru about a paragraph of text and then says

module is unknown

and comes up with tthe login screen again.

---

### Post by matthew on 2006-08-26
Okay, that's not so good, but we can try some things. It's possible this can be fixed, although I might have to leave before the process is complete...

Can you boot in recovery mode? When you first start the computer and it says "loading grub" or something like that, hit "esc" and it will take you to a menu. Select the option that says something like this```
Ubuntu, kernel 2.6.15-26-386 (recovery mode)
```and see if it will boot to a command prompt like this```
login@computername:~#
```

---

### Post by omega_c on 2006-08-26
ok, i did that, and now it came up with what you said, except it's

root@computername (the rest is the same)

---

### Post by omega_c on 2006-08-26
Help please!

I'd like to find out whats wrong...

---

### Post by omega_c on 2006-08-27
ok, it's getting late where i am...

can someone please please please help me?

If linux is totally screwing up, i'd at least like to get all of my files off it...

help me please!

---

### Post by matthew on 2006-08-27
> **omega_c said:**
> ok, i did that, and now it came up with what you said, except it's

root@computername (the rest is the same)
Sorry I was gone...it was the middle of the night here and I desperately needed sleep. It's Sunday afternoon now so in between playing with my kids I'll try to stop in here and take a look.

What this means it that there is a problem with a module that is loading when booting normally, but it's not something that affects the base installation. That's good, it means with some work it should be able to be repaired and, more importantly, it means you don't have a hardware problem causing the difficulty.

Please use the following command to list the contents of the file /etc/modules and we can take a look and see if we can discover which one is causing the problem```
less /etc/modules
```Hit the "q" key to exit back to a command prompt when you're done reading the file's contents.

For comparison, here is what mine looks like. Bear in mind, yours will be different because you don't have the same hardware as I have.```
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
mousedev
psmouse
sbp2
sr_mod
acerhk
snd-intel8x0

```

---

### Post by omega_c on 2006-08-27
Ok, i did that, and here's what it came up with:

> # /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
sbp2
sr_mod
/etc/modules (END)

---

### Post by tseliot on 2006-08-28
> **omega_c said:**
> ok, i did that

it comes up with a screen about how there's no warranty and ubuntu is free software, then it says 'module is unknown' and goes back to the screen i first posted.

Boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Update the system:
```
aptitude update && aptitude upgrade
```

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by omega_c on 2006-08-28
there isn't one... (vesa driver)

it comes up as:


> Select the desired X server driver.

apm
ark
ati (which is highlighted)
chipes
cirrus
cyrix
fbdev

**EDIT:** Eh, sorry, im an idiot... I didn't realize you could scroll down.
Just so you know, i'm running ubuntu on a compaq presario 1700t laptop. I haven't added any hardware or anything.

---

### Post by omega_c on 2006-08-28
Doesn't work... Came up with the same error message as the first time.

> "module is unknown"

after i tried to sign in under

> computername login:

So... Basically it's back to the same thing as before. I hit enter each time it came up with a question (15 to 20) then typed reboot, it rebooted... and yeah.

---

### Post by omega_c on 2006-08-29
c'mon folks... Help me out please. I have files that i dont want to lose on that computer

---

### Post by jerry_c on 2006-08-30
Hey, omega,

I lost my kernel, too, when my boot partition got wiped out, along with grub. I was able to reinstall it using just the Live/install CD. Here's what I did:[http://ubuntuforums.org/showthread.php?p=1431609#post1431609]("http://ubuntuforums.org/showthread.php?p=1431609#post1431609") You may not need to deal with grub, but if you do, it's in there, too. 

Good luck.

---

### Post by matthew on 2006-08-30
> **omega_c said:**
> c'mon folks... Help me out please. I have files that i dont want to lose on that computerI'm sorry. I'm in and out this week--just had a ton of work dropped on me.

From looking at the /etc/modules file all seems okay. I think what tseliot said should work once we get the vesa module installed for you. It is installed by default so I'm not sure why it's not there for you now.

Boot again in recovery mode then do this:```
aptitude install xserver-xorg-driver-vesa
```If that works (and it really should) then try tseliot's advice again and it should work. I'll try to check in again later today and see where you're at.

---

### Post by omega_c on 2006-08-30
ok, i did what you said, matthew, and then what tseliot said to do.

It came up with a new error message.


> * Checking root file system...
/dev/hda1 has been mounted 30 times without being check, check forced.
/dev/hda1:
Inode 1279321is in use, but has dtime set.  FIXED.
/dev/hda1: Inode 1279321 has imagic flag set.

/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
     (i.e., without -a or -p options
                                  [[COLOR="Red"]fail[/COLOR]]
[COLOR="Red"]*[COLOR="Black"]An automatic file system check of the root filesystem failed.[/COLOR]
* [COLOR="Black"]a manual fsck must be forformed, then the system rebooted.[/COLOR]
* [COLOR="black"]This fsck can be performed in maintenance mode.[/COLOR]
* [COLOR="black"]Please note that the root filesystem is currently mounted read-only[/COLOR]
* [COLOR="black"]The fsck should only be performed while the root filesystem is mounted read-only. However, the command to remount it read-write is:[/COLOR]
* [COLOR="black"]     # mount -n -o remount, rw /
[/COLOR]
[/COLOR]
root@computername:~# and not foundenance shell, press control-D

Ok.... Yeah. Sorry for being irritable but.... Well, nobody likes having to worry about their files and stuff.

Quick question: Is it possible to get my files off of this computer, say if i bringing it to someones house/work who has ubuntu...or windows? (It's a laptop)

Thanks

---

### Post by tseliot on 2006-08-30
> **omega_c said:**
> ok, i did what you said, matthew, and then what tseliot said to do.

It came up with a new error message.




Ok.... Yeah. Sorry for being irritable but.... Well, nobody likes having to worry about their files and stuff.

Quick question: Is it possible to get my files off of this computer, say if i bringing it to someones house/work who has ubuntu...or windows? (It's a laptop)

Thanks
Let's try to fix the hard disk:
when that warning about your hard disk shows up, type:
```
fsck -c /dev/hda1
```

then press Y whenever it asks you. It might take some time.


BTW: to transfer your files to another computer you could use a livecd and move the files through SAMBA or a USB storage medium.

---

### Post by omega_c on 2006-08-30
Ok, so i just booted it up again, and i didn't press escape fast enough. It came up with the last error message i posted.

Then i tried to boot it up in recovery mode. It did the same thing.

I tried what you said, and it came up with a list:

> Emergency help:

- p                    Automatic repair (no questions)
- n                    Make no changes to the filesystem
- y                    Assume "yes" to all questions
- c                    Check for bad blcoks and add them to the  badblockk list
- f                    Force checking even if filesystem is marked clean
- v                    Be verbose
- b superblock         Use alternative superblock
- B blocksize          Force blocksize when looking for superblock
- j external_journal   Set location of the external journal
- l bad_blocks_file    Add to badblocks list
- L bad_blocks_file    Set badblocks list
root@computername:~#

I typed Y after the root@computername:~#

It came up with:

> root@computername:~# Y
bash: Y: command not found
root@computername:~#

Did i not type it in where I was supposed to?




I have an external hard drive, with more than enough space to transfer all my files. How do i do that?

Of course, I want to get ubuntu running, but I'd like to have a backup.

---

### Post by tseliot on 2006-08-30
> **omega_c said:**
> Ok, so i just booted it up again, and i didn't press escape fast enough. It came up with the last error message i posted.

Then i tried to boot it up in recovery mode. It did the same thing.

I tried what you said, and it came up with a list:



I typed Y after the root@computername:~#

It came up with:



Did i not type it in where I was supposed to?
My bad. "c" should be uppercase.

therefore the right command is:
```
fsck -C
```



> **omega_c said:**
> I have an external hard drive, with more than enough space to transfer all my files. How do i do that?

Of course, I want to get ubuntu running, but I'd like to have a backup.
Boot in the livecd plug in the external hard disk then drag and drop the files

---

### Post by omega_c on 2006-08-30
Ok, i followed your instructions, and once it was done, it said the file system had been modified, and to reboot linux. I rebooted, and it came up with the very first warning screen that i got...](*,) 

"module is unknown"

Egh....

Any other ideas?

---

### Post by tseliot on 2006-08-30
> **omega_c said:**
> Ok, i followed your instructions, and once it was done, it said the file system had been modified, and to reboot linux. I rebooted, and it came up with the very first warning screen that i got...](*,) 

"module is unknown"

Egh....

Any other ideas?

I would like to be more of help but I'm afraid that I can't, since I can't see what appears before "module is unknown" (so as to know which module is unknown).

You could try typing:
dmesg > boot.txt

then:
nano boot.txt

so as to see the list of events which take place at boot.


However I suggest you to use the livecd, browse your hard disk from there and transfer the files to your external hard disk (USB, I hope).

---

### Post by omega_c on 2006-08-30
Yes, my external hard disk is USB, but the problem is I actually just tried to boot using the livecd, and it wont boot. It gets to the menu, and looks like it's loading fine, but then a ton of error messages pop up... I think the disk is scratched.

I'll try what you said, and post what happens.

By the way, i think i posted the first error message on the first page of this topic...

---

### Post by omega_c on 2006-08-30
ok, i did that, and it came up with a huge list....

I wish i could just start over, but i can't even boot up to get my files off.

---

### Post by tseliot on 2006-08-30
You can backup the files from the command line.

Try this:

Boot in Ubuntu as usual (you will get to the command line)

then plug in the USB cable of your external hard disk

wait a few seconds

type:
```
fdisk -l | grep sda
```

and you will get something like:
```
Disk /dev/sda: 506 MB, 506462208 bytes
/dev/sda1               1          61      489951   83  Linux
```

You will see that your usb device is /dev/sdax (e.g. /dev/sda**1**, /dev/sda**2**, etc.)

Let's assume that your device is /dev/sda1

type
```
sudo mkdir /media/usb
```

(don't worry if it already exists)

then if your external hard disk is fat32, type:
```
sudo mount -t vfat /dev/sda1 /media/usb
```

else, if it is NTFS:
```
sudo mount -t ntfs /dev/sda1 /media/usb
```

Ok now you have mounted your external hard disk.


Copy the files you need to your external hard disk:

if you want to copy all your files to your external hard disk:
create a folder on your usb drive:
```
sudo mkdir /media/usb/backup
```
then copy the files:
```
sudo cp -R /home/your_username/* /media/usb/backup/
```
NOTE: you have to replace "your_username" with your username

When it finishes unmount your usb drive:
```
sudo umount /dev/sda1
```

NOTE: it's "umount" and not "unmount"

Unplug the USB cable.


enjoy

---

### Post by omega_c on 2006-08-31
well, it works up until it wants to create new directories

I added my own directorys by plugging the drive into another (windows) computer.

But when i tried to do one of the final steps, it said the drive was read-only. I cant figure out how to change that. I reconnected it to the windows computer, and tried to change it in the properties, but i didn't see a box...


I think that's the only reason why it's not working.

How do i change it from read-only to...whatever?

---

### Post by tseliot on 2006-08-31
> **omega_c said:**
> well, it works up until it wants to create new directories

I added my own directorys by plugging the drive into another (windows) computer.

But when i tried to do one of the final steps, it said the drive was read-only. I cant figure out how to change that. I reconnected it to the windows computer, and tried to change it in the properties, but i didn't see a box...


I think that's the only reason why it's not working.

How do i change it from read-only to...whatever?

you could do this:
```
cd /media/usb
```
```
sudo chmod -R a+rw *
```

---

### Post by omega_c on 2006-08-31
didn't work... it still says it's read-only.

---

### Post by tseliot on 2006-08-31
> **omega_c said:**
> didn't work... it still says it's read-only.

what about:
```
sudo chown -R your_username /media/usb
```

NOTE: replace your_username with your username

---

### Post by omega_c on 2006-08-31
ok, i did that. it waited a second, and then came up with a second commandline. tried to copy the files over using the code that you had posted before, but it just went down to the next line, and waited for me to type something...no commandline, nothing.

erg...

---

### Post by tseliot on 2006-09-01
> **omega_c said:**
> ok, i did that. it waited a second, and then came up with a second commandline. tried to copy the files over using the code that you had posted before, but it just went down to the next line, and waited for me to type something...no commandline, nothing.

erg...

Perhaps it was copying the files, therefore the blinking cursor might mean that you need to wait.

---

### Post by omega_c on 2006-09-03
I checked the folder, and it didn't look like anything had been copied.

Ok, here's my *new* problem.

I finally managed to download and burn a livecd. I booted up using that CD, it booted up fine, etc. I hooked up my external hard drive, and went looking for my files.

/home only had one folder, /ubuntu.

I opened that, and it came up with /desktop (a folder)

I clicked on that, and now showing are /examples (a folder) and an icon, "install"

In /examples, there's the interview with nelson mandela, some music, logos, etc.

But my files aren't there. Is it because I'm booting from the CD?

What can I do?

So, I'm here:

/home/ubuntu/desktop

---

### Post by omega_c on 2006-09-08
little help, please...

let me explain myself better.

I booted up using the livecd, and when i got to the desktop, i went looking for my files, searches didn't turn anything up, and i couldn't find it in the c-drive folders...


help!

---

