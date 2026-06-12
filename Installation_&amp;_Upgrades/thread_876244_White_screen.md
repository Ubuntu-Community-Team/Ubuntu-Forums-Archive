---
title: "White screen"
date: 2008-07-31
forum: Installation &amp; Upgrades
---

### Post by chejose on 2008-07-31
I recently bought a HP 2133 (a lovely little machine) and have installed 8.04 on it. I read that to avoid video problems you should put "xforcevesa" into the command line on installation. I did it, but must have done it wrong since when the installation was complete, I had a white/yellow screen.

I tried putting the same into the command line on booting up, but it did not work. Maybe I put it into the wrong place, since there are more than one line that can be edited.

Anyway, there must be a "trick" to make Ubuntu load up correctly, and so I put the problem to you.

Many thanks,

José

---

### Post by dileepm on 2008-08-01
Where does the white screen appear at the time of booting or after logging...

---

### Post by chejose on 2008-08-01
Thanks for getting back.

It appears early in the boot process. 

The first Ubuntu icon with the progress bar shows up. At almost the end of the process the bar changes from orange to white, and when the next stage shows up the screen slowly turns grey/yellow.

I could tell when it reached the user name/password stage (it stopped processing), which I entered. It then apparently finished the process of loading Ubuntu. At that stage I simply turned the machine off since I could read nothing.

José

---

### Post by jtappin on 2008-08-01
The xforcevesa line in the install boot allows the graphical installer to be used (otherwise you just get a black (IIRC) screen at that stage).

The xforcevesa line is automatically added to /boot/grub/menu.lst by the installer, and can be removed if you install one of the other drivers or specify a driver in xorg.conf. 

There are however some infelicities in each possible video driver option:

VIA binaries (stable): Work, but 3-D acceleration is only possible with the 2.6.24-16 kernel not with the current Hardy versions. As far as I am aware this is the only option to get 3-D acceleration.

VIA binaries (beta): At least for me did not work -- just cycled through a series of coloured screens.

vesa: Works but I was only able to get 1280x720 resolution not 1280x768.

openchrome (hardy package): Doesn't recognise the chipset.

openchrome (svn): Works but frequently gives a whitish screen on shutdow and inhibits powerdown. No 3-D acceleration.

For what it's worth I'm currently using VIA with the -19 kernel.

---

### Post by chejose on 2008-08-02
Was gone a day and am finally getting back to the problem.

Thanks for your answer, but I am afraid that it doesn't help... two reasons:

First, it still does not help me to get a screen I can see on my installation. Anything has to be done when I boot, since very quickly I can see nothing.

And second, I am afraid that my expertise in Ubuntu is not high enough to be able to apply things without fairly detailed descriptions. 

So again, I hope someone can get me out of this hole.

José

---

### Post by SamTzu on 2008-08-02
Try reconfiguring your /etc/X11/xorg.conf file.

If you search the forum for that "xorg.conf" keyword you will find some examples how it can be done.

---

### Post by chejose on 2008-08-02
Well... thanks. But how can you edit a file if you just have a blank screen? I can tell that the program is loading OK (asks for name, key) and then the tune that says it is loading, but since the screen is just a grey blank, there is no way for me to do anything.

I need to somehow tell it what to do at the first boot options page.

So I keep trying... and hoping.

José

---

### Post by SamTzu on 2008-08-03
There are several different ways but they are all more than little technical. Easiest is to boot the PC with a LIVECD like PCLinuxOS2007 and then configure the xorg.conf file.

---

### Post by chejose on 2008-08-04
Hmmm.... this gets to be frustrating. I downloaded the pclinux file and ran it. It runs with no problems, but does not recognize the hard disk of the computer. It does not show up as part of the "hardware" listing, and if I try to do the install (better than fighting with Ubuntu all the time) it says there is no HD.

So I am still out on a limb with no luck so far in the different things  have tried.

Thanks for the answers,

José

---

### Post by jtappin on 2008-08-11
> **jtappin said:**
> 
VIA binaries (stable): Work, but 3-D acceleration is only possible with the 2.6.24-16 kernel not with the current Hardy versions. As far as I am aware this is the only option to get 3-D acceleration.


It turns out that it is possible to get 3-D acceleration with the 2.6.24-19 kernel if you download the module source patches (available from the RH column of the VIA download page) and follow the instructions included with them.

---

