---
title: "ubuntu seems to boot slowly. help?"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by darksidedude on 2008-07-17
hello again ubuntu forums. I have a bit of a problem. Ubuntu seems to boot slowly for some reason or another. I have Vista on one harddrive. it boots in about 30sec. Ubuntu 8.04.1 takes almost 1min 30sec. I was wondering whats going on. here are my PC specs.

AMD althon x64 6400 + 3.2ghz dual core
nvidia 8800gt (EnvtNG driver installed)
2gb ddr2 ram
1tb Sata2 harddrive. 

By my guess shouldn't ubuntu boot in like 2secs:lolflag:

---

### Post by achim_59 on 2008-07-17
I'm not familiar with 64 bit setups, but never-the-less any version of Linux should boot faster than that on a 3.2 GHz machine!!

Have you set the boot sequence up to display the precise setup steps (like on older Linux versions)? I'm thinking that somewhere along the line it hangs for a while, trying to communicate with some device that isn't responding. I use Feisty 7.04 (when I can=I'm currently forced to use Windoze) and there's an option to display the boot messages. 

Try that and see if there isn't some point at which the boot sequence hangs.

Achim

---

### Post by Pumalite on 2008-07-17
Try removing 'splash' in /boot/grub/menu.lst

---

### Post by darksidedude on 2008-07-17
can you show me how to edit the grub.lst I'm afraid I might bork my install. 

Im running X86 ubuntu and X64 vista. when i tried X64 ubuntu X wouldn't even start in VESA on my 8800gt. I would have a black screen
so if it makes a difference. Im using X86 ubuntu

---

### Post by Pumalite on 2008-07-17
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.old
Edit:
gksudo gedit /boot/grub/menu.lst

---

### Post by darksidedude on 2008-07-18
I didn't end up editing anything. is there anyway to boot in verbose mode. in case it ever hangs again?

---

### Post by achim_59 on 2008-08-20
If it hangs *againn*? I'm guessing that it works OK now.

In any event, the preceding commands from Pumalite will copy your old /boot/grub/menu.lst to /boot/grub/menu.lst.old first. This means you can easily recover. 

Whatever the problem: Be brave, give it a go, and remember the famous words of Douglas Adams: DON'T PANIC!

Achim

---

