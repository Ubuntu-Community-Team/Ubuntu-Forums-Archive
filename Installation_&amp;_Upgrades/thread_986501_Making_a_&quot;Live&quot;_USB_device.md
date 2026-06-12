---
title: "Making a &quot;Live&quot; USB device"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by j.daniel on 2008-11-18
**Hello there,**

I have an idea that I want to try out and I wonder if you guys & gals have any pointer as to how to proceed:

I would like to make a "Live" USB device - i.e. memory stick or removable USB hard drive etc. Reason for this is that I want to try to use a computer which normally runs Windows to run Linux once in a while and I do not want to install Linux on its local hard drive.

So what I thought ought to be possible is to somehow install Ubuntu on some kind of USB device and then boot from it instead.

The reason I do not want to use a Live CD/DVD is that I would like to be able to add/remove applications - that's why I think that a USB device would be the best choice here.

Any ideas out there?

Cheers
/ Daniel

---

### Post by snova on 2008-11-18
It's very much possible. If you're using Gnome, it's System -> Administration -> Create bootable USB (or something like that).

You'll need to have the CD image available. I'm also uncertain whether you can install things to the drive afterwards...

I've created one myself, but I never booted it. I just wanted to see how it would work.

(Oh, and if you aren't using Gnome, it's in the usb-creator package and should be on the K menu somewhere.)

Edit: Oops, I hope you weren't trying to create it from Windows, I don't know how to do that... Wubi *might* be able to do it, but I've never used Wubi...

---

### Post by C.S.Cameron on 2008-11-18
From Windows you can use Unetbootin and the Ubuntu iso.


edit
UNetbootin

---

### Post by snova on 2008-11-18
Good idea, but it's called UNetbootin (typo).

I also found this: [HOWTO: Install Ubuntu without a CD using UNetbootin]("http://ubuntuforums.org/showthread.php?t=427540")

---

### Post by j.daniel on 2008-11-19
Thank you for the info! I can't see any "Create Bootable USB" in my System - Administration meny, but then I still run Ubuntu 8.04. Is it an 8.10 thing ? Or do I perhaps need some applications - I will do a search.

Still - I have some leads I will try out.

Thank you
/ Daniel

---

### Post by stanlavisbad on 2008-11-19
I found this recently, it works really well: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

What I would like to do though is to boot it up using a virtual machine like virtualbox. but i can't seem to find a program that will boot from a pen drive.

---

### Post by JamesGarry on 2008-11-19
hey,
There is an easy way to create a Live USB stick. Check following link that explains how to create a bootable openSUSE 11.0 USB stick.  [http://en.opensuse.org/Live_USB_stick](http://en.opensuse.org/Live_USB_stick)

---

### Post by j.daniel on 2008-11-19
Hi

Following up on some of your leads I found this one:

[https://wiki.ubuntu.com/LiveUsbPendrivePersistent](https://wiki.ubuntu.com/LiveUsbPendrivePersistent)

...seems to be a lot of interesting info there.

Cheers!
/ Daniel

---

### Post by C.S.Cameron on 2008-11-19
That's a good page for background, but a bit dated.
The usb-creator tool seems to work for 8.10 only.
Casper is a bit messed up in 8.04.1 and persistence does not work, (without tweaking).

---

