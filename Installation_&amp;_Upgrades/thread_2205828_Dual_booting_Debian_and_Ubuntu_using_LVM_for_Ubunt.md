---
title: "Dual booting Debian and Ubuntu using LVM for Ubuntu"
date: 2014-02-16
forum: Installation &amp; Upgrades
---

### Post by anotherbigal on 2014-02-16
I have a 250 GB hdd that contains one 50GB primary partition, /dev/sda1. It has Debian Wheezy (v7.2) installed without any further partitioning.. The remainder of the drive, /dev/sda2 is formatted as an extended partition. That in turn has a small, 3.9GB logical partition at the start, /dev/sda5 formatted as the linux-swap space for the Debian installation.

Using GParted I created another 50GB logical partition. The intention is to use this for a Ubuntu installation. I want to use LVM for this installation but this is where I ran into my main trouble. I had downloaded the Live i386 (v13.10) DVD, verified the checksum then burnt it to disk.  The little icons that appear at the bottom of the screen are hardly informative and it was only because I had some prior knowledge that I knew to touch a key on the keyboard to reveal the options. Selecting the appropriate one I verified the disk integrity which led to a reboot once satisfactorily completed.

Despite the advice contained in the Ubuntu Installation Guide to be found at [https://help.ubuntu.com/13.10/installation-guide/i386/index.html](https://help.ubuntu.com/13.10/installation-guide/i386/index.html) there are no options to select a GUI or text installation. You get the GUI. Unlike other installation programs, highlighting an option and pressing tab, does not allow you to edit it. I use fixed IP addresses for all my machines, added to which I want to install Ubuntu with  my preferred KDE desktop. The options are limited. I had to press F6 to get to some other options, then press escape to enable the boot options. I entered 'netcfg_disable=true' to force manual networking configuration and 'desktop=kde' to change the default desktop (No apostrophises though) Pressing return started the installer. I opted to 'Download updates while installing', and to install the 'third-party software'.

When you arrive at the 'Installation Type' menu you are presented with the following options:

"This computer currently has Debian GNU/Linux (7.4) on it. What would you like to do?"

[LIST]
[*]**Option** - Install Ubuntu alongside Debian GNU/Linux
(*Documents, music, and other personal files will be kept. You can choose which operating system you want each time the computer starts up*) 
[*]**Option** - Replace Debian GNU/Linux (7.4) with Ubuntu
(*Warning: This will delete all of you Debian GNU/Linus 97.4) programs, documents, music, and any other files*) 
[*]**Option** - (Greyed out unless option 2; Replace Debian, is selected)
(*Encrypt the new Ubuntu installation for security (You will choose a security key in the next step*) 
[*]**Option** - (Greyed out unless option 2; Replace Debian, is selected)
(*Use LVM with the new Ubuntu installation (This will set up Logical Volume management. It allows taking snapshots and easier partition resizing*) 
[*]**Option** - Something else
(*You can create or resize partitions yourself, or choose multiple partitions for Ubuntu*) 
[/LIST]

I wanted the 4th option. Use LVM. However, as noted it is unavailable unless I choose to destroy my Debian installation. So I went for the final option, 'Something Else. Now I am presented with a graphical representation of my partition table. My 50GB partition is shown, quite correctly as /dev/sda6. It is already shown the type as ext4. Double clicking on it allows me to edit it so I enter a size of 1024MB, and despite previously indicating the file system I enter ext4. I want it formatted and intend to use it as root so look at the drop down list and select '/' I have also ticked the check box to format the partition. Partman now wants to write this change to disk before continuing. I agree. This change destroys my 50GB partition but allows me to create other partitions for other parts of my installation. This is where I get into trouble.

I want to set up LVM partitions for /usr, /var, /tmp, and /home. I can opt to make my new partition a logical one and put it at the beginning of the free space, I can choose the file system. The drop down list of possible mount points is /, /boot, /home, /tmp, /usr, /var, /srv, /opt and /usr/local. No LVM option anywhere.
I reiterate, I want to use an LVM installation but keep my existing Debian installation. How do I go about this. There does not seem to be any options for this anywhere.
 I am sorry that this post is lengthy but at least any reader will know exactly what is, or is not, going on.

This is also posted on the Mint forum as once I have Ubuntu installed using LVM I want to triple up with Mint.

Alan

---

### Post by fantab on 2014-02-16
>  I want to use an LVM installation but keep my existing Debian  installation. How do I go about this. There does not seem to be any  options for this anywhere.
To make an LVM partition you will have put a 'lvm' flag on the partition. In Gparted this is found under 'Manage Flags' in the rt.click menu. 

More Here:
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)

Since you already have Debian setup, probably in, Ext4 filesystem, I'd say use the same ext4 for your triple distros.
I triple boot on my another PC with Ext4 filesystem and this is how my HDD-Partitions setup looks:
20Gb Primary Ext4 '/' (Say, Debian System-files)
20Gb Primary Ext4 '/' (Ubuntu SF)
20Gb Primary Ext4 '/' (Say, Mint SF)
190Gb Extended Partition
2Gb Logical linuxSWAP
188Gb Logical Ext4 Simple DATA partition (No mountpoint), to store data and share between all the installed distros.

---

### Post by oldfred on 2014-02-16
Most desktops do not need separate system partitions. Ubuntu's default is just / (root) and swap. Sometimes we suggest separate /home, but if multi-booting a separate data partition will make more sense as that can be shared.

With the 12.04 alternative text based installer and LVM that has always been a full drive install. LVM does not offer as many advantages unless you use the full drive. Alternative installer has been discontinued after 12.04.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)

