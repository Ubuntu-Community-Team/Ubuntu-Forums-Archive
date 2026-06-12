---
title: "Ubuntu won't install. Absolute Newbie."
date: 2015-04-14
forum: Installation &amp; Upgrades
---

### Post by andrew214 on 2015-04-14
Hey guys,

I'm an absolute newbie with this and a computer layman. I appreciate any help I can get.

I have a Dell XPS 15Z that I am trying to install Ubuntu 14.04 on. It was previously running Windows 7, however, the hard drive failed a couple days ago. I bought a used hard drive from a from a local repair shop and am attempting to install Ubuntu on it. I really have extremely little experience with fixing computers so please excuse me... 

I created a bootable USB and DVD, however, neither work. Here's what happens:

USB:

-The computer boots up to the menu and I can select any of the options. 
-If I select Install Ubuntu it will start the Ubuntu install very slowly and will freeze up before I can actually do the install. One time I got though a couple of the preference screens but it had some errors such as "error opening /dev/sdb" and then it freezes.
- If I select Try Ubuntu Before Installing it loads up very slowly and is basically unusable. If I try to use the install Icon it won't do anything.

DVD:

The computer boots up and loads the DVD. Ubuntu does not load and I get what looks like a "dos screen"(black screen with text going across it quickly) and it ends with an error saying "cannot find medium live file system" Then it does nothing.

I've been at it for hours trying different USB's and different DVDs with no luck. I also reformatted the hard drive to NTFS with no luck.

Where do I go from here? 

Perhaps the computer has more issues than just a failed hard drive?

Again, appreciate any direction someone can point me in. It would be much better if I can get this computer working so I can get my project done on budget....

---

### Post by Bashing-om on 2015-04-14
andrew214; Hi ! Welcome to the forum .

