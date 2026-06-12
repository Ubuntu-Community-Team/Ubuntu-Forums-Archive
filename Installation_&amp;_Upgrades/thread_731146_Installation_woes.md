---
title: "Installation woes"
date: 2008-03-21
forum: Installation &amp; Upgrades
---

### Post by jakerockcity on 2008-03-21
Good day,

I have just installed Ubuntu 7.10.  I reformatted and partitioned because I am done with XP.  The live cd work very well.  After I installed, I restarted and it acted as if it were loading and now I just see a blank screen (kinda pinkish) with my mouse cursor in the center.  The cpu acts like it is processing something but nothing happens.  Any suggestions?

Thanks

Jake

---

### Post by Pumalite on 2008-03-21
Post your specs. Burn a new CD at 4x after doing md5sum. I'd recommend downloading a new iso of the Alternate CD:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Mark the box below the sign 'Start Download'

---

### Post by dstew on 2008-03-21
You probably need to reconfigure the xserver, the software that creates the graphical user interface. When you get to the blank screen, hit ctrl-alt-F1. That should get you a command line. On the command line, enter```
sudo dpkg-reconfigure xserver-xorg
```That gets you a text-based installer that leads you through the reconfiguration process. When you get to the part about the display, choose the **vesa** driver. When you have finished reconfiguring, press ctrl-alt-backspace to restart the display. Or, you can restart.

You should get a usable desktop. Once you can go into the desktop, go to System --> Administration --> Restricted Drivers Manager. See if there is a display driver for your video card, and install it.

---

### Post by jakerockcity on 2008-03-22
Hi

Thanks for the prompt responses, everyone.  I just came home from work and restarted and it now let me log in and I am looking at the desktop.  I'm not sure if the problem is forever solved.  I've got a Dell Inspiron 5150 with a pentium 3.0ghz, 2gb ram and an ati graphics card with 256mb.  md5sum check out ok.

Jake

---

### Post by jakerockcity on 2008-03-22
Ok, I spoke too soon.  I am looking at the desktop but I cannot click on anything and the computer seems to be running pretty hard but it is not responding to my commands.  Crazy.  :)

---

### Post by jakerockcity on 2008-03-22
Ok,

I reconfigure the xserver display thing and now it is kinda working.  it says there are 202 available updates to install; do I need to install all of them?

jake

---

### Post by jakerockcity on 2008-03-22
Hello,

Everything seems to be working fine!  Is there anyway to connect to a Win XP pc on my network?  It is plugged into the same router as my pc with ubuntu.  Thanks for all the help.

Jake

---

### Post by Pumalite on 2008-03-22
Install samba

---

### Post by black3ug on 2008-03-22
If you want to access a shared folder, then:

1. go to *Places > Connect to Server*
2. select *Windows Share* for the *Service Type*
3. click the *Connect* button
4. wait for it to load.

If you want to "Remote Desktop" your XP machine, then:

1. go to *Applications > Internet > Terminal Serverl Client*
2. provide the necessary data (computer name, user name, password ...)
3. click *Connect*. 
4. wait for the remote desktop to load

---

### Post by jakerockcity on 2008-03-22
That worked fine!  Everything seems to be running smoothly except my video driver.  I check ed for restricted drivers, as I was told, but there are none for the video just something to do with a modem.  I am an ATI mobility radeon 9000 series and I have read that this is not supported well by ubuntu.  what are my options?  thanks

jake

---

### Post by jakerockcity on 2008-03-22
Extra info:

Google earth tells me that my system is running in graphic emulation because it does not detect a video card

Hmm...

---

### Post by dstew on 2008-03-22
I think the Ubuntu ati driver should work with that card. You can do sudo dpkg-reconfigure xserver-xorg again, but instead of the vesa drive, choose the ati driver. See if that helps.

---

### Post by jakerockcity on 2008-03-23
Hi,

I tried selecting ati but it only made it worse :)  I went back to vesa and I think that should work for want I need it for.  thanks so much for the help.


jake

---

### Post by jakerockcity on 2008-03-23
Hi,


Ok, I give up.  This is just too unstable and I have spent 5 days trying to get it to work properly.  Do you think that future versions might work better on my pc?

Thanks

Jake

---

### Post by dstew on 2008-03-23
It depends on the manufacturer of your video display adapter. If they only want to provide drivers for Windows systems, we will continue to have problems. The best thing to do is to complain to the video card maker and ask them to create a restricted driver for LInux, or to go the whole way and cooperate with the Linux developers and create an open source driver.

---

### Post by Pumalite on 2008-03-23
+1

---

