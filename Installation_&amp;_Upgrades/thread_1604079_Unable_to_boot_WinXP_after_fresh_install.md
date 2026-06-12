---
title: "Unable to boot WinXP after fresh install"
date: 2010-10-23
forum: Installation &amp; Upgrades
---

### Post by 0akash0 on 2010-10-23
Dear All;

I thank you in advance for your help, I have some proprietory softwares installed on WinXP so it is very important for my work that it is up and running.

I performed a FULL INSTALL from the Live-CD (10.10) and installed grub on the windows partition.
Now whenever I try to select the Windows option in the Grub menu, the screen goes blank and it gets me back to the Grub menu.

Please Help. :confused::confused::confused:

---

### Post by drs305 on 2010-10-23
Please post the results of forum member *meierfra's* boot info script, found at:
[http://bootinfoscript.sourceforge.net/]("http://bootinfoscript.sourceforge.net/")
Post the contents between "code" tags, which you generate with the # icon in the menubar.

It will give us a good idea of what is happening on your system.

---

### Post by Ubuntows Rocks on 2010-10-23
> **0akash0 said:**
> Dear All;

I thank you in advance for your help, I have some proprietory softwares installed on WinXP so it is very important for my work that it is up and running.

I performed a FULL INSTALL from the Live-CD (10.10) and installed grub on the windows partition.
Now whenever I try to select the Windows option in the Grub menu, the screen goes blank and it gets me back to the Grub menu.

Please Help. :confused::confused::confused:

Just checking but you did choose install alongside another System right?

---

### Post by 0akash0 on 2010-10-23
Is this what was required???

And no, I did not choose the "alongside" option, I changed the partitions while installing, had some NTFS partitions, which I deleted and made swap, "/" partitions.

[PHP]### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"
if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  insmod vbe
  insmod vga
}

insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
if loadfont /usr/share/grub/unicode.pf2 ; then
  set gfxmode=640x480
  load_video
  insmod gfxterm
fi
terminal_output gfxterm
insmod part_msdos
insmod ext2
set root='(hd0,msdos6)'
search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
set locale_dir=($root)/boot/grub/locale
set lang=en
insmod gettext
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
menuentry 'Ubuntu, with Linux 2.6.35-22-generic' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0cc2ca7b-ade9-420d-b964-d4f5f90613d0 ro   quiet splash
    initrd    /boot/initrd.img-2.6.35-22-generic
}
menuentry 'Ubuntu, with Linux 2.6.35-22-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
    echo    'Loading Linux 2.6.35-22-generic ...'
    linux    /boot/vmlinuz-2.6.35-22-generic root=UUID=0cc2ca7b-ade9-420d-b964-d4f5f90613d0 ro single 
    echo    'Loading initial ramdisk ...'
    initrd    /boot/initrd.img-2.6.35-22-generic
}
### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###
### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
menuentry "Memory test (memtest86+)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
    linux16    /boot/memtest86+.bin
}
menuentry "Memory test (memtest86+, serial console 115200)" {
    insmod part_msdos
    insmod ext2
    set root='(hd0,msdos6)'
    search --no-floppy --fs-uuid --set 0cc2ca7b-ade9-420d-b964-d4f5f90613d0
    linux16    /boot/memtest86+.bin console=ttyS0,115200n8
}
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows NT/2000/XP (on /dev/sda1)" {
    insmod part_msdos
    insmod ntfs
    set root='(hd0,msdos1)'
    search --no-floppy --fs-uuid --set 12100948100933ef
    drivemap -s (hd0) ${root}
    chainloader +1
}
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###[/PHP]

---

### Post by 0akash0 on 2010-10-23
Thank you for your quick response,
 
I searched in the the link that was posted above and went and did this:
 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)
 
i.e. used testdisk and backupBS
 
Now, I can boot into windows, but it is only showing me the windows bootloader and not grub.

---

### Post by drs305 on 2010-10-23
You should be able to reinstall Grub from the LiveCD Desktop. If installed correctly, you will then be able to boot both Ubuntu and Windows.

From the LiveCD, mount your Ubuntu partition. Looking at your previous post it should be on sda6. If different, change the partition number below. Note you include the partition number:
```
sudo mount /dev/sda6 /mnt

```
Next, install Grub. Note you do NOT use the partition number:
```
sudo grub-install --root-directory=/mnt/ /dev/sda
```

Reboot and you should have a choice of either OS. If you don't, once you have rebooted, open a terminal and run:
```
sudo update-grub
```

---

### Post by ronparent on 2010-10-23
Don't mean to be picky but that should be:
> sudo mount /dev/sda6 /mnt
and
> sudo grub-install --root-directory=/mnt/ /dev/sda

I guess it's ground into my consciousness after doing it enough. lol

---

### Post by 0akash0 on 2010-10-23
Dear All;

Thank you very much for your quick responses and taking time to help me out. It worked and both the o/s's are booting properly.

+++ karma

---

### Post by drs305 on 2010-10-23
> **ronparent said:**
> 
I guess it's ground into my consciousness after doing it enough. lol

It actually works either way. I've never been consistent so I tried it in various combinations. I really should pick one and stick to it though. Adherence to strict standards should probably be a goal for me.

---

### Post by ronparent on 2010-10-23
OK, that makes some sense. I guess the root / has to be designated one place or the other!

---

