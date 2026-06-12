---
title: "Triple booting WinXp, Ubutu 6.10 and FC6"
date: 2006-12-27
forum: Installation &amp; Upgrades
---

### Post by igeldard on 2006-12-27
Hi,

I'm trying to multiple boot WinXPSP2 and various Linux distros and have managed to dual-boot WinXP with Ubuntu 6.10 no problem. My problem is triple booting with Fedora Core 6.

WinXP is on the first partition of hd0 (/dev/hda1) and Ubuntu is on /dev/hda3. GRUB is installed on the MBR and is happy with

title Ubuntu, kernel 2.6.17-10-generic
root (hd0,2)
kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

and

title Microsoft Windows XP Professional
root (hd0,0)
savedefault
makeactive
chainloader +1

I have an unformatted partition and created part of this as /dev/hda4

I edited /boot/grub/menu.lst to include

Title empty partition in hda4
Root (hd0,3)
Chainloader +1

That worked OK on reboot so I installed FC6 in hda4 and didn't select a GRUB install

That didn't work, so I tried

title Fedora Core (2.6.18-1.2798.fc6)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/1 rhgb quiet
initrd /boot/initrd-2.6.18-1.2798.fc6.img
boot

But that wouldn't boot either (note that I copied the kernel and initrd from another FC6 posting and that could be wrong - how do I find the correct values?)

Any ideas?

Ian

---

### Post by igeldard on 2006-12-27
> **igeldard said:**
> Hi,

title Fedora Core (2.6.18-1.2798.fc6)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-1.2798.fc6 ro root=LABEL=/1 rhgb quiet
initrd /boot/initrd-2.6.18-1.2798.fc6.img
boot



Changed this to 

title 		Fedora Core (2.6.18-1.2798.fc6)
root 		(hd0,3)
kernel 		/boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hda4 ro quiet splash
initrd 		/boot/initrd-2.6.18-1.2798.fc6.img
quiet
boot		

And it booted ok, though the setup process in FC6 did not seem as smooth as with Ubuntu 6.10 - blank screens, mystery logout and a lot of update downloading. 

Still I now have a triple boot system, now for a quad boot. But how, in principle, does one find the vmlinuz/initrd values of a distro before installation? 

Ian

---

### Post by louieb on 2006-12-27
I haven't figured out how to find out before hand what kernel file name is.
In the past when I installed a 2nd distribution I did not  let it install grub.
I booted to the first distribution  and used its file browser to look in the newly installed distribution /boot directory to get the kernel name and then add the entry to menu.lst.
Now thanks to Herman and his [Dual Boot site]("http://users.bigpond.net.au/hermanzone/") I let the new distribution put grub in the partition that I installed it to. Then it is a matter of going back to the first distributions menu.lst and and adding a chain loading entry for it. 
Check out Herman's site he explains it much better that I can.

---

### Post by igeldard on 2006-12-28
> **louieb said:**
> Now thanks to Herman and his [Dual Boot site]("http://users.bigpond.net.au/hermanzone/") I let the new distribution put grub in the partition that I installed it to. Then it is a matter of going back to the first distributions menu.lst and and adding a chain loading entry for it. 

I tried that with an entry for FC6 in Ubuntu's GRUB's menu.lst as

title empty partition in hda4
Root (hd0,3)
Chainloader +1

FC6 went in hda4, and bootloader was installed on / not MBR, but it wouldn't boot with the above entry so I had to enter it as

title Fedora Core (2.6.18-1.2798.fc6)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hda4 ro quiet splash
initrd /boot/initrd-2.6.18-1.2798.fc6.img
quiet
boot 

Any ideas why the chainloader method didn't work?

Ian

---

### Post by confused57 on 2006-12-28
> **igeldard said:**
> I tried that with an entry for FC6 in Ubuntu's GRUB's menu.lst as

title empty partition in hda4
Root (hd0,3)
Chainloader +1

FC6 went in hda4, and bootloader was installed on / not MBR, but it wouldn't boot with the above entry so I had to enter it as

title Fedora Core (2.6.18-1.2798.fc6)
root (hd0,3)
kernel /boot/vmlinuz-2.6.18-1.2798.fc6 root=/dev/hda4 ro quiet splash
initrd /boot/initrd-2.6.18-1.2798.fc6.img
quiet
boot 

Any ideas why the chainloader method didn't work?

Ian

You might want to try:
title empty partition in hda4
root  (hd0,3)
chainloader +1

As louieb mentioned, this only works if the Fedora Core grub is installed to it's root partition...if it's not, you can reinstall it using a live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by igeldard on 2007-01-02
> **confused57 said:**
> You might want to try:
title empty partition in hda4
root  (hd0,3)
chainloader +1

As louieb mentioned, this only works if the Fedora Core grub is installed to it's root partition...if it's not, you can reinstall it using a live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

Tried that, but get a grub error 13: Invalid or unsupported executable format

Ian

---

