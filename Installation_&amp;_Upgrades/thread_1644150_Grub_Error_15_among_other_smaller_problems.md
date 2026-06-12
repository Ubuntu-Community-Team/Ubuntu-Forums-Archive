---
title: "Grub Error 15 among other smaller problems"
date: 2010-12-12
forum: Installation &amp; Upgrades
---

### Post by Dutch70 on 2010-12-12
Hi, I've been trying to fix this problem on my own for several days. just keeps getting worse. At my wits end now.

UPGRADE...
Tried upgrading from 8.04 lts to 10.04 and it wouldn't work b/c of too many mods to my 8.04 system???. So I tried a fresh install per usb stick. System kept locking up during install, as well as when I run it from the usb, I've since learned. 
graphics card??? probably.

CURRENT PROBLEM...
The problem I'm having now is I can't log into windows either per the grub loading please wait..
error 15.

ATTEMPS TO FIX...
I've googled & searched the forums & everything I've tried doesn't work, there were some possible solutions that I don't understand how to do. can't get to a terminal to check or modify anything. Hitting "e" at the boot menu does nothing. I don't know how to do anything from here!!! 

SYSTEM...
Compaq Presario SR5350, 2GB RAM, Dual Core Proc 2150MHz.
Dual boot w/Vista, HDD is partitioned separately with Root, Home & swap. 
Also, sda5 or / has been formatted to ext4, still using grub 1.5.

Thank you for taking the time to read my post. :)
And for any help you may offer!!!

---

### Post by Quackers on 2010-12-12
Please boot from the Ubuntu Live cd/usb and select "try ubuntu" then when the desktop is loaded make sure you have an internet connection and go to the site below and download the boot script to your DESKTOP and then open up a terminal (Applications > Accessories > terminal) and run
```

sudo bash ~/Desktop/boot_info_script*.sh
```

This will produce a results.txt file on your desktop. Please copy the contents of that file and paste them in your next post between CODE tags. For CODE tags click on New Reply (not quick reply)and then click on the # symbol in the toolbar.
This will give a full overview of your current system.
Thanks.

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

---

### Post by Dutch70 on 2010-12-12
Thank you, but I don't think I can do that since 10.04 locks up anywhere from 10 seconds to 60 seconds after I log onto it. However I will give it a shot!

---

### Post by Quackers on 2010-12-12
Use the Live cd or Live usb

---

### Post by Dutch70 on 2010-12-12
I was using live usb with 10.04, seems that I've deleted 10.04 from the usb. Is there an older version of ubuntu that I can use with the usb that may work on my pc? I thought 9.04 worked with a live usb, but wasn't exactly sure which file to download. My plan was to install it & hope it fixed the grub error.

Edit: looking for i386 iso for use with usb...all I can find is for a cd, unfortunately my 
cdrom isn't working.

---

### Post by Quackers on 2010-12-12
I believe that an error 15 is usually because grub legacy (installed with 8.04) doesn't get on too well with grub2 (installed with 10.04). It may be the case that purging grub and re-installing grub2 will solve your problem. But we would need to know what partition 10.04 is on. That's where the boot script comes in.
That is the best I can come up with. Maybe somebody else can come up with another plan :-)

---

### Post by Dutch70 on 2010-12-12
> **Quackers said:**
> I believe that an error 15 is usually because grub legacy (installed with 8.04) doesn't get on too well with grub2 (installed with 10.04). It may be the case that purging grub and re-installing grub2 will solve your problem. **But we would need to know what partition 10.04 is on**. That's where the boot script comes in.
That is the best I can come up with. Maybe somebody else can come up with another plan :-)

"/" is on /dev/sda5 :D

---

