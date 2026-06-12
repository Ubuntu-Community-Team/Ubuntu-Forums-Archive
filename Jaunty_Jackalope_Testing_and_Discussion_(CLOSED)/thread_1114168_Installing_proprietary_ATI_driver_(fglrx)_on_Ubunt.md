---
title: "Installing proprietary ATI driver (fglrx) on Ubuntu 9.04 beta"
date: 2009-04-02
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by nkteam on 2009-04-02
I'm having problems with opensource ATI drivers.
When I'm for example scrolling through FireFox, or any 2d operation, screen start to flicker (some fuzzy lines appears) inside vertical area (~2cm wide) on the right side of the screen. On the other side, I didn't have this problem with Ubuntu 8.10.

I want to install proprietary ATI driver, but cannot find instructions on how to uninstall this one and install fglrx driver, and wanted to ask for instructions before I start playing with that...

Instructions I found are targeted to older Ubuntu versions.
Anyone have some time to help?

Thanx!!!

---

### Post by Pyker on 2009-04-03
I think that the instructions are basically the same for all versions, but, have you tried the following code?

```
sudo apt-get install xorg-driver-fglrx
```

---

### Post by nkteam on 2009-04-03
yes... but that only messed up my xorg configuration :(. After that I was unable to start graphical environment :(
So, I deinstalled it, changed xorg.conf and went to where I was, using 'radeon' SGI drivers :)

---

### Post by Pyker on 2009-04-03
Sorry about that, I guess I missed a command.

This time try:
```
sudo -i
apt-get install xorg-driver-fglrx
dpkg-reconfigure xserver-xorg
```

Sorry for messing up your Xorg configuration.
It should work now.

---

### Post by Mark Phelps on 2009-04-03
Two other ways to install the proprietary drivers are:
1) Download the source from the AMD/ATI site along with the installation instructions.  Follow the instructions for installing the drivers.
2) Download EnvyNG and run it.  It will open a menu that will allow you to select what you want done (Install ATI drivers).

---

### Post by nkteam on 2009-04-03
thanx, I'll try

---

### Post by MaximCarnage on 2009-04-04
well i can report that envy doesn't properly install it. also fails to work properly, preventing the graphical environment from starting properly.

the official drivers using the instructions from [http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Jaunty_Installation_Guide)
also fail.

---

### Post by markbuntu on 2009-04-04
If you are on jaunty you need to use hardware drivers to get flgrx. The one at ati will not work with jaunty because it does not have support for the jaunty xserver.

---

### Post by MaximCarnage on 2009-04-04
the unreleased driver the 8.600 dont work for me either. Tried them and they caused the same problem with the graphical environment

---

### Post by ktp on 2009-04-04
That could be because latest fglrx might not suppost your card...they dropped support for R500-R300.

If you know your card is supported then you can try removing the xorg config and creating a new one using

aticonfig --initial

I am also seeing that open source drivers are having issues in 9.04 when it was working great in 8.10.  I was able to improving by using following xorg config

[http://ubuntuforums.org/showpost.php?p=6971991&postcount=6](http://ubuntuforums.org/showpost.php?p=6971991&postcount=6)

---

### Post by Yuka on 2009-04-04
I'm having the same issue in 8.04 LTS (Hardy Heron). I installed everything properly (nothing failed following the guides), but when I restart X (gdm or even reboot) it fails to start it correctly: gives me a window saying "low res mode" and some options wich fail to start the fglrx drivers and monitor resolution.

My Rig is an AMD64X2/nF4 based system with a Radeon 4850, kernel 2.6.24-23-generic. More info next:

```
yuka@lime:~$ lspci | grep ATI
05:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 9442
05:00.1 Audio device: ATI Technologies Inc Unknown device aa30
```

That gives me a question: are my kernel modules outdated for my 4850 or its just lspci?

If you guys need anything else, i'll be online.

BTW, I'm new to Ubuntu, came from Gentoo to try it out and guys, I'm liking it by the minute! Amazing job Developers!

TYVM!

Esop!

PS: My first post :P

---

### Post by MaximCarnage on 2009-04-04
thanks for that. hope those settings hold up :)

