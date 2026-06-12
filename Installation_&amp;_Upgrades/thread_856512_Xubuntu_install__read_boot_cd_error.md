---
title: "Xubuntu install : read boot cd error"
date: 2008-07-11
forum: Installation &amp; Upgrades
---

### Post by gasaraki on 2008-07-11
Hi all I'm trying to install Xubuntu on a crappy old laptop i was given for the purpose of playing mp3's from a usb hard-drive.

Every time i boot from the live cd downloaded from here [http://www.xubuntu.org/get](http://www.xubuntu.org/get) ( 8.04 release) it gets to the main menu anything i try (run Xubuntu, install Xubuntu, check disk) it comes up with an error box saying it can read the boot cd and forces me to reboot.

I know the cd is ok because i tried it with my main machine and it ran fine and got into the desktop environment. I'm also sure the cd drive in the machine is ok because when i run windows on the laptop i can view the cd fine.

any suggestions on what i could to to solve this? I tried to read up on command line extras for the install but it was all a bit over my head.

the laptop is a Dell Latitude CPx  / 500 MHz CPU / 256mb RAM / 12 GB HD /

also when i use the install (if i get it to work ) will i be able to fully format the HD and get rid of all the evil dell stuff ?

Thanks G.

---

### Post by Pumalite on 2008-07-11
Clean the lens in your burner. Also try editing your boot line and trying all_generic_ide at the end of the line. Other things to try are noapic nolapic acpi=off.

---

### Post by NovruzeliH on 2008-07-11
do exactly what Pumalite told ya, cuz i got a crappy laptop from my frined and he wanted me to burn xubuntu on it for him, so i did it and it worked fine no prblems at all, and the latest version i did for him i belive its 8.04

---

### Post by gasaraki on 2008-07-12
Thanks for the help, however its still not responding to any of those commands or options, i think the problem might be to do with dell's evilness ill try wiping the HD and see if that helps?

any other suggestions ?

---

