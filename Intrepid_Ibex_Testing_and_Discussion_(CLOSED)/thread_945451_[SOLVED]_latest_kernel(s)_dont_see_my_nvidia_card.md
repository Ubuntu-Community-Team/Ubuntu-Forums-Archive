---
title: "[SOLVED] latest kernel(s) dont see my nvidia card"
date: 2008-10-12
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by ubername on 2008-10-12
Hi

After recent upgrades I can't get compiz to work. I think this is because the system does not seem to see my nvidia card. I have nvidia-glx-177 installed, but when I try 'Restricted drivers' I am told that no proprietary drivers are installed, and when I try to enable visual effects from 'preferences it checks for available drivers then says 'desktop effects cannot be enabled'

Any Clues?

TIA

(BTW my post number 300!)

---

### Post by mikedep333 on 2008-10-12
Open up jockey-gtk (hardware drivers) and install the version 173 driver.

The 177 driver that is included in intrepid was intended only for the GTX 200 series (at least according to Nvidia.)

---

### Post by plun on 2008-10-12
It seems that all of us are "lost in the jungle" about nVidia drivers.

First file a bug about your trouble.

Also remember to include these
 /var/log/Xorg.0.log 

/etc/X11/xorg.conf


Then test **envyng** which is available within Intrepids repo

```
sudo envyng -t
``` from a terminal

You can also install a downloaded driver from nvidia and install from tty, gdm must  first be stopped. After install just restart gdm

---

### Post by plun on 2008-10-12
> **mikedep333 said:**
> 
The 177 driver that is included in intrepid was intended only for the GTX 200 series (at least according to Nvidia.)

Please read release notes/readme.

[http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/177.80/README/appendix-a.html)

---

### Post by bull205 on 2008-10-12
Can I get in on this??  I am having the same problem.  I believe that I have an intel graphics card as well.  I get the same result when I try to enable desktop effects.  I also don't have any restricted driver listed when I goto the hardware driver menu.

I am running a sony vaio laptop SR-165E.  Output of my lshw says I have a cantiga integrated graphics controller.

I don't want to highjack your post, but I would like to walk with you as this gets solved...

>    *-pci
          description: Host bridge
          product: Cantiga Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 07
          width: 32 bits
          clock: 33MHz
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Cantiga Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Cantiga Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 07
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0


---

### Post by ubername on 2008-10-12
> **mikedep333 said:**
> Open up jockey-gtk (hardware drivers) and install the version 173 driver.

The 177 driver that is included in intrepid was intended only for the GTX 200 series (at least according to Nvidia.)

No Joy

---

### Post by ubername on 2008-10-12
> **plun said:**
> It seems that all of us are "lost in the jungle" about nVidia drivers.

First file a bug about your trouble.

Also remember to include these
 /var/log/Xorg.0.log 

/etc/X11/xorg.conf


Then test **envyng** which is available within Intrepids repo

```
sudo envyng -t
``` from a terminal

You can also install a downloaded driver from nvidia and install from tty, gdm must  first be stopped. After install just restart gdm

I am not sure that this fixed it, but after a restart (and installing envyng) my restricted drivers icon pooped up saying I had a number of nvidia drivers available, and now compiz (and beryl theme manager, which I had always struggled with~) seem to be working well!

Thanks a lot, all.

---

### Post by Kevbert on 2008-10-12
Please check your software sources. The top four boxes under Ubuntu software should be ticked and under Updates Important, recommended and Unsupported updates should be ticked.  Then go to terminal (if no updates are indicated in the top righthand corner of your desktop and enter
```
sudo apt-get update
sudo apt-get upgrade
```
Hopefully then the Nvidia driver will update and you should have the restricted driver.  Don't forget to download CCSM if you don't have Advanced Desktop Effects (under Preferences).
If you still have problems try running [[COLOR="Red"]compiz-check[/COLOR]]("http://forlong.blogage.de/entries/pages/Compiz-Check").

---

### Post by plun on 2008-10-12
Well... this is just  :confused::confused::confused::confused:

I knows that Alberto and Martin looks at this so hopefully
it will work for all.

:)

---

### Post by klamari on 2008-10-12
Hello plun

running envyg -t gives the following output for me:

