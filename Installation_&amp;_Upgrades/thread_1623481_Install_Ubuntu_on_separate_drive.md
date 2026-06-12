---
title: "Install Ubuntu on separate drive"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by hawkdrv on 2010-11-16
I have searched and read an older tutorial on installing Ubuntu 9.xx, but I'm looking for newer instructions on how to install the latest version under the following conditions:

Drive C is Win XP/SP2
Drive D is Win7

Windows boot selection gives me the option of selecting either WinXP or Win7.  

I want to install Ubuntu on a separate drive, ie., E, and be able to select Ubuntu or WinXP or Win7.

How do I accomplish this?  I have no formal Linux experience, but I'm willing to learn.  Thanks.

---

### Post by oldfred on 2010-11-16
Welcome to the forums.

Separate drive is best case. You can leave your current drive as is and reboot it from BIOS if ever needed. You do have to be careful to install grub2 to the MBR of the second drive and then in BIOS set the second drive as the boot drive.

You will not (easily) be able to directly boot both Windows from grub. Windows moves the boot files from the second install to the first install, so the second install can only be booted thru the first.

If reinstalling windows you can do it.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Not sure if you can move boot flag and repair the second install and then boot it directly.

Some issues with the new installer. To get the choice of where to install grub you have to use manual install. I always partition in advance, so I have not seen the issue. I would suggest you do that also.

Some examples of installs and issues:
[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.dedoimedo.com/computers/ubuntu-maverick.html](http://www.dedoimedo.com/computers/ubuntu-maverick.html)
Full Disk Install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)

---

### Post by hawkdrv on 2010-11-16
What if I just discount the idea of being able to select any of the three installs from the main boot drive and just install Ubuntu to the third drive all by its self.  Can I do that, and from the BIOS just select the third drive manually or set it to boot to that drive?

Or, perhaps there's more to it (and I expect there is)?

Also, when I was "testing" the latest release using a CD (also tried with a USB stick) the boot up and loading, as well as shutdown, as terribly slow.  I would guess about 15-20 minutes to get to the main "desktop".  Once loaded it was fine. But to shutdown, it took a little over 10 minutes.  Is this normal?

This is my main reason for installing to a separate drive.  I lost a lot of confidence because of the slow boot/shutdown.

---

### Post by oldfred on 2010-11-17
CD's are slower but those times are very slow. 

Both my laptop and desktop that are about 3 years old  and mid priced systems, they boot in under a minute and shut down in 10-15 seconds. The more drives you have and the more NTFS partitions that you mount slows boot slightly, I have 3 drives and several NTFS (XP & shared data) and an old FAT partition that I mount normally as part of boot.

If you really want fast boot you have to have SSD and only mount / (root) with /home as part of /. Certain hardware also may be faster, but I am happy with less than a minute to boot and am waiting for SSD's to come down in price.

I have 3 installs of Ubuntu and XP. I boot from sdc and have installs of Ubuntu in sdc5 Karmic, sdc7 Lucid & sdb2 Maverick. with XP in sda1. Grub2 finds all of them and lets me boot anything.

---

### Post by hawkdrv on 2010-11-17
Not sure why it's so slow either.  I have a i7 920 processor with 6GB RAM, boot drive is raptor along with 3 other WD 7200rpm drives.  I mean, even Windows will boot in 30 seconds.

I'm still interested in knowing if it is possible to install Ubuntu to a separate drive and just boot directly to it from the BIOS (without modifying/putting anything on my usual C drive).  I'm confused.  Too many tutorials and researched posts, but nothing I can find really answers this question.

---

### Post by oldfred on 2010-11-17
You can use BIOS to choose which to boot, and I occasionally do that when moving boot loaders around or testing to make sure each drive boots. But grub2 lets you directly boot any installed system. 

But you must be sure to install grub to the drive you install Ubuntu. They seem to have made it more difficult with Maverick and you only get the choice on where to install grub if you use manual install. I always partition in advance and use manual install so I have not seen the issue.

