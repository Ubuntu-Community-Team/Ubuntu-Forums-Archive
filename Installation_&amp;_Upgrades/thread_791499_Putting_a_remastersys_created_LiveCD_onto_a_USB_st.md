---
title: "Putting a remastersys created LiveCD onto a USB stick"
date: 2008-05-12
forum: Installation &amp; Upgrades
---

### Post by John Read on 2008-05-12
Hi all,

I've used Remastersys to create a live DVD (800Mb+) so that I can copy my Ubuntu 8.04 installation (and extra packages I've added to it) to my friends' computers who do not have a broadband Internet connection.

It works a treat!

The hassle I have is some of my friends' computers only have CD drives.

I've been trying to set up a 2Gb USB stick and copy files from the DVD (that was created using Remastersys) to the USB stick. The idea being that I could boot my friends' computers from the USB stick and install from there. So far I have not been able to do this.

Any instructions on how to do this would be greatly appreciated.

Regards,

John R.

---

### Post by Partyboi2 on 2008-05-12
Maybe you could follow and modify this how-to ([http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html](http://www.ubuntugeek.com/how-to-install-ubuntu-linux-from-usb-stick.html))

---

### Post by John Read on 2008-05-14
hi Partyboi2,

Thanks a lot for the link to the HowTo. I'll try it too.

The hassle I'm having is that the ISO of Remastersys (when burnt to a DVD) has contents rather different to that of the Live Ubuntu CD that most tutorials describe.

I'll continue trying until I get there and then post a HowTo to help others trying to do the same thing. The time & hassle I would save if I could get it to work would be incredible.

Best regards,

John R.

---

### Post by Goll on 2008-12-26
No luck for me.

---

### Post by yurfader on 2009-06-30
I hope this would be helpful for someonelse. 

I had the same problems that you were facing, but I solved it installing UNetbootin and with that I installed the original ISO image from Ubuntu (Jaunty in my case).

Once I have the USB working with the original ISO, I create the custom image with remastersys. I extract the filesystem.squashfs file from the custom ISO file and copy the file to the casper folder on the USB unit. That file has the most important information of the custom distribution.

I think this is very straightforward, and won't need a lot of knowledge to make it.


:guitar:

---

### Post by itsjareds on 2009-09-18
I followed the last user's suggestion which unfortunately didn't work, but thankfully Jaunty has a built-in method (System > Admin. > USB Startup Disk Creator) to create a Live USB from an ISO source. I ran this program using the remastersys .iso as the source and it worked perfectly.

---

