---
title: "Going back to Windows"
date: 2013-04-04
forum: Installation &amp; Upgrades
---

### Post by Johnexx on 2013-04-04
Installed Linux on Partition - Liked it,
Installed Linux on Hardrive completely over Windows
Didn't work, couldn't fix it (Black Screen)
Installed Windows again, Could not find Data Grub (Searched everywhere for solution - none worked)
Installed Linux - Worked fine for months, now need to change back due to work requirements, I have got Windows Recovery disks from when I bought the P.

In short -

I need to change from Linux to Windows safely, using recovery disks as well as fix Update New Data To DMI problem so Windows will startup.


Edit - Change Grub to DatA dmi

---

### Post by mikewhatever on 2013-04-04
Windows recovery disks don't use grub, and usually, wipe everything, and install their stuff. I don't think there is anything to fix.
Best of luck.

---

### Post by Johnexx on 2013-04-04
I apologize, I didn't mean Grub....It said Update New Data To DMI

---

### Post by Johnexx on 2013-04-04
I have installed the Recovery discs, and now I have restarted the PC only to be greeted by

AMD Data Change...Update Data to DMI!error: unknown filesystem.
grub rescue>

---

### Post by whatthefunk on 2013-04-04
I might be mistaken, but I dont think you can install Windows from Windows recovery disks.  They are only meant to restore a broken system that already has Windows installed.

---

### Post by frank cox on 2013-04-04
You have to be patient. It can be frustrating if you don't know how to restore windows but once you learn it is a 3 minute operation. If you no longer want Linux on the machine delete the Linux partition and reformat the whole drive to NTFS and run the recovery disks , they will install the system, there is no such thing as a recovery disk that only works on a broken windows , actuall they will not repair at all, they re-install which is what you want. I am sorry you failed to take the time to learn how to duall boot, it is not that hard. No one can really help you as you never mentioned if you were using legacy grub or grub 2. Without that info you will never find the files that need to be changed to get it to boot. There are alternatives to use the machine until you learn how such as booting from a Hiren's boot cd for example. 

The problem you are having is because windows is designed to screw up any os that tries to use the first partition on the first drive other than another windows. Lack of patience to find the proper procedure is the other. I can install Linux anywhere I like and put windows where I want to and it makes litle , if any, difference in how long it takes , it was not always so. One thing that makes Linux so cool is you can have lots of os's on the same machine and just one data partition  shared by Linux and for those who still think they need windows as well.

I have had 6 Ubuntu varients {Ubuntu-LinuxMint, Bohdi etc,} , 5 Puppies , and a few RedHat derivatives running on the same machine ! Some of them booted 2 at a time with a VM. 

You said "work requirements}" forced you to return to windows , what does that mean ? If you need to share MS Office files you can install MS Office under wine or in windows on a virtual machine under Linux. Better yet get SoftMaker Office, it is way faster, totally compatible with MS Word, PP, and Excell and a third the price. I would use the windows version if I used windows but I have been winders free for 3 years and miss nothing whatsover!
[http://softmaker.com/english/blog/](http://softmaker.com/english/blog/)    [http://www.softmaker.com/english/](http://www.softmaker.com/english/)

---

### Post by Frogs Hair on 2013-04-04
**What does a Windows Recovery Disk let you do?**
 
[LIST]
[*]Repair a computer which won’t start up
[*]Allow you to restore your computer to a given restore point
[*]Allow you to restore an image of your machine
[*]Perform a memory (RAM – random access memory) analysis
[/LIST]
 **What does a Windows Recovery Disk not do?**
 
[LIST]
[*]Allow you to install a fresh copy of Windows.
[/LIST]

---

