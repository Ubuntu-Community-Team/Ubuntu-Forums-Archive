---
title: "GRUB boot problems"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by kob0724 on 2008-11-25
So here's my dilema.
I have two internal hard drives. In the beggining, the master had Windows on it and the slave had ubuntu on it. I later decided it would be fun to try arch linux on my computer. So I resized my windows partition and put arch linux on it. Archlinux wrote a new grub menu, but after fooling around I was able to add Ubuntu to the menu.lst file in Arch.

Today I decided I wanted to do a clean install of 8.10. I erased my hard drive with ubuntu on it and installed 8.10 succesfully on it. However when I went to boot into it from my archlinux grub menu, I found that did not work. I get an error that says
```

GRUB ERROR 13: invalid or unsupported executable format


```

Here is my arch liunx menu.lst file
```

# (0) Arch Linux
title  Arch Linux
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/0c98488f-b7e2-4d31-9f04-06c1d8e4e009 ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,1)
kernel /boot/vmlinuz26 root=/dev/disk/by-uuid/0c98488f-b7e2-4d31-9f04-06c1d8e4e009 ro
initrd /boot/kernel26-fallback.img

title           Ubuntu
rootnoverify            (hd1,0)
makeactive
chainloader +1

 (1) Windows
title Windows
rootnoverify (hd0,0)
makeactive
chainloader +1

```

Here is the current ubuntu menu.lst (I can still boot into arch and look at it from there)
```

title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            df5805b0-72dd-4aae-b680-1b7235c0178e
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=df5805b0-72dd-4aae-b680-1b7235c0178e ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet

title           Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid            df5805b0-72dd-4aae-b680-1b7235c0178e
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=df5805b0-72dd-4aae-b680-1b7235c0178e ro  single
initrd          /boot/initrd.img-2.6.27-7-generic

title           Ubuntu 8.10, memtest86+
uuid            df5805b0-72dd-4aae-b680-1b7235c0178e
kernel          /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title           Windows Vista/Longhorn (loader)
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Arch Linux (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/vmlinuz26 root=/dev/disk/by-uuid/0c98488f-b7e2-4d31-9f04-06c1d8e4e009 ro
initrd          /boot/kernel26.img
savedefault
boot

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Arch Linux (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/vmlinuz26 root=/dev/disk/by-uuid/0c98488f-b7e2-4d31-9f04-06c1d8e4e009 ro
initrd          /boot/kernel26.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sdb2.
title           Arch Linux Fallback (on /dev/sdb2)
root            (hd1,1)
kernel          /boot/vmlinuz26 root=/dev/disk/by-uuid/0c98488f-b7e2-4d31-9f04-06c1d8e4e009 ro
initrd          /boot/kernel26-fallback.img
savedefault
boot



```


Here are some solutions I have tried that HAVE NOT WORKED

1.
From a terminal in arch linux I tried doing the following
```

$ grub
> root (hd1,0)
> setup (hd1)
> quit
$ exit

```

2. Adding the map commands to my ubuntu entry in my arch linux menu.lst
```

title           Ubuntu
rootnoverify            (hd1,0)
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1



```

---

### Post by icanfly0307 on 2008-11-25
Hey there,
                   In your Arch Linux Grub file, ***replace this:***

t[I]itle           Ubuntu
rootnoverify            (hd1,0)
makeactive
chainloader +1[/I]

***with this:***

[I]title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            df5805b0-72dd-4aae-b680-1b7235c0178e
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=df5805b0-72dd-4aae-b680-1b7235c0178e ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet
[/I]
As far as I know, you can't boot Ubuntu because the Arch Linux Grub file can't figure out the kernel for Ubuntu. All that I did above was replace the Ubuntu entry in the Arch Grub file with the Ubuntu entry from the Ubuntu Grub file. It's just a matter of simple copying and pasting.

Let me know what happens and I'll help you out further if you need it. Good Luck! :)

---

### Post by kob0724 on 2008-11-25
> **icanfly0307 said:**
> Hey there,
                   In your Arch Linux Grub file, ***replace this:***

t[I]itle           Ubuntu
rootnoverify            (hd1,0)
makeactive
chainloader +1[/I]

***with this:***

[I]title           Ubuntu 8.10, kernel 2.6.27-7-generic
uuid            df5805b0-72dd-4aae-b680-1b7235c0178e
kernel          /boot/vmlinuz-2.6.27-7-generic root=UUID=df5805b0-72dd-4aae-b680-1b7235c0178e ro quiet splash
initrd          /boot/initrd.img-2.6.27-7-generic
quiet
[/I]
As far as I know, you can't boot Ubuntu because the Arch Linux Grub file can't figure out the kernel for Ubuntu. All that I did above was replace the Ubuntu entry in the Arch Grub file with the Ubuntu entry from the Ubuntu Grub file. It's just a matter of simple copying and pasting.

Let me know what happens and I'll help you out further if you need it. Good Luck! :)

My bad. I forgot to mention I already tried this solution. If I try to do what you suggested above I get this grub error:
```

ERROR 15: File not found

```

---

### Post by ajgreeny on 2008-11-25
Try replacing the line:-

[I]uuid            df5805b0-72dd-4aae-b680-1b7235c0178e

[/I]with the more normal, in older grub menus anyway, :-
[I]
root   (hd0,1)[/I]

changing the hd0,1 to whatever Ubuntu is on, of course.  I suggest this because I tried to boot Ubuntu 8.10 from my main 8.04 install's grub menu and got nowhere when I just copied the grub entry from 8.10's grub menu.  Only by changing the entry to show the root (hd1,0) did it to work.  Here's my entry:-

# This entry added manually by AJG after installing Ubuntu 8.10
title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=d71efa88-3f27-47df-a077-6d2ebb317999 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet

---

### Post by kob0724 on 2008-11-25
> **ajgreeny said:**
> Try replacing the line:-

[I]uuid            df5805b0-72dd-4aae-b680-1b7235c0178e

[/I]with the more normal, in older grub menus anyway, :-
[I]
root   (hd0,1)[/I]

changing the hd0,1 to whatever Ubuntu is on, of course.  I suggest this because I tried to boot Ubuntu 8.10 from my main 8.04 install's grub menu and got nowhere when I just copied the grub entry from 8.10's grub menu.  Only by changing the entry to show the root (hd1,0) did it to work.  Here's my entry:-

# This entry added manually by AJG after installing Ubuntu 8.10
title        Ubuntu 8.10, kernel 2.6.27-7-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.27-7-generic root=UUID=d71efa88-3f27-47df-a077-6d2ebb317999 ro quiet splash 
initrd        /boot/initrd.img-2.6.27-7-generic
quiet


HEY! THAT DID IT! Many thanks!!!!

---

### Post by ajgreeny on 2008-11-26
Great!  I gather this is because the version of grub in 8.10 is later than that in 8.04, and the 8.04 version is not able to read the *uuid* line.  This was nearly a breaker for me and it was only luck that I found that difference between the grub entires and sorted the problem.

---

