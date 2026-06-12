---
title: "Uninstall Ubuntu from Vista Dual boot with no recovery CD"
date: 2009-12-31
forum: Installation &amp; Upgrades
---

### Post by ph9enix on 2009-12-31
I'm dual booting Ubuntu 8.10 and Windows Vista, but need to uninstall Ubuntu to free up space on the windows partition.  Vista didn't come with any installation CDs as it was preinstalled on my laptop, though I do have a separate recovery partition for it.  I'm fairly certain this partition is only useful for restoring the computer to factory conditions (wiping the hard drive to a fresh Vista install), which I can't do.  I need a way to remove Ubuntu, reclaim its partition for Vista, keep all my windows files in their proper places, and hopefully restore the boot loader as well.  Can this be done?

---

### Post by k64 on 2009-12-31
> **ph9enix said:**
> I'm dual booting Ubuntu 8.10 and Windows Vista, but need to uninstall Ubuntu to free up space on the windows partition.  Vista didn't come with any installation CDs as it was preinstalled on my laptop, though I do have a separate recovery partition for it.  I'm fairly certain this partition is only useful for restoring the computer to factory conditions (wiping the hard drive to a fresh Vista install), which I can't do.  I need a way to remove Ubuntu, reclaim its partition for Vista, keep all my windows files in their proper places, and hopefully restore the boot loader as well.  Can this be done?

Try going into Control Panel\Programs\Programs and Features\, selecting Wubi (Windows Ubuntu Installer), and then "Uninstall". I'm assuming the install is WUBI the way you worded this post, which you can use the Windows Uninstaller for.

---

### Post by ph9enix on 2009-12-31
There's no WUBI in my programs and features.  I have ubuntu in a full install on a separate partition, not a Live CD install through Vista

---

### Post by raymondh on 2009-12-31
If Ubuntu is in it's own partition (not wubi-installed)...

[Download this first and burn to CD.]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/")  

-  back-up your files/data.  No guarantees.
-  Use the liveCD and go live session try ubuntu...)
-  Access gparted (system > admin > partition editor) and use that to delete the ubuntu and it's swap partition. Also the extended, if any.  In order ... Ubuntu > swap > extended partition. 
-  Exit gparted and the liveCD ... and boot into windows.
-  Access the windows disk management utility and use that to extend/enlarge the existing windows partition
-  when ok, reboot windows and allow it to run its' checkdisk.
-  You still have GRUB in the MBR.  If you want to fix the MBR, boot into the disc I asked you to burn.  Select REPAIR computer > command prompt > type

bootrec.exe/fixmbr

If success, type EXIT.  If not, type (one at a time)

bootrec.exe/fixboot
bootrec.exe/fixmbr
exit


If this is a wubi-install ... [see this guid]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")e.  You will have to also edit the boot.ini file in windows to remove the wubi-related line.


Post back for clarification or, if you encounter errors.

Regards,

---

### Post by ph9enix on 2009-12-31
It's definitely not WUBI
The main issue is that the files I need to keep I can't really back up
They're for Ableton Live projects (Music making software)
and if they're not all in their proper places all my projects get wrecked
I'd back them up and put them back, but there are probably over a thousand all scattered about.
If anyone has a surefire way of doing this without any risk to the files in my windows partition it would be much appreciated

Alternatively, I could just keep ubuntu running on very little space if there's a way to reallocate some of its partition to windows without actually deleting ubuntu

---

### Post by raymondh on 2009-12-31
Yes you can.  If you need a mini-how-to, post back a screenshot of gparted to help visualize your HD.

[http://gparted.sourceforge.net/larry/resize/resizing.htm](http://gparted.sourceforge.net/larry/resize/resizing.htm)

Sorry to say but even re-sizing partitions has risks of losing data...

---

### Post by ph9enix on 2009-12-31
Anyone know what would happen if I just go to Vista's partition management,([http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista))
delete the ubuntu partition, and expand the vista partition to fill its place?

---

### Post by raymondh on 2009-12-31
> **ph9enix said:**
> Anyone know what would happen if I just go to Vista's partition management,([http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista))
delete the ubuntu partition, and expand the vista partition to fill its place?

This [threa]("http://ubuntuforums.org/showthread.php?p=8588969#post8588969")d may help.

Best wishes ... good luck.

---

### Post by presence1960 on 2010-01-01
> **ph9enix said:**
> Anyone know what would happen if I just go to Vista's partition management,([http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista))
delete the ubuntu partition, and expand the vista partition to fill its place?

You will have gotten rid of Ubuntu but your machine would be unbootable with a GRUB error because GRUB will still be on MBR of your disk. This is assuming Vista & Ubuntu are installed on the same disk.

Raymond gave you a link to download an iso and burn it as image to CD in post #4. This CD will give you the ability to run Vista Recovery which will allow you to replace GRUB with the Vista bootloader on MBR. Boot that CD and do this:

_**How to restore the Windows Vista or 7 bootloader**_

To restore the Windows Vista/7 bootloader, you must first boot off your Windows Vista/7 installation DVD.
If you have one of the many OEM computers that didnt come with a Vista/7 installation disk, you can get the same effect with a Vista recovery disk, which you can download from here (see post #4 by Raymondh).
When you get to the Regional settings, select your Location/Keyboard setting then click next. On the next page you must click on "Repair your computer."

On the next page, if it finds your Windows Vista/7 installation, make sure it is UNSELECTED before clicking next.
Then click on "Command prompt". From there, type in the folowing:

```
bootrec.exe /fixboot
```

```
bootrec.exe /fixmbr

```
Now close the two windows and click "Restart."

Do that first then go to Vista's disk management and get rid of Ubuntu partition(s). You need to fix your MBR so windows will boot.

---

### Post by Moozillaaa on 2010-01-01
> **ph9enix said:**
> Anyone know what would happen if I just go to Vista's partition management,([http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista](http://www.vistarewired.com/2007/02/16/how-to-resize-a-partition-in-windows-vista))
delete the ubuntu partition, and expand the vista partition to fill its place?


You can delete the partition, and you don't need to expand the Vista partition (and risk problems). Just do a NTFS 'Quick Format' as a second partition...

Oops - I see the Vista loader will not work with GRUB wiped...

---

