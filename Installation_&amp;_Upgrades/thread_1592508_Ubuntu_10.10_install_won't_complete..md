---
title: "Ubuntu 10.10 install won't complete."
date: 2010-10-10
forum: Installation &amp; Upgrades
---

### Post by lonegeek on 2010-10-10
I first tried the RC, then daily build from 10/7, and now the official release, which has worked best.

It is now getting hung up on "configuring hardware"

It seems basically installed yet I think is getting hung up on installing a bootloader.

Ideas?

---

### Post by lonegeek on 2010-10-10
ubuntu ubiquity: update-initramfs: Generating /boot/initrd.img-2.6.35-22-generic

Stuck here

---

### Post by mörgæs on 2010-10-10
What is 'best'? Does the final release work when booted as a live CD, or are there some strange observations? 

Which hardware are you using, especially how much memory is on the system?

---

### Post by lonegeek on 2010-10-10
RC would error that bootloader could not be installed.

Daily build burned wrong I think.

Seems to have progressed slightly?

ubuntu CRON[23038]: (root) CMD (    cd / && run-parts --report /etc/cron.hourly)


It is a sempron 3100+ with 1 gb ram.

Ran 10.04 just fine.

Thanks!

---

### Post by nicko1805 on 2010-10-10
ok so I am having exactly the same problem, had to sign up just then to ask.
install gets to about 40% then tells me there is an error (errno 5) and it cant continue. 
so any help would be good.
ps. had 10.04 running on here perfectly

---

### Post by Slave2Metal on 2010-10-10
I downloaded two different iso files.  One was from a torrent and the other direct.  Cannot for the life of me get the cd to boot.  Put in my 10.04 cd and it boots right up.  Is the Maverick iso really only 632 MB?

---

### Post by lonegeek on 2010-10-10
Just removed all the other hard drives besides the destination drive.

Bootloader install failed

---

### Post by jcolyn on 2010-10-10
Burn another copy at 10x speed or slower. Fast burns usually give install problems.

I burned my copy at 6x and install went without a hitch.

---

### Post by lonegeek on 2010-10-10
> **jcolyn said:**
> Burn another copy at 10x speed or slower. Fast burns usually give install problems.

I burned my copy at 6x and install went without a hitch.

I burned this copy at 10x and the burner verified it.

Grub will not install.

---

### Post by lonegeek on 2010-10-10
I'm trying to format the drive using GUID with disk utility, but it will not let me and claims the disk is busy.

---

### Post by lonegeek on 2010-10-10
> **lonegeek said:**
> I'm trying to format the drive using GUID with disk utility, but it will not let me and claims the disk is busy.

Just formated the drive with guid scheme or whatever.

Still cannot install a bootloader.

---

### Post by lonegeek on 2010-10-10
Just tried to install 10.04.1 ..

"The installer encountered an unrecoverable error."

---

### Post by flatko on 2010-10-11
I experience the same issue - installer freezes at "Configuring hardware". Tried several times, it freezes sometimes at "update-initramfs" and sometimes at "CRON".
My system is: MB: Asus K8N, 1GB of RAM, AMD Sempron 2500+

I've burned the CD at 8x and the integrity check passed without errors.

---

### Post by lonegeek on 2010-10-11
I've tried to manually install grub.

sudo mount /dev/sda1 /mnt


sudo grub-install --force --root-directory=/mnt/ /dev/sda1


All the files are there, but I only get a flashing white line when I restart.

---

### Post by lonegeek on 2010-10-11
Seriously, I'm not sure what I'm not getting.

Ive manually installed grub and it cant determine the partition type so it apparenly wont boot.

I've completely erased the hard drive with no partition tables using disk utility.

Still hangs up on generating /boot/initrd.img-2.6.35-22-generic

I've never had a single problem install ubuntu before. 10.04.1 is having the same problem too.

---

