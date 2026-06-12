---
title: "[SOLVED] 8.04 installation Freezes"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by melenor on 2008-05-08
I downloaded the  8.04 32-bit iso and tried to install on my computer after chooseing "language - English" and then no matter what option i choose the Disc freezes, and i have tried downloading the ISO file many times and i have checked the MD5 and it seems to work when i put it into a windows machine. Also the same thing happens after i install it within Windows, i restart (after installing) and it freezes. 

My Specs are
[LIST]
[*]AMD Athlon X2
[*]4GB DDR
[*]ATI X1800
[*]Audigy Sound Blaster SB0160
[*]and a 
[*]Hauppage TV Tuner.
[/LIST]

Any help would be much appreciated. Thanks

---

### Post by Partyboi2 on 2008-05-08
have you tried installing the 64bit one?

---

### Post by melenor on 2008-05-09
I thought that the 64-bit verison was not as much supported by the applications and users. If i can use the same applications in 64-bit i will but i was told that you couldn't. I actually might just to see if it even works. thanks.

---

### Post by melenor on 2008-05-09
Alright i have tried the 64-bit disc but ran into the same problem. i decided to try the other options. A few weeks ago i upgraded from an "Athlon 3000+" to "Athlon X2 4200+". I also installed 2GB of RAM making a total of 4GB RAM. I have no problem in Windows XP in fact i saw a much better performence now. I have no idea if this is related but just wanted to state it just in case. I really can't wait until i can get this problem resolved so that i can install 8.04, so thank you so much everyone for helping me out.





Booted into "ACPI Problem" and got this right away

[	0.000000] ata5.00: Exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[	0.000000] ata5.00: CPB resp_flags 0x11 , CMD error
[	0.000000] ata5.00: cmd c8/00:f8:3f:a0:23/00:00:00:00:00/e3 tag 0 dma 126976 in
[	0.000000] ata5.00: Status: { DRDY ERR }
[	0.000000] ata5.00: error: { UNC }
[	0.000000] 
[	0.000000] HARDWARE ERROR
[	0.000000] CPU 0: Machine Check Exception:
[	0.000000] TSC 20cbaa7a14
[	0.000000] This is not a software problem!
[	0.000000] Run though mcelog --ascii to decode and contact your hardware vendor.
[	0.000000] Kernal panic - not syncing: Machine Check

---

### Post by Partyboi2 on 2008-05-09
try adding acpi=off as a boot option to see if it helps.

---

### Post by melenor on 2008-05-09
All right, right now i booting into the ubuntu i installed within windows, i go into grub press "e" to edit and add a line and add "acpi=off" and when i try to boot that way it says that the command is unrecognized, i am not sure if i put it in worng or something else is "acpi=off" the exact command to add right before boot?

---

### Post by Partyboi2 on 2008-05-10
> **melenor said:**
> All right, right now i booting into the ubuntu i installed within windows, i go into grub press "e" to edit and add a line and add "acpi=off" and when i try to boot that way it says that the command is unrecognized, i am not sure if i put it in worng or something else is "acpi=off" the exact command to add right before boot?

When you get to grub menu, highlight the kernel you normally boot into and press "e" then highlight the line starting with "kernel" and press "e' again then at the end of the line add acpi=off then press enter then "b" to boot.

---

### Post by ssican on 2008-05-10
On this Guide: Downloading and burning an ISO of Ubuntu:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)  
there is this information:
 "You should select a slow CD writing speed (4x or 8x, as opposed to 48x). A slower writing speed is less likely to result in a badly burned CD. Badly burned Ubuntu CDs can **freeze up in the middle of booting up or installing**."

---

### Post by melenor on 2008-05-10
> **Partyboi2 said:**
> When you get to grub menu, highlight the kernel you normally boot into and press "e" then highlight the line starting with "kernel" and press "e' again then at the end of the line add acpi=off then press enter then "b" to boot.


I looked into that and i read the line and it already had "acpi=off" so i tried "acpi=on" and there was only one difference this line 

[     190.089472] Clocksource tsc unstable (delta = 468615226)

was at the very bottom

---

### Post by melenor on 2008-05-10
I decided to post the grub that is being used off the hard drive. I think that this is somehow related to my computer but i have no idea what it is or what might be wrong. Someone committed that it could be overclocking causing the problem, but i don't overclock and don't have a way to find out if anything is overclocked anyone know of a way to tell if anything is overclocked.

---

### Post by RJARRRPCGP on 2008-05-10
> **melenor said:**
> Alright i have tried the 64-bit disc but ran into the same problem. i decided to try the other options. A few weeks ago i upgraded from an "Athlon 3000+" to "Athlon X2 4200+". I also installed 2GB of RAM making a total of 4GB RAM. I have no problem in Windows XP in fact i saw a much better performence now. I have no idea if this is related but just wanted to state it just in case. I really can't wait until i can get this problem resolved so that i can install 8.04, so thank you so much everyone for helping me out.





Booted into "ACPI Problem" and got this right away

[	0.000000] ata5.00: Exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0
[	0.000000] ata5.00: CPB resp_flags 0x11 , CMD error
[	0.000000] ata5.00: cmd c8/00:f8:3f:a0:23/00:00:00:00:00/e3 tag 0 dma 126976 in
[	0.000000] ata5.00: Status: { DRDY ERR }
[	0.000000] ata5.00: error: { UNC }
[	0.000000] 
[	0.000000] HARDWARE ERROR
[	0.000000] CPU 0: Machine Check Exception:
[	0.000000] TSC 20cbaa7a14
[	0.000000] This is not a software problem!
[	0.000000] Run though mcelog --ascii to decode and contact your hardware vendor.
[	0.000000] Kernal panic - not syncing: Machine Check


Probably unstable processor core because of bad overclock. (second one) (the machine check exception)

---

### Post by melenor on 2008-05-10
how do i unclock it? i don't want anything overclocked in my machine

---

### Post by melenor on 2008-05-11
I just tried restore to default setting in my BIOS and it didn't help i still have problems any one out there that can help me?

---

### Post by melenor on 2008-05-11
By the way, i also have this problem when i try to boot into my ubuntu 7.10
[	9.332000] ata3: timeout waiting for ADMA IDLE, stat=0x440
[	9.332000] ata3: timeout waiting for ADMA Legacy, stat=0x440
[	9.332000] ata3.00: Exception Emask 0x1 SAct 0x0 SErr 0x0 action 0x0

[	9.332000] ata3.00: (CPB resp_flags 0x11: CMD error)

[	9.332000] ata3.00: cmd c8/00:f8:3f:a0:23/00:00:00:00:00/e3 tag 0 cdb 0x0 data 126976 in
[	9.332000] ata3.00: res 51/40:00:da:23/00:00:00:00:00/e3 Emask 0x9 (media error)

All my problems for ubuntu 7.10 seem to go back to when i upgraded my "Athlon 64 3000+" to an "Athlon X2 4200+" i would prefer not to have to downgrade but if anyone out there knows of a solution it would be very helpful.

---

### Post by melenor on 2008-05-11
More info i tried to use the ubuntu 8.04 64-bit live CD and i got these errors, hopes this helps.(i got the error about 4 times)

[ 87.2221893] Buffer I/O error on device fd0, logical block 0

---

### Post by melenor on 2008-05-12
I was able to resolve this by going though several test of just trying to uplug one think then boot up i finally found it. It was the partition of ubuntu 7.10 was corrupted and i had to unplug it, boot into liveCD then plug back in the drive then delete the partition and install 8.04.
Thanks Everyone.

---

