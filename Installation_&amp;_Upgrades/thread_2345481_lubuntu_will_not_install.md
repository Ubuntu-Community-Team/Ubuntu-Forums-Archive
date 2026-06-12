---
title: "lubuntu will not install"
date: 2016-12-04
forum: Installation &amp; Upgrades
---

### Post by artunix on 2016-12-04
lubuntu will not install. The 16.10 ISO is missing the bootloader, and or the install program in the ISO is badly written because when it gets to point where it is 'configuring bootloader', 'installing grub2' the following happens:

a windows comes up - grub installation failed - "the 'grub-pc' package failed to install into /target/. without the GRUB boot loader, the installed system will not boot."

you hit the OK button.

then you get the 'sorry.... how would you like to proceed?...' window. 
And no matter what choice you choose and hit OK you know what happens...... NOTHING; BADLY 
WRITTEN.

1 The ISO should ask where it is to be installed before it starts copying anything. * IDE SATA TO USB *.

2 In the 'other..option' a better explanation of the swap file and swap options, like partitions, and swap sizing etc..

3 since bootloader is an issue that should the first thing the ISO should attempt.

---

### Post by QIII on 2016-12-04
Hello and welcome to the Forums!

Did you run a checksum on the .iso after downloading and burning it?  Did you check the integrity of the burned media?

---

### Post by yancek on 2016-12-04
Since you make no mention of any other OS installed, does that mean you selected the "Erase Disk and install Lubuntu" option?

The installer does ask where you want to install and you can select any harddrive or any partition on any hard drive when you use the manual installation option ("Something Else").  If you want to do a non-standard install of some kind, you would obviously need to use the manual option.

Posting info on your hardware as well as the output of boot repair would be a good starting point to get help.

---

### Post by apexpredy on 2016-12-04
I had that issue to I solved it by connecting to the wifi/Ethernet if you have any

---

### Post by artunix on 2016-12-06
> **QIII said:**
> Hello and welcome to the Forums!

Did you run a checksum on the .iso after downloading and burning it?  Did you check the integrity of the burned media?
yes. yes.

> **apexpredy said:**
> I had that issue to I solved it by connecting to the wifi/Ethernet if you have any

Need wifi ?! sounds like Microsoft. Phone Home! Sounds like ACTIVATION !.

trying to install on dell laptop with 40gb HD, and 2GB of memory.

don't like the phone home.


reactos installed, but that needs a LOT of work.


does Canonical own all flavors ubuntu.??

what other things beside wifi will get lubuntu to work?

---

### Post by FerryGnu on 2016-12-10
Add me to this issue with Lubuntu 16.10 to an SSD. I tried with RJ45 to router and wifi with "update while installing" and still got the same response at the end. Then it locked up so I couldn't send report. Had to pull the laptop battery to shut it down.

Tried installing alongside 14.4 and then used GParted to clean the SSD and full clean install. Still same problem - I quit. :)

---

### Post by artunix on 2016-12-11
> **FerryGnu said:**
> ..Add me to this issue with Lubuntu 16.10 ... :)


You have been here since Aug 2013; so I think it is something with the install iso.

---

