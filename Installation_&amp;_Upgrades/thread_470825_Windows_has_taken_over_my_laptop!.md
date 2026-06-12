---
title: "Windows has taken over my laptop!"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by Elrohir on 2007-06-11
SOMEONE! HELP! THE DARK SIDE IS UPON ME!!!
 
lol... no, seriously!
 
last night I went for a complete cleaning of my laptop so I reformatted the HD and I what I did was (as usual) to install Windows first (I need it for some development) and on top of that Ubuntu...
 
Problem: once I got Windows installed, I CAN'T BOOT INTO LIVE CD!!! WTF??!! has anyone experienced this? any pointers? I'm coming desperate... help? :(

---

### Post by wpshooter on 2007-06-11
You say "and on top of that Ubuntu", did you install Ubuntu to your hard drive or are you just trying to run Ubuntu from the CD ?

---

### Post by Elrohir on 2007-06-11
> **wpshooter said:**
> You say "and on top of that Ubuntu", did you install Ubuntu to your hard drive or are you just trying to run Ubuntu from the CD ?
Right now, trying to boot the Live CD so I can install Ubuntu...

---

### Post by Elrohir on 2007-06-11
I can't boot any CD... not even by changing the boot sequence on the BIOS... It boots straght from the HD... I'm going desperate on this...

---

### Post by wpshooter on 2007-06-11
Do you have a floppy drive on your machine ?

---

### Post by Elrohir on 2007-06-11
no... laptop... Toshiba Satellite A105-S361

---

### Post by wpshooter on 2007-06-11
My suggestion was going to be that if you had a floppy drive to make the floppy the first boot device in BIOS and then see if you could boot to a WIN98 bootable diskette.

IF you are positive that you have the boot order set as CD-ROM drive 1st on the listing and IF you are certain that what you are trying to boot to is a BOOTABLE CD and it wouldn't boot to them, then there must be something wrong with the BIOS of your computer.  Have you tried booting to the WINDOW CD of  O/S that you installed and see if it will boot to that.

If that does not work I would go into BIOS and write down all parameters and then set ALL values back to defaults, then boot the machine, then shutdown and then go back in and reset all BIOS values to the proper settings including making the CD-ROM the first boot device.

Good luck.

---

### Post by Elrohir on 2007-06-11
ok, so here's where I stand now... I followed your procedure with no luck... so I went for the BIOS upgrade... YAY! I can boot live CD now...
 
wait... what now?
 
Ubuntu doesn't login... it halts at the brown screen before the splash screen comes up... and it stays there... :(

---

### Post by wpshooter on 2007-06-11
Do you have Ubuntu installed on your hard drive or not ?

If you are just running from the CD, I don't believe you would get a log-in screen.

Have you tried booting the live CD using the safe video graphics mode parameter ?

---

### Post by Elrohir on 2007-06-11
i mean the splash screen, the one that shows when Nautilus, Gnome Panel is loading... that I don't get... it halts just before that, so I don't get a Desktop, nor can install... I'll try the safe graphics mode... never thought of that... just wondering, is there a way to install via CLI?

---

### Post by stchman on 2007-06-11
> **Elrohir said:**
> SOMEONE! HELP! THE DARK SIDE IS UPON ME!!!
 
lol... no, seriously!
 
last night I went for a complete cleaning of my laptop so I reformatted the HD and I what I did was (as usual) to install Windows first (I need it for some development) and on top of that Ubuntu...
 
Problem: once I got Windows installed, I CAN'T BOOT INTO LIVE CD!!! WTF??!! has anyone experienced this? any pointers? I'm coming desperate... help? :(

Let me ask an ultra obvious question:

I am going to assume you downloaded the .iso image file.  Did you simply burn the .iso file to a CD?  If so then that is the problem.  This is a common mistake.  You need to burn it as an image not as a data CD.

It is strange that you installed Windows (XP I assume) and then cannot get the Ubuntu CD to boot.

The OS is independent of the BIOS booting order.

---

### Post by wpshooter on 2007-06-11
stchman:

It sounds like to me that they are getting at least part the way thru the loading of the Ubuntu O/S live CD.  Just hanging at a certain point.

Wonder what software they used to clear the drive ?

I would use:  [www.killdisk.com](www.killdisk.com)  

Then would reinstall XP from scratch and then come back and try the LIVE Ubuntu CD again.

Let me ask the poster this inportant question ?  Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

If Ubuntu LIVE CD checks out O.K. and then still will not install, they may want to download, burn and try the ALTERNATE (text based) CD.

Good luck.

---

### Post by Elrohir on 2007-06-11
> **wpshooter said:**
> stchman:

It sounds like to me that they are getting at least part the way thru the loading of the Ubuntu O/S live CD.  Just hanging at a certain point.

Wonder what software they used to clear the drive ?

I would use:  [www.killdisk.com]("http://www.killdisk.com")  

Then would reinstall XP from scratch and then come back and try the LIVE Ubuntu CD again.

Let me ask the poster this inportant question ?  Did you check the integrity of your Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu ?

If Ubuntu LIVE CD checks out O.K. and then still will not install, they may want to download, burn and try the ALTERNATE (text based) CD.

Good luck.
The cd I have is one of the 3 I requested to ShipIt! and, yes, I also checked it for errors (just in case), came out clean... I'll go for the full monty now (I know it has nothing to do, but just in case), I'll format the disk using [GParted]("http://gparted.sourceforge.net")...

Wish me luck!

---

### Post by Elrohir on 2007-06-11
Updates: Uninstalled completely Windows from HD, BIOS has been upgraded, but still can't get to live CD's Desktop... this really getting annoying... 

just for some testing, I went to CLI (Ctrl+Alt+F1) and restarted GDM (Ctrl+Alt+Backspace) and I DO get a login (where it says ubuntu user will login in 10 seconds)... So I let it log in... no dice... same result... But somehow I made a further step, now appears what it looks like a window, borderless and textless though... Last time I saw a window like this was on Edgy when while loading Deskptop it appeared an error saying that a module couldn't be loaded, but once I closed that window, Desktop loaded... might be the same thing here, but I have no output son can't be sure... :(

This version its gaining his name: FEISTY!

---

### Post by merlinus on 2007-06-11
You can try the Alternate Desktop cd from ubuntu.com.  It is a text-based installer, and will work when there are video incompatibilities that can be sorted out later.

Good luck!

-merlin

---

### Post by Elrohir on 2007-06-11
Download the ISO? *sighs*

new moves: restarted GDM and changed the session to Failsafe GNOME... nada... Virtual PC is becoming really friendly right now...

*me preparing the single shot*

---

