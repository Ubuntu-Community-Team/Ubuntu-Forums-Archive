---
title: "Live USB Problems (Jaunty)"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by r11_kaede on 2010-02-28
Hi guys,

1) I tried to upgrade from Hardy Heron via Update Manager.

2) Some packages could not be installed, so I had to restart my computer, and then I got a series of errors, and I cannot login to the main menu. Ctrl-Alt-F2 works, but I'm only at my Home folder, I can't get into root, I think.

3) I tried installing Jaunty via Live USB, but my HP Mininote 2133 refuses to boot from USB.

Any help here will be appreciated.

Thanks. :)

---

### Post by garvinrick4 on 2010-02-28
Some machines will not boot from USB. I would say to use a Live CD and see if you can mount your drive. Should be able to. Then chroot into it and download upgrade aqain then
sudo apt-get -f install.

Easier if you are wired. If wireless have to make your drive mounted have the same etc/resolv.conf  as the Live CD's. That gives you internet wireless. 

If you do not know how to chroot to get into a drive to fix it now is the time to learn. 

Lets try to repair this.

You did go into your BIOS and change it to boot off of USB first or second right, before HD.

---

### Post by r11_kaede on 2010-02-28
Hi,

Thanks for the reply. Unfortunately, I can't use a Live CD (I have no CD drive, internal/external), so USB is my only option.

Yes, I did select USB above HDD, and I also selected USB as my boot device, just to be sure.

Still no joy.

Thanks :)

---

### Post by garvinrick4 on 2010-02-28
Have you tried more than 1 USB stick. If recognizes a boot flag on install should boot?

These mini machines are made to boot off of USB. That is what they claim. They better.

Anything else to report?

---

### Post by r11_kaede on 2010-03-01
They are supposed to, yes. When I first got it, I could install Hardy off USB easily.

Anyway, I formatted my hard drive using KillDisk, and then reloaded Jaunty on my USB using UNetBootin.

Instead, the system directs me to the recently used - KillDisk, instead of loading from USB, even if I pressed F9 and selected USB directly.

Could it be a BIOS problem?

---

