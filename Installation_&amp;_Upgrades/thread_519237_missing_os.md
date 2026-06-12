---
title: "missing os"
date: 2007-08-06
forum: Installation &amp; Upgrades
---

### Post by JAM3S on 2007-08-06
Hello,
First off,  I am new to linux. I have a live cd of ubuntu and loved it so I tried to install on my laptop. Sadly the cd drive on my laptop is broken. So I needed to download from the web and i did and the install seemd to complete 100%(also if it helps diagose my problem, I chose to use all the hdd for linux)Upon completion, installation prompted me to restart. When I did I get the horrible " missing operating system" error. Please help!I've searched the forums and the web but cant find/understand any answers that apply to my case.  I have a desktop and a flshdrive if I can somehow use those to fix the linux on the laptop I would be so grateful.

---

### Post by Pumalite on 2007-08-06
Use Super Grub: [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#15)

---

### Post by JAM3S on 2007-08-06
Thanks Ill try this and see how it works. Just to be clear I downloaded the usb version to my flash drive now i just try to boot from flash drive?

---

### Post by Pumalite on 2007-08-06
If it boots; great. Don't forget to set BIOS to USB 1st.

---

### Post by JAM3S on 2007-08-06
Ok i set to boot from removable storage but when i hit enter it just shows the same missing os error. :confused:
Should I organize the files on the usb a certain way?

---

### Post by Pumalite on 2007-08-06
That means your BIOS is not recognizing your USB device as bootable. You have to have a bootable 'Image' there; not just files. Check this: [https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by JAM3S on 2007-08-07
OK I downloaded the ISO torrent but i cant find anyway to  use infra recorder to put it onto flash. Would it be easier if I just go buy a new cd/dvd rom drive. Please help I really want to run linux

---

### Post by merlinus on 2007-08-07
Since at some point you will need a cd-dvd drive-burner, best to do that now and save loads of agita.

-merlin

---

### Post by JAM3S on 2007-08-07
Sounds good but just to be sure, if i had a new optical drive i should be able to boot/install from my live cd with little problems (in theory atleast) right?

---

### Post by psusi on 2007-08-07
ISOs are for cds, not flash drives.

---

### Post by merlinus on 2007-08-07
In theory, for sure.  But things do not always work out that way.

Be sure that you have an option in your BIOS to boot from the cd-dvd drive before the hard drive.

You may run into problems with your video card, but there are good workarounds.

-merlin

---

