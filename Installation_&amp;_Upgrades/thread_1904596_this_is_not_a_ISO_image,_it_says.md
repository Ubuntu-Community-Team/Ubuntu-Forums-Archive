---
title: "this is not a ISO image, it says"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by abelito8 on 2012-01-05
Hi there, I am unable to install anything on my Asus EEE (12')

I have created dozens of USB start-up, with different systems (ubuntu, mint, debian) and every time it does not read it

I have used usb-startup gtk and kde, as well as unetbootin

...anyone had a similar problem?

---

### Post by carl4926 on 2012-01-05
No
My Eeepc works fine

With Ubuntu I used Unetbootin

You should be hitting Esc at the BIOS screen to have it offer the boot device...Yes?

---

### Post by Togras on 2012-01-05
you put your usb as first in boot options?
this works not fine with all sticks, in general i advise to use the additional boot menu you have to look which button you have to press your this then it should work...

---

### Post by abelito8 on 2012-01-05
yes, this is the message I get when I "force" the computer to boot from the USB instead of the hard disk. My bios comes with F2 (not Esc) and I exclude any other device but the USB

---

### Post by carl4926 on 2012-01-05
> I have created dozens of USB start-up

Can you just confirm you are writing a .iso with unetbootin of the .iso _**you downloaded **_from
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Try formatting the USB

Are you working from Linux or Windows

Does the Eeepc have a fast boot partition ?
Or did you like me wipe your HD

---

### Post by abelito8 on 2012-01-05
yes I was writing ISO images

from Linux

actually the only time it worked and I could install a Debian version the USB had been created from a Windows system (humiliating...) 

otherwise it never worked (and I am actually surprised that it worked the first time...)

I still have ubuntu on it but I was trying to install another version on the free space because I was not happy with the way 11.10 was working on that computer

---

### Post by carl4926 on 2012-01-05
If you look at the file system of the USB you have written.
This is what I see:
[http://paste.opensuse.org/64794991](http://paste.opensuse.org/64794991)

Do you see the same?

---

### Post by abelito8 on 2012-01-14
This is what I see, not really the same

---

### Post by abelito8 on 2012-01-14
This is from a Linux Mint usb startup I created with no luck

---

### Post by carl4926 on 2012-01-14
I really can't say what the problem is. I have been using USB's to boot my eeepc for the past couple of months, ever since I got it.
I have tried just about everything on it. They all boot and install and work.
I have settled for Ubuntu 11.10 and openSUSE 11.4
Using Unity 2D in Ubuntu
Using Gnome 2 in SUSE with kernel 3.2 to improve wireless

I think you must be missing something.
What exactly happens when you get to the BIOS and select the USB device to boot?

What model eeepc is it?

---

### Post by abelito8 on 2012-01-15
I agree I must have something wrong, I am probably wrong but I think it's the BIOS

when I select boot from USB it gives me a black screen and says either error or the file is not a ISO image...

I have been creating USB start-ups since 2009 and this is the first time this error happens so persistently (and with so many distributions that I think the problem is in my pc) 

Eee does not show anywhere the model, I just know it's a 12.1' screen

---

