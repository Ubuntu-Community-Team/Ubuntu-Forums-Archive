---
title: "Screen does not show when trying to install from CD"
date: 2007-06-29
forum: Installation &amp; Upgrades
---

### Post by indigo0086 on 2007-06-29
I started up the Ubuntu 7.06 install from cd by booting from it.  After the initial choosing of whether to install, install in safe graphics mode (both of which I chose with the same result), the screen loads the bar, then it goes blank.  I have a "samsung Syncmaster 941bw" widescreen LCD monitor, and a radeon x1950 graphics card.  How am I supposed to install it if I can't see the screen, is there another way to do it, is the monitor even supported?

---

### Post by merlinus on 2007-06-29
You might try the Alternate Desktop install cd. It is text-based, but quite straightforward.

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tick the box below the green Start Download text, then click the text to begin.

-merlin

---

### Post by indigo0086 on 2007-06-29
Thanks.  Though when I actually install it will it do the same thing when I first boot it up?  I mean if it uses the same desktop then when I use it for the first time won't it go blank?

---

### Post by iamplasma on 2007-06-29
It doesn't use any desktop, it uses plain old text-only.

---

### Post by indigo0086 on 2007-06-29
But I want the ubuntu desktop.  Is there a way to fix it not showing up on my screen before it boots to the desktop?

---

### Post by haden9 on 2007-06-29
With the alternate installation cd, you will have the option to choose the lowest resolution possibly handled by your monitor, I think thats what your problem may be. I would suggest perhaps using 640x480 if the screen indeed goes blank it may mean that the native resolution your monitor uses is not handled by the vesa drivers which are installed as a default in Ubuntu. Try it out and please let us know what happens!

haden9

:popcorn:

---

### Post by footwo on 2007-06-29
I am having the exact same problem. I have an LG L226WTQ 22" Widescreen LCD Monitor. I boot from the disc and get to the menu, when I choose install it gives me a loading bar which fills up, then my monitor goes out of phase and turns off.

How can we tell the install program to use the lowest res?

---

### Post by indigo0086 on 2007-06-30
Okay I installed ubuntu fine, but still having the problem with the monitor.  I tried all sorts of things like modifying the xorg.conf file with my proper refresh rates with no luck.  I tried updating my ATI drivers but it just caused my xorg.conf to be corrupt and I had to modify the file to use the backup.  Nothing is working with my monitor.  The monitor is a SyncMaster 941bw and I use a resolution of 1440x900 @ 32 bit on windows, and i knew before I installed the drivers on windows that it acted up if I didn't have the proper refresh rate or resolution.  

I'm really having too much trouble with this, I'm putting ubuntu on the back burner for a while.

---

### Post by haden9 on 2007-07-03
Could you post your fglrxinfo log,

Just want to make sure if it is recognizing the video card properly.

And to answer a question above too, try

sudo dpkg-reconfigure xserver-xorg

---

### Post by Jacemg on 2007-07-03
> **indigo0086 said:**
> Okay I installed ubuntu fine, but still having the problem with the monitor.  I tried all sorts of things like modifying the xorg.conf file with my proper refresh rates with no luck.  I tried updating my ATI drivers but it just caused my xorg.conf to be corrupt and I had to modify the file to use the backup.  Nothing is working with my monitor.  The monitor is a SyncMaster 941bw and I use a resolution of 1440x900 @ 32 bit on windows, and i knew before I installed the drivers on windows that it acted up if I didn't have the proper refresh rate or resolution.  

I'm really having too much trouble with this, I'm putting ubuntu on the back burner for a while.

seems like ATI is having trouble making their drivers open source.. maybe you should complain to them for a change ;)

nvidia ftw

---

### Post by indigo0086 on 2007-07-05
> **haden9 said:**
> Could you post your fglrxinfo log,

Just want to make sure if it is recognizing the video card properly.

And to answer a question above too, try

sudo dpkg-reconfigure xserver-xorg

I did that and it rendered my monitor useless when I started up, I had to log in to the shell and copy a backup I made before hand (thank god I'm taking a Unix programming course)

---

