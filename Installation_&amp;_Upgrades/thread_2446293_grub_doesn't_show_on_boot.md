---
title: "grub doesn't show on boot"
date: 2020-06-27
forum: Installation &amp; Upgrades
---

### Post by rahmann7854 on 2020-06-27
I've installed Ubuntu 20.04 after installing Windows 10 (both on GPT)
but grub doesn't show on boot and windows still boots directly
I've tried to use boot repair and here is the link to the report generated in Pastebin
[https://paste.ubuntu.com/p/zZBPDFjXmh/](https://paste.ubuntu.com/p/zZBPDFjXmh/)
I can't access my uefi firmeware settings to try to do something about it

---

### Post by yancek on 2020-06-28
Your boot repair output is minimal and much of what is generally shown is not there for some reason.  You seem to be missing some Grub files, particularly the grub.cfg file which is your boot menu.  Your inability to access the BIOS firmware is your biggest and the first problem you will have to resolve.  You might post some info on the manufacturer or hardware and someone familiar may be able to help.i

---

### Post by VMC on 2020-06-28
Is the USB device plugged in when you boot, or did you pull it out then re-boot?
[I'm looking @ the efibootmgr output.]

edit: also did you read this section:> If your UEFI firmware does not allow to change the boot order, change the default boot entry of the Windows bootloader. For example you can boot into Windows, then type the following command in an admin command prompt:
bcdedit /set {bootmgr} path \EFI\ubuntu\shimx64.efi

---

