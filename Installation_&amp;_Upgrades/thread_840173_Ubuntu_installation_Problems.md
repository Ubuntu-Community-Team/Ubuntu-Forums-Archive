---
title: "Ubuntu installation Problems"
date: 2008-06-25
forum: Installation &amp; Upgrades
---

### Post by nparayo on 2008-06-25
Hi im new to linux and i want to try it out but my computer refuses to load it. 

Some info first just from dxdiag

Fujitsu Siemens S6010 
Pentium 3 CPU - M 
1000MHz
502MB RAM

Intel 82830M Graphics Controller
Total memory: 48MB

BIOS: PhoenixBIOS 4.0 Release 6.0

I downloaded the iso, and i booted into windows and ran the CD and went for the second option to install linux within windows i though i would just have a linux shortcut and i would just run it but turns out it create kinda like a second partition and there is a selection between windows and linux on boot so i select linux and i get errors:

screenshot:
[[IMG]http://img168.imageshack.us/img168/5356/25062008102ll2.th.jpg[/IMG]](http://img168.imageshack.us/my.php?image=25062008102ll2.jpg)

The second option i tried was booting straight from CD so i press F12 on start up choose CD and it gives several options i tried the first one "Try Ubuntu without any changes to your computer"
and the display just crashes and turns white eventually, screenshot:
[[IMG]http://img522.imageshack.us/img522/6812/25062008103rn5.th.jpg[/IMG]](http://img522.imageshack.us/my.php?image=25062008103rn5.jpg)

So then i tried the second option when booting the CD "Install Ubuntu" and i get this screen displayed durin install, screenshot:
[[IMG]http://img262.imageshack.us/img262/1715/25062008104ya3.th.jpg[/IMG]](http://img262.imageshack.us/my.php?image=25062008104ya3.jpg)

What are my options any help appreciated.

---

### Post by Pumalite on 2008-06-25
Use the Alternate CD to install. Do md5sum, burn at 4x or lees, as an 'image' and not as 'data'.
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by nparayo on 2008-06-25
Hi thanks for the reply

the MD5 check was fine, i burnt alternative at 4x as iso as before, it installed fine and things were looking good, no probs during install, i restarted the laptop as the process and it just did the same as screenshot 2 where the dsiplay seems to crash, any solution or does my Ubuntu experience stop here lol.

---

### Post by Pumalite on 2008-06-25
Do you get to see a Grub menu?

---

### Post by nparayo on 2008-06-25
yes i can access grub menu with ESC
grub menu with 3 options

Ubuntu 8.04, kernel 2.6.24-16-generic
Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
Ubuntu 8.04, memtest 86+

ive tried recovery and typing sudo dpkg-reconfigure xserver-xorg but this just bring up keyboard options

ive tried

nano xorg

it brings up this text editor and i have no idea how to edit the driver to choose vesa

---

### Post by nparayo on 2008-06-25
one more thing thing ive managed to get it to shortly display the message  by runnung recovery and go to reset xserver settings i think,
"your monitor display settings could not be found" and also soemthing about choosing them manually but this screen immediately starts to fade like screenshot 2 into a blank screen.

---

### Post by Pumalite on 2008-06-25
Maybe all you need is to install a video driver. To configure your display:
gksudo displayconfig-gtk
I'm not sure you can run it in Recovery Mode. Try it.

---

### Post by avtolle on 2008-06-25
And, if you can't run it (Pumalite's suggested command) from Recovery Mode, have you tried to boot into safe-graphics mode? I believe it is an option under F6.

---

### Post by nparayo on 2008-06-26
Hi thanks for the replies. i tried

gksudo displayconfig-gtk

but it gives this:

(gksudo:4499): Gtk-WARNING **:cannot open display:

Also about F6 when can i press this i even pressed it all throughout the boot sequence but it did not alter??

I am using 8.04 the newest release and the help documentation seems to dffer slightly F6 has been mentioned before but i  cant get to this, 

thanks

---

### Post by nparayo on 2008-06-26
I found this other thread but being new how to i perform this

> I am using the newest ubuntu, on 7.10 i was able to use dpkg-reconfigure xserver-xorg in recovery mode to manually select vesa, I tried dpkg-reconfigure xserver-xorg in the newest ubuntu and all i can reconfigure is the kboard stuff, how would i go about reconfiguring w/e to use vesa driver instead of vga?

thanx.

EDIT: i nano xorg at recovery and just manually typed in

Driver "vesa"

into the video part, it works now, in xorg by default, xorg or w/e does not pick anything up by itself by default? not my regular wheel mouse, Not even my monitor, meaning i gotta edit everything by hand in xorg? "don't answer that question, no need to" for the help of this problem, i got none but thats ok, thanx for the support :/.

although i am using 8.04 when i type in nano xorg i get this text editor but no idea how to do what the post says?

---

### Post by Pumalite on 2008-06-26
Make sure every instance of 'driver' is 'vesa'
Ctrl+o + 'Enter'to save
Ctrl+x to exit having saved your changes

---

### Post by nparayo on 2008-06-26
This is the image i get when i type in 

nano xorg

[[IMG]http://img291.imageshack.us/img291/3950/26062008106sq4.th.jpg[/IMG]](http://img291.imageshack.us/my.php?image=26062008106sq4.jpg)


there is no text its blank, so there isnt anything for me to edit?

also when can i press F6 to enter safe graphics mode?

---

### Post by Pumalite on 2008-06-26
nano /etc/X11/xorg.conf

---

### Post by nparayo on 2008-06-26
hi thanks i started a new thread but ill post it again here

hi thanks i tried adding Driver "vesa" i wasnt sure where so i put it were i though necesary and it still does not work should i even replace ALL Driver instances with vesa including keyboard?
e including:

Driver "kdb"
Driver "mouse"
Driver "synaptics"

i would just try but im afraid it might make the devices useless, then i wouldnt be able to use the keyboard?

heres what i did do:
[[IMG]http://img241.imageshack.us/img241/6724/26062008107ni9.th.jpg[/IMG]](http://img241.imageshack.us/my.php?image=26062008107ni9.jpg)

or any other solution?

---

### Post by Pumalite on 2008-06-26
[http://ubuntuforums.org/showthread.php?t=841693](http://ubuntuforums.org/showthread.php?t=841693)

---

