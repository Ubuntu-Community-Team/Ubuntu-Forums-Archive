---
title: "Dual Boot with Windows Vista and Lubuntu"
date: 2014-04-29
forum: Installation &amp; Upgrades
---

### Post by sfink16 on 2014-04-29
Hi,

On my original setup of my laptop I had Vista only boot.  I since update to a dual boot with Lubuntu.  The Lubuntu comes up fine.  The Vista just sits on the logo screens what may be infinity.  I tried to run Boot-Repair using this tool:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

without success.  Below is a link as to the results:

[http://paste.ubuntu.com/7353852/](http://paste.ubuntu.com/7353852/)

The Grub login screen appears to be OK.  I can't find any errors that would stop Vista from finishing the boot.  Can anyone help?

Thanks!

Steve

---

### Post by oldfred on 2014-04-29
How did you shrink Vista NTFS partition?
Usually better to use Windows tools and immediately reboot so it can run chkdsk.

It looks like Boot-Repair tried to run ntfsfix but that does not do much, and really just sets chkdsk flag so when you boot Vista it will run chkdsk. Is it running chkdsk when you boot, that can take a while?

Or you need a Windows repair CD or flash drive to run the chkdsk on your NTFS partition or make other repairs.

       We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

   Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)

   Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

### Post by sfink16 on 2014-04-29
Thanks Fred!  Me answers and further questions are intermixed in red below.  Once solved or I give up, I'll use the tools to close the thread.

Steve

> **oldfred said:**
> How did you shrink Vista NTFS partition?   [COLOR="#FF0000"]The Vista partion was shrunk during the Lubuntu installation unfortunately[/COLOR]
Usually better to use Windows tools and immediately reboot so it can run chkdsk.

It looks like Boot-Repair tried to run ntfsfix but that does not do much, and really just sets chkdsk flag so when you boot Vista it will run chkdsk. Is it running chkdsk when you boot, that can take a while?   [COLOR="#FF0000"]Not that I can see. I suppose if I press the "esc" button I may be able to see what it is doing.  UPDATE:  I started it in Safe Mode and the indicator says "Please" Wait" with the last line on the screen reading "/Windows/Systems32/drivers/crcdisk.sys"
[/COLOR]
Or you need a Windows repair CD or flash drive to run the chkdsk on your NTFS partition or make other repairs.

       We used to recommend Neosmart as they had a free download for the Windows repairs. They were offline for a while & I now see they want $10 for the download. [COLOR="#FF0000"]I don't need Visyta that much to have to pay for it again.  I'll go without it if need be.[/COLOR] So make one yourself before you have to pay to get one.
Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

[COLOR="#FF0000"]It's not clear to me if my Windows 7 in this dual boot desktop would work on a Vista partion or not.  Would it work?  Also, can I use a USB flash card instead of a DVD or CD?[/COLOR]

   Also has chkdsk and some other Windows repairs in free version:
[http://www.partitionwizard.com/features.html](http://www.partitionwizard.com/features.html)  [COLOR="#FF0000"]Is chkdsk inside this tool?  It's not clear to me what's inside?  I need to look at the other tools below to understand them better.[/COLOR]

   Repair BCD
[https://neosmart.net/EasyBCD/](https://neosmart.net/EasyBCD/)

   EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

   Third party chkdsk tools
Hiren's Boot CD, and do a chkdsk on the XP
[http://www.hirensbootcd.org/](http://www.hirensbootcd.org/)

---

### Post by oldfred on 2014-04-29
I have used a Windows 7 flash drive to run chkdsk on my XP. But you cannot run some other updates or the auto fix from a different version. With my version it converted the NTFS PBR or partition boot sector from XP using ntldr to Windows 7 type with bootmgr. So I had to convert it back to ntldr with bootsec.exe.

       Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

See also this user who did get f8 to work.
[http://ubuntuforums.org/showthread.php?t=2220772](http://ubuntuforums.org/showthread.php?t=2220772)

Neosmart supposed had copyright issues in distribution a copy of the Windows repair tools. So they had to start charging. But it would make sense to me that you want to make it easy for users to fix your system. Others may not call it chkdsk, but just repairs or something else.

---

### Post by sfink16 on 2014-04-30
My problem has been solved.  This was the only link I found that creates a Vista ISO, so I did just that, create a Vista ISO -> [http://getintopc.com/softwares/operating-systems/windows-vista-download/]("http://getintopc.com/softwares/operating-systems/windows-vista-download/")

I had to use Wine, from within Ubuntu to unzip/extract the ISO file.

Next I used the link provided by oldfred -> [http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html]("http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html")  making sure to use step 2 to create the NTFS from UNetbootin (494) and step 3 replacing the Windows 7 ISO with my Vista ISO.

Next I booted up the USB on my laptop and was greeted by 2 choices.  First, I could have selected to do a fresh install.  Second, I could choose to do a repair.  

I chose number two where the software found my factory installed Vista.  Finally, I was able to reboot without the flash USB into my Grub 2 menu.  In testing both Lubuntu and Vista both worked.

One more question ->  Should I be concerned that my Vista partition only has about 1.5 GBs left?    If I decide I need to redistribute the hard drive, I take it that I should use fdisk within Visat, correct?

Thanks Fred!  I'll mark solved once I figure that out.

Steve

---

### Post by oldfred on 2014-04-30
Everything I have seen with Windows is that you really should have 30% free space or a lot of room. At 10% free system will slow to a crawl and it may take forever to run defrag as there is no working room.

Linux likes some extra space and actually hides 5% to try to prevent you from crashing system if too little space left. But on multi-TB drives the 5% is too much.

I do not have Vista, but does it not have a gui Disk managment? fdisk is command line. 
Usually considered better to use Windows tools to modify the Windows system partition, but not to create new partitions as it may convert to dynamic.

       Shrinking a Windows Vista/7/8 partition is best done in Windows. But do not create new partitions with Windows.
[http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/](http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/)

---

### Post by sfink16 on 2014-05-01
Vista does have a GUI disk management.  I have about 15% free space now.  I'll work on trying to get up to about 30%.

Thanks again Fred!

Steve

---

