---
title: "Cannot install Ubuntu 14.04.02"
date: 2015-11-25
forum: Installation &amp; Upgrades
---

### Post by write2diba on 2015-11-25
I have recently bought a Lenovo Ideapad 100-151BY laptop. Firstly Windows 7 was installed on it. Now whenever I am trying to Install Ubuntu with the Live DVD it is getting shutdown. 

After clicking on "Install Ubuntu" and going through few steps I saw one strange thing. The page where it is written Installation Type it is written " Install inside Windows 7" instead of " Install alongside Windows 7". After this when I click install now it says "Please remove any installation media and press Enter". After doing this step nothing happens...


please help me. What should I do.. Is dual boot not possible in my laptop? Is this even possible?

---

### Post by howefield on 2015-11-25
Thread moved to the "*Installation & Upgrades*" forum.

---

### Post by ajgreeny on 2015-11-25
The  "Install inside Windows 7" that you see suggests that you are still running Windows 7 and trying to install Ubuntu that way using wubi.

It was possible in the past, but that manner of installation, wubi, is no longer supported, and was never intended as a proper dual boot setup; it was a way to check that Ubuntu would run on the hardware, and to use to test the system.

Shutdown Windows 7 completely; if Win 7 uses the same semi-hibernation system as Win 8 you may have to shutdown in a non-standard manner to ensure it is totally shutdown, not hibernated, but I have not used Windows since XP so I have no idea about the details of that any more.

Once Windows is totally shutdown, boot the computer with the DVD live system in the drive, or USB in the socket, and if the boot priority is set correctly the machine will boot to the live Ubuntu OS from which, if everything works as it should, you can install Ubuntu.

---

### Post by ubfan1 on 2015-11-25
If your laptop already has four primary partitions, and no extended partition,  you will need to figure out how to add/convert/fit an extended partition onto your disk so the installer can create logical partitions as needed (usually two, root and swap).

---

### Post by write2diba on 2015-12-25
Yes you are right.. My laptop came with Four primary partitions... Is there any possibility to create an extended partition after having four primary partitions..???

Thanks..

---

### Post by sudodus on 2015-12-25
Before doing anything else you should ***backup*** your present system with Windows, because editing partitions is risky. At the very least you should backup all the files (documents, pictures ...) that are important for you.

You have to remove one of the primary partitions. The least important one maybe only contains some programs that you are not using. You could copy the content of that partition to an external drive, and after that boot from a DVD disk or USB pendrive with Ubuntu (boot a live session, 'Try Ubuntu') and use ***gparted*** to delete that partition and after that create an extended partition for Ubuntu.

-o-

Now, boot from a DVD disk or USB pendrive with Ubuntu and run the following commands from a terminal window:

```
df

sudo fdisk -lu

sudo parted -ls

sudo lsblk -fm
```

Copy and paste the output to a reply, and we can help you decide the next step.

---

### Post by Skaperen on 2015-12-25
if *you* can _afford 2 computers_ or can live a _totally windows-free life_(as i do), then *i recommend* _not having dual-boot_ and use a _separate computer for linux_.  soon you will want to run _server-like things_, such as a web server, and have _reasons to *not* shut down linux_.

---

### Post by write2diba on 2015-12-26
> **sudodus said:**
> Before doing anything else you should ***backup*** your present system with Windows, because editing partitions is risky. At the very least you should backup all the files (documents, pictures ...) that are important for you.

You have to remove one of the primary partitions. The least important one maybe only contains some programs that you are not using. You could copy the content of that partition to an external drive, and after that boot from a DVD disk or USB pendrive with Ubuntu (boot a live session, 'Try Ubuntu') and use ***gparted*** to delete that partition and after that create an extended partition for Ubuntu.

-o-

Now, boot from a DVD disk or USB pendrive with Ubuntu and run the following commands from a terminal window:

```
df

sudo fdisk -lu

sudo parted -ls

sudo lsblk -fm
```

Copy and paste the output to a reply, and we can help you decide the next step.




Thank for replying... I have installed 12.04.5 with Wubi.. So I didn't have to do any partition...
But I would like to know that if I upgrade 12.04.5 to 14.04 will there be any problem..?? I mean will it work on Wubi system...

---

### Post by write2diba on 2015-12-26
> **Skaperen said:**
> if *you* can _afford 2 computers_ or can live a _totally windows-free life_(as i do), then *i recommend* _not having dual-boot_ and use a _separate computer for linux_.  soon you will want to run _server-like things_, such as a web server, and have _reasons to *not* shut down linux_.



Okkk... I will note down your suggestion .... :grin:

---

### Post by sudodus on 2015-12-26
> **write2diba said:**
> Thank for replying... I have installed 12.04.5 with Wubi.. So I didn't have to do any partition...
But I would like to know that if I upgrade 12.04.5 to 14.04 will there be any problem..?? I mean will it work on Wubi system...

I'm glad it works for you with wubi and 12.04.5 LTS, but next time, when you want to upgrade to a new version of Ubuntu I suggest that you consider another method to install Ubuntu.

