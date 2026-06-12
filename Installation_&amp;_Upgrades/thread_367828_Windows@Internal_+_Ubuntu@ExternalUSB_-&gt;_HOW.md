---
title: "Windows@Internal + Ubuntu@ExternalUSB -&gt; HOW?"
date: 2007-02-22
forum: Installation &amp; Upgrades
---

### Post by msonny on 2007-02-22
Hi!

I want to do the following on my laptop.

I already have WindowsXP installed on my internal harddrive.

I tried to install Ubuntu on my external USB drive.
During install I was asked where to put GRUB, since the external drive was identified as HD0 I put it there...

I want windows to boot as normal when the external drive is NOT present.
I want to be able to choose between Windows and Ubuntu when the external drive IS present.

But after I installed Ubuntu, I now must have the external USB drive connected to be able to boot Windows. Without it connected, GRUB only gives me an errormessage.

Is it even possible to do what I want?

If so...can someone tell me what I need to do?

Please help! :)


Best regards,

Kent

---

### Post by bulldog on 2007-02-22
If you see GRUB booting from the internal disk...........you most probably installed it to the MBR of the windows disk instead of the external ubuntu disk.

You can use the recovery console of the windows install disk to repair the MBR of the windows disk using fixmbr in the recovery console.
After that you can reinstall GRUB from the live cd to the external disk if you want.

---

