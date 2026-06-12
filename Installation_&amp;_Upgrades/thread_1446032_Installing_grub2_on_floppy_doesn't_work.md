---
title: "Installing grub2 on floppy doesn't work"
date: 2010-04-03
forum: Installation &amp; Upgrades
---

### Post by OniNiubbo on 2010-04-03
Hi all. I've just updated to Lucid from previous LTS and I've found out that:

[LIST]
[*]grub2 exists
[*]grub2 is the new boot loader
[/LIST]
I used to install grub's stage 1 to the floppy, but apparently I can't do that with grub2. I did try to go like this:
```

sudo grub-install --force --root-directory=/media/floppy /dev/fd0
sudo grub-mkconfig -o /media/floppy/boot/grub/grub.cfg

```But it creates a menu with un-bootable elements. They all give me the error 'no such device'. Here is an example of grub.cfg entry:
```

menuentry "Ubuntu, con Linux 2.6.32-19-generic" --class ubuntu --class gnu-linux --class gnu --class os {
    recordfail
    insmod ext2
    set root='(hd1,1)'
    search --no-floppy --fs-uuid --set b6aebe68-b778-43cf-ac3d-6a365e28c701
    linux    /boot/vmlinuz-2.6.32-19-generic root=UUID=b6aebe68-b778-43cf-ac3d-6a365e28c701 ro   quiet splash
    initrd    /boot/initrd.img-2.6.32-19-generic
}

```Luckly I managed to create a rescue grub2 disk with which I can boot with:
```

linux (hd1,1)/vmlinuz root=/dev/sdb1
initrd (hd1,1)/initrd.img
boot

```Those commands work only if I run them from the rescue floppy, not from the one created with 'grub-install'.
So yes, sdb1 is linux' partition and its uuid is indeed correct:
```

ls -l /dev/disk/by-uuid 
totale 0
lrwxrwxrwx 1 root root 10 2010-04-03 17:51 55585297731F26A5 -> ../../sdc1
lrwxrwxrwx 1 root root 10 2010-04-03 17:51 55fb64f5-8ec5-4d8b-a53a-0c51a1e2e658 -> ../../sdb5
lrwxrwxrwx 1 root root 10 2010-04-03 17:51 8C84E9C884E9B4BC -> ../../sda1
lrwxrwxrwx 1 root root 10 2010-04-03 17:51 b6aebe68-b778-43cf-ac3d-6a365e28c701 -> ../../sdb1

```Am I doing something wrong?

On a side note, I want my system to behave like this:

[LIST]
[*]boot without floppy -> boot straight in windows
[*]boot with floppy -> boot straight in lucid
[/LIST]
Is it possible to achieve that without installing the whole grub in the floppy? It would be cool to just 'redirect' the boot process to lucid.

---

### Post by oldfred on 2010-04-03
I cannot help on floppy issue but you are showing several drives. 

Why not have the windows boot loader in sda and grub in sdb. You set BIOS to boot sdb and can choose either Ubuntu or windows. If you want you can use the f12 (or whatever key your system uses) to one time select to boot sda?

---

### Post by OniNiubbo on 2010-04-03
The point is that I don't want to see grub menu, at least not for booting windows. And changing BIOS settings when I want to boot lucid doesn't seem practical. The floppy method seems more reasonable to me.

But your post suggested me a possible solution: install grub on sda and let it handle the issue of showing/hiding the menu.

Apparently grub2 can hide the menu and show it if shift is pressed during the booting process. It sounded great in theory, but it didn't work out.

I changed /etc/default/grub to look like this:
```

GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)"
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=-1
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```According to grub2 docs ([https://help.ubuntu.com/community/Grub2):]("https://help.ubuntu.com/community/Grub2%29:")
```

GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
```should exist for this very purpose. Wait 5 seconds. If the user presses 'shift' go on and show the menu for GRUB_TIMEOUT seconds. But nothing is easy with grub2. In fact, for some reason I can't really understand, if a user has more than one os GRUB_HIDDEN_TIMEOUT is ignored. Why? Who knows.

As a workaround this /etc/default/grub can be used:
```

GRUB_DEFAULT="Microsoft Windows XP Home Edition (on /dev/sda1)"
GRUB_HIDDEN_TIMEOUT=5
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=0
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```The GRUB_HIDDEN_TIMEOUT is ignored, so we need a little hack in /etc/grub.d/00_header. Add this at the bottom:
```

# Wait keypress
cat << EOF
if sleep --interruptible 5 ; then
  set timeout=-1
fi
EOF
```This way grub will wait 5 seconds. If the user doesn't hit any key, the menu is shown.

But the floppy issue is still there.

---

