---
title: "Jmicron problem Solved?"
date: 2006-11-03
forum: Installation &amp; Upgrades
---

### Post by antaresdark on 2006-11-03
Hi all, i need to known if JMicron problem was solved in the last & recent version (6.10) for those who have a 965P chipset in the motherboar like me.
I have a Gigabyte GA 965P DS3 motherboard with Core 2 Duo e6300. 

Have a **ubuntu-6.10-desktop-amd64.iso** download in progress.. it will work?

Thanks 
Antares

---

### Post by antaresdark on 2006-11-03
I'm again
Looking in the activity log for bugs i found that the fix was released (the last post minus 5 )
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502/+activity](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502/+activity)
but nothing tell that the fix was included in the ubuntu 6.10 kernel.
Any with the 6.10 version working in this hard ?

Antares

---

### Post by towsonu2003 on 2006-11-03
> **antaresdark said:**
> I'm again
Looking in the activity log for bugs i found that the fix was released (the last post minus 5 )
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502/+activity](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502/+activity)
but nothing tell that the fix was included in the ubuntu 6.10 kernel.
Any with the 6.10 version working in this hard ?

Antares

According to this [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502) a fix was released for 6.10 ("linux-source-2.6.17", which means if you upgrade your kernel you will get the fix as long as you have edgy) but not yet for 6.06 (linux-source-2.6.15).

---

### Post by antaresdark on 2006-11-04
Ok thanks, i have not 6.06, only 6.10 this mean that the fix in incuded in this version? (Yes/No)

OT: finally i have the iso burned in rewritable CD, but when try to boot inmmediatly after detects DVD and show "ISOLINUX .... "
I have this message
"isolinux: Disk error 80, AX = 4280, drive FF"
Now i'm re-burning the iso which have a correct md5 sum perhaps it be a bad burn but, its strange i've checked this in VmWare under Win XP and boots ok, and the live cd works well ... ¿?

Antares

---

### Post by towsonu2003 on 2006-11-04
> **antaresdark said:**
> Ok thanks, i have not 6.06, only 6.10 this mean that the fix in incuded in this version? (Yes/No)
not sure. you might wanna ask that in the bug report as
"I downloaded the iso image from the ubuntu website. does it include the fix?"

it is *possible* that the iso from this site includes the fix:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

> 
OT: finally i have the iso burned in rewritable CD, but when try to boot inmmediatly after detects DVD and show "ISOLINUX .... "
I have this message
"isolinux: Disk error 80, AX = 4280, drive FF"
Now i'm re-burning the iso which have a correct md5 sum perhaps it be a bad burn but, its strange i've checked this in VmWare under Win XP and boots ok, and the live cd works well ... ¿?
sorry, I have no idea what that means. make sure you burn with a very slow speed (1x or 2x perhaps).

---

### Post by antaresdark on 2006-11-04
OK for the first.

the OT:
Have changed the "Onboard SATA/IDE ctrl mode" to **IDE** works fine but the same CD in **AHCI** mode wont boot: "isolinux: Disk error 80, AX = 4280, drive FF" the strange thing is in others distros (Kernel >= 2.6.18) the only way to get linux working is setting the AHCI mode in the BIOS.

BUT finally in Live CD mode in partition step Qparted Hangs :(

Antares

---

### Post by BananaJoe on 2006-11-04
Hello, i would like to know the same.. :KS 

When you tried it, please tell me if all on the Board like LAN, Sound, etc does work with 6.10.

Thanks

---

### Post by antaresdark on 2006-11-04
Hello BananaJoe seems that all works well in live CD mode, for the onboard NIC connector i don't known my PC isn't networked and i don't put an eye on this. the only conection i have is an SpeedTouch 330 USB modem (cheap hardware for windoze grrrr) don't work.

Antares

---