---

### Post by Herman on 2014-02-16
My suggestion is to try setting up your LVM first, before starting your Ubuntu installer.
I haven't tried dual booting with LVM yet, so I can't make any comments about that. I'm still new to LVM and experimenting with it, so I can only say what I have done with it.

In the past I used to use the 'Alternate' installer for making LUKS encrypted LVM installations.

When the 'Alternate' installed was discontinued I was able to install Ubuntu 12.10 in LVM using the standard 12.10 'Desktop' installation. The way I did that was to set up LVM before beginning the installation process. It was quite simple, I used GParted for working with partitions, and after that I installed a nice graphical tool called Logical Volume Manager. Once I had everything set up, the 12.10 installer had no problem to recognise the logical volume, format it with a file system and install into it. That time I made a LUKS encrypted installation in a USB flash memory stick. 
Then later I added three more USB flash memory sticks around a USB hub, and used Logical Volume Manager again to register the new USB sticks as physical volumes. I stretched the operating system out across the other three USBs.

In another LVM installation I followed a how-to in Ubuntu Community Docs about how to install in striped LVM, like RAID0. I have four x 500GB HDDs and this time I set up the LVM from the command line. I wanted 12.04 and I tried that first. The 12.04 Live CD was able to see the LVM, but was not able to install into it. 
Then I tried 13.10 and the installer for 13.10 seems quite a bit improved. I still doesn't seem to have the capability of creating logical volumes during the installation process, but at least when the LVs were already prepared, I had no problem at all getting the 13.10 installer to format it with a file system and install into it. The installation only took fifteen minutes and I'm that's the operating system I'm using at the moment. [StripedVolume HowTo]("https://help.ubuntu.com/community/StripedVolumeHowTo") - Ubuntu Community Docs.

EDIT: The how-to I linked to has not need edited in some time, and includes instructions for creating a separate /boot for Legacy GRUB. I didn't create a separate /boot this time, because we're using GRUB2 now, and it has lvm.mod for supporting booting OS's in LVs directly. A separate /boot outside of the LVM is optional but no longer required.

Sorry for being too wordy, but I hope I'm helping other people who might also be interested in installing with LVM.

---

### Post by Herman on 2014-02-18
I am trying out a test installation myself to see if the original poster, (anotherbigal)'s configuration will work.