[http://ubuntuforums.org/showthread.php?t=1622388](http://ubuntuforums.org/showthread.php?t=1622388)
[]("http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml")
Full Disk Install
[http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat](http://www.howtoforge.com/the-perfect-desktop-ubuntu-10.10-maverick-meerkat)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)

Some suggest uninstalling other drives to be sure not to install grub to the wrong drive. I have not had issues but if unsure that will definitely prevent any issue. Grub will boot using UUIDs so even if drive order changes it should boot. But you may need to rerun some config to make sure it reinstalls to the correct drive once all drives are plugged in.
to get grub to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc

And in worse case it is not all that difficult to reinstall any bootloader if you have a liveCD and a windows repair CD.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Video drivers have been an issue for many, what video card do you have?

---

### Post by hawkdrv on 2010-11-17
Video card is NVidia GeForce GTX 275

---

### Post by hawkdrv on 2010-11-17
For some reason, my system just doesn't like Ubuntu.  I did the following:

Booted from CD:

from boot start to background (purplish cloud-like screen) displayed on screen = 55 sec.
from boot start until "Ubuntu" with five dots (. . . . .) displayed 3:57
from boot start until Welcome screen 4:35

This time, I clicked on install just to see what options it would give.

Then I cancelled all that to return back to the welcome screen.

After about 5 minutes, the system completely shutdown and powered off.  I couldn't get it to reboot.  It would power on but no post.  I had to remove the power cord twice and let it sit a few minutes and then finally I could get back in to my Windows XP.

Crazy!

---

### Post by oldfred on 2010-11-17
I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
Possible additional things to run once nvidia working:
gksudo nvidia-settings
sudo nvidia-xconfig

---

### Post by hawkdrv on 2010-11-17
I booted from the CD and pressed F6, then selected the nomodeset option.  It took a little over 5 minutes to get the desktop.  As before, I was able to poke around a little bit, and it seemed to be working as it should.  The only difference was the display of the desktop itself (video setting), of course.

Then, I selected the shutdown option.  

The system began shutting down.  After 30 seconds, the CD was ejected by the system.  I waited for over 20 minutes and it never shutdown.  It was frozen with the cursor on a blank desktop background (default one that ubuntu uses).  I had to do a hard reset.

Interestingly when I rebooted (to WinXP) my network adapter showed cabled unplugged.  It wasn't.  And, using IPCONFIG, I had no IP address.  The other day, when I first booted unbunto from CD, it hung on shutdown.  When I rebooted to WinXP, my ethernet port showed cabled unplugged.  I checked the ethernet port, and it stayed lighted with a solid amber light, even when I removed the plug.  (This time (today) no lights on ethernet port.)

The only way I could get my ethernet port to work again was to remove all power from the system (unplug power cord---reboots and shutdowns with the power button did not work) and wait about a minute and restart.

This is really strange.  I have never encountered anything like this before.  I can't imagine what is causing long boot ups, frozen shutdowns and weired things with the network ports.  You got any other ideas before I just call it quits with my attempt at this unbuntu thing?

---

### Post by oldfred on 2010-11-17
There is a minor bug on shutdown of CD. It seems to exit before it is done. I think I got it to work just by pressing enter. I normally use USB now so I do not have that problem. But I think I still have to press enter at the end of a live session to get everything to close.

Your issue with Ethernet card. I remember several years ago someone had something similar and we all said it was impossible as each system is independent. But it turned out that the card did save some data somehow between reboots. I thought the issue had been fixed as I have not recently seen anything like that. Not sure if just not having full shutdown was your cause or not.

---

### Post by hawkdrv on 2010-11-18
I used a USB stick and booted.  Took 53 seconds to reach the click to "test" or "install" screen.  I selected test.  After about 90 seconds, I was at a working desktop.  I selected shutdown (also pressed enter afterwards--not sure if that made a difference or not) and the system shutdown within 10 seconds.

I rebooted to Win XP, and no problems with ethernet ports.

Problem solved as far as that goes.

I still need to get a handle on how I'm going to install to the separate drive.  I've go to read up on Grub2, as I'm not familiar with how it works.  I will go back and read your links again and see if I can grasp it all.

Thank for your help.

---

### Post by oldfred on 2010-11-18
Everyone has different suggestions on partitioning and none are really wrong. It depends greatly on how you use system, how you plan to upgrade and things that change over time. I used just root & swap with a shared NTFS partition for years but then changed things a lot with a new drive & lots of room to work.

You do need to partition in advance to get the combo box on which drive's MBR to install grub2 and if the third drive then you want grub2 on the MBR of sdc. Then in BIOS boot the drive that is sdc.

Ubuntu's standard install is just / & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

But, I like to have several 25GB roots if hard drive is large enough, I prefer separate /data over /home but that requires a little more configuration after the install to set up. Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM.

---

