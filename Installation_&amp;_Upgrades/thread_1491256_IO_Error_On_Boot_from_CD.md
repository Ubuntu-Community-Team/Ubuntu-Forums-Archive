---
title: "I/O Error On Boot from CD"
date: 2010-05-23
forum: Installation &amp; Upgrades
---

### Post by Lolpanda on 2010-05-23
Hey guys, For the longest time I've used 32-Bit Linux OS's. Keep it simple and make sure everything works. Recently I've felt like switching over to 64-bit. I know my CPU supports 64 bit because I have windows 7 (64) installed and it works flawlessly. 

My issue is after downloading and burning the 9.10 amd64 ISO, when I hit "Install Ubuntu" I get "I/O Error Reading Boot CD" and the error code "R42AAEF" at the top left and top-middle of my screen. 

I know the CD is fine because just a few days ago I used the same CD to install 9.10 32-bit on a friend's laptop and he's had no issues.

MD5sum and "Verify Local Data" Through BitTorrent both came back to be 100% stable and authentic. 

If anyone has any more ideas I'd love to hear them, if it matters, my CPU is an AMD Athlon II x4

---

### Post by dino99 on 2010-05-23
wow, you are the only one with this error known on google, you are the winner :P

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

check your bios settings and try with ahci. if it fail, try to boot with acpi=off, or lapic=off, noacpi, nomodeset=0

---

### Post by cybrsaylr on 2010-05-23
I just installed 32 bit Lucid on an old PC and got several I/O errors that stopped the install several times. I used the Live-CD mailed me by the Ubuntu mail service! After checking what the I/O errors suggested and not finding any fault, I just pushed it on through and after several attempts 32 bit Lucid installed and appears to be running very well. This is the first time experiencing these I/O errors. 

When I installed 64 bit Lucid on my laptop, the install was smooth and flawless with the 64 bit Live-CD I had created. This install complete with LL updates took ~30 minutes on this newer laptop. 

Don't know why there were so many problems installing the 32 bit version of Lucid on my other older PC.

---

### Post by dino99 on 2010-05-23
the "32" kernel coming with lucid has many issues, so if you cant find a workaround, install karmic then dist-upgrade and install kernel 33 with this link: [http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/)

---

### Post by Lolpanda on 2010-05-23
> **dino99 said:**
> wow, you are the only one with this error known on google, you are the winner :P

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14) 

check your bios settings and try with ahci. if it fail, try to boot with acpi=off, or lapic=off, noacpi, nomodeset=0

Thanks for the quick reply Dino. I'll give it a shot when I get back home. Just out of curiousity can you explain what those boot options do. For future referrence.

PS: yeah I know, I was shocked when it came back with zero results to that error code. Hence why I came here haha

edit: I went into bios, browsed through all the menus and couldn't find any referrence to the advanced hist controller. Again, if it matters: 1TB Sata HDD.

---

### Post by Lolpanda on 2010-05-23
Well whatever was the issue, its gone now. I used Unetbootin to burn the AMD64 iso to a spare flash drive and installed from there -- no issues, no problems.

---

