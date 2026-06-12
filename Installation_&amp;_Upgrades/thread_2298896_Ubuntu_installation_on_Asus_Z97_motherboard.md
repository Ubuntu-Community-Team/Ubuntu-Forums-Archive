---
title: "Ubuntu installation on Asus Z97 motherboard"
date: 2015-10-14
forum: Installation &amp; Upgrades
---

### Post by Aries01 on 2015-10-14
I'm not able to install Ubuntu on a new computer with a Asus Z97 motherboard. There is some parameter in the BIOS that is blocking the booting of a Ubuntu installation medium- I tested the computer with a Windows disk and it worked with no problem. In instructions on installing Ubuntu on a UEFI-capable motherboard they tell you to disable Secure Boot- but there is no such parameter in the Z97 setup menu. The booting starts okay, in a UEFI boot one can select either trying the OS or installing it- whichever is selected, the computer just goes dead after that. If anyone else has encountered this problem with this piece of hardware and has been able to solve it, I would be interested to know.

---

### Post by Dennis N on 2015-10-14
I built with an Asus H97 board which is similar, except a few features not included such as overclocking ability. 

Ubuntu supports secure boot, since it has a signed kernel available. I installed Xubuntu and Ubuntu MATE, both with Secure Boot enabled, and had no problem doing that. So there may be some other setting change needed.

When I installed, I used the one-time boot option (F8) and selected the UEFI option for my flash drive installer (the boot menu entry has UEFI in the description). Everything went without a hitch. This board has proven to be very good.

If you need to disable secure boot, it can be done. Some OSes do not support that setting. For example, Linux Mint will not run the installer if secure boot is enabled. I will post some instructions.

---

### Post by oldfred on 2015-10-14
My install is to a Asus X97-ar.
I did have to change a lot of UEFI settings and when I updated UEFI to new version it reset them all back to defaults. So update first and keep a record of changes.

What video are you using Intel, or another video card?

I changed OS from Windows to Other. And had to have UEFI only on to let me boot flash drive installer in UEFI mode.
I turned off fast boot for both cold & warm reboot. But after install and configuration was done I changed reboot to fast, but with a 3 second delay, so I still could press a key if quick. And a 3 second delay in grub for same reason.

 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
BIOS only install Asus Z97-a
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)

---

### Post by Dennis N on 2015-10-14
Here are some directions, if needed:

Disable secure boot - Asus H97M-Plus motherboard - simple, but not that obvious. 

Enter Setup, use F7 for Advanced, then Boot Tab.
Find "Secure Boot" and Enter to get the secure boot settings.

See attached screenshot. _Lines 1,2 are informative only - not interactive_. 

Change OS Type to "Other OS". This enters a "permissive mode" where secure boot is not enforced. But, note that "Secure Boot State" is indicated as still "enabled". 

In this mode, I installed Linux Mint and Manjaro which do not support secure boot. Each boots with a regular kernel (unsigned).

Advice on the Internet suggested deleting the Platform Key to disable secure boot. I found it was not necessary (at least on this motherboard). But, if you do that, "Secure Boot State" will then say "disabled". 

Note: My Platform Key status says "unloaded". This changed from "loaded" after I saved the keys to a USB stick for backup. I took no other action in the Key Management.

---

### Post by Aries01 on 2015-10-15
I appreciate all the advice. I did find the Secure Boot submenu, I selected "Other OS" in place of Windows, and I removed the security keys. The problem persists. I need to keep looking into this. I'm trying to install the regular 64-bit Ubuntu 15.04- should I try some other version of Ubuntu?

---

### Post by oldfred on 2015-10-15
I have 14.04 as my main working instal, and 15.04 and 15.10 as test installs just to see if the install ok and they have.

What video are you using? Intel or another video card?

Some more screenshots:
I liked Asus as it will take screen shots & save them to flash drive.
It only let me attact two?
But in this thread I had more screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

---

### Post by Aries01 on 2015-10-17
I disabled Fast Boot and Secure Boot and cleared the security keys, then proceeded with installing from a DVD. The installation menu appears, and after a selection is made sounds from the DVD drive suggest that the disc is being read properly. Then the monitor goes to sleep- it flashes a "going to sleep" message, event though the computer is still using the DVD. Could the display card have something to do with this problem? I am using a NVIDIA GTX card.
  I'm upgrading from a pre-UEFI era computer, and all these UEFI-related issues are new to me.

