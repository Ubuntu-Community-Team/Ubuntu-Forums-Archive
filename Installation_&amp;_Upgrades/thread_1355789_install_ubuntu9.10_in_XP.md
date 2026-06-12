---
title: "install ubuntu9.10 in XP"
date: 2009-12-15
forum: Installation &amp; Upgrades
---

### Post by weishigoname on 2009-12-15
I want to install ubuntu in XP ,
I use grub4dos tool,extract grldr and menu.lst into c:\,and extract vmlinuz and initrd.lz in ubuntu-9.10-desktop-amd64.iso's casper directory into c:\.
and add below in menu.lst :
              title Install Ubuntu
              root (hd0,0)
               kernel /vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-desktopamd64.iso locale=zh_CN.UTF-8
initrd /initrd.lz
 
and I copy  ubuntu-9.10-desktopamd64.iso into c:\
 
and add "c:\grldr="Install Ubuntu" " in boot.ini,
and then restart ,select Install unbuntu,and get in.
 
in livecd,I use command "sudo umount -l /isodevice" and then install,
The partition below:
 
        /dev/sda8   boot           ext3
       /dev/sda9    /               ext 4
      /dev/sda6    /home        ext4
      /dev/sda7   swap         
but 
after that ,I reboot ,in windows xp ,I remove initrd.lz,vmlinuz,and menu.lst ,and then reboot ,
the grub do not change ,when I  select "Install ubuntu"
 
error occur:
      Booting "Install Ubuntu"
  filsystem type is ntfs, partition type 0x07
kernel /vmlinuz boot=casper iso-scan/filename=/ubuntu-9.10-desktop-amd64.iso lcale=zh_CN.UTF-8
error 15:file not found

---

### Post by darkod on 2009-12-15
Do you want to install INSIDE win XP or side-by-side (next) to win XP?
In either case, the steps you're trying are not necessary.
If you want to install inside windows, it's called wubi install, just execute the wubi.exe file from the ubuntu cd. ALso if you already have the ISO on your hdd, put the ISO and the wubi.exe file in same folder and execute wubi.exe and it will install inside windows.
If you want to install next to windows and dual boot, do not create any partitions for ubuntu from windows. Just make sure you have unallocated space on the hdd, either by deleting some partitions or shrinking them, then boot with the ubuntu cd, select Install Ubuntu option and let it use the available free space.

---

### Post by MelDJ on 2009-12-15
see: [https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by nitstorm on 2009-12-15
or if you want to run ubuntu and windows at the same time, why not try a virtual machine? i think VMware supports 64-bit OS's now....

---

