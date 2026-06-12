---
title: "Ubuntu 12.10 64bits multiboot with uefi machine with win8 pre installed"
date: 2013-03-22
forum: Installation &amp; Upgrades
---

### Post by c.pfarher on 2013-03-22
Hello, I installed ubuntu 12.10 in my uefi machine with windows 8 pre installed. When power on the computer, it doesn´t show the grub menu, it just only show a violet screen and then started ubuntu....
This is de boot info generated with boot-repair
[http://paste.ubuntu.com/5638008/](http://paste.ubuntu.com/5638008/)

I need to know if it is safe to execute de recomended boot repair for showing the grub menu for access to ubuntu or windows 8 or what is the solution?? Thank you

---

### Post by harlequin_ on 2013-03-22
Hi,

Before you do anything, boot-repair or manual changes, I highly would recommend having a backup of your EFI partition, which I believe in your case is sda2 (but you must verify this yourself before moving on). Then, you can do the following (replace the xy with the corresponding letter and the digit) 
```
sudo mkdir /mnt/efi_partition
sudo mount -t vfat /dev/sdXY /mnt/efi_partition
cd /mnt
sudo tar -cvzf efi_partition.tgz efi_partition
sudo mv efi_partition.tgz /path/to/desktop/or/whatever/you/like
```

Next  you can try boot-repair, and if something goes wrong, you can extract and replace the files from the .tgz you recently created.

---

### Post by oldfred on 2013-03-22
+1 on backing up efi partition.

When Ubuntu/grub only see one installed system, it directly boots Ubuntu.

But grub2's os-prober still has a bug and creates the old style BIOS boot not the newer efi boot stanza.
If you just run this it will add Windows entries but they will be wrong. You can manually create boot stanza as shown in the bug, or just use Boot-Repair to automatically create those boot stanzas in 25_custom.

sudo update-grub

       grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
type of entry from Boot-Repair that should work.
'Windows UEFI loader'
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

