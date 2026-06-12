---
title: "Two Install Scenarios"
date: 2007-06-02
forum: Installation &amp; Upgrades
---

### Post by Toxicityj on 2007-06-02
first scenario-
I want to duel boot Vista and Ubuntu, but the last time I did that, it froze during the partition and I had to reinstall Vista and I never got to use Ubuntu. And I've heard about how difficult it is to duel boot Vista and anything, so is there a way to duel boot the two without me losing Vista and all of my files?

second scenario-
I recently bought a 250GB external harddrive (its truly a beautiful thing). What I want to do is install Ubuntu on that and boot from it on my other computer, but also be able to plug it into my laptop and use it for backing up stuff. So basically I'm wondering if its possible to use half or so of the drive for Ubuntu and the other half as storage that i can plug into any other computer w/o it trying to boot up Ubuntu or something.

thank in advance :)

---

### Post by Toxicityj on 2007-06-02
anyone... at all?

---

### Post by fsando on 2007-06-02
I don't have an answer to your question but I think your chance of an answer is much higher if you post in 'absolute beginner'

---

### Post by Herman on 2007-06-02
Hello Toxicityj,
Okay, I know how you feel. My wife was out one day and I had always promised her I would update her computer. 
She had Windows XP and Breezy and Dapper triple boot. She wanted me to replace Breezy with a nice fresh install of Feisty Fawn.
I had noticed already that her PC seemed to have a lot of strange problems with doing things from a LiveCD such as partitioning and installing. 
We have an identical pair of [Acer Aspire T310]("http://www.acersupport.com/desktop/aspire/html/as_t310.html")'s, with ATI Radeon 9200 graphics cards and we have never had any problems dual booting before. 
In fact I even made a website to help other people dual boot!

During installation I wanted to do some partition re-arranging and equalize the sizes of her two Ubuntu partitions. 
Well her computer froze up during partitioning didn't it!  Whatever happened cause her partition table to be corrupted. 
I could have recovered it again with TestDisk probably, but I decided to wait 'till she came home to decide what to do next. 
Well she didn't care at all! She already had all her music backed up in her laptop and she doesn't use Windows in her Desktop anymore, she only likes Ubuntu. 
She wanted me to go ahead and not to worry about Windows XP. I don't know why, but I still put Windows back in again anyway, just because it's there I guess. 
We have Acer's Windows 'Recovery Disks', that delete everything on our hard disks and return the computer to its 'factory shipped state', (with Windows XP taking up the entire disk). 
So I guess that means it's wise to put that in first just in case she changes her mind later and it turns out she does want Windows XP for something. (Unlikely but I have to 'cover' myself against that possibility).
It takes three CDs to re-install Windows in it's bare-bones state, then a CD for Service Pack2, then one for Works 7.0 before Windows can even do anything. 
Then there's another CD for the NTI CD&DVD Maker, another for the printer driver and another for her camera and so on...
I didn't actually waste my time feeding her computer all those CDs, I just put in the bare bones Windows XP and SP2, at least Windows is in in case she ever wants it for anything. (I doubt it).
Then I put in the Feisty install CD again. Just one CD for Ubuntu installs more software than about ten or a dozen CDs we would have needed to enable even basic functionality in Windows XP.
It red screened about half way again but this time I got a message about an error (disk read error or something), often caused by a dirty or scratched CD or a dirty CD drive, please check your CD and/or clean out your CD drive and try again.
A dirty CD Drive? - That's the problem exactly, I had suspected that already and now I was sure of it!  Ubuntu is so cool!   :D
First I tried  [Cleaning a CD or DVD ROM Drive]("http://www.computercleaningguide.com/dvd-cd.htm") but that wasn't enough. So I took her computer apart and removed the CD/DVD drive and took it apart and cleaned it out, like this, [Cleaning Your (XBox) DVD drive]("http://www.llamma.com/xbox/Repairs/cleaning_your_dvd_drive.htm") and now that it's all back together it works 100% better than it did before. It was filthy! 
After that I had no more problems and I installed Ubuntu Feisty Fawn for her and Ubuntu Ultimate Edition as well. She's really happy now, she really loves Ubuntu and I don't think she has even booted Window XP even to take a look at it. I may never have to install all the rest of those Windows apps and drivers disks and sit there rebooting it all day long. What a waste of time!
I do suspect however that the fact that so much software is jammed onto one disc for Ubuntu could exacerbate problems like a dirty CD drive though. 

Your particular problems could stem from an entirely different cause, but I would hazard a guess that a good percentage of Ubuntu install problems could be averted by better hardware maintenance,particulary for the CD/DVD drive. That was my story anyway.

We haven't got Vista and I don't expect we'll ever want it either, so I can't tell you much about dual booting Vista. There are some links in my website about that if you want to check those. (Click my first signature link, and click one of the NTFS install pages, they are right near the top there somewhere).
I'll make another post commenting on how to install Fesity in a USB drive shortly, however I am more in favor of internal hard disk installs.

---

### Post by Herman on 2007-06-02
A lot of people seem to want Ubuntu in an external USB disk for some reason.
Not all  PCs have a BIOS that supports booting from a USB, you need to have a computer that can do that before you can start. Here's how I boot my USB drive in my computer  that does support it, [  How I boot from my BIOS]("http://www.users.bigpond.net.au/hermanzone/p1.htm#How_I_boot_from_my_BIOS_with_my_F12_key") with my F12 key (or F8 key in most PCs).

