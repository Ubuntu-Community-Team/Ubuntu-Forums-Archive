---
title: "Boot multiple distros from USB?"
date: 2009-11-22
forum: Installation &amp; Upgrades
---

### Post by footloose143 on 2009-11-22
I am a newbie here and apologies if this is an already answered question, ... 

I have a 8Gigs pendrive and looking for a way where I could copy multiple installs to different directories on USB and still access this drive from windows as well

viz

F:\Ubuntu
F:\Kubuntu
F:\Slax
...
F:\Data

and use the boot loader to point to different OS's while booting from USB  and all could access the Data folder where I can save my configs and user data??

---

### Post by darkod on 2009-11-22
Are you talking about installations or just the install files?
I don't know about the others but just the Ubuntu 9.10 Desktop installation is around 2.7GB brand new. So that doesn't leave much space for the others and data. Plus without swap partition how would they work?

If you are talking only about the install files which are approx one CD 700MB, you can put a lot on the stick but then the only use would be to boot from it and install on a computer.

---

### Post by LoloftheRings on 2009-11-22
Ubuntu does not install on a fat32 partition (windows readable) so you're gonna have to use the create live usb feature to do this. The 'data' folder is absolutely possible, I don't think multiple distro's is gonna be easy though.

Adding a data folder is as easy as plugging in the usb drive and creating a folder. You will probably get

F:\bla blabuntu
F:\blaisolinux
F:\blablakernel
F:\blablaboot
F:\blablainstallationfoles

F:\Data

It's gonna be a mess, but one distro + data is possible.

---

### Post by darkod on 2009-11-22
If you wanna test and also if you plan to use the stick sometimes on windows you have to make the first partition the data. Windows is limited to looking only at the first partition of usb sticks. In fact, you can't even create more than the one partition. On Linux yes.

There are ways to mask the stick as external usb hdd in windows but it's not easy and it will work only on computers where you've done that, so taking the stick to your friends won't work. Only the first partition will be visible.

---

### Post by footloose143 on 2009-11-23
What I was looking for is configuring a bootable usb pen drive which I could use for all my Linux projects. I dont wanted to mess up my laptop hdd installation nor change its MBR (BTW I had already screwed by mbr last night and had to fix it back to access my windwos :-) again). I wouldnt mind creating multiple partitions on the drive for installation but I still wanted to access atleast one drive which is FAT32 for windows and share that on Linux install as well.
 
Please suggest !!! :-k

---

### Post by footloose143 on 2009-11-23
Could get a source at [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

but could someone tell me how to make persistence changes??

---

### Post by dbzkid on 2009-12-11
> **darkod said:**
> Are you talking about installations or just the install files?
I don't know about the others but just the Ubuntu 9.10 Desktop installation is around 2.7GB brand new. So that doesn't leave much space for the others and data. Plus without swap partition how would they work?

If you are talking only about the install files which are approx one CD 700MB, you can put a lot on the stick but then the only use would be to boot from it and install on a computer.

You could make it work with out swap, it will just be harder on your physical ram, but swap is similar to the page file in windows

---

### Post by phillw on 2009-12-11
> **footloose143 said:**
> Could get a source at [http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/](http://www.pendrivelinux.com/boot-multiple-iso-from-usb-multiboot-usb/)

but could someone tell me how to make persistence changes??


From the same site - you want [http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/](http://www.pendrivelinux.com/how-to-create-a-larger-casper-rw-loop-file/)

Phill.

---

