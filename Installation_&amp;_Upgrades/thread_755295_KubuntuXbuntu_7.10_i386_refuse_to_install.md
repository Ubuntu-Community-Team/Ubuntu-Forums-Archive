---
title: "Kubuntu/Xbuntu 7.10 i386 refuse to install"
date: 2008-04-14
forum: Installation &amp; Upgrades
---

### Post by Tempshed on 2008-04-14
I decided to try installing Ubuntu on an old machine that been languishing in the attic a few years. To cut a long story short Kubuntu 7.10 i386, Kubuntu alternate 7.10 i386, Xbuntu 7.10 i386 and even ***Suse 10.3 i386*** flatly refuse to install. However Windows XP Pro that terrible o/s so despised by the Linux community installs flawlessly. After booting up I get as far as the initial splash screen "Start or install Ubuntu" plus the list of other options and as soon as I hit the enter button the installation progress bar flashes on screen for a second at most and then the machine reboots and then reboots and reboots. Often I don't get as far the initial splash screen, the machine boots up then goes straight to reboot. The machine spec is: Gigabyte GA-5AX mainboard, AMD K6 500Mhz cpu, 750MB ram, 40GB Seagate ide hdd, Adaptec AHA2930CU scsi host adapter connected to a Plextor scsi CDROM drive and a Plextor scsi CDRW drive, Belkin pci lan card, generic pci to pcmcia controller card with a D-Link DWL-G650 inserted, 8MB ATI Rage pro graphics card, usb keyboard and mouse. And yes I did check the md5sum of the downloaded iso file and burned the disk at a slow speed. The D-Link DWL-G650 together with the pci to pcmcia controller card work perfectly in my other high spec modern machine. I've tried everything I can think of, to no avail. Perhaps one of you guys can help me out. TIA.

---

### Post by Pumalite on 2008-04-14
Try the Alternate CD.

---

### Post by Tempshed on 2008-04-15
What can I say; I'm underwhelmed. Fourteen hours after my original post and one four word response from some one who didn't bother to read my post properly.

---

### Post by PmDematagoda on 2008-04-15
Did you try booting the Ubuntu Live CD using parameters such as "noapic" or "nosplash"?

---

### Post by Tempshed on 2008-04-15
Assuming I've got to the intro/splash screen, how would I enter these parameters you  mention? Bearing in mind that just hitting the enter key causes the machine to reboot.

---

### Post by martrn on 2008-04-15
OK here is my sudgestion :

Rather than try installing Kubuntu from the Kubuntu alternate 7.10 Download the server editition (for ubuntu) and do not install X11 (the server edition will not install this anyway).

Then login to a termernial when this is installed and type 

//  First update your sources for ubuntu
```
sudo nano /etc/apt/sources.list
```

```
sudo apt-get install kdm
```
//  [OR - (NOT BOTH)
```
sudo apt-get install gdm
```

```
sudo apt-get install xubuntu-desktop
sudo apt-get update
sudo apt-get upgrade
```

// Then try configureing you X11
```
sudo dpkg-reconfigure xserver-xorg
```

Find out if you can get X- running
```
startx
```

And find out at what section it fails.

Configureing an full X11 system on a AMD K6 500Mhz is frought with a few problems you need trial and error to find out what fails.  Do not install COMPIZ, GNOME or KDE install XFCE  [http://www.xfce.org/](http://www.xfce.org/)

---

