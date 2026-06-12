---
title: "trying to install but get read error"
date: 2010-01-25
forum: Installation &amp; Upgrades
---

### Post by biigg on 2010-01-25
[SIZE=3]**Hi  guys, Trying to install Ubuntu **on older [/SIZE][SIZE=3]HP[/SIZE][SIZE=3] laptop. have downloaded it twice and burnt 2 CDs thinking it was not burnt right the first time. But when I put the CD in CD-rom it  acts like it is going to go so I can install it. But when the menu screen comes up I move it down to install Ubuntu and immediately I get an I/O error  and it says error reading boot CD and it tells me to reboot. I do this and the same thing again, can anyone out there figure why this is doing this. PLEASE HELP NO SUCCESS.  Thank you for any help.
I am burning the disc as slow as I can and as an ISO image disc.  [/SIZE]

---

### Post by spcwingo on 2010-01-25
I had the same problem on a few machines.  Some were dirty lenses inside of the CDROM.  Some just refused to use the live CD or Alternate CD.  The way that I got Ubuntu installed on those was to use the mini ISO.  Note that the mini will only install a CLI system.  You can get the full desktop with one command:

```
sudo apt-get install ubuntu-desktop
```

Anyways, enough jabbering...here's a link to the mini ISO:

[https://help.ubuntu.com/community/Installation/MinimalCD]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by biigg on 2010-01-28
**Sorry **[spcwingo]("http://ubuntuforums.org/member.php?u=710414"), this did not work or I am not doing it right. Is it possible you could give me some step by step instructions on how and where to find the right ver. of Ubuntu, and how to install it, cause everything that i have tried has failed me. It would be of great help so i can get this laptop up and running. Thank you again if you can do this.     biigg

---

### Post by spcwingo on 2010-01-28
Which version of Ubuntu would you like...the latest and greatest or the LTS [long term support (which in my opinion is the most stable right now)]?

---

### Post by krosby on 2010-01-28
I'm interested in this thread, as I'm having the same exact problem...  I'm trying to build a computer, and don't want windows to touch it.   I have all the hardware together ok.  
Admittedly, this is my first attempt at dealing with BIOS settings, and to me it *seems* that 
all the devices are working ok.
When I insert the install disc, I get the ubuntu splash screen, but when I try to do anything, check 
disc, install, I get the I/O error, and have to reboot.
I'll try the miniIso when I get off work...
Thanks for your help!
 
Do I need to partition the drive I'm installing to before inserting the install disc??


Later::  I solved my problem by burning the ISO at x1  instead of x16   now having different issues, and don't want to derail this
            thread any more.  Thanks for your help!

---

### Post by spcwingo on 2010-01-28
> **krosby said:**
> Do I need to partition the drive I'm installing to before inserting the install disc??

No, all that can be done from within the installer.

---

### Post by biigg on 2010-01-28
**Thank you for getting back to me. More than likely would use the LTS. You suggested going ****to the 9.04, can you give me a link to that page which will suit my computer , I am running with 128mb ram, 32 bit system, and a 20g hdd, If you need more info than that let me know and I will get back to you asap after you respond to this. The computer is a HP Pavilion laptop, I have CD-ROM and floppy drive in it too. But to use the USB it does not recognize it until the OS is installed. Let me know if you need more, I will get back to you. Thanks**

---

### Post by spcwingo on 2010-01-28
Does it have a network adapter?  The reason I ask is the mini installer only has enough on the disk to get the system booted.  Everything else that is installed is pulled in from the repositories so an internet connection is vital for this method of installation.

I also seen one other thing against you for running Ubuntu speedily...the 128 RAM.  If you have (or can get your hands on) more RAM it would help you out immensely.

Anyways, here is a link to the Hardy (8.04) mini ISO:

[http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso]("http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/installer-i386/current/images/netboot/mini.iso")

If you need info on burning the image to disk, look here:

[https://help.ubuntu.com/community/BurningIsoHowto]("https://help.ubuntu.com/community/BurningIsoHowto")

After you burn the CD and boot from it (make sure that booting from the CD before the HD is enabled in BIOS) and follow the on-screen instructions for installation of a command-line-only installation.

After that, reboot your comp and login on the terminal (you will not get any feedback on-screen while typing your password...this is normal).  After login enter this command:

```
sudo apt-get install ubuntu-desktop && sudo apt-get clean
```

When it gets done doing it's thing, enter this command:

```
sudo reboot
```

Welcome to your new Ubuntu desktop!

---

### Post by biigg on 2010-01-31
[spcwingo]("http://ubuntuforums.org/member.php?u=710414"), I will have to try and get more memory for the computer I am working on, and then try the tings you have given me help with. I cant connect to the net to get things setup the way they should be.
So till I find another memory card for it will have to set. It's not going the way I thought it might. Oh and by the way I have both a 10/100 Ethernet converter and a bus card..... Zonet zew 1501 model. The other problem I have with that is that for security it asks for wep and the network in my house is set at wpa, don't know if you have any solutions for that but will keep trying. Thanks much....and will keep in touch.

---

