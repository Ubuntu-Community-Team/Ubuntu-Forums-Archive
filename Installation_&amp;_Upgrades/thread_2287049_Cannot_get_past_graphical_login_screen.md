---
title: "Cannot get past graphical login screen"
date: 2015-07-16
forum: Installation &amp; Upgrades
---

### Post by keith45 on 2015-07-16
First, apologies for my total ignorance of ubuntu. I'm pretty good on (Windows) computers, so offered to do a favour for a neighbour, and now I'm regretting it...

She has a compact desktop computer with ubuntu installed. She says that after an update last week her login no longer works.

I've searched around here and found how to toggle to the command line interface. From there I can login to her user account with no problem at all. But from the graphical interface it throws me to a purple screen with nothing on it except the ubuntu logo and version number.

I know I'm not alone with this problem, but I don't understand what the advice in other threads is actually telling me to do. So I need somebody to explain real slow...

Version number shows as 12.04 on graphical screen, but 14.04.2 on text screen.

I'm sure you'll want to know more, but I don't know what...

Thanks
Keith

---

### Post by howefield on 2015-07-16
Could be a kernel update borking the graphics card drivers.

Can you boot from a previous kernel ? (If you don't get a grub screen on boot up, pressing the shift key should bring it up).

---

### Post by dino99 on 2015-07-16
*****Version number shows as 12.04 on graphical screen, but 14.04.2 on text screen.********

first that is a bit strange; its either 12.04 or 14.04.2 but not both
is it ubuntu or xubuntu or .... ?
is it a normal installation or into a virtual host ?  

can you post here the output of:  > cat /etc/apt/sources.list

---

### Post by keith45 on 2015-07-16
@howefield
eventually found my way to something that said grub screen - it presented me with two previous versions. Tried them both - both gave flashing, unusable screen display. Looked like a login screen, but wouldn't stay still long enough

@dino99
seemed strange to me too, but I'm only reporting what I see
no idea about xubuntu - it says ubuntu when it starts up
I can't believe this installation is anything as complex as a virtual host - this is a little old lady who sends emails and that's about it

Your cat command gave me several screens of fast moving text - how can I get that off a non-working computer and on to here?

---

### Post by tokyobadger on 2015-07-17
[quote="keith45"]Your cat command gave me several screens of fast moving text - how can I get that off a non-working computer and on to here?[/quote]
One way would be to use a live environment (USB or CD/DVD), mount the hard drive where the Ubuntu partition is and then copy-paste the file.
It would also be good to see the partition table if you say there are previous versions

---

### Post by keith45 on 2015-07-17
The output from the cat command doesn't appear to be writing to a file...

And how do I show you the partition table?

Sorry, I meant it when I said I'm ignorant of Ubuntu...

1. If you use the live environment you don't need to use cat - mount the hard drive by clicking on the disk icon in the task-bar on the left, navigate to /etc/apt/sources.list double click on it select all text and copy (right click), paste it in your reply using code tags ```
your pasted text here
```

2. To show the partition table:
   (a) open a terminal and show us what you get from sudo fdisk -l (password is ubuntu all lower case) - you can copy from the terminal and then paste as in #1 above
   (b) open gparted (click the Ubuntu symbol top-left, select Apps - the A symbol at the bottom of the pop-up - scroll down to the "G" section), note what you see in gparted and then describe it in your reply

Everyone was a beginner once :-)

Regarding your instructions for the partition table - how can I select the text from the terminal view in order to copy it?

sorry, tried to paste a screenshot - that didn't work.

I see 3 partitions:
/dev/sda1 ext4 227.03GB (11.98 used) boot
/dev/sda2 extended 5.86GB
/dev/sda5 linux-swap 5.86GB (508KB used)

Hey, one small step for you guys, but an enormous leap for me!

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty universe
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ trusty-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu trusty partner
# deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu trusty main
deb-src http://extras.ubuntu.com/ubuntu trusty main

deb http://security.ubuntu.com/ubuntu trusty-security main restricted
deb-src http://security.ubuntu.com/ubuntu trusty-security main restricted
deb http://security.ubuntu.com/ubuntu trusty-security universe
deb-src http://security.ubuntu.com/ubuntu trusty-security universe
deb http://security.ubuntu.com/ubuntu trusty-security multiverse
deb-src http://security.ubuntu.com/ubuntu trusty-security multiverse

```

---

### Post by howefield on 2015-07-17
> **keith45 said:**
> this is what I see in gparted...

When you wish to post an image, please use the paperclip icon which you'll find in the posting window toolbar.

Presumably you dragged your image into the browser triggering a Firefox bug rendering your image as a huge amount of base64 code.

---

### Post by keith45 on 2015-07-17
Is this better...?
[ATTACH=CONFIG]263248[/ATTACH]

---

### Post by tokyobadger on 2015-07-19
[quote="keith45"]eventually found my way to something that said grub screen - it  presented me with two previous versions. Tried them both - both gave  flashing, unusable screen display. Looked like a login screen, but  wouldn't stay still long enough[/quote]
Since the partition table just shows one install (unless there are multiple disks) I guess the "two previous versions" refer to kernels? Can you confirm and also let us know which kernel version numbers you see in the grub menu (under advanced).

The /etc/apt/sources.list looks as if it should be correct as all references to 10.10 (maverick) are commented by a # and the uncommented lines (active) point to trusty (14.04) - maybe someone sees something there that I don't.

Can you tell us more about the hardware - CPU, RAM and graphics? This might help diagnose the flashing screen you mentioned.

Alternative: I don't usually suggest this, but a reinstall might be faster in the circumstances - using the livecd/usb back up the owner's data and then install 14.04

---

### Post by keith45 on 2015-07-20
CPU: Intel Atom D525 1.80Ghz x 4
RAM 2.0GB
Graphics: Intel IGD x86/MMX/SSE2

I was considering the reinstall option too - would that leave any installed apps in place?

I don't really know how to read the grub screen, but it's showing "Ubuntu, with Linux 3.2.0 - 41 - generic", then the same again with "(Recovery mode): tagged on the end

Then it says "Previous versions". When I click on that it two entries like the above, but with version numbers 3.0.0 - 29 and 2.6.38 - 15.

I don't know whether they're versions or kernels - I really don't know the difference :?

I've been trying to back up the user's data - two questions:
1) should it be enough just to copy the Home/<username> folder?
2) how do I override the permissions to allow me to copy it from the live environment?

