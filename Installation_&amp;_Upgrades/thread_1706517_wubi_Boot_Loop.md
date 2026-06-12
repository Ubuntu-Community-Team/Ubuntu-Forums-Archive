---
title: "wubi Boot Loop"
date: 2011-03-14
forum: Installation &amp; Upgrades
---

### Post by Jwoofter on 2011-03-14
I recently upgraded my computer to windows 7. I previously had XP with wubi working great but I wanted to get a taste of 7.

I tried to install wubi again on my new 7 and everything went fine up until I restarted. When I choose wubi from the boot selection at start up it just restarts then comes back to the selection screen. I can boot into windows just fine but wubi just loops.

How can I solve this? 

I have tried erasing the install and reinstalling and i have also tried running chkdsk after the install but no luck. I couldn't think of or find anything else to try.

thanks

---

### Post by bcbc on 2011-03-14
Are you saying it reboots on the 'first reboot' where you choose Ubuntu? Or did you get Ubuntu installed, see the slide-show, run some updates and then it reboots (if so see the [wubi megathread]("http://ubuntuforums.org/showthread.php?t=1639198"))
What version of ubuntu are you installing? An old 10.04?

---

### Post by Jwoofter on 2011-03-14
Yea on the first time I select Ubuntu on the bootloader it just reboots the computer each time I click it. Ubuntu has not once booted up.

I'm trying to install the latest 10.10 but I did try using 10.04 but it did the same thing.

---

### Post by bcbc on 2011-03-14
> **Jwoofter said:**
> Yea on the first time I select Ubuntu on the bootloader it just reboots the computer each time I click it. Ubuntu has not once booted up.

I'm trying to install the latest 10.10 but I did try using 10.04 but it did the same thing.

That's strange. I've never heard of this. I think with wubildr.mbr (grub4dos) you can hit the INSERT key rapidly to get some debug info. It's worth a shot. 

[http://diddy.boot-land.net/grub4dos/files/basics.htm](http://diddy.boot-land.net/grub4dos/files/basics.htm)  This link has some background info on entering debug mode. Note there are some differences with wubi (grldr.mbr and grldr are renamed wubildr.mbr and wubildr, and also wubildr chains to grub2 so there is no menu.lst). Because of these differences I'm not sure the INSERT key will work the same but hopefully you'll get some useful info.

Also try defragging your computer. Sometimes this can affect wubildr.

---

