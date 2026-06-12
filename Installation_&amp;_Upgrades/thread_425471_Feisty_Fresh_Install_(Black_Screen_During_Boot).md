---
title: "Feisty Fresh Install (Black Screen During Boot)"
date: 2007-04-27
forum: Installation &amp; Upgrades
---

### Post by michwill on 2007-04-27
Hi All,

I'm having some severe trouble with my Ubuntu 7.04 install.  The system specs are as follows:


-Chaintech 7NJL6 Socket A

-2.15 GHz Athlon XP 3000+

-160GB Maxtor HD

-Chaintech XGI Volari V3 / 128MB DDR / AGP 8X / VGA / DVI / TV Out / Video Card

-512MB PC3200




I've tried every single option (Desktop/Alt/Server. . .factory discs where available) from 6.06 to 7.04 all to no avail.  Basically the CD loads, gets to the "Start and/or Install screen".  I select it and the screen goes, and remains, black.  Oddly enough there seems to be a signal to the monitor because the light stays green and there is no "NO SIGNAL" warning.  I've tried two different monitors.

Any ideas as to what in the world could be going on?  It is of note that the following OSes are viewable and will install fine:


Windows XP
SuSE 10
Knoppix 5.0.1

---

### Post by dannyboy79 on 2007-04-27
this is an easy as I went thru this already. follow only the part about adding break=bottom to your boot line and then update xorg.conf file by chrooting into it, then save the xorg.conf, than when you're back at the busybox prompt, hit control d and it should continue. it has to do witht the installer chosing the wrong graphics driver, so if you chose the basic one, vesa, then you'll be able to do the install.

1) In the boot option on Live CD boot screen (F6), at the end of the line remove splash as well as quite AND at the end add:
break=bottom

**This gives you a command prompt before you boot**

2) after editing the boot line following the onscreen instructions and adding break=bottom, you should be able to boot that boot line by hitting B and wait for the (initramfs) prmpt. At the prompt do:
mv /root/etc/X11/xorg.conf /root/etc/X11/xorg.conf.disabled

**Moving the xorg configuration file forces boot in vesa mode, which works with an ATI Card, should work for any card as vesa is capable of running almost any graphics card**

3) At the prompt do:
exit OR control d

**This allows the LiveCD to boot**

OK, now you can see SOMETHING. If you try to install ubuntu, it fails. You moved xorg.conf, remember? Move it back.

4) At a command prompt, enter
sudo mv /root/etc/X11/xorg.conf.disabled /root/etc/X11/xorg.conf

5) Install Ubuntu like you would normally.

6) Reboot

7) X fails to start again.... Hit Ctrl + Alt + F1 and login. Now install the ati drivers OR change it to vesa again to at least be able to see stuff and then come here if you want help with graphics acceleration:
sudo apt-get-install xorg-driver-fglrx fglrx-control
sudo aticonfig --initial

---

### Post by michwill on 2007-04-27
Actually, I swapped out the video card from another machine and got it installed.  Now, of course, with the old card back in, X won't start.  I tried your last two lines but that didn't seem to fix anything.  Is there perhaps another item I should install?

Thx for your post btw.

---

### Post by dannyboy79 on 2007-04-30
> **michwill said:**
> Actually, I swapped out the video card from another machine and got it installed.  Now, of course, with the old card back in, X won't start.  I tried your last two lines but that didn't seem to fix anything.  Is there perhaps another item I should install?

Thx for your post btw.


what video card are you trying to get x to work with? did you try 

sudo dpkg-reconfigure xserver-xorg

you should be able to get into your box without x, then run that at the command line which should do it. this is of course AFTER you install the proper drivers for your card.

---

### Post by michwill on 2007-05-02
System info in original post.  It appears that it's neither ATI nor NVIDIA.  I've tried VGA, VESA, and TRIDENT all to no avail.  It seems like this card is super finicky.  The only way I could get it to even install was to put an NVIDIA card in it, load Ubuntu, then put the Volari back in and have X crash out and send me to terminal.  Beginning with the Volari doesn't seem to be an option.  As for the proper Linux drivers for the Volari, I haven't found those yet.  Although there are a few posts, it seems a pretty obscure card in the Linux realm.  Any ideas?  Thanks.

---

### Post by dannyboy79 on 2007-05-02
well let me see the output from 

lspci -v 

of course when the Volari  card is inserted in the motherboard, you can always boot into text mode and perform this command. i would like to see what chipset is on the card.

found the open source code for the V3XE, it might work. DOwnload it from here: [http://www.xgitech.com/sd/sd_opensource.asp](http://www.xgitech.com/sd/sd_opensource.asp)
and then compile it and use it per the readme instructions. good luck

but here's some bad news but it's an older article so still give it a try.

[B]further investigation results in horrible news, according to this: http://www.xgitech.com/about/about_press1.asp?CTID={C3FD7D03-6BE1-4BB9-9F34-1221E723B87F}
they only support Xorg up to 6.8.X and Edgy uses 7.1 and Feisty uses 7.2. [/B]

**I would have to tell you, sorry it's just not going to work for ya.**

---

### Post by blazercist on 2007-05-02
delete "quiet splash" from the boot line.

---

### Post by dannyboy79 on 2007-05-02
that will merely remove the splash screen from appearing and will also show him the boot process. That will in no way solve is lack of a supporting driver for his graphics card.

---

### Post by blazercist on 2007-05-02
are we 100% sure that its the driver for his card thats causing the problem?  Do we know the last stage in the boot process before his screen blanks out?  this will help us understand the cause of the problem... AFAIK the system will boot with the vesa driver unless the specific driver has been installed or enabled via the restricted drivers manager.  vesa should work on 99% of video cards.  usplash has been known to cause a similar behavior.  I'm just trying to be helpful don't knock me.

---

### Post by michwill on 2007-05-03
Well, I can't give you an "lspci -v" from Ubuntu because I wiped it and installed Knoppix.  Knoppix works well, and chose to use the Volari XP5 driver (despite the fact that the card is a V3).  I'm not sure which version of Xorg Knoppix currently uses.  Just FYI, it's my bro's computer, so I'll have to wait 'til tomorrow to try more fixes.  Let me know if you think of anything else.

Thanks again.

---

