---
title: "Ext3-ext4 upgrade massive failure"
date: 2010-03-21
forum: Installation &amp; Upgrades
---

### Post by hihihi100 on 2010-03-21
Hiya:
 
The laptop I regularly use is out of use after having tried to upgrade from ext3 to ext4, following the instructions that can be found at [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)
 
namely, Step 2: Upgrading to Ext4
 
Well, the first step was done without problems, but when I reached "Mount your filesystem", the problems started:
 
When typing
 
[COLOR=#c20cb9]sudo[/COLOR] [COLOR=#c20cb9]mount[/COLOR] [COLOR=#660033]-t[/COLOR] ext4 [COLOR=#000000]/[/COLOR]dev[COLOR=#000000]/[/COLOR]XXXX [COLOR=#000000]/[/COLOR]mnt
 
what appears is:
 
UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
 
Stupid me, I did nothin but jump to the next step:
 
gksu gedit [COLOR=#000000]/[/COLOR]mnt[COLOR=#000000]/[/COLOR]etc[COLOR=#000000]/[/COLOR]fstab
 
Where I only got a fully white screen with no written text at all, instead of the menu that should have appeared, as can be seen on that webpage.
 
However, after running Gparted again, it showed the extension as EXT4, not EXT3, so I thought the system had automatically upgraded. Then I proceeded to boot the system, and this is where the massive failure appeared: After seeing the Ubuntu logo for a while, the system directs me to a blank screen with the message:
 
Mount of filesystem failed.dc5123-ec01-4438-8bd6-cb85bb080f87A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try.
root@hihihi-laptop:#
 
So I type CTRL-D:
 
mountall start/startingfsck from until-linux-ng 2.16
/dev/sda1: One or more block group descriptor checksums are invalid. FIXED
/dev/sda1: Group descriptor 0 checksum is invalid
/dev/sda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
(i.e., without -a or -p options)
swapon: /dev/disk/by-uuid/72edafb7-a004-4a19-b4aa-26d18c5ae43a: swapon failed device or resource busy
mountall: swapon /dev/disk/by-uuid/72edafb7-a004-4a19-b4aa-26d18c5ae43a 949terminated with status 255
mountall: Problem activating swap: /dev/disk/by-uuid/72edafb7-a004-4a19-b4aa-26d18c5ae43a
mountall: fsck / 947 terminated with status 4
mountall: Filesystem has errors: /
init: mountall main process (945) terminated with status 3
Mount of filesystem failed.
A maintenance shell will now be started.
CONTROL-D will terminate this shell and re-try
root@hihihi-laptop: #
 
AFAIK, the system, when I turn on the laptop, somehow recognizes thatEXT4 is present (I write this because a line appears reading EXT4, not EXT3 as before this unsuccessful intent to upgrade, but, at the same time, I didnt upgrade all of it, cause other parts of the OS still use EXT3, hence, this massive failure. Im a noob, so correct me if Im wrong.
 
So, please, I need to know what do I have to write in that blank screen as root@hihihi-laptop: user to fully upgrade to EXT4 and be able to use the laptop again.
 
If I press CTRL-D for a second time, the same message appears, and againfor a 3rd time, a 4th...
 
Cheers

---

### Post by hihihi100 on 2010-03-21
I have absolutely no idea what have I done, or typed, but, after, somehow, running fsck, the system seems to be fully operational, and Gparted shows the extension as EXT4.
 
I had the chance to see how the OS corrected nearly 2000 corrupted files
 
Now, does this mean EXT4 is fully operational in my laptop? or could it be that it only shows EXT4 as the default, but in reality running EXT3?
 
No data loss so far
 
Tips please

---

### Post by Directive 4 on 2010-03-21
here's a tip

this step.

**Step 1: Upgrade your existing Ubuntu**



miss it out next time.

try instead to do a fresh install, 
this should solve all problems.

---

### Post by 98cwitr on 2010-03-21
so why did you upgrade to ext4 in the first place?

---

### Post by phillw on 2010-03-21
Hi,

if you pop over to [http://forum.phillw.net/viewtopic.php?f=4&t=8](http://forum.phillw.net/viewtopic.php?f=4&t=8)

Head to the part with

```

e2fsck -y /dev/DEV
```

For you, from the LiveCD run

```

e2fsck -y /dev/sdxy

```

Where sdxy is the disk number and partition number, e.g. sda1, sda5, sdb1 etc. that you have converted from ext3 --> ext4

Once done, reboot into your hard drive and issue the df -HT to confirm you have gotten ext4

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-21
well, if I run ubuntu 9.10 as my infobox says, I dont see how I can upgrade... 10.04 anyone?

Thx phil... after typing

e2fsck -y /dev/sdxy
I get: 

/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

Given my previous miscalculation that led to that massive error, I wouldnt like to experience more problems with my laptop... should I continue?

---

### Post by phillw on 2010-03-21
> **hihihi100 said:**
> Hiya:
 
The laptop I regularly use is out of use after having tried to upgrade from ext3 to ext4, following the instructions that can be found at [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)


For others following, [http://forum.phillw.net/viewtopic.php?f=4&t=8](http://forum.phillw.net/viewtopic.php?f=4&t=8)  is based upon [https://ext4.wiki.kernel.org/index.php/Ext4_Howto](https://ext4.wiki.kernel.org/index.php/Ext4_Howto)  with the little tweak for the error message. I wrote it as I converted my disks over.

Regards,

Phill.

---

### Post by phillw on 2010-03-21
> **hihihi100 said:**
> well, if I run ubuntu 9.10 as my infobox says, I dont see how I can upgrade... 10.04 anyone?

Thx phil... after typing

e2fsck -y /dev/sdxy
I get: 

/dev/sda1 is mounted.  

WARNING!!!  Running e2fsck on a mounted filesystem may cause
SEVERE filesystem damage.

Do you really want to continue (y/n)?

Given my previous miscalculation that led to that massive error, I wouldnt like to experience more problems with my laptop... should I continue?

NO !!!!!


/dev/sda1 is mounted.  


You **MUST** run it from LiveCD, with /dev/sda1 un mounted

Phill.

---

### Post by hihihi100 on 2010-03-21
k, k, thx

---

### Post by tgalati4 on 2010-03-21
If you had a working system with ext3, then why the urge to update to ext4?

We sometimes feel that we must upgrade to the lastest-and-greatest, but sometimes the performance gains are minimal.  And there is risk.  Backups are essential, and clean installs are usually better for updating an existing system.

So, you were able to recover in this instance, but how do you know which of those 2,000 files are critical, and have they really been fixed?

If your disk drive was a consumer drive (and not an enterprise drive), the drive heads get toasty when writing lots of files, continuously.  That happens when you do an install, or a conversion.  So if your drive is older, or hot inside it's enclosure, then such a conversion can be risky.  We expect reliability, but certain disk-intensive actions can lead to failures.  Is this a fault of linux?  Ext4? Linux allows you to stress a disk drive in ways that wouldn't happen with a preinstalled operating system.

What was the make and model or your disk drive?

---

### Post by hihihi100 on 2010-03-22
tgalati;

not sure if this is the information you are asking me:

toshiba mk3263gs

In a previous post I asked about both advantages and disadvantages about upgrading from EXT3 to EXT4, so far I have received 2 answers, affirming that the speed increases, the main reason why I am upgrading. Yours is the first not-so-positive judgment

And, according to you, should I revert back to EXT3?

Phil:

after running

sudo umount /dev/sda1

I get

umount: /: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8 or fuser(1))

So I run:

fuser -m /dev/sda1

to get:

dev/sda1:            2944rce  2959rce  3191rce  3192rce  3225rce  3243rce  3245rce  3255rce  3258rce  3272rce  3276rce  3281rce  3282rce  3284rce  3292rce  3293rce  3309rce  3310rce  3335rce  3370rce  3371rce  3372rce  3374rce  3377rce  3378rce  3379rce  3381rce  3384rce  3386rce  3388rce  3392rce  3394rce  3395rce  3399rce  3401rce  3404rce  3406rce  3407rce  3408rce  3419rce  3428rce  3432rce  3434rce  3447rce  3451rce  3477rce  3485rce  3486rce  3512rce  3566rce  3593rce  3594rce  3607rce  3616rce  3628rce  3630rce  3632rce  3634rce  3636rce  3676rce  3680rce  4424rce  4430rce  4682rce  9022rce  9025rce  9027rce  9035rce  9193rce

Im lost here

---

### Post by phillw on 2010-03-22
Hi,

Boot from the LiveCD, Select 'Try Ubuntu without altering my Computer' mode, then get a terminal session going.

Issue ```
mount | grep sda
```

If you see /dev/sda1 listed, issue the ```
sudo umount /dev/sda1
``` command again.

I'm slightly puzzled, as with the LiveCD running you should be able to unmount the partition, even if it were to get automatically mounted, as this is required for doing an installation etc.

If you'd like details of the changes that ext4 brings over ext3, you can pop over to [https://ext4.wiki.kernel.org/index.php/Ext4_Howto#EXT4_features](https://ext4.wiki.kernel.org/index.php/Ext4_Howto#EXT4_features)

As you've converted, we believe, to ext4 all I want to ensure is that the drive fsck's okay and that it is in ext4 now.

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-22
I did the livecd thing you recommended and, after doing things I cannot exactly recall (I apologize), I booted the system. Now, every time I turn on the laptop, a line appears:

/dev/sda1 on / type ext4 (rw,relatime,errors=remount-ro)

It then redirects me to a menu of different Ubuntu 9.10 versions and, after choosing, not the last one (20), but number 19, I can log in without problems. As a matter of fact, I am writing this reply from the laptop in question

I apologize for my lousy computing skills, but Im gonna ask for more help...

---

### Post by phillw on 2010-03-22
Hmm, I'm not in 9.10 atm. Give me a few minutes to reboot.

Phill.

---

### Post by phillw on 2010-03-22
Hi,

I dropped over to 9.10 (Long time since I've been in 9.10 ;-) )

```
sudo apt-get remove --purge 2.6.31-20-*
```Then

```
sudo update-grub
```Go get the *20 version again,

```
sudo apt-get install linux-image
sudo update-grub
```That will get the *20 and update grub.

You should then be good to go with *20 :-)

Regards,

Phill.

---

### Post by tgalati4 on 2010-03-22
I apologize for my rant.  No you shouldn't go back to ext3, but you may have to reinstall anyway if you experience instability.

If this is a new drive (Toshiba, 2.5", 5400 rpm, 320 GB, SATA), then you might consider breaking it in before really using it.  Some drives need some burn-in time, otherwise they experience strange problems--such as what you are experiencing.

You can search the net for various break-in procedures (writing 0's to the drive, badblocks, surface scans, Ultimate Boot CD tests, etc).  If you experience problems during these burn-in cycles, then it's time to replace the drive under warranty.

So, I'm inclined to think that it's a hardware problem, not a filesystem problem.  Although you can search for ext4 bug reports, to see if others have had similar problems.

I would back up my data, wipe the disk, run a few burn-in cycles, then do a fresh install with ext4.  Then keep a log of any weirdness you experience after that point.  If you still have problems, then file a warranty claim.

---

### Post by hihihi100 on 2010-03-22
More problems:

after doing what Phil told me to do (I pasted the commands, reinstalled the 20*, booted the system when told to, this is what I read when turning on the laptop:

Boot (hd 0,0) ext4   50dc 5123-ec01-4438-8bd6-cb85bb080f87

Error13: invalid or unsupported executable format

Press any key to continue

So, again, I have to use 19* (Ubuntu 9.10 Kernel 2.16.31-19 generic)

Thinking about a fresh reinstallation...

tgalati:

yes, thats the HDD in the laptop, I dont believe my knowledge is enough to start what you suggest me to do, I may just delete it all, fresh reinstall and leave it on EXT3

---

### Post by phillw on 2010-03-22
Hi,

that looks like a UUID problem. UUID is the "way of the future", but is still causing problems in the present.

Hold fire before you re-install, I'm going to ask for advice on this one.

If it is a re-install, format the disk as ext4 to begin with ;-)

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-22
I dont know if this may be of help:

when running:

sudo update-grub

I get:

Searching for GRUB installation directory ... found: /boot/grub
Searching for default file ... found: /boot/grub/default
Testing for an existing GRUB menu.lst file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...

Just how important is "splash image"?

After a short period of time, it goes on:

Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-18-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-server
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-server
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-server
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-server
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-12-server
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-server
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

---

### Post by phillw on 2010-03-22
Hmm,

could you post the result of

```
grub-install -v
```

Thanks,

Phill.

And, yes, the penny has finally dropped here .... grub legacy... ext4 ... Doh :-(

---

### Post by hihihi100 on 2010-03-22
no, thanks to you for all the help:

grub-install (GNU GRUB 0.97)

---

### Post by phillw on 2010-03-22
> **hihihi100 said:**
> no, thanks to you for all the help:

grub-install (GNU GRUB 0.97)

[start rant]
Exceedingly deep sigh,

As to how someone could write a How To for ext3 --> ext4 without stipulating you need grub2 is beyond me.
[end rant]

Why I did not check, is my own fault & I apologise.

The good news ? It's quite easy, painless & does not need a re-install 
:popcorn:

[https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202](https://help.ubuntu.com/community/Grub2#Upgrading%20to%20GRUB%202)

By the way, just to re-itterate, none of this is your fault. You trusted a 'How To', and it was wrong.

Get grub2 on, do the old [sudo update-grub] and see if we get *20 back playing :-)

Once *20 is running, I'll give you a dead easy way to get rid of the old ones, but having seen how to get rid of *20, I think you'll suss that one out ;-)

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-22
Hope you have a lot of patience with this issue:

When typing:

apt-get update

I get:

E: Could not open lock file /var/lib/apt/lists/lock - open (13: Permission denied)
E: Unable to lock the list directory

I could do the second mentioned step (sudo apt-get install grub-pc) 

without problems, it automatically deleted the previous version of GRUB

but I am not prompted to press any OK, it just stops there

---

### Post by phillw on 2010-03-22
E: lock is frequently caused if you have Synaptics Package Mananger open

That's the one via System --> Administration

If you have it open, it will fail with that error if you try to do something from the command line.

Regards,

Phill.

---

### Post by phillw on 2010-03-22
> **hihihi100 said:**
> Hope you have a lot of patience with this issue:

When typing:

apt-get update




```
 sudo apt-get update 
```

Sorry, i missed it
:popcorn:

---

### Post by Slim Odds on 2010-03-22
> **hihihi100 said:**
> 
Just how important is "splash image"?


Almost everyone gets this. You don't get it ONLY if you install a **custom** splash image.

> 
After a short period of time, it goes on:

Found kernel: /boot/vmlinuz-2.6.31-20-generic
Found kernel: /boot/vmlinuz-2.6.31-19-generic
Found kernel: /boot/vmlinuz-2.6.31-18-generic
Found kernel: /boot/vmlinuz-2.6.31-16-generic
Found kernel: /boot/vmlinuz-2.6.31-15-generic
Found kernel: /boot/vmlinuz-2.6.31-14-generic
Found kernel: /boot/vmlinuz-2.6.28-16-server
Found kernel: /boot/vmlinuz-2.6.28-16-generic
Found kernel: /boot/vmlinuz-2.6.28-15-server
Found kernel: /boot/vmlinuz-2.6.28-15-generic
Found kernel: /boot/vmlinuz-2.6.28-14-server
Found kernel: /boot/vmlinuz-2.6.28-14-generic
Found kernel: /boot/vmlinuz-2.6.28-13-server
Found kernel: /boot/vmlinuz-2.6.28-13-generic
Found kernel: /boot/vmlinuz-2.6.28-12-server
Found kernel: /boot/vmlinuz-2.6.28-12-generic
Found kernel: /boot/vmlinuz-2.6.28-11-server
Found kernel: /boot/vmlinuz-2.6.28-11-generic
Found kernel: /boot/vmlinuz-2.6.28-3-rt
Found kernel: /boot/vmlinuz-2.6.27-14-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... doneI think that you need a couple more kernels    :D

---

### Post by phillw on 2010-03-22
> **Slim Odds said:**
> Almost everyone gets this. You don't get it ONLY if you install a **custom** splash image.

I think that you need a couple more kernels    :D

Slim, we've only just realised that the ***** who wrote the ext3 --> ext4 proceedure the OP has followed did not ensure that they were on Grub2. Things are tough enough ;-)

(I have a real small bit of 'fine print, sub-section a, paragraph b' on mine --> [http://forum.phillw.net/viewtopic.php?f=4&t=8](http://forum.phillw.net/viewtopic.php?f=4&t=8))

As for using splash to hide old kernels, well, that's a bit like applying a plaster to a broken leg to stop the bone being visible.

\\:D/ :D

Deleting old kernels R us, for those who get a bit carried away, we do also have a team effort from ubuntu hiding over here --> [http://forum.phillw.net/viewtopic.php?f=4&t=35](http://forum.phillw.net/viewtopic.php?f=4&t=35)

Keeps us out of mischief and writing crappy 'How-Tos' lol

Pulling out hair correcting stuff --> free of charge.
Getting a Ubuntu user up and running --> Priceless

:KS  :popcorn:  :KS

Hmm, only 24 beers ;-)

Regards,

Phill.

---

### Post by Slim Odds on 2010-03-22
> **phillw said:**
> ...
As for using splash to hide old kernels, well, that's a bit like applying a plaster to a broken leg to stop the bone being visible.
...

I wasn't talking about hiding kernels using the splash screen.

My point was that 99.999% of the people out there get that same message:
_Searching for splash image ... none found, skipping ..._

Because the only time that you **don't get** that message is if you install a custom splash screen. Which the vast, vast majority do not.

The reference to numerous kernel was a joke and hence the :D

Carry on.....

---

### Post by phillw on 2010-03-22
> **Slim Odds said:**
> I wasn't talking about hiding kernels using the splash screen.

My point was that 99.999% of the people out there get that same message:
_Searching for splash image ... none found, skipping ..._

Because the only time that you **don't get** that message is if you install a custom splash screen. Which the vast, vast majority do not.

The reference to numerous kernel was a joke and hence the :D

Carry on.....

Slim, my apologies if I seemed 'off', I haven't booted into 9.10 until this thread for a couple of months, I get out of touch as to what is going on :-(

(I don't see the message in 10.04 testing)

With the 'goings on' with 'splash' on the testing area, I'm not the biggest fan of it. Others love it & think it is the "bees knees" - I guess I'm just a saddo who just wants the computer to turn on and work :lolflag:

But, splash screens are for a different thread. My being 'off' / 'terse' was down to the shear annoyance of the ext3 --> ext4 'How-To' the OP had followed, coupled with my not asking for the grub-install -v at the start, I've been caught out with the Wubi one before & should really know better.

Save one of those beers for me :D

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-23
Great, now I don't know to read:

Yes, the instructions clearly say "sudo apt-get updates" but somehow, smart me, forgot to write "sudo" in the beginning, Im sorry.

Anyway, an update: now I have successfully run both:

"sudo apt-get update" and
"sudo apt-get install grub-pc"

And, after booting the system:

Error 13: Invalid or unsupported executable format
_Chainload into GRUB 2_
When you have verified GRUB2 works, you can use this command to complete the upgrade: upgrade-from-grub-legacy

And then it shows the regular list of kernels, but I still have to choose

Ubuntu 9.10 kernel 2.6.31.19-generic

 Because if I choose "Chainload", it redirects me to the same blank screen

Back to that Error 13 thing

---

### Post by phillw on 2010-03-23
> **hihihi100 said:**
> Great, now I don't know to read:

Yes, the instructions clearly say "sudo apt-get updates" 

The instructions **now** clearly say sudo .....;)

If you can leave it in *19 for now, I'll ask drs305 about it when he comes on-line, the only references I can find for the error are when you have a Windows system as well Ubuntu.

Regards,

Phill.

---

### Post by phillw on 2010-03-24
Hi,

as promised, drs305 has had a look. His suggestion is that we do, indeed, scrap the grub / grub2 and pop grub2 on fresh.

> Phill,

I was called out to fly up to Washington DC.  I'm back now - didn't see
President Obama while I was there.  ;-)

Any, I can't tell where the OP's system is. I'd recommend getting rid of
all traces of Grub/Grub2 and reinstall Grub 2. The instructions on how
to do this are in post #9 of this thread:
[http://ubuntuforums.org/showthread.php?t=1425998](http://ubuntuforums.org/showthread.php?t=1425998) 

All the best.

drs305


Sounds like a plan to me :D
You'll see from that thread, that grub can get itself all confused.
Just remember that you're using sda and not sdb

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-24
Again, Id like to thank you for all the help, this one is gonna be a long post:

I did as you told me, executing those 3 commands:

```
sudo apt-get purge grub grub-pc grub-common
```
```
sudo apt-get install grub-pc grub-common
```

and

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

And this is what appeared (clicking yes on all the defaults):

```
hihihi100@hihihi100-laptop:~$ sudo apt-get install grub-pc grub-common
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libevolution5.0-cil gcj-4.3-base lirc menu-xdg desktop-base
  libmono-getoptions2.0-cil planner python-pygoocanvas libccaudio2-0.9-0
  libboost-regex1.34.1 libgsf-gnome-1-114 rev-plugins dvgrab gthumb
  sooperlooper libavutil-unstripped-49 blepvco gnome-games-extra-data
  linux-backports-modules-2.6.28-15-generic python-renderpm libgcj9-0
  swh-plugins libgcj-bc lives-data libgda3-common language-support-writing-se
  libcvaux1 omins python-plasma libots0 gnome-network-admin hardinfo
  libboost-program-options1.34.1 scim-m17n libboost-program-options1.35.0
  gthumb-data scim-chewing w3c-dtd-xhtml bsh-gcj libcommoncpp2-1.6-0
  libaiksaurusgtk-1.2-0c2a liblo0ldbl libgoocanvas-common libmono-data1.0-cil
  epiphany-extensions libaiksaurus-1.2-0c2a openoffice.org-writer2latex
  scim-hangul screen-profiles gnustep-back0.14 mcp-plugins libass1
  python-reportlab-accel gnumeric-common gnumeric-doc libgnustep-gui0.14
  libweed0 libkcddb4 frei0r-plugins caps libsdl-net1.2 libeet1
  language-support-se dontzap link-grammar-dictionaries-en p7zip libx264-65
  gnome-themes-extras libopal3.6.1 libgoffice-0-6-common stardata-common blop
  amb-plugins libparted1.8-10 arj libgnomescanui-common gnome-volume-manager
  cmt vco-plugins libdumbnet1 libt1-5 libaiksaurus-1.2-data ogmtools
  libmikmod2 gnome-backgrounds gok libgdome2-0 libgnustep-base1.16
  linux-backports-modules-2.6.28-15-server libgavl1 icedax
  libmono-getoptions1.0-cil gnome-user-guide-ca gnome-user-guide-bg
  gnome-user-guide-da gnome-user-guide-ar gnome-user-guide-de libpoppler4
  gnome-user-guide-cs gnome-user-guide-el gnome-user-guide-fi
  gnome-user-guide-en gnome-user-guide-eo gnome-user-guide-es
  gnome-user-guide-he gnome-user-guide-et gnome-user-guide-eu
  gnome-user-guide-gl gnome-user-guide-fr gnome-user-guide-id
  openoffice.org-voikko gnome-user-guide-ja gnome-user-guide-hu
  gnome-user-guide-is gnome-user-guide-it gnome-user-guide-ko
  gnome-user-guide-nb gnome-user-guide-oc gnome-user-guide-pa
  gnome-user-guide-nl gnome-user-guide-nn gnome-user-guide-ms libqzion0
  gnome-user-guide-pl libgcj9-jar gnome-user-guide-pt gnome-user-guide-ro
  gnome-user-guide-sk libsigc++-1.2-5c2 gnome-user-guide-th
  gnome-user-guide-ru gnome-user-guide-sq libwmf-bin gnome-user-guide-uk
  gnome-user-guide-sv gnome-user-guide-tr gnome-user-guide-vi
  gnome-user-guide-zh libffado0 libboost-iostreams1.38.0 fil-plugins libcv1
  libgoffice-0-6 libmagick++1 mozvoikko libphonon4 libzip1 python-uniconvertor
  vdr language-pack-zh-base update-motd imagemagick-doc libmono-data2.0-cil
  libsdl-mixer1.2 libhighgui1 libpt2.6.1 libvolume-id1 libgdome2-cpp-smart0c2a
  libffcall1 gnome-core libzlcore0.9 libgda3-bin gnumeric libgda3-3
  scim-pinyin libindicate1 scim-anthy libboost-filesystem1.34.1 libgmyth0
  liblink-grammar4 libgtkmathview0c2a liblrdf0 tap-plugins odt2txt mkvtoolnix
  libccrtp1-1.6-1 language-pack-gnome-zh-base libcolamd-3.2.0
  gnustep-back0.14-art libjpeg-progs portmap inkscape libzrtpcpp-1.3-0
  python-reportlab libosip2-3deb dpatch libgoocanvas3
  language-pack-kde-zh-base libqedje0 serpentine qt4-qtconfig libntfs-3g49
  gnome-vfs-obexftp xutils-dev libsmpeg0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  multiboot-doc grub-emu
The following NEW packages will be installed:
  grub-common grub-pc
0 upgraded, 2 newly installed, 0 to remove and 394 not upgraded.
Need to get 995kB/1,431kB of archives.
After this operation, 4,178kB of additional disk space will be used.
Get:1 http://archive.ubuntu.com karmic-proposed/main grub-common 1.97~beta4-1ubuntu5 [995kB]
Fetched 995kB in 34s (28.5kB/s)                                                
Preconfiguring packages ...
Selecting previously deselected package grub-common.
(Reading database ... 568693 files and directories currently installed.)
Unpacking grub-common (from .../grub-common_1.97~beta4-1ubuntu5_i386.deb) ...
Selecting previously deselected package grub-pc.
Unpacking grub-pc (from .../grub-pc_1.97~beta4-1ubuntu5_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for install-info ...
install-info: warning: no info dir entry in `/usr/share/info/menu.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond.info-images-dir-dep.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-learning.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-snippets.info-images-dir-dep.gz'
install-info: warning: no info dir entry in `/usr/share/info/sdic.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/netmask.info.gz'
install-info: warning: no info dir entry in `/usr/share/info/lilypond-program.info.gz'
Processing triggers for ureadahead ...
Setting up grub-common (1.97~beta4-1ubuntu5) ...

Setting up grub-pc (1.97~beta4-1ubuntu5) ...

Creating config file /etc/default/grub with new version
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-18-generic
Found initrd image: /boot/initrd.img-2.6.31-18-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-server
Found initrd image: /boot/initrd.img-2.6.28-16-server
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-server
Found initrd image: /boot/initrd.img-2.6.28-15-server
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-server
Found initrd image: /boot/initrd.img-2.6.28-14-server
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-13-server
Found initrd image: /boot/initrd.img-2.6.28-13-server
Found linux image: /boot/vmlinuz-2.6.28-13-generic
Found initrd image: /boot/initrd.img-2.6.28-13-generic
Found linux image: /boot/vmlinuz-2.6.28-12-server
Found initrd image: /boot/initrd.img-2.6.28-12-server
Found linux image: /boot/vmlinuz-2.6.28-12-generic
Found initrd image: /boot/initrd.img-2.6.28-12-generic
Found linux image: /boot/vmlinuz-2.6.28-11-server
Found initrd image: /boot/initrd.img-2.6.28-11-server
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found linux image: /boot/vmlinuz-2.6.28-3-rt
Found initrd image: /boot/initrd.img-2.6.28-3-rt
Found linux image: /boot/vmlinuz-2.6.27-14-generic
Found initrd image: /boot/initrd.img-2.6.27-14-generic
Found memtest86+ image: /boot/memtest86+.bin
File descriptor 3 left open
done

```

Then, as suggested by the post you make reference to, I also executed:

```
sudo grub-mkconfig -o /boot/grub/grub.cfg
```

```
hihihi100@hihihi100-laptop:~$ sudo grub-mkconfig -o /boot/grub/grub.cfg
Generating grub.cfg ...
Found Debian background: moreblue-orbit-grub.png
Found linux image: /boot/vmlinuz-2.6.31-20-generic
Found initrd image: /boot/initrd.img-2.6.31-20-generic
Found linux image: /boot/vmlinuz-2.6.31-19-generic
Found initrd image: /boot/initrd.img-2.6.31-19-generic
Found linux image: /boot/vmlinuz-2.6.31-18-generic
Found initrd image: /boot/initrd.img-2.6.31-18-generic
Found linux image: /boot/vmlinuz-2.6.31-16-generic
Found initrd image: /boot/initrd.img-2.6.31-16-generic
Found linux image: /boot/vmlinuz-2.6.31-15-generic
Found initrd image: /boot/initrd.img-2.6.31-15-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found linux image: /boot/vmlinuz-2.6.28-16-server
Found initrd image: /boot/initrd.img-2.6.28-16-server
Found linux image: /boot/vmlinuz-2.6.28-16-generic
Found initrd image: /boot/initrd.img-2.6.28-16-generic
Found linux image: /boot/vmlinuz-2.6.28-15-server
Found initrd image: /boot/initrd.img-2.6.28-15-server
Found linux image: /boot/vmlinuz-2.6.28-15-generic
Found initrd image: /boot/initrd.img-2.6.28-15-generic
Found linux image: /boot/vmlinuz-2.6.28-14-server
Found initrd image: /boot/initrd.img-2.6.28-14-server
Found linux image: /boot/vmlinuz-2.6.28-14-generic
Found initrd image: /boot/initrd.img-2.6.28-14-generic
Found linux image: /boot/vmlinuz-2.6.28-13-server
Found initrd image: /boot/initrd.img-2.6.28-13-server
Found linux image: /boot/vmlinuz-2.6.28-13-generic
Found initrd image: /boot/initrd.img-2.6.28-13-generic
Found linux image: /boot/vmlinuz-2.6.28-12-server
Found initrd image: /boot/initrd.img-2.6.28-12-server
Found linux image: /boot/vmlinuz-2.6.28-12-generic
Found initrd image: /boot/initrd.img-2.6.28-12-generic
Found linux image: /boot/vmlinuz-2.6.28-11-server
Found initrd image: /boot/initrd.img-2.6.28-11-server
Found linux image: /boot/vmlinuz-2.6.28-11-generic
Found initrd image: /boot/initrd.img-2.6.28-11-generic
Found linux image: /boot/vmlinuz-2.6.28-3-rt
Found initrd image: /boot/initrd.img-2.6.28-3-rt
Found linux image: /boot/vmlinuz-2.6.27-14-generic
Found initrd image: /boot/initrd.img-2.6.27-14-generic
Found memtest86+ image: /boot/memtest86+.bin
done

```

And, lastly, I dont know if more problems may appear, so I executed:

```
sudo bash ~/Desktop/boot_info_script*.sh
```

To get a txt file with all the possible information (As you seem to know much more about linux than I, I just thought that you may see possible errors, or have a clearer idea why my laptop has this problem). The results are:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Grub 0.97 is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

sda1: _________________________________________________________________________

    File system:       ext4
    Boot sector type:  -
    Boot sector info:  
    Operating System:  Ubuntu 9.10
    Boot files/dirs:   /boot/grub/menu.lst /boot/grub/grub.cfg /etc/fstab 
                       /boot/grub/core.img

sda2: _________________________________________________________________________

    File system:       Extended Partition
    Boot sector type:  -
    Boot sector info:  

sda5: _________________________________________________________________________

    File system:       swap
    Boot sector type:  -
    Boot sector info:  

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00034e3b

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   613,008,269   613,008,207  83 Linux
/dev/sda2         613,008,270   625,137,344    12,129,075   5 Extended
/dev/sda5         613,008,333   625,137,344    12,129,012  82 Linux swap / Solaris


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/sda1        50dc5123-ec01-4438-8bd6-cb85bb080f87   ext4                                     
/dev/sda5        72edafb7-a004-4a19-b4aa-26d18c5ae43a   swap                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

/dev/sda1        /                        ext4       (rw,relatime,errors=remount-ro)


=========================== sda1/boot/grub/menu.lst: ===========================

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout        3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title        Windows 95/98/NT/2000
# root        (hd0,0)
# makeactive
# chainloader    +1
#
# title        Linux
# root        (hd0,1)
# kernel    /vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=50dc5123-ec01-4438-8bd6-cb85bb080f87

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title        Ubuntu 9.10, kernel 2.6.31-20-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-20-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-20-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-20-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-20-generic

title        Ubuntu 9.10, kernel 2.6.31-19-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-19-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-19-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-19-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-19-generic

title        Ubuntu 9.10, kernel 2.6.31-18-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-18-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-18-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-18-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-18-generic

title        Ubuntu 9.10, kernel 2.6.31-16-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-16-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-16-generic

title        Ubuntu 9.10, kernel 2.6.31-15-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-15-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-15-generic

title        Ubuntu 9.10, kernel 2.6.31-14-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.31-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.31-14-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.31-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.31-14-generic

title        Ubuntu 9.10, kernel 2.6.28-16-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-16-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-16-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-16-server

title        Ubuntu 9.10, kernel 2.6.28-16-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-16-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-16-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-16-generic

title        Ubuntu 9.10, kernel 2.6.28-15-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-15-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-15-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-15-server

title        Ubuntu 9.10, kernel 2.6.28-15-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-15-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.10, kernel 2.6.28-14-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-14-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-14-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-14-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-14-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-14-server

title        Ubuntu 9.10, kernel 2.6.28-14-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-14-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-14-generic

title        Ubuntu 9.10, kernel 2.6.28-13-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-13-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-13-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-13-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-13-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-13-server

title        Ubuntu 9.10, kernel 2.6.28-13-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-13-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-13-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-13-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-13-generic

title        Ubuntu 9.10, kernel 2.6.28-12-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-12-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-12-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-12-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-12-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-12-server

title        Ubuntu 9.10, kernel 2.6.28-12-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-12-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-12-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-12-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-12-generic

title        Ubuntu 9.10, kernel 2.6.28-11-server
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-server
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-server (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-11-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-11-server

title        Ubuntu 9.10, kernel 2.6.28-11-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.10, kernel 2.6.28-11-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.10, kernel 2.6.28-3-rt
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.28-3-rt
quiet

title        Ubuntu 9.10, kernel 2.6.28-3-rt (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.28-3-rt root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.28-3-rt

title        Ubuntu 9.10, kernel 2.6.27-14-generic
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro quiet splash
initrd        /boot/initrd.img-2.6.27-14-generic
quiet

title        Ubuntu 9.10, kernel 2.6.27-14-generic (recovery mode)
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/vmlinuz-2.6.27-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single
initrd        /boot/initrd.img-2.6.27-14-generic

title        Ubuntu 9.10, memtest86+
uuid        50dc5123-ec01-4438-8bd6-cb85bb080f87
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

=========================== sda1/boot/grub/grub.cfg: ===========================

#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by /usr/sbin/grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s /boot/grub/grubenv ]; then
  have_grubenv=true
  load_env
fi
set default="0"
if [ ${prev_saved_entry} ]; then
  saved_entry=${prev_saved_entry}
  save_env saved_entry
  prev_saved_entry=
  save_env prev_saved_entry
fi
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  insmod gfxterm
  insmod vbe
  if terminal_output gfxterm ; then true ; else
    # For backward compatibility with versions of terminal.mod that don't
    # understand terminal_output
    terminal gfxterm
  fi
fi
if [ ${recordfail} = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
insmod ext2
set root=(hd0,1)
search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
insmod png
if background_image /boot/grub/moreblue-orbit-grub.png ; then
  set color_normal=black/black
  set color_highlight=magenta/black
else
  set menu_color_normal=white/black
  set menu_color_highlight=black/white
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry "Ubuntu, Linux 2.6.31-20-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-20-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-20-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-20-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-19-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-19-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-19-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-18-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-18-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-18-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-16-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-15-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.31-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.31-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.31-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-16-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu, Linux 2.6.28-16-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-16-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-16-server
}
menuentry "Ubuntu, Linux 2.6.28-16-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-16-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-16-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-16-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-15-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-15-server
}
menuentry "Ubuntu, Linux 2.6.28-15-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-15-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-15-server
}
menuentry "Ubuntu, Linux 2.6.28-15-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-15-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-15-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-15-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-14-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu, Linux 2.6.28-14-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-14-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-14-server
}
menuentry "Ubuntu, Linux 2.6.28-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-14-generic
}
menuentry "Ubuntu, Linux 2.6.28-13-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-13-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-13-server
}
menuentry "Ubuntu, Linux 2.6.28-13-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-13-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-13-server
}
menuentry "Ubuntu, Linux 2.6.28-13-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-13-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, Linux 2.6.28-13-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-13-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-13-generic
}
menuentry "Ubuntu, Linux 2.6.28-12-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-12-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-12-server
}
menuentry "Ubuntu, Linux 2.6.28-12-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-12-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-12-server
}
menuentry "Ubuntu, Linux 2.6.28-12-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-12-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-12-generic
}
menuentry "Ubuntu, Linux 2.6.28-12-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-12-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-12-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-server" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-11-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-11-server
}
menuentry "Ubuntu, Linux 2.6.28-11-server (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-11-server root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-11-server
}
menuentry "Ubuntu, Linux 2.6.28-11-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-11-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-11-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-11-generic
}
menuentry "Ubuntu, Linux 2.6.28-3-rt" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-3-rt root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu, Linux 2.6.28-3-rt (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.28-3-rt root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.28-3-rt
}
menuentry "Ubuntu, Linux 2.6.27-14-generic" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    set quiet=1
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.27-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro   quiet splash
    initrd    /boot/initrd.img-2.6.27-14-generic
}
menuentry "Ubuntu, Linux 2.6.27-14-generic (recovery mode)" {
        recordfail=1
        if [ -n ${have_grubenv} ]; then save_env recordfail; fi
    insmod ext2
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 50dc5123-ec01-4438-8bd6-cb85bb080f87
    linux    /boot/vmlinuz-2.6.27-14-generic root=UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 ro single 
    initrd    /boot/initrd.img-2.6.27-14-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ ${timeout} != -1 ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

=============================== sda1/etc/fstab: ===============================

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=72edafb7-a004-4a19-b4aa-26d18c5ae43a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

=================== sda1: Location of files loaded by Grub: ===================


 104.8GB: boot/grub/core.img
 288.2GB: boot/grub/grub.cfg
    .0GB: boot/grub/menu.lst
 288.0GB: boot/grub/stage2
 288.2GB: boot/initrd.img-2.6.27-14-generic
 288.2GB: boot/initrd.img-2.6.28-11-generic
 288.1GB: boot/initrd.img-2.6.28-11-server
 288.0GB: boot/initrd.img-2.6.28-12-generic
 288.2GB: boot/initrd.img-2.6.28-12-server
 288.1GB: boot/initrd.img-2.6.28-13-generic
 288.2GB: boot/initrd.img-2.6.28-13-server
 288.1GB: boot/initrd.img-2.6.28-14-generic
 288.2GB: boot/initrd.img-2.6.28-14-server
 288.2GB: boot/initrd.img-2.6.28-15-generic
 288.2GB: boot/initrd.img-2.6.28-15-server
 288.2GB: boot/initrd.img-2.6.28-16-generic
 288.2GB: boot/initrd.img-2.6.28-16-server
 288.1GB: boot/initrd.img-2.6.28-3-rt
 288.2GB: boot/initrd.img-2.6.31-14-generic
 302.8GB: boot/initrd.img-2.6.31-15-generic
 307.6GB: boot/initrd.img-2.6.31-16-generic
  62.3GB: boot/initrd.img-2.6.31-18-generic
  63.0GB: boot/initrd.img-2.6.31-19-generic
 288.2GB: boot/initrd.img-2.6.31-20-generic
 288.1GB: boot/vmlinuz-2.6.27-14-generic
 288.0GB: boot/vmlinuz-2.6.28-11-generic
 288.0GB: boot/vmlinuz-2.6.28-11-server
 288.0GB: boot/vmlinuz-2.6.28-12-generic
 288.0GB: boot/vmlinuz-2.6.28-12-server
 288.0GB: boot/vmlinuz-2.6.28-13-generic
 288.0GB: boot/vmlinuz-2.6.28-13-server
 288.1GB: boot/vmlinuz-2.6.28-14-generic
 288.1GB: boot/vmlinuz-2.6.28-14-server
 288.0GB: boot/vmlinuz-2.6.28-15-generic
 288.1GB: boot/vmlinuz-2.6.28-15-server
 288.1GB: boot/vmlinuz-2.6.28-16-generic
 288.1GB: boot/vmlinuz-2.6.28-16-server
 288.1GB: boot/vmlinuz-2.6.28-3-rt
 302.9GB: boot/vmlinuz-2.6.31-14-generic
 288.0GB: boot/vmlinuz-2.6.31-15-generic
   6.3GB: boot/vmlinuz-2.6.31-16-generic
  14.8GB: boot/vmlinuz-2.6.31-18-generic
  62.3GB: boot/vmlinuz-2.6.31-19-generic
 288.1GB: boot/vmlinuz-2.6.31-20-generic
 288.2GB: initrd.img
  63.0GB: initrd.img.old
 288.1GB: vmlinuz
  62.3GB: vmlinuz.old
```

Now Im gonna turn off the laptop, and, given that I gotta go, I wont be able to turn it on till, at least, another 5 hours, but good news, it seems that GRUB2 has been correctly re-installed, and, as the txt file shows, EXT4 is the standard in use, or so I think...

Cheers

---

### Post by phillw on 2010-03-24
Hi,

as you're aware, you had pretty much gotten to the limit of what I am knowledgeable for (hence my asking drs305 to take a look).

It looks okay, the true test will be when you boot into the *20 kernel.

Assuming that works, removing the old ones from the list is a very easy job.

I'll also post how to re-gain the disk space being tied up by the stuff it said it didn't need any longer.

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-24
No luck so far:
```
Error 13: Invalid or unsupported executable format
```Still appears, and I am still being asked to choose a kernel from the list. Given that I cannot use kernel 2.6.31.20, I use 2.6.31.19 generic

No references to GRUB or any chainload appear

And something else, if I run
```
grub-install -v
```

I get:
```
grub-install (GNU GRUB 1.97~beta4)
```

However, after executing:
```
sudo bash ~/Desktop/boot_info_script*.sh
```

The first lines of the .txt file with all the information show:
```
  Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => _Grub 0.97_ is installed in the MBR of /dev/sda and looks on the same drive 
    in partition #1 for /boot/grub/stage2 and /boot/grub/menu.lst.

```

Shouldn't the underlined GRUB 0.97 be GRUB 1.97 beta?

---

### Post by phillw on 2010-03-24
Yes, it should only show 1.97, and not 0.97.

I'm well beyond my limits of my understanding of Grub and your problem.

I just cannot see how the instructions that drs305 suggested would leave grub legacy kicking around.

Once again, I'm going to have to ask for some help on this one.

I'm real sorry that the problem has dragged on, this is not how it should be.

Phill.

---

### Post by Herman on 2010-03-25
:D You could try installing the MBR part of GRUB2 to MBR.

A quick way would be just to do this, #[**2**]("http://ubuntuforums.org/showpost.php?p=8200936&postcount=2")

Another way would be to try booting your system and running grub-install /dev/sda.
If your system has boot problems (error 13), you can boot it anyway if you can follow the examples in the link following, [GRUB2 How To Boot From CLI Mode]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20How%20To%20Boot%20From%20CLI%20Mode.html") -  NEW!  Rescue your System.
The other way is to [chroot]("http://ubuntuforums.org/showpost.php?p=8995103&postcount=37") into your Ubuntu installation from a Live CD to run grub-install.
```
sudo grub-install /dev/sda
```

---

### Post by hihihi100 on 2010-03-25
Some more info:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=72edafb7-a004-4a19-b4aa-26d18c5ae43a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             288G   17G  257G   7% /
udev                 1006M  244K 1006M   1% /dev
none                 1006M  200K 1006M   1% /dev/shm
none                 1006M  244K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
$ 

```EXT3???

---

### Post by hihihi100 on 2010-03-26
Screw it!! Im making a fresh reinstallation from the live cd, Ill leave it on EXT3

---

### Post by phillw on 2010-03-26
You may as well format to ext4 if you're doing it from scratch.

Phill.

---

### Post by phillw on 2010-03-26
> **hihihi100 said:**
> Some more info:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda1
UUID=50dc5123-ec01-4438-8bd6-cb85bb080f87 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda5
UUID=72edafb7-a004-4a19-b4aa-26d18c5ae43a none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             288G   17G  257G   7% /
udev                 1006M  244K 1006M   1% /dev
none                 1006M  200K 1006M   1% /dev/shm
none                 1006M  244K 1006M   1% /var/run
none                 1006M     0 1006M   0% /var/lock
none                 1006M     0 1006M   0% /lib/init/rw
$ 

```EXT3???

Hmmm....  ```
gksudo gedit /etc/fstab
```
alter the ext3 to ext4, then save and re-boot. It's quite obvious now that the how-to you were following was incorrect in a couple of areas :-(

We should be able to rsync your /home over to the external hard-drive with that corrected.

Phill.

---

### Post by hihihi100 on 2010-03-26
too late phil, but thanks anyway...

Im writting from the freshly re installed 9.10, but there are still some things I dont understand, hope you can help me:

I erased and used the entire disk to reinstall, the previous Ubuntu 9.10 is totally gone, but during the process, this is what appeared on the last step right before the reinstallation:

```
The partition tables of the following devices are changed
SCSI1 (0,0,0) (sda)
the following partitions are going to ve formatted
partition #1 of SCSI1 (0,0,0) (sda) as _ext4_
partition #5 of SCSI1 (0,0,0) (sda) as swap
```

I confess I never expected to see again EXT4... The live cd installed the whole OS and I started to use it. As soon as I could I downloaded Gparted from the software center and, again, just take a look at the .png I have attached...

---

### Post by hihihi100 on 2010-03-26
HOLY MOTHERFVCKING ****!!!!!!!!!!!!

```
              Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => _Grub 2_ is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #1 for /boot/grub.
 => Windows is installed in the MBR of /dev/sdb
```GRUB 2 IS INSTALLED!!!!!!!!!!!!!!!!!!!

Does this mean I finally have, when I thought everything was lost, EXT4 fully functioning?

Windows??? Im not running windows, I have never used a windows live cd in this laptop, what is Windows doing there?

---

### Post by phillw on 2010-03-26
Antonio, I appreciate your exuberance, but be careful with expletives. :-\

ext4 is the default file system for 9.10 and I would  expect it to be there.
grub2 has also gotten itself fully in control.
at some point in the past, or present  your external hard drive had / has windows on it the Windows boot is still on that hard drive. That is not a problem, as you are not booting via sdb

You look Good To Go !!!

Regards,

Phill.

---

### Post by hihihi100 on 2010-03-26
Id just like to thank u again, phil, for all the help provided, it is a pity that I had to make a fresh reinstallation, but now EXT4 is fully operative, and thats what matters

This thread is closed

:p:p:p

---

