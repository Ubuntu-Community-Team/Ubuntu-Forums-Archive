---
title: "Problems installing Ubuntu"
date: 2007-09-11
forum: Installation &amp; Upgrades
---

### Post by zinite on 2007-09-11
Hi, I recently purchased a laptop, and decided to convert my old desktop into an ubuntu-powered box. I downloaded the official 7.04 iso, and burnt it using Nero. My friend told me I didn't need to format my hard drive because the install process would do it for me. I put the disk in, and upon booting from CD and running the install I get this:

 "/bin/sh: can't access tty; job control turned off"


...


and after awhile it'll just sit there putting out messages like this:

"[1827.081060]  ata1.00: exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
 [1827.081115] cmd c8/00:08:00:00:00/00:00:00:00:00/e0 tag 0 cdb 0x0 data 4096 in"

If i restart the computer and run it in Graphic-Safe mode (or whatever it's called), it does the same thing but eventually loads the Live CD. When I click the Install button on the desktop, and the "Prepare Partitions" step appears blank (there is no partition to choose from).

I tried downloading and running 7.10 Gutsy to see if that would work: no luck. I tried burning 7.04 on a different computer in case it was the burner that was creating a malfunctioning disk. No luck.

Following some advice I found on google, I downloaded SystemRescueCD and used it to format the drive into an ext3 file system. The drive is now empty, containing 1 148 gigabiyte ext3 partition. Still, no partition appears on the Prepare Partitions page.

I'm 100% new to linux, but i'm a pretty advanced Windows user (that apparently doesn't mean anything once you step into a new operating system).

Thank you in advance for your help, I sincerely appreciate it. I was hoping this would be a painless conversion but, as it always is with computers, it's very frustrating.

Edit: I've also tried doing the proposed fix "break=top" for the tty error. As soon as i hit enter, my keyboard stops working so I cannot enter the other part of the fix. Is there anything I can put in that "advanced options" field that won't kill my keyboard? I'm running a Logitech G15 keyboard.

---

### Post by Sef on 2007-09-11
1) Did you [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") the download?

2) Did you burn the cd at 4x or less?  (Faster can corrupt the burn.)

3) Check the cd for defects.

---

### Post by merlinus on 2007-09-11
Did you run the Check CD option at the startup menu?  DId you burn at no more than 4x?

---

### Post by zinite on 2007-09-13
Thank you for your suggestions,

The CD was made at 4x speed, and the md5 is the same.

I can get Ubuntu up now, but on step 4/7 on the installer, "Prepare Partitions", there is no partition to choose from. Where do I go from here?

---

### Post by Pumalite on 2007-09-13
How much memory do you have and what graphics?

---

### Post by rocketero on 2007-09-13
did you try to install it from one of the ubuntu (Feisty or Gusty) LIVE CD's available?

after you boot from the Live CD there is an icon on the desktop to install it, I did it that way in one computer, and installed fine.

Also you could try partitioning the hard disk from this same Live CD, in one of the menus I don't recall exactly there is a menu-item to deal with the partitioning. If this program don't find any disks on your computer to partitioning then let us know to follow from there.

---

### Post by zinite on 2007-09-13
1 Gig of Memory, 150gb hard drive, nvidia 5800 graphics card. 

Yes, I'm booting it from the Feisty Live CD. When I bring up GParted (the partitioning device you're thinking of), it says "No devices detected" on the bottom left corner.

---

