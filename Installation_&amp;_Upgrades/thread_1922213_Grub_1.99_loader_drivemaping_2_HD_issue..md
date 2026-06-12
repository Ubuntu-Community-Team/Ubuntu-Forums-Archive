---
title: "Grub 1.99 loader drivemaping 2 HD issue."
date: 2012-02-08
forum: Installation &amp; Upgrades
---

### Post by Wilscco on 2012-02-08
Grub  1.99 loader drivemaping 2 HD issue.
Old desktop Intel 845, Pentiun 2.40, 2GB
2 Sata drives:
Hd0  with Windows Xp
Hd1 with Ubuntu 11.0

Bios booting default: Hd1 (where grub is installed)

Selecting Windows booting option sends error and Ctrl-Alt-Del reset message.

The old grub I had with OpenSuse was so simple, and drive switching-mapping worked so well with only two short code lines:  map (Hd0) (hd1),  map (Hd1) (hd0) for drives shifting
BUT now...
--------
Grub.cfg  as per Ubuntu installation:

### BEGIN /etc/grub.d/10_linux ###
if [ ${recordfail} != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "$linux_gfx_mode" != "text" ]; then load_video; fi
menuentry 'Ubuntu, con Linux 3.0.0-12-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    set gfxpayload=$linux_gfx_mode
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 6912cb7c-5808-4618-bad8-c787c2ca1f02
    linux    /vmlinuz-3.0.0-12-generic root=UUID=2adbee80-42af-442b-ad8c-edb423553483 ro  splash vga=771  quiet splash vt.handoff=7
    initrd    /initrd.img-3.0.0-12-generic
}
menuentry 'Ubuntu, con Linux 3.0.0-12-generic (modo recuperación)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod gzio
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 6912cb7c-5808-4618-bad8-c787c2ca1f02
    echo    'Cargando Linux 3.0.0-12-generic ...'
    linux    /vmlinuz-3.0.0-12-generic root=UUID=2adbee80-42af-442b-ad8c-edb423553483 ro recovery nomodeset  splash vga=771
    echo    'Cargando el disco RAM inicial...'
    initrd    /initrd.img-3.0.0-12-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 6912cb7c-5808-4618-bad8-c787c2ca1f02
    linux16    /memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd1,msdos1)'
    search --no-floppy --fs-uuid --set=root 6912cb7c-5808-4618-bad8-c787c2ca1f02
    linux16    /memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Microsoft Windows XP Professional (on /dev/sda1)" --class windows --class os {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set=root 5A64528664526533
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###
--------------
This code does not do the job for Windows Xp booting


Please help to fix the code, so mapping works and I don't have to get into BIOS to change default HD.
Thanks in advance. Wilscco
:guitar: Yes; 64 years old and I still play it: "La Vieja Banda" (Venezuela) 1960-1970's Rock&Roll

---

### Post by Mark Phelps on 2012-02-08
You shouldn't have to be doing this by hand.

Instead, boot into Ubuntu, open a terminal and enter "sudo update-grub".  That will regenerate the default GRUB config file -- and the new one should point properly to the Windows partition.

If Windows still does not start after a reboot and OS selection, then remove the Ubuntu drive and confirm that the Windows drive will boot into the desktop on its own.

---

### Post by Wilscco on 2012-02-08
Mark thanks for your answer. But it just did not work.
 Sata HD with windowsXp partitions boots fine by itself. Either leaving or removing the second sata HD with the Ubuntu 11.10 system and grub. The update via "sudo update-grub " added a new line to grub with previous system option. the WindowsXp option code remain unchanged and same error occurs

---

