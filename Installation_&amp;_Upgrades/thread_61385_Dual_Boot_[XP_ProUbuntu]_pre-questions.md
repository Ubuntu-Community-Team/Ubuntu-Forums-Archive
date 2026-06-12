---
title: "Dual Boot [XP Pro/Ubuntu] pre-questions"
date: 2005-08-31
forum: Installation &amp; Upgrades
---

### Post by eelozano on 2005-08-31
Hello,

I am going to go from Ubuntu to Ubuntu/WinXP Pro dual boot.  The reasoning being that although I am comfortable with Ubuntu some others who I allow to use my laptop are not.  I feel that dual booting while giving Windows a smaller partition would be a good compromise.

My only concern is that I would like the dual boot to go as smoothly as possible.  I have read that I should install XP Pro first because windows seems to have its way with the Master Boot Record.

Are there any other things I should be aware of (perhaps some configuration that I may need to do while dealing with the bootloader (grub?).  

Any suggestions are greatly appreciated.

---

### Post by c0rderr0y on 2005-08-31
no you should be fine windows is added automatically into grub.

---

### Post by izmaelis on 2005-08-31
I dual boot between Ubuntu and Windows XP Pro with no problems. Although I do boot to Win very rarely it wotks ok. Here is mine /boot/grub/menu.lst:
```

default         0
timeout         10

title           Ubuntu, kernel 2.6.10-5-686
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.10-5-686 root=/dev/hda7 ro quiet splash
initrd          /boot/initrd.img-2.6.10-5-686
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,6)
kernel          /boot/memtest86+.bin
savedefault
boot

title           Other operating systems:
root

title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

```
And yes I installed Win before installing Ubuntu. I think I escaped messing arround with install/reinstalling MBR by doing so.

---

