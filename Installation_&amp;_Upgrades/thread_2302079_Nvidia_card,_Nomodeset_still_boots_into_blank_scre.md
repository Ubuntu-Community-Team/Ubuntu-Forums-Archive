---
title: "Nvidia card, Nomodeset still boots into blank screen"
date: 2015-11-07
forum: Installation &amp; Upgrades
---

### Post by mat91fnd on 2015-11-07
Hello all,
I have read through [**[COLOR=#DD4814][B]MAFoElffen**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=1044547") starting thread.  I have a question
My configuration is 
[LIST]
[*]Intel Pentium 4 CPU, 2.80 GHz
[*]OS Ubuntu 14.04.3 LTS
[/LIST]
My video card (which worked with Windows XP, but so far not Linux) is
[LIST]
[*]Sparkle SFPC84GS256U2LP  --> essentially Nvidia.
[/LIST]
It booted into GRUB (step 2 in the MAFoElffen thread).  So I went into 'e' edit mode and appended "nomodeset" right after quiet splash to the Linux kernel line like this[COLOR=#ff0000][/COLOR]
[LIST]
[*]"linux    /boot/vmlinuz ......  quiet splash [COLOR=#ff0000]nomodeset[/COLOR] $(something)"
[/LIST]
Press Ctrl-X to test it, and system went into graphics just fine.
So I edit grub.cfg using sudo vi /etc/default/grub, appended nomodeset to the linux kernel line.  Did the sudo update-grub.
However, upon rebooting the system, I ended up with the blank screen instead.  So what am I missing?  Thanks.

---

### Post by ubfan1 on 2015-11-07
If you edited the grub.cfg file, update-grub rewrites it, removing your changes.  If you edited the /etc/default/grub file, then your changes should be in the new /boot/grub/grub.cfg file, are they?

---

### Post by mat91fnd on 2015-11-08
Well, I must have made a mistake somewhere.  Repeating the same process as before, Lubuntu is now booting properly with Nvidia video card.  
Here is a synopsis of what I did.

vvt@vvt-Dell-DV051:~$ sudo vi /etc/default/grub
vvt@vvt-Dell-DV051:~$ grep 'splash' /etc/default/grub
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash nomodeset"

vvt@vvt-Dell-DV051:~$ sudo update-grub
Generating grub configuration file ...
Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported.
Found linux image: /boot/vmlinuz-3.13.0-66-generic
Found initrd image: /boot/initrd.img-3.13.0-66-generic
Found linux image: /boot/vmlinuz-3.13.0-46-generic
Found initrd image: /boot/initrd.img-3.13.0-46-generic
Found memtest86+ image: /memtest86+.elf
Found memtest86+ image: /memtest86+.bin
done

vvt@vvt-Dell-DV051:~$ grep 'splash' /boot/grub/grub.cfg
    linux    /vmlinuz-3.13.0-66-generic root=/dev/mapper/lubuntu--vg-root ro  quiet splash nomodeset $vt_handoff
        linux    /vmlinuz-3.13.0-66-generic root=/dev/mapper/lubuntu--vg-root ro  quiet splash nomodeset $vt_handoff
        linux    /vmlinuz-3.13.0-46-generic root=/dev/mapper/lubuntu--vg-root ro  quiet splash nomodeset $vt_handoff

nomodeset can be seen in the grub.cfg after update-grub was run.
I learned a bunch of things about GRUB and Linux that I didn't know before.  Thanks for help and explanation.  ;)

---

