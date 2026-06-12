---
title: "theoretical install question"
date: 2012-07-30
forum: Installation &amp; Upgrades
---

### Post by Austin Texas on 2012-07-30
I have a couple of general questions about installing the operating system.

First, my daughter has a laptop with a somewhat questionable CD drive.  Is it possible for us to link through our home network, and I install the OS  to her computer using my computer? 

That brings up my next question about the installation program itself.
Obviously, there is a program on the installation disk which manages the installation procedure.  Why is that program not available to me on my current operating system, so that I can use it to install the OS to a USB, or another hard drive, without resorting to the use of an installation disk?  Or is it available?

---

### Post by Cheesemill on 2012-07-30
You could try installing using the mini.iso
This contains the absolute bare minimum required to fire up the installer, everything else is downloaded directly from the internet.
[http://cdimage.ubuntu.com/netboot/precise/](http://cdimage.ubuntu.com/netboot/precise/)

If the Laptop can boot from USB you could also install using that method.

---

### Post by Ansowi on 2012-07-30
> Obviously, there is a program on the installation disk which manages the  installation procedure.  Why is that program not available to me on my  current operating system, so that I can use it to install the OS to a  USB, or another hard drive, without resorting to the use of an  installation disk?  Or is it available?

If you are referring to Ubiquity, there is a version for Windows: Wubi. I'm not certain if there is a Mac alternative.

And you can easily write the ISO image to a USB and run the installation from there, use a tool like UNetbootin.

---

### Post by Austin Texas on 2012-07-30
Thank you, Cheesemill and Ansowi, for your responses.
I understand that I can install from a USB.  But apart from solving the practical problem of her computer, I really asked the questions so that I could learn more about the possibilities of using the home network to do an install, and using my OS to install to another hard drive, instead of using the installation disk.
Ansowi, I think your suggestion of Ubiquity is what I was looking for in regards to the second question.  Thanks. I will follow up on that.

---

### Post by oldfred on 2012-07-30
I have never tried network booting:

[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

If the computer has grub2 for booting, you can directly boot an ISO.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)

---

### Post by Austin Texas on 2012-07-30
Wow, oldfred, you're a wizard.
I configured my grub2 to boot the iso into ram (since I have plenty of ram).
And of course the install was much faster than from the CD.
I used it to install my OS to my backup hard drive, sdb, and then booted to the new OS.
I am amazed. I had no idea such a thing was possible, and it is exactly what I was looking for !
Thanks

---

### Post by Austin Texas on 2012-07-30
Now I don't have to burn a CD or DVD when I want to install a new OS.
I just boot it to ram !  Awesome !

---

### Post by oldfred on 2012-07-30
Glad it worked. :)

I used to use CDs and found flash was faster, but my flash drives started to get larger and I wanted to use them better. I started to use the grub loopmount to boot the ISOs from the flash drive. I can have several repair ISOs on one flash that way.
Now there are several scripts that automate that process.

Then I installed ISOs to hard drive and install was even faster. I recently got a SSD and the install from a hard drive to the SSD was extremely fast even with my 6 year old hardware.

---

