---
title: "Ubuntu not booting from usb stick on sony vaio S"
date: 2014-06-28
forum: Installation &amp; Upgrades
---

### Post by chris252 on 2014-06-28
OK here's the thing. I have a sony vaio s which boots multiple operating systems, Windows 8, and several kernels of Ubuntu (i'm not sure why that's the way it was when I got it from work). It was Ubuntu 12 and I don't particularly like ubuntu 12 cause it's kinda blocky so I updated to Ubuntu 14 and when I restarted I was sent into Grub rescue mode. Now I've already looked at like every thread on grub rescue mode and they all say to do the thing where you
find the harddrive with the lost and found and the vmlinuz and i've done that. I've set the root and set the prefix but when I get to the part where I'm supposed to type in insmod normal, it tells me no file found so I have no idea what to do.

Anyway I've tried that and installed Ubuntu 14.04 onto my flash drive on my personal computer. Alright, so i've gone into the BIOS and set external device as first booting option. I've tried it in legacy mode as well is in UEFI mode. When I do it in legacy mode it just stays on the VAIO screen indefinitely. When I do it in the UEFI mode it just flashes that same Vaio screen about every 3 seconds.
Please i need to recover this badly it's my work computer and has a lot of good programs installed on it on the windows partition.

---

### Post by yancek on 2014-06-28
More detailed information would probably help someone to help you.  You can use the Ubuntu flash drive or any Linux Live CD to go to the site below.  Read the instructions in the link in the Description box, then download and run the script.  It will output a results.txt file which provides detailed information on your partitions and boot files.

[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)

---

### Post by chris252 on 2014-06-28
I stated above very clearly that I cannot boot from usb with the live usb. if I could I wouldn't be having any problems.

---

### Post by Vladlenin5000 on 2014-06-28
The question now is how did you made that USB? When we want a "live session + installer" we don't actually install the OS in that USB, although it's possible. And yet you mentioned you "installed"...
The next question is about UEFI/Legacy... Were the  OSs already there installed in UEFI or legacy? You have to boot any other device in the same way.

---

### Post by chris252 on 2014-06-28
i tried with universal usb installer then with linux live usb creator. The OS's were all installed in UEFI i believe. i used the iso from the ubuntu download page too

---

