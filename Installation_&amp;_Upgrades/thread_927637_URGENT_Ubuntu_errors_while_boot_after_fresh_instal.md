---
title: "URGENT: Ubuntu errors while boot after fresh installs (pic included)"
date: 2008-09-23
forum: Installation &amp; Upgrades
---

### Post by go_beep_yourself on 2008-09-23
Tried Ubuntu desktop and alternate installer with the same results. I disabled splash and quiet from the boot options and used my friends phone camera to take this picture of the errors. Booting stops here. Sorry I couldn't get a clearer picture with a phone, but I editted it with some software the best I could.

[IMG]http://ubuntuforums.org/attachment.php?attachmentid=86168&d=1222169009[/IMG]

---

### Post by lukjad on 2008-09-23
Ummm... There's no pic.
Okay, it's there.

So, how long have you left it idle there? 30 min?

---

### Post by go_beep_yourself on 2008-09-23
> **lukjad007 said:**
> Ummm... There's no pic.
Okay, it's there.

So, how long have you left it idle there? 30 min?

Tried leaving it there all night, happens every time.

---

### Post by lukjad on 2008-09-23
First, have you checked the cd for defects? Have you run a md5sum?

Can you boot to a live CD? First try an Ubuntu Live CD then another version of Linux.

---

### Post by go_beep_yourself on 2008-09-23
> **lukjad007 said:**
> First, have you checked the cd for defects? Have you run a md5sum?

Can you boot to a live CD? First try an Ubuntu Live CD then another version of Linux.

This is my friends computer. He got the same problem with the live cd of 8.04.1 (desktop installer), and now I installed raid 0 with the alternate installer. All went well during the install, but it locks up the same during boot. He really likes Ubuntu, don't think he's going to want to switch distros. He's found it the easiest to use.

Before installing, when I got to the first menu, I choose "check cd for defects", and it said the cd was fine.

---

### Post by lukjad on 2008-09-23
Is this an older PC? If so, it may be that the hardware is not able to handle it. Can you boot to Ubuntu from a live cd?

---

### Post by go_beep_yourself on 2008-09-24
> **lukjad007 said:**
> Is this an older PC? If so, it may be that the hardware is not able to handle it. Can you boot to Ubuntu from a live cd?

No, it's a quad core intel 3ghz w/9 series nvidia card. I'm running ubuntu in raid 0 and it boots up fine now with agp=no added to the boot kernel parameter in grub.

---

### Post by lukjad on 2008-09-24
All fixed? Great! Sorry I couldn't be of more help.

---

