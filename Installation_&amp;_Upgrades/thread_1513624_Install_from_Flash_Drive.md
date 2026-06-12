---
title: "Install from Flash Drive"
date: 2010-06-19
forum: Installation &amp; Upgrades
---

### Post by jchase45 on 2010-06-19
I wanted to reinstall Ubuntu , so I took my iso of Ubuntu desktop 10.4 LTS and followed these directions 

[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

Under create usb stick and ubuntu , but when I went to boot from it after restarting, it hung for like 10 mins at the Ubuntu Splash screen. I'm not sure what is wrong , it worked fine when I installed it on windows

---

### Post by oldfred on 2010-06-19
I had to do this, (I actually used Flash with a grub boot loader and edited the boot line the same way as first boot):
boot from the cd, press F6 and then select the nomodeset option.
then
On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

After I installed nvidia driver (default from pop up) then it has worked without issue.
gksudo nvidia-settings
Or it should be in System>administration>Hardware drivers.

---

### Post by jchase45 on 2010-06-19
but Im not usign a CD

---

### Post by oldfred on 2010-06-19
the flash drive boots the same as a CD. I just edited the grub line.

---

### Post by jchase45 on 2010-06-19
I have no idea what a grub line is or how I would edit it

isnt there a way to install Ubuntu from within Ubuntu?

---

### Post by darkod on 2010-06-19
OK, lets be direct and short.

Are you able to boot with the usb stick you created and start the install process or it hangs before that? Because I didn't understand.

---

### Post by jchase45 on 2010-06-19
Well this time I tried hitting F6 , hit F4 and chose nomodeset , then chose to Install ubuntu , and it did the same thing , it acted like it was loading and just kept loading forever , I hit any F key during the hang and it  showed me this 

GLib : Get Pwvider(): failded due to unknown user ID

---

### Post by darkod on 2010-06-19
I think you have a bad ISO file. Can you download a new ISO file, and it's better (and usually faster) to download with torrent, because it checks for corruption during download.

Get the 32bit or 64bit torrent file here, and then use your favorite torrent program:
[http://releases.ubuntu.com/lucid/](http://releases.ubuntu.com/lucid/)

The files are at the bottom of the screen. Get the .torrent file.

Then create new usb stick and try again.

---

### Post by jchase45 on 2010-06-19
Wont i need to verify my hash if I dl it from a torrent?

---

### Post by darkod on 2010-06-19
> **jchase45 said:**
> Wont i need to verify my hash if I dl it from a torrent?

You can but usually the software itself is checking for corruption during download.

Otherwise I have no idea what it going on if that's not the issue. But that message about unknown user ID sounds like bad image I guess.

---

### Post by jchase45 on 2010-06-19
It wouldn't let me set any special options , but it did let me reinstall , thank you! :p

---