### Post by Quackers on 2010-12-12
I'm sorry I think I have misled you.
In order to purge grub and re-install grub2 it would be necessary to be in a Live cd/usb environment (in the case that Ubuntu won't boot).
That's where the commands would be issued from.

---

### Post by Dutch70 on 2010-12-12
I'm sure it was me who missed you :) But I am currently downloading the 9.04 alternate iso.torrent. Then I may be able to get on the live usb without locking up.
per these 2 sites...
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/]("http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/")
AND...
[http://releases.ubuntu.com/jaunty/]("http://releases.ubuntu.com/jaunty/") ...for torrent download.

 it's gonna take about 30 min though.
 
I really appreciate all your help. Will you be around for a while? If so, I'll try to get you the info you 1st requested.

---

### Post by Quackers on 2010-12-12
Sadly 9.04 will only replace the grub legacy version of grub, not grub2.
If it is your wish to just re-install 9.04 that would be ok.

---

### Post by Quackers on 2010-12-12
You will be able to fix Windows with a Windows repair disc. It would over-write grub.

---

### Post by Dutch70 on 2010-12-12
Thanks Quackers. That's good to know b/c 9.04 iso.torrent wouldn't install from the usb. It would go so far, then say I didn't have a cd in the cdrom. I'm gonna try 10.10 first.

---

### Post by oldfred on 2010-12-13
Note that the alternate install CDs are not liveCDs.

What video card do you have.  9.10 has been the only one that I have not had to edit grub or use f6 on install boot to set video parameter.

I had to do this with my Nvidia 9600GT:
boot from the cd, press F6 and then select the nomodeset option.
I edited my grub.cfg as I use grub to boot ISO, in syslinux.cfg or text.cfg
then
On first boot after install, press e on getting the GRUB bootloader. 
Hold shift from BIOS boot to get menu if only one system installed.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

Some other settings:
[http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/](http://ubuntu-tutorials.com/2010/05/06/ubuntu-10-04-lucid-blank-screen-at-startup-workaround/)
* Older Intel video card: i915.modeset=1 or i915.modeset=0
* nVidia: nomodeset
* Generic: xforcevesa or nouveau.modeset=0
* Radeon: radeon.modeset=0

---

### Post by Dutch70 on 2010-12-13
Thanks Oldfred. It's a realtek video card I believe. I don't have any cd's right now, and probably won't for a few days. I'm using a usb stick and with 10.10, putting it on a usb from windows and this website. [http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download") 
I'm getting "Data error in casper\filesystem.squashfs. file is broken. While trying to put it on the usb. 

this is from a working windows pc. not sure if it's a problem with the download or what. I

I would really have to study on the other info you gave me, which I don't mind doing, but I don't know what most of that stuff is right now. :lol:

---

### Post by oldfred on 2010-12-13
There are some issues with some versions of the USB creator.

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)
**8.04 Hardy:** Unfortunately, there is a [bug]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192") in the versions of casper in Hardy that cause the persistent partition to not be mounted on boot.  There is a [workaround]("https://bugs.launchpad.net/ubuntu/+source/casper/+bug/219192/comments/3") available, and you can download a [replacement initrd.gz]("http://launchpadlibrarian.net/15990491/initrd.gz.8.04.1.casper.fixed") for 8.04.1 (place in casper directory on first partition of USB key). 

Some other errors depending on how you installed it:
syslinux errors help/enter works:
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/617779)
Delete ui in syslinux.cfg
[https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382](https://bugs.launchpad.net/ubuntu/+source/syslinux/+bug/608382)

---

### Post by Dutch70 on 2010-12-13
I hate to back up on you Oldfred, but I thought I'd try some of the info you previously gave me for the video card and try 10.04 again, which is what I really want. I was able to use it from the usb stick before, but now, I'm getting this response...

```
Syslinux 4.02 Copyright EDD etc.
unknown keyword in configuration file... gfxboot
vesamenu.c32: not a COM32R Image
boot:
```

Then it keeps saying this part over & over...

```
vesamenu.c32: not a COM32R Image
boot:
```

from my research, it seems to be happening b/c I first tried to use 10.10, and the version 
of Syslinux on the box differs from what's on the usb. 

Still researching!!!

---

### Post by oldfred on 2010-12-13
It not that what the two bug links, I gave you abpve. They have some work arounds in the discussion of the bugs. One is type help then press enter. The other was remove the ui in a syslinux.cfg file. There may be more as I have not thoroughly reviewed bug reports.

---

### Post by Dutch70 on 2010-12-13
> **oldfred said:**
> It not that what the two bug links, I gave you abpve. They have some work arounds in the discussion of the bugs. One is type help then press enter. The other was remove the ui in a syslinux.cfg file. There may be more as I have not thoroughly reviewed bug reports.

Yes I checked them closely, didn't find a "ui" in my syslinux.cfg file.

However, I did get it fixed, just now :P. You'll never believe how.

The only thing I did was log into Ubuntu 10.04 installed into windows via Wubi and installed 10.04 onto my usb with Ubuntu as opposed to windows. (On a different pc of course) 


I didn't lose any of my files and my pc is running great with the exception of the graphics/video card incompatibility issue with 10.04. 


I'm gonna do some research on that and start another thread if I don't get it fixed. 


Thanks to you Oldfred & Quackers for all your help!!! I probably would have given up & started over if it weren't for the two of you.


Can you not give beans anymore? 

This thread is solved, hope it helps someone else.

---

### Post by Quackers on 2010-12-13
Nice one :-)

---

