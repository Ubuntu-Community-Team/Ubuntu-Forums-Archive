---
title: "Grub error 21 on fresh install to second hard drive"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by pchemist on 2007-04-29
Last night, I installed Ubuntu (feisty) onto the (new) second hard drive of a machine which has previously run Windows XP for two years. (So, dual boot setup by someone with low-mid linux experience)

Installation proceeded without errors, but when I restarted, I was immediately faced with  grub "error 21".

Got online from another computer, and discovered that this meant a drive could not be found. I booted back into the liveCD, and was able to mount both the old and new drives and confirm that the contents are still there, and that drives can be read.

However, at the moment, this also means I can't load either windows or Linux. Am currently using my desktop machine as a lovely paperweight. How to fix the error and regain use of at least one OS?

(Also, if it involves editing a file by booting into the LiveCD, that seems to mount my second, linux hard drive as read-only, so a note on how to change that would be helpful)

Thanks in advance, and I'll be happy to add more info as needed.

---

### Post by confused57 on 2007-04-29
You might want to go into your bios setup and make sure that the controller for your 2nd hard drive is enabled, or set to "auto" or "on".  Also, make sure your jumper settings are correct on the hd, if it's IDE.

---

### Post by sewercake on 2007-04-29
I just had this problem a couple of hours ago, and it turned out that my second hard drive was knocked about and the cords were a little off. I have no idea if this will help, but check on the BIOS to see if it recognizing both drives, just a thought. Another thing you could try is unplugging, then plugging back in the drives, there is a slight possibility it will work then.
cheers



-Sewercake

---

### Post by pchemist on 2007-04-29
Thanks- actually, changing the setting in BIOS did the trick. I'd assumed that the ability to read the drive and install an entire OS meant I could gloss over that.... I think the real trick is to not install an OS without the benefit of coffee. :D

Appreciate the help much, and now off to enjoy the new linux install.

---

