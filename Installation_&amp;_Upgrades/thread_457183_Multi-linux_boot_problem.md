---
title: "Multi-linux boot problem"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by Paracelsius on 2007-05-28
Firstly I do not have any version of windows on my iBuddie desknote!  But I do have several partitions so that I can experiment with different versions of Linux.  I mostly use PCLinuxOS, but also ubuntu for some programs like Gramps that run better under gnome.  I have just installed the latest PCLinuxOS (2007 - final) and had PCLinuxOS 0.93 and ubuntu 7.0.4 installed as well.  

After installation a bit of editing of the menu.lst in the /boot/grub folder of the latest installation was needed to restore access to the other versions: I copyied and pasted the relevant bits from the menu.lst files in the appropriate partitions  as I had done before.  I have access to my two PCLinuxOS versions, but ubuntu crashes at the file system check of its own partition and throws me into a command line with messages about file check failure and then says I might be able to correct it by hand (don't know enough to do that!) and that it cannot find aptget.

When I reboot PCLOS the first time after this it says "recovering journal" when it does a file check on the ubuntu partition, but on re-rebooting after that everything is fine.  Somehow the call to boot ubuntu seems to be corrupting the files somewhere.  The odd thing is that another PCLOS user was able to copy over the booting instructions from ubuntu to PCLOS without any problems.  This is also the second time this has happened to me!

I don't want to have to re-install, and configure ubuntu every time I install something else - does anyone know what is happening here and can suggest a solution?  The only positive thing is that ubuntu is much better than PCLOS at finding other Linuxes and incorporating them into its menu.lst.

I haven't been able to find this topic -  all the multi boot problems search turns up for me involve something apparently called Windows.

---

### Post by vtel57 on 2007-05-28
Is this a single hard drive?

IDE or SATA/PATA?

Can you please post the output of this command:

```
 $ fdisk -l
```

Can you please COPY/PASTE your menu.lst here? I'm talking about the menu.lst from your bootloader in your Master Boot Record... the loader you use to boot all the OS's on your system.

---

### Post by Paracelsius on 2007-05-29
vtel57, thanks for your suggestions, but I didn't need to do that.

With the help of someone on the PCLinuxOS forum I have worked out what the problem is - it's that ubuntu bases its fstab on the UUIDs of partitions at the time it was installed.  When I later reformated a partition to install PCLOS 2007 its UUID was changed and ubuntu couldn't find it when it did a file system check, and somehow gives the impression that its the ubuntu partition that's causing the problem.

The work around is to edit ubuntu's fstab, either removing the defunct UUID, or setting the default parameters at 0 0.  A real cure would be to replace the UUID with the new one - but at present I don't know how to find it!

---

### Post by Bigdog60 on 2007-05-29
Dude first off you really shouldn't be putting that many systems on to one computer because you are going to have many many problems. Also you are just wasting some of your space on your hardrive for example when you put alot of stuff on one of the linux systems the others are going to slow down dramatically only have 2 systems.

---

### Post by Paracelsius on 2007-05-29
I have a 120 Gb drive, 88% free.  None of my installation partitions are more than 38%.  I cannot see that there's a problem.  I'm certainly not aware of any speed problem.  Any idea how to find a UUID?

---

### Post by confused57 on 2007-05-29
> **Paracelsius said:**
> I have a 120 Gb drive, 88% free.  None of my installation partitions are more than 38%.  I cannot see that there's a problem.  I'm certainly not aware of any speed problem.  Any idea how to find a UUID?

I'm currently booting 8 different distros on 2 hard drives, a SATA & an IDE, no problems.

You can determine the new UUID's with the command "blkid"...you can probably just copy & paste the UUID from the blkid output into your Feisty /etc/fstab.   You could probably mount your Feisty root partition from your PCLinuxOS & make the changes.

Added:  Here's an excellent explanation of UUID's:
[http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with](http://users.bigpond.net.au/hermanzone/p10.htm#Edgy_Efts_new_etcfstab_files_with)

You could also use the Feisty live cd to mount your root partition:
```
sudo mkdir /media/ubuntu
sudo mount -t ext3 /dev/hda3 /media/ubuntu
```
substitute your root partition in place of hda3, then
```
gksudo gedit /media/ubuntu/etc/fstab
```

---

### Post by dabl on 2007-05-29
I have a "quad-boot" system on 2 SATA and 1 IDE drives.  Ubuntu Feisty 64-bit low-latency, Kubuntu Feisty 32-bit generic, elive, and WinXP.  The challenge is to remember the rule "last Linux to write grub wins".  The "real" grub menu is the one written by the last Linux you installed -- in my case Ubuntu 64-bit -- unless you manually changed it back or prevented it from writing.  A kernel upgrade in my other two Linuces will re-write those /boot/grub/menu.lst files, but they are not used to boot the computer. So it's a matter of fixing the "real" file in the Ubuntu file system.

Hope this helps a confused person (like me, often).  :D

---

### Post by vtel57 on 2007-05-29
> **Paracelsius said:**
> vtel57, thanks for your suggestions, but I didn't need to do that.

With the help of someone on the PCLinuxOS forum I have worked out what the problem is - it's that ubuntu bases its fstab on the UUIDs of partitions at the time it was installed.  When I later reformated a partition to install PCLOS 2007 its UUID was changed and ubuntu couldn't find it when it did a file system check, and somehow gives the impression that its the ubuntu partition that's causing the problem.

The work around is to edit ubuntu's fstab, either removing the defunct UUID, or setting the default parameters at 0 0.  A real cure would be to replace the UUID with the new one - but at present I don't know how to find it!

Indeed. That's precisely the reason I was asking for that information... to assist you to properly edit the fstab. Anyway, glad you got it straightened out. 

Have FUN! :)

---

### Post by vtel57 on 2007-05-29
> **Bigdog60 said:**
> Dude first off you really shouldn't be putting that many systems on to one computer because you are going to have many many problems. Also you are just wasting some of your space on your hardrive for example when you put alot of stuff on one of the linux systems the others are going to slow down dramatically only have 2 systems.

I hate to say this, but you are totally wrong in this belief. I run eight operating systems on my machine. I have MS Win XP Pro on a 250Gig RAID 1 (mirrored) set up and seven GNU/Linux distributions on my primary IDE (Ubuntu, Debian, Fedora Core, SuSE, Slackware, Mepis, and Mandriva). 

Having multiple operating systems on your machine does **not** affect performance in any way. Hardware performance is determined by software. Each operating system on my machine is independent of the others. Only one OS can be booted and in control of the hardware at any given time.

In closing, sorry to contradict your statement, but it is what it is.

Luck!

---

### Post by vtel57 on 2007-05-29
> **Paracelsius said:**
> I have a 120 Gb drive, 88% free.  None of my installation partitions are more than 38%.  I cannot see that there's a problem.  I'm certainly not aware of any speed problem.  Any idea how to find a UUID?

In /dev/disks, you'll find the partitions listed. Check the properties of the UUID partitions and it will show you the hda/hdb/sda/sdb labels.

---

### Post by coffeecat on 2007-05-29
> **Bigdog60 said:**
> Dude first off you really shouldn't be putting that many systems on to one computer because you are going to have many many problems. Also you are just wasting some of your space on your hardrive for example when you put alot of stuff on one of the linux systems the others are going to slow down dramatically only have 2 systems.

I have to agree with **vtel57**. That is just plain wrong. I too have multi-boots on both my laptop and two desktops partly so that I can experiment with different distros and partly to have a bit of variety. The only possible slowdown comes at bootup if several partitions are due a fsck at the same time. That can be solved by judicious use of  tune2fs -c.

---

### Post by Henry Rayker on 2007-05-29
> **Bigdog60 said:**
> Dude first off you really shouldn't be putting that many systems on to one computer because you are going to have many many problems. Also you are just wasting some of your space on your hardrive for example when you put alot of stuff on one of the linux systems the others are going to slow down dramatically only have 2 systems.

....are you retarded? Or perhaps a child? The ONLY thing that will slow down is possibly the disk check in the boot sequence. Aside from that, there will be no slow-down. As far as wasting space, it's not as if the operating systems could be actually condensed...if he/she wants to experiment with different OSes, it's not a waste of space. "waste of space" in this context is a personal opinion.

---

### Post by Paracelsius on 2007-05-29
Thanks to everyone in the PCLinuxOS and ubuntu forums who have made suggestions on this problem.  Some worked, some didn't, but my ubuntu is now booting as it should, and, once you know, it isn't that difficult to fix – although it would be better if you didn't have to!

The problem is that ubuntu stores the identities of other partitions in its fstab as UUIDs rather than in /dev/hdax format, and these are fixed at the time of installation.  If you subsequently reformat a partition, as you do when installing another OS, ubuntu still looks for it under the old number and may crash on boot up.

To fix this you need a working Linux – e.g. the one you installed that caused the problem.  First find the new UUID, this is obtained using the command **blkid** from a root command line.  

Leave this on the screen and, again as root, find /etc/fstab in the ubuntu partition and load it into your favourite editor (mine is vi – but do this any way you know how.).   Delete the offending UUID (only the UUID – not the rest of the line!).  

Then copy the new UUID from the first screen and paste in into the empty space.  Remove the “” around the hex number (may not be necessary, but it won't do any harm!).  Save the file, and ubuntu should boot up as it used to.

---

### Post by vtel57 on 2007-05-29
I don't know what the Ubuntu developers were smoking when they decided to go to this UUID crap. It's causing a lot of people a lot of needless problems. And I've yet to read anywhere about the advantages of this change. :(

---