There is a bug in 13.10 which causes the GUI Logical Volume Manager program to pop out a terminal and ask for your password a couple of times and then fail to start. I found the following comand in launchpad in the bugs reports for starting Logical Volume Manager with instead,
```
sudo /usr/share/system-config-lvm/system-config-lvm.py;
```

Otherwise, we can still use the normal lvm commands from the command line, for people who prefer doing things that way. If you're not sure I recommend reading lvm how-to's, especially in ubuntu wiki pages, and maybe practicing the commands in a USB flash drive first.

In my test installation I made a partition sheme similar to anotherbigal's and installed 13.10 xubuntu in the first partition, equivalent to the OP's Debian installation, with swap in a logical partion, /dev/sda5, inside /dev/sda2, (extended).

I decided to try going one step further and installing not just one more operating system, but two more instead. I made two more partitions in the extended partition, one for kubuntu 13.10 and another for ubuntu 13.10. In hindsight, that turned out to be a silly move, because it negates most of the advantages of using LVM, I would have been better off leaving it as one partition and creating more logical volumes to install into. Put it down to inexperience, I am learning a lot about LVM.

The main thing I can tell the OP is that the scheme has resulted in a working dual boot or triple boot setup.

---

### Post by anotherbigal on 2014-02-18
The machine I was setting this up on is a test bed. I wanted at least 4 logical partitions in my volume group but to set the installation up without destroying the other OS already installed.. There seems to be no way that I can achieve any of this- and that is before attempting to triple boot Ubuntu with Mint. The installation options are so very limited. I know it is a Live image, but other similar live images I have used in the past usually have the facility to install direct from the initial menu.
 

 What is also very bad is that the instructions given in the 'Installation Guide - Lifted straight from the Debian one, do not even refer to what actually happens when you put the disk in and start the machine up. To my mind this is not so (new) user friendly at all.
 

 I tried swapping the drive for a spare 160 GB one in an effort to save the previously install OS (Debian) and tried again. Ubuntu obviously does not like my machine Spec. is Intel Celeron 2.26 GHz
 Graphics Gallium 0.4 on NV4a (GeForce 6200)
 Memory 2GiB
 OS 32 bit.
 

 I shall go away. Thank you all for your input though. I really do appreciate it.

---

### Post by Herman on 2014-02-19
I'm sorry I wasn't able to give better help.  You should have been able to do what you say you wanted, it is quite achievable I assure you. At least in my computer it's easy enough. I think it's best to start with an empty disk for LVM though, just one big partition, and make all your operating systems in logical volumes. That way you can make the best use of all the advantages of LMV. I have blown mine all away already and will start again and do it better next time.

---

### Post by anotherbigal on 2014-02-19
I do not seem to have had any success with any of the Linux installations I have tried.; Mint - Cinnamon, Mate, KDE also  Ubuntu. All are from live dvds none of which offer the option to configure the hdd the way I want, moderately sized LVs the I can expand as and when I need. Also none of them let me add the installation alongside a previously installed OS.

 

  Yes, I was attempting all of this in logical partitions although the original installation is in a primary one. I couldn't even achieve my aim when using the entire disk. Perhaps it is me. I am disappointed that installation seems to have to be done via a live dvd though. That uses far more resources than is necessary.
 

 Thank you again for all you help
 

 Cheers
 

 Alan

---

### Post by Herman on 2014-02-19
There are lots of ways to install Ubuntu. I normally download the .iso file via tranmission bit torrent client via a torrent file.
I think all Ubuntu .iso files are for burning to a CD, but instead I always use Startup Disk Creator to copy them to USB flash memory sticks and run them from there. I stopped using optical drives years ago, except if there's no other way.

There are plenty of excellent tutorials available on the internet about how to set up LVM from the command line. The Ubuntu Wiki has some nice ones but they may need a little updating. As I said before, we no longer need a separate /boot for GRUB now that we have GRUB2, and that makes LVM very attractive to people like yourself who want to multi-boot.

