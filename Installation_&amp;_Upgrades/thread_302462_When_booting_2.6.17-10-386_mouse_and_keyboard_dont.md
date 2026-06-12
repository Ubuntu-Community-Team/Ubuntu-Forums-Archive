---
title: "When booting 2.6.17-10-386 mouse and keyboard dont work"
date: 2006-11-18
forum: Installation &amp; Upgrades
---

### Post by gni on 2006-11-18
I have updated to latest version and in boot menu i got 2 new versions:
Ubuntu, kernel 2.6.17-10-386 When i try this keyboard and mouse does not work.
Ubuntu, kernel 2.6.15-27-386 This one works.

How do i troubleshoot booting kernel 2.6.17-10-386?
(i got an HP computer whit wireless mouse and keyboard connected via receiver to usb port)
/Gosta

---

### Post by gni on 2006-11-24
Any suggestions how to fix this?

---

### Post by gni on 2006-12-05
Hello out there, does anyone have some advise how to fix my problem?

---

### Post by Randori on 2006-12-14
I'm having the same problem as you. Lets see if we can work anything out.

First off what computer are you using, which version did you download.
And What mouse and keyboard are you using? Any other things that should be known about it , also?

---

### Post by Roobert on 2006-12-14
I upgraded today to 2.6.17-10 and was left with no display and a completely unresponsive computer. See [here]("http://www.ubuntuforums.org/showthread.php?t=318970").

I had to revert to 2.6.15, or whatever the current kernel version was in the grub menu before today's update.

---

### Post by Roobert on 2006-12-15
I fixed the problem I was having - I edited out the 'savedefault' line in my /boot/grub/menu.lst file and now 2.6.17-10 boots normally.

---

### Post by gni on 2006-12-20
I have tested to remove 'savedefault' in menu.lst file, but it still hangs when i try to boot whit 2.6.17-10-386.

Part of menu.lst
> title		Ubuntu, kernel 2.6.17-10-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=8de8e613-403a-477e-8e35-ea89f14434a8 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.17-10-386 root=UUID=8de8e613-403a-477e-8e35-ea89f14434a8 ro single
initrd		/boot/initrd.img-2.6.17-10-386
boot

title		Ubuntu, kernel 2.6.15-27-386
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=8de8e613-403a-477e-8e35-ea89f14434a8 ro quiet splash
initrd		/boot/initrd.img-2.6.15-27-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-27-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.15-27-386 root=UUID=8de8e613-403a-477e-8e35-ea89f14434a8 ro single
initrd		/boot/initrd.img-2.6.15-27-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin
boot

What to do now?

---

### Post by masahl on 2007-01-10
Hello,

I have the same problem. I do not have any answer to you, but maby we can narrow the problem down... Could it be that you have an HP Pavilion with an AMD Athlon64 X2?

I know there is some problems with the Fedora dist on this computer as well. Anyway, have you tried to run Edgy in 64-bit version? I wouldn't be supprised if that works...

/Martin

---

