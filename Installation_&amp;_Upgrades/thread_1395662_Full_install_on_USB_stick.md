---
title: "Full install on USB stick"
date: 2010-02-01
forum: Installation &amp; Upgrades
---

### Post by parker13 on 2010-02-01
Hi,

I'm trying to make a bootable USB stick.

I tried various methods of making a persistent live USB (using a casper-rw filesystem), but they seem a bit compromised.

So, I've tried doing a full install onto USB. I did this by booting the live CD and changing the target to the USB stick, remembering to click advanced and changed the GRUB boot loader install to /dev/sdb.

This works fine. However, when I try to download my wireless driver using the jockey Hardware Drivers app, it says: "failed to fetch [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com)... Could not resolve gb.archive.ubuntu.com"

With a persistent USB install, Ubuntu can find the driver without having to connect to the internet. Why does this not work for a full USB install?

---

### Post by djdan2k8 on 2010-02-01
> **parker13 said:**
> Hi,

I'm trying to make a bootable USB stick.

I tried various methods of making a persistent live USB (using a casper-rw filesystem), but they seem a bit compromised.



I used system > Administration > Create Usb Start Up Disk

This worked really well for me as my original Ubuntu Live CD is a bit old and didnt work too well lol.

---

### Post by parker13 on 2010-02-01
Maybe I posted this a bit early as I've worked it out.

Basically, the live CD comes with its own little repo. So, to replicate this on the USB stick, just copy it from the CD (here, I have both the CD and USB stick mounted on another machine):

```

sudo mkdir /media/yourusb/ubuntu
cd /media/Ubuntu\ 9.10\ i386
sudo cp -rp pool dists /media/yourusb/ubuntu/

```

Then just change the APT sources.list on the USB to include the new location:

```

sudo vim /media/yourusb/etc/apt/sources.list

```

Add the following at the top:
```

deb file:///ubuntu karmic main restricted

```

Boot from the USB, do an "sudo apt-get update" and the Hardware Drivers screen should be able to load the wireless driver from the USB stick.

---

### Post by garvinrick4 on 2010-02-01
I have done these USB installs with a /boot,/and swap all in ext3 using LIVE CD as medium and install to USB stick. After sudo apt-get update and upgrade all worked just as install on Hard disk. It will look for mbr on main drive no matter what. System does grub-update on upgrade on its own also, so can not avoid. Will put itself in mbr and if you use it on a machine without
grub2 it will install grub2 on that machine. If you want to use it on your machine with Linux already installed it is great.
 The USB installs from programs installed will use Fat32 and have a persistence of 4 gig. Then set to do no updates in software sources. Will never look for mbr so can use anywhere as Great little system just no /home, no room with 4 gig. Real nice LIVE CD, they are a lot quicker than CD drive. 
 Never did figure out how to do one in ext format without looking for mbr but did get 16 gig persistence and is beautiful karmic setup but to be used on my machine only, friends and family will freak if they
see grub2 in there little XP system that they have used for 7 years. Just to see scrowling will give them a minor  cardiac infarction at best.

All installs on these devices have been capable of Wifi internet connection. If you got a problem, do a wired connection, if works, then
post I found a little etc/resolv.conf     thing to look at for wifi that should look into. Three lines, I copy and paste or you can command line copy.

---

### Post by parker13 on 2010-02-03
Thanks for the replies,

Does anybody know how portable a USB stick is if I do a full install? Is it possible to have the upgradeability of a full install with the portability of a live image?

What extra hardware detection does the live CD/USB image do?

---

### Post by Herman on 2010-02-03
:) Why don't you just try your regular install in a few different PCs and let us know?

In my opinion a full install in a USB stick is as portable as a Live CD or Persistence install. Maybe I'm just lucky, but it works well for me.

There are a lot of people in this forum lately who don't believe me or who have phenomonally bad luck and report that it doesn't work or they can't do it.

To prove my point I have just booted my Kingston DataTraveller G2 16GB USB flash memory stick with a standard full Ubuntu Karmic Koala in it in four different computers.

Karmic was originally installed in the USB using an Acer Aspire 1640Z laptop and it worked fine in that. It's an old laptop and it has a few hardware problems but Karmic could do everything except fix the broken hardware.