I looked around for a how-to with screen caps showing how to use the GUI Logical Volume Manager. It may not be so obvious what to do the first time a person uses it, but it seems very simple once a person knows how to find their way around in it. Once you try it and get used to it you won't care about having the LVM options in the installer anymore. Except without a good illustrated how-to I can link you to it's kind of hard to mentally telepathasise to you what to do. I may make an illustrated web page about it myself when I get time. However, I have had people complain it's not good ettiquette for me to post links in the forum to my own web site, so I have been refraining from doing that for a long time now. I suppose the solution would be roll up my sleeves and jump in and edit the wiki, but that's a little bit more time consuming.

---

### Post by anotherbigal on 2014-02-20
I am still very much at the early learning stage of using the command line and, unfortunately cannot regularly devote the time needed to get more into it. Although interested, I am very much a user of computers rather than even attempting to be an administrator. Its not that I would like to learn more. I definitely would but I have to be practical about these things. I am not consistent.  One week I can spend a good few hours most days looking around and trying to work with the system, then it might go a month or so before I can devote any more time to it, by when, mostly I have forgotten what I did before. Memory never was a strong point- even worse nowadays.

 

 In the past I have set up I LVM a couple of times but always via a GUI. Never the less as a result I am reasonably familiar with the process. In those days the DVD images available were not only live disks, you could also pull down straight forward installation disks and they all had fully customisable facilities for setting up LVM. I do not know much, but I do know enough to appreciate just how useful LVM is. As I have said before, I am practising on a test bed machine. The ultimate destination machine has a lot of hard disk space but space is still something I do not want to waste unnecessarily.  
 

 Over the last couple of weeks I seem to have read hundreds of tutorials, well, all right, quite a few, and followed a LOT of links to various forum postings and other tutorials and comments, but mostly they are out of date. As an example I read a Ubuntu post that told me that what I should look for was under the menu entry Administration>System>Utilities (That is probably not correct, but you will see, I hope, what I meant) only to find that on the current GNOME desktop there is no 'Administration'  menu - anywhere. Well, not that I could find anyway. As a bye the bye, and off topic I know, I really do not like the profusion of icons all over the place. Particularly on the GNOME desktop. I find a simple list is so much easier to work with.

 

 Right now the time is rapidly approaching when I have got to go away and do other things. I suspect that despite what all the 'About's say at least some of my trouble is the spec on my machines; specifically the graphics cards. KDE, as a for instance simply will not render properly. Just several grey bars at the bottom of the screen some of which, when clicked on reveal another grey box but with scribble on. Unfortunately KDE is normally my preferred choice. Xfce is okay but a bit limiting for my needs.

 

 I am considering at some point in the future, to try installing a very much older version of an OS. May be 2 or three years old, one that I know I CAN set up the way I want, then try updating it. Not something I really want to do as I can foresee no end of problems laying there awaiting me.
 

  Ah well!
 

 Cheers
 

 Alan

---

### Post by anotherbigal on 2014-02-20
I am still very much at the early learning stage of using the command line and, unfortunately cannot regularly devote the time needed to get more into it. Although interested, I am very much a user of computers rather than even attempting to be an administrator. Its not that I would like to learn more. I definitely would but I have to be practical about these things. I am not consistent.  One week I can spend a good few hours most days looking around and trying to work with the system, then it might go a month or so before I can devote any more time to it, by when, mostly I have forgotten what I did before. Memory never was a strong point- even worse nowadays.

 

 In the past I have set up I LVM a couple of times but always via a GUI. Never the less as a result I am reasonably familiar with the process. In those days the DVD images available were not only live disks, you could also pull down straight forward installation disks and they all had fully customisable facilities for setting up LVM. I do not know much, but I do know enough to appreciate just how useful LVM is. As I have said before, I am practising on a test bed machine. The ultimate destination machine has a lot of hard disk space but space is still something I do not want to waste unnecessarily.  
 

 Over the last couple of weeks I seem to have read hundreds of tutorials, well, all right, quite a few, and followed a LOT of links to various forum postings and other tutorials and comments, but mostly they are out of date. As an example I read a Ubuntu post that told me that what I should look for was under the menu entry Administration>System>Utilities (That is probably not correct, but you will see, I hope, what I meant) only to find that on the current GNOME desktop there is no 'Administration'  menu - anywhere. Well, not that I could find anyway. As a bye the bye, and off topic I know, I really do not like the profusion of icons all over the place. Particularly on the GNOME desktop. I find a simple list is so much easier to work with.

 

 Right now the time is rapidly approaching when I have got to go away and do other things. I suspect that despite what all the 'About's say at least some of my trouble is the spec on my machines; specifically the graphics cards. KDE, as a for instance simply will not render properly. Just several grey bars at the bottom of the screen some of which, when clicked on reveal another grey box but with scribble on. Unfortunately KDE is normally my preferred choice. Xfce is okay but a bit limiting for my needs.

 

 I am considering at some point in the future, to try installing a very much older version of an OS. May be 2 or three years old, one that I know I CAN set up the way I want, then try updating it. Not something I really want to do as I can foresee no end of problems laying there awaiting me.
 

  Ah well!
 

 Cheers
 

 Alan

