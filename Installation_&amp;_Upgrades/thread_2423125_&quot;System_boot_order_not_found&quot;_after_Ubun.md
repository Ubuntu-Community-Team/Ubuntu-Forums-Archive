---
title: "&quot;System boot order not found&quot; after Ubuntu 18.04 installation"
date: 2019-07-17
forum: Installation &amp; Upgrades
---

### Post by davidnagore on 2019-07-17
Hi, this is my first post in the forum.

My problem is that, after having installed ubuntu over windows 10 (no dual boot), the tablet keeps restarting all the time. For a second, the message "System boot order not found. Initializing defaults." was shown.

I've tried the [boot-repair]("https://help.ubuntu.com/community/Boot-Repair") software, but the problem persists. This was the result: [http://paste.ubuntu.com/p/qkdPVhghrz/](http://paste.ubuntu.com/p/qkdPVhghrz/)

I also followed this instructions to repair it from grub [https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot](https://unix.stackexchange.com/questions/329926/grub-starts-in-command-line-after-reboot), and it started ubuntu, but after restarting the tablet, configuration was lost.

Could anyone give me some advice on this? Thank you very much.

---

### Post by oldfred on 2019-07-17
What brand/model tablet?

Are you able to change boot order in UEFI settings? Some systems want that not the efibootmgr change that grub uses to make ubuntu first in boot order.

A few only want to boot "Windows Boot Manager" by description. Many of those now work with UEFI updates. But using description to boot is not allowed per UEFI standard.

If you must boot "Windows Boot Manager", you can change description of shimx64.efi to boot Ubuntu to be that.

Not sure since MMC drive, if you have to be specific. This defaults to sda1.
       **D:  **Use efibootmgr

 **d1**:  If Description has to be Windows then change UEFI description. Assumes ESP is sda1.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi" 
     
If specific drive and partition required it may be like this? add - d & -p parameters, see
man efibootmgr
       
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\Boot\bootx64.efi" -d /dev/mmcblk0 -p 1

---

### Post by davidnagore on 2019-07-18
Thank you for your guidelines.

I'm working with a Chuwi H10 air tablet. It seems that changes made with efibootmgr take no effect. Even changing the "Boot options priorities" in BIOS menu doen't work. And the "UEFI hard disk drive BBS priorities" is blocked, so no changes can be made. Any ideas?

---

### Post by oldfred on 2019-07-18
Did you try creating the Windows description boot entry that really boots Ubuntu using shimx64.efi?

---

