---
title: "grub problems...."
date: 2010-04-20
forum: Installation &amp; Upgrades
---

### Post by dedemith on 2010-04-20
last month i update my ubuntu.. and i installed all the components that i've been updated (cos i still newbi)..
After i had instsalled all the components, i restarted my laptop... and i suddenly confused when i looked at my boot order (i use dual os)..
there're more than 2 boot order thar i didnt want.. (just like in the below)

[COLOR=DarkOrchid]"Generating grub.cfg ...[/COLOR]
[COLOR=DarkOrchid]Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done"

[COLOR=Black]my questions's "Can i delete boot order that i didnt want to use?" or can i just have 2 kinds of boot order (because i just use dual os, 1 for ubuntu and 1 for windows)?"[/COLOR]
[/COLOR]

---

### Post by wilee-nilee on 2010-04-20
> **dedemith said:**
> last month i update my ubuntu.. and i installed all the components that i've been updated (cos i still newbi)..
After i had instsalled all the components, i restarted my laptop... and i suddenly confused when i looked at my boot order (i use dual os)..
there're more than 2 boot order thar i didnt want.. (just like in the below)

[COLOR=DarkOrchid]"Generating grub.cfg ...[/COLOR]
[COLOR=DarkOrchid]Found linux image: /boot/vmlinuz-2.6.31-21-generic
Found initrd image: /boot/initrd.img-2.6.31-21-generic
Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done"

[COLOR=Black]my questions's "Can i delete boot order that i didnt want to use?" or can i just have 2 kinds of boot order (because i just use dual os, 1 for ubuntu and 1 for windows)?"[/COLOR]
[/COLOR]

The first 4 lines are kernels, you actually want at least two especially since your new at this. The reason for having two is if 1st one lines 1 & 2 had some problems the 2nd 3rd & 4th line would work generally.

---

