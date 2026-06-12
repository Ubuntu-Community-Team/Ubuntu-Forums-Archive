---
title: "Can not install Ubuntu on toshiba NB255"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by Justpeter6 on 2011-01-19
I have a Toshiba netbook NB 255. As you know there is no CD drive so I have to boot from a usb flash drive. I follow all of the instructions on the Ubuntu web site to get the .iso onto the flash drive using pendrivelinux.com and the universal usb installer. However for some reason whenever I try to boot from any usb drive on my netbook I am getting an error saying "graphics initialization failed Error in setting up gfxboot" and on the next line down it says "boot:" and the flashing cursor. I consider myself a generally tech savvy person but this is a problem that I have never encountered. 

I really prefer Ubuntu on my netbook rather than whatever garbage windows version the manufacturer put on the netbook. If anyone has any insight on this matter at all it would be greatly appreciated.

If this topic was already talked about I apologize in advance.

---

### Post by Justpeter6 on 2011-01-19
bump

---

### Post by Justpeter6 on 2011-01-20
sorry to be annoying but I really need help with this issue

---

### Post by Bucky Ball on 2011-01-20
I found 10.10 was the only release that would work on my Toshiba Satellite Pro L510. Pity because I'd rather be using the 10.04 LTS release. :(

---

### Post by Quackers on 2011-01-20
Just a few ideas here.
Have you checked the MD5SUM of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If that checks out ok, when booting from the flash drive press the Esc key. You should get a purpleish screen which will immediately be covered by a language choice screen. Choose language and OK. The next screen should give you some options to choose from. Choose "check cd for errors" and see if any are reported.

---

### Post by Justpeter6 on 2011-01-21
I checked the MD5SUM of the download and it was wrong, so i reinstalled the operating system from the Ubuntu web site and then put it on the flash drive as explained on the web site and I am still getting the exact same error. then I proceed to press the Esc key and nothing happened at all. Is there by any chance possibly another installation method for netbooks?

---

### Post by Justpeter6 on 2011-01-21
I started to type things after the line that says boot: because it has the flashing cursor after it and no matter what i type it says can not find kernel image : (whatever I typed)

hope this helps

---

### Post by Justpeter6 on 2011-01-22
bump

---

### Post by Titanracer86 on 2011-01-24
I have the same netbook and when I went into the Bios I had no USB option, so I followed the install from this webpage:
[http://www.howtogeek.com/howto/17486/install-ubuntu-netbook-remix-with-wubi-installer/](http://www.howtogeek.com/howto/17486/install-ubuntu-netbook-remix-with-wubi-installer/)

---

### Post by leumas89 on 2011-01-25
Type help in the boot prompt. 

If the image is good it should boot up fine. I had this same problem tonight and was pulling my hair out trying to figure this out.

---

### Post by rocthrttle on 2011-01-25
> **Justpeter6 said:**
> I have a Toshiba netbook NB 255. As you know there is no CD drive so I have to boot from a usb flash drive. I follow all of the instructions on the Ubuntu web site to get the .iso onto the flash drive using pendrivelinux.com and the universal usb installer. However for some reason whenever I try to boot from any usb drive on my netbook I am getting an error saying "graphics initialization failed Error in setting up gfxboot" and on the next line down it says "boot:" and the flashing cursor. I consider myself a generally tech savvy person but this is a problem that I have never encountered. 

I really prefer Ubuntu on my netbook rather than whatever garbage windows version the manufacturer put on the netbook. If anyone has any insight on this matter at all it would be greatly appreciated.

If this topic was already talked about I apologize in advance.

check your bios for a setting called "sata mode". ahci will stop toshiba netbooks from working well or at all with ubuntu. set it to "compatible" mode or anything other than ahci. i fought for hours with this one too. it was a toughy. hang in there it's worth it.

i got 10.04.1 lts netbook remix fine on a toshiba netbook after switching the sata mode. also if you plan on keeping windows and dual booting this setting must be changed back for windows to boot properly.

---

### Post by rockerZ71 on 2011-02-02
I had the same thing happen and as someone else already said, typing 'help' at the prompt caused it to boot off of my SD card every time.  I don't remember if I had to press enter at the help screen or not.

---

### Post by Justpeter6 on 2011-02-02
I used WUBI and installed the regular ubuntu desktop edition just to see if it would work. It did. now probably going to uninstall the desktop edition and try to install netbook edition with wubi. hopefully that works

---

### Post by Bucky Ball on 2011-02-03
> **Justpeter6 said:**
> I used WUBI and installed the regular ubuntu desktop edition just to see if it would work. It did. now probably going to uninstall the desktop edition and try to install netbook edition with wubi. hopefully that works

Not quite the same as the OPs issue. A Wubi install is not the same as a dual-boot or single Linux OS install. ;)

You will find either is faster and more flexible than a Wubi. Wubi is really to try and see if you like and it works on your machine. OP is having trouble installing to hard drive. ;)

---

### Post by Justpeter6 on 2011-02-03
I am actually the OP. and i didnt know that wubi was that much different. i only tried it because it was a different way to trey and get linux on my machine as all other ways have failed. I will now try and do what all you others are suggesting. i will keep you guys posted

---

### Post by Justpeter6 on 2011-02-03
awesome. typing help fixed the problem. Ubuntu 10.10 maverick merkat netbook edition is installed and running great. thanks everyone

---

### Post by rockerZ71 on 2011-02-04
if you hate the netbook interface they made like I do, the nb255 runs a standard 10.10 install with gnome just fine

---

### Post by elchago on 2011-02-10
if you do have another pc in your network install the mini to it using the router ,,, on main pc insert the cd with installation files for Ubuntu and go to Computer then on the driver with the cd right click and share with everybody and network ,,,,, go to mini and look for the network and the drive with the cd the from there you can install it ,,,, that is how i got mine working ,,,,, Toshiba N255 N245 i hope works and is another way in the Ubuntu page using a USB Stick of 2 Gigs ,,,,,,,, found that later ,,,,,,,

---