### Post by flatko on 2010-10-12
Is there a reported bug, related to this issue? We can report it, but I'm not familiar with reporting bugs. This is a serious problem and maybe it's related to a specific hardware.

---

### Post by lonegeek on 2010-10-12
An error finally came up in 10.10. I changed the hard drive/ dvd drive cabling. 

SQUASHFS error: Unable to read page, block 1b3bf3b9, size e7e3

---

### Post by mörgæs on 2010-10-12
Sorry, I am losing the overview. How are you trying to install, with CD or USB? If USB. how did you create it?

---

### Post by lonegeek on 2010-10-12
> **mörgæs said:**
> Sorry, I am losing the overview. How are you trying to install, with CD or USB? If USB. how did you create it?

With a cd. Burned at 10x with Disk Utility on OSX. 

I'm going to back up my 250 gb hard drive and try to install to that.

---

### Post by lonegeek on 2010-10-12
Just tried with another hard drive.

"Bootloader install failed"

The disc was verified when I burned it. Something is seriously messed up.

---

### Post by Tobias2 on 2010-10-13
I tried it twice and had the same problem. My System:

AMD Sempron 3100+ 1,81GHz, 1,5GB Ram.

It could really have to do something with the hardware. One more thing: I tried to install the 32Bit version on 64Bit System. Maybe there is a problem. I try installing the 64Bit version soon.

---

### Post by mörgæs on 2010-10-13
> **lonegeek said:**
> With a cd. Burned at 10x with Disk Utility on OSX. 

I'm going to back up my 250 gb hard drive and try to install to that.

Have you tried with a USB stick created with Unetbootin?

---

### Post by mörgæs on 2010-10-13
> **Tobias2 said:**
> I tried it twice and had the same problem. My System:

AMD Sempron 3100+ 1,81GHz, 1,5GB Ram.

It could really have to do something with the hardware. One more thing: I tried to install the 32Bit version on 64Bit System. Maybe there is a problem. I try installing the 64Bit version soon.

It is very unlikely that 64 bit works if 32 doesn't. The other way around is a good test, but I doubt this one will help.

Best is to try some different install media.

---

### Post by lonegeek on 2010-10-13
I'll try a usb stick.

Also, this computer is only 32 bit.

---

### Post by pailale on 2010-10-13
I am having a similar installation problem.

I have tried the 32bit versions of ubuntu and kubuntu and the same thing happens. The installation seems to be progressing fine and then when it comes to install the boot loader it brings up an error saying it can't compete the installation because an error has occurred.

I have tried doing the installation in Virtualbox and something similar happens. This time though virtualbox just quits when it gets to the error. I have tried installing from a cd and directly from the iso file and get the same problem. I have checked the checksums on the iso's and they are fine.

---

### Post by lonegeek on 2010-10-13
> **pailale said:**
> I am having a similar installation problem.

I have tried the 32bit versions of ubuntu and kubuntu and the same thing happens. The installation seems to be progressing fine and then when it comes to install the boot loader it brings up an error saying it can't compete the installation because an error has occurred.

I have tried doing the installation in Virtualbox and something similar happens. This time though virtualbox just quits when it gets to the error. I have tried installing from a cd and directly from the iso file and get the same problem. I have checked the checksums on the iso's and they are fine.

What kind of motherboard do you have? I have a K8N3 chipset (afaik) and I believe another person in this thread also has a similar setup.

What's strange is that I get the same error with 10.04.1 now. Not even that will install.

---

### Post by lonegeek on 2010-10-13
Just installed from usb drive just fine.

I'm assuming there is some sort of conflict or issue with my disc drive. As, all 3 discs I had burned had the same problem installing a bootloader.

EDIT: Actually it won't boot. NTDLR is missing.

---

### Post by cristianrosa on 2010-10-13
So installing from a USB drive solved your GRUB install problem?
I'm experiencing the same problem on a machine with two drives one sata and ona pata, when trying to overwrite my old lucid instalation (on the pata).

