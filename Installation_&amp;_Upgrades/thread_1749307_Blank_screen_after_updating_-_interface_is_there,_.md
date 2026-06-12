---
title: "Blank screen after updating - interface is there, but I can't see it"
date: 2011-05-04
forum: Installation &amp; Upgrades
---

### Post by albyr on 2011-05-04
Just upgraded to 11.04 from 10.10 and I understand I'm not the only one having a problem with a blank screen after booting.

Everything worked perfectly under 10.10; I had no complaints at all. I can use the new purple-backgrounded GRUB to boot into an older version of ubuntu, which is what I'm using at the moment to write this message.

 The first time I booted into the upgraded version I got my background wallpaper but no other interface elements. I rebooted and now whenever ubuntu boots everything looks normal until I end up with a black screen and a white mouse pointer. As I move the pointer around it changes to a cursor so it is definitely interacting with the interface, I just can't see it. I can bring up terminal windows too.

I have a Dell M65 w/ 4GB RAM. I suspect that the problem may be related to the NVIDIA video card; I'm using "version current" of the NVIDIA driver - might uninstalling this fix the problem?

---

### Post by Dutch70 on 2011-05-04
Either try nomodeset or logging in to failsafe mode until you can check for drivers.
[[COLOR="Red"]How to set NOMODESET and other kernel boot options in grub2 [/COLOR]]("http://ubuntuforums.org/showthread.php?t=1613132")

Just a thought, but if you can open a terminal window, have you tried updating?

---

