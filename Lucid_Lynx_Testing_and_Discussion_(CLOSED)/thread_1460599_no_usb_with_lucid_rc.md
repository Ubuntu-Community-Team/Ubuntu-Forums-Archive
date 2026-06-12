---
title: "no usb with lucid rc"
date: 2010-04-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by itsagony on 2010-04-23
hi,

today i tried to install lucid rc from the .iso on an older pc with nvidia nforce2 chipset.
installation from the alternate cd worked flawless.
after the first reboot there was no mouse, no keyboard actually no usb device at all.
after plugging a ps/2 keyboard to the machine to check whats going on, i found out there was no usb related module loaded at all.using the lsusb command gives no output and the command made the console stuck.
so i took the hdd from this machine and connect it to my other pc with a more moderm mobo and the rc install boots flawless with usb support.
plugging the hdd back to the old pc and booting karmic brings up a system with useable usb aswell.

so its sure the usb ports on the old pc are enabled and working (in karmic).

anybody else experienced such a problem and found a solution ? almighty google didn't had any valuable hint what could be wrong here. ) 

thanks

---

### Post by wilee-nilee on 2010-04-23
Look in the bios to make sure the usb is on. Personally I haven't seen this problem, but others may have. I would try a live cd and see if it is still acting the same way as well.

---

### Post by itsagony on 2010-04-23
hi, yes i double checked if usb is enabled in the bios. thats why usb works fine on the same machine with karmic.

but: [SOLVED]

after resetting the cmos usb works also in lucid. still beyond my understanding but it works. 

thanks

---

### Post by DougieFresh4U on 2010-04-23
> **itsagony said:**
>  [SOLVED]

after resetting the cmos usb works also in lucid. still beyond my understanding but it works. 

thanks

I am having same issue and usb works on Windows partition but not my Lucid.
How do you reset **cmos**?
Thanks

---

### Post by cariboo on 2010-04-23
Most bioses allow you to set to defaults, or you can reset it with a jumper on the motherboard.

---

### Post by DougieFresh4U on 2010-04-23
I still do not get how to 'do it', set cmos. Also, because they work on one partition, (Windows), I would still need to reset cmnos or bios?
Sorry for my ignorance on this situation.

---

### Post by psyke83 on 2010-04-23
> **DougieFresh4U said:**
> I still do not get how to 'do it', set cmos. Also, because they work on one partition, (Windows), I would still need to reset cmnos or bios?
Sorry for my ignorance on this situation.

[CMOS]("http://en.wikipedia.org/wiki/CMOS") is a physical region of your motherboard that stores the computer's BIOS configuration. Without providing your exact motherboard/computer type, nobody can show you exactly how to reset your motherboard's CMOS. Most BIOS configuration screens have a "reset to defaults" option which effectively resets the contents of the CMOS. If you check your motherboard manual it will list the jumpers that you can physically set to clear the CMOS as well.

There's no guarantee that it will fix your issue. You may need to set an option such as "support for legacy USB devices" in the BIOS configuration (which may not be enabled by default, i.e. when the CMOS is cleared).

---

