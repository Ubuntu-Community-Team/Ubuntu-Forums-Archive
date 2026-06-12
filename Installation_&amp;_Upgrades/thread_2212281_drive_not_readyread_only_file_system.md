---
title: "drive not ready/read only file system"
date: 2014-03-20
forum: Installation &amp; Upgrades
---

### Post by kate5 on 2014-03-20
Hey. I will try my best to not ramble. I am using a phone to post this after trying to find answers, but i think i really need dumbed down help.

I ordered an older laptop "with a fresh upgrade of ubuntu" and it was...10.4 i believe. The laptop is an Acer aspire initially with Windows 7 (if it is still on there somewhere, idk how to find it). The specs sticker is still on it, so ill just type what i see:

Aspire 5552-7803
AMD Phenom II x4 N970
15.6" HD LED LCD
ATI Mobility Radeon HD 4250
4GB RAM
640gb hdd
DVD super multi dl drive
Acer NPLIFY 802 11b/g/n
6 cell battery

The system already worked fine(ish, better than now), but I bought this for work and needed to upgrade it so i could have an odesk tracker that actually worked. So, i decided to upgrade through the site. 

Now it says the /disk isnt there or ready and when i would try the commands that i did find online, it would say files were read only. I would say at this point, i am as new as it gets since i cant figure anything out despite following directions.

If anyone can really help me, that would be great. I am at my wits end with it and really need to be able to work again. Thanks.

---

### Post by 7sbaV8Kt5PTh on 2014-03-20
Hi Kate.  It could be that because of an error, it is booting "read-only".  When it is booting, do you see any kind of error go by? Can you 'cd /var/log' and see any files there?  Maybe do a 'tail -200 syslog' to see if there are any errors?  

If you can boot from a Live CD, you could do an 'fdisk -l' to see what it thinks the partitions look like.  You can also do a 'fsck /dev/sda1' (Or whatever the drive might be named) on an unmounted disk.  **Let it run to completion!**  This will tell you if there are problems with the actual drive, or if it is clean.  Here are the [man pages]("http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html") for fsck.

---

### Post by ajgreeny on 2014-03-20
If it really was 10.04, that version is no longer supported so you did the right thing upgrading.  However, there were major changes between 10.04 and 12.04 that I recall causing many problems when on-line upgrades were carried out at the time that 12.04 appeared, and many users thought it was better to do a clean install.

I think that machine should run Ubuntu 12.04 fairly easily, though I am not sure about the ATI Mobility Radeon HD 4250 graphic card; I think it will work but may need a proprietary driver to run unity properly and I am not sure if that card is supported by AMD any more; not absolutely sure about that, so try with a live USB/DVD first to be sure.  The open source driver will probably work but may not be good enough for unity.

If that works OK go ahead and try installing clean, having first backed up your personal files, including the hidden ones, in /home to a USB hard drive, if you have one.  If unity still does not work properly consider using Xubuntu 12.04 or 13.10, or Lubuntu 13.10, and remember 14.04 of all of the ubuntu family is soon to arrive, and is looking very good at the moment, so you my even consider using that in April.

---

### Post by kate5 on 2014-03-20
As far as i can tell, i cannot get past that manual screen at all and the other options are useless. I ended up purchasing a disk, hoping to be able to fix it after the upgrade failed. are there certain commands to get the disk read properly? I did go into bios and set it up so the dvd drive would load first, but nothing actually changed.