---

### Post by lonegeek on 2010-10-13
Well it claims to have installed yet its just a flashing white line and doesnt boot.

I'm running out of ideas.

---

### Post by mörgæs on 2010-10-13
So am I, almost... All I can think of regarding a clean install is here:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

Have you tried the alternate ISO? 
Various ways of installing on the USB stick?

---

### Post by lonegeek on 2010-10-13
It works now. 

I guess just took a lot of times.

It sits at the flashing white line for quite a while before you realize its booting.

---

### Post by mörgæs on 2010-10-14
Congratulations. Good to be persistent!

---

### Post by Tobias2 on 2010-10-18
I figured out, that I can boot form a build in card reader. So I tried to install a 32bit version from a SD-Card without success. Then I tried installing the 64bit version excepting also no success. But I didn't faced any problems. The weekend turned to be successful:)

---

### Post by flatko on 2010-10-19
Well, I finally got it to install from Alternate CD, but most things don't work. 
NetworkManager can't handle 2 network cards, if i set the local network, Internet access stops (it still shows "Connected"). This is important, since I share the connection to the other room. In 10.04, everything works fine.
Gwibber don't work with Facebook, there's no button "Add", so I can't add the FB account. None of the fixes in the forums work for me.
Rhythmbox can't be closed in any way, it stays open in the Volume control applet forever.

At this time, there's no reason for me to upgrade (I tried it in a separate HDD, just for the experiment). The strange thing is that the Beta worked fine, it even installed from the LiveCD.

---

### Post by bluethug on 2010-10-19
> **mörgæs said:**
> Sorry, I am losing the overview. How are you trying to install, with CD or USB? If USB. how did you create it?

Help!, I am new on Ubuntu, im trying to install the Netbook Remix 10.10 from USB, i build the USB with MultiBootISOs-2.1.3.5.exe, when i run the installation everything looks good but then stops on the "Who are you?" screen, i've already type mi name, computer's name, username, pw, and pw confirmation, and the Forward button is still disabled!, i can't complete the instalation, the status bar say "ready when you are", may be is a simple stupid question but i'm a newbee and i'm looking forward to star using ubuntu

---

### Post by mörgæs on 2010-10-19
Hi, welcome to the forum. 

Have you tried a username with only small letters and no spaces and the like?

---

### Post by mörgæs on 2010-10-19
> **flatko said:**
> Well, I finally got it to install from Alternate CD, but most things don't work. 
NetworkManager can't handle 2 network cards, if i set the local network, Internet access stops (it still shows "Connected"). This is important, since I share the connection to the other room. In 10.04, everything works fine.
Gwibber don't work with Facebook, there's no button "Add", so I can't add the FB account. None of the fixes in the forums work for me.
Rhythmbox can't be closed in any way, it stays open in the Volume control applet forever.

At this time, there's no reason for me to upgrade (I tried it in a separate HDD, just for the experiment). The strange thing is that the Beta worked fine, it even installed from the LiveCD.


When there are so many bugs best is to stay with 10.04, which is finally getting stable. Frankly I don't understand why people are so eager to get rid of 10.04.

---

### Post by bluethug on 2010-10-19
> **mörgæs said:**
> Hi, welcome to the forum. 

Have you tried a username with only small letters and no spaces and the like?

Many Thanks mörgæs, as simple as that.

---

### Post by suelynnes on 2010-11-03
Hi, I had the same installation issues with 10.10 until I decided to pick my partition manually. Both the beta install live cd and the release sent the bootloader to my second drive not to the drive I was installing the OS on. I corrected this by doing the partitions manually and have not had an issue since. I have not tried it with any other media, but the live CD I used today, had the same problem of not booting after install, so I redid it and manually parititioned the drive and it works great now. I think someone needs to look at the default setting for the bootloader on the live CD. Just a thought.

---