The other four computers I booted my USB full installation in include an Acer Aspire T310, a couple of boxes I put together myself and an ASUS EeePC. 
The largest monitor I used was an Acer AL2016W with a  20" screen (it was the biggest in the store when I got it but there are bigger ones for sale now), and the smallest was of course the EeePc's tiny wee 7" display.

Ubuntu detected all the hardware and set itself up automatically during bootup and I had no trouble with the display or any hardware in the four other computers I have tried it in so far. That includes the webcam and the wireless networking card in the EeePC. 

Well actually I mean since I started recording, I'm sure I have booted Ubuntu in USB sticks in lots of other computers before this. I'm always fixing other people's computers and/or installing Ubuntu for people so I know it works in most computers, but there might be the odd one or two that might be difficult. In the ones that are difficult I can't remember if those could even boot a Live CD, so I will need to start paying more attention and keeping records if I want to learn anything for sure.

Attached are the hardware lists for the four computers I just finished trying my USB Ubuntu in, just in case anyone wants to check.

---

### Post by parker13 on 2010-02-03
> **Herman said:**
> :) Why don't you just try your regular install in a few different PCs and let us know?


Yes, I know I should do that. It works fine for me on a couple of PCs, but I'm trying to help a friend online who is having problems. I was just wondering about people's experiences are with this.

Thanks for the feedback. I'll try to track down some more PCs which actually boot from USB to test it with!

Has anybody got this to work:

[http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/](http://www.pendrivelinux.com/make-a-usb-boot-cd-for-ubuntu-9-10/)

If I could get the boot CD working I could try my USB stick on more hardware, but it kernel panics when I follow the above instructions.

---

### Post by parker13 on 2010-02-05
Just a follow up.

I managed to track down 3 PCs which will boot from USB. Each has a different graphics card - nVidia, ATi and Intel.

The same USB stick works perfectly on each. Xorg loads the appropriate graphics driver.

The problems start if you choose a proprietary driver, such as nvidia. Once that is installed, an /etc/X11/xorg.conf appears. From that point on, X won't load on the other machines.

The moral seems to be that if you stick to the open source drivers, and let Xorg decide which to load, the stick is completely portable.

---

### Post by johan85 on 2010-02-05
thaks for the info on how to install...

---

### Post by garvinrick4 on 2010-02-05
[QUOTE=Herman;8767938]:) Why don't you just try your regular install in a few different PCs and let us know?

In my opinion a full install in a USB stick is as portable as a Live CD or Persistence install. Maybe I'm just lucky, but it works well for me.

There are a lot of people in this forum lately who don't believe me or who have phenomonally bad luck and report that it doesn't work or they can't do it.

To prove my point I have just booted my Kingston DataTraveller G2 16GB USB flash memory stick with a standard full Ubuntu Karmic Koala in it in four different computers.

Karmic was originally installed in the USB using an Acer Aspire 1640Z laptop and it worked fine in that. It's an old laptop and it has a few hardware problems but Karmic could do everything except fix the broken hardware.

The other four computers include an Acer Aspire T310, a couple of boxes I put together myself and an ASUS EeePC. 
The largest monitor I used was an Acer AL2016W with a  20" screen (it was the biggest in the store when I got it but there are bigger ones for sale now), and the smallest was of course the EeePc's tiney 7" display.

Ubuntu detected all the hardware and set itself up automatically during bootup and I had no trouble with the display or any hardware in the four other computers I have tried it in so far. That includes the webcam and the wireless networking card in the EeePC. 

Well actually I mean since I started recording, I'm sure I have booted Ubuntu in USB sticks in lots of other computers before this. I'm always fixing other people's computers and/or installing Ubuntu for people so I know it works in most computers, but there might be the odd one or two that might be difficult. In the ones that are difficult I can't remember if those could even boot a Live CD, so I will need to start paying more attention and keeping records if I want to learn anything for sure.

