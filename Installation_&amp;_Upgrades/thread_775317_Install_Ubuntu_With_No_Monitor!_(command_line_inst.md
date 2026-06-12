---
title: "Install Ubuntu With No Monitor! (command line install?) :)"
date: 2008-04-30
forum: Installation &amp; Upgrades
---

### Post by joshuaf on 2008-04-30
I've got a laptop with a broken video card/chip that I'm too cheap to replace. It will not display correctly on the LCD or external monitor. I'd like to install ubuntu on it and access it remotely.

I can boot the live cd and install ssh to get in remotely, but, I can't figure out what to do to perform the installation from the command line, if that's even possible.

Any suggestions? Thanks in advance.

---

### Post by acelin on 2008-04-30
You are screwed. Kind of have to see the command line to know what is going on.

---

### Post by acelin on 2008-04-30
I really dont see how its possible... unless you take the hard drive out, and install it in another computer...

---

### Post by natrixgli on 2008-04-30
I take it you are installing openssh on the live cd blind from memory? (been there, done that!) 

What about X forwarding? you could SSH in from another linux desktop PC and run the graphical installer that way. 

```

ssh -X ubuntu@[ipofbrokenlaptop] ubiquity

```

Not sure if it will work, but I can't think of why it wouldn't.... And I'm all for saving semi-broken laptops!

-n8

---

### Post by vlgligor on 2008-04-30
I think your only alternative is an installation script to run all the needed commands blindly and set all the parameters you will need to access the computer remotely. I was thiking also to this solution, but in my case I want to run it over internet and have minimum contribution (just insert the bootable cd) from the one in front of the computer. But I haven't done it yet.

---

### Post by finite9 on 2008-04-30
> **acelin said:**
> I really dont see how its possible... unless you take the hard drive out, and install it in another computer...

yeah, how do you do this??  I have a laptop with broken CD drive, no usb boot and no network boot.  I can take the laptop out of install ubuntu on it from another computer, but when I  put the drive back in the original laptop, it complains about UUIDs.  Is this a known issue with an easy workaround?

---

### Post by joshuaf on 2008-04-30
Yeah, I blind installed openssh-server. (Alt-F2, xterm, sudo apt-get...)

X forwarding! Yay! Why I have I never heard of that! :)

I'll give it a whirl a bit later and post my results. Thanks.

---

### Post by joshuaf on 2008-04-30
X forwarding worked, I used Xming and was able to install ubuntu to the hard drive. I even got the vnc server started (Remote Desktop), but, this is funny, it was all garbled, just like the LCD/Monitor! Apparently if the video card is messed up... so is VNC!

---

### Post by natrixgli on 2008-04-30
Congrats, glad it worked! I've never installed a system blind, but I've recovered data from boxes this way. 

Cheerio,

-n8

---

