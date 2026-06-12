---
title: "Sda wiped and deleted after failed installation wizard"
date: 2022-06-08
forum: Installation &amp; Upgrades
---

### Post by artusso on 2022-06-08
Hi, 
I've tried to install ubuntu on my new laptop I bought second hand  (Asus S56CM-XX085h) windows was installed but not working trying to repair some stuff I don't really know.

I made a bootable usb and tried ubuntu 22.04 LTS and it seemed to work great. I then tried to make a minimal installation but with third party drivers included, secure boot unchecked.
I chose my SSD (sda) to install it on and just 2-3 minutes later I get an error sda ext4 installation failed and now I can't see my sda anymore. Only sdb and sdc.

My laptop is still on. What can I do to make it work ?
I have no data to save or backup it was my first time booting it up.

---

### Post by artusso on 2022-06-09
Up

---

### Post by tea for one on 2022-06-09
If the live session seemed OK with 22.04, why not try it again?
Perhaps the installation will complete if you avoid the minimal installation choice.
Depending on the age and condition of this second-hand  laptop, Ubuntu may not be the best OS choice i.e. Lubuntu/Xubuntu may be more suitable.

You can check if your sda disk has re-appeared using gparted in the live environment.

Lastly, you mentioned  [COLOR="#0000FF"]"windows was installed but not working trying to repair some stuff I don't really know"[/COLOR] -possibly, the laptop may have an unknown hardware problem?

---

### Post by Impavidus on 2022-06-09
So the hard drive (the actual device, not some partition or filesystem) disappeared after you attempted to write something to it. That sounds like broken hardware. Maybe it's just a loose connector.

---

### Post by #&amp;thj^% on 2022-06-09
> **Impavidus said:**
> So the hard drive (the actual device, not some partition or filesystem) disappeared after you attempted to write something to it. That sounds like broken hardware. Maybe it's just a loose connector.

+1
And OP stated windows was wonky for  what ever reason, and a 2nd hand laptop, connectors or the drive itself.
Op said live environment worked ok. so that narrows things down a bit.                   ^^^^^^^^^^^^^^^^^^^^^^^^^^^

---

### Post by artusso on 2022-06-10
The computer turned off and now it shows a black screen when I'm powering it on. The bios doesn't seem to be loading

---

### Post by tea for one on 2022-06-10
When you power on the PC, are you tapping the dedicated key to access the BIOS (or UEFI)?

---

