---
title: "Grub Menu - Too Many Options?"
date: 2006-07-03
forum: Installation &amp; Upgrades
---

### Post by JustDon on 2006-07-03
When I boot my computer the Grub Menu pops up and offers me the option of booting Ubuntu two separate times and (Recovery Mode) two times as well. I also have the option of Windows XP and Windows 2000 (which I dont have installed). In /boot/grub/menu.lst I see:

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-25-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot

title Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single
initrd /boot/initrd.img-2.6.15-25-386
boot

title Ubuntu, kernel 2.6.15-23-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.15-23-386
savedefault
boot

title Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-23-386 root=/dev/hda5 ro single
initrd /boot/initrd.img-2.6.15-23-386
boot

title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
chainloader +1


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title Windows NT/2000/XP
root (hd0,2)
savedefault
makeactive
chainloader +1

Can I alter this file and thus reduce my Grub Loader options to Ubuntu, Ubuntu (Recovery Mode) and Windows XP? Is this file safe to modify? It is also annotated as (Read Only) at the top, so I guess the main questions is IF I can modify this file?

---

### Post by Raezel on 2006-07-03
You can modify it as root (sudo), and it is safe IF you make a backup and remove ONLY the options you don't need.

In the case you described the modified file would be as follows:
```

## ## End Default Options ##

title Ubuntu, kernel 2.6.15-25-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.15-25-386
savedefault
boot

title Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-25-386 root=/dev/hda5 ro single
initrd /boot/initrd.img-2.6.15-25-386
boot


title Ubuntu, memtest86+
root (hd0,4)
kernel /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title Microsoft Windows XP Home Edition
root (hd0,1)
savedefault
makeactive
```


Althought it might be wise to only remove the Win 2000 part because that wau you can boot to a older kernel in case of problems with the new one.

---

### Post by JustDon on 2006-07-03
I tried to log in as root. I opened the terminal, typed in "su", entered my password that I assigned myself upon installation and it tells me that it is incorrect. I then type in "sudo su", enter the password and it allows me to log in as root. After I alter the grub menu.lst to remove Windows 2000 it prompts me to "save as". What do I save it as in order to have this new file be my Grub boot menu? I also see what you are saying about the two Ubuntu's, I had not noticed that it was two different kernels. Thanks.

---

### Post by az on 2006-07-03
[QUOTE=JustDon]

Can I alter this file and thus reduce my Grub Loader options to Ubuntu, Ubuntu (Recovery Mode) and Windows XP? Is this file safe to modify? It is also annotated as (Read Only) at the top, so I guess the main questions is IF I can modify this file?[/QUOTE]

It is best to let the package manager alter the grub menu.  Just remove the linux-image-2.6.15-23-386 pasckage and those entries will be removed for you by apt.


Use synaptic or any other package manager frontend.

---

### Post by JustDon on 2006-07-03
[QUOTE=azz]It is best to let the package manager alter the grub menu.  Just remove the linux-image-2.6.15-23-386 pasckage and those entries will be removed for you by apt.


Use synaptic or any other package manager frontend.[/QUOTE]

I apologize for sounding base but I must ask for more remedial instructions. I have only used Feather Linux up to this point on an _old_ laptop. Feather is _VERY_ basic so I am basically at a loss at this point. Can you please be more specific on how to alter this file?

---

### Post by az on 2006-07-03
[QUOTE=JustDon]I apologize for sounding base but I must ask for more remedial instructions. I have only used Feather Linux up to this point on an _old_ laptop. Feather is _VERY_ basic so I am basically at a loss at this point. Can you please be more specific on how to alter this file?[/QUOTE]
Open synaptic.  Search for "linux-image".  You will be shown all the linux-image packages that are installed or avilable for installation.  Remove the linux-image-2.6.15-23-386 package (select it and click remove).  Click on apply.  You are done.

---

### Post by Raezel on 2006-07-04
[QUOTE=JustDon]After I alter the grub menu.lst to remove Windows 2000 it prompts me to "save as". What do I save it as in order to have this new file be my Grub boot menu? .[/QUOTE]

You just replace the old menu.lst (AFTER making a backup of the old one).

---

