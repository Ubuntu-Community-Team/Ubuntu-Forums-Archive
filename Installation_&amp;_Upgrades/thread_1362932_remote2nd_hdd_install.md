---
title: "remote/2nd hdd install"
date: 2009-12-23
forum: Installation &amp; Upgrades
---

### Post by dvb on 2009-12-23
Hello everyone, I am new to the forum and to Ubuntu, but have been playing for a little while.
I am trying to install unr on my photoframe built from an old laptop. (mainly due to the fact that windows keeps corrupting itself on unexpected power down)
I find that I cannot do this on the laptop for a couple of reasons that I am still investigating but the main one is that I get a blank screen for the install so cannot see what is going on.

My question is
How can I install unr onto the photoframes hdd whilst it is connected to my windows laptop via a usb adaptor without changing the laptop in any way. I can then reinstall the hdd into the photoframe.
The photoframe mobo does not support usb boot otherwise that would have been my preferred route

Hopefully I have been the first to ask this, but if not a gentle pointer to a previous thread would be welcome.
Many thanks
David

---

### Post by audiomick on 2009-12-23
Hallo.

I have never done anything even remotely like this, but it should be possible.

You need to be really sure which HDD is which!!

If you run the installer and choose manual partitioning, you will be able to choose to install to the drive you want.

The installed grub will likely have an entry for the os in the laptop, and you will need to take care to write the grub to the appropriate HDD, or it will overwrite your windows mbr, I think. As far as I know, there is an option near the end of the install for this.

A safer and probably simpler route would be to use a desktop, and unplug the HDD from it before you start.

---

### Post by dvb on 2009-12-23
Hi Michael
Thanks for your very swift reponse.
I had not thought of the desktop method, I could disconnect both hdd's, boot from the Ubuntu cd and install. 
Many thanks for that, its amazing how much effort one puts in to do something like this and then someone comes along with a simple solution. Thanks Michael and thanks to forums like this.
I will try tomorrow and repost my results.
Regards
David

---

