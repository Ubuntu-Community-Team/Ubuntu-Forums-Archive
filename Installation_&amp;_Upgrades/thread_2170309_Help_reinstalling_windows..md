---
title: "Help reinstalling windows."
date: 2013-08-25
forum: Installation &amp; Upgrades
---

### Post by jakev3 on 2013-08-25
I need to reinstall windows 7 on my computer, but I am having some issues. 

I used WinUSB to make a bootable USB with a copy of windows 7 iso from Digital River, a licensed distributor of Microsoft software. When I went to boot from the usb it either a) booted directly into ubuntu or b) went to the gnu grub menu with no option to boot from usb. I know that my computer can boot from a usb because I used a usb to install Ubuntu. I am running 13.04 and have the most up to date grub version. 

I have no idea what to do and couldn't find any info after searching for hours. 

All help is greatly appreciated! Thanks in advance.

---

### Post by Quackers on 2013-08-25
There will be a key to press during boot to enter the boot choice menu. If it's an older pc there will be an option in BIOS to set for booting from a USB.
By getting to the grub menu you are getting past the stage where you can choose to boot from USB.

---

### Post by jakev3 on 2013-08-25
I already set the BIOS up to boot from external device. I also tried pressing the key to enter the boot menu and it said the was no OS found. Could it be an issue with the image on the memory stick? Would trying a DVD work better?

---

### Post by Quackers on 2013-08-25
It's possible, if the BIOS is actually looking at the memory stick when it gives that error.
Does your bios detect the memory stick? On an older laptop of mine I had to select to boot a USB drive in order to detect my memory stick. Others actually detect the stick as a memory stick.
Do you have another pc to try that stick with?

---

### Post by jakev3 on 2013-08-25
I'm assuming my BIOS can detect the memory stick because it did it without a problem when installing Ubuntu. I'm not sure how I would double check that. 
I'm testing the stick on another computer now.

---

### Post by jakev3 on 2013-08-25
It appears as though the usb doesn&#8217;t work. I tried it in another computer and was able to select boot from usb but the system just loaded into the installed OS. No errors were given it just went straight to the log in screen.

---

### Post by Quackers on 2013-08-25
Hmm maybe it is faulty then.
Do you still have the recovery partition on this pc or was it over-written when you installed Ubuntu?

---

### Post by jakev3 on 2013-08-25
I accidentally overwrote everything when I installed and I have no recovery disk hence the memory stick.

---

### Post by Quackers on 2013-08-25
Not the best way to go about it really. Making the recovery discs and also a repair disc is always best.
I would have thought any downloaded copy of the same version of Win 7 that you had installed would install ok with your product key. Maybe something else to look at.

---

### Post by jakev3 on 2013-08-25
Hmm. Is there a good program to make a DVD instead of a memory stick?

---

### Post by Quackers on 2013-08-25
From a downloaded .iso file?
You could do that with Brasero or K3b in the Ubuntu live desktop. The failure rate would normally be higher than with a USB though (at least in my experience).
In fact you could load the Ubuntu live desktop (or Ubuntu if it's still bootable) and view what's on that memory stick. You could possibly even extract the .iso from it, though I'm not sure how you could do that exactly (it's been a while since I did anything like that).

---