Attached are the hardware lists for the four computers I just finished trying my USB Ubuntu in, just in case anyone wants to check.[/QUOTE
Did all these boxes have linux running already? It looks for an
mbr eventually if it is running linux that is fine and the same grub. IF it looks while in a Windows machine it will install grub
to the mbr, sooner or later. You have had to use ext3 or ext4 with a /boot a / and a swap. HMMM a system that does not update grub ever? Let me know how you did that.

---

### Post by Herman on 2010-02-05
:D Thanks. 
Yes, that has been my experience too. 
It seems to me that as long as we don't load a proprietary video driver the regular install is as able to be used on the same variety of hardware as the persistence installations.
We'll only know for sure beyond our own experieces if more people will try it and let us know how they went. 

The persistence installations have the advantage that they include the Ubuntu installer.
That's useful for somebody who doesn't have Ubuntu installed in their computer yet, or someone who wants to go around installing Ubuntu for their friends. I have one with an apt cache in a spare partition with a script for installing software and updates after the installation. It also copies some how-to videos from ubuntu screencasts, and a collection of nice desktop backgrounds and so on into the new installation to help get the new user off to a good start.

The real installations in a USB have an advantage that they're able to handle all updates, including kernel updates.
If someone wants to follow a how-to in Ubuntu Web Forums Tutorials and Tips that contains commands for making some change in the operating system files they can because they're using the same Ubuntu as everybody else.
 A big advantage is they include GRUB2, so they have the dual purpose of being able to be used for booting an operating system in any computer when somebody has a booting problem. It's important to have GRUB.

---

### Post by DZ* on 2010-02-05
garvinrick4: a proper full install to a USB won't be looking for grub anywhere except on that stick, and it's not supposed to write grub to the hard drive. I've always used "Alternate CD" to install to a USB. You just have to watch where you put the grub. Other than that there is nothing special to it. It works and updates great and I confirm Herman's experience that it works fine on different computers (6 in my case, a netbook, two laptops, 3 desktops).

---

### Post by Herman on 2010-02-05
> Did all these boxes have linux running already? It looks for an
mbr eventually if it is running linux that is fine and the same grub. IF it looks while in a Windows machine it will install grub
to the mbr, sooner or later. You have had to use ext3 or ext4 with a /boot a / and a swap. HMMM a system that does not update grub ever? Let me know how you did that.@ garvinrick4
:D No, you don't to install in a lot of different partitions at all, I don't know where you got that idea from, just perform a regular installation, it's simple.
The default partition scheme will do fine, one root partition with everything in it and a swap area.
Some like a separate /home for reasons I disagree with, but each to their own likes and dislikes.
Actually, I go out of my my way to install in one single partition with the swap in a swap file, according to iva2k's thread: [HOWTO: Use swapfile instead of swap partition and have working hibernation]("http://ubuntuforums.org/showthread.php?t=1042946").

Yes, all these boxes have Ubuntu in them and some have more than one Ubuntu and other distros as well. One box, the Acer T310, still has an old Windows XP installation in it that I use for destruction testing purposes. (LOL).

It's simply not true that Ubuntu will 'look while in a Windows Machine and install GRUB.'
I have been using Ubuntu almost since it first came out in 2004, and I have never had that happen. 
Maybe you mean during installation it defaults to installing GRUB to MBR in the first hard disk. If you read any decent installation guide you should see how to install Ubuntu and control where GRUB is installed. 
Once Ubuntu is install it is possible to have Ubuntu install GRUB anywhere the user wants, but the user complete control. We have to give the commands to make Ubuntu do that, and we also need super-user priveleges, it involves typing our passwords.  It's definitely not something that can happen by accident. :D

For flash memory I recommend the ext4 file system, I used to like reiserfs before ext4 came out.
I noticed a huge performance improvement with reiserfs compared with ext3 because reiserfs is up to ten or fifteen times faster writing small files and an operating system runs on small files. Now that ext4 is available by default, I think it's as fast as reiserfs and I know ext4 is designed to work well in flash memory so it's definitely the best choice for a file system now.
I use elevator=noop as a kernel option in GRUB, and I set noatime in /etc/fstab as a mount option.
I add a line in /etc/sysctl.conf , vm.swappiness=10 so the system will prefer to use RAM instead of the swap file most of the time if it can.
Those tweaks are for speed and performance, and if they reduce memory wear that's an incidental benefit. I don't believe flash memory wear is anywhere near the issue some people like to pretend it is. When I have a flash device wear out I'll let you know. At the moment I have a few broken hard disk drives but no worn out flash memory yet. :D

---

### Post by koryGander on 2010-02-05
Thank you so much for all this info. Especially the one above with the link to a how-to site. 


____________________________________________
[SIZE=1]Here's your friendly neighborhood [irs extension]("http://www.onlineirsextension.com/").[/SIZE]

---

### Post by brallan on 2010-02-05
I wonder why a USB full install can't simply also have all of the things we would desire from a liveCD? 

Given the enourmous size of pendrives these days, why can't it be a complete system, updated and configured as each person likes, that could contain the entire repos or any part of them we choose, install a vanilla ubuntu or an updated vanilla install or even install all of the programs currently installed on the USB?

thats the liveUSB I have been dreaming about for years. If you install Ubuntu often, as I do, it's such a drag on both ourselves and the repos, to do a vanilla install, then have to update it, then install the language packs, then install the extra programs we want, remember what they all are, wait hours while it downloads the latest of each, install firefox's and thunderbird's complements, etc etc.

---

### Post by brallan on 2010-02-05
oops sorry, double posted.

---

### Post by Herman on 2010-02-05
@ koryGander, thank you. :)

