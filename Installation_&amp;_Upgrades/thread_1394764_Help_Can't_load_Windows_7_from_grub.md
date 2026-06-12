---
title: "Help: Can't load Windows 7 from grub"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by jrsmee on 2010-01-31
Help.  I new to linux.  I previously was only running windows 7, and decided to give ubuntu a try.  I created two new partitions, one for ubuntu and a third (largest) as a shared storage drive.  I shrank my one windows partition, created two partitions in gparted and loaded Ubuntu 9.10.  When I restart my machine, I get 5 choices in the grub loader.  The first two are the Ubuntu ones which work fine.  The new two are the check disk, which seem fine as well.  The final one is Windows 7 (loader).  When I select the loaded, the system restarts and I'm brought back to the grub menu.  I think Windows 7 is fine, and I can access files from my windows partition from ubuntu.

In gparted, my partitions are as follows:
unallocated
/dev/sda1     system reserved (for Windows 7)
/dev/sda2                              (my windows 7 partition)
unallocated
/dev/sda3                               (where ubuntu is installed)
/dev/sda4      storage              (largest partition, ntfs)

I believe these are the relevant lines from grub:
### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
    insmod ntfs
    set root=(hd0,1)
    search --no-floppy --fs-uuid --set 4880e99080e98532
    chainloader +1

Please help.  So far I really like ubuntu, but am not willing to give up windows, at least just yet.

---

### Post by amsterdamharu on 2010-01-31
In ubuntu can you run:

```
sudo update-grub
```

Then reboot and see what happens.

---

### Post by bean123 on 2010-01-31
You can try BURG, the installation guild is here:

[http://code.google.com/p/burg/wiki/InstallUbuntu](http://code.google.com/p/burg/wiki/InstallUbuntu)

BURG support chainloading NT boot loader directly, you can edit /boot/burg/burg.cfg and modify the Windows 7 boot entry as such:

```

menuentry "Windows 7 (loader) (on /dev/sda1)" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set 4880e99080e98532
ntldr /bootmgr
}

```

BTW, you can have both grub and burg installed, to switch between them, use grub-install or burg-install to install the boot loader to MBR.

---

### Post by oldfred on 2010-01-31
When you created your new partitions did you use the window7 tools? Did you boot windows several times to make sure it worked ok with the new size. It often wants to run repairs or chkdsk to be sure it is ok after a resize.

Sometimes you have to use your windows cd to repair the windows install then reinstall grub to get everything working.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

You will need to boot with your Windows 7 installation disk. Hit Enter at the language selection prompt then hit "R" to get to the repair section. You can then select the automatic boot repair tool, but it often will not do any good. Then select the command prompt (console) and type in the following commands: 
BootRec.exe /fixmbr 
BootRec.exe /FixBoot 
BootRec.exe /ScanOs 
BootRec.exe /RebuildBcd

---

### Post by jrsmee on 2010-02-01
Thanks for all the help.  I ran the update grub, and tried again.  It now seems to work, but sometimes, when I select windows 7 (loader) it will start up, but other times, the whole computer reboots.  I reselect windows 7 (loader) and then it works.  

Oh well.

---

