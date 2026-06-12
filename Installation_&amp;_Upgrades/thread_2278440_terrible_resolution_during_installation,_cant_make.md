---
title: "terrible resolution during installation, cant make out screen well enough to change"
date: 2015-05-16
forum: Installation &amp; Upgrades
---

### Post by Kelly_Goose on 2015-05-16
Hello,

I'm trying to install 14.04 from a usb boot stick onto a separate hard drive from the one I boot windows from.  I can get to the install screen, or even run Ubuntu without installing, but when it comes up the resolution is beyond bad and I cannot make out any icons or text to navigate and change it.  My display is an ASUS VG248QE  1920x1080, graphics card is an MSI GeForce GTX 750ti and I'm using a dual link DVI cable to connect.  

I read through the graphics resolution sticky thread, but I can't find a way to troubleshoot because it's not installed yet and I can't make out anything on the screen.

Thanks for any help.

---

### Post by v3.xx on 2015-05-16
What about going to low res mode during grub boot? May be called recovery mode on yours.  That would be good enough to install a driver.

I run a older model, but did get a lot of forum hits on your geforce.

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GeForce+GTX+750ti&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=GeForce+GTX+750ti&sa=Search&cof=FORID:9)

---

### Post by Kelly_Goose on 2015-05-16
Thanks.  

Did not even think about the drivers..  I will sift through the search results and see if I can't figure this out.  I'm brand new to Linux if you couldn't tell.

---

### Post by v3.xx on 2015-05-16
Sounds like a plan.  Go ahead and research it and come on back with any questions.

---

### Post by Kelly_Goose on 2015-05-16
Ok, so I went to Nvidia and got the driver I needed, it is a .run file.  I managed to put it somewhere I could find it easily.  In ubuntu, I double click the file and it opens in gedit, i think.   Can't read anything thats going on but there is a progress bar moving across the top very slowly...    

Playing around with it now while, when i make a window go full screen, the resolution while it's increasing size, looks fine, but only for that split second while the window is changing size.  

I don't have any options in the gnu grub besides install, try without installing, and check disk.   I can type help and get a list of commands but none of them look like a safe mode or recovery mode type option.   I'm assuming this is because ubuntu is not yet installed, which I can't do because I can't see what I'm doing.  
So I'm trying to figure out how to fix this while it's just running off the USB drive so I can see what I'm doing to install it.

I can open a terminal but can't read the text, i suppose I could type some commands in carefully if there was some way to help from that approach.....

Also, I can open up the display settings, it shows built in display, and I can't make out the numbers but I think it is actually set to 1920x1080, can't tell for sure though.

UPDATE: Connected my display via HDMI cord, and now the screen is legible, but max resolution it offers is 1024 x 768.  Also I'd prefer to use the dual link DVI cable for this monitor and use HDMI for my other display.....   I will keep on fighting this.

---

### Post by ajgreeny on 2015-05-16
It is probably best not to download a driver from nvidia direct but to use the Additional Drivers utility, from the dash.  Try the one marked as recommended first.

---

### Post by Kelly_Goose on 2015-05-16
Ok so I installed ubuntu to the hard drive, got all the software updates, then went on to tackle the nvidia drivers.  First I downloaded from site and got the .run file.  Failed to get that to execute.   Tried to use the Additional Drivers utility but it wouldn't find any more drivers.  So I set up the xorg-edgers ppa and got the drivers installed.  Reset, and bam, beautiful 1080 resolution and my dual link dvi cable works again!!!!  And now to set up multiple displays,,,,,   

Thanks for the replies and interest..

---

