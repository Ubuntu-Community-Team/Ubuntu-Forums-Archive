---
title: "xubuntu on thinkpad 240"
date: 2007-11-26
forum: Installation &amp; Upgrades
---

### Post by russj1975 on 2007-11-26
Hi people

I'm new to this forum (and to linux)

I've installed ubuntu onto a laptop and really enjoy the system, but now i want to get xubuntu onto an IBM Thinkpad 240.  My problem is the machine doesnt boot from cd and i have no floppy drive.

I've had a look on the net and havent yet found and answer.

I have tried creating a hard disc with two partitions, one containg the contents of the live cd in the hope that it would boot from this and i would be able to intall to the other partition, but i just get error 15 or 17 messages.

Is there a simple way to get xubuntu onto this machine?

many thanks

---

### Post by russj1975 on 2007-11-26
Ok

i found this [http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html]("http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html")

i've tried bulding a grub using the live cd, but it will not work, i have tried supergrub cd, but it will not install grub just error 17.  this is all very frustrating.  in theory its oh so simple.  Install grub and place the alternative iso into the /boot folder on the second partition, along with a few other files, and edit the menu.lst file, and it should work according to the article, but in reality it appears that is anything but the case.

how on earth does one install grub with out resort to banging ones head against a brick wall??

its a whole loit easier to just buy a laptop with a cd rom drive.....

---

### Post by hencke on 2008-02-24
Hi!

I have Windows 98 on my ThinkPad 240 and I was looking for an easy way to install Xubuntu on it. I ended up using lubi/unetbooting to install Xubuntu 7.10 on the laptop.

