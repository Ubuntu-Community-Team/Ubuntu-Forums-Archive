---
title: "portable installation to USB hard disk."
date: 2007-06-07
forum: Installation &amp; Upgrades
---

### Post by decoherence on 2007-06-07
Hello Forum!

I've installed Feisty on an external USB hard drive with the intention to move it from computer to computer.

The installation went fine, except for an md5sum mismatch on the grub package. I couldn't find a reference md5sum for the ISO at [http://www.ubuntu.com/getubuntu/downloading](http://www.ubuntu.com/getubuntu/downloading) ... is it somewhere else? Anyway, using lilo for now...

Since I'm going to boot this from different computers with varying bits of hardware, I'd like to use the vesa driver for video. It doesn't need to be fast, it just has to work. Unfortunately I can't for the life of me get it to work. The autodetected i810 driver works fine, but no matter what settings I give vesa it always complains that it can't find a matching mode. There's an unconfirmed (and informationally-challenged) bug report against Xorg 7.1 in Edgy that sounds like it could be this... maybe... sorta... anybody confirm?

Can anyone give me any advice on the best way to do this? Would it be better to copy the liveCD on to the disk? What pitfalls would I have to watch out for there? (mounting as read only, etc) Or, is there a way to get X auto-detection on a regular installation? (using only free drivers, of course)

Anybody else doing this? It doesn't HAVE to be with Ubuntu, though I do prefer apt-based distros to those OTHERS...

thanks,

---

### Post by Hugh Nano on 2007-06-07
> **decoherence said:**
> I've installed Feisty on an external USB hard drive with the intention to move it from computer to computer.

You did? I've been trying to do this for over a week now and can't seem to get it to work! Any tips you could offer? I've used the live CD to install to the external HDD (both Ubuntu and Xubuntu), but can't seem to get my Inspiron 6000 to boot from the drive - despite the fact that the BIOS supports booting from USB.

---

### Post by decoherence on 2007-06-08
Not sure what I can do to help... all I did was unplug the internal drive to be mighty sure it's MBR didn't get written to. The only glitch for me was the md5 mismatch while trying to install grub, so I'm using lilo instead. Other than that I didn't do anything special. I press F12 at boot to bring up a boot device list and select "USB Flash Device" (even though it's a hard drive.) Also, I used the alternate, text mode installer instead of the livecd -- not sure if that'd make a difference.

---

