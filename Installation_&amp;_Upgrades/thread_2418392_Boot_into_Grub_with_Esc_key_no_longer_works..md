---
title: "Boot into Grub with Esc key no longer works."
date: 2019-05-06
forum: Installation &amp; Upgrades
---

### Post by stepheny on 2019-05-06
I have recently upgraded from a new install of 18.10 to 19.04. This is the only OS on the laptop. Previously if I wanted to change things in the BIOS/UEFI I pressed the Esc key during bootup and I got the Grub menu which enabled me to boot into the BIOS. Since the update I can't boot into the Grub menu. I've tried pressing Esc, Shift, Spacebar etc. but the laptop always continues into the Ubuntu login screen.

How do I boot into Grub on a one-off basis? I don't want to boot into Grub every time I boot up, just when I need to.

---

### Post by dino99 on 2019-05-06
Try F8 or F11 at early boot time

Usually that happen when only one kernel is installed

---

### Post by Rubi1200 on 2019-05-06
"Here's a list of common BIOS keys by brand. Depending on the age of your model, the key may be different.


ASRock: F2 or DEL
ASUS: F2 for all PCs, F2 or DEL for Motherboards
Acer: F2 or DEL
Dell: F2 or F12
ECS: DEL
Gigabyte / Aorus: F2 or DEL
HP: F10
Lenovo (Consumer Laptops): F2 or Fn + F2
Lenovo (Desktops): F1
Lenovo (ThinkPads): Enter then F1.
MSI: DEL for motherboards and PCs
Microsoft Surface Tablets: Press and hold volume up button.
Origin PC: F2
Samsung: F2
Toshiba: F2
Zotac: DEL"

Source:
[https://www.tomshardware.com/reviews/bios-keys-to-access-your-firmware,5732.html](https://www.tomshardware.com/reviews/bios-keys-to-access-your-firmware,5732.html)

---

### Post by stepheny on 2019-05-06
Thanks, but I did write that the Esc key worked until I upgraded to 19.04. My laptop is a [Tuxedo]("https://www.tuxedocomputers.com/en/TUXEDO-WebFAI.tuxedo") linux laptop.

---

### Post by Rubi1200 on 2019-05-06
Had never heard of them, interesting.

Well, have you tried asking them for support?
[https://www.tuxedocomputers.com/en/Contact.tuxedo](https://www.tuxedocomputers.com/en/Contact.tuxedo)

---

### Post by stepheny on 2019-05-06
I have reverted back to my 18.10 OS via a Clonezilla image and the Esc key now causes the laptop to boot into BIOS. I suspect the problem is an UEFI issue but I don't know enough about it to confirm that. All I know is that the Esc key does not boot into the Grub menu in Ubuntu 19.04 on my laptop, but it does in 18.10.

---

### Post by Rubi1200 on 2019-05-06
Not sure what to tell you, that is a bit odd.

The only other thing I might have suggested would be to edit the grub file to show the menu at startup (can be done from within Ubuntu) and then run update but if you have already reverted...

---

### Post by stepheny on 2019-05-06
Yes,  I did think of that and set the GRUB_TIMEOUT=5, but it is not as nice as having no Grub menu unless you actually want one. 

I have a few other minor issues with 19.04, for instance the touchpad doesn't work after logging in but it works in the login screen. This is not a big problem because I use a bluetooth mouse but it's not right and so I have decided to wait awhile before upgrading.

---

