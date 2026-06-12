---
title: "cannon pixma mx432 scanner help"
date: 2012-12-19
forum: Installation &amp; Upgrades
---

### Post by C9ILL on 2012-12-19
kinda new to ubuntu been using it for a year. Running 11.10  In the past i've been able to solve my issues by searching the internet.  But now I'm trying to install cannon pixma mx432 printer scanner. I got the printer working but I'm having a hard time with the scanner i get this message when i have sane find scanner 

  # sane-find-scanner will now attempt to detect your scanner. If the
  # result is different from what you expected, first make sure your
  # scanner is powered up and properly connected to your computer.

  # No SCSI scanners found. If you expected something different, make sure that
  # you have loaded a kernel SCSI driver for your SCSI adapter.

found USB scanner (vendor=0x04a9 [Canon], product=0x175b [MX430 series]) at libusb:001:007
  # Your USB scanner was (probably) detected. It may or may not be supported by
  # SANE. Try scanimage -L and read the backend's manpage.

  # Not checking for parallel port scanners.

  # Most Scanners connected to the parallel port or other proprietary ports
  # can't be detected by this program.
 

any help or if some on can point in a direction i got the .deb driver from cannon asia

---

### Post by pdc on 2012-12-21
so you downloaded MX430 series ScanGear MP Ver. 1.90 for Linux (debian Packagearchive)

it comes in as [COLOR="SeaGreen"]scangearmp-mx430series-1.90-1-deb.tar.gz[/COLOR]

.......the goal is to install Canon's programme called ScanGearMP

can I suggest some commands?

> [COLOR="Red"]cd Downloads[/COLOR]

> [COLOR="Red"]tar -zxvf scangearmp-mx430series-1.90-1-deb.tar.gz[/COLOR]

> [COLOR="Red"]cd scangearmp-mx430series-1.90-1-deb[/COLOR]

> [COLOR="Red"]./install.sh[/COLOR]

..........the install script should install the correct package for you

.....to run it...........

> [COLOR="Red"]scangearmp[/COLOR] in a terminal will open the programme

......*so you are using a Canon programme to run your scanner* .....

you may well find a launcher automates this process 

.......... I think .........

[http://handytutorial.com/install-qle-unity-launcher-quicklist-editor-in-ubuntu-12-04-12-10/](http://handytutorial.com/install-qle-unity-launcher-quicklist-editor-in-ubuntu-12-04-12-10/)

this will do what you need .......

(I use gnome 2 and it creates launchers more easily......)

---

### Post by Chasehead on 2013-04-17
Also remember that it the "scangearmp" executable will not show up in the Unity dash by default so you must run it from the command line as "scangearmp" or double click the icon from within the /usr/bin/ directory. I find it helps to just copy it to the desktop or somewhere else that's easy to remember. There are ways to add it the dash properly but that's way too much effort for people like me.

Here's where I found the rest of the information needed to solve this puzzle:

[http://forums.linuxmint.com/viewtopic.php?f=49&t=121215](http://forums.linuxmint.com/viewtopic.php?f=49&t=121215)

---

### Post by prj44 on 2013-12-07
Thanks to those who have tried to make this work properly. But I am having the most frustrating of Noob experiences.  The sw installs, just fine.  Thanks for the commands.  The preview scan works just fine.  But when I try to do a scan, I enter the filename "testscan" but the sw then refuses to scan until I enter filename; it won't accept my keystrokes!  It won't allow me to select a folder as a destination!  <Gnash!>

I haven't yet tried to find a way to put it on the desktop.  I just want a scan!

Thanks in advance.

---

### Post by Resistent on 2013-12-07
> **prj44 said:**
> Thanks to those who have tried to make this work properly. But I am having the most frustrating of Noob experiences.  The sw installs, just fine.  Thanks for the commands.  The preview scan works just fine.  But when I try to do a scan, I enter the filename "testscan" but the sw then refuses to scan until I enter filename; it won't accept my keystrokes!  It won't allow me to select a folder as a destination!  <Gnash!>

I haven't yet tried to find a way to put it on the desktop.  I just want a scan!

Thanks in advance.

That's not scangearmp's fault. I could always use my keyboard in the program. Does is happen always ?
And in other programs ?

---

### Post by prj44 on 2013-12-07
Thanks.  Keyboard works just fine everywhere else.  It works when I enter a filename; the text appears when I type..  But there are no folders evident and no way to select a folder to save the output.  When I press Save, the msg is "No filename."  I'm bewildered.

---

