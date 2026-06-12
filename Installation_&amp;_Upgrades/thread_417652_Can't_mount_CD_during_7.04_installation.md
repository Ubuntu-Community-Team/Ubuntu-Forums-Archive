---
title: "Can't mount CD during 7.04 installation"
date: 2007-04-21
forum: Installation &amp; Upgrades
---

### Post by trinity! on 2007-04-21
I downloaded 7.04 Ubuntu server, created a CD and tried to install it on a Dell Optiplex 260 by inserting the cd in the drive and turning the power on.  I keep getting an error very early in the installation that the CD can't be mounted.  I have tried verifying the cd on that same machine with no luck, same problem.  I tried verifying the cd on another machine and it passed.   I am a long time Windows user and I'm trying to get to know Linux but this is troublng.  I didn't even get passed the first two minutes of the installation. :confused: 

Any suggestions?

---

### Post by KenF on 2007-04-21
Same problem here.  I had this problem with Feisty Herd1 and Feisty Herd3.  Feisty Beta was OK, but the final Feisty had the same problem for me.

In my case, the CDROM drive is a SCSI drive.  The system has an ASUS P2B-S motherboard with an Adaptec 7890 SCSI controller and an Adaptec 3840.  I added various aic7xxx options to the boot prompt with no success.  The boot-up seems to die as it is loading the "Uniform CD Drivers."  Anyway,  I find it strange that the Feisty Beta from 3 weeks back works fine, but that the final release doesn't work.

Any help?  Any ideas on what changed from the Feisty Beta (downloaded April 13th) to the Final Release?

KenF

---

### Post by KenF on 2007-04-22
> **trinity! said:**
> I downloaded 7.04 Ubuntu server, created a CD and tried to install it on a Dell Optiplex 260 by inserting the cd in the drive and turning the power on.  I keep getting an error very early in the installation that the CD can't be mounted.  I have tried verifying the cd on that same machine with no luck, same problem.  I tried verifying the cd on another machine and it passed.   I am a long time Windows user and I'm trying to get to know Linux but this is troublng.  I didn't even get passed the first two minutes of the installation. :confused: 

Any suggestions?


Searching through another part of the forums, I found something that fixed mine.  It seems silly, but choose the "Install with Driver Update CD" (third menu item instead of the first).  It will ask you to insert the driver CD and hit enter.  Just hit Enter.  After a while it will ask you to insert the Install CD and hit enter.   Again, just hit Enter.  It's not supposed to work that way, but .... it worked for me.

KenF

---

### Post by trinity! on 2007-04-22
Thanks for the response but I don't have the menu entry you describe in the menu (Install with Driver Update CD).  Mine are:

Install to hard disk
Check CD for defects
Rescue a broken system
Memory test
Boot from first hard drive

The file I downloaded is "ubuntu-7.04-server-i386.iso".  Do I have the wrong installation file?  Am I referring to the wrong menu?  ](*,)

---

### Post by spiralvoice on 2007-04-22
Same for me, I am using a SCSI-only system
> $ lspci | grep SCSI
01:07.0 SCSI storage controller: Adaptec AIC-7892A U160/m (rev 02)
> $ lsscsi
[0:0:0:0]    disk    SEAGATE  ST318438LW       0003  /dev/sda
[0:0:1:0]    disk    SEAGATE  ST336938LW       0003  /dev/sdb
[0:0:2:0]    disk    IOMEGA   ZIP 100          J.03  /dev/sdc
[0:0:3:0]    cd/dvd  TEAC     CD-W512SB        1.0H  /dev/scd0
[0:0:4:0]    cd/dvd  TOSHIBA  DVD-ROM SD-M1401 X011  /dev/scd1
using ubuntu-7.04-desktop-i386.iso

Its a bit weird that such a renowned distribution like Ubuntu can not
cope with this setup. Using the "Install with Driver Update CD" approach
proposed by KenF worked for me however. I guess this setting is
not available on all install CDs...

I played around with some boot parameters (like "boot aic7xxx")
but they did not work. Any other hints to get Ubuntu detect the
SCSI card without weird tricks?

---

### Post by KenF on 2007-04-22
> **trinity! said:**
> Thanks for the response but I don't have the menu entry you describe in the menu (Install with Driver Update CD).  Mine are:

Install to hard disk
Check CD for defects
Rescue a broken system
Memory test
Boot from first hard drive

The file I downloaded is "ubuntu-7.04-server-i386.iso".  Do I have the wrong installation file?  Am I referring to the wrong menu?  ](*,)

I guess I didn't read your post carefully enough.  It looks like my comment only helps for the "desktop" install.  This is only a guess, but it is based on the fact that from edgy/dapper to feisty the cdrom and hard drive drivers are all listed to look like SCSI devices.  What is odd is that most CDROM drives these days are ATAPI and not SCSI.  Anyway, for some reason, it looks like SCSI CDROM drives don't get mounted properly during the install.

I'm sure a dev or moderator would be able to read the comments in this section and recommend an easy solution.   Perhaps there's already one posted in the "launchpad" area?

KenF

---

### Post by spiralvoice on 2007-04-22
> **spiralvoice said:**
> using ubuntu-7.04-desktop-i386.iso
ubuntu-7.04-alternate-i386.iso found my SCSI CD-ROM during install without intervention.

---

### Post by jayjaygibbs on 2007-04-22
> **trinity! said:**
> Thanks for the response but I don't have the menu entry you describe in the menu (Install with Driver Update CD). Mine are:
 
Install to hard disk
Check CD for defects
Rescue a broken system
Memory test
Boot from first hard drive
 
The file I downloaded is "ubuntu-7.04-server-i386.iso". Do I have the wrong installation file? Am I referring to the wrong menu? ](*,)
 
If you used to be a windoz man then I suggest that you use the desktop edition, I'm sure that will solve the problem aswel as suite your needs

---

### Post by trinity! on 2007-04-22
> **jayjaygibbs said:**
> If you used to be a windoz man then I suggest that you use the desktop edition, I'm sure that will solve the problem aswel as suite your needs

Still am a Windows user.  I am trying to learn more about the linux world but it is not going well.  Windows does have a Server version and I am trying to set up a comparable linux server that includes appliction, database, web etc. servers.  This distro was very attractive since it says it will set up everything during installation (LAMP should be 15 minute install time) without the hours of setup time required for each server product but it seems it is taking hours just to setup the OS.

Thanks for your suggestion but I would like the server distro working.  Any suggestions for a workaround to this problem are appreciated.

---

### Post by pbirch on 2007-04-23
I'm having the same problem using the 7.04 alternate (i386) image.  I'm trying to install onto a Dell Lattitude C640 laptop.  I've installed Edgy, Dapper, and 5.04 with no problems in the past.

So does anyone have a fix for this?  I'm a bit disappointed that this problem occurs with the best Linux Distro available.

---

### Post by Castanea_d. on 2007-04-30
Add me to the list. I am trying to use the Alternate-Install disk for Xbuntu 7.04. My machine is a pretty old Dell -- OptiPlex GX1p, Pentium III, 128 MB of RAM, ATAPI type CD-ROM.

I get the "CD-ROM couldn't be mounted" error.

For what it is worth, I am a complete Linux newbie. My machine currently runs Win95. I purchased a 30-GB hard drive at a computer surplus place and installed it as a second drive, and I hope to install Xbuntu (or some form for Linux) on the second drive, and leave Win95 on the first drive.

---

### Post by .matteo on 2007-05-04
I got my cdrom recognised adding "linux pci=off" parameter to the boot options

---

