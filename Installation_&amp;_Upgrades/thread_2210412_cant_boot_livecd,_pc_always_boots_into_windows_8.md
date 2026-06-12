---
title: "cant boot livecd, pc always boots into windows 8"
date: 2014-03-10
forum: Installation &amp; Upgrades
---

### Post by static-warp-shell on 2014-03-10
got a new laptop and i'd like to dual boot with the preinstalled windows 8 and ubuntu.

it is an hp 255 g1 with an amd a4 apu and 4gb ram. the uefi version is insydeh20. 

i've been following this guide:

[http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html](http://www.everydaylinuxuser.com/2013/09/install-ubuntu-linux-alongside-windows.html)

i have completed all the steps up to step 5 (run the ubuntu installer).

i cant boot the livecd. i've successfully burned the iso to a dvd (i'm using the zorinos 7.1 core image which is titled zorin-os-7.1-core-64.iso, it is an ubuntu 13.04 based distro). when i put the dvd in the drive and reboot, the laptop always boots into windows 8. i've disable secure boot, disabled fast startup, and made the dvd drive 1st in the uefi boot order.

i've been skimming a lot of guides and info on this and cant find anything relevant to my issue, as most of them address boot issues that occur after ubuntu is installed. my problem is that i can't even install it because i can't boot the livecd.

---

### Post by oldfred on 2014-03-10
Know nothing about zorinos 7.1, but 13.04 is obsolete.
       EOL Notice: Raring (13.04) will be End of Life on January 27, 2014
[http://releases.ubuntu.com/13.04/](http://releases.ubuntu.com/13.04/)

Both Vendors UEFI/BIOS and Linux UEFI boot have many updates.
check that your vendor UEFI is current versions.
And better to use newest version 13.10 or 12.04.4.
Some with very new Haswell based systems find all the even newer UEFI, kernel and video updates in 14.04 work even better, but until released I cannot recommend it as a primary system.

---

### Post by static-warp-shell on 2014-03-10
i've confirmed that i have the manufacturer's latest uefi version installed on my laptop. i've read carefully the thread you pointed to: [http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

and it didn't contain any information to help me move forward - i'm unable to boot from a livecd, so the information presented on fixing boot issues with ubuntu isn't helpful at this point since i can't boot the livecd. 

after realizing that optical drives are considered legacy boot devices, i decided to try booting the image from a usb flash drive. i formatted the drive and used netbootin to add the image to it, shut down the laptop, inserted the usb drive, and turned the laptop back on. windows 8 still boots up.

so i'm still at square one here, i can't boot from any external media.

---

### Post by jaspreet on 2014-03-10
Are you able to boot a different system using the same dvd? If no then you might not have burnt the dvd right or it has gone bad.

---

### Post by static-warp-shell on 2014-03-10
thanks to usr13 in the irc channel for encouraging me to enable legacy boot despite the scary warning message i was able to boot from usb by hitting escape at startup, f9, and selecting the usb drive from the boot options menu. :)

---

### Post by oldfred on 2014-03-11
You cannot just plug a flash drive in and have it boot, unless you had previous changed UEFI/BIOS to make USB first as boot choice.
So to boot flash drive or DVD, you have to use one time boot key or UEFI menu.
With UEFI you should have two boot choices, one UEFI and the other not UEFI or BIOS but often not clear what it is.
IF you have left Secure boot on, only those systems that are secure boot will even be offered to boot.

Some systems will only boot Windows. They have modified UEFI (against UEFI std) to only boot Windows, but Boot-Repair as a work around where it will rename Windows boot file.

---

