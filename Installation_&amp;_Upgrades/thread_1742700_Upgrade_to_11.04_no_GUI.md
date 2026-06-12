---
title: "Upgrade to 11.04 no GUI"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by judiM on 2011-04-29
Hi

Ubuntu 11.04
Nvidi GeForce graphics card

I've just upgraded from 10.10 to 11.04 and now I have go GUI just the command line login. Sorry - I'm not used to working with the command line at all but here's what I've tried after a bit of research:

startx (doesn't work)
sudi apt-get install nvidia-current (already have latest version)

Then I tried to install Gnome again as seemed it may be a problem with Unity? the install seemed to work but still same problem so not sure if there is something else I need to do?

Anyway, tried all same things again, startx produces a whole page of error messages including:

FATAL: Module nvidia not found

Fatal Server Error
no screens found

xinit: giving up
xinit: unable to connect to xserver: connection refused
xinit: server error

I can type it all in if it would help.  I really don't want to have to do a clean install this time as have got it set up nicely (luckily remembered to backup files).

Thanks

J

---

### Post by dino99 on 2011-04-29
might be due to xorg.conf, you can remove it (kernel now directly deal with X)

sudo rm /etc/X11/xorg.conf

then rebbot

---

### Post by marek_online on 2011-04-29
I had similar problems.

Firstly, check what type of card you have and the natty release notes (there's a particular problem with the nVidia 8600 GTS).

If your card should work, then try installing the linux-headers appropriate to your kernel, which is what fixed it for me. (I also removed every package related to nvidia except the basic xorg ones and re-installed just nvidia-current and its dependencies, for good measure.)

---

### Post by mermshaus on 2011-04-29
Removing the xorg.conf file worked for my GeForce 8200 (on Kubuntu 11.04). Thanks!

---

### Post by judiM on 2011-04-29
My graphics card is 9000-series, I tried installing linux headers etc but unfort that didn't work for me, removing xorg.conf did work though - brilliant!

Thanks to both of you for your replies

J

---

### Post by andy_blah on 2011-04-29
I have the same problem, the only difference is that instead of using the NVidia drivers that came with Ubuntu (which don't work as always ~.~ ), I switched from the official one from NVidia, seems that the install ran through a few minor problems (can't recall, sorry). I tried to restart xorg by the above mentioned command, and tried to delete it's configuration file, but still it refuses to work. Xorg outputs an error with not having any screens, so I suppose the driver didn't install properly. Is there anything I could do?

---

### Post by kukker32 on 2011-04-29
also did you try this ..... if you are going to wipe your system it may be worth trying it first.

sudo apt-get install nvidia-xconfig (if its not already installed)
[COLOR=Red][B]nvidia-xconfig
[/B] [/COLOR]to create a xorg.conf file ....... 

(you still have a few options if you want to try to solve it - did you back everything up ?)

The way it usually works is there is a driver that should exist on the system for your graphics card
this driver is then picked up from the header files for the kernel
the kernel gets compiled to include it .......

as long as you have the correct drivers installed for the graphics card ..... and the kernel has picked them up ok
then the xorg.conf can set the display  to be used 

There is a way to 'swap' and boot into [COLOR=Red]**kdm**[/COLOR] to boot up to the desktop ........ 

[COLOR=Red]**sudo apt-get install kdm**[/COLOR]

you still can run ubuntu and even swap back ..... to [COLOR=Red]gdm [/COLOR]later if it should solve a problem .....

maybe someone else has some more useful info .....

---

### Post by buri on 2011-04-29
After I upgraded to Ubuntu 11.04 I ended up without the graphical login. gdm failed to start and X could not be started as well (module not found).

When running an 'sudo aptitude upgrade' DKMS tried to compile the nvidia-current and failed with an error and a look at the file /var/lib/dkms/nvidia-current/build/make.log revield:
"gcc unable to create executables' 

Trying to compile anything else led to the same result when running the configure. 

To make a long story short: libmpfr.so.SOMETHING was missing and I was able to fix it by installing that lib:

sudo apt-get install libmpfr1ldbl

Hope this is helpful to someone.

---

### Post by andy_blah on 2011-04-29
> **kukker32 said:**
> sudo apt-get install nvidia-xconfig (if its not already installed)

I can't really do that since the connection wasn't working after I finished updating (for what reason... I don't know, it had the same settings as the previous installation and it worked).
So in that case, what should I do?

---

### Post by andy_blah on 2011-05-02
Anyone? ~.~

---

### Post by andy_blah on 2011-05-03
So, nobody's answering, surprise, surprise. Well I've finally succeeded in making the connection work, just that there's no package "nvidia-xconfig".
Anyone else know what to do?
Here's what I have gathered from the error message:
```
(EE)Screens found, but none have an usable configuration
Fatal Server error
no screens found
```

I also tried to run the NVidia installer again to see what it reported last time, the thing it says is that it can't remove the distro driver for the video card, so I suppose that might have an influence on it.

---

### Post by mamahopsk87 on 2011-05-07
[B]> **dino99 said:**
> might be due to xorg.conf, you can remove it (kernel now directly deal with X)

sudo rm /etc/X11/xorg.conf

then rebbot[/B]

hey, it works for me. I'm using hp pavilion tx 1000 with nvidia graphics. After upgrading from 10.10 to 11.04 the GUI missing. I follow these steps and it just work. Thank you very much! now it works but with the traditional gnome 2 not unity......

---

### Post by andy_blah on 2011-05-07
Nevermind, I investigated further, and when tried to make X reconfigure itself, it gave me this:

"This server hs a video driver ABI version of 10.0 that is not supported by this NVidia Driver. Please check for driver updates or downgrade to an X server wth a supported driver ABI."

So I just did what it said, and surprisingly, even for such an old card as mine they updated the driver to be more compatible with that ABI version, and with the newer kernel versions. Forgot I had the intention of posting in this thread again, but wanted to do so for those who wait 3-4 days for an answer on those forums ~.~
So in the end, Nvidia gets from me two points for updating the driver, and the Ubuntu forums get zero.

---

