---
title: "Dual booting Xubuntu and Win7"
date: 2012-03-01
forum: Installation &amp; Upgrades
---

### Post by TeeJay3800 on 2012-03-01
I'm having some trouble installing Xubuntu on my laptop.  I did search for similar issues, but I believe my particular problem is somewhat unique.  I'm not a n00b when it comes to installing Windows, but I am a complete n00b when it comes to installing and using Linux, as well as dual booting two OSes.

Before I began this process, I had Windows 7 Ultimate x86 installed on the only partition on my HDD.  My ultimate goal was to have Win7 on one partition, Xubuntu on another, and be prompted when turning on the computer which I wanted to use.  In preparation of that, I created a new 40GB partition with the intention of installing Xubuntu on that smaller partition.

I then downloaded the "desktop CD" image from [this link]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/11.10/release/xubuntu-11.10-desktop-i386.iso") then used [LinuxLive]("http://www.linuxliveusb.com") to make a bootable USB drive.  Next I booted from the USB drive and selected install.  During the installation process I'm pretty sure I selected the new 40GB partition for installation, but somehow Xubuntu got installed on the same partition as Win7.

At this point Windows 7 still boots and works normally, but I have a Xubuntu installation that I can't access.  Through some reading I've realized I need to install a bootloader to allow me to be able to select which OS I want to boot.  I'd also like to uninstall Xubuntu from my Win7 partition and install it on the other.  At this point I feel somewhat lost and overwhelmed, so any help that gets me on the right track is appreciated!

---

### Post by mastablasta on 2012-03-02
> **TeeJay3800 said:**
> I then downloaded the "desktop CD" image from [this link]("http://mirror.anl.gov/pub/ubuntu-iso/CDs-Xubuntu/11.10/release/xubuntu-11.10-desktop-i386.iso") then used [LinuxLive]("http://www.linuxliveusb.com") to make a bootable USB drive. Next I booted from the USB drive and selected install. During the installation process I'm pretty sure I selected the new 40GB partition for installation, but somehow Xubuntu got installed on the same partition as Win7.
 
It probably asked you where to install bootloader in that step. just guessing since you are sure you pointed it to 40GB partition.
 
> 
At this point Windows 7 still boots and works normally, but I have a Xubuntu installation that I can't access. Through some reading I've realized I need to install a bootloader to allow me to be able to select which OS I want to boot. I'd also like to uninstall Xubuntu from my Win7 partition and install it on the other. At this point I feel somewhat lost and overwhelmed, so any help that gets me on the right track is appreciated!
 
if it is really on windows part of disk then simply just delete it and try again. this time though choose it install on largest free space. 
the partition you allocated for Ubutnu should be empty (i.e. not formated or unnalocated in gParted). 
 
and yes grub in this case has to be on main disk and will (has to) overwrite the windows boot loader. hope this helps.
 
if you need help or are not sure then ask because with  a wrong setting you can erase your disk/data.

---

### Post by oldfred on 2012-03-02
The only way Ubuntu could be on the same partition as the Windows install is with wubi. Then you use the Windows boot loader to boot.

To see what partitions you have from liveCD terminal copy & post this back.

```
sudo fdisk -lu
```
or
sudo parted /dev/sda unit s print

---

### Post by TeeJay3800 on 2012-03-02
> **mastablasta said:**
> if it is really on windows part of disk then simply just delete it and try again. this time though choose it install on largest free space. 
the partition you allocated for Ubutnu should be empty (i.e. not formated or unnalocated in gParted). 
 
and yes grub in this case has to be on main disk and will (has to) overwrite the windows boot loader. hope this helps.
 
if you need help or are not sure then ask because with  a wrong setting you can erase your disk/data.
Here is a screenshot of what I now see on my HDD:

[ [IMG]http://s1.bild.me/bilder/060112/thumb_1942335screenshot5.png[/IMG]](http://s1.bild.me/bilder/060112/1942335screenshot5.png)

(click for full size)

As you can see, I don't see any additional folders on C (where I lost a lot of space after installing Xubuntu).  The only new item I saw afterwards, is "VC_RED".  I have no idea what that is.

You can also see the new partition I created ("Secondary OS" F) which is still completely empty.

At this point I would like to start over, but have no idea how to uninstall the Xubuntu installation that ended up on my C partition.  Please get me pointed in the right direction.  Thank you both for responding!

---

### Post by TeeJay3800 on 2012-03-02
> **oldfred said:**
> The only way Ubuntu could be on the same partition as the Windows install is with wubi. Then you use the Windows boot loader to boot.

To see what partitions you have from liveCD terminal copy & post this back.

```
sudo fdisk -lu
```
or
sudo parted /dev/sda unit s print
I do not know what Wubi is, but I assure you that after installing Xubuntu, the amount of free space available on my C partition (where Win7 is installed) was drastically reduced.  The partition where I *thought* the Xubuntu installation app told me it was being installed ("Secondary OS", partition F), was empty before the installation, and still is.

---

### Post by oldfred on 2012-03-02
From a liveCD post the results.txt that boot info script creates. Then we can see what is where.

There is a new test/git version that you can directly download.

```
wget -O bootinfoscript 'http://bootinfoscript.git.sourceforge.net/git/gitweb.cgi?p=bootinfoscript/bootinfoscript;a=blob_plain;f=bootinfoscript;hb=HEAD'
chmod a+x bootinfoscript
sudo bash bootinfoscript

```

or you can download this program which can often do minor boot repairs and run script so we can suggest major repairs.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

If making system changes be sure to have a Windows repairCD. Do not create new partitions with Windows as it will convert you to dynamic partitions which do not work with Linux and reportedly some Windows repair tools.

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Also make sure you have good backups before starting.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by TeeJay3800 on 2012-03-02
Thank you very much for the detailed response.  However, before I proceed any further, I need to correct myself on some statements I made in previous posts.

[IMG]http://s1.bild.me/bilder/060112/3793560h.png[/IMG]

[IMG]http://s1.bild.me/bilder/060112/2933176j.png[/IMG]

I have a 160GB HDD, so I was surprised to notice that, as you can see in the first screenshot, my total HDD space only adds up to 111GB.

I then when to "Computer Management" and noticed that somehow during the Xubuntu installation, I ended up with two new partitions that are both under the C drive.  Before beginning the whole process, I manually created the "Secondary OS" Drive F partition with the intention of installing Xubuntu there.  However, it appears it was actually installed on the C drive in one of the two newly created partitions.

This means that you were right, that indeed Xubuntu was installed on the C drive, which explains why the free space there dropped so dramatically after the installation.

I do not know if this changes what I should do next, so please advise before I go any further.  Thank you!

---

### Post by oldfred on 2012-03-03
It looks like you may have the four primary partitions which is the max that MBR partitioning allows. You can use one primary as an extended partition which is the container for many logical partitions. Windows only boots from a primary, but Ubuntu will work and data partitions for both Windows & Linux can be logical partitions.

Back to post this from a Ubuntu liveCD or USB. Then we can be sure of partition layout. 

```
sudo fdisk -lu
```

Some sites with examples of installs with screen shots.

Install 11.10 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/](http://debianhelp.wordpress.com/2011/09/12/to-do-list-after-installing-ubuntu-11-10-aka-oneiric-ocelot/)
Install 11.04
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing) - side by side auto install
Ubuntu Install steps - then choose guide, close to what you want.
[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Installs with good screenshots/examples:
[http://members.iinet.net.au/~herman546/p22.html](http://members.iinet.net.au/~herman546/p22.html)
Install with separate /home from aysiu
[http://www.psychocats.net/ubuntu/installseparatehome](http://www.psychocats.net/ubuntu/installseparatehome)
[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)
[http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/](http://www.linuxbsdos.com/2010/10/12/ubuntu-10-10-manual-disk-partitioning-guide/)

---