ati really picked the worst time to jump ship :( 
I hope they would atleast release 1 functioning set of drivers 9.04 before they leave everybody in the dark

---

### Post by ktp on 2009-04-04
> **MaximCarnage said:**
> thanks for that. hope those settings hold up :)

ati really picked the worst time to jump ship :( 
I hope they would atleast release 1 functioning set of drivers 9.04 before they leave everybody in the dark

this seems good for open source drivers since they are "helping" improve the drivers.  People expect the open source to have 3D support at or close to fglrx performance level by end of the summer.

---

### Post by Yuka on 2009-04-05
Ok, a little update.

I managed to install v9.1 without a problem and everything is working fine, even AIGLX (or Compiz, don't know, lol).

What i did different: cleared all packages from the repository (uninstalled everything fglrx related, except kernel-modules).

Hope it helps. I'll try to install 9.3 once more and see how it goes... Tomorrow xD

Esop!

PS: Follow this [guide]("http://wiki.cchtml.com/index.php/Ubuntu_Hardy_Installation_Guide"), step 2+3+4+5 and it *should* work.

---

### Post by locksley on 2009-04-06
Everything with the ubuntu drivers worked perfectly for me with 3300's and 4850's as as follows:

System: amd quad core, Asus M3a78-T MB with on-board ati 3300, two ATI 4850's.

Installation:

Ubuntu 9.04, full upgrade, enable propitiatory drivers, Custom built xorg.conf but that's only because of the number of cards and screens:

```

Section "ServerLayout"
        Identifier     "amdcccle Layout"
        Screen      0  "aticonfig-Screen[0]-0" 2874 0
        Screen         "aticonfig-Screen[2]-0" 933 0 
        Screen         "aticonfig-Screen[2]-1" 0 1080
        Screen         "amdcccle-Screen[3]-0" 1920 1080
        Screen         "amdcccle-Screen[3]-1" 3840 1080
EndSection

Section "Files"
EndSection

Section "Module"
        Load  "glx"
EndSection

Section "ServerFlags"
        Option      "Xinerama" "off"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[2]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[2]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "amdcccle-Monitor[3]-0"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[3]-1"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]-0"
        Driver      "fglrx"
        BusID       "PCI:1:5:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[2]-0"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[2]-1"
        Driver      "fglrx"
        BusID       "PCI:2:0:0"
        Screen      1
EndSection

Section "Device"
        Identifier  "amdcccle-Device[3]-0"
        Driver      "fglrx"
        BusID       "PCI:3:0:0"
EndSection

Section "Device"
        Identifier  "amdcccle-Device[3]-1"
        Driver      "fglrx"
        BusID       "PCI:3:0:0"
        Screen      1
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]-0"
        Device     "aticonfig-Device[0]-0"
        Monitor    "aticonfig-Monitor[0]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[2]-0"
        Device     "aticonfig-Device[2]-0"
        Monitor    "aticonfig-Monitor[2]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[2]-1"
        Device     "aticonfig-Device[2]-1"
        Monitor    "aticonfig-Monitor[2]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[3]-0"
        Device     "amdcccle-Device[3]-0"
        Monitor    "amdcccle-Monitor[3]-0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

Section "Screen"
        Identifier "amdcccle-Screen[3]-1"
        Device     "amdcccle-Device[3]-1"
        Monitor    "amdcccle-Monitor[3]-1"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24  
        EndSubSection
EndSection

```

The screens a stacked thats why the layout section is a bit wiered. I could not get Xinerama going at all.

My problem is I'm trying (with out much luck) to get them all going one big desktop. 

I'm trying to get ATI 9.3 going as we speak but as mentioned it does not work, however i have read threads that it appears people have got it going?

Good luck i hope this helps.
.

---

### Post by Jakey_TheSnake on 2009-04-09
Sorry to bump the old thread, but when upgrading I get this:

[img]http://img134.imageshack.us/img134/9947/fucka.png[/img]

---

### Post by sdowney717 on 2009-04-09
your video card is no longer supported by AMD fglrx driver.
This means ubunut will only be able to use its free ATI radeon driver which if you do any 3d stuff will make you feel like a 100 year old crossing a busy street.

I have read sometime late this year they hope to get good 3d performance in the free radeon driver.

---

### Post by mendieta on 2009-04-18
> **locksley said:**
> Everything with the ubuntu drivers worked perfectly for me with 3300's and 4850's as as follows:

System: amd quad core, Asus M3a78-T MB with on-board ati 3300, two ATI 4850's.

Installation:

Ubuntu 9.04, full upgrade, enable propitiatory drivers ...


Thanks, locksley. Is it still running fine with he latest updates for you? I am not sure I should try. I just upgraded from 8.10 with the proprietary driver activated, and was that **painful**. Half-hour rebooting to a crashed XServer, the "bullet-proof-x" vga graphics didn't kick in, so there was nothing to do. Dropping to a shell in the "repair" grub entry would ask for the root passwd (???). Until I could [alt-2] and login and open a shell before the X crash and kill gdm. 

I have a similar GPU (Onboard Radeon 3200).

I hope this gets fixed for final, I'll probably fill a bug report in launchpad (I am sure someone did, this is a biggie).

---

### Post by mendieta on 2009-04-19
arrgg, i installed the latest fglrx from ATI's site (the .run binary, without noticing that you could create deb's). The system won't load x. But now **I can't revert to the opensource driver. How do I do this?** Please!!

I also created debs later on and installed them, then removed them, i tried dpkg-reconfigure on the xorg package, and i tried rebooting in safe mode to repair x. Nothing worked!

Many thanks for any help, I am locked out of my machine right now!

---

### Post by mendieta on 2009-04-19
Ok. I fixed it, I followed the advice here:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

and in addition, I had to reinstall **xserver-xorg-core**

---

### Post by DougieFresh4U on 2009-04-19
Ok, after a serious 'bork' job last nite, I did fresh install and installed the .30rc2 kernel.
Machine is AMD Athlon 5200 x2 with onboard ATI Radeon HD 3200 for graphics.
From the 'borked' system, I do know that 'fglrx' does NOT work with the .30 kernel. Please, what drivers in Synaptic should be installed and can I get compiz or desktop effects to work?
Got the following from terminal:
```
dougie@DougiesLeanMachine:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon HD 3200 Graphics [1002:9610]
```
```
dougie@DougiesLeanMachine:~$ glxinfo |grep vendor
unknown chip id 0x9610, can't guess.
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: Mesa Project

```
```
dougie@DougiesLeanMachine:~$  glxinfo | grep "direct rendering"
unknown chip id 0x9610, can't guess.
direct rendering: Yes

```
Why am I getting this 'unknown chip' message?

---

### Post by mendieta on 2009-04-21
All, there is a related bug report in Launchpad, you may want to contribute to a fix by reporting/subscribing there:

[https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/363868](https://bugs.launchpad.net/ubuntu/+source/acpi/+bug/363868)

---

### Post by rukna on 2009-04-21
I have a similar issue where my Jaunty upgrade now does not support the ATI card on my Dell optiplex desktop. The dual-head setup was running perfectly in Intrepid. Makes me wonder if I upgraded a bit too early. I've tried installing the latest fglrx without any help. The only setup that works with the card is using SGI and the monitors cloned. Any help or pointers to get my dual-screen setup to work would be appreciated

```

#lspci | egrep -i vga
01:00.0 VGA compatible controller: ATI Technologies Inc RV380 [Radeon X600 (PCIE)]

#glxinfo | egrep vendor
server glx vendor string: SGI
client glx vendor string: SGI
OpenGL vendor string: DRI R300 Project

```

---

### Post by kekegg on 2009-04-21
> **nkteam said:**
> I'm having problems with opensource ATI drivers.
When I'm for example scrolling through FireFox, or any 2d operation, screen start to flicker (some fuzzy lines appears) inside vertical area (~2cm wide) on the right side of the screen. On the other side, I didn't have this problem with Ubuntu 8.10.

I want to install proprietary ATI driver, but cannot find instructions on how to uninstall this one and install fglrx driver, and wanted to ask for instructions before I start playing with that...

Instructions I found are targeted to older Ubuntu versions.
Anyone have some time to help?

Thanx!!!
I have exactly the same problem. So I can't use Gnome-do docky, which flickers more. How to solve it?

---

### Post by Yashiro on 2009-04-22
> Please, what drivers in Synaptic should be installed and can I get compiz or desktop effects to work?
With that kernel and your card, none at the moment.

---

