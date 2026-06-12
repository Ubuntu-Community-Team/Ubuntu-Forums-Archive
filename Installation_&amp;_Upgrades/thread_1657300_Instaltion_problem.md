---
title: "Instaltion problem"
date: 2011-01-01
forum: Installation &amp; Upgrades
---

### Post by seatsea on 2011-01-01
I want to install ubuntu 10.10 alongside XP but all the CD's don't start (the CD's are The linux format magazine DVD and the 10.10 CD). When I install ubuntu via Wubi, if I ubgrade from 10.4 to 10.10 I can't star up Ubuntu and it gives me this eror mesage "eror: file not found".

---

### Post by Idefix82 on 2011-01-01
What exactly do you mean by "the CDs don't start"? Is CD-ROM the first option in the boot order in your BIOS? If not, then you should enter the BIOS (F1 or F2 or F12 or something else, you should hopefully be told what, immediately when you start the computer, before Windows starts booting) and change the order of the boot devices accordingly.

---

### Post by Rubi1200 on 2011-01-01
Hi and welcome to the forums seatsea :-)

If this is a Wubi install, see here for issues and solutions:
[http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

In your situation, as you describe it, you have problem #2, needs solution #2.

If for some reason that does not work, use solution#1.

However, if you have a problem starting the CD we need to sort that out first as you will need it.

Is BIOS set to boot from the CD drive?

---

### Post by seatsea on 2011-01-01
> **Idefix82 said:**
> What exactly do you mean by "the CDs don't start"? Is CD-ROM the first option in the boot order in your BIOS? If not, then you should enter the BIOS (F1 or F2 or F12 or something else, you should hopefully be told what, immediately when you start the computer, before Windows starts booting) and change the order of the boot devices accordingly.

well i mean that the CD starts up but it stays on Ubuntu with the 4 dots under it.

---

### Post by Rubi1200 on 2011-01-01
What graphics card do you have installed?

---

### Post by seatsea on 2011-01-01
I have a NVIDIA GeForce Ti 200

---

### Post by Rubi1200 on 2011-01-01
Okay, this is what you need to try:

Put the LiveCD in and boot up;

when you see the Ubuntu logo hit Enter;

Choose language and leave the default Try as a live cd or whatever it says again;

Important: hit F6 and then Esc to see the boot line

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz quiet splash --**

Now, again this is important, move the cursor backwards and remove quiet splash;

Add the following parameter:

nomodeset

In other words, the boot should look like this:

**file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.lz nomodeset --**

Now hit Enter and hopefully you will be at the desktop.

You may need to try F6 and Esc as the first step.

If this gets you booting the LiveCD, we can then move to the next step.

---

### Post by seatsea on 2011-01-01
I still have a problem "[ 90.150696] Buffer 1/0 error on device loop, logical block 676315" and other erors.

---

### Post by Rubi1200 on 2011-01-01
It sounds as if that might be a corrupt or damaged disk. 

When do you see these errors, at what stage?

Are you able to get hold of another LiveCD?

---

### Post by seatsea on 2011-01-02
I see the error messages show up when I have Done F6 and escape and all the rest.The CD that I used is one that I created on a different computer and i can create a new one.

I forgot to tell you my computer is a dell from 2002

---

### Post by seatsea on 2011-01-02
I have just tried a new crated DVD and it works.\\:D/
Shold I install ubuntu? 

Oh, and thanks for the help so far.

---

### Post by Rubi1200 on 2011-01-02
Okay, if it works then this is what I would like you to do.

Start the computer with the LiveDVD and choose to try not install Ubuntu.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here so we can see what is going on with your setup.

Then we can advise you as to the next step.

---

### Post by seatsea on 2011-01-02
Well here is what you asked me:
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

sdb: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files/dirs:   

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   156,232,124   156,232,062   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/sda1        4414ECDB14ECD14A                       ntfs                                     
/dev/sda: PTTYPE="dos" 
/dev/sdb         149CC3579CC331D2                       ntfs                                     

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect /TUTag=QXO3B8 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn

---

### Post by dino99 on 2011-01-02
a little help:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by Rubi1200 on 2011-01-02
Thanks for the results.

Okay, so you currently have Windows XP installed.

You have an 80GB drive and want to install Ubuntu; correct?

You do not have Ubuntu installed.

Is the DVD you created now version 10.10 or 10.04?

It makes a big difference in terms of the advice on how exactly to install.

Also, let me know how much space you want to give Ubuntu. I recommend at least 20-30GB, but it depends on what you want to do.

---

### Post by seatsea on 2011-01-02
I have 10.10 on the DVD, but I want to install it on the 200GB hard drive, if possible.

---

### Post by Rubi1200 on 2011-01-02
From the LiveDVD, please post the output of this command from the terminal:
```
sudo parted -l
```
(lowercase L not 1)

Is the 200GB drive currently plugged in?

---

### Post by seatsea on 2011-01-02
Here are the results:
```
Model: ATA WDC WD800BB-75CA (scsi)
Disk /dev/sda: 80.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type     File system  Flags
 1      32.3kB  80.0GB  80.0GB  primary  ntfs         boot


Model: ATA WDC WD2000JB-00G (scsi)
Disk /dev/sdb: 200GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
 1      0.00B  200GB  200GB  ntfs


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: /dev/sr0: unrecognised disk label
```

And I have mounted the 200GB Drive.

---

### Post by Quackers on 2011-01-02
The 200GB drive is currently occupied by a 200GB NTFS partition. Ubuntu will not install in a NTFS partition. That partition needs to be either deleted which would leave the disc unallocated and Ubuntu could install there, or reduced in size, leaving some unallocated space for Ubuntu.
Is that partition currently used for anything?

---

### Post by seatsea on 2011-01-03
Yes that partition is used by some programs on XP, so I would prefer to reduce the size of that partition.

---

### Post by Idefix82 on 2011-01-03
Make sure you defragment the drive before you resize the partition!

---

### Post by seatsea on 2011-01-04
I suppose I do that on the ubuntu installation.

---

### Post by seatsea on 2011-01-04
I have decided to put only Ubuntu on my PC.
How can I do that? Because with the way to start Ubuntu via the live DVD is not working.
sorry for the change.

---

### Post by Idefix82 on 2011-01-06
A couple of days ago you said
> **seatsea said:**
> I have just tried a new crated DVD and it works.\\:D/


but now you are saying that the DVD is not working. Could you elaborate, how it is not working? First of all, can you boot with it?

---

### Post by seatsea on 2011-01-09
I have solved the problem with the DVD, but when I install Ubuntu it doesn't boot up. It stays at this point:
[IMG]http://www.hackourlife.com/wp-content/uploads/2010/05/Ubuntu-10.04-Lucid-Lynx.png[/IMG]

---

### Post by Rubi1200 on 2011-01-09
You probably need to use the nomodeset option I mentioned earlier in the thread.

Try again and see what happens.

More info:
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.
(courtesy of forum member oldfred)

---

### Post by seatsea on 2011-01-09
Thanks for your help but I still have a problem. I am using a different computer but is less powerful so in the future I will come back to computer that has the problem.

So I will say the thread is paused.

---

