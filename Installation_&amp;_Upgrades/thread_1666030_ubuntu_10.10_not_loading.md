---
title: "ubuntu 10.10 not loading"
date: 2011-01-13
forum: Installation &amp; Upgrades
---

### Post by mervad08 on 2011-01-13
I originally had debian 4.0 on my laptop.I tried to upgrade to 9.04??? but did not load correctly.I then downloaded ubuntu 10.10 onto a cd.I he trid to load this into my laptop.The programme only goes so far then stops.I think I may need to clear my hard drive completely and need a disc to do this thus enabling me to load Ubuntu 10.10 on.I am a beginner with this so need helpand advice desperately
Robert

---

### Post by Quackers on 2011-01-13
You say the installer only goes so far then stops. Please give more details about this.
As far as wiping everything out on the disc, the installaer will do that if you choose to use the whole disc for Ubuntu installation.

---

### Post by mervad08 on 2011-01-13
Starts loading
then reads "stdin error"
This is followed by several entries either cannot execute or error on ?//
several unable to read page or unable to read data
"authentication failure"
SQUASHFS error unable to read page  484.656896]
SQUASHFS error unable to read data   484.6569551
 
Stops loading at this point

---

### Post by Quackers on 2011-01-13
Have you checked the MD5SUM of the downloaded iso file?
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
If that checks out ok, boot from the cd/usb again and press the Esc key before the purple screen. You will get a screen with a language choice, make a choice then on the next screen you will have some choices. Choose the one that checks the cd for errors.

---

### Post by mervad08 on 2011-01-14
I do not seem to be able to do the md5 check.On going to disc error check,it indicates several errors.As I copied this disc when using the original debian programme,I must hae picked up the errors then.How can I obtain an uncorrupted disc of 10.10 as I now have no means of downloading one.I am having to use another persons pc,due to this problem and they cannot download to disc.

---

### Post by dino99 on 2011-01-14
on the boot line (F6), add either: acpi=off or ide=nodma

note: when burning, always use the slowest speed

---

### Post by mervad08 on 2011-01-14
thanks,but i do notknow how to do either of your suggestions.After loading up to the staed point (in my lst message)the screen is blank and I cannot get anything
Robert

---

### Post by mervad08 on 2011-01-14
thanks,but i do notknow how to do either of your suggestions.After loading up to the staed point (in my lst message)the screen is blank and I cannot get anything
Robert

---