> Traceback (most recent call last):                                              
  File "interface.py", line 428, in <module>                                    
    a = Interface()                                                             
  File "interface.py", line 126, in __init__                                    
    self.abstract = abstraction.Abstraction(progress, True)                     
  File "/usr/lib/python2.5/site-packages/Envy/abstraction.py", line 39, in __init__
    self.driverDetails = self.hardware.selectDriver()                           
  File "/usr/lib/python2.5/site-packages/Envy/detection.py", line 248, in selectDriver
    if 173 in candidates['nvidia'] and 177 in candidates['nvidia']:
TypeError: list indices must be integers

What does the error mean?
The reply from ubername that things are fixed on his end gave me some hope, but now I am stuck again...

Greetings  
martin

---

### Post by plun on 2008-10-12
Run with sudo

Works for me
```

plun@plun:~$ **sudo envyng -t**


 +-------------------------------------------------+
 |                                                 |
 |             Welcome to EnvyNG                   |
 |    Developed by Alberto Milone (aka tseliot)    |
 |                                                 |
 +-------------------------------------------------+


 +-----------------------------------------------------------+
 |    EnvyNG Menu                                            |
 |                                                           |
 |    1 - Install the NVIDIA driver                          |
 |                                                           |
 |    2 - Uninstall the NVIDIA driver                        |
 |                                                           |
 |    3 - Install the ATI driver                             |
 |                                                           |
 |    4 - Uninstall the ATI driver                           |
 |                                                           |
 |    5 - Restart the Xserver                                |
 |                                                           |
 |    6 - Restart your computer                              |
 |                                                           |
 |    7 - Exit                                               |
 |                                                           |
 |    NOTE: IF THE SCREEN TURNS BLACK, PLEASE TYPE ALT+F1    |
 +-----------------------------------------------------------+
Please select one of the activities displayed above and press ENTER:
```


Good Luck !

---

### Post by klamari on 2008-10-12
Sorry, was run in sudo envyng -t, also tried sudo envyng -k as I am using KDE

so, bad luck

---

### Post by plun on 2008-10-12
> **klamari said:**
> Sorry, was run in sudo envyng -t, also tried sudo envyng -k as I am using KDE

so, bad luck

Ok... we must beat this one..

This is packages

[http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=envyng](http://packages.ubuntu.com/search?suite=default&section=all&arch=any&searchon=names&keywords=envyng)

In your case with KDE

```
sudo apt-get install envyng-core envyng-qt
```

or  use Adept.

I dont have KDE installed for the moment so I cannot test.

You should also get a GUI entry for EnvyNG.


EDIT tested in Gnome and it work (qt package)

sudo envyng -k

---

### Post by klamari on 2008-10-12
Hello again plun (and of course anyone else:) )

With 8.04 it works fine but on 8.10 still get above error message, guess something in my whole setup got wrong but just re-installed 8.10 today from scratch, all I did is getting all the updates via apt-get
Will try now with the old kernel...
otherwise no idea

Thanks anyway, linux is a lot "learning by doing" I guess

---

### Post by ubername on 2008-10-13
I took the admittedly dramatic step of reinstalling from a 64 bit alpha 5 desktop CD (6/9/8) and then doing all the upgrades. I has fixed my compiz issues and I am back to square one on my sound issues ([http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=913328](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=913328)), but at least I know where I am starting from, as I had messed with so many things that I had lost track of what I had / had not done.

---

### Post by dabl on 2008-10-13
My experience with the Restricted Drivers Manager, aka jockey-kde, has been spotty.  It worked well in Alpha 5, but no go in Beta, then I got hit with the e1000e module blacklist (with no backup kernel) and ended up re-installing a daily build from 6 or 7 OCT.  On this one, I installed the downloaded Nvidia 177.80 driver and it works perfectly.  One upgrade last week did a stealth partial disabling of the driver -- although it appeared to be running and the screen looked right, Compiz wouldn't start, and upon investigation glxgears wouldn't run, but a re-installation of 177.80 put me back in business, and it's been working fine through the past 3 or 4 days' of updates.

So, if jockey and EnvyNG aren't working right, you might consider trying the downloaded driver. Don't forget to install the kernel-headers and build-essential packages in advance.  :)

---

### Post by ubername on 2008-10-24
Long time ago now - recent upgrades seem to have fixed - marked as 'solved'.

---

