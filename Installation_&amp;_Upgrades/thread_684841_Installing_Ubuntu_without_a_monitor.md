---
title: "Installing Ubuntu without a monitor"
date: 2008-02-01
forum: Installation &amp; Upgrades
---

### Post by rmanor on 2008-02-01
Hi,

I have a blank computer (no OS) connected to my network and I want to install Ubuntu on it.
The problem is that I don't have a monitor to attach to the computer (I only have a laptop).
The video card on the computer does have a tv output.

Is there anyway to install Ubuntu using the TV as monitor? or without a monitor at all (some kind of network installation) ?

thanks.

---

### Post by jrthom444 on 2008-02-01
Why can't you connect a monitor to it?

---

### Post by macstyle@freeshells.ch on 2008-02-01
Hi,

You can use the serial console...You need a nullmodem cable and 2 serial port (one on the linux pc and one in the other)

You have to use the following method with netinstall iso of ubuntu.

[http://www.debian-administration.org/articles/221](http://www.debian-administration.org/articles/221) (maybe you have to change the "linux" in some other check in a pc with monitor with f1 or f2 key)

boot the linux installation with appropriate command and on the other pc run putty on the with serial interface mode.

It's not simple to do I've done on debian but in ubuntu change something :)

I hope for your success

Bye

---

### Post by self-defence on 2008-02-01
Well you could try something radical. :) Keep in mind it's much more simple to get a monitor, but you can give this a shot anyway.
You get a software that can run virtual systems like VirtualBox you install it on your laptop and install any system you want to put on the pc without the monitor. Now when you have installed the system set it up so that it is accessible from the network (ssh,vnc,whatever) and I would suggest that you set up at the end a static IP address(so you know what IP to access later). When this is setup make an image of the virtual system, this you have to figure out how to do. You can use a bootable software like Clonezilla and try to copy the image to your disk via network or just figure a way how to dd the image out of the virtual disk file (this is something that would interest me to). Then when you have the image of your system just take out the hard drive of the pc without the monitor and then hook it up via USB or some kind of interface to your laptop and just trans fare the content of your image file onto the disk. Then just put the disk back and hope that it boots up.

I still think it's easier to find a monitor somewhere (if you were near me I'd give you one) and do it that way. But if you try something like the above please let me know how it went...

Best of luck and hope you get your system installed.

---

### Post by rmanor on 2008-02-01
> **jrthom444 said:**
> Why can't you connect a monitor to it?

I don't have one.

---

### Post by rmanor on 2008-02-01
> **macstyle@freeshells.ch said:**
> Hi,

You can use the serial console...You need a nullmodem cable and 2 serial port (one on the linux pc and one in the other)

You have to use the following method with netinstall iso of ubuntu.

[http://www.debian-administration.org/articles/221](http://www.debian-administration.org/articles/221) (maybe you have to change the "linux" in some other check in a pc with monitor with f1 or f2 key)

boot the linux installation with appropriate command and on the other pc run putty on the with serial interface mode.

It's not simple to do I've done on debian but in ubuntu change something :)

I hope for your success

Bye

I'll try reading it, thanks.

---

### Post by rmanor on 2008-02-01
> **self-defence said:**
> Well you could try something radical. :) Keep in mind it's much more simple to get a monitor, but you can give this a shot anyway.
You get a software that can run virtual systems like VirtualBox you install it on your laptop and install any system you want to put on the pc without the monitor. Now when you have installed the system set it up so that it is accessible from the network (ssh,vnc,whatever) and I would suggest that you set up at the end a static IP address(so you know what IP to access later). When this is setup make an image of the virtual system, this you have to figure out how to do. You can use a bootable software like Clonezilla and try to copy the image to your disk via network or just figure a way how to dd the image out of the virtual disk file (this is something that would interest me to). Then when you have the image of your system just take out the hard drive of the pc without the monitor and then hook it up via USB or some kind of interface to your laptop and just trans fare the content of your image file onto the disk. Then just put the disk back and hope that it boots up.

I still think it's easier to find a monitor somewhere (if you were near me I'd give you one) and do it that way. But if you try something like the above please let me know how it went...

Best of luck and hope you get your system installed.

Nice idea, but I don't have a usb interface for a harddrive. 
Maybe I'll just take the hard drive to someone and install the linux over there..
well, if you're in Israel somewhere... thanks anyway. :-)

---

### Post by self-defence on 2008-02-01
Sorry dude over 1000 miles away in Slovenia. :(
Well that you could do install on a different pc and just replug the disk. Should work only don't forge to setup networking and a way to connect to the system (ssh).

Bye

---

