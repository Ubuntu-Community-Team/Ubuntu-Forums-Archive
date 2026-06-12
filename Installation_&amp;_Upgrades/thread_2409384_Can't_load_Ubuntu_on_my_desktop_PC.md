---
title: "Can't load Ubuntu on my desktop PC"
date: 2019-01-01
forum: Installation &amp; Upgrades
---

### Post by bluemetal04606 on 2019-01-01
I have been wanting to permanently switch from Windows to Linux for years, but some issue keep occurring, and it's driving me nuts!  Right now, I been trying to load several different versions of Ubuntu and its variants (Ubuntu, Kubuntu, Mint, Pup, and even even tried Debian) onto my PC, but I can't even get it to boot. Some versions just gives a black screen with a white _ on the top left, but does nothing, while the rest completely shuts off all hardware except for the CPU fan when trying to boot it.  
   
   The only version that I managed to get working somewhat is 14.04 lts, which would have been fine, except that there was no drivers for my hardware, probably because my PC parts is newer than the OS itself.  I had no ethernet, and tried a USB WI-FI adapter and it wouldn't work on it either.  I managed to find drivers for the WI-FI card, but it refused to install, guessing because the OS needed updated in order for it to install properly, which is something I can't do.  Either way, I would prefer to install either 18.04 or 18.10 of the Kubuntu version (if possible).  

I am using a Asus TUF B360M-E Gaming motherboard, if anyone knows how I can get Kubuntu 18.04 or 18.10 (whichever would work best on this PC) to boot properly, I'd appreciate it!

---

### Post by oldfred on 2019-01-01
Some others with similar issues. 
Some issues are brand specific and others are related to the AMD model.

 Gigabyte B450 Ryzen needs kernel & mesa drivers
[https://ubuntuforums.org/showthread.php?t=2408247](https://ubuntuforums.org/showthread.php?t=2408247)
Asus B350M-A needs newer kernel that 18.04 default
[https://ubuntuforums.org/showthread.php?t=2391892](https://ubuntuforums.org/showthread.php?t=2391892)
[https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816](https://ubuntuforums.org/showthread.php?t=2390660&p=13799816#post13799816)
MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)

---

### Post by bluemetal04606 on 2019-01-02
Sadly none of those helped, I spent days trying different distros and changing the BIOS settings, especially the secure boot thing.  It could be brand specific because I'm using the Intel version with a 8th gen i3 processor.

---

### Post by oldfred on 2019-01-02
Sorry, I thought that model number was in the AMD types. 
Intel versions have some different issues. I have an Asus z97 and what I have seen posted of newer Asus Intel motherboards the UEFI is very similar.
       Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=297](http://ubuntuforums.org/showthread.php?t=2258575&page=297)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 
    
       MSI Tomahawk Z370 GTX 1070 TI [SOLVED] Grub error during install two NVMe drives
[https://ubuntuforums.org/showthread.php?t=2398599](https://ubuntuforums.org/showthread.php?t=2398599)
Asus X299 Wired Internet issue, UEFI system clock
[https://ubuntuforums.org/showthread.php?t=2395036](https://ubuntuforums.org/showthread.php?t=2395036)
[https://ubuntuforums.org/showthread.php?t=2397473](https://ubuntuforums.org/showthread.php?t=2397473)
MSI X370 Gaming Plus used rEFInd
[https://ubuntuforums.org/showthread.php?t=2378837](https://ubuntuforums.org/showthread.php?t=2378837)
Asus Prime Z270-A  Ethernet patch
[https://ubuntuforums.org/showthread.php?t=2351572](https://ubuntuforums.org/showthread.php?t=2351572)

---

### Post by Dennis N on 2019-01-02
> **bluemetal04606 said:**
> Sadly none of those helped, I spent days trying different distros and changing the BIOS settings, especially the secure boot thing.  It could be brand specific because I'm using the Intel version with a 8th gen i3 processor.

B360 chipset works fine if you use 18.04 with supplied 4.15 kernel. I used MSI B360M Pro in my last build and it worked without a problem for a UEFI install of Ubuntu 18.04.

---

### Post by bluemetal04606 on 2019-01-03
I installed 14.04 lts on an external hard drive through my laptop and updated everything and added drivers to it so I can get it working on the desktop.  I been slowly upgrading the version to see what would happen.  16.04 worked, just missing intel LAN drivers (like the others I've tried), but when upgrading to 18.04, it just doesn't load, same issue.  Keyboard, mouse, and even the hard drive shuts off, and only get a blank screen.  

   Then, I just assumed that 18.04 needed updated, so I plugged the hard drive back into the laptop and updated everything, and finally plugged it back on the desktop.  Still have the same issue.  The 4.15 kernel made no difference, so I don't know what's going on.  I did switch back and forth between UEFI and legacy, as well as turning on and off secure boot, basically been playing around with BIOS to see if anything changes, but it doesn't.  I would stick with 16.04, but unsure if future versions will work or not.

---

### Post by oldfred on 2019-01-03
What video card or using Intel internal video?

If nVidia:
Some turn off video card in UEFI settings & install with just Intel. Then add nVidia driver and turn back on video card.
Normally we just use nomodeset to boot in lower quality mode and add nVidia driver.

---

### Post by bluemetal04606 on 2019-01-03
It's like you knew exactly what I was trying lol.  I took the graphics card out in a last attempt and that was the issue all along.  I will be installing the nvidia driver like you mentioned, thanks for the help!

---

### Post by oldfred on 2019-01-03
If real new nVidia card, you may want to add the ppa to get the very latest.
Do not install a .run file directly from nVidia.

       nVidia install, purge if needed.
[https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336](https://ubuntuforums.org/showthread.php?t=2383560&p=13735336#post13735336) 
            If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061)
[https://ubuntuforums.org/showthread.php?t=2362351](https://ubuntuforums.org/showthread.php?t=2362351) 
            
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html) 

   # Shows standard repository versions, which is the same as
System Settings, Software & Updates icon, Additional drivers tab
With 18.04, the only way I can get to this now is with Software Updater & Settings.
ubuntu-drivers devices 
   [https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
# make sure system is up to date
sudo apt-get update
sudo apt-get upgrade
sudo apt-add-repository ppa:graphics-drivers/ppa
sudo apt-get update 
   # to uninstall ppa
sudo add-apt-repository --remove ppa:graphics-drivers/ppa 
   # should show newest versions available in addition
ubuntu-drivers devices
You then can manually choose any in list.
sudo apt-get install nvidia-XXX

---