I wish i could wait until April, but i spent the last of my money on this laptop and then got laid off pretty much immediately. This is causing a lot of problems. I just need a real solution. :(

---

### Post by kate5 on 2014-03-20
Looking into this now

---

### Post by kate5 on 2014-03-20
> **John_Forristel said:**
> Hi Kate.  It could be that because of an error, it is booting "read-only".  When it is booting, do you see any kind of error go by? Can you 'cd /var/log' and see any files there?  Maybe do a 'tail -200 syslog' to see if there are any errors?  

If you can boot from a Live CD, you could do an 'fdisk -l' to see what it thinks the partitions look like.  You can also do a 'fsck /dev/sda1' (Or whatever the drive might be named) on an unmounted disk.  **Let it run to completion!**  This will tell you if there are problems with the actual drive, or if it is clean.  Here are the [man pages]("http://manpages.ubuntu.com/manpages/hardy/man8/fsck.8.html") for fsck.
  When it boots past the acer screen it says "warning ** command line 'dbus-launch --autolaunch=cfe450ad0fa167bd3401121452fa0da2 --binary-syntax --close-stderr' exited with non zero exi..." (it cut off) and "autolaunch error: x11 initialization failed.\n

I press m and "root file check failed" appears. I did the "cd/var/log" and got "no such file or directory". Then the tail one got "cannot open 'syslog' for reading: no such file or directory. 

The disk i have in just keeps trying to spin and nothing happens.

---

### Post by Bashing-om on 2014-03-20
kate5; Hi !

My bit to try and help:

Let's get that liveDVD booting, and see what there is to work with.
I agree that machine should run anything you choose to throw on it .. with the caveat that the graphics card is no longer supported by AMD, you only have recourse to the open source drivers on anything beyond the 12.04.1 release.
OK -> Booting:
Boot the liveDVD ( bios set as the dvd device 1st boot priority) ->
As soon as the bios screen clears depress and hold the right shift key -> language screen, escape key to accept the default -> boot option screen:

Boot options screen -> choose "check disk for defects"  If it runs and NO errors found, then:
choose "try ubuntu" // a long process to copy stuff into ram, and then make up the operating system - be patient //; ===> Do you now boot to the desk top ?

At this point you have a fully functioning operating system and we will want some amplifying information. Terminal time !
From the desk top the key combo ctl+alt+t will yield a terminal ->
To start with, the release and kernel we are working with.
Post back the output of terminal commands:
```

lsb_release -a
uname -a

```
And hey we can do this.
[INDENT][INDENT]with 'buntu and a liveDVD
[INDENT][INDENT][INDENT]all things are possible
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by kate5 on 2014-03-20
When i pressed and held down the right shift key, i ended up with four options. Run ubuntu, run ubuntu in restore mode, and two mem tests. Currently running the memory test. Hopefully they are simply using different synonyms and i am in the right place!

---

### Post by Bashing-om on 2014-03-20
kate5; Hey ,

That "sounds" to me like you are still booting the install and getting grub's boot menu.
Double check that you know how to reset bios to have bios boot the dvd device.

At this point we really really want to boot up the liveDVD, and then look around.

Running the memtest is a good thing as it surely will hurt nothing to check.

sometimes,
[INDENT][INDENT]there is no substitute for the liveDVD
[/INDENT][/INDENT]

---

### Post by kate5 on 2014-03-20
P.s. It says "ECC: disabled" next to the AMD Info, so i think you duders are right about that.

---

### Post by kate5 on 2014-03-20
I went into bios and then the boot menu. I put the dvd tray into the number one spot. Then i saved and exited.

---

### Post by Bashing-om on 2014-03-20
kate5; Hey

ECC disabled is no big deal, ECC is error checking on the ram chips and is expensive, rarely is that capability provided.
Ignore it and move on.

There are so many different bios and the means to alter the boot order, UEFI and secure boot confuses the situation even more. Only someone who has your machine can advise exactly how to boot the dvd.

Keep trying until you can get the dvd's boot options screen, verify the DVD and can boot with the DVD's boot option "try ubuntu".

We will hang with you .

---

### Post by kate5 on 2014-03-20
I did it! The disk is running and the purple ubuntu screen is up. well, now im at the install or try menu!

---

### Post by kate5 on 2014-03-20
Hopefully i can just navigate it properly from here? Thanks, everyone! I will still check back in case i missed something

---

### Post by Bashing-om on 2014-03-20
kate5; Outstanding.

Moving along smartly,

Choose "check disk for defects" and when done choose "try ubuntu"
Will take a long while to load up. talk to us next from the "try ubuntu" desk top -> FireFOx !

[INDENT][INDENT]we be look'n fer ya
[/INDENT][/INDENT]

---

### Post by kate5 on 2014-03-21
Hey. I actually decided to go "all the way" and install it. Everything seems to be working pretty well! I even figured out how to install Spotify! Thank you so much! I'm liking this OS a lot.

---

### Post by Bashing-om on 2014-03-21
kate5; Outstanding !

Welcome to our world.

As you are up and running, please mark this thread solved, aids others seeking a similar solution, and helps keep the forum tidy. 1st post -> thread tools -

As you progress - this forum, as you have found out, is a great resource. Open as many threads as needed to address any issue you have. One thread one issue. Just keep in mind ubuntu ain't Windows, a different mind set and a different way of doing things ! It is a process of learning.

[INDENT]ubuntu, In My Humblest Of Opinions
[INDENT][INDENT][INDENT]the greatest operating system the world has ever known
[/INDENT][/INDENT][/INDENT][/INDENT]

---

