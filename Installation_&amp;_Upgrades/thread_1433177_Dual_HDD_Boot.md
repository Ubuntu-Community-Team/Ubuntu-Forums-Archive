---
title: "Dual HDD Boot"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by -tr on 2010-03-18
Hi guys, (hopefully) simple question here. How can I set up my pc where it default boots to my main HDD with Windows 7, and a secondary HDD with ubuntu after pressing F12 or something? 

I was going to just do a dual boot, but I remembered I had this extra HDD sitting around (which I was 'borrowing' from walmart for something I can't remember and lost the receipt =s) so I figured I'd just install ubuntu to it and dual boot like that.

Thanks for any help. =)


EDIT: Disregard that. Just installed Ubuntu to my second HDD and it booted to the grub loader, which had the Windows 7 option in it. However, I do have one more question: as I'm still using the Windows 7 RC (which expires pretty soon), will a clean install of Windows 7 overwrite the grub loader seen on startup? If so, how do I go about booting back into the second HDD to reinstall grub?

---

### Post by oldfred on 2010-03-18
It is easy to install grub2 from your working system to another drive. 

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sda"  then just run: 
sudo grub-install /dev/sda 
If that returns any errors run: 
sudo grub-install --recheck /dev/sda 
Then: 
sudo update-grub

If you set your second drive to first to boot in BIOS it will boot that copy of grub.

---

