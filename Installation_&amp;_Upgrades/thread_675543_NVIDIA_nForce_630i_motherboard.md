---
title: "NVIDIA nForce 630i motherboard"
date: 2008-01-22
forum: Installation &amp; Upgrades
---

### Post by bert_pereira on 2008-01-22
I recently purchased an XFX nForce 630i with Integrated GeForce 7100 Graphics board [http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?series=XFX+nForce+630i&productConfigurationId=1698931](http://www.xfxforce.com/web/product/listConfigurationDetails.jspa?series=XFX+nForce+630i&productConfigurationId=1698931) Ubuntu doesn't seem to detect the graphics and i just get a blank screen after some time - Does anyone have an idea of a workaround for this

Thanks in advance

Regards, 

Bert

---

### Post by Cal55 on 2008-01-23
Hi,

First caveat, I'm a linux and ubuntu newbie.  

However, I have an MSI P6NGM motherboard with what I believe is and nForce 630i chipset (the  MSI manual suggests GeForce MCP730U/PV/V).

I had problems getting anywhere with an install of ubuntu Gutsy 7.10.  It kept hanging with a message of '...local boot scripts'.  Alt + F2 gave a console (of sorts)

The first thing that helped was the ** 'Alternative Install CD'** which gives a 'text mode' install.  It doesn't look too great, but it did get me up and running.

This gave me a full install, but no GUI.

I have a PCI-E nVidia 8600GT graphics card, so I had to switch off the onboard graphics chip in the BIOS before the card worked.  I had to then do a

```
sudo dpkg-reconfigure -phigh xserver-xorg
```
to rebuild the xorg.conf.

This might help?

BUT. I'm having other problems with the chipset I think.  I can't get the onboard sound working for example. Thus, I'm thinking the chipset isn't supported, and am trying to get more info.

Hope this helps a bit.  Let me know if you need more info.

You might also like to look at this : [http://www.phoronix.com/forums/showthread.php?t=6524](http://www.phoronix.com/forums/showthread.php?t=6524)

Cheers
Chris

---

### Post by opportunity on 2008-02-22
on the boot loader from the cd there is an option to do a safe mode install. That will get you off the ground and get you at minimum a sluggish gui to work in.

---

### Post by kaivalagi on 2008-02-24
As 'opportunity' suggests use the safemode option. I have a 630i/7100 mobo (gigabyte ga-73pvm-s2h) and when installing mythbuntu 7.10 (xfce based ubuntu with mythtv) I had to do to do the same. Once in, I then installed envy and got the latest nvidia drivers installed (169.x). My graphics are fine now.

I now have issues with the audio chipset ](*,)

New mobo, new chipsets, new headaches...let's hope all these issues get resolved soon in a new ubuntu release (8.04 maybe)

Come back onto this thread with any other issues and we can try and work through them, the more the merrier!

---

### Post by kaivalagi on 2008-02-24
To get the 630i based onboard sound working head over to the realtek website ([www.realtek.com.tw](www.realtek.com.tw)) and download the latest linux 2.4/2.6 HD audio codec drivers.

The automatic install works,and updates all the relevant alsa drivers/libs/utils with alsa 0.15.

Some decent drivers from a manufacturer for a change :)

---

### Post by abhisheknegi on 2008-03-08
Yeah same problem with my Palit mobo too....same configuration....it seems gutsy doesnt want to detect it at all :(

---

### Post by kaivalagi on 2008-03-20
Yes, see my previous post.

Head over to the realtek website and download the linux HD audio codec drivers (the link is on the main page).

Once you get them, extract and run the install script as root i.e. sudo ./install

Any issues just post here

---

### Post by steinair on 2008-03-27
Hmm... as well as U guys..

I have also the P6NGM MSI board and can't get the sound working, 
When I try to install it tells me 
checking for initscr in -lncurses... no
checking for initscr in -lcurses... no
configure: error: this packages requires a curses library
make: *** No targets specified and no makefile found.  Stop.
make: *** No rule to make target `install'.  Stop.
Remove Folder.....
./install: 101: alsaconf: not found

But I already have the 
libncurses5   libncursesw5 

Why is that? 

By the way I still couldn't find a driver for my video card Nvidia Geforce MCP73
:confused:

---

### Post by kaivalagi on 2008-03-27
Try installing the libncurses5-dev package, I think it needs the development libraries rather than the binaries...Also, make sure you have the build-essential package installed...both apt-get install commands below:

```
sudo apt-get install build-essential
sudo apt-get install libncurses5-dev
```

I hope that sorts it for you, if not post back and we can go from there.

Cheers

---

