---
title: "Toshiba laptop will only boot using live cd after installing Ubuntu mate"
date: 2018-11-25
forum: Installation &amp; Upgrades
---

### Post by loughja on 2018-11-25
Hi,

I’m a newbie with Linux. I have a Toshiba Satellite C55D-B5308 laptop that had windows 8 originally installed. I installed Ubuntu Mate 18.04 amd64 and now the laptop will only boot from a live cd. I installed and ran Boot Repair in the live session, but it didn’t correct the boot issue. Here’s the url that Boot Repair gave me: [http://paste.ubuntu.com/p/C4kDgrh7q9/](http://paste.ubuntu.com/p/C4kDgrh7q9/)

Any help is much appreciated!

---

### Post by oldfred on 2018-11-27
Have you checked to see if there is an UEFI update for your system. If best to update it.

Some Toshibas only want to boot Windows.
One work around is to boot "Windows" by description, but actually boot shim/grub to boot Ubuntu.

       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 

Then see if "Windows" entry in UEFI boots Ubuntu.

---

