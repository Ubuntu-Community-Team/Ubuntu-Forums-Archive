---
title: "bootable USB drive gives &quot;No Boot Sector found&quot;"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by stargatefan on 2011-09-06
I am currently using ubuntu 11.04, and I am trying to revert back to 10.04. When I use the startup disk creator everything works fine, but when I try to boot from the usb thumb drive the BIOS gives the error "No boot sector on the usb device." 

Any ideas?

Thanks in advance.

---

### Post by Grenage on 2011-09-06
Howdy,

Is the USB partition marked as bootable?  You can check in gparted, but you can also check using fdisk from a terminal.

---

### Post by stargatefan on 2011-09-06
Thanks for the reply,

Yes it is labled as bootable. I tried creating a bootable partition on my external hard drive to see if it was the usb stick itself. I tried booting up with the external hard drive in and it gave me the same error... I am going to download the iso again to see if that was the problem.

---

### Post by stargatefan on 2011-09-06
I downloaded a new iso, and this time I had booting with only the usb stick plugged in (as opposed to having the mouse and ext HD plugged in). Now instead of giving "No boot sector found on USB device" it looks like it might boot up and then it gives an error like "vesamenu.c32 not a com3r image" or something like that.


P.S. It might be useful to note that I have tried using unetbootin instead of startup disk creator, and everytime it stops during step 2 (extracting and copying), specifically on file 10 of 187.

This is a sandisk with u3 capability, but I have partitioned and formatted this thing so many times that i doubt that the u3 launchpad is still on it.

---

### Post by Hakunka-Matata on 2011-09-06
**update: u3 software removal > **[http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)

> **stargatefan said:**
> I downloaded a new iso, and this time I had booting with only the usb stick plugged in (as opposed to having the mouse and ext HD plugged in). Now instead of giving "No boot sector found on USB device" it looks like it might boot up and then it gives an error like "vesamenu.c32 not a com3r image" or something like that.


P.S. It might be useful to note that I have tried using unetbootin instead of startup disk creator, and everytime it stops during step 2 (extracting and copying), specifically on[COLOR=Red] file 10 of 187.[/COLOR]

This is a sandisk with [COLOR=Red]u3 capability[/COLOR], but I have partitioned and formatted this thing so many times that i doubt that the u3 launchpad is still on it.

re: file 10 of 187:  Yes, you are right, it takes a LONG time for that file to unpack and start loading, "a caution note would be nice to alert you that it may take as much as 5 minutes."  It's taken nearly that long on this machine with 4GB RAM and a Phenom 4core cpu.
the FIX:  just let it run, it'll complete...............
unetbootin rocks.

u3 capability:  Search it on the net, it's a problem, should get rid of it.  I'll post a link, [http://u3.sandisk.com/launchpadremoval.htm](http://u3.sandisk.com/launchpadremoval.htm)

---

