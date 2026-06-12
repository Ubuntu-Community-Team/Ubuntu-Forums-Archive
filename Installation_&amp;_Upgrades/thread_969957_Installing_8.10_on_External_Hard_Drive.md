---
title: "Installing 8.10 on External Hard Drive"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by MTGap on 2008-11-03
Well I know of one method to do this which includes removing the IDE cable from my internal hard drive and then hitting install from the CD. Unfortunately my dad won't allow me to do this and everything becomes much more difficult. 

So now I need a method to get a full installation of 8.10 onto the external hard drive (80GB) which I want to be able to save my work on it for later boots with it. So that it is basically just any other installation on an internal hard drive, but portable. 

I found this method, but I'm not sure if it applies to my problem: [http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/]("http://www.pendrivelinux.com/2008/10/15/ubuntu-810-persistent-flash-drive-install-from-live-cd/")

If I was to do this I would have to do automatic, because I'm not yet familiar with Ubuntu or any other Linux distribution. The whole point of getting it on the external hard drive is to give it a try! ;)

So can I do that method, the automatic part would be easy for me. Because I've read other things on the forums and many are way to complicated for me...

---

### Post by wdaim on 2008-11-04
yeah that link should be fine, just follow the instructions, worked fine for me (:

---

### Post by caljohnsmith on 2008-11-04
That link you have gives instructions for installing the Live CD to the external drive, i.e. not doing a full installation. I would just go with a full installation if I were you, and it is really easy: just go through the normal Ubuntu installer on the Live CD, select your external drive to install Ubuntu to, and then the important step is when you get to the final step of the installation, click the "advanced" button and have Grub installed to /dev/sdb or whichever is your external drive. Don't let Grub be installed to (hd0) or /dev/sda, or you'll overwrite the MBR (Master Boot Record) in your internal drive. That should be all it takes. Let me know how it goes.

---

### Post by MTGap on 2008-11-04
So when I'm doing this how will I know what external hard drive I'm installing it to... I mean what exactly will I be clicking to install it too...


Isn't this a little risky? I want something fairly simple that is risk free...


Is that basically this tutorial: [http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/]("http://www.pendrivelinux.com/2008/04/14/ubuntu-804-usb-hard-drive-install/")

I want to be sure, I won't write over anything. My dad doesn't want me unplugging the internal hard drive though... 

What would the name be of my external hard drive.

---

### Post by caljohnsmith on 2008-11-04
I think the only way you can guarantee being 100% risk-free from touching the internal drive is to disconnect the internal drive. But when you go through the installer, it clearly gives you a choice of drives to install to; just select your 80 GB external drive and you'll be fine, and make sure you use that "advanced" button at the end like I mentioned to install Grub to the external drive.

---

### Post by MTGap on 2008-11-04
So on step 9 on the link, the grub advanced thing. Which one would I choose, is that how the hard drive name is displayed? I'm confused because the picture shows two things: 

/dev/sda  

and

/dev/sda1

No harm can be caused by disconnecting the internal hard drive though correct? My dad just doesn't want me to mess it up...


For the beginning of the installation will I see my 80GB external hard drive?

---

### Post by caljohnsmith on 2008-11-04
In that tutorial you linked to, they show choosing the "install Ubuntu" option from the main menu when you boot the Live CD; I think that's the option that installs Ubuntu inside Windows, at least that's the way I remember it with the 8.04 CD. The way I know works is to select the "Try Ubuntu without making changes" option from the main menu, and then once you get to the Ubuntu desktop, double-click the installer on the desktop. And yes, it will give you the choice at the beginning which drive to install to. When you click the "advanced" button at the end, it should give an option to install to /dev/sdb, which will be your external drive if you only have two drives.

---

### Post by jimv on 2008-11-04
Unless both drives are 80 gigs, choose the one that shows up as an 80 gig drive.

OR 

Go into the bios and disable the internal HD, then re-enable when you're done (if you forget the setting, just go back to the defaults)

OR

Pre-partition your portable HD with an EXT3 partition, so when you are looking at it from the Ubuntu installer, it'll be the only one with an EXT3 partition.

---

### Post by MTGap on 2008-11-04
Well I'm now able to do it thanks to a friend with installing inside of windows, he tells me that I have to have the options at the boot screen between XP and Ubuntu.

He said that I can't boot from my external hard drive without it because there needs to be a boot.ini or something.


Is this true, I believe him, but want it to be false... 

Because my dad doesn't want it to be on there like this.

---

### Post by caljohnsmith on 2008-11-04
> **MTGap said:**
> Well I'm now able to do it thanks to a friend with installing inside of windows, he tells me that I have to have the options at the boot screen between XP and Ubuntu.

He said that I can't boot from my external hard drive without it because there needs to be a boot.ini or something.


Is this true, I believe him, but want it to be false... 

Because my dad doesn't want it to be on there like this.
If you can set your BIOS to boot from your external drive, there is absolutely no reason to modify your Windows boot.ini file to boot the external drive. Also, you don't need to install Ubuntu within Windows; if you use the strategy I gave in my earlier posts, Ubuntu will be only on the external drive, and the internal Windows drive will be untouched. That's a lot less invasive than modifying the Windows boot.ini file I think.

---

### Post by MTGap on 2008-11-04
Well I did it so it's easier, where I just plug in my external hard drive and specify it in the ubuntu setup, I can get rid of the boot options through remove programs correct?


Is this a full install?

---

### Post by ferrettsyl on 2008-11-22
When I run Ubuntu through the Live CD and then select the install option from there, on the third step or so it asks how I want to partition my harddrive without asking which drive I want to install to. It doesn't make sense that it would ask that before knowing which harddrive to install to, so I'm nervous to click forward lest it partition my internal drive, which I do not want. I have a laptop so disconnecting my internal drive would be... difficult.

---

### Post by unutbu on 2008-11-22
Don't worry. It will ask you which drive you wish to use. Also, nothing gets written to disk until you click Install in Step #7 (the final step).

When you partition, note the name assigned to your external drive. It might be (hd1) for example. You'll use this in the final step (#7), below:

When you get to the final step, click the "Advanced" button. There, make sure that you install the bootloader, GRUB, on the external drive, not your internal drive. 

If you install GRUB on your internal drive, then you will not be able to boot your laptop without your external drive connected (...not good). There is a way to fix this, but it's better to avoid the problem if possible.

If you install GRUB on the external drive, then to boot Ubuntu, you will need to tell your BIOS to boot from the external drive.

---

### Post by thietala on 2008-12-03
I disconnected my hard drives and installed Ubuntu 8.10 on a 320 GB USB external hard drive (platter type).  Grub 1.5 executes but I continually get a

Boot from (hd0,0) ext3 7f8b2a05-3747-4340-b231-39931131fe61
Starting up ...
[    0.788084] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I am kind of stuck from where to go from here.

Thanks...

---

### Post by thietala on 2008-12-04
> **thietala said:**
> I disconnected my hard drives and installed Ubuntu 8.10 on a 320 GB USB external hard drive (platter type).  Grub 1.5 executes but I continually get a

Boot from (hd0,0) ext3 7f8b2a05-3747-4340-b231-39931131fe61
Starting up ...
[    0.788084] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I am kind of stuck from where to go from here.

Thanks...

I tried the 8.04 install and did not have any problems...

Thanks

---

### Post by brookie on 2008-12-16
Hi there, I need a little help and hope someone can point me in the right direction.

I downloaded Ubuntu iso and burned it to a cd. Then I followed this tutorial: [http://ubuntuforums.org/showthread.php?t=678146](http://ubuntuforums.org/showthread.php?t=678146) on how to install ubuntu to an external hdd. This tut was for version 7.10 however. 

I ran the install and got grub and the entire system installed on the external hdd. I have my bios set up to boot from the external usb as well. After the install, no dual boot option, and winxp cannot see the external hdd. 

The problem I encountered was in the fourth step step of the tutorial I was following. It said not to shut down and continue making the correct system changes via a terminal window. Well, 8.10 only has an option to restart after install to complete so I couldn't edit the files from the instructions I was following. 

Can I do steps 4-13 [http://ubuntuforums.org/showthread.php?t=678146]("http://ubuntuforums.org/showthread.php?t=678146") to get this drive to dual boot as an external. My internal drive has winxp pro on it. 

I swapped out my external hdd (ubuntu 8.10 now) for my internal hdd (winxp pro sp3) and turned on the machine and it booted into ubuntu 8.10 updated it and it's running awesomely. 

Any help will be appreciated. I'd still like to set it up as an external dual boot with winxp until I can learn more about ubuntu, linux, filesystems, networking in ubuntu, etc...

Cheers, 

brookie

ps...now that I swapped my disks i am running ubuntu and have access to the system files, but don't want to change the system files for an external usb dual boot until i get some feedback on the proper steps to take, an if the instructions i mentioned above will work. :p

pss...i cannot do one of the steps anyhow, in terminal, su fails with authentication failure. i typed in my password for the user i created on install but it does not work.???

---

### Post by mrbiggbrain on 2008-12-17
> **caljohnsmith said:**
> If you can set your BIOS to boot from your external drive, there is absolutely no reason to modify your Windows boot.ini file to boot the external drive. Also, you don't need to install Ubuntu within Windows; if you use the strategy I gave in my earlier posts, Ubuntu will be only on the external drive, and the internal Windows drive will be untouched. That's a lot less invasive than modifying the Windows boot.ini file I think.

indeed, setting up the windows boot.ini file would cause more problems, take you more time (as you may or may not need to make a boot image) and remove one of the nicest features of USB booting.

Have grub installed on the MBR of the external 80gb drive, as well as setting up a swap partition.  now any pc you go to just needs to be setup to boot off external drives BEFORE internal HDD, the bios will detect the External, locate the MBR on that external, and boot. 

setting up the windows boot.ini file could cause issues for the WHOLE system if the drive is not connected and someone tries to boot (depending on how its setup) and would mean you could boot it on only the pc setup for that, the grub option allows you to boot it off ANY pc setup to boot off external sources.

and also, if for some reason you screw up the MBR on windows xp or vista, on xp its as easy as booting the pc with the windows install disk, waiting 5 or so minutes for it to load, choosing recover till the recovery console comes up, login into admin of c:/ and typing fixmbr. 

"Yes i understand" (don't worry this is a disclaimer, i don't take responsibility if this hurts your pc, but iv done it about 50 times without an issue)

This is so common, windows vista does it automatically if you boot an install Cd, some recovery tools, or even the free windows vista toolkit that has the recovery console on it.

afterwards you'll likely see chkdsk doing its thing, don't worry THIS IS GOOD, this means windows noticed the disk changed and is going to clean it up, and fix any minor issues that may have occurred (broken file system etc)

you can run it yourself by saying chkdsk -r (i think its r), chkdsk /? will give you the command, it says fix disk errors instead of just scanning, it takes a while, but do it one way or another! if windows doesn't auto do it, log back into the recovery disk and do it yourself.

if someone could verify its ok for him to do this, i dont want it being just me who says its a good idea, nervious hands do dirty deeds when they get scared, and the recovery console though easy is scary!

---

### Post by unutbu on 2008-12-17
brookie, that you managed to boot Ubuntu by swapping the external and internal drives demonstrates that you don't need steps 4--13 of that guide you posted. In fact, 8.10 uses uuid's to specify the grub root partition, so in fact, the guide's instructions are obsolete.

Try unswapping your drives (so Ubuntu is on the external drive) and using the BIOS to boot from the external drive. I suspect that is all you need to do.

---

