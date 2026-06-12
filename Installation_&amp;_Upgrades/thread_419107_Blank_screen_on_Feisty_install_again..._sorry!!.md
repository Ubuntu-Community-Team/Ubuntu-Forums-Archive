---
title: "Blank screen on Feisty install again... sorry!!"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by willie_wang on 2007-04-22
Hello! I'm new to linux, having tried ubuntu 6.10 and loved it, I've downloaded the live CD (64 bit) and tried to install. I have a windows laptop now and want to install feisty instead.

Acer Aspire 5021 Laptop
ATI x700 graphics
monitor native res 1280 x 800

After I boot from the CD and select the option to install, i wait for the kernel and driver modules to load up and into the installation... then blank screen - although as other people have said, I can also hear the music, i can press ctrl-alt-f3 i think it is and get to a text-based command line but nothing else...

can someone help me please? i've read the other solutions, but they all seem to imply that there is an existing ubuntu installation on the hard disk. i've tried to press f4 and change the resolution - i've tried this with 800x600 and also 1024x768 16 and 32 bit colours, but same blank screen every time... i've even removed the quiet splash from the boot options, but still no go...

please help.

Willie

---

### Post by Lemony Fresh on 2007-04-22
I have the same problem.  I ended up installing with the alternate cd and used text mode.  Then from there I have to choose recovery startup on grub.  Of course my screen blanks during a normal boot.  From the command prompt I can type exit and them GDM starts and the desktop loads.  It is only in 800x600 although my xorg.conf has 1280x1024 as default.  This may have something to do with the fact I am in recovery mode.  glxinfo reads radeon x800 as it is supposed to.  I can even get  desktop effects to work flawlessly. 

Feisty 7.04 x64 
ATI x800
1GB RAM
ASUS mainboard

---

### Post by willie_wang on 2007-04-22
i'll try the alternate cd to see if that works then and i'll get back to you :)

---

### Post by atze76 on 2007-04-22
If you can change to a console window after your system has booted successfully, then you could try to add the following line to the **Section "Device"** section in the /etc/X11/xorg.conf file:

Option		"MonitorLayout"		"LVDS, AUTO"

The best way to see whether this fixed you black-screen problem or not, is just to reboot your system.

---

### Post by Kytsi on 2007-04-23
Hi

Same problem here with same laptop.

---

### Post by danrooke on 2007-04-23
I have the same problem with an Acer 5024WLMi.

Not a burning issue for me, but I did want to try out Ubuntu on this machine to see how it performed.

Dan

---

### Post by UrbanFallout on 2007-04-24
Hi

I too have a an Acer 5024 WLMi, but I think will help anyone with an ATI express card on a laptop.

I managed to get x going by doing the following:

1. Select the default option for booting and wait the 3 minutes or so for it to boot up. You will of course be presented with a blank screen.

2. **Press Ctrl+Alt+F1**. You will be presented with a text terminal screen.

3. Type 
```
sudo dpkg-reconfigure xserver-xorg
```
This will start a script to reconfigure your xserver. You will be presented with a series of text dialogs requesting choices to be made or telling you how to select options appropriately. In almost every case you can select the default option.

4. However on screen 2 for the [COLOR="Red"]X server driver[/COLOR], **Select "vesa"**. You can navigate to it by using the up down arrow keys. Then **Press Enter**. 

5. In some information windows "OK" is not highlighted. **Press the TAB button** to select OK and then **Press ENTER**.

6.On about screen 10 or so, you will be presented with a "[COLOR="Red"]X.org server modules[/COLOR]" screen. **Make sure "int10" is deselected**. You can do this by navigating to "int10" with the arrow keys and Pressing the SPACE BAR.

7. About 5 screens after that you will be presented with a dialog requesting what [COLOR="Red"]video resolutions[/COLOR] are valid for your monitor. **Select the relevant resolutions** (in my case 1280x800) by navigating to it with the arrow keys and pressing the SPACE BAR.

8. About 5 screens after this is a dialog requesting what [COLOR="Red"]bit-depth[/COLOR] to use. **Select 16** with the arrow keys and press ENTER. 24 bits appears to fail for some reason.

9. Press enter for the remaining few dialogs.

10. Now type
```
startx
```
in the terminal window.

This should get you far enough to start the actual installation. After installation you will probably need to read the howto on installing the ATI driver. Don't be too daunted. This is not as difficult as it first seems.

Hope this helps
Nick

---

### Post by UrbanFallout on 2007-04-25
Actually, if your network is up and running this post gives a more elegant solution:

[COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=414723]("http://ubuntuforums.org/showthread.php?t=414723")[/COLOR]

---

