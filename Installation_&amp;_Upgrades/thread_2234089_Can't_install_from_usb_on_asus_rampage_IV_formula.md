---
title: "Can't install from usb on asus rampage IV formula"
date: 2014-07-12
forum: Installation &amp; Upgrades
---

### Post by jeffrey-hollis1 on 2014-07-12
I have searched everywhere for an answer to this. 

System specs:

asus rampage iv formula
intel i7 3930k
ripsaw ram 8 gig
geforce gtx 680 sli
3 hardrives
ssd corsair neutron
barracuda 2tb
ssd samsung


i have installed ubuntu on 32 gig USB with pen drive installer. No issues. I have used linux virtual box and the program loads fine on windows 7. So no issues with file integrity. 

When I boot to usb from bios I can get to the purple splash screen. I hit shift, click English, f6 and put on no modest, acpi=off. I hit enter and get a flashing cursor. 

I have changed fastboot to off. I have turned secure boot off. ACHI controllers on all drivers. I selected other OS instead of  UEFI. 

i have  no idea what to do. I loaded with no splash to see where error lies. No kernel panicks. 

Any help would make my day.

---

### Post by mooreted on 2014-07-12
Looks like several people have had trouble running that board. I don't know the answer, but I found a couple of things to try:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)

---

### Post by jeffrey-hollis1 on 2014-07-12
Yeah I'm combing through it.  Nothing is sticking out to me. I've seen threads where people claim they can install on the IV formula board. I think the board is the issue.

---

### Post by jeffrey-hollis1 on 2014-07-12
My problem is solved.

I unplugged my CD drive connected to my mother board. 

It works with no issues. Installed just fine.

I don't know what to say.....

edit: Let more clarify one extra thing. I did reconnect the cd drive to motherboard and the error occurred again. It's safe to say that ubuntu could not load the drivers for it for whatever reason.

---

