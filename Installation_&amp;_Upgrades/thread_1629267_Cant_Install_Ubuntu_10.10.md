---
title: "Cant Install Ubuntu 10.10"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by Kingslice on 2010-11-23
I went ahead and created another partition and installed Ubuntu on it. now my other partition consisting of Windows had crashed so i was just going to rid of it completely and be a Linux user. So I accidently deleted the wrong partition and when i first started my PC i got a grub error. So i decided to just reboot from a CD and try re-installing the software. I got to a screen and it said this

(initramfs) mount: mounting/dev/loop0on// filesystem. squashfs failed: Input/Output error

and also

Can not mount /dev/loop0(/cdrom/casper/filesystem.squashfs) on//filesystem.squashfs

Now i have no idea what this means and i need to know what to do. Please help :)

---

### Post by mörgæs on 2010-11-23
Have you tried booting from a USB stick made with Unetbootin?

[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by Hippytaff on 2010-11-23
You shouldn't get this error from liveCD, unless the disc is bad.

---

### Post by Kingslice on 2010-11-23
I tried both of the things. Booting from the USB with multiple versions did not work and the help page did not have any info, from what i could undrstand, to help me.

---

### Post by Hippytaff on 2010-11-23
ok...have a read of these, if your still stuck let us know
[https://help.ubuntu.com/community/LiveCD](https://help.ubuntu.com/community/LiveCD)
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

You should be able to boot by using either of these methods and choose to install ubuntu if your happy to after trying it this way.

:-)

---

### Post by Kingslice on 2010-11-24
So i tried making a new disc and It was better this time. At least it could find my hard drive. But now i got an error stating b43 /ucode.fw not found. and a few other things i couldnt grab before it crashed. Any idea what this could mean?:P

---

### Post by mörgæs on 2010-11-24
B43 usually indicates a driver for a wirefree card, but before going so far I think you should aim for getting the system running having wired internet access while installing. 

Trying the alternate installer might also help.

---

### Post by srikanth.gundaz on 2010-11-24
Hi Kingslice, 
Your grub is corrupted. If you want to go back to windows, then put your windows 7 cd and when the first screen appears, select "Repair Windows". Now you will be shown command prompt. 
First type  fixboot and then enter.
Now type fixmbr.
Now you can easily login to your windows. Now freshly install Ubuntu and enjoy :)

---

### Post by Kingslice on 2010-11-24
I appreciate that but the windows cd is nowhere to be found so thats my predicament.

---

### Post by mörgæs on 2010-11-24
Grub does not matter. If you are aiming for a clean Ubuntu system as indicated in the first post you can just choose to erase the whole hard drive in the process, when you get the CD or USB to work. Then a new GRUB will be installed. 

Did the alternate version work better (or 10.04)? 

[http://www.releases.ubuntu.com/](http://www.releases.ubuntu.com/)

---

### Post by Kingslice on 2010-11-24
The version that got closest was a new cd of 10.10. It said something abt a driver thats missing but i didnt have that problem before.

---

### Post by Kingslice on 2010-11-24
Yeah none of the variants worked. Its saying i need to install some sort of driver. But how can i install drivers without an OS?

---

### Post by mörgæs on 2010-11-25
'None of the variants'... does that mean that you have also tried 10.04? 

If 10.04 also gives an error, please write the exact wording here.

---

### Post by srikanth.gundaz on 2010-11-25
> **mörgæs said:**
> 'None of the variants'... does that mean that you have also tried 10.04? 

If 10.04 also gives an error, please write the exact wording here.

Which companies laptop?
Is it HP?  Bcoz my friend too have the same problem. Ubuntu will not get installed in his system too. May be some difference in hardware compatibility issues :( :(

---

### Post by madjr on 2010-11-25
you may also try mint 10

which while is based on ubuntu 10.10, does get a few more updates and fixes included before release. So it might be worth trying with your current hardware.

[http://www.linuxmint.com/](http://www.linuxmint.com/)

also you may google your "laptop model+ubuntu" and see if it has issues or not.

if you have windows, you may also try the windows installer (wubi)

---

### Post by mörgæs on 2010-11-26
This shows how different hardware behaves with Ubuntu:
[www.linuxhcl.com](www.linuxhcl.com)

---

