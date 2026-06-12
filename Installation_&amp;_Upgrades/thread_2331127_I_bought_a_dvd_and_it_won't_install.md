---
title: "I bought a dvd and it won't install"
date: 2016-07-18
forum: Installation &amp; Upgrades
---

### Post by bklark on 2016-07-18
Ok so I have a laptop that I just bought a new hard drive for, blank, and I actually bought an Ubuntu disk (14.04) because the last five images I downloaded didn't work. So I was excited because I thought surely now it will work, but it doesn't. This is what I get:

I get a simple ui called xboot DVD with options to boot from hard drive first, second and third are Ubuntu 14.04 32 and 64 bit respectively. Fourth is help. There seems to be no installation program.

While trying either of the Ubuntu boots, I get either a command prompt where I know not what to do, or two lines asking for and getting some kind of kernel permission or something and getting it. That's all it does. Is this just a disk or do I need to learn something? All the disks I've burned trying to get this seem to automatically install, and so the printed instructions tell me this one will too

---

### Post by QIII on 2016-07-18
There is no reason to believe that media bought from a third party is any better than the official images.  From whom did you buy this media?  Do you know it to contain an unsullied image?

What, exactly, did not work with the official images?  Specifics are necessary.  What errors or messages did you get?  Exact text is important.

What are the hardware specs of your laptop?

---

### Post by Bucky Ball on 2016-07-18
Welcome. Yes, I think we should try and help you install from the official image downloaded from the official site. There is absolutely no knowing how the kernel has been tweaked by a third-party (Frankenstein's monster we have no idea about) so unless you bought it from Canonical ...

So, +1 to all of what QIII said, and

[quote=QIII]What, exactly, did not work with the official images? Specifics are necessary. What errors or messages did you get? Exact text is important.

What are the hardware specs of your laptop?[/quote]

If you want an unsullied image, you've already got one if you downloaded the ISO from the Canonical site. And I advise you start with 16.04 LTS. It came out in April and has the longest support (April 2021).

If you're ever having issues or need answers and can't find them on the net, don't hesitate to ask here. It can save a _*lot*_ of time. :)

---

### Post by Geoffrey_Arndt on 2016-07-18
bklark . . to clarify a bit, please note:

>   There is no installation program but there is an iso image that contains all the required packages (programs & support files).  
>   The iso must be correctly burned to either a DVD or a usb flash-device . . . this is not the same as "copying" the iso file from the download directory to the dvd or device.
>   The PC must be configured to allow the DVD or usb flash-device to boot (instead of booting from the hard drive).    This is done via editing the bios/uefi firmware to change boot order or via special one time boot commands

If all three things above are done correctly, the PC will boot from the dvd or usb device into a "Live" OS that provides two choices . . try Ubuntu or install Ubuntu.

Besides advising of the source of your install media, perhaps a screen-grab of the top-level directories will help us to understand if it is what you need.

---

### Post by QIII on 2016-07-19
bklark --

If my answer was a bit curt, please forgive me.  I was sitting next to my wife while she was driving the last leg of a four day road trip -- and I was on my cell phone.

We are asking a lot of questions because we want to have the best set of information we can get.  It is frustrating for both the person seeking help and those trying to give it when those giving support are working in the dark.

We are not trying to be difficult.  Rather, we are trying to be sure we can help.

---

### Post by Bucky Ball on 2016-07-19
> **QIII said:**
> We are not trying to be difficult.  Rather, we are trying to be sure we can help.

And once again, +1. No one wants to shoot in the dark as they might hit the wrong target and then we'll all be more confused! :)

---

