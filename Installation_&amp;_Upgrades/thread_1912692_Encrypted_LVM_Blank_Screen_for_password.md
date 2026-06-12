---
title: "Encrypted LVM Blank Screen for password"
date: 2012-01-21
forum: Installation &amp; Upgrades
---

### Post by Cookie11 on 2012-01-21
Hi everyone,

I am having the following problem:

After a fresh install of 64 bit encrypted LVM Ubuntu, grub complains with "Error: No video mode activated", and doesn't display the password prompt for LVM. I can type it in "in the dark" and if I don't make any mistakes, it then boots fine.

I was able to avoid video mode all together by uncommenting "GRUB_TERMINAL=console" in /etc/default/grub and do a "sudo update-grub", however, that would only display the grub boot options, the LVM screen was still black.

This seems to be related to [http://ubuntuforums.org/showthread.php?t=1762702](http://ubuntuforums.org/showthread.php?t=1762702), although that thread is now quite old.

Interestingly, I did an install of 32 bit, exactly same setup, a few hours earlier, and it worked fine. Although that previous install was of a CD, and the second of a USB disk with the 64 bit alternative installer iso. But then I figure since I have run update-grub a couple of times at least my grub must be in the right place...

Anyway, does anyone have an idea for a fix? Or alternatively, can I force LVM to use the console? Ctrl+Alt+F1 and so forth had no effect.

Thanks

---

### Post by ti1ion on 2012-03-11
I would like to get help with the same issue.

Just installed 64 bit 12.04 and have the same problem.  I found the solution to resolve the error, but the enctyption password screen is blank.

Thanks.

---

### Post by Herman on 2012-03-11
I just think of it as an extra security feature.
If an attacker doesn't know they're supposed to type a password, it would likely delay them indefinitely. However, I know to give the OS a minute or so after the GRUB Menu and then try typing my password. :)

---

### Post by ti1ion on 2012-03-29
So, it appears that I may have resolved my issue.  In my case, I am using a brand new Dell 6420 laptop with an Nvidia graphics card.  I installed the proprietary driver (for a different reason) and now I am able to see the encryption password screen on boot.  It may be this is a problem with the open source video driver.

Herman, I decided to look at the issue the same way you did and was just going to live with it.

---

### Post by Herman on 2012-03-29
Aha! That's very interesting ti1ion, and that reminded me of something else as well. 

****Here is a link to an very well written how to from back in the GRUB Legacy days, **[HOWTO: Change bootup resolution]("http://www.ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters").**

I'm not too sure if there's a newer equivalent to that excellent how-to around anywhere, (updated for GRUB2 and more recent versions of Ubuntu). I imagine much of the information there would still apply or at least I think it's still worth a read.

---

