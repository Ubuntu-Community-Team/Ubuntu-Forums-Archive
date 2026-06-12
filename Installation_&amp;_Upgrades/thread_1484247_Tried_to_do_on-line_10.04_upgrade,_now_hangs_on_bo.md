---
title: "Tried to do on-line 10.04 upgrade, now hangs on boot"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by PabloTempe on 2010-05-15
Hello All,
 
I was really enjoying the speediness of 9.10 on my HP Pavilion ze4900. Once I got the wireless driver loaded correctly, anyway.
 
Tried to do an on-line upgrade to 10.04, but figured I should have had a hard-wired internet connection when I got installation messages that "Could not set up..." the network. But, installation continued without any other apparent issues.
 
As soon as it rebooted at the end, the problem started. It hangs right after the ubuntu logo, with a completely blank screen.
 
My questions:
 
1) Can I get this to start booting properly?
2) If not, what would be the best way to retrieve my evolution mail files, so I can do a clean install? If I boot from a CD, will I be able to retrieve those files and maybe put them on a memory stick? 
 
Appreciate any help from the gurus.
 
Thanks, Pablo

---

### Post by kansasnoob on 2010-05-15
> **PabloTempe said:**
> Hello All,
 
I was really enjoying the speediness of 9.10 on my HP Pavilion ze4900. Once I got the wireless driver loaded correctly, anyway.
 
Tried to do an on-line upgrade to 10.04, but figured I should have had a hard-wired internet connection when I got installation messages that "Could not set up..." the network. But, installation continued without any other apparent issues.
 
As soon as it rebooted at the end, the problem started. It hangs right after the ubuntu logo, with a completely blank screen.
 
My questions:
 
1) Can I get this to start booting properly?
2) If not, what would be the best way to retrieve my evolution mail files, so I can do a clean install? If I boot from a CD, will I be able to retrieve those files and maybe put them on a memory stick? 
 
Appreciate any help from the gurus.
 
Thanks, Pablo

You may be able to complete/repair the upgrade in a chroot:

[http://ubuntuforums.org/showpost.php?p=8068512&postcount=10](http://ubuntuforums.org/showpost.php?p=8068512&postcount=10)

If you need more detailed help please post the output of the Boot Info Script:

[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

If you decide to try this I'd absolutely recommend doing so with a wired connection :)

---

### Post by oldfred on 2010-05-15
I think you are past grub boot issues and into Ubuntu issues which are often video related.

Can you from the grub menu boot into the recovery mode? What video driver are you using?

this was what I had to do to get into low graphics mode:

On first boot after install, press e on getting the GRUB bootloader.
Using arrow keys navigate to and delete quiet and splash and type the word nomodeset in their place
Press Ctrl and X to boot (low graphics mode)

---

### Post by captaincoredump on 2010-05-16
Pablo --

I have had exactly the same problems on my HP ZE4900.  I solved them this way:

(1) choose the "recovery mode" boot option for Ubuntu 10.04 LTS (likely displayed as kernel 2.6.32-22-generic (recovery mode) when you boot
(2) when you receive a "Recovery Menu" (which will be a low-tech, ASCII-style menu), select the failsafeX option.  You can move to this option using the arrow keys on your keyboard.
(3) when you receive a message that you are running in low-graphics mode, click on OK (there really is no other choice).
(4) select the "Run Ubuntu in low-graphics mode for just one session" option; I believe this is the first option presented, although they are not numbered.
(5) click on OK.

I found that Ubuntu presented me with a login screen, and I could continue as I normally would (enter password, etc.).  After logging in, everything appeared to work properly, and I was able to configure my desktop, etc.  I hope this works for you and you can (continue to) enjoy Ubuntu.

regards,

-captaincoredump

---