@ brallan, :)
> I wonder why a USB full install can't simply also have all of the things we would desire from a liveCD?  It can.
Things will be even better when USB3 becomes widespread and USB drives will be able to transfer data through the USB3 interface as fast as a disc connected by SATAII.

IDE, SATA or USB are all just names for the kind of wires we use to plug the disc into the motherboard with really. Well, that's thanks to the excellent job done by programmers and developers, but to users it doesn't really matter which interface we use apart from the data transfer speeds. 
I'm referring to my USB with the regular installation in it here.

> Given the enourmous size of pendrives these days, why can't it be a complete system, updated and configured as each person likes, that could contain the entire repos or any part of them we choose, install a vanilla ubuntu or an updated vanilla install or even install all of the programs currently installed on the USB?
thats the liveUSB I have been dreaming about for years.Yes, that's why I have an apt cache in my USB startup disk.

I'm now referring to my other USB made by the 'System'-->' Administration'-->'Startup Disc Creator' program in Ubuntu now.

It has another partition after the LiveCD partition with a .deb cache in it and lots of goodies I have downloaded from the internet to be copied into a newly installed Ubuntu system. Some of those things are things I made myself too.

 After I install Ubuntu I run a script that copies all the .deb files into the new installation's /var/cache/apt/archives/ so very little needs to be downloaded over the internet. Then my script runs apt-get update and installs whatever softrware I have listed. When it's all done it copies the /var/cache/apt/archives/ back into the USB's apt cache to update that one ready for next time. ;)

I copy of my newest post-installation script is attached to this post just for an example of what I mean. It isn't finished yet, I'm getting it ready for when Lucid Linx is released in a few months from now. It probably won't work for anybody but me because you would need the same files and directories in your USB as I have in mine. Anyone interesting in making their own similar script might get some ideas they can use from it. Feel welcome to copy any code from it if you like.  :)

---

### Post by Browser_ice on 2010-02-05
Have you tried to directly install Ubuntu onto your USB key form the Live-CD ?

That is what I did months ago. I have now a full persistent bootable ubuntu on my 8Gb USB key. I used to have ubuntu 8.04 on it and last week I installed ubuntu 9.04 on it and I did not have to make any changes once the installation was done.  It is perfectly usable. I use it at the office on a PC that only has Windows on it.

---

### Post by brallan on 2010-02-05
> **Herman said:**
> 
It isn't finished yet, I'm getting it ready for when Lucid Linx is released in a few months from now.

Wow, that's fantastic Herman! I hope its not too complicated to figure out. Are you saying you're developing that for all of us for lucid?

now that diskspace is hardly an issue anymore, it would be so wonderful to simpy have some kind of system-wide option in the GUI/option when installing to automatically apt-cache every deb that's ever installed (meanwhile removing older versions) so that any installUSB or liveUSB with an apt-cache can work as a repo for an update or run ubiquity for a new install with all kinds of programs and updates not in the vanilla install, and the only thing that one needs to know about a USB install is the release and the date of the last update & upgrade.
 
Seems like a simple step ahead that would save incredible amounts of bandwidth for everyone, and I bet if it had an easy gui huge numbers of folks with a slow connection like myself would be thrilled. 

Anybody know if there's a brainstorm to vote on?

---

