---
title: "Dell Optiplex GX270"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by dellowner on 2010-12-14
I received a Dell without a harddrive or OS on it, so a friend reccommended putting Ubuntu as my OS, I downloaded the ISO and burned it to a disk. When I put the disk in I tried it out to see what it would look like, it worked fine for me then. But when i installed it onto a 40 gb PATA drive, the problems started. It went through the installion without a problem but when it told me to restart i did and after the Dell screen it went to a black screen with just a flashing text line like this _ i let it sit there for about an hour to see if it was just loading the drivers but it still did nothing. Can someone tell me what might be wrong?

---

### Post by sikander3786 on 2010-12-15
Press down and hold Shift key from Bios screen until you see the Grub menu. Highlighting the first entry there, press 'e' to edit it. Navigate to words "quiet splash", delete them and type "nomodeset" in their place (without quotes). Press Ctrl + X to continue boot. Can you see the desktop now?

If not, you may need to try that step 3 more times and replace 'nomodeset' with one of these every step.

1. i915.modeset=1
2. i915.modeset=0
3. xforcevesa

If that doesn't help, we need to know more about your hardware. Specially graphics card and RAM.

Let us know how that goes.

---

### Post by dellowner on 2010-12-18
Hey thanks for the response, I got to the GRUB menu but there was nothing showing except for the word GRUB, does this mean i need to download a GRUB loader?

---

### Post by sikander3786 on 2010-12-19
> **dellowner said:**
> Hey thanks for the response, I got to the GRUB menu but there was nothing showing except for the word GRUB, does this mean i need to download a GRUB loader?
That is strange. Boot an Ubuntu Live CD and post the output of bootinfoscript as per instructions here to let us take a look at your boot.

[http://bootinfoscript.sourceforge.net](http://bootinfoscript.sourceforge.net)

While posting, click the # icon in post menu and paste your text in between the generated code tags.

---

