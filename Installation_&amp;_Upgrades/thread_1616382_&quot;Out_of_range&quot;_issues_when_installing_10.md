---
title: "&quot;Out of range&quot; issues when installing 10.10"
date: 2010-11-08
forum: Installation &amp; Upgrades
---

### Post by GoGoGulliver on 2010-11-08
I'm currently trying to install 10.10 on my (8-year old) desktop, but I'm getting a warning that says "PC video resolution is out of range. Change setting to Recommended resolution 1924*768@85Hz".

Which would be fine, if I knew how. Is there any way to do this in the installer? I can't get any further than the "Try/Install etc" menu screen.

It has a nvidia Geforce graphics card, if that helps. I can't give you any more info than that because the specs have been lost to the mists of time and old email addresses.

If anyone can help, I'd be really grateful.

---

### Post by dino99 on 2010-11-08
[http://ubuntuforums.org/showpost.php?p=10088903&postcount=2](http://ubuntuforums.org/showpost.php?p=10088903&postcount=2)

you can use partedmagic to do it, then install from "alternate" iso and select manual installation (you need to know the / name to install on it, something like /dev/sd?, you get it when formatting)

---

### Post by P4man on 2010-11-08
but if you install the alternate, you cant test the OS, and the problem will reoccur after booting.

@GoGoGulliver,
You could try the nomodeset trick explained in my signature.

---

### Post by GoGoGulliver on 2010-11-08
nomodeset got me a little further.

Now, I have "BusyBox Built in shell"

initramfs mount mounting dev/loop0/ on /filesystem.squashfs failed: input/output error

Can not mount (the above).

Maybe I'll try the alternate install, at least then I can stumble through the terminal and install the correct driver (which I'm guessing is the first problem)

---

### Post by dino99 on 2010-11-08
this is not the ubuntu default:

**** initramfs mount mounting dev/loop0/ on /filesystem.squashfs failed: input/output error  ****

use ext3 or ext4 format

---

### Post by P4man on 2010-11-08
input output error would suggest a problem with either the install medium (or possibly your  harddrive if it had a linux version installed before, and the problem is the swap partition).

From the boot menu where you enabled nomodeset, there is also an option "test this cd for defects". Run that. See if it has errors.

---

### Post by GoGoGulliver on 2010-11-08
This is what I like about the Linux community; people fly in and help you when you need it.

Thanks everyone, I'm downloading the alternate install (assuming it was a smooshed disc or something like that, and also I really don't need all those splash screens telling me how clever I am for choosing Ubuntu).

---