---

### Post by anotherbigal on 2014-02-20
> **anotherbigal said:**
> 

 As a bye the bye, and off topic I know, I really do not like the profusion of icons all over the place. Particularly on the GNOME desktop. I find a simple list is so much easier to work with.

What a coincidence. I just found this article  
 ```

http://www.datamation.com/open-source/what-makes-a-classic-linux-desktop-classic-1.html

```

Interesting reading.

Alan

---

### Post by Herman on 2014-02-20
Nice article, yes, I agree with you. It has taken me a long time to adjust to the new desktop environment and I still miss the classic desktop too. 

For some reason I had a lot of trouble trying to install 13.10 Kubuntu too. It might be better to install the server and then add the KDE desktop later, or install plain Ubuntu and then install the KDE desktop. I haven't tried it lately, but we used to be able to install various desktops.

I'll start a web page to illustrate the use of the GUI tool 'Logical Volume Management', and possibly another page about how to prepare logical volumes for Ubuntu and other Gnu/Linux installations using the command line. My website is here, [Herman's Tips and Tricks Blog]("http://members.iinet.net/~herman546/"). It was formerly called 'Illustrated Dual Boot Site', which you can see if you scroll down.
I might call it something along the lines of 'yyyy_MM_dd - Preparing Logical Volumes For Ubuntu Installations', or something like that.
I'm not sure how quickly I'll be able to get this done. I still have a page from last weekend which is waiting to have screencaps added and be re-edited.
Give me one or two weekends and then perhaps I'll be ready for somebody to give me some feedback on what needs improving in it.  I don't want to promise I'll have it complete and perfected by any deadline though.

Regards, Herman :)

---

### Post by Herman on 2014-02-21
I have just finished (for now) the new web page, [2014_02_22 Preparing Logical Volumes For Ubuntu Installations]("http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html").  It will probably need some editing, but I think I have most of it there well enough for somebody to be able to understand how to use the Logical Volume Manager at least. 

Regards, Herman :)

---

### Post by oldfred on 2014-02-22
On classic desktops, I install Ubuntu but use Fallback/flashback.

 sudo apt-get install gnome-panel
On login screen click on logo/cog-wheel/star and choose 
[http://www.psychocats.net/ubuntu/classicgnome](http://www.psychocats.net/ubuntu/classicgnome)
12.04 LTS / Precise Classic (No effects) Tweaks and tricks kansasnoob & cortman
[https://help.ubuntu.com/community/PreciseGnomeClassicTweaks](https://help.ubuntu.com/community/PreciseGnomeClassicTweaks)
[http://ubuntuforums.org/showthread.php?t=1966370](http://ubuntuforums.org/showthread.php?t=1966370) 

        New gnome3.8 flashback
[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)
[https://wiki.gnome.org/GnomeFlashback](https://wiki.gnome.org/GnomeFlashback)
[http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103](http://ubuntuforums.org/showthread.php?t=2090021&p=12859103#post12859103)

---

