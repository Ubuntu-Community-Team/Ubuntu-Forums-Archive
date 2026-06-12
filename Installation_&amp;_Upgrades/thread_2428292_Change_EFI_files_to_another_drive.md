---
title: "Change EFI files to another drive"
date: 2019-10-02
forum: Installation &amp; Upgrades
---

### Post by andorift on 2019-10-02
Hi,

[https://paste.ubuntu.com/p/3rHTw8KGBt/](https://paste.ubuntu.com/p/3rHTw8KGBt/)

My SSD Disk located at **sda** is failing and I reinstalled ubuntu in a new HDD [B]sdb.

[/B]I just noticed after transferring the personal files that I failed at the installation process and the EFI boot files are at **sda1 **instead of [B]sdb1

[/B]I want to remove from the system the SSD at sda and just want the system to boot from [B]sdb1 
[/B]
¿Is there any way faster than uninstalling the SSD and reinstalling the whole system again?


Thx a lot in advance.

---

### Post by oldfred on 2019-10-03
You can totally reinstall grub2, often easier with Boot-Repair. That uses efibootmgr to specify drive & partition.
Or you can copy /EFI/ubuntu & /EFI/Boot from sda to sdb's ESP and use efibootmgr to create UEFI boot entry to use boot files on sdb's ESP.

See
man efibootmgr

Some examples in link in my signature.

       sudo efibootmgr -c -l "\EFI\ubuntu\shimx64.EFI" -L ubuntu -d /dev/sdX -p Y
where /dev/sdX is the disk and Y is the partition number of ESP.
[http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected](http://askubuntu.com/questions/668506/changed-the-uefi-motherboard-on-a-dell-laptop-now-it-says-no-os-detected) 
   The switches and options state: -c create new entry on -d disk, on -p partition, -w write unique signature into MBR if needed, and use -L label to mark the new entry. You can use any label you want. The partition number must match your ESP.

---

### Post by andorift on 2019-10-04
I did it with boot-repair the app you suggested.

Thx a lot for the help.

---

### Post by oldfred on 2019-10-04
You can change to [Solved], so others may find thread and a solution.

---