Wubi does not work with the new versions of Windows in UEFI mode. It is no longer developed which means that there is really no support for it. See this link

[Forums Staff recommendations on WUBI](http://ubuntuforums.org/showthread.php?t=2229766)

Instead you should either make

1. a dual boot system or

2. run Windows as a guest operating system in a virtual machine (for example VirtualBox) in an Ubuntu host operating system, or the opposite, run Ubuntu as a guest operating system in a virtual machine (for example VirtualBox) in a Windows host operating system.

3. or run two separate machines as suggested by Skaperen.

Each of these options are used by many people.

---

### Post by write2diba on 2015-12-28
> **sudodus said:**
> I'm glad it works for you with wubi and 12.04.5 LTS, but next time, when you want to upgrade to a new version of Ubuntu I suggest that you consider another method to install Ubuntu.

Wubi does not work with the new versions of Windows in UEFI mode. It is no longer developed which means that there is really no support for it. See this link

[Forums Staff recommendations on WUBI]("http://ubuntuforums.org/showthread.php?t=2229766")

Instead you should either make

1. a dual boot system or

2. run Windows as a guest operating system in a virtual machine (for example VirtualBox) in an Ubuntu host operating system, or the opposite, run Ubuntu as a guest operating system in a virtual machine (for example VirtualBox) in a Windows host operating system.

3. or run two separate machines as suggested by Skaperen.

Each of these options are used by many people.




Thanks for your suggestions... In the future I will install the new version of Ubuntu by partitioning the harddrive... Actually I cannot risk this doing at present, since I am away from home. Hence I cannot even do a backup of my hard disk...

Is there any possibilities of Wubi development in the future..? Actually it gives a hasslefree installation and in my case this was a boon to me since my Laptop came with 4 partition originally...

Speaking about virtualbox I had installed it in Windows previously and firstly I installed Debian in it. But the problem that I was facing was the speed. Speed of the system in VirtualBox was very slow. I don't know whether it's a system fault or any other thing... :(

---

### Post by sudodus on 2015-12-28
> **write2diba said:**
> Thanks for your suggestions... In the future I will install the new version of Ubuntu by partitioning the harddrive... Actually I cannot risk this doing at present, since I am away from home. Hence I cannot even do a backup of my hard disk...

You are right - avoid risky operations if you have no current backup.
> 
Is there any possibilities of Wubi development in the future..? Actually it gives a hasslefree installation and in my case this was a boon to me since my Laptop came with 4 partition originally...

No I don't think so. But who knows, maybe some new method will be developed, that can replace it (and work also with the newest versions of Windows).
> 
Speaking about virtualbox I had installed it in Windows previously and firstly I installed Debian in it. But the problem that I was facing was the speed. Speed of the system in VirtualBox was very slow. I don't know whether it's a system fault or any other thing... :(

Yes, systems will be slower in a virtual machine. But in many cases with modern computers, they will be fast enough for doing what you cannot do in the main operating system. And the advantage is that you need not reboot.

---

### Post by write2diba on 2015-12-31
Thanks very much for all your help and support... It has been very helpful .... :)

Wishing all a very Happy New Year.. :)

---

### Post by hakuna_matata on 2016-01-05
> **write2diba said:**
> 
Is there any possibilities of Wubi development in the future..?
There are bugfixes for all known Wubi issues at [launchpad.net]("https://code.launchpad.net/~hakuna-matata") . But it seems that the official maintainers of Wubi (=Ubuntu Installer Team) are not interested in releasing fully fixed Wubi versions. I submitted the [bugfixes for 15.04]("https://code.launchpad.net/~hakuna-matata/wubi/upstart/+merge/259318") but no response.

Currently, that means that the official maintainers do not maintain Wubi and it is also not possible that other people can officially maintain Wubi.

So if you think you need Wubi (*) you can build your own Wubi version (see article of bcbc: [Wubi development and customisation]("http://ubuntu-with-wubi.blogspot.ca/2012/10/wubi-development-and-customisation.html")) or if you trust me and dropbox you can use the versions of my dropbox folder ([shortened link]("http://bit.ly/1O1AJLz") or [direct link)]("https://www.dropbox.com/sh/6uqomp8l1frcd1y/AAAhSCimTaYE-94egbmc1X_na").

(*)
> since my Laptop came with 4 partition originally...
If you have 4 primary partitions, 
 * you can use [Gparted]("https://en.wikipedia.org/wiki/GParted")'s resize function to create a little gap before primary partition which you need as logical. It should be not a Windows boot partition and it should have enough space for Ubuntu.  
 * Then use [fixparts]("http://www.rodsbooks.com/gdisk/fixparts.html") to convert a primary partition to a logical partition without loosing data
 * If something goes wrong, use [testdisk]("http://www.cgsecurity.org/wiki/TestDisk") to restore your old partition table and try again
 * Then the Ubuntu default installer (not Wubi) should shrink your logical partition and create new logical partitions for Ubuntu.
Note: It is still a risky operation, so I strongly recommend a current backup for this method.

But a current backup is always not a bad idea.....

---

