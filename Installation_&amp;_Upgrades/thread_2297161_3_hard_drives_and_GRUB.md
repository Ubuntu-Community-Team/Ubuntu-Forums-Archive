---
title: "3 hard drives and GRUB"
date: 2015-10-01
forum: Installation &amp; Upgrades
---

### Post by jlumbtx on 2015-10-01
I currently have two HDs in my desktop- one with Win7 and one with Lubuntu.  If I install a 3rd HD with Win10, will GRUB display all the drives and let me select among the three?
I propose to use Win10 but I want to keep the Win7 drive up to date by opening it and running the lastest MS updates every couple of weeks. 

John

---

### Post by pfeiffep on 2015-10-01
I have no direct experience with Win 10, but I suspect that installing it on a third HDD might be ok. If you can disconnect the Lubuntu drive all the better.
You should plan on executing this command after all three drives are connected and you've booted Lubuntu ```
sudo update-grub
``` this should identify Win 10
Hopefully someone with Win 10 and Linux experience will confirm for you.

---

### Post by oldfred on 2015-10-01
Best if you also disconnect Windows drive.

Windows only boots from the one drive set as default boot in BIOS, and then using the one NTFS partition with the boot flag. A second install of Windows that is newer overwrites all the boot files in the first install and adds the first install to the BCD so you can boot both Windows. But you cannot then boot second install on its own via BIOS or grub.

Are Windows & Ubuntu both in BIOS boot mode, or newer UEFI?

I thought Microsoft was going to automatically update old systems??

---

### Post by jlumbtx on 2015-10-03
oldfred,

My PC is about 5 years old so it uses BIOS, not UEFI.  
I have edited GRUB so that Windows is the first item on the GRUB screen and Ubunti is the second. 
I am waiting for the go-ahead from MS to upgrade the C drive's Win7 to Win10.   I have a third HDD (not in the PC) with Win7 cloned on it.
I am just trying to find an easy way to keep the cloned Win7 up to date in case I want to use it- short of opening the case 
occasionally. disconnecting the C drive, connecting the cloned drive, updating it, then putting everything back the way it was.
I was hoping to get the cloned Win7 drive as the third item on the GRUB screen.  Maybe not possible.

John

---

### Post by oldfred on 2015-10-03
Windows will not boot from an external USB drive. If an eSATA connection seen as an internal drive then it may work. Windows does checks to make sure you are not using a portable drive. It is licensed for one computer only.

---

### Post by jlumbtx on 2015-10-04
How did UBS get involved?
I will restate my goal:  one PC with three internal HDDs.  One HDD with Win10.  One HDD with Win7.  One HDD with Ubuntu.   
All three drives displayed on GRUB enabling me to open any one of the three.
Is it practicle?

John

---

### Post by oldfred on 2015-10-04
This is more for two installs on one drive, but explains how all Windows in BIOS mode work.
 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
[http://www.multibooters.co.uk/articles/windows_seven.html](http://www.multibooters.co.uk/articles/windows_seven.html)

With another drive, probably easiest to disconnect other drives. But if you make BIOS boot from the new drive you install into before install, Windows should then install its boot files to that drive. If other Windows drive is default second install will put all boot files on first installs boot partition as explained above.

Then with two bootable Windows systems, grub will find both. Its just from each Windows you will not be able to directly boot the other. But you still should be able to directly boot from BIOS. Just make sure you keep Windows boot loaders on Windows drive and grub only on Ubuntu drive and BIOS boot from Ubuntu drive.
Never run auto-fix from Boot-Repair as that installs grub to all drives. You can use advanced mode.

---

### Post by jlumbtx on 2015-10-08
OK.  I'll give it a try.  Thanks
John

---

