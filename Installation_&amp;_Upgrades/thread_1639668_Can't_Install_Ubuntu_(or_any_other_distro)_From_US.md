---
title: "Can't Install Ubuntu (or any other distro) From USB"
date: 2010-12-07
forum: Installation &amp; Upgrades
---

### Post by AmiableAdder on 2010-12-07
I've tried Unetbootin, PendriveLinux, Linux Live USB Creator, Universal Usb Installer, and usb_creator.exe, and for some reason none of them work.

For distro's I've tried Ubuntu 10.10, 10.04, 10.10 Netbook, Crunchbang 9.04, Fedora 13, Fedora 14, and Fedora lxde.


When my computer starts it just goes to a black screen with a flashing white underscore in the top left (does this on both my netbook and my main comp, no matter which installer or distro i try).

I put another post on about the same thing a while ago and it never really got solved, but I decided to just use Wubi. Now I don't even use windows on my netbook because it's too cumbersome, and I'd like to install Ubuntu (or another distro, but preferably Ubuntu) as the main operating system so I don't have to keep selecting what to boot into and to increase system performance.

I've looked up ways to turn the wubi install into a native install, and from reading a bunch of them it seems like none of them are 100% sure to work. I'd prefer to just reinstall linux, considering it'll be on a netbook and the only thing I really use it for is internet and music (which I already have backed up on an external hard drive and don't mind transfering)without having to buy an external cd drive (i was considering it because cd's seem to work fine, but I probably wouldn't use it for anything except installing Ubuntu, and I don't wanna pay $70-$100 to install a free OS  :/  ).

Are there any special hints that aren't in the instructions? Like something you have to do after you install it to the USB? I've tried so many different things and the only thing I could think of is maybe rebooting directly after installing it to the USB. I've been using my main comp to download and install stuff because it runs faster, so after it installs to the USB I just unplug it and put it in my netbook and boot it up (I assume since the iso is from a live cd it should work fine that way, but for some reason it's not).


*EDIT* Tried running wubi from my flash drive. I chose the Demo and Full Install Later option, and it just goes to the black screen when it reboots.

---

### Post by oldfred on 2010-12-07
HOWTO: migrate wubi install to partition - bcbc 
[http://ubuntuforums.org/showthread.php?t=1519354](http://ubuntuforums.org/showthread.php?t=1519354)

What video card do you have. My computer would just go to  a black screen sleep mode, but USB was still flashing so install was working. It is a video issue.

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed Nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by AmiableAdder on 2010-12-07
My main has an nvidia geforce gtx 260m, and my netbook has an Intel GMA 950. I noticed my usb also flashes like it's trying to do something even though nothing is happening.

I looked at the instructions for the graphics fix, but the problem for me is in the first step. I can't even get to the install screen :( it basically just goes straight to the black screen with the white underscore.

I think I'll try migrating wubi for now and see how that works out. 

Thanks for the links.

---

### Post by Quackers on 2010-12-07
When you are booting up the Ubuntu Live cd/usb tap the F6 key and you will get options, like oldfred suggested.

---

### Post by AmiableAdder on 2010-12-08
It doesn't boot the Live USB, it just goes to a black screen with a white underscore. When I press F6 it just beeps :-(

---

### Post by Quackers on 2010-12-08
Do you ever get to a purple screen with Ubuntu written in the middle?

---

### Post by AmiableAdder on 2010-12-08
No, just the Samsung screen on startup, then black.

It acts like the bootlader isn't on the usb, but i checked it and it is. If that was the case I think another installer would work at least.

Is there a certain format my usb has to be? I've tried FAT32 and NTFS.

---

### Post by Quackers on 2010-12-08
I have no experience in booting a live usb, but I suspect there is something wrong with yours if it's not working on 2 different computers. AFAIK they are usually fat32 format. Again, afaik, the downloaded .iso file must be burned as an image, not a normal file burn. Unetbootin has worked for many others. It may be wise if you could go back over how you made the usb image and see if a step got missed.
On the other hand, I could be barkingup the wrong tree :-)

---

### Post by AmiableAdder on 2010-12-08
I know it's not something wrong with my usb drive because I've gotten it to boot before (when I first started doing this, I tried fedora, but I couldn't get my wireless drivers to work, so I tried Ubuntu and the only problem was it froze during installation, then it just started doing the black screen thing after trying a few different distros). I also completely erase and format the usb every time after trying to get it to work, so there isn't any leftover stuff on it that shouldn't be there.

I've looked up a lot of different directions and they basically just say insert usb, start program (Unetbootin, pendrivelinux, etc), select distro to be downloaded and installed or iso if you already have one downloaded, click ok.

I've looked around for solutions a lot too, but it seems like most people just have problems installing, not getting it to boot in the first place.

*EDIT*: Got Jolicloud to work, but still trying to get Ubuntu 10.04 or Debian Lenny because I don't have wifi access.

---

### Post by AmiableAdder on 2010-12-12
I got it ubuntu to boot now. For whatever reason it decided to work.

Now I have a new problem :/

I checked disk for errors and nothing was wrong, but when I try to install or try ubuntu without install it says "Can not mount /dev/loop1 on /cow".

Googling now :P

*EDIT*: Used usb_creator and chose the "Discarded on shutdown, unless you have saved them elsewhere" option and that worked.

---