### Post by brallan on 2010-02-05
> **Herman said:**
> 
IDE, SATA or USB are all just names for the kind of wires we use to plug the disc into the motherboard with really. Well, that's thanks to the excellent job done by programmers and developers, but to users it doesn't really matter which interface we use apart from the data transfer speeds. 
I'm referring to my USB with the regular installation in it here.

yeah, for this reason at times i've though that it's too bad how the usb startup disk creater doesn't allow one to do a "liveHD" install to an internal HD. On old boxes that are terribly slow or have USB1, I've sometimes wanted to simply do a quick and dirty install so that there's a system there inside the box instead of going through a full install.  I wanted a liveUSB with the speed of an internal SATA - and wished that it would let me do it to sda1 or sdb1 instead of only higher letters.

---

### Post by Herman on 2010-02-05
> Have you tried to directly install Ubuntu onto your USB key form the Live-CD ?

That is what I did months ago. I have now a full persistent bootable ubuntu on my 8Gb USB key. I used to have ubuntu 8.04 on it and last week I installed ubuntu 9.04 on it and I did not have to make any changes once the installation was done. It is perfectly usable. I use it at the office on a PC that only has Windows on it.:D Installing Ubuntu directly into the USB drive is the main thing we're talking about, yes. As a normal operating system, the same as one would install in a hard disk inside the computer, commonly connected by IDE or SATA.
This is what I'm called the 'full installation' or 'normal installation'.

A 'Persistence' type of installation is something quite a bit different.
It behaves like a Live CD and has the Ubuntu installer in it, but it also has a partition for storing files and unlike a LiveCD, it can store added software and settings, hence the name 'Persistenence'. The 'Persistence' type of install was first made popular by the website at [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)
Even though the commands are there in black and white, a lot of people who aren't used to using the command line were not able to copy and paste the commands by themselves easily, (for some reason, ... ), and needed a lot of help. That's okay.

Now, it's easier for novices to create a 'Persistence' type of Ubuntu USB by using the 'System'-->' Administration'-->'Startup Disc Creator' program. Even people who can't use the command line can do it that way.

The reason why we used 'Persistence' type of installations before Hardy Heron came out was because a Live CD, which the 'Persistence' installs could automatically detect hardware and set themselves up at boot time.
Before Hardy Heron, a normal installation could not, if we pulled a hard drive and plugged it into a different computer it would boot to a black screen and we would have to run a lengthy process called 'sudo dpkg-reconfigure x-server.org', which took about ten or fifteen minutes. Longer if we didn't know what we were doing. Then the display, keyboard and mouse would work, (we hoped).

Since Ubuntu Hardy Heron a regular Ubuntu install will be able to  automatically detect hardware and set itself up at boot time just as well as a Live CD or a 'Persistence' USB install, or at least that's what I believe.

There are still a lot of people who believe they need an 'Persistence' type of installation for a USB flash memory drive for some reason, and they have some pretty good arguments in favor of that type of installation.

There are pros and cons about both kinds of USB installation I guess.

I'm still interested in reading about regular installations in USB drives that can or cannot automatically configure themselves at boot time, and if a CD or persistence USB can do better in the same hardware.

Thank you for posting your experience here, Browser_ice :D

Do you take your USB home from the office and run it in your computer at home and if so does it work well in both computers?

---

### Post by Herman on 2010-02-05
> Wow, that's fantastic Herman! I hope its not too complicated to figure out. Are you saying you're developing that for all of us for lucid?:redface: No, I'm not a developer, just a keen Ubuntu enthusiast and I'm a beginner at shell scripting.
Anyone can learn how to make their own shell scripts.
I just use this script myself to make it easier for me to install Ubuntu for friends and family in my town and locality.

If anyone wants it though, you're welcome to adapt it to your own wants and needs and use it.  :D

EDIT: If you do want to use it you'd need to have the following directories in a partition labelled 'POST-INSTALLATION', grub_backgrounds  
openclipart,  Software, deb, freefont, sharefont, Pictures,  Spreadsheet_Templates, icons, desktop_backgrounds, sourcerer, ubuntu_videos, ubuntupocketguide-v1-1.pdf, Grokking-the-GIMP-v1.0 and flash_tweaker.sh
EDIT: I can tell you how to make your own USB  POST-INSTALLATON partition and set it all up to run by the script but that's a subject for another thread.

---