[http://lubi.sourceforge.net/unetbootin.html](http://lubi.sourceforge.net/unetbootin.html)

I have a model 2609-41G with 64 MB RAM + I installed 128 MB extra. It has a 12 GB hard disk, of which Windows is on a 2GB partition (C: or hda1) and there was also a 10GB FAT 32 partition (D: ). To prepare for the installation I defragmented both drives (the Windows defradmenter is in the Start->Progrmas->System Tools menu). After that I downloaded the 10 MB .exe-file and followed the instructions it gave me. Here is a possibly useful step-by-step guide if you wish to see what happens (it shows the steps on a different computer with XP, but the same instructions apply for virtually any PC with Windows 98-Vista):

[http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora](http://www.howtoforge.com/unetbootin_windows_ubuntu_fedora)

So basically getting the install process running was as easy as installing any Windows program. After installation I know have a working system with both Windows 98 and Xubuntu 7.10. Xubuntu has 6GB for itself and it can also access the 6 GB that Windows 98 uses. Everything I need, including my Cisco Aironet wireless (that doesn't have drivers for Win98 ) worked after installation without configuration (I only had to enable wireless networking from the network applet).

Here is a few optional remarks on power management:

Without acpi=force (default for my bios) (I presume xubuntu uses apm when acpi is disabled):
-you have to press the power key to turn the display off after xubuntu has shutdown
-suspend does not work
-hibernate works, but you have to press the power key to turn the display off after xubuntu has entered hibernation
-the system goes to sleep when you close the lid and wakes up in about 15 seconds when you open it
-hard disk drive spins down after a moment

When using acpi=force:
-the system does shutdown properly
-suspend works (wakes up by pressing the "Fn" key. Waking up takes about 20 seconds.)
-hibernation works (wakes up by pressing the power button, boots in about one minute from boot menu (twice as fast as normal boot))
-nothing happens when you close the lid
-hard disk drive doesn't seem to spin down

At the start of the boot process, in both cases I get an error telling me to use acpi=force, even though in the second case I am using it. If for some reason you wish to use the acpi=force option you have to add it to your menu.lst. To do this open a terminal and type "sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup" to backup menu.lst and "sudo nano /boot/grub/menu.lst" to edit it. Navigate to the kernel line and add the option "acpi=force" (without quotes) to the end of the line. Press ctrl+o to save and ctrl+x to exit.

---

### Post by jcgrv06 on 2008-04-07
henckle,

Thanks for your post. I was able to install Xubuntu in my Thinkpad 240. I have now a dual boot with Windows 2000.

However, the maximum resolution I'm getting is 800x600. I tried reducing the pixel depth to 16 from 24 and adding 1024x768 as one of the modes in xorg.conf, but it didn't help.

Are you getting 1024x768?

Thanks.

---

### Post by hencke on 2008-04-07
Hi jcgrv06!

My ThinkPad 240 model 2609-41G has a 10.4 inch TFT with 800x600 resolution, unfortunately. Which model do you have? (This might help in finding out what settings you should use for the display.)

If you are new to linux/debian/ubuntu, I'd recommend trying this:

Open a terminal, then backup xorg.conf:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

Then reconfigure your xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

My best guess is that you should leave all other settings as they are (just press enter many times) but change the resolution to 1024x768, pixel depth to 16 and vertical refresh rate to 60 Hz, if possible. When presented with the option of configuring the monitor with the simple/medium/advanced options choose medium and then from the list presented choose 1024x768@60. Soon after this you can choose the pixel depth to be 16. (If you choose the advanced option you should also be able to configure the horizontal sync as well. I'm not sure what the horizontal sync should be, the link at the bottom might or might not help.)

[INDENT]If something goes wrong and you wish to use your old xorg.conf please boot in safe mode and:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

to get your old xorg.conf back and then type:

```
startx
```

to start the window manager. (Remember that then you have root-privileges and should restart asap.)[/INDENT]

If you have already tried something like this, then I can't really help too much, because I don't have the same screen as you do. You might want to try the link that gives you the horizontal sync and then try the configuration again with the advanced option, though.

Here are a few possibly useful links:

[LIST]
[*][http://moblog.co.uk/view.php?id=203052](http://moblog.co.uk/view.php?id=203052)

[*][http://www-307.ibm.com/pc/support/site.wss/product.do?template=%2Fproductselection%2Flandingpages%2FbrowseByProductLandingPage.vm&sitestyle=lenovo&brandind=10&validate=true](http://www-307.ibm.com/pc/support/site.wss/product.do?template=%2Fproductselection%2Flandingpages%2FbrowseByProductLandingPage.vm&sitestyle=lenovo&brandind=10&validate=true)

[*][http://www.thinkwiki.org/wiki/Category:240](http://www.thinkwiki.org/wiki/Category:240)
[/LIST]

This might help if you don't know your Horizontal sync rate:
[LIST]
[*][http://xtiming.sourceforge.net/cgi-bin/xtiming.pl](http://xtiming.sourceforge.net/cgi-bin/xtiming.pl)
[/LIST]

Please report back, I'm happy to TRY and help... =)

---

### Post by synchromesh on 2008-04-28
Thinkpad 240 and 240x systems came with 800x600 screens. The only exception to the rule are Japan-only 240z systems. Some of those had an integrated Ethernet port and 1024x768 screen. Those are pretty hard to come by around here.

So it's very unlikely that you'll be able to run your 240x at XGA resolutions.

The cool part about them is that they accept a real miniPCI wireless card instead of the modem. Another hack involves cutting off a few legs on the onboard RAM chips to disable it, then the system can take a 256MB Low Density chip and work with it. Chipset limitation is 256MB so 512MB chips will only work as 256MB if at all. Hope this helps.

---

### Post by hencke on 2008-04-29
> **synchromesh said:**
> Thinkpad 240 and 240x systems came with 800x600 screens. The only exception to the rule are Japan-only 240z systems. Some of those had an integrated Ethernet port and 1024x768 screen. Those are pretty hard to come by around here.

So it's very unlikely that you'll be able to run your 240x at XGA resolutions.

The cool part about them is that they accept a real miniPCI wireless card instead of the modem. Another hack involves cutting off a few legs on the onboard RAM chips to disable it, then the system can take a 256MB Low Density chip and work with it. Chipset limitation is 256MB so 512MB chips will only work as 256MB if at all. Hope this helps.

Agreed. Thanks for the input, there still seems to be a few TP 240s out there.

---

### Post by NoobieDoobieDo on 2008-05-26
> **synchromesh said:**
> Thinkpad 240 and 240x systems came with 800x600 screens. The only exception to the rule are Japan-only 240z systems. Some of those had an integrated Ethernet port and 1024x768 screen. Those are pretty hard to come by around here.


I have a plain Jane US version of the 240 and I get 1024x768 support in Win2k with no problems.  However it's not "true" 1024x768, it's 800x600 and the extra stuff is "off" the screen, when the mouse reaches the edge of the screen the display pans across to show the full resolution.

I hope this makes sense.

ps. I dont have built in ethernet

---

### Post by hencke on 2008-05-27
> **NoobieDoobieDo said:**
> I have a plain Jane US version of the 240 and I get 1024x768 support in Win2k with no problems.  However it's not "true" 1024x768, it's 800x600 and the extra stuff is "off" the screen, when the mouse reaches the edge of the screen the display pans across to show the full resolution.

I hope this makes sense.

ps. I dont have built in ethernet

Hi NoobieDoodieDo!

I just tried it myself and also in xubuntu you can get "1024x768 support" with a 800x600 monitor, although I wouldn't say "with no problems" to a newbie. Anyway, if somebody wants to try, this is where I got the info from:

[LIST]
[*][http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html](http://www.x.org/archive/X11R6.8.0/doc/xorg.conf.5.html)
[/LIST]

And here's what I did:
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

I went to the SubSection "Display" (under the Section "Screen") and added the line

```
Virtual 1024 768
```

and then I pressed Ctrl+o to save and Ctrl+x to exit. After that I logged out, pressed Ctrl+Alt+Backspace to restart the xserver, logged in and went to Applications > Settings > Settings Manager > Display and selected the new 1024x768@60 Resolution. I also tried a few other more exotic resolutions, but of course they didn't work because of the video card/video card driver.

---

