---
title: "Grub 2 for Windows 7 and Ubuntu - Invalid Signature"
date: 2011-11-17
forum: Installation &amp; Upgrades
---

### Post by mr.swift on 2011-11-17
I've been looking through old posts for this problem and haven't been able to figure it out. I have Windows 7 installed on hd0, hd1 contains files and programs for windows, and hd2 has ubuntu installed.

Grub2 can't load windows however. If I write a script to include it, it returns 'error: invalid signature'. The os-prober that identified Windows, and includes the 'Windows 7 (loader)' option opens to the windows loading screen ("starting windows", with the wavy windows logo), and then reboots, returning to Grub.

I've attached my RESULTS.txt from the boot_info_script. Hopefully someone can help me out.

Thanks

---

### Post by raja.genupula on 2011-11-17
EDIT : sorry other post answer posted  here in a confuse

[http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/](http://www.linuxquestions.org/questions/linux-software-2/how-do-i-add-windows-xp-to-grub-boot-loader-375198/)

or look at my signature for GRUB recovery , it will update everything

have you tried to do 
**sudo update-grub **
from terminal.
 .

---

### Post by darkod on 2011-11-17
The disk that has win7 (/dev/sda) has the windows bootloader in its MBR. Which means that if you boot from this 250GB disk it should load win7 (it can't see ubuntu and will not offer an option to load it).

So, first to see if the windows loads fine because it might be a problem with windows. It looks like it, it starts to load but fails.

Grub2 will only start loading it, after that it's up to windows to load fine.

---

### Post by Mark Phelps on 2011-11-17
HOW did you shrink the Win7 OS to make room for Ubuntu? IF you used the installer, in side-by-side mode, dragging a slider, then you fell vicitim to the common problem of filesystem corruption in Win7 resulting from doing that.

You can try using the Boot-Repair utility to fix Win7 boot:

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by darkod on 2011-11-17
> **Mark Phelps said:**
> HOW did you shrink the Win7 OS to make room for Ubuntu? IF you used the installer, in side-by-side mode, dragging a slider, then you fell vicitim to the common problem of filesystem corruption in Win7 resulting from doing that.

You can try using the Boot-Repair utility to fix Win7 boot:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

They are on separate HDDs, it doesn't seem win7 was shrinked at all.

---

### Post by Mark Phelps on 2011-11-17
> **darkod said:**
> They are on separate HDDs, it doesn't seem win7 was shrinked at all.

Good point!  (Missed that)

But ... since Win7 isn't booting, using the boot-repair might get it booting again.  Since it's free, it's worth trying.

---

