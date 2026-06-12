---
title: "Windows 8 UEFI dual boot problem with Ubuntu 12.10"
date: 2013-01-24
forum: Installation &amp; Upgrades
---

### Post by jimirings on 2013-01-24
I have installed Ubuntu 12.10 on my computer that had Windows 8 pre-installed. I used the instructions on this page:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

After following the instructions through to the end, and having run Boot Repair twice, I am still unable to load Windows 8 from Grub. I am, however, able to load it from BIOS.  

Here is the boot info: [http://paste.ubuntu.com/1567295/](http://paste.ubuntu.com/1567295/)

Any suggestions to fix this would be greatly appreciated. While loading Windows from the BIOS is workable, it is certainly not ideal. 

Thanks in advance.

---

### Post by oldfred on 2013-01-24
You have 5 Windows entries in grub. The first 4 all say recovery, but the first 2 are from your efi partition and should boot Windows. The next two are from recovery partition and the last one is the bug in grub2 where it creates a BIOS type entry.

You also have the new boot into UEFI as the last entry. Does that work?

So when you boot from UEFI/BIOS and choose ubuntu, from grub menu do not the first 2 Windows entries work?

---

### Post by jimirings on 2013-01-24
Nope, none of them work. I tried them all before posting. The last one says something to the affect of "invalid EFI file path" and the rest say something like "could not load image."

---

### Post by oldfred on 2013-01-24
They look correct and generally boot repair does put in the correct entries. Do you have secure boot on or off?

Since it seems to be the path, we can try changing the search by UUID (which is the preferred way) to hard coded.

At the grub menu press e on the first Windows entry. make sure it the one with the UUID E060-6E5F and change the entire search line to this:
set root='hd0,gpt2'

See if you still get same error or not.

---

### Post by jimirings on 2013-01-25
Secure boot was on. I decided to try with it off before editing anything and it worked great! 

Thanks!

---

