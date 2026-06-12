---
title: "Network installation (Feisty)"
date: 2007-03-31
forum: Installation &amp; Upgrades
---

### Post by ELMIT on 2007-03-31
I have a Toshiba Portege 3440CT and want to make a network installation of the newest 7.04-beta-alternate.

tftp, dhcp got me to boot and has partitioned the hard disk, but now it stops that it cannot find a mirror. I tried: Taiwan (where I am), Hong Kong, Japan, USA, U.K. (archive.ubuntu.com) but without success.

None of the mirrors seems to have 7.04-beta.

I have a CD burned. Is there a way to get this CD somewhere on my web sever and use my "own site" as the mirror? I have not found the place where I can add my own mirror.
I tried to use:
[www.elmit.biz](www.elmit.biz) 
directory:
  /ubuntu/
  /ubuntu/feisty/
  /ubuntu/feisty/alternate/

but none of them worked!

BTW, after several mirrors I wanted to cancel it, but it loops to the same picture, ...


bye

Ronald

---

### Post by zvacet on 2007-03-31
I see that you have alternate iso and this maybe help you 
[http://ubuntuforums.org/showthread.php?t=316093&highlight=iso]("http://ubuntuforums.org/showthread.php?t=316093&highlight=iso")

---

### Post by ELMIT on 2007-04-02
I could not figure out how it could help me. I have no floppy either. Well, this computer has a floppy, but I have no other computer anymore which would have a floppy to create grub.


The installation ends with:

Configure the clock
Bad archive mirror
The specified Ubuntu archive mirror is either not available, or does not have a valid Release file on it. Please try a different mirror.


And that message comes up for any mirror, including "enter information manually"
[www.elmit.biz](www.elmit.biz)
/ubuntu/

I tried also 6.10 edgy and changed dhcpd.conf and mounted this iso.

I must do something wrong, but what?
I followed [https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)  (at least I came with that till step 7 "Yippee!"


bye

Ronald

---

### Post by ELMIT on 2007-04-06
I got now my CD/ROM to work. Was just a little switch to take the power from the computer.

When I boot from this PCMCIA CD/ROM it complaints that it needs a driver for the CD/ROM to continue. Somehow strange, since it booted from the CD so far. Anyway, how can I supply the driver?

bye

Ronald

---

### Post by ELMIT on 2007-04-10
I did now as you suggested, went earlier to the office, swapped hard disk to one of the office notebooks and installed and updated Ubuntu.

Now I have some minor problems. I hope you can help me.

When I booted up the Toshiba Protégé 3440 CT I got an error about "No screen defined". Deleting /etc/X11/xorg.conf   "fixed it" so far, that I can use it, but the 11" screen has now a 1" black frame around. Where / how can I get the picture over the entire screen?

Does anybody know, where I can get 128 MB RAM Mini-DIMM for that baby? I can only get 512M or 1G here, but the docs I read says only 128MB possible. Would be 512MB/1G just recognized as 128MB or do not work at all?

I don't have a manual nor a technical data sheet. Is the USB port really 2.0 ????

bye

Ronald

---