### Post by Pumalite on 2007-09-13
I would use the Alternate CD. Use gparted to prepare your partitions ahead of time. 
( the stand alone, burn to CD, boot from, program): [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
[http://gparted.sourceforge.net/documentation.php](http://gparted.sourceforge.net/documentation.php)
Do md5sum on the iso, then burn it with ImgBurn(free): [http://www.imgburn.com/](http://www.imgburn.com/)
Install, go to Mode>ISO>Burn
When using Gparted, if you are not dual booting, make one large partition of your hard drive, format ext3, then install>Guided>Use Entire Disk
Good luck.

---

### Post by maybeway36 on 2007-09-13
You don't need gparted if you're using the whole drive.

---

### Post by d00derino on 2007-09-13
I get the same problem. My ISO file's hash matches up and I burnt it at 4x (and 24x and 10x) and I'm always getting this error. My system *should* be able to run it.

I have:
-667 MHz
-191 MB Ram
-11 GIG HDD

Which is why I'm trying to switch to Linux in the first place, to use this as a stripped down PC only for work. Anyhow, I can't get away from this error. Every listing I press (except memory check) leads me here. The CDs all work; they'll load IN Windows, but I want this to replace Windows 98.

---

### Post by Pumalite on 2007-09-13
You don't mention graphics, but I suspect they are integrated; that would leave you with less than 191 MB RAM. You might try Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
That still leaves the question of your graphics being supported. Good luck.

---

### Post by zinite on 2007-09-15
Sigh... 

Alright, using the Alternate disk, after attempting to detect my CDROM drive, I get this:

```
No common CD-ROM drive was detected.

Your CD-ROM drive may be an old Mitsumi or anther non-IDE, non-SCSI
CD-ROM drive. In that case you should choose which module to load and
the device to use. If you don't know which module and device are
needed, look for some documentation or try a network installation
instead of a CD-ROM installation.

Manually select a CD-ROM module and device?

none
cdrom
gscd
isp16
mcdx
optcd
sjcd
sonycd535


```


Then I try the most obvious one, cdrom, and it gives me this:

```
In order to access your CD-ROM drive, please enter the device file
that should be used. Non-standard CD-ROM drives use non-standard
device files (such as /dev/mcdx).

You may switch to the shell on the second terminal (Alt+F2) to check
the available devices in /dev with "ls /dev". You can return to this
screen by pressing ALT+F1.

Device file for accessing the CD-ROM:
```

Then it tries something in /dev and it doesn't work. I can't proceed with the installation because the next couple steps error out because it can't access the CD-ROM drive.

---

### Post by Pumalite on 2007-09-15
Did you go to CLI with Alt+F1 to check /dev available?. What happened?

---

### Post by Pumalite on 2007-09-15
It would also help to know the specs of your CD-ROM. Maybe we can fix the problem in BIOS:

---

### Post by weathergeek2021 on 2007-09-29
I have exactly the same problem. I am trying to install Xubuntu (Feisty Fawn) with the Alternate Disk and I get the exact same error. I don't know how to fix it.

Specs:
Gateway 933C (non supported anymore)
Windows Me
11 Gigs HDD
127 MB RAM
Mitsumi CD-ROM FX4831!A

It also says that if the CD-ROM installation doesn't work, you should try network installing. I wont be getting the computer networked until I get my networking equipment. If network install works, I'll post it.

---

### Post by Pumalite on 2007-09-29
Have you tried installing a smaller distro such as: Zenwalk, DSL, or Puppy?

---

### Post by weathergeek2021 on 2007-09-29
I've tried those.

---

### Post by Pumalite on 2007-09-29
That might be your size.

---

### Post by weathergeek2021 on 2007-09-29
I doubt it. I just need 4 Gigs for Xubuntu. I think its the problem of CD ROM drive. How can I get around that problem?

---

### Post by weathergeek2021 on 2007-09-29
> **zinite said:**
> Sigh... 

Alright, using the Alternate disk, after attempting to detect my CDROM drive, I get this:

```
No common CD-ROM drive was detected.

Your CD-ROM drive may be an old Mitsumi or anther non-IDE, non-SCSI
CD-ROM drive. In that case you should choose which module to load and
the device to use. If you don't know which module and device are
needed, look for some documentation or try a network installation
instead of a CD-ROM installation.

Manually select a CD-ROM module and device?

none
cdrom
gscd
isp16
mcdx
optcd
sjcd
sonycd535


```


Then I try the most obvious one, cdrom, and it gives me this:

```
In order to access your CD-ROM drive, please enter the device file
that should be used. Non-standard CD-ROM drives use non-standard
device files (such as /dev/mcdx).

You may switch to the shell on the second terminal (Alt+F2) to check
the available devices in /dev with "ls /dev". You can return to this
screen by pressing ALT+F1.

Device file for accessing the CD-ROM:
```

Then it tries something in /dev and it doesn't work. I can't proceed with the installation because the next couple steps error out because it can't access the CD-ROM drive.

That is the error specfically. I've used the "mcdx" command and I've also tried the "cdrom" command.

---

### Post by Pumalite on 2007-09-29
This: 127 MB RAM, with integrated graphics is your problem.

---

### Post by weathergeek2021 on 2007-09-29
I'm using the Alternate Disc

---

### Post by Pumalite on 2007-09-29
Yeah...but the system you install has to be able to make it on the RAM you have.
Plug a stick of RAM in there. Memory is cheap nowadays.

---

### Post by johnnydoe1894 on 2008-02-04
Was there ever a resolution for this?  

I have the same problem installing 7.10 on an HP X-Class workstation with a Mitsumi FX4830T CDRom 52X, it has a Gig of Ram, dual 866 processors, dual 10K 18gig SCSI drives so ram shortage is not the problem.  

Is there a driver for this on the alternate install CD?  I looked in /dev and nothing there looked like a driver but being a NOOB I don't know. 

If not does anyone know where to get one?  Is there a way around this?  This CD will run in DOS or windows with a default setup, hard to imagine there's no support for it in Ubuntu especially since there's tons of these drives around.

---

### Post by stevetsc on 2008-04-29
I have had issues on an HP Visualize X-Class Workstation, Model A1280 (Dual Pentium 3 @ 866MHz w/2GB of RAM).  In Ubuntu 8.04 the system begins to load, then when it should start the x-server the system halts.  Any ideas what's going on with this?

--EDIT--
After playing around a bit more, such as exchanging graphics cards / testing other distributions I've found Fedora 9-preview works on my HP Visualize "Kayak" X550 (Uniprocessor Xeon 550MHz w/1GB of RAM) with a PCI graphics card (replacing the existing workstation graphics card that is a weird AGP & PCI slot double-decker card which is also present in the A1280) so tonight I plan on attempting installing Ubuntu again.  I will also be trying the same with my X-Class A1280.  Hopefully it's only the graphics card crashing me to the BusyBox (intiramfs) prompt.  Still, if you have any information, please let me know, thanks!

---

### Post by Sir_Willard on 2008-04-29
Hey all, 
I am a total NOOB here, and had the same errors that halted the system from working.  This may help a few others also
in BIOS, if you have a PATA/SATA mode, you HAVE to set it to combined mode instead of enhanced mode.  I did that and 8.04 worked with no problem.  If you have windows as well (like I do) the next time it starts it will detect your drives as IDE instead of SATA, but work just fine.  
This is my first time using Ubuntu, and it was a 2 hour fight to get it going, but I went back to windows to make sure it worked, and it sure feels clunky after using this!

Hope this fixes a few more of you that still have issues

---

### Post by kochecc2 on 2008-05-01
I had the same problem ("No Devices Detected" in the Partition Editor) with an older machine and I changed the hard drive jumper from Master to Cable Select. Master seemed to work when it had Windows on it, or the CD drive was from another box, but the CD drive was set to CS, so making sure they were the same is what fixed me. Hope this helps.

---

