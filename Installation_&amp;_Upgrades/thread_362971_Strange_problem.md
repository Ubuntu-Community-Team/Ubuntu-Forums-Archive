---
title: "Strange problem"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by suselinux2 on 2007-02-16
Hello

I have two very strange problems. I have two computers. First one is laptop p3-700, 256mb (ram), 10Gb Hdd; the second one is home computer Amd 64x2 3600+, 512 mb of ram... .

I tried to install on both Ubuntu, But I was unsuccessful. In both freezes after loading to 100% (the first boot screen after the start menu). I also tried with older versions of Ubuntu, but the result was the same. What is wrong wiht Ubuntu? I also have another laptop (1.5 Ghz Celeron) and I have installed the same distribution of Ubuntu without any problems. Just for knowing: Mandriva 2007 loads perfectly.

Thank you for all your help.

---

### Post by Kateikyoushi on 2007-02-16
Did you try to check the disc for errors ? Might be a wrong disc.

---

### Post by suselinux2 on 2007-02-16
Yes I did. From this disc I installed Ubuntu on on my Personal notebook sucessfully (celeron 1.5).

---

### Post by suselinux2 on 2007-02-19
I have resolved my problem with home computer Amd 64x2 3600+, 512 mb of ram... . The problem it was wih graphic card (some Ati based graphic cards are not supported with linux). I had changed it by Nvidia graphic card and everything works perfectly.

But still remanins laptop (Mitac MTC-6120 - p3-700). I can`t install (x)ubuntu on it. It freezes while booting it from cd.

Thanks for all your help.

---

### Post by aberry5555 on 2007-02-19
It's most likely the ATI graphics cards are supported, it's just that the automatic configuration scripts for loading ATI drivers are not set up properly. If you want to get the desk top working on your laptop then try the following, as I have a feeling it's a driver problem as well, although you will have to give more information about your laptop's graphics card.

at start-up on the live cd press F6 to edit the boot line. Delete "quiet - splash" and type in "break = bottom". 

This will stop the Ubuntu loading bar from appearing and will run through a load of commands on screen (loading up ubuntu) and, about half way through loading, will stop and give you a command line. Don't worry about any error messages so far.

at the command line type in the following:

```
chroot /root nano /etc/X11/xorg.conf
```

This will open up your GUI configuration file (it contains the settings for things like your mouse, keyboard, monitor and graphics card.)

scroll down until you find a heading called "Device", below this should be a sub-heading called "Driver". Depending on the type of Graphics card it is (I'm thinking maybe an ATI one) it will say which driver it is using in inverted commas like so:

```
Driver        "ATI"
```

Change the driver name (whether it be "ATI" or something else) to "VESA" (these are the most basic graphics drivers available to linux). Once you've done this press ctrl+O and ctrl+X, this will save and exit the text editor, bringing you back to the command line. Now type in "exit" at the command line and Ubuntu will continue to load with the VESA drivers and, hopefully, should boot!

---

### Post by HellionDarkLord on 2007-02-19
I have the same problem with the 6.10 Edgy installation disc.  And this is a bigger problem than everybody is assuming it is.

What I had to do:  Install 6.06 LTS completely, upgrade using the live cd for Edgy while running Dapper, Reboot into failsafe from the boot menu and reconfigure the xserver-xorg. 

That got me to the point where I could do everything in the desktops except scroll upwards with the mouse or scrollbar because it messed everything up.  Then I attepmted to download drivers for my video card and found out that the only drivers available through the manufacturer were indeed open source, but only good for Xfree86 and not Xorg.  So I went through all the hassle to convert Ubuntu to xfree86 but in the end got nowhere. 

I did everything exactly as I was supposed to, and I know what I'm doing. After only a day of smooth running I tried to upgrade the system thinking to do some art with gimp and Whammo!! everything blew up on me.  I suppose that I shouldn't really have messed with it, but HEY I'm new to Ubuntu and have only tried a few times to really use the system.

I'm no expert, but I think that the xserver setup in Edgy needs some serious reworking because EVERYTHING works fine here in Dapper Drake 6.06 LTS

---

### Post by Kateikyoushi on 2007-02-20
The X setup is being worked on, probably feisty +1 will be able to do it automagically, feisty can fall back on low res desktop instead of terminal.

---

