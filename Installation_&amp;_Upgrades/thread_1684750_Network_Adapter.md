---
title: "Network Adapter"
date: 2011-02-09
forum: Installation &amp; Upgrades
---

### Post by Ihsan_Cingisiz on 2011-02-09
Hello,

I want to install Ubuntu on my system, but I want to ask
first for the driver for my 'Sitecom WL-142' 140g+ network
adapter because, if I install Ubuntu on my system, I don't
have access to the Internet and that will be a problem to
search for the driver. Does someone know the place where I
can download the driver for this adapter?

K. Regards,
I. C.

---

### Post by JoeFriday49 on 2011-02-09
Just boot from the CD and see if it works...  It should be fine...

---

### Post by Ihsan_Cingisiz on 2011-02-09
> **JoeFriday49 said:**
> Just boot from the CD and see if it works...  It should be fine...

Thanks for your reply, but it works because I have Windows installed with the driver. I tried that a while ago, so I
thought: "Yes, it's working, let's format my whole PC and
install Ubuntu...". After I did that, my adapter didn't work
anymore. So I need the drivers for it. Can I do this with a
long Ethernet cable to downstairs and connect to my router?
If i got connected, what should I do next? How can I make 
Ubuntu detect what kind of adapter I'm using and how do I 
install the driver then?

PS:
Why can't I find my USB on this list, it that a problem?:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

Double PS:
And when I tried with the boot thing, it was not using this adapter
but using another adapter.

---

### Post by Ihsan_Cingisiz on 2011-02-10
> **Ihsan_Cingisiz said:**
> Thanks for your reply, but it works because I have Windows installed with the driver. I tried that a while ago, so I
thought: "Yes, it's working, let's format my whole PC and
install Ubuntu...". After I did that, my adapter didn't work
anymore. So I need the drivers for it. Can I do this with a
long Ethernet cable to downstairs and connect to my router?
If i got connected, what should I do next? How can I make 
Ubuntu detect what kind of adapter I'm using and how do I 
install the driver then?

PS:
Why can't I find my USB on this list, it that a problem?:
[http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB](http://sourceforge.net/apps/mediawiki/ndiswrapper/index.php?title=Category:USB)

Double PS:
And when I tried with the boot thing, it was not using this adapter
but using another adapter.

* bump *

---

### Post by grahammechanical on 2011-02-10
err, how about using the other adapter? The one that you know works with Ubuntu.

Yes, you can use an ethernet cable to connect. Then go to System>Administration>Additional Drivers. See if one is listed for your USB adapter. If it is activate it.

Your USB adapter is not on that list because it might be out of date. It does not mean that your adapter will not work. It means we try out Ubuntu with a live CD first, to confirm that our hardware is recognized.

Regards.

---

### Post by TBABill on 2011-02-10
Can you post the output of ```
lsusb
``` while running the live CD? We need to know what chipset it has so we can know if it needs a proprietary driver or just configuration with drivers in the kernel. I assume this is a USB device. If it's internal, then use ```
lspci
``` instead.
 
And while you have the live CD running, can you also ```
sudo lshw -C network
``` and paste that back as well? You may have to manually type some of this in order to do this since you can't get online with that machine while in Ubuntu, and if it's too much to type then just do the first code and we can go from there.

---

### Post by Ihsan_Cingisiz on 2011-02-10
> **TBABill said:**
> Can you post the output of ```
lsusb
``` while running the live CD? We need to know what chipset it has so we can know if it needs a proprietary driver or just configuration with drivers in the kernel. I assume this is a USB device. If it's internal, then use ```
lspci
``` instead.
 
And while you have the live CD running, can you also ```
sudo lshw -C network
``` and paste that back as well? You may have to manually type some of this in order to do this since you can't get online with that machine while in Ubuntu, and if it's too much to type then just do the first code and we can go from there.

Thanks for the information.
I tried 'lsusb' with my Sitecom WL-142 but Ubuntu was unable
to detect the adapter. And I had another Network Adapter, a
U.S. Robotics, I connected it to the PC and did again 'lsusb'
and Bingo! It was able to detect the adapter. The output of
'lsusb' in terminal is:

---
Bus 001 Device 007: ID 0baf:0118 U.S. Robotics U5 802.11g Adapter
--

And this is on the label of the Robotics Adapter:

-----
U.S. Robotics
Model: USR805422
FCC ID: RAXWN4501G3
IC: 4711A-WN4501G3

S/N: 2WB4E9NF2241

U.S. Robotics 802.11g 54Mbps USB Adapter(CR)
Assembled in China(9) GZ 146000026600J R01 EL
-----

I hope this info is enough to get helped by you! :D

Thanks!

K. Regards,
I. C.

---

### Post by TBABill on 2011-02-10
See here [http://kubuntuforums.net/forums/index.php?topic=3111943.0](http://kubuntuforums.net/forums/index.php?topic=3111943.0)
 
Looks like first you need to install non free firmware ```
sudo apt-get install linux-firmware-nonfree
``` 
Then restart and see if it works. This is for the US Robotics device, not the other.

---

### Post by Ihsan_Cingisiz on 2011-02-10
> **TBABill said:**
> See here [http://kubuntuforums.net/forums/index.php?topic=3111943.0](http://kubuntuforums.net/forums/index.php?topic=3111943.0)
 
Looks like first you need to install non free firmware ```
sudo apt-get install linux-firmware-nonfree
``` 
Then restart and see if it works. This is for the US Robotics device, not the other.

Thanks for the search! :)

But, I don't have access to the Internet, I can't even connect
my PC with the router because it's downstairs, it's a bit hard
to move my desktop to there. Do you have further information for
how to download the program, the non-free-thingy :D and put in
USB-Stick and install from there, or do you know a better way?

It's a bit hard for me, because i'm very new to Linux.

Again, really thanks for your help!

PS: Do I need to pay for the program, because the name is non-free..?

---

### Post by TBABill on 2011-02-10
Since the file is in a respository I'm not sure how you can get it without any access at all. You could save to a USB if you could download it somehow, but without the ability to get to it I'm not sure. Maybe someone can offer insight if they have faced that situation before.
 
The file is non-free, but that only means it is not open source. You do not pay for it. It is readily available to anyone but its source code is restricted and proprietary so it cannot be modified or supported by another party.
 
Best of luck getting the file. Worst case maybe you could move the desktop machine to the router or modem location long enough to install that, then move it back? I know that is a pain to do but I don't know how to get that file without at least one instance of Internet access so you can save it to a portable drive.

---

### Post by Ihsan_Cingisiz on 2011-02-10
> **TBABill said:**
> Since the file is in a respository I'm not sure how you can get it without any access at all. You could save to a USB if you could download it somehow, but without the ability to get to it I'm not sure. Maybe someone can offer insight if they have faced that situation before.
 
The file is non-free, but that only means it is not open source. You do not pay for it. It is readily available to anyone but its source code is restricted and proprietary so it cannot be modified or supported by another party.
 
Best of luck getting the file. Worst case maybe you could move the desktop machine to the router or modem location long enough to install that, then move it back? I know that is a pain to do but I don't know how to get that file without at least one instance of Internet access so you can save it to a portable drive.

I found this, and tried with the live CD but nothing happens, 
is that because of the CD or something else?

This is the link where i found the download:
[http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree](http://packages.ubuntu.com/lucid/all/linux-firmware-nonfree)

K. Regards

---

