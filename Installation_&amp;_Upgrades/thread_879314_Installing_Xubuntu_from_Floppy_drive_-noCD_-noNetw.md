---
title: "Installing Xubuntu from Floppy drive? -noCD -noNetwork -noUSB"
date: 2008-08-03
forum: Installation &amp; Upgrades
---

### Post by grossaffe on 2008-08-03
OK guys, i've got a really old laptop here that not only lacks a CD drive, but it doesn't have a network adapter or a USB port.  Basically the only way to put stuff on there is through floppy disk.  Is there a way to install Xubuntu via floppy drive?

---

### Post by Sef on 2008-08-03
This [tutorial]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") was for breezy, but it may work for you.

---

### Post by grossaffe on 2008-08-03
> **Sef said:**
> This [tutorial]("https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies") was for breezy, but it may work for you.

That one won't work as it utilizes a USB.

oops, i guess I forgot to mention that in first post; no USB drive

---

### Post by SoloSalsa on 2008-08-03
I think your only option is to install to your target drive from another machine.

---

### Post by grossaffe on 2008-08-03
> **SoloSalsa said:**
> I think your only option is to install to your target drive from another machine.

that is exactly what I didn't want to hear.  oh well.

How about other (graphical) Linux distros?  are there any good ones that install from a floppy?

---

### Post by logos34 on 2008-08-04
Puppy Linux or Damn Small Linux

---

### Post by grossaffe on 2008-08-04
> **logos34 said:**
> Puppy Linux or Damn Small Linux

I've been looking at those two but haven't been able to locate any good directions for installing via floppy disks.

---

### Post by logos34 on 2008-08-04
[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29]("http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_with_Netcard_%28Poormans_Install%29")

There used to be a 'floppy-Puppy', but apparently they've discontinued it in the present 4.0 release.  Maybe try [an older version]("http://linux.wareseeker.com/System/puppy-linux-2.17.1.zip/334856")...Once you're up an running on linux do a xubuntu [install from hard disk.]("https://help.ubuntu.com/community/Installation/FromLinux") 

There's also BasicLinux floppies:
[http://distro.ibiblio.org/pub/linux/distributions/baslinux/](http://distro.ibiblio.org/pub/linux/distributions/baslinux/)

---

### Post by kerry_s on 2008-08-04
what are the specs for that old laptop?

---

### Post by grossaffe on 2008-08-04
> **kerry_s said:**
> what are the specs for that old laptop?

Unfortunately I can't seem to get to the screen that says what all it has anymore.  Ever since the last time I entered that screen its just been turning on, checking ram, telling me I have an invalid system disk.  All I can tell you now is that it has 12160KB RAM.

The model is Toshiba T3400CT if you really want to look it up.


anyways, I finally found a way to install Damn Small Linux that works for a computer with:
No CD
no Network card
no USB port

[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_(No_Netcard%2C_Linux_Only](http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_(No_Netcard%2C_Linux_Only))
I have yet to try it out (60 friggin floppies!), but it should work.

---

### Post by snowpine on 2008-08-04
> **grossaffe said:**
> Unfortunately I can't seem to get to the screen that says what all it has anymore.  Ever since the last time I entered that screen its just been turning on, checking ram, telling me I have an invalid system disk.  All I can tell you now is that it has 12160KB RAM.

The model is Toshiba T3400CT if you really want to look it up.


anyways, I finally found a way to install Damn Small Linux that works for a computer with:
No CD
no Network card
no USB port

[http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_(No_Netcard%2C_Linux_Only](http://www.damnsmalllinux.org/wiki/index.php/Floppy_Only_Install_(No_Netcard%2C_Linux_Only))
I have yet to try it out (60 friggin floppies!), but it should work.

Wow, that is an old-timer! You might have to go even lighter than DSL on that one. :)

---

### Post by grossaffe on 2008-08-04
> **snowpine said:**
> Wow, that is an old-timer! You might have to go even lighter than DSL on that one. :)

really?  Windows 95 used to run on here before I swapped hard-drives.  Is DSL gonna be slower than Win95?

---

### Post by snowpine on 2008-08-04
> **grossaffe said:**
> really?  Windows 95 used to run on here before I swapped hard-drives.  Is DSL gonna be slower than Win95?

If I'm doing the math correctly, your computer has 12mb of ram... damnsmalllinux.org recommends a minimum of 16 (and xubuntu requires 128mb for a typical installation). Not saying it won't work (because I have never tried it) but ask yourself if it's worth 60 floppies to find out. :)

There are distros out there for really, really ancient computers (deli comes to mind)... poke around and you'll find some very informative threads here on the forums.

---

### Post by grossaffe on 2008-08-04
> **snowpine said:**
> If I'm doing the math correctly, your computer has 12mb of ram... damnsmalllinux.org recommends a minimum of 16 (and xubuntu requires 128mb for a typical installation). Not saying it won't work (because I have never tried it) but ask yourself if it's worth 60 floppies to find out. :)

There are distros out there for really, really ancient computers (deli comes to mind)... poke around and you'll find some very informative threads here on the forums.

Oh goodness, I didn't even bother to do the math.  I was thinking it was near much higher in RAM.  Don't know why since the hard-drive it came with was about 120MB (which I upgraded to 2 GB).

---

### Post by stchman on 2008-08-04
> **grossaffe said:**
> OK guys, i've got a really old laptop here that not only lacks a CD drive, but it doesn't have a network adapter or a USB port.  Basically the only way to put stuff on there is through floppy disk.  Is there a way to install Xubuntu via floppy drive?

A laptop that old would not even run Xubuntu.  How old is this laptop?  What is the processor?  Memory?

Also Xubuntu is about 550MB which is ~380 floppies.

You could try removing the hard disk and install it via another PC and replace.

---

### Post by stchman on 2008-08-04
> **grossaffe said:**
> really?  Windows 95 used to run on here before I swapped hard-drives.  Is DSL gonna be slower than Win95?

Remember Windows 95 is over 13 years old so yes DSL is going to be more processor intensive.

The original Windows 95 ran on 8MB RAM with a 386 processor.

[http://support.microsoft.com/kb/138349](http://support.microsoft.com/kb/138349)

The latest Puppy is far more advanced.

---

