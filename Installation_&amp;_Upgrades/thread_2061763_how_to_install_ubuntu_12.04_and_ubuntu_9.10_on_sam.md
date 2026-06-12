---
title: "how to install ubuntu 12.04 and ubuntu 9.10 on same pc"
date: 2012-09-23
forum: Installation &amp; Upgrades
---

### Post by rxlord on 2012-09-23
greetings everyone,
can anybody give me step by step instructions on how to install ubuntu 12.04 and ubntuntu 9.10 on same pc.
i tried it
i had ubuntu 12.04 installed and then i installed 9.10 but it only booted in 9.10 and there was no option of 12.04 in grub.I deleted some lines in grub in 9.10 and it booted showing error 15.then
i deleted 9.10 partition and installed win 7.I still have my 12.04 partition (i have not ruined 12.04 grub file) can anybody tell me how can i boot form my 12.04 partition.
and also give me step by step instructions on how to install ubuntu 12.04 and 9.10 on same pc

---

### Post by darkod on 2012-09-23
If everything was installed correctly, grub2 from 9.10 should have picked up the 12.04 and show it in the menu. So, something happened during one install or the other.

Also, you better leave grub2 from 12.04 to be your main bootloader since 9.10 doesn't have updates any more. Why do you need to install 9.10 which is not supported any more?

On another note, grub error 15 is usually for grub1, and both 9.10 and 12.04 come with grub2 so you shouldn't be getting that error no matter what you do. If you were playing with grub and trying to use grub1 instead of grub2, then you might need to add some OSs manually. Grub2 does it automatically for you.

I recommend you simply use 12.04 since 9.10 is way too old and without support any more.

If you still want to install it, in one of the last steps of the install these is Advanced button for advanced options. There you can tell it not to install grub at all and use grub2 from 12.04.

In your case you might need to repair grub2 on the MBR right now, using the 12.04 cd to restore grub2 from your installation that you say still exists. You have instructions how to do it here:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

Make sure you use the 12.04 cd, it needs to be the same version as the one you are repairing.

---

### Post by rxlord on 2012-09-23
I want to play around with old ubuntu versions. 
and btw i loved ubuntu 9.10 boot screen and boot animation.
how can i get ubuntu 9.10 boot screen and boot animation in ubuntu 12.04

---

### Post by black veils on 2012-09-24
if you have 2-3gb ram, you could use **virtualbox** to run the old operating systems within your current operating system, like an application.

you open virtualbox application, setup/install the old system, and load it in a window (which you can make fullscreen if you want). its an easy wizard setup process, just go with the defaults, but add more ram if necessary (within reason, to allow main system to function still).

if you dont have the ram for that, you can make a persistent usb stick. its a live usb stick which is able to save settings. you can create this with **unetbootin**.

---

