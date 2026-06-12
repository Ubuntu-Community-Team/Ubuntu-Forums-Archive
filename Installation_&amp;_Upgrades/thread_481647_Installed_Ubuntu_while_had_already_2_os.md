---
title: "Installed Ubuntu while had already 2 os"
date: 2007-06-22
forum: Installation &amp; Upgrades
---

### Post by murzim on 2007-06-22
Well, here is my problem.

I got a 120GB hd. I had installed an old 64bit beta xp version on it (on C, the first i installed).

Then I made a partition (110GB on C and 10 more on D) and I installed on D a windows xp 32bit for the programs i could not run in 64bit.

After a series of various problems, i fed up and made one more partition where I installed another 32bit version. This was installed in G: So I found myself using the G: partition, booting from there and logging into the 32bit xp system.

Then yesterday, I formatted the D: section and installed ubuntu there after making another one partition of 700mb for the swap file (moving just the D part). I logged in the ubuntu system just fine, getting as sda5 the part  the xp 32 i was using so far and as sda1 the old C partition with windows 64.

So far so good, the problem starts when I try to log into the xp32 system. It say that ntoskrnl.exe is corrupted or missing and it cannot go further (it is not missing though, checked from ubuntu).

The most weird thing is when I boot from the windows xp cd, it recognizes that my xp 32 version is installed on the driver D while in fact it was on G.


I believe that there is some sort of collision after the ubuntu installation. I am not aware what exactly happened but its a messy situation for sure.

Anyone know something that may help ?

Thank you very much before hand.

---

### Post by Jose Catre-Vandis on 2007-06-22
Have you tried a repair on your xp32? Doesn't sound like an ubuntu/grub problem more a windows problem. you may need to copy over the ntoskernel.exe file in any case, as it may have become misplaced or corrupted. When I ever got this under windows it was usually a reinstall or a repair to fix

---

### Post by murzim on 2007-06-22
I tried to repair but I guess I will try again. I just thought because it happened shortly after the ubuntu install, this would have been because of the installation.

I will report back anyway.

Thx

---

### Post by murzim on 2007-06-22
ok, ressolved it.

It was entirely a windows problem, perhaps solved solely through windows but still I guess ubuntu had to do with it.

For future reference here is how I got it fixed:

-Booted from Windows XP cd
-Runned the repair console
-Typed bootcfg /rebuild
-I picked which installations I wanted to boot
-Then replaced the file (expand cddrive:\i386\ntoskrnl.exe windowsdrive:\windows\system32 (Y for overwriting).

Then rebooted and all fine once more.

Note that only replacing the file didn't work. The boot.ini was a bit messed up it seems.

Thx

---

