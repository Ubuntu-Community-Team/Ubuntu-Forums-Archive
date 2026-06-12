---
title: "Re-install XP, keep Ubuntu"
date: 2008-04-18
forum: Installation &amp; Upgrades
---

### Post by joeri_83 on 2008-04-18
I've been running XP Pro (installed first) and Ubuntu (on a separate disk) for quite a while, and I enjoy Ubuntu immensely. However, my XP install just now broke down completely, with a Windows Update breaking the registry and file system, and I can't access anything. Seems like I will have to reinstall XP.

My problem then is this: If I re-install XP from scratch, will GRUB still be there, or will I lose the option to boot into my Ubuntu install? What do I need to do to avoid this, or fix it after reinstallation if that's how it works?

Any help is much appreciated.

---

### Post by Pumalite on 2008-04-18
This might help:
[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

---

### Post by joeri_83 on 2008-04-18
Thanks for the quick reply!

That seems like a solution, though it's rather scary since it's not precisly the same. My Windows install will be on hda 0 (Ubuntu on hdb I think)... This makes me worried that I will mess up trying to configure GRUB.

---

### Post by joeri_83 on 2008-04-18
Seems like just trying to repair Windows (even though I never installed anything...) threw GRUB out of the MBR, because now GRUB never loads...

Is there anyway to get the Ubuntu Live CD to recognise my Ubuntu install and just set up GRUB for me?

---

### Post by overdrank on 2008-04-18
> **joeri_83 said:**
> Seems like just trying to repair Windows (even though I never installed anything...) threw GRUB out of the MBR, because now GRUB never loads...

Is there anyway to get the Ubuntu Live CD to recognise my Ubuntu install and just set up GRUB for me?

HI and yes you can reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by joeri_83 on 2008-04-18
Thanks! I will try this. I have a 6.10 cd; does it matter if I use this, or should I first get the latest Ubuntu disc?

---

### Post by Trevster on 2008-04-18
A boot cd called Super Grub Disk is useful in situations like this. It will reinstall grub for you.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by joeri_83 on 2008-04-18
Again, thanks. Is the Super Grub Disk preferrable to the other method? Also, the instructions appears to be in Spanish which I do not speak.

---

### Post by Pumalite on 2008-04-18
It's good to have Super Grub around anyway. Both ways are effective.

---

### Post by joeri_83 on 2008-04-18
Thank you, guys!! You saved my day.

---

