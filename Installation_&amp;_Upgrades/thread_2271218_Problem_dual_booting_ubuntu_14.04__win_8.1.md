---
title: "Problem dual booting ubuntu 14.04 / win 8.1"
date: 2015-03-28
forum: Installation &amp; Upgrades
---

### Post by brent20 on 2015-03-28
Hi,

I wanna dual boot ubuntu alongsde windows 8.1 on my Lenovo y50. Despite turning of fast and secure boot i was not able to boot from my usb drive with UEFI boot mode on. So i googled how to install it and read somewhere to change UEFI to Legacy. I did this and installed Ubuntu on the partition i made for it and also created a swap partition. Both windows and Ubuntu run just fine, but the problem is that whenever i want to change OS I have to go into my bios and change the boot mode from UEFI to Legacy and vice versa. I can get into ubuntu on Legacy and when grub pops up and I select windows it tells me I need to repair windows or something like that, but when i set boot mode to UEFI windows runs just fine.

Is there a way to change the installed Ubuntu to make it boot in UEFI mode so i never have to go into the bios again, OR make my pc boot from the usb in UEFI so i can install a fresh version of ubuntu in UEFI mode?

(edit: grammar)

---

### Post by SuperFreak on 2015-03-28
Boot Repair may fix this for you

[http://askubuntu.com/questions/401323/how-to-run-installed-windows-8-along-ubuntu-after-installing-ubuntu-in-legacy-m]("http://askubuntu.com/questions/401323/how-to-run-installed-windows-8-along-ubuntu-after-installing-ubuntu-in-legacy-m")

[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by brent20 on 2015-03-28
Thank you for the quick reply,

I installed Boot-repair and followed the instruction from the first link you provided. It did not work because boot repair gives me the error that i'm currently in Legacy mode (which is true) and that i need to run boot-repair when I boot from a USB or CD in UEFI mode...

So i'm basically back where i began, not beign able to boot from my USB in UEFI.

---

### Post by brent20 on 2015-03-28
So I figured out how to boot from usb in uefi mode. I had to boot into windows (UEFI). then hold shift and click on reboot. That brought me to a blue windows setting menu where i could click on my usb and it booted from it!

Just to be sure i ran the following line :

[ -d /sys/firmware/efi ] && echo UEFI || echo BIOS

it echoed UEFI.

I'm currently reinstalling Ubuntu and will post an update if all goed well.

---

### Post by oldfred on 2015-03-28
DO NOT use any auto reinstall options. Only use something else. See link in my signature below.

Boot-Repair in UEFI mode can convert an existing BIOS/CSM install to UEFI boot by uninstalling grub-pc and installing grub-efi-amd64.

---

### Post by brent20 on 2015-03-28
Wow, did I just dodge a bullet there!

I read your warning after I had already reinstalled ubuntu. I luckily chose 'something else'  and told ubuntu on which partition it should install itself. Now when I boot (in UEFI) grub gives me the option to boot into ubuntu or windows and both are working fine. 

Very strange that the first option said that it would erase ubuntu and install it and then it would wipe the entire drive

---

### Post by ajgreeny on 2015-03-28
Great!

Please mark as solved from the Thread Tools menu at the top.

---