---

### Post by ubfan1 on 2015-07-20
Yes to 1) -- /home/<username> contains all the user's data (careful of case, Ubuntu is case sensitive, and the leading / is good to use).
On 2), guessing your using a GUI (nautilus?) to copy the files, which starts with the privs of the user (ubuntu) you start it with.  I use the command line for this sort of thing, so my advice may be off.  Starting from a terminal (ctrl-alt-t), issue the "gksudo nautilus) command to start it with root privs.  Not sure if the gksudo will work, but try it.    
  Now on the reinstall -- With only 2G of ram, if you can't get Ubuntu to work right, try Lubuntu 14.04 (a long term support version) instead of Ubuntu.  I was updating Ubuntu on my old 2G HP until it just wouldn't run anymore, but Lubuntu still worked fine.  Show your neighbor what Lubuntu looks like and how it runs from a live media, and see if it's acceptable.  I bet she'd prefer to stick with what she's using, but it may just not run right anymore.

---

### Post by keith45 on 2015-07-21
gksudo didn't work, but I looked elsewhere on this forum and found the command line procedure, so user files are now safely backed up

Is there a way to list installed apps so that I can get the system back to the way it was after reinstalling ubuntu?

---

### Post by howefield on 2015-07-21
```
apt-mark showmanual >installed-pkgs.txt
```

Will put a text file in your home folder which can be used to aid reinstall.

By the way,did you back up the /home folder as well as user files ? Perhaps you do not need to, but may want some user configuration files.

---

### Post by keith45 on 2015-07-21
Thanks everyone - the reinstall worked! And all the user files, settings and installed apps survived, so didn't even need my carefully created backup.

I think I'll have a very happy neighbour when I take her computer back tomorrow - trouble is, she'll now think that I'm an expert.

Thanks for all the patient explanation.

---

