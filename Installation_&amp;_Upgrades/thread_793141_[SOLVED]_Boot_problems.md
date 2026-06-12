---
title: "[SOLVED] Boot problems"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by MunkyJunky on 2008-05-13
I run Ubuntu 8.04, using an MSI P965 Neo motherboard. This seems to be notorious for its problems with Linux. 

When booting (during the splash) the bar loads about 1/8th, then pauses for about 30 seconds before fulling loading. So, dear community, I need your help on 2 things. 

[LIST=1]
[*]How do I find which particular part of the boot is causing the problems? I know its something with harddrives (something about IRQ something or other,  or something similar, but I need to pinpoint it so I can fix it. Isn't there a boot log? 

[*]Upon finding out what this problem is, I'll undoubtedly need help fixing it
[/LIST]

Thanks to anyone who can help! I apologise for my vagueness in the matter.

---

### Post by lemming465 on 2008-05-20
Looking in /var/log/dmesg and /var/log/kern.log will show you most of what happened.  However, if things work, except slowly, there is probably some weird interaction of hardware probes for stuff you don't have with devices you do have causing the delay.  The odds are that this won't have anything logged about it, so tracking it down will take some detective work.  The quick thing to do is take "quiet splash" out of the boot entry you are using (in /boot/grub/menu.lst if you are using Grub).  Then see what the line of text just before the pause is.

---

### Post by iaculallad on 2008-05-20
In other words, place a comment on "quiet", append a # sign to it so that all messages will be shown upon bootup.

i.e:

title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=6d422661-145e-4c07-9cbb-8428c17a2b1f ro quiet splash vga=792
initrd		/boot/initrd.img-2.6.22-14-generic
#quiet <- Like this, append the # sign

For the second part:

Try posting any error that you can see.

---