---

### Post by oldfred on 2015-10-17
I have used nVidia and for the last 3 or 4 years have had to use nomodset to boot. I even add it to my installer, so it is always there. I also have to use nomodeset on first boot or until I install the nVidia driver. 

What video card. The newer Maxwells do require the newest kernel, support software and nVidia driver. Often best then to use ppa. Do not download from nVidia.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132
[/URL]
 Updated driver search by nVidia model, do not download, just check correct driver version
[URL="http://www.geforce.com/drivers"]http://www.geforce.com/drivers
[/URL]
 Ubuntu Launches Its "Fresh" Proprietary Driver PPA
[http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA](http://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-Fresh-Driver-PPA)
[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
Instructions are newest driver for newest cards, must load legacy driver if old nVidia card.
[http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action](http://www.omgubuntu.co.uk/2015/08/ubuntu-nvidia-graphics-drivers-ppa-is-ready-for-action)
Details on why and future incorporation to Ubuntu installer
[https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html](https://lists.ubuntu.com/archives/ubuntu-desktop/2015-August/004693.html)

# Shows standard repository versions
 ubuntu-drivers devices

sudo apt-add-repository ppa:graphics-drivers/ppa
# should show newest versions available in addition
 ubuntu-drivers devices
sudo apt-get update && sudo apt-get install nvidia-3xx
# I usually use nvidia-3xx-updates, where 3xx is newest available, if older card do not install newest version, check correct legacy version from nVidia.

#To roll back/undo changes made the PPA you should use the ppa-purge command.
If you install wrong nVidia, do not install a newer or correct one unless you totally purge the old one. [URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

---

### Post by Aries01 on 2015-10-17
Giving one last try to this, I placed a 14.04 DVD into the DVD drive and Ubuntu installed itself very nicely and without display problems, in Legacy mode however. 

If I tried to install Windows 7 in Virtualbox on this installation, would the Legacy installation of the Ubuntu host cause a problem? In other words, does the Secure Boot parameter that is set to "other OS" make Windows install in Legacy mode too, or does the BIOS always require Windows to work in UEFI? Admittedly, this is a small problem compared to not having any OS in the computer at all.

My GTX card is made by Asus and it's just astonishing that that piece of hardware can sabotage a OS installation, and the same can be done by security settings in the BIOS that are made for a world where there is only Windows.

---

### Post by oldfred on 2015-10-17
Did you try nomodeset using grub menu with UEFI boot and edit linux line?

Did you use gpt partitioning?
I prefer gpt for either BIOS/CSM or UEFI boot but only on drives that will not need Windows in BIOS boot mode.
Windows only boots from gpt with UEFI.
Windows only boots from MBR(msdos) with BIOS.
Not sure then what partitioning is seen by Windows in VirtualBox? Or can you change partitioning inside it as opposed to actual partitions on drive?

---

### Post by Aries01 on 2015-10-18
I am totally unfamiliar with editing GRUB, but at least I got my computer working with a Legacy installation of Ubuntu. Funny that it works with version 14.04, but not 15.04. I bought the components just a month ago, so this must be an issue of new hardware not accepting Ubuntu, so to speak. Maybe Ubuntu developers might be interested in the experience I described here, even if the people at Asus weren't.

The graphics card is Asus STRIX-GTX980-DC20C-4GD5 GTX 980, if anyone wants to know. It appears that the proprietary driver and its control panel are working just fine, in spite of this boot issue.

---

### Post by Dennis N on 2015-10-18
Glad you got that system working. I think you will enjoy it. The general rule is with the latest components, the latest version of Ubuntu will give the best results. so yes, that is odd that 15.04 caused you problems. My system (Asus H97) has only the Intel integrated graphics, and it installed without a hitch, and every distro (Ubuntu or other) that I have added works well. After using the UEFI over a year now, I like it better than the legacy boot. I even switched another computer to UEFI that had been running in BIOS mode previously.

---

