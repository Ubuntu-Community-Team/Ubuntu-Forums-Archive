---
title: "Screen goes black during installation. help?"
date: 2006-06-04
forum: Installation &amp; Upgrades
---

### Post by Tekk on 2006-06-04
I've been attempting to load the alternate (inadvertantly DL it instead of the desktop one) version of Dapper Drake on to my laptop to no avail. It'll proceed smoothly to "Software selection and installation," make it most of the way through that process, and then go to a almost completely black screen for eternity. I say *almost* completely black as two small white rectangles do still remain. The final component that it installs before the crash I believe is xserver, if that provides any clue. 

 Any thoughts?   ](*,)

---

### Post by c0njur on 2006-06-05
WOW I've been having the exact same issue, just as you described.

I 2nd the request for help.

---

### Post by aligator on 2006-06-05
I have Acer travelmate 4101WLMi and same problem. I have tried several boot options (noapic, acpi off, vga ...), changing resolution in grub, but nothing helped. After Ubuntu (live CD 386 version) starts to boot, 9 error messages show up "PCI Cannot allocate resource - region 7,.. then region 8 then 9". Then all boot up procedures seems to load ok. But as soon as Ubuntu is trying to move to GUI, screen goes black, and thats it. (I hear some system sound, probably GUI was loaded .. or i hope it was). I don't know, what to change to be able to boot it normally. Travelmate 4101 got X700 on PCIx and I have had some problems with previous ubuntu or gentoo or fedora with it, but was able to install them and then change xorg or another config files to display X correctly. Please help us :))

---

### Post by Michael Kofler on 2006-06-05
same as #1 here 

I installed with the text mode installer (i386) from the DVD; the problem occurred only on one system, a Acer TravelMate 4020 (Centrino, Intel Graphics); three more text-mode installations on other hardware were fine; also an Ubiquity installation on the TravelMate was fine (i.e. I did not experience the problems reported in #3)

[https://launchpad.net/distros/ubuntu/+bug/48488](https://launchpad.net/distros/ubuntu/+bug/48488)

---

### Post by bluegene on 2006-06-05
i stumbled with the same problem on my toshiba satellite m40-237 laptop. but i managed to install dapper using external monitor connected to (RGB-out). however, i have to googlish so as to find solutions and one option i am considering right now is to upgrade the ati driver in my case ati radeon mobilty x700 and figure out if dapper still has some installation bugs on certain laptops..

the following link might be helpful for those who have ati graphics card.

[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)

---

### Post by markh on 2006-06-05
I get the exact same problem on an D915GAG (Intel) chipset, I guess it's something to do with the Intel 810/910 graphics too. If I remember Flight 6? and earlier were ok, this seems to have crept in for the release.

---

### Post by aligator on 2006-06-05
I have found one bug probably related to our issues. there is some working workaround, so i will try it today and will see if I can manage Ubuntu to start X correctly. 

[https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/22985]("https://launchpad.net/distros/ubuntu/+source/xserver-xorg-driver-ati/+bug/22985")

---

### Post by c0njur on 2006-06-05
To be more exact, the screen goes black when the "Software selection and installation" stage gets to 58% and the system is "Preparing to configure ubuntu-desktop".


EDIT: Also I'm running this on a Sony VAIO laptop (Centrino & Intel graphics)

---

### Post by c0njur on 2006-06-06
UPDATE

With the help of others, I was finally able to circumvent this problem. Instead of installing the desktop using the text based method, choose the server option from the list of actions on the alternative CD. After installing the server, enter this in the terminal:

```
sudo apt-get install ubuntu-desktop
```

This will download and update your install into the desktop version. The blackscreen with the 2 boxes only pops up for a second and then the install resumes normally.

Try this fix and let me know if it works for anybody else.

---

