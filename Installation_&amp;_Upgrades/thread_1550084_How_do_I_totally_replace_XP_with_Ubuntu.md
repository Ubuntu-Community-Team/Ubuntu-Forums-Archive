---
title: "How do I totally replace XP with Ubuntu?"
date: 2010-08-10
forum: Installation &amp; Upgrades
---

### Post by QuickSnail on 2010-08-10
G'Day,


How do I install Ubuntu and trash XP.  At present I get offered at bootup to choose Windows XP or Ubuntu (which needs the CD to fully setup).


On the laptop I now just want Ubuntu, no XP.  How do I go about it? :confused:

---

### Post by howefield on 2010-08-10
> **QuickSnail said:**
> (which needs the CD to fully setup).

Not sure what you mean by this, but depending on how complicated your setup is, might simply be quicker to install Ubuntu (again) using the "use whole disk" option at the partitioning stage.

---

### Post by linux18 on 2010-08-10
put the live cd in, start gparted
-erase the xp partition (usually ntfs)
-apply
-expand ubuntu partition to fill the whole drive 
-apply
always remember to backup important data

---

### Post by QuickSnail on 2010-08-10
oh-oh.  I pulled the laptop out and switched on.  Forgot to mention current state of disaster;

A while back i got frustrated as to how to remove the ubuntu.... so in the end I just trashed the Ubunyu folder in C Drive.  Not a good idea.

I just powered on.  Its mumbling something about Minimal bash and ends with;
[COLOR=Red]grub>[/COLOR]

---

