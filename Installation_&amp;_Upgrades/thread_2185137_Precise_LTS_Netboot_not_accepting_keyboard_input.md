---
title: "Precise LTS Netboot not accepting keyboard input"
date: 2013-11-01
forum: Installation &amp; Upgrades
---

### Post by Lars Noodén on 2013-11-01
I'm looking at a machine with an AMD Duron CPU and trying netboot.  I got the netboot image from this URL

[http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/precise-updates/main/installer-i386/current/images/netboot/)

and can boot up fine to the "Installer boot menu".  The problem I am encountering is that at that point the machine does not accept any keyboard input.  Not even caps lock nor num lock register.  

What is the way around this or should I be using the non-PAE netboot image for this one?

---

### Post by Lars Noodén on 2013-11-01
The same problem seems to occur for Saucy's netboot i386 image.

---

### Post by Bucky Ball on 2013-11-01
Silly question perhaps, but in the hopes of isolating the issue and clarity: is it a USB keyboard? What setup have you got? Desktop, laptop keyboard? Bluetooth?

---

### Post by Lars Noodén on 2013-11-01
It's a usb keyboard that works fine during the BIOS menu to select netboot.  It just seems to shut off once the boot menu is shown.  I've tried other keyboard and all the USB ports front and back.

The machine is a desktop 'tower' with the above processor and 512MB RAM.

Edit: the BIOS are AMI if that matters.

---

### Post by Bucky Ball on 2013-11-01
512Mb of RAM? Which release are you attempting to run? Ubuntu 12.04 LTS? That might be pushing it!

Just out of curiousity, have you tried anything lighter if the above is the case?

When you say the boot menu, do you mean the login screen? I am not familiar with Netboot so not sure of the procedure.

---

### Post by Lars Noodén on 2013-11-01
I was considering falling back to Lubuntu if Ubuntu is too heavy, but there is only one netboot image for the lot, isn't there?  I'm not seeing a netboot image here :[http://cdimages.ubuntu.com/lubuntu/releases/saucy/release/](http://cdimages.ubuntu.com/lubuntu/releases/saucy/release/)

I figured first get a system on then I can add or remove things.

---

### Post by Bucky Ball on 2013-11-01
You're using Lubuntu. That should work. 13.10? Who knows. Only just released so this could be a bug specific to netboot and it.

If you just want to get a system on perhaps try the mini.iso (if you have a CD or USB boot option and internet cable). 

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

This will allow you to install the kernel ONLY and then just the desktop environment and apps you want/use (Lubuntu uses lxde so you would install that and it won't drag in the whole lubuntu-desktop or any default apps). Extremely light option if you're careful (and DON'T install '*buntu-desktop anything!).

With a bit of planning you could get a reasonably quick setup. ;)

---

### Post by Lars Noodén on 2013-11-01
Yes, once  I get anything at all on the machine, I can adjust it according to its capacity.  Right now the CD reader is quite dead so I figured I would try netboot.  Netboot was easy 4 years ago, but not now.  I'll keep the Minimal CD in mind if we can get a replacement optical drive.  But for right now I have to try netboot.

---

### Post by Bucky Ball on 2013-11-01
I said it but didn't realise what I said and skipped over it! You're using Saucy, not Precise according to the link you sent me (which would render the thread title incorrect). Try with 12.04 and see if you have the same problem. This could be a bug with a very fresh release that most folk haven't noticed.

Trying with a known entity would at least rule out that possibility.

---

### Post by Lars Noodén on 2013-11-01
I tried 12.04 first, but also tried 13.10.  Same results with both.

---

### Post by Lars Noodén on 2013-11-01
I'm done for the weekend with that one, perhaps I will be able to get the optical drive fixed next week.

---

### Post by mörgæs on 2013-11-01
> **Lars Noodén said:**
> 
What is the way around this or should I be using the non-PAE netboot image for this one?

There's no PAE problem on AMD (just to rule out a factor in the troubleshooting).

---

