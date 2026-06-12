---
title: "Stuck at installation type"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by querolus on 2012-08-30
Hi

I'm trying to install Ubuntu in a Dell Inspiron 14z Ultrabook i recently purchased. I'm a complete beginner in Ubuntu but i wanted to try open source software. I've installed Ubuntu with wubi and it worked well but it crashed twice and the ubuntu remained unbootable so i decided to proceed with a regular installation. 
The problem is that when i get to the "installation type" window it does not recognize any partition or drive and gets stuck in there. I've seen that other people had the same problem with 11.10 version and, in fact, it was reported as a bug that looks unresolved: 

[http://ubuntuforums.org/showthread.php?t=1870478&highlight=stuck+at+installation+type](http://ubuntuforums.org/showthread.php?t=1870478&highlight=stuck+at+installation+type)

Can you please help me solving this issue?

Thanks

---

### Post by oldfred on 2012-09-01
Does liveCD work ok?

How many partitions do you have. Most new Windows 7 computers use all 4 primary partitions. Just to make it difficult, I think.

This is for HP but it is similar for all installs:

Good advice on how to handle all four primary partitions used. - srs5694
[http://ubuntuforums.org/showthread.php?t=1686440](http://ubuntuforums.org/showthread.php?t=1686440)
Besure to create recovery DVD(s) first. And a Windows repair CD.
HP tools partition discussion - similar for other vendor partitions:
[http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360](http://h30434.www3.hp.com/t5/Notebook-Hardware/Hp-Tools-Partion/td-p/228360)

---

### Post by querolus on 2012-09-03
Yes, my computer has 4 partitions. Two inaccesible, the C: and a Recovery partition. I'm going to try to solve it with the instructions for HP and see if it works. I already have a recovery CD that Dell provides when purchasing the computer.

---

### Post by oldfred on 2012-09-03
If it is just a CD, then it must only boot and use recovery partition to reinstall.

Dell restore partition.
[http://www.goodells.net/dellrestore/](http://www.goodells.net/dellrestore/)

Dell Media direct or Uninstall Dell DataSafe issues with MBR
[http://ubuntuforums.org/showpost.php?p=9330849&postcount=9](http://ubuntuforums.org/showpost.php?p=9330849&postcount=9)
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

### Post by querolus on 2012-09-03
Hi

I've tried to boot the computer with the "Reinstallation CD". Mi idea was to format the whole HDD (i don't have anything worth preserving) and re-do partition organization. However, it seems that what the CD does it's just look if Windows is installed already and, if it is, the only option is to "Update". Yo have the option of "Reinstalling" in a Custom way, but it gets only to a window in which the system asks for disk drivers and does not detect current drive partition organization.

I'm doing now what you suggested in the previous link. Make a recovery CD with the partition i want to eliminate (which will be the recovery partition, D in my case). Eliminate that one and start over to see what happens. 

My only question is if it is possible to format everything with Ubuntu (from the CD), re-install windows from the CD and then try to re-install Ubuntu as double boot...

Thank you

PS: i can't believe that manufacturers set so many hurdles for the people that want to install Linux. By the way... I know that the XPS 13 Ultrabook is working perfectly with Ubuntu. How can it be that it doesn't with the 14z. Are the default settings so different?

---

### Post by oldfred on 2012-09-03
The 4 partition limit has been an issue since the first hard drive for a PC. But it was only with Windows 7 that Microsoft and the Vendors arranged to use all 4 primary making it difficult to reconfigure. 

I prefer a second drive to avoid issue, but that can be difficult or less than optimal with a laptop and only one internal drive. You can use a USB drive or even a flash drive and have a working system, just not quite as fast as an internal drive.

You should only use Windows to resize/shrink Windows and can only reinstall Windows from the Windows install media. But you want to use gparted to create the extended partition and any logical partitions you want for Linux.

The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=2040149](http://ubuntuforums.org/showthread.php?t=2040149)
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

Make your own Windows repairCD (not vendor recovery):
[http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc](http://windows.microsoft.com/en-GB/windows7/Create-a-system-repair-disc)
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

---

### Post by querolus on 2012-09-04
I did a full back up yesterday and i'll try to reinstall Ubuntu this evening. I will let you know if i'm able or not.

Thank you again.

---

### Post by querolus on 2012-09-04
I think where is the problem, but i don't know if solving it is going to  be easy...Anyway is just an intuition because, very likely, i might be  completely wrong considering my no-expertise... here it is:

Following your links i did a full image of my system and tried to  eliminate one of the partitions (the D:, "Recovery" one). The system did  not allow me because is the "active partition". I changed the active  partition to the C:, and tried to boot and the computer did not boot. It  displayed a message saying "Missing BootMNGR". So i booted with Ubuntu  and changed the congfiguration back to D: being the bootable one.

Doing that, with GParted i've realized one thing that might be important  (but i don't know). I have two HDD, one SSD, 32Gb that is divided  between a 8gb partition and 23 unassigned Gb. The other one is a 500 HD  that is divided in 3: Dell Utility, Recovery partition (the bootable  one) and the  C: . Both are controlled by a 82801 Mobile SATA Controller  that is in Raid Mode. I've seen in other posts that the Raid Mode has  to be deactivated so Linux can recognize the partition system and i've  thought that there could be the problem. The 8Gb partition of the SSD HD  is also in raid mode.

Do you think that changing the raid mode it could work? I've seen how to do it in a HDD but not in the controller... 

Thank you very much

---

### Post by querolus on 2012-09-04
I think i got it... and it was related to the RAID configuration...

I did:

```
sudo su

dmraid -E -r /dev/sda
```

When asked if i want to delete metadata i clicked yes and now it recognizes the different partitions. I haven't finished yet the installation. When i'm done i will post the complete process and mark it as solved.

---

### Post by oldfred on 2012-09-04
You have to know which partition has the Windows boot files and not delete that. Usually it is a 100MB boot/repair partition. The vendor recovery is often bootable but not the main boot, but it sounds like yours may be?

So your system is like this?
 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)

---

### Post by querolus on 2012-09-05
Yes, that's exactly what happens. In fact, i've installed Ubuntu before knowing those threads and now Ubuntu does not boot so i guess i have to do the second part, with the boot repair utility.

Also i have the feeling that windows is running more slowly, but not much. I will post a full review of the process if i can solve it.

---

### Post by querolus on 2012-09-06
Well i think it's finally solved...

This was the process:

- First thing i did, as pointed in other threads, was to remove the RAID status of the C: drive

```
sudo su
dmraid -E -r /dev/sda

```

When asked to erase the metadata of the drive, replied "yes"

- Then booted with windows and created a new partition in the C: drive
- Downloaded the UBUNTU-SECURED REMIX 64bits installation cd image [http://sourceforge.net/projects/ubuntu-secured/files/](http://sourceforge.net/projects/ubuntu-secured/files/)
- Burnt the iso in a CD and booted the computer from that CD
-Installed Ubuntu from the CD.

I decided to installed from the Ubuntu- Secured-remix because i tried with the regular installer and the double boot did not work.

Now both systems work properly, although i would say that Windows booting is a little bit slower than before. However, nothing important.

So, to me this is solved.

Thanks for the help.

---

