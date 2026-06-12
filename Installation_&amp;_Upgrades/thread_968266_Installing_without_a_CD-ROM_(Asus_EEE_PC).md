---
title: "Installing without a CD-ROM (Asus EEE PC)"
date: 2008-11-02
forum: Installation &amp; Upgrades
---

### Post by mschira on 2008-11-02
Hi 
I am trying to install Ubuntu on my Asus eee 1000H.

Using the standard procedure doesn't work, since I got no CD-ROM.
(And by the way I consider it highly not up to data for canonical not having thoroughly prepared for such situations)

My most favorite option would be installing Ubuntu on a 16Gb SD card, my second favorite option is installing it on the harddrive. (I have a 250 GB harddrive in the eee PC)

I found some potential instructions
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
but somehow this doesn't work.
I downloaded the the .iso for the normal installation on 8.10, I downloaded the live USB creator and copied the files to the SD card. Now I tried to boot from the Card but it didn't quite work.
It started the boot loader from the SD card but then it failed to boot Ubuntu. (I think it should start to boot a live system form here, but I am not sure, the instructions don't tell.

Any suggestions? Maybe the card is to big for the boot loader assuming a FAT filesystem?
I don't know. I don't even get error messages...
M.

---

### Post by logos34 on 2008-11-02
Try Unetbootin live usb:

[http://unetbootin.sourceforge.net/#requirements](http://unetbootin.sourceforge.net/#requirements)
[http://unetbootin.wiki.sourceforge.net/guide](http://unetbootin.wiki.sourceforge.net/guide)

good luck

---

### Post by mschira on 2008-11-02
Well, that is the tool I tried.
I choose the Ubuntu 8.10 iso tell unetbootin to copy it to D:\ which is the SD card press O.K. and it seems to work all fine, does something and then asks me to reboot, so I reboot.
When I reboot I end with a gray unetbootin screen with as simple menu, offering 1:boot, 2:help 3; Setup [OEM].

and it is counting down seconds till it wants to boot. Well after it has counted down it starts with 10 again and counts down and again and again...

When I press return to boot it gets back to 10 right away, so I think it tries to boot (or does??? it quite fast i.e. instant). and then get's back to the boring menue.
Choosing help or OEM doesn't change a thing. When i press TAB i get some place where I can change some kernel boot options - of which I have no clue.

Back booting windows again I find that there are only 21 Mb used on the flash drive - hardly enough for the complete Ubuntu. 

Not sure If am missing something or doing wrong - but this is either not straightforward by any means or it just doesn't work. (and does not create error messages either!)
M.
P.S. this is not the first Linux I install - I have a running server with Suse 10.3 happily supporting 10 people doing professional work on it, so I shouldn't be to dumb  - I would guess.

---

