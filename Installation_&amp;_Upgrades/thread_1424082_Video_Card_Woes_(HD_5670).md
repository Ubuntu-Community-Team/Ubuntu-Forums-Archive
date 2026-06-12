---
title: "Video Card Woes (HD 5670)"
date: 2010-03-07
forum: Installation &amp; Upgrades
---

### Post by babarsac on 2010-03-07
I recently finished my first Ubuntu build the other and so far everything has worked flawlessly.  Even the PCI wi-fi card worked out of the box.  My motherboard is an ASUS M4A78-EM with an on-board video chip.  The on-board video works fine but I wanted some better performance, and for that I have a Sapphire Radeon HD 5670.

At first the system wouldn't detect the card so I went into the BIOS to change some setting.  On this board you can't completely disable the on-board video, but you can change the order of where the system looks first.  After making the changes the system picked up my card and I booted into Ubuntu.

Next step was to update the video driver.  After some googling I brought up the "Hardware Drivers" tool which was nice enough to tell me I needed the "ATI\AMD proprietary FGLRX driver".  I clicked install and rebooted my system.

And it goes downhill from here. ](*,)

Upon rebooting I get past the ASUS splash screen, then I see the Ubuntu symbol, and then the screen goes black.  I don't get a warning from my monitor that there's no video input so that means Ubuntu is feeding me a blank screen.  Even worse when I reboot again and press DEL to enter the BIOS it won't go into the BIOS.  All it does is skip ahead to the Ubuntu symbol then the blank screen.

The only way I can boot properly or access the BIOS is remove the video card.  I'm thinking that this a driver issue but does anyone have any ideas why this is happening?

Oh yeah I'm running Ubuntu release 9.10

---

### Post by khelben1979 on 2010-03-07
Can you access the tty terminals when the 5670 is inserted? (press ctrl + alt + f1 to access the first one)

On some graphic cards you need to upgrade the BIOS on the card itself. Have you checked this up if their website recommends this?

---

### Post by lidex on 2010-03-07
Have you tried it with windows? May be a linux specific issue:
[http://ubuntuforums.org/showthread.php?t=1419962]("http://ubuntuforums.org/showthread.php?t=1419962")

---

### Post by cascade9 on 2010-03-07
It could be that your config is setup to use the ATI 3200, and putting the 5670 in just confuses the hell out of the config. 

Maybe try removing the ATI drivers, shut down, install the video card, start, then reinstall the ATI drivers.

---

### Post by khelben1979 on 2010-03-07
Try with different versions of [ATi Catalyst]("http://en.wikipedia.org/wiki/ATI_Catalyst") from the ATi webpage to see if it solves your graphics issues.

---

### Post by lidex on 2010-03-07
> **cascade9 said:**
> It could be that your config is setup to use the ATI 3200, and putting the 5670 in just confuses the hell out of the config. 

Maybe try removing the ATI drivers, shut down, install the video card, start, then reinstall the ATI drivers.

Yes, absolutely best practice is to remove any old/conflicting drivers before installing card. Try booting from onboard port to get to desktop and remove xorg.conf while you're in there:
```
sudo mv /etc/X11/xorg.conf xorg.conf.old
``` If you still can't boot go into Live session and remove/rename.
One other thing - I know this is billed as low power board, but what is your power supply rated?

---

### Post by lavinog on 2010-03-07
The 5600 series is only supported with the most recent driver Feb 2010 (10-2)
The driver that is installed by the ubuntu hardware drivers manager is 9-11 which does not support this card.
[http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf](http://www2.ati.com/drivers/linux/catalyst_102_linux.pdf)

---

### Post by speedygonzales on 2010-04-08
I have a similar problem. 9.10 works fine just after install, and after I install the latest catalyst from AMD. However, the screen goes black when rebooting after updating. I suspect that there are some driver package that I should not update.

---

### Post by lidex on 2010-04-08
> **speedygonzales said:**
> I have a similar problem. 9.10 works fine just after install, and after I install the latest catalyst from AMD. However, the screen goes black when rebooting after updating. I suspect that there are some driver package that I should not update.
Have a look here:
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by quadproc on 2010-04-08
> **babarsac said:**
> 
...
Next step was to update the video driver.  After some googling I brought up the "Hardware Drivers" tool which was nice enough to tell me I needed the "ATI\AMD proprietary FGLRX driver".  I clicked install and rebooted my system.

A couple of points:

The Hardware Drivers utility does not necessarily do what you want or need, and it does **not** correctly report your system's configuration.  I find that I get much better results downloading the appropriate driver file from ATI and then installing it using ATI's installation procedure.  If you add arguments of --keep and --install to the .run file then the installation will leave behind all of the files and directories that it used for the install as well as doing the install.  You might find those files useful.

I don't know if this problem has been fixed, but X windows used to have a fatal problem if the hardware had more than one graphics subsystem.  In this case, X could not decide which subsystem was the primary one (the one it uses to communicate with the user) and would simply quit executing.  The workaround for this that I used was to include a BusID spec in the Driver section of the xorg.conf file.  Only the primary hardware needs such a spec.

quadproc

---

### Post by speedygonzales on 2010-04-09
Thanks. Building the packages fail, see attached log.

---

### Post by speedygonzales on 2010-04-10
Got it working.
Installing xorg-driver-fglrx first enabled the drivers to build successfully, then I had to remove xorg-driver-fglrx to resolve a conflict in order to install the *.deb packages.

---

### Post by jasonbauer on 2010-05-15
I had a similar problem with the same card when installing on 10.04. I finally booted from the onboard video and installed the binary driver. Now it works, but the screen resolution is set to full (1920x1080) but there is a black border around my desktop. Anyone know how to fix that???

---

### Post by lidex on 2010-05-16
> **jasonbauer said:**
> I had a similar problem with the same card when installing on 10.04. I finally booted from the onboard video and installed the binary driver. Now it works, but the screen resolution is set to full (1920x1080) but there is a black border around my desktop. Anyone know how to fix that???

Have a look here:
[http://ubuntuforums.org/showthread.php?t=872330]("http://ubuntuforums.org/showthread.php?t=872330")

---

### Post by - Mikael - on 2010-09-02
It works fine with 10.10 beta, no drivers to be installed first  :)

---

