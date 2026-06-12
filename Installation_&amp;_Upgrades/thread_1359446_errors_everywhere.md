---
title: "errors everywhere"
date: 2009-12-19
forum: Installation &amp; Upgrades
---

### Post by potrock on 2009-12-19
hello
i installed ubuntu 9.10 on my laptop a few days ago and it was amazing all the options i could change around. so i decided i want to install it on my desktop with the AMD 64bit CD. after many attempts and help from this site i made it past the "login before installaion"  now i face an eve bigger problem and i cant seem to find an answer anywhere.
for some reason my ubuntu does not want to update or upgrade or do anything :(
i constantly get errors with 
apt-check[2821]: segfault at 7f35198ca1a0 ip 00007f35113e8e2d sp 00007fff2ea143b0 error 4 in _libapt-pkg-libc6.10-6.so.4.8.1_[7f35113b0000+bc000]

in my log file viewer. i have burned multiple CDs many times with the same results after the installation 
then in terminal i try the "sudo apt-get updates"and i get the 
Segmentation faultsts... 1%

please help :confused:

---

### Post by potrock on 2009-12-20
everything is pointing to the libapt-pkg-libc6.10-6.so.4.8.1 file in the log file viewer it doesnt let me install or upgrade or update anything all it does is give me a segfault

---

### Post by byStanderone on 2009-12-20
...am thinking, perhaps your desktop is not yet capable of supporting 64-bits.

---

### Post by potrock on 2009-12-20
im running an athlon AMD 64^^
should i try the 32bit just incase ?

---

### Post by darkod on 2009-12-20
Did you try installing from usb stick? Sometimes there can be weird errors from cd but it will work from usb stick. Maybe your cd drive lens is dirty or something, so you can burn as many CDs as you want, same thing.

---

### Post by potrock on 2009-12-20
where do i get the download for a usb stick instead of the cd ?

---

### Post by darkod on 2009-12-20
If you created your own CD you just use the same ISO. There is no different ISO for usb. If you are sure it's not corrupted during download, no need to download again.
If you have another computer with ubuntu, copy the ISO there, plug in the stick and in System-Administration there is USB Startup disc creator. That will create bootable usb stick from the ISO.
If you only have a windows computer, download the free program unetbootin (google will find it). Open the program and it will also allow you to select the ISO and in the bottom select the letter of the stick. When it finishes ignore the question to reboot, just close it.
To get rid of the unetbootin boot menu and to enable the main ubuntu menu, open the stick and do:
1. In the root folder rename syslinux.cfg to syslinux.old
2. In the folder isolinux find and rename isolinux.bin to syslinux.bin, isolinux.cfg to syslinux.cfg
3. Go back and rename the whole folder isolinux to syslinux

That will enable the ubuntu menu. Now you can boot with that stick any computer that allows booting from usb. You might need to go into the BIOS and set usb to boot before the internal hdd.

---

### Post by potrock on 2009-12-20
ok just tested the usb version i still get the same segment fault...
but at the start i saw that it said it could not read the non-existing dists/karmic/main/packages
in the "try ubuntu without any change to your computer" everything works

---

### Post by darkod on 2009-12-20
If you used the same ISO, it might be corrupted. Try downloading new ISO from different mirror and try that.
Also you might want to MD5SUM the ISO you already have but I don't know how to do that procedure. Basically it should show if the image corresponds with the original on the server. You can google how to do the check.

---

### Post by potrock on 2009-12-20
k i just got a new cd and the same "non-existing file" showed up before the set up started 
this was the 4th cd i made and this one was from the us mirror
could it be because i turned off the LAPIC at the start ? because i do this to avert the need to login before setup

---

### Post by darkod on 2009-12-20
> **potrock said:**
> k i just got a new cd and the same "non-existing file" showed up before the set up started 
this was the 4th cd i made and this one was from the us mirror

My idea was to create the usb stick again with a new image. That way you don't waste CDs too. You cd drive might not be reading them correctly. I don't know, if a usb stick from the new image doesn't work I have no idea. Sorry.

---

### Post by potrock on 2009-12-20
k ill try a usb version with a us mirrored iso

---

### Post by potrock on 2009-12-20
Nope it still says it cannot open the non-existing file. Im gonna try the 32 bit now. All the downloads are the same they all tell me that the 
Dists/karmic/main/binary-amd64/packages
Dists/karmic/restricted/binary-amd64/packages
Are unable to be opened

---

### Post by potrock on 2009-12-20
ok it works now so far i can install stuff but still those files at the start say they cannot be opened :D

---

