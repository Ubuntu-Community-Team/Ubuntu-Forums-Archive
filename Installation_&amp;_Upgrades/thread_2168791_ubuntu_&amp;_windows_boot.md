---
title: "ubuntu &amp; windows boot"
date: 2013-08-19
forum: Installation &amp; Upgrades
---

### Post by osaga on 2013-08-19
here's what I have... first drive, I had win XP and then installed ubuntu.. worked great and I had access to both... I ended getting another drive and installed windows 8, with its boot the only way I could access the ubuntu is if I booted of the first drive.. which was fine cuz I still had access to all 3... but having problems with XP, I did a repair and now its all messed up, I tried bunch of things, even ran a live cd and tried the boot repair which now the grub ONLY loads ubuntu..
heres the 'link' it generated:
[http://paste.ubuntu.com/6000783](http://paste.ubuntu.com/6000783)

can I keep all 3 OS with only 1 boot manager?

---

### Post by carl4926 on 2013-08-19
So you can boot Ubuntu?
Please try this from Ubuntu

```
sudo update-grub
```
```
sudo grub-install /dev/sda
```

---

### Post by osaga on 2013-08-19
thanks for the quick reply... I did upgrade grub.. seems to be stuck...

give me a message...

found...so and so
found... so and so
found memtest...

and nothing after  that besides a flashing cursor under memtest... about 5 min already

---

### Post by carl4926 on 2013-08-19
In the nautlius file browser
Open the windows partitions as if to read the files, for both XP and Windows 8
Is there an error with accessing windows 8 or is it OK?

---

### Post by osaga on 2013-08-19
ok.. I'll try that.. I'll let you know after I come home.... looking over the grub report.. it said something .. "[COLOR=#BB4444]XP not detected by os-prober on sda1. Please report this message to [email]boot.repair@gmail.com[/email]"

[/COLOR]

---

### Post by oldfred on 2013-08-19
Windows installs its boot files to the active partition (boot flag) of the drive you have set to boot from with BIOS. So it looks like Windows 8 installed its boot files to your XP install.

Boot files in XP, You also have grldr or grub4dos, so were you using EasyBCD?
     Boot files:        /boot.ini /grldr /bootmgr /Boot/BCD /grldr /ntldr 
                       /NTDETECT.COM

      
 Windows Boot files:
WinXP
/boot.ini /ntldr /NTDETECT.COM
Vista/7/8 (with 7 or 8 the first two files are usually in a separate 100MB boot partition) Yours are in XP.
/bootmgr /Boot/BCD /Windows/System32/winload.exe 

I might install a Windows boot loader to sdb and make repairs so Windows 8 boots without any other drive. You would have to install the Windows boot loader to the MBR and set BIOS to boot sdb before running Windows 8 repairs.

      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)
But then files may be corrupted similar to Windows 7 Hibernation:
[http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html](http://ubuntu-with-wubi.blogspot.ca/2012/09/windows-8-fast-start-and-hybrid-sleep.html)
[http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot](http://superuser.com/questions/144720/missing-files-when-windows-7-returns-from-hibernate-w-dual-boot)
Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
Force removal of hiberfil from Ubuntu
[http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/](http://www.hecticgeek.com/2013/01/mount-windows-8-partition-ubuntu-hybrid-boot/)

---

### Post by osaga on 2013-08-19
> **carl4926 said:**
> In the nautlius file browser
Open the windows partitions as if to read the files, for both XP and Windows 8
Is there an error with accessing windows 8 or is it OK?

ok, I have no problems reading the first drive with XP and ubuntu... BUT now the win8 drive does not even show up in the browser.. but it was there yesterday before I ran the boot repair

but the second drive does show up in the bios... the grub is installed on the second (win8) drive ... if I diable/unplug the second drive than nothing loads up.. I get a grub rescue screen

---

### Post by carl4926 on 2013-08-19
Last machine I worked on with 2 drives and winders 8 I had to have the windows 8 HD 1st in the BIOS boot order
But my knowledge is incomplete because the customer to a look at windows 8 and hated it, and we replaced it with windows 7.

I don't know how knowledgeable you are or how easy you will find, but...

You could make the win8 HD first and repair it's MBR
Replace the Ubuntu HD and use the live cd  to repair grub (installing to sda) (the windows 8 HD) MBR

---

### Post by osaga on 2013-08-21
ok.. this is what i did so far... set the 2nd drive (IDE: win8 and grub boot) to be the 1st boot drive.. booted off the win8 cd and went into command prompt... ran chkdsk c:.. no problems.. ran chksdk d: (sata: winXP and ubuntu) which found few 'index' errors... ran chkdsk with /f option to fix errors

once done, I wanna disable/remove the the second drive and run the fixmbr and fixboot on the xp drive
then, remove the xp drive and connect the win8 and do the same
once the xp can boot off the 1st by itself and the win8 can boot by itself when the 1st boot is set to second drive
then I wanna run the ubuntu live cd and try the boot repair...

ok.. with the second drive ddisconnected.. I got the xp to boot..

---

### Post by osaga on 2013-08-22
YES.. I finally got it... I repaired win8 boot with bootrec /fixmbr
so, I had first drive boot into xp and second into win8 and still nothing for ubuntu..
I downloaded boot editor... easy BCD.. with it, took me less than a minute to add all three into the boot menu...finally I can select any OS without having to switch drive boot!!

---

### Post by osaga on 2013-08-22
the EASY BCD is awesome!!
thanks all for help

---