### Post by dougalkerr on 2010-08-10
Insert a LiveCD of the version you want to use. I use Ultimate Edition on my Dell Studio 1537 with a 2.93GHz processor and 3Gb RAM with a 128Mb graphics card. It runs really fast with absolutely no problems.
It even installs and runs things like HP printers that Windows 7 will not even after a supposed driver update file has been downloaded (I am talking about my work Desktop PC not my home Laptop, I don't use Windows if I can help it).
Ultimate Edition takes a little time to load though but, it is worth the wait. It is heaps better than Windows 7.

It will run a little slow though if your machine is not up to the task of running big programs and things.

I have also used and liked Crunchbang Linux. It is very small and very fast because it is very minimal with nothing fancy to screw things up and it is a good way of becoming familiar with Ubuntu commands and how to install all manner of stuff.

So, where were we...

Follow the onscreen prompts and opt to 'Use entire disc' when the partition manager is loaded. This will wipe and format your whole drive if you opt to format (which you will).
Remember to make a small SWAP space. I like to use twice the amount of RAM that I have so if you have 1Gb RAM then a SWAP space of 2GB will be more than enough. A lot of people use the same size as their RAM.
Then when you have created the disc partition for your Linux system label it / and follow the rest of the install instructions.

Good luck.

---

### Post by linux18 on 2010-08-10
your laptop's current state will require a live cd in order to boot up. once started you can back up important information to a flsh drive and install ubuntu

---

### Post by QuickSnail on 2010-08-10
I have a Cd.  The hassle is at bootup it offers XP or Ubuntu...u have x secs to choose..........

If i pick........ Ubuntu >minimal bash followed by   grub> .
On boot, it wont throw up the cd option because it sees ubuntu already 'on board'.

---

### Post by QuickSnail on 2010-08-10
About the CD.  its labeled 'install ubuntu'.  is that the same as liveCD?

---

### Post by howefield on 2010-08-10
> **QuickSnail said:**
> On boot, it wont throw up the cd option because it sees ubuntu already 'on board'.

Go into your machines BIOS and enable booting from CD in the BOOT options. If your CD is bootable, it should try to boot from it before it tries the hard drive.

Have you backed up anything you need to keep from the hard disk ?

---

### Post by dougalkerr on 2010-08-10
Install Ubuntu???

Haven't coem across that name to Ubuntu LiveCD before... anyways, it sounds like your PC is not allowing you to boot from CD. You must set the option in your BIOS to allow this and even then I still opt for the boot options when the PC starts up.

I have the options of F2 for the BIOS set-up screens or F12 for the boot device options only.

Set-up your BIOS.

If you can't boot from CD then go into XP and insert the LiveCD, it will run in Windows and install will be allowed when it has finished loading.

Or if you can boot into Linux at all the  again run the LiveCD and install once it has finished loading.

---

### Post by Shompol on 2010-08-10
Assuming you have dual-boot and BACKED UP ALL YOUR MY DOCUMENTS in WINDOWS:

System -> Administration -> Disk Manager
1. Delete the windows partition (NTFS or FAT)
2. Increase the partition of your choice to fill up the gap.
3. Edit the grub menu to remove the windows option: [http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html](http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html)

---

### Post by QuickSnail on 2010-08-10
> **Shompol said:**
> Assuming you have dual-boot and BACKED UP ALL YOUR MY DOCUMENTS in WINDOWS:

System -> Administration -> Disk Manager
1. Delete the windows partition (NTFS or FAT)
2. Increase the partition of your choice to fill up the gap.
3. Edit the grub menu to remove the windows option: [http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html](http://www.ehow.com/how_2251661_edit-grub-menu-ubuntu.html)

Man that's scary.  If i lose XP I'll have no OS.
When I go to ehow.com it says;

STEP 1: Boot Ubuntu, login as a user and start a terminal session.

I can't use f12.  This is how the laptop starts.........

POWER ON>toshiba banner>choose windows or ubuntu.  

That's it.  No time.   A quick toshiba banner then next step is "Choose your OP"

If I trash XP are you sure Ubuntu will start again instead of "Minimal Bash > grub>"?
[LEFT][COLOR=#000000]

[/COLOR][/LEFT]

---

### Post by QuickSnail on 2010-08-10
How can I format my C Drive?

I only know 'how to' via the XP CD.  I want to be rid of the XP OS.  Then install ubuntu on a clean C Drive.

---

### Post by howefield on 2010-08-11
> **QuickSnail said:**
> How can I format my C Drive?

I only know 'how to' via the XP CD.  I want to be rid of the XP OS.  Then install ubuntu on a clean C Drive.

You can boot with the Ubuntu Live CD and use System > Administration > GParted to format your drive.

Or you can simply install Ubuntu over your XP install.

There are a few short videos you might want to watch covering partitioning and installing Ubuntu at

[http://screencasts.ubuntu.com/](http://screencasts.ubuntu.com/)

[http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning](http://screencasts.ubuntu.com/2009/09/03/Ubuntu_Partitioning)
[http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install](http://screencasts.ubuntu.com/2009/09/02/Ubuntu_Dual_Boot_Install)
[http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen](http://screencasts.ubuntu.com/2009/08/25/Ubuntu_Live_Installer_Boot_Screen)

There are many others.

But as others have said, ensure that you back everything up that you wouldn't want to lose.*

---

### Post by QuickSnail on 2010-08-11
Thanks 4 replying.
The ubuntu CD i have came from here.

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Its useless.  Is there a better one??

REcapping.

XP  _exists_.
_installed_ above ubuntu as demo
So laptop boots up with toshiba banner then....
>select xp or ubuntu to boot up with........

I couldn't figure out how to remove ubuntu so eventually I trashed ubuntu folder from C Drive while i was in XP.

So now there is a major problem.  Ubuntu at boot is still there.  But selecting ubuntu takes you to a command called grub>

Access to F12 ain't there.  Its just toshiba banner>choose your op system

If i use the ubuntu CD it says "to install u must reboot".  Reboot= toshiba banner>select OS> ubuntu>grub.

The question is there a program to format C Drive so i can start over?
Or what command can I tell grub to solve the issue?

---

### Post by arpanaut on 2010-08-11
To get the CD to boot first you will need to access your bios and designate the CD drive to be the first in the boot order, see this link as to how you get into the bios menu.

[http://uk.computers.toshiba-europe.com/innovation/faq.jsp?service=UK&FID=0000000401](http://uk.computers.toshiba-europe.com/innovation/faq.jsp?service=UK&FID=0000000401)

---

### Post by QuickSnail on 2010-08-11
Relief.  Thanks.  Not used to the This Toshiba laptop.  NetBios = ESC > F1.  Thank you.:D

---

