---
title: "Try(hd0, 0): ntfs5: error: &quot;prefix is not set&quot; after installing Xubuntu 11.10 from XP"
date: 2012-03-21
forum: Installation &amp; Upgrades
---

### Post by Sseo on 2012-03-21
I'm trying to install Xubuntu 11.10 from Windows XP for almost 20 hours now. I tried at least 5 times, changing partitions, installing in online and offline mode, but when I restart PC after Wubi finish the install, and I choose to boot Xubuntu on the boot menu I'm getting this error:
 
```
Try(hd0, 0): ntfs5: error: "prefix is not set" 
```
 
I can't install it from CD because I don't have a Disk Burner right now, nor I have a big enough USB stick(yup, I know it sounds silly for 2012 :P).
 
I think I'm good enough to follow your instructions, but I am almost completely new in Ubuntu field, so please try to explain as good as possible :P
 
I hope this data will help you to understand my problem:
 
- I did a disk check from XP on both partitions - there are no errors.
 
-I have partitions C: and E:. Xubuntu is currently installed on E:. 
 
-Content of C:/boot.ini:
 
```
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Xubuntu"
```
 
-Content of E:/boot.ini:
 
```
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
C:\wubildr.mbr = "Xubuntu"
```
 
- E:/ubuntu/disks/root.disk is present(size 19.3gb)
 
-E:/ubuntu/disks/boot/grub/ is empty
 
-Content of Results.txt from Boot Info Script:
 
```
                  Boot Info Script 0.60    from 17 May 2011
 
 
============================= Boot Info Summary: ===============================
 
 => Windows is installed in the MBR of /dev/sda.
 
sda1: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr /wubildr.mbr
 
sda2: __________________________________________________________________________
 
    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:   No errors found in the Boot Parameter Block.
    Operating System:  
    Boot files:        /boot.ini /ntldr /NTDETECT.COM /wubildr 
                       /ubuntu/winboot/wubildr /wubildr.mbr 
                       /ubuntu/winboot/wubildr.mbr /ubuntu/disks/root.disk 
                       /ubuntu/disks/swap.disk
 
sda2/Wubi: _____________________________________________________________________
 
    File system:       
    Boot sector type:  Unknown
    Boot sector info:  
    Mounting failed:   mount: unknown filesystem type ''
 
============================ Drive/Partition Info: =============================
 
Drive: sda _____________________________________________________________________
 
Disk /dev/sda: 82.0 GB, 81964302336 bytes
255 heads, 63 sectors/track, 9964 cylinders, total 160086528 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
 
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
 
/dev/sda1    *             63    61,432,559    61,432,497   7 NTFS / exFAT / HPFS
/dev/sda2          61,432,623   160,055,594    98,622,972   7 NTFS / exFAT / HPFS
 
 
"blkid" output: ________________________________________________________________
 
Device           UUID                                   TYPE       LABEL
 
/dev/loop0                                              squashfs   
/dev/sda1        E8ECB97FECB94898                       ntfs       
/dev/sda2        742809E12809A36B                       ntfs       E
 
================================ Mount points: =================================
 
Device           Mount_Point              Type       Options
 
/dev/loop0       /rofs                    squashfs   (ro,noatime)
/dev/sda1        /media/E8ECB97FECB94898  fuseblk    (rw,nosuid,nodev,allow_other,blksize=4096,default_permissions)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
 
 
================================ sda1/boot.ini: ================================
 
--------------------------------------------------------------------------------
[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect 
C:\wubildr.mbr = "Xubuntu" 
--------------------------------------------------------------------------------
 
================================ sda2/boot.ini: ================================
 
--------------------------------------------------------------------------------
[boot loader] 
timeout=1 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS.0="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /noexecute=optin 
C:\wubildr.mbr = "Xubuntu" 
--------------------------------------------------------------------------------
 
======================== Unknown MBRs/Boot Sectors/etc: ========================
 
Unknown BootLoader on sda2/Wubi
 
00000000  30 30 30 30 30 30 30 30  30 30 30 30 30 30 30 30  |0000000000000000|
*
00000200
```
 
Any help is appreciated! :)
 
*I've just tried to install Linux Mint 12 LXDE with "mint4win" and I'm getting exactly same error :S :S :S

---

### Post by bcbc on 2012-03-21
That's not actually an error. Well the 'error' part is but it happens on every wubi install, every time it boots (since 11.04 was released) and so it's more an error that there's an error.

So... you could wait a minute or so and see what happens. The last time someone reported this sort of problem they said it took a minute before it finally booted. This isn't normal though.

