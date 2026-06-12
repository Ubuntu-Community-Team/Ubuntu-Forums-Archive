---
title: "Booting Problem"
date: 2008-03-03
forum: Installation &amp; Upgrades
---

### Post by trm96 on 2008-03-03
I know this is a hardware problem but... I have a Copy of Gutsy (I got the free CD) i know the CD works cause I've tried it in other machines. When I try to boot from the CD in my desktop the booting process hangs.

Here is the configuration of my desktop:
Intel Core 2 Quad Q6600 processor
EVGA 780i SLI Mother board
4GB PC6400 DDR2 RAM (2 x 2GB)
A pair of XFX GeForce 8800GT video cards (in an SLI config)
750GB WD SATA HDD

Is it just that the current version of Ubuntu is just not compatible with some/all of my hardware or what?

---

### Post by dstew on 2008-03-04
Where does the Live CD hang? Often it is a graphics card incompatibility. Try booting the Live CD in Safe Graphics Mode.

---

### Post by trm96 on 2008-03-04
Ok. I will have to get back to you on that one...

---

### Post by uberlube on 2008-03-04
And if that doesnt work, try setting the vga by editing the boot process with "vga=791" and erasing "quiet splash"

---

### Post by trm96 on 2008-03-04
I got the live cd to boot boot using Safe Graphics Mode. I had to plug in the monitor cable to one of the other outputs on my first video card. Now tho only other problem is that I could only get the 32bit version to display the live desktop the 64 bit version is a no go. It does not display anything at all on the monitor and after a few mins i hear beeps form my computer...

---

### Post by Pumalite on 2008-03-04
Burn a new CD and try again. Do md5sum on the iso, burn at 4x or less, etc. Good luck. It should work. I have 64 bits in a Core 2 Duo and it's working fine. It should recognize your Quad too.

---

### Post by trm96 on 2008-03-04
I did not burn the 64 bit cd I sent out for it but I could try to download it if you think it will do any good.

---

### Post by Pumalite on 2008-03-04
Download from here:
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
Torrents are better. Many sent for CD's do not work.

---

### Post by trm96 on 2008-03-04
ok downloading... What should the MD5 be?

---

### Post by Pumalite on 2008-03-04
[http://en.wikipedia.org/wiki/Md5sum](http://en.wikipedia.org/wiki/Md5sum)
Follow this guide:
[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)

---

### Post by trm96 on 2008-03-04
I know how to find the MD5 of a file, waht I ask is what should the MD5 be

---

### Post by Pumalite on 2008-03-04
It's at the site where you download from. I'll check

---

### Post by Pumalite on 2008-03-04
[http://www.google.com/search?q=md5sums&btnGNS=Search+ubuntu.com&oi=navquery_searchbox&sa=X&as_sitesearch=ubuntu.com](http://www.google.com/search?q=md5sums&btnGNS=Search+ubuntu.com&oi=navquery_searchbox&sa=X&as_sitesearch=ubuntu.com)

---

### Post by trm96 on 2008-03-04
here btw is the MD5 from the ISO I just downloaded: 
61c87943a92bc7bf519da4e2555d6e86
As far as the link you gave me they are the same I will commence burning...

---

### Post by trm96 on 2008-03-04
Ok I burned the ISO and booted off the CD but the 64 bit version still hangs. The screen says "running local boot scripts                   [ok]". I let it run for a while (like 15 or so mins). If i press cotrl+alt+delete it does open the disk tray and allow the machine to reboot.


Ok I have decided to just install the bit version. After I install I get a GRUB error 22. Let me explain my situation I have a 75GB hdd with Windows Vista installed (had it installed before I installed Ubuntu. I Used acronis disk director to patition the drive in Windows. I also installed the acronis os selector. When I select Linux from the menu it shows GRUB and gives me the error.

---

