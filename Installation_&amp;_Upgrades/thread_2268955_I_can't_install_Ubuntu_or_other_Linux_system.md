---
title: "I can't install Ubuntu or other Linux system"
date: 2015-03-12
forum: Installation &amp; Upgrades
---

### Post by bashful2 on 2015-03-12
Hello.
So I got into programming and I want to switch to Linux now, so at first I tried Ubuntu, Linux Mint and none of them works... 
Everytime I boot up and start the Linux I get this error:

> [COLOR=#333333][FONT=Lucida Grande]cannot mount /dev/loop0 on //filesystem.squashfs[/FONT][/COLOR]

I was searching through Interrnet, but I couldn't find anything :( Please help me!

---

### Post by Bashing-om on 2015-03-12
bashful2; Hi ! Welcome to the forum.

We work to find the reason why.

For starters, what is the hardware you are attempting to install onto ?
Is this a UEFI based system, and if so, what are you setting for the boot parameter in that firmware ?

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by bashful2 on 2015-03-12
Sorry, I totally forgot about that, I just went to dxdiag in Windows 7 (cause that's what I'm using atm) 

[img]http://i.imgur.com/z8qkWKO.png[/img]

I hope it's enough information, if you need anything else just let me know :)
I booted from USB stick, but before, on my laptop it worked well, cause I was using some Ubuntu, or I should say trying before, and it worked perfectly, so I guess it's something with my computer.

---

### Post by Bashing-om on 2015-03-12
bashful2; Well.

Fairly descent little box there. Windows 7, maybe UEFI maybe not. Let's get some direct info that will relate to installing ubuntu:
Boot the liveDVD to terminal:
post back -Between Code Tags - the output of terminal commands:
```

sudo fdisk -lu
sudo parted -l

```
code tag tutorial:
[http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](http://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)
with the "supposition" presently that the partitioning scheme is legacy (MBR) and that Windows  occupies the 4 (max allowed) partitions.
Then we see what to do.

[INDENT][INDENT]what to do, OH what to do
[/INDENT][/INDENT]

---

### Post by bashful2 on 2015-03-12
Okay.
I have another dumb question, which terminal should I use?
When I boot up Linux installation should I choose "Install Linux" and when I get that screen with this error:

```
cannot mount /dev/loop0 on //filesystem.squashfs
```

Type those commands:

```

sudo fdisk -lu
sudo parted -l

```

in that black screen where I have the error message, or there's another terminal that I can use? 

Sorry for my dumbness, I'm just a newbie in Linux, so sorry.

---

### Post by Bashing-om on 2015-03-12
bashful2; Hey !

You are "here", here there is no such thing as " a dumb question ". It is dumb not to ask.

OK, how to get a terminal in the liveDVD:
When you boot the liveDVD(USB) you get a screen to choose "try ubuntu" or "install ubuntu"
choose "try ubuntu" -> loads to a GUI desktop.
At this desktop, key combo ctl+alt+t yields a terminal.
Issue the requested commands in this terminal, - the FireFox browser is fully functional; copy and paste the results between code tags.

[INDENT][INDENT]up up and away
[/INDENT][/INDENT]

---

### Post by bashful2 on 2015-03-12
Well... You actually miss understood what I mean... 
The problem is this; when I boot up Ubuntu(Or any Linux distro in that matter) and click the button "try ubuntu" I get a black screen with the error message

```
cannot mount /dev/loop0 on //filesystem.squashfs
```

So there's no way I can get to the GUI and even to the terminal and I want to solve it, that's what I was asking... Therefore I can't install or even try ubuntu.

---

### Post by Bashing-om on 2015-03-12
bashful2; Oh, sorry .

That may be a couple or few reasons.
1) UEFI system and is 'secure boot" enabled ?
2) Did you verify the .iso and the disk integrity ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Got to have a firm foundation.

---