Maybe try defragging your drive?

---

### Post by Sseo on 2012-03-22
Thank you for your answer :) This is kinda weird. Is there a lets say known problem when some PC's work ok with gnome, but have problems with KDE, XFCE... ? :S

- I have Mandriva KDE(some older version) on a live CD. When I try to  install I'm having some issues(which I should probably mention here, but  I don't remember them).

- I have a Linux Mint 12 KDE on a live cd and after I go to trying mode  and click on "Install Linux Mint" nothing happends in next few  hours(tested few times)

- I tried to install Xubuntu few times and I got this error every time.

- After that I was trying to install Linux Mint XFCE with "mint4win" and I got same problem

- After that I tried to install Debian(KDE or XFCE), installation run smoothly, but after install is finished I have problems with logging in(I can't log in)

Gnome part:

-I have a live CD for Ubuntu 10.04 GNOME and both live mode and installing mode works like a charm(Only thing because I had to go for some other linux is that I can't set the resolution higher then 800x600, I tried literaly every tutorial on the internet but without success).

-I just installed Ubuntu 11.10 GNOME with Wubi without a single problem, and now everything works great(At least I hope).

Is there a chance that my PC is not compatible with versions other than GNOME ?

*I'm not a native english speaker, so please forgive me for my bad grammar :)

Regards.

---

### Post by bcbc on 2012-03-22
What brand/model and graphics card do you have?

---

### Post by Sseo on 2012-03-27
I have an very old configuration. Thats why I would like to use Xubuntu, or some XFCE linux instead of Gnome or KDE. Ubuntu Gnome 10.10(or 04) works great for me except there is no way I can set up my monitor to work on 1024x768 resolution :S (I had problems with old monitor also, but tutorials helped me to fix it, unfortunately not helping with current monitor :S).

Motherboard: AsRock P4VM800
Processor: Intel Celeron CPU 2.13GHz
RAM: DDR1 768MB(704 actually, because of integrated graphic chip)
Display: VIA/S3G UniChrome Pro IGP (64MB)
Monitor: Hansol 730ED
I think sound card, network etc are not important...

---

### Post by bcbc on 2012-03-28
I can't find anything useful on this... :( maybe create a new thread with a title that refers to the graphics card/monitor - you might get some more help.

---

### Post by Sseo on 2012-03-29
I'm pretty sure I have some problems with my partition where I try to install it. Thread solved(by getting USB drive and using it for installation)

---

### Post by Anil Mathew on 2012-10-08
Try(hd0, 0): ntfs5: error: "prefix is not set" after installing Xubuntu 11.10

---

### Post by Skara Brae on 2012-11-02
[*bump*]

...not wanting to hijack this thread... but my Wubi install of "Maya" seems to have failed just a few minutes ago.

Since I can't get "Maya" and/or Xubuntu 12.04 installed in a regular dual-boot (and since Fedora 17-with-Gnome 3 stinks and Fedora-with-xfce just doesn't feel nicely), I tried Mint4win.
I, too, get that "*Try (hd0 0) ntfs5 error prefix is not set*" message on my screen for quite a long time. Then I got a black screen with

=============================================
"Completing the Linux Mint installation.
For more installation boot options, press 'ESC' now...
0
- (*blinking cursor*)
=============================================

and nothing else.

Thank heavens for the Reset button, again.

-oo-

I am now officially giving up GNU/Linux and returning to that propietary OS... (Windows Vista, if anyone is wondering; I do not plan to ever install Win 7 (let alone buy legally), which I don't like, and I will of course not even mention Win 8. A Mac would be an alternative, if it weren't so disgracefully expensive.).

All that hassle to get Linux on my new computer is really not worth it (anymore). I want a computer that *lets* me work, not one that *makes* me work.

In the end, Vista isn't so bad yet... Well... Yeah... Nevermind my saying this :roll:

*Oh, how I so miss my defective, old, loyal Athlon64-based computer...*

I wish all the GNU/Linux users out there "a lot of fun".

---

### Post by Pee-Tor on 2013-07-07
On one of my computers, my Ubuntu installation has worked fine for the past year and a half at least, I think even longer. Today, all of a sudden, my computer froze and there was nothing I could do but cut the power and reboot the hard way. When I boot this computer now, I'm getting this error message (Try(hd0,0): NTFS5: error: "prefix" is not set) and after a while I get the grub prompt. Any ideas?

---

### Post by bcbc on 2013-07-08
Pee-Tor, see [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

