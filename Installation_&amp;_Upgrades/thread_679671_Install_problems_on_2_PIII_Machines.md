---
title: "Install problems on 2 PIII Machines"
date: 2008-01-27
forum: Installation &amp; Upgrades
---

### Post by Paul5910 on 2008-01-27
Hello every one!  I Just installed Ubuntu 7.1 on my P4 machine and it works great!  I am trying to install it on a couple of P3 machines and it keeps freezing during the install.  I did try a couple of different hard drives (I have plenty) without success.  I do have plenty of memory in both machines (512 or better.)  I also tried Xubuntu and it froze during installation as well.  I have tried installing well over 25 times (for the last week or so) and it just keeps freezing up at different points in installation.. I thought I might have an over heating problem, so I left the side cover off and turned a fan on it on high speed with no difference.... HELP

Paul

---

### Post by az on 2008-01-27
Did you run memtest?

Did you check the cd integrity?

---

### Post by Pumalite on 2008-01-27
Try hitting 'e' at boot and adding this to the boot parameters: 
no apic nolapic acpi=off
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by Paul5910 on 2008-01-27
I think I have done the memory test and CD check, but will do them both again.  I am 3/4 through another install attempt, so I will try these when she freezes again.  I will also try the ACPI=off as well.  Thanks for the feedback and I will let you know what happens.

Paul

---

### Post by Paul5910 on 2008-01-29
I did run the mem and cd check and both are good.  Can you tell me what the command you recommended is supposed to do?

Paul

---

### Post by louieb on 2008-01-29
The kernel has boot options. most of the time the defaults work.
Here a couple of lists for Debian based distributions.
[BootOptions - Ubuntu Documentation]("https://help.ubuntu.com/community/BootOptions")
[Cheat Codes - Knoppix Documentation Wiki]("http://www.knoppix.net/wiki/Cheat_Codes")

But iin the case of the P2 don't think thats the problem. If it were me I try the alternate text based install  CD. You may have just not given it enough time. I have a pretty good wait at about 80-85% 
Good luck

---

### Post by DRPend on 2008-01-29
If this continues to be a problem consider running an install on an older build. I had trouble with some PIII's trying to install Fiesty Fawn, but when I went to Dapper Drake it ran fine.  I suspect that the default driver base is just too far off on some of the newer builds. Once you get the older build running copy out all you conf files to offline storage and run and upgrade. not the tidiest way to do business, but at least you can get somewhere. Most of the problems were with old PIII 500's, but it's probably more of an issue with which onboard peripherals you have (audio/video, etc...  the ACPI fix is supposed to help with power management driver issues, but can only fix so much. Canned Dell and Gateway systems will give you the most headache, so if your using one of these then I'd say that's your problem. Newer installs also like to set up the USB mouse and the old machines run PS/2 mice. I've had this create problems too.

---