First things 1st; Did you verify the .iso file ?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows](http://www.linuxquestions.org/linux/answers/LQ_ISO/Checking_the_md5sum_in_Windows)

Next; Did you verify the burn(s) ?
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows](http://www.ubuntu.com/download/desktop/burn-a-dvd-on-windows)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

With known good medium in hand, we can proceed.

[INDENT][INDENT]all in the process
[/INDENT][/INDENT]

---

### Post by grahammechanical on 2015-04-14
According to this link that machine has hybrid graphics, also called Nvidia Optimus technology. It has both an Intel and an Nvidia graphic adapter. It could be the installer is getting confused about which graphic adapter to use. 

[http://www.pcworld.com/product/917937/dell-xps-15z-notebook.html](http://www.pcworld.com/product/917937/dell-xps-15z-notebook.html)

Is it possible to set the machine to use either the Intel adapter or the Nvidia adapter for the purpose of installing? The installer uses an open source video driver which will work with either Intel or Nvidia video adapters but I have no idea how well it works when both adapters are available.

The Nvidia drivers that come with Ubuntu 14.04 and later versions do work with Hybrid graphics but they do not do automatic switching of adapters. That has to be done through the Nvidia Xserver Settings utility that will install along with the Nvidia video driver. You can search for it in the Dash once Ubuntu is installed. Click the Ubuntu icon at the top of the Launcher (side panel) and search for Nvidia.

Or you can install Prime Indicator which will put an app indicator in the top panel and you can use that for switching video adapters.

[http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html](http://www.webupd8.org/2014/01/prime-indicator-lets-you-quickly-switch.html)

Regards.

---

### Post by andrew214 on 2015-04-14
Gentlemen,

Thanks very much for the replies.

Bashing, 

I have redownloaded Ubuntu and tried it again following your steps as indicated. As far as I can tell everything should be good to go. However, it still is not working. I took some pictures with my phone. This is what happens first:
[IMG]http://i.imgur.com/xCZwKQM.jpg[/IMG]

Then the screen goes black for about 2 min and then this shows up:
[IMG]http://i.imgur.com/bQ1N6JL.jpg[/IMG]

That's all it does. It does not let me type anything.
[COLOR=#000000]
grahammechanical,

It does indeed have an extra graphics card. I searched through BIOS and could not find a way to shut any of them off. I did a google search and it seems like many others have been wanting to do the same thing but cannot find a way to do it either. (without windows being installed that is). That could very well be the issue...

[/COLOR]

---

### Post by oldfred on 2015-04-14
Your drive is showing frozen as the status. 
Does UEFI/BIOS show drive correctly?

And sr0 is your DVD, and it then shows an error. It should boot even without a hard drive.
So seems DVD burn was not correct.

Did/does this system have Intel SRT or similar? The Intel settings for that can cause problems.
Make sure UEFI has hard drive settings changed from Intel SRT to AHCI.

Then try flash drive again.

---

### Post by andrew214 on 2015-04-14
oldfred,

Funny you say the DVD is frozen... I was actually just wondering if the dvd drive still works in it. I honestly can't remember the last time I tried to use it. Also, yes it is set to AHCI.

UPDATE:

I just successfully installed 12.4.5 32 bit via USB. Everything seems to be working so I am now attempting to upgrade it to 14.04 32bit. I will update once it completes.

Perhaps it was the 64 bit version causing issues? I think it should work with 64 though, as the windows 7 was 64 bit. It has an i7-2630m processor and 8 GB of ram. If possible I would like to utilize the 64 bit version...

---

### Post by oldfred on 2015-04-15
Not sure why 64 bit should not work, unless original download of ISO had an error?
The 32 bit version will only install in BIOS boot mode.

With and i7, you should use 64 bit.
Is system only BIOS or UEFI and CSM.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

Frozen was on ata2 which I guess is hard drive. 
But sr0 is DVD.

Post this from either live installer or your 32 bit install:
sudo parted -l

---

### Post by andrew214 on 2015-04-15
Ok, so, here is a series of events that took place:

-12.4.5 32 bit installed fine with a USB.
-After testing it out for a few min I decided to try to upgrade to 14.04 32 bit. 
- 14.04 installed but would not work. It would only get me to a "grub screen" where it would ask me to select Ubuntu or recovery mode. If i tried either it would go to a black screen for a minute or two and then restart the computer.
- I formatted the hard drive.
- I tried to install 12.4.5 64 bit with USB.
- It failed to install and froze up the same way the 14.04 64 bit would. It always freezes up when I try to use the keyboard (The first time you use the keyboard is to connect to wifi).
- I then installed 14.04 32 bit with USB and it installed perfectly. I am currently using this version.

When I type you command in to the terminal I get this:
[IMG]http://i.imgur.com/Fb81a6e.jpg[/IMG]

Also, while I was typing this up the screen went black (I thought it was just a screen saver) and I got this error:
[IMG]http://i.imgur.com/v9hyHB7.jpg[/IMG][IMG]http://i.imgur.com/v97bDnN.jpg[/IMG]

Regarding the BIOS vs UEFI.. Sorry, that's a bit over my head. I tried to do a google search but didn't come up with anything I understood.

Thanks very much for your help.

---

### Post by yancek on 2015-04-15
It's not possible to read the error message in the image.  Could you post what comes after "Sorry, Ubuntu 14.04 has ...??

---

### Post by andrew214 on 2015-04-15
> **yancek said:**
> It's not possible to read the error message in the image.  Could you post what comes after "Sorry, Ubuntu 14.04 has ...??

Sorry, it said "Ubuntu 14.04 has experienced an internal error".

The first line in the text box that's hard to read says:
 "Executable Path
/usr/bin/compiz"

For what it's worth, I've been using the computer for about 1 hour now without issue.

---

### Post by oldfred on 2015-04-15
I would think the issue is with video drivers in the 64 bit, but do not know for sure.

Most users with newer Dell systems have installed in UEFI mode.
For lots of info and many links to too much info see link in my signature below.

Have you updated your UEFI/BIOS to the latest version from Dell?

Dell issues are common across models.
       Dell Inspiron 3521
[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)
Ubuntu on the Precision M3800 or XPS15 Nov 2013
[http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx](http://en.community.dell.com/techcenter/b/techcenter/archive/2013/11/14/ubuntu-on-the-precision-m3800.aspx)
[https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z](https://wiki.ubuntu.com/HardwareSupport/Machines/Laptops/Dell/XPS/15z)
Dell 14z & 17r with Intel SRT
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Dell 17R Brightness
[http://ubuntuforums.org/showthread.php?t=2195650](http://ubuntuforums.org/showthread.php?t=2195650)
[http://ubuntuforums.org/showthread.php?t=2204287](http://ubuntuforums.org/showthread.php?t=2204287)

---

