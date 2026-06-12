---
title: "install 13.04 on asus ux32a, problems with usb boot"
date: 2013-05-18
forum: Installation &amp; Upgrades
---

### Post by jamaas on 2013-05-18
I can't seem to get the machine to boot from the usb disk that I made. I suspect it has something to do with this UEFI disk setup but I have no idea how to fix it ... I get "This is not a bootable disk. Please insert .... "  Does anyone have a simple solution or where to look for one?  I have dug around but no luck. This machine does not have a cd drive so has to be usb stick.

Thanks

J

---

### Post by fantab on 2013-05-18
Reads to me like a bad burn. Burn the .iso again to USB and try again.

---

### Post by jamaas on 2013-05-18
Right on the money, thanks fantab!  :-)
J

---

### Post by rhysphillips on 2013-06-23
Hi there jamaas,

Did you get Ubuntu running successfully on the UX32A?

Rhys

---

### Post by jamaas on 2013-06-24
Yes, it seems to work quite well and I've not made any serious changes.

Jim


> **rhysphillips said:**
> Hi there jamaas,

Did you get Ubuntu running successfully on the UX32A?

Rhys

---

### Post by rhysphillips on 2013-06-29
Great cheers for the reply. I installed Ubuntu 13.04 in about 20mins onto my new UX32A Zenbook without any problems at all! Everything works fine, even the function keys to adjust keyboard lighting which some people said wouldn't work.

---

### Post by iisjman07 on 2013-06-29
> **rhysphillips said:**
> Great cheers for the reply. I installed Ubuntu 13.04 in about 20mins onto my new UX32A Zenbook without any problems at all! Everything works fine, even the function keys to adjust keyboard lighting which some people said wouldn't work.

No issues with a black screen on bootup? I remember 12.x had issues with booting but you've convinced me to give it a go...

---

### Post by teo.g.georgiev on 2013-11-08
Hey guys, first time question here.

I'm having the same problem and am really stuck. It's the UX31A, initially with Windows 7.

I can insert the USB into whichever usb port I want and restart/shutdown-reboot the computer and the result is always the same: it boots into Windows 7.

I've created a dual boot system eight times now without a single fault but this one won't go. Any suggestions? I've already disabled Fast Boot or Instant On or whatever Asus was calling it (this was a setting not in BIOS but in Windows). And I really can't find Secure Boot. Customer service told me it wasn't there.

---

### Post by jamaas on 2013-11-08
One thing I did recently with mine was to download the most recent bios from ASUS and flash the bios.  The newer one gives better control of bootup options  I think.  However flashing a bios is not for beginners so only do it if you know what you are doing and follow the instructions to the letter!

Are you using the esc key during bootup to get the different options?  Have you tried the bootable usb stick you created into another computer to confirm that it works?  I've found the Ubuntu package "create startup disk" really dodgy and tempermental.  If often doesn't work, have to repeat several times and try a few different memory sticks.  I would first confirm that your bootable usb stick is a good one ... try it on anther computer.

HTH,

J

---

### Post by teo.g.georgiev on 2013-11-08
Thanks to Jamaas, but I figured my problem out after a good night's rest. This has never happened before and I don't know why you would do this, but the ASUS BIOS that came with this had not only Boot Priorities (which were correct by default, hooray!), but also HDD Priorities (which were not correct by default, boo!).

I did not have to download the newer BIOS and would rather not. I do not consider myself clever enough to mess with BIOS beyond what I absolutely must do. But I will keep the suggestion in mind if it ever becomes necessary.

Thanks to everyone, hopefully this wasn't too much spam for you, but for a while I really was stuck and considering returning the laptop.

---

