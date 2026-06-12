---
title: "Ubuntu 14.04 installer goes to black screen."
date: 2015-01-14
forum: Installation &amp; Upgrades
---

### Post by chip3 on 2015-01-14
I'm trying to install Ubuntu 14.04 onto my new computer.  I have tried both burning the iso onto a dvd and also using a thumbdrive. (The thumbdrive worked on a different machine two days ago, so I'm pretty confident the thumbdrive is set up correctly.)

When I boot from DVD I get the purple splash screen seen in the first answer to this question

[http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it](http://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it)

I have tried all the options given in this answer. Without using nomodeset I go directly to a black screen never to recover. When nomodeset is checked I get a bit farther, it goes to a screen that says Ubuntu 14.04 with four dots under it. These dots flash white to red, and then ultimately white to yellow, then the screen goes black. I have combed through the bios making sure that everything I can turn off about quick boot or UEFI launching with legacy that I can find. 

When I try to boot from the USB thumbdrive, I go straight to a black Installer boot menu that lists options like, "Try Ubuntu without installing" or "Install Ubuntu". There are no advanced options though. Selecting that and hitting enter takes me to a submenu that only has the option to go back. (So I can't set nomodeset) When I select either Try Ubuntu without installing or Install Ubuntu I go to a light gray screen with a flashing cursor in the upper left corner.

As with the DVD I've tried multiple settings in the bios and haven't found anything that makes a difference. Anyone got any suggestions what to try?

Help is greatly appreciated.
Chip

---

### Post by QIII on 2015-01-14
Hello!

Could you tell us about your machine specs?

---

### Post by chip3 on 2015-01-14
> **QIII said:**
> Hello!

Could you tell us about your machine specs?

Intel i7-4790k
Gigabyte GA-Z97Z-Gaming 5 motherboard
32 Gb Corsair Vengence Ram DDR3 2400
EVGA GeForce GTX 970 Video Card
PNY 480GB SSD
Crucial 1Tb SSD

---

### Post by fantab on 2015-01-14
Boot your DVD/USB with **nomodeset** kernel option: [http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997](http://ubuntuforums.org/showthread.php?t=1613132&p=10069997#post10069997)
Nomodeset option will boot Ubuntu in 'failsafe graphics' mode. After you have installed Ubuntu and when you restart, you must again use 'nomodeset', then go to System Settings -> Additional driver and install the appropriate graphics driver.

EDIT:
> There are no advanced options though. Selecting that and hitting enter  takes me to a submenu that only has the option to go back. (So I can't  set nomodeset)

I missed that earlier.

After you've selected the 'Try Ubuntu' option press the 'e' key... that should give you the option to edit.

You have UEFI boot probably, that is why you see black grub menu...
Doest this machine has any pre-installed OS? Or any other OS, like Win8?
I suggest that take a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by chip3 on 2015-01-14
> **fantab said:**
> After you've selected the 'Try Ubuntu' option press the 'e' key... that should give you the option to edit.


Unfortunately when using the USB boot, as soon as Try Ubuntu starts, it goes immediately to the grey screen with flashing cursor. Hitting e key doesn't do anything. With the DVD boot I am able to select nomodeset and that runs for a while (Ubuntu 14.04 with four dots under it that cycle white/red) but ultimately just goes full black.

When I launch from DVD I have the following options that I can set true or false
acpi = off
noapci
nolapci
edd=on
nodmraid
nomodeset
Free software only

I have tried various combinations of them. setting nomodeset to true means that when the install starts I do get the loading screen for a while. The others don't seem to make much difference. 

> **fantab said:**
> 
You have UEFI boot probably, that is why you see black grub menu...
Doest this machine has any pre-installed OS? Or any other OS, like Win8?
I suggest that take a look at [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

This machine has Windows 7 installed on the 1TB ssd. I have tried removing the 1TB ssd and leaving the 480gb ssd and that makes no difference.

EDIT:  I notice that a number of posts that relate to UEFI are if you bought a computer that has windows 8 preinstalled. Just for the record, this is NOT the case here.  I built this computer and installed windows 7 from the disk.

---

### Post by fantab on 2015-01-15
Do you have two Graphics cards? If you do then check this: [Hybrid Graphics]("https://help.ubuntu.com/community/HybridGraphics")
Look in the BIOS/UEFI menu if there is an option to switch off one of the Grpahics card.

Since you already have Win7, is it installed in UEFI mode or Legacy mode?

Try another distro and see how it fares...

---

### Post by MAFoElffen on 2015-01-15
If you have a single nVidia... use this as your appended kernel boot option
```

nomodeset nouveau.modeset=0

```
Your nVidia card is so new, that nouveau does not support it yet, so has to be excluded...

If you have SLI (nVidia times two), refer to the bottom of Post #1 of my sticky (link in my signature line, where it mentions SLI....

Basically, physically pull the second card until you get the system installed with the nVidia driver. That means using F6 > nomodeset at the advanced install menu of the installer (detailed instruction for that at the top of Post #3 of my sticky)... After the install, on first boot, using nomodeset as a kernel boot option (instructions in Post #1 of my sticky, and in more detail in another tutorial linked from Post #2). add on
```

nouveau.modeset=0

```
after the nomodeset option (Post #3 of my sticky) to the end of that

With SLI and ___, this is not specific just to Ubuntu. This is the same using SLI on Unix and any flavor of Linux. The graphics layer works the same. Been doing SLI with them for over 10 years now... The explanation? What others are explaining is hybrid graphics.which means two different kinds of cards, switching from one two another, one at a time... SLI is more of a challenge, where you have two identical cards working as one. XServer, on it's own, doesn't know how to do that without the nVidia driver installed first.

After you get it up with the driver's installed... put the second card back in and reconfigure it, in the nVidia setting. That will rewrite  the xorg.conf file to include the specifics for the second (or second and third) card(s).You use the same method for Radeon Crossfire.

Is that enough info to get you started?

---

### Post by chip3 on 2015-01-15
> **MAFoElffen said:**
> 
Basically, physically pull the second card until you get the system installed with the nVidia driver.

Ok, when I physical remove the nVidia card (and use the onboard intel graphics) I'm able to get much farther. 

I get asked to pick a language, and then I select download updates while installing, and then I come to the Installation Type page.

Here it always tells me that there is no operating system installed. But there is an operating system installed...  Needless to say, I don't like the idea of erasing my disk...

Any idea what to do now?

Thanks for all the help
Chip

EDIT:  I guess I should mention at the Installation type page I get the following 4 options
Erase disk and install Ubuntu
Encrypt the new Ubuntu installation for security
Use LVM with the new Ubuntu installation
Something else.

I poked around under Something else, but I'm uncertain what to do. I does see the two partitions on my windows boot disk I believe.

---

### Post by fantab on 2015-01-16
Use the 'Something Else' option... and install Ubuntu '/' to the partition to the partition you want to install to... Swap will the detected and used if already available.
You can also use Gparted from Live Ubuntu desktop.

Post the output of :
```
sudo parted -l
sudo fdisk -l
```
if you have any further clarifications...

---

### Post by MAFoElffen on 2015-01-16
sidenote question--
Is your onboard Intel APU or CPU? 

Wondering if you just could have turned that off in the BIOS. You don't sound like your are SLI. You sound like you only have 1 physical nVidia card, You have nVidia (not onboard) and Intel (onboard), but you are not considered as Hybrid Graphics.

You can install like you are doing, with no worries about that. Just thinking ahead towards your reboot and graphics driver install...

---

