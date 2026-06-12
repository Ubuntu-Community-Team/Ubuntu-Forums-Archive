---
title: "How to remove unwanting boot imag folder?"
date: 2011-02-17
forum: Installation &amp; Upgrades
---

### Post by F8M on 2011-02-17
According to oldFred, I need to remove the extra Windows boot image folder in my Ubuntu/Windows dual-boot system.

sdb1: __________________
    File system:       ntfs
    Boot sector type:  Windows Vista/7
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /boot/BCD /Windows/System32/winload.exe 
                       /boot/grub/core.img

I need to remove the last line only "/boot/grub/core.img and anything else related to it BUT NOT /boot/BCD.
Any suggestions would be helpful. Thank you.

---

### Post by quixote on 2011-02-18
The commands to delete files and folders are as follows.  You'll need to do them as "sudo" since these are system files.  Also, since these are system directories, if you make a mistake or typo you could destroy your whole installation.  So be super-careful!

```
sudo rm /boot/grub/core.img
```will remove the file "core.img".  Any other related files that need to be removed you have to find and remove the same way: "sudo rm /path/to/filename"

If you need to remove a folder, the command is ```
sudo rmdir /path/to/dir/
```The folder has to be empty for this to work.  I.e., delete the files inside first using "rm".

Triple check that you have the right path and filename, because there's not much you can erase with impunity in /boot and its subdirectories.

---