Then when you install Ubuntu it will probably work in some PCs and not in others, because of hardware differences. You may need to run  sudo dpkg-reconfigure xserver-xorg (video, keyboard & mouse drivers, settings) when you plug it into a different PC, like this, [Xserver Page]("http://users.bigpond.net.au/hermanzone/p7.html").

 If you just want to use it in one PC, then okay, but then why not pull the disk out of the USB case and bolt it into the computer and just plug it in to an IDE cable or SATA port?

Well anyway, I happened to have an old laptop hard disk lying around in a usb case and it already had Ubuntu installed in it so I decided to see if I could get it to boot up. I made a small ext2 partition in it and copied Super Grub Disk for USB into it first. Super Grub Disk is better for USB dirves than regular Grub because not only can Super Grub help you boot your and your friend's computers when they have a problem, it also has special patches to it's grub called 'usbshift' and 'setgrubdevice', which mean the USB drive's Grub doesn't assume the USBDIsk is the first hard disk. That makes it simpler to edit the grub menus in operating systems inside the USB Disk. (In my opinion anyway).
I copied Super Grub Disk for usb to the partition I made for it with a 'sudp cp' command. Then I installed Super Grub Disk's Grub IPL to MBR in the USB disk from a grub shell in my installed system, something like this, [reinstall Grub]("http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD").
Then i edited the operating system's /boot/grub/menu.lst file and it's /etc/fstab file to change all instances of (hd0,2) to (hd1,2) , and all instances of 'dev/hda3' to '/dev/sda3' instead. The only reason I had to do that was because that was an old install of Ubuntu that was configured for my laptop, not for running in a USB external enclosure. I had to run 'sudo dpkg-reconfigure xserver-xorg' the first time I booted it too.
Then I edited Super Grub Disk fro USB's /boot/sgd/menu.lst file with a line for a menu.lst of my own, like this,
```
default 2 # Go directly to SGD menu
foreground ffffff
background 0c00ff
color white/blue yellow/cyan
#splashimage=/boot/sdg/gotera14.xpm.gz
#gfxmenu /boot/grub/message

title <--Main Menu.lst #0
catis off
configfile $(grub_device)/boot/grub/menu.lst

title *S.G.D. Language Selection. #1
catis on
configfile $(grub_device)/boot/sgd/menu.lst

[COLOR=Red][B]title  Super Herman Grub Menu #2
catis on
configfile $(grub_device)/boot/sgd/S10en/hermanmenu.lst
[/B][/COLOR]
title English Super Grub Disk #3
catis on
configfile $(grub_device)/boot/sgd/S10en/menu.lst
```After that I made a text file and named it 'hermanmenu.lst', and copied it to my /boot/SGD/S10en directory, it looks like this, 
```
default 0 
foreground ffffff
background 0c00ff
color white/blue yellow/cyan
#splashimage=/boot/sdg/gotera14.xpm.gz
#gfxmenu /boot/grub/message

title  Ubuntu Feisty Fawn
configfile  (hd1,1)/boot/grub/menu.lst

title  Ubuntu Dapper Drake
configfile  (hd1,2)/boot/grub/menu.lst

title  Ubuntu Edgy Eft
configfile  (hd1,5)/boot/grub/menu.lst

title  Back to Super Grub Disk
configfile  (hd1,3)/boot/grub/menu.lst
```As you can see, actually I ma triple booting in my USB disk. The extra operating systems were already in there, the Dapper Drake one is good, that's the one I was working on to begin with. The Edgy Eft one is no good, it's broken because of an experiment I tried and can be deleted. The Feisty Fawn installation is new, it replaces an old Breezy install. 

Installing Feisty Fawn over the old Breezy install was very simple and straight forward and simple, anyone would be able to do that. I used the 'Alternate CD' and installed Grub to the first sector of its own partition. Then I edited the hermanmenu with the configfile entry already shown, and that was it! Super Grub for USB does the rest.
It will only boot easily up in my own computer though, because I have an ATI graphics card. My wife's computer is identical to mine but she has a 17" monitor and I have a 20" one, they use different resolutions, so I'd have to run sudo dpkg-reconfigure xserver-xorg every time I switch, but after the first time I could use a command to switch /etc/X11/xorg.conf files each time. I could make a script for changing xorg.config files. Actually I imagine if someone used a vesa driver they could probably just plug their usbdisk into most computers and boot it up okay if they chose computers with monitors about the same shape. It won't boot in either of our laptops either because those don't support booting USB devices and also they have widescreens of another different ratio. Right now I'm trying to boot it in my AMD64 computer and it has frozen right away. AH, I got a 'tty error, busybox dropping to a shell'. The problem with the AMD64 computer is it's BIOS doesn't have  the boot menu when I press the F8 or F12 keys, so I am trying to boot with the AMD64's Feisty install's Grub, rather than with Super Grub Disk's Grub, so I am not now able to use 'usbshift and 'setgrubdevice'. I can still boot it up with Grub's Command Line Interface though.

I have a perfectly good how-to on using Knoppix and making a nice persistent /home for Knoppix in a USB disk here, [Knoppix Page]("http://users.bigpond.net.au/hermanzone/p20.html"). In my opinion that's a much more practical way to use a USB drive. Knoppix boots in any computer and you won't have to learn all about editing all kinds of operating system and boot loader configuration files.

I think if you want to use Ubuntu, install to an internal disk, and if you want to use a USB, I recommend Knoppix.
USB Disks are great for data storage, that's what my wife and I use them for mainly. She takes her 2.5" laptop hard drive to work and brings home data to work on with her home computer so she can spend more time at home.

That's just my opinion, 
Regards, Herman :D

---

