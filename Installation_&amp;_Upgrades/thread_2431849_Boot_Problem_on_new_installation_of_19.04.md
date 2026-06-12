---
title: "Boot Problem on new installation of 19.04"
date: 2019-11-22
forum: Installation &amp; Upgrades
---

### Post by eddugo on 2019-11-22
Installed Ubuntu 19.04 along side windows 10 on a HP Model # 17-by1023cl.  Thought install went fine, however it will only boot into windows msaw GRUB being installed.

Tried Boot repair.  [http://paste.ubuntu.com/p/TGXS4tg6sw/](http://paste.ubuntu.com/p/TGXS4tg6sw/)
Secure boot is off

Boot repair gave me a command for the Windows command prompt to change the bootmgr, but windows came back with access denied.

thank you in advance for help getting this running.

Ed

---

### Post by oldfred on 2019-11-22
Do you have Windows fast start up off? Separate issue, but grub will only boot Windows if it is off.

Some with HP have said that changing boot order with efibootmgr does not stick. Grub install uses efibootmgr to make Ubuntu/grub first in UEFI boot order.
They did say going into UEFI and using it to change boot order worked.

# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

HP 250 G4 Ubuntu 19.04 only recognizes 8GB RAM out of 16GB, (system max 8GB)
[https://askubuntu.com/questions/1168949/ubuntu-19-04-only-recognizes-8gb-ram-out-of-16gb](https://askubuntu.com/questions/1168949/ubuntu-19-04-only-recognizes-8gb-ram-out-of-16gb)
HP Pavilion Gaming Laptop 15 -cx0049nr Disable Optane memory
[https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved](https://askubuntu.com/questions/1134503/cant-boot-ubuntu-because-windows-10-rewrites-entire-efi-partition-solved)
 HP Elitebook 745 G2  Newbie trying to install Ubuntu as dual boot  with Windows10 us
[https://ubuntuforums.org/showthread.php?t=2412901](https://ubuntuforums.org/showthread.php?t=2412901)

---

### Post by eddugo on 2019-11-23
Thank you.

I tried to turn off Fast Boot, but couldn't find it.  Looking for fast boot I came across a boot option that allowed me to switch boot to Ubuntu.  Now the problem I have is that the computer will not shut down in Ubuntu - it acts like a restart.  it will shut down if i let it reboot into windows and select power off.  is there a fix for it not powering off in Ubuntu?

Ed

---

### Post by eddugo on 2019-11-23
WAIT!  It powers off now after 2 reboots.  i think I may have it working

---

### Post by eddugo on 2019-11-23
New problem now.  The arrow and enter keys keys do not work in GRUB so it's not possible to go anywhere in GRUB except Ubuntu

---

### Post by eddugo on 2019-11-23
Arrow and enter keys will work if i choose restart when powering down ubuntu so it is possible to get to Windoze.  Is it OK to run in this configuration?

---

### Post by oldfred on 2019-11-23
If the keys do not work when booting in grub, then it usually is a UEFI/BIOS setting.
You may need to turn on USB setting or settings. Some just say full support for USB others may mention turn on keys.

---

### Post by eddugo on 2019-11-23
Mine says "USB Boot" and it's enabled

---

### Post by oldfred on 2019-11-23
Often another setting somewhere on enabling USB.
When UEFI Secure Boot is on, USB is normally off. So they have a separate setting to enable USB. That should be separate, but do not know HP and details on its version of UEFI.

---

### Post by TheFu on 2019-11-23
BTW, 19.04 support ends in about 2 months.  Before fighting too much with this, might be worth moving to 19.10 if you intend to move to 20.04 in May
or
moving back to 18.04 if you want a stable, documented, OS that is supported into 2023.

Not all Ubuntu releases are the same.  19.04 and 19.10 have experimental features. Sometimes that works well and then there are the other times, not so much.

Anyways, a few things to consider.

---

### Post by hk42 on 2019-11-23
Be very careful with USB in BIOS 
I had the case of disabling USB at Boot on a PC with only USB ports.
Then it was impossible to enter the BIOS any more :(
W10 saved me as I found ,a year later, an utility to flash BIOS from Windows.

---

### Post by eddugo on 2019-11-23
Thank you both for your help.  I'm up and running now and will move to 19.10.  I will mark this as solved.

---

