---
title: "Upgrade to kernel 32-28 breaks grub.cfg"
date: 2011-01-26
forum: Installation &amp; Upgrades
---

### Post by sapeurcamembert on 2011-01-26
Upgraded with update-manager and install kernel 32-28 + other various upgrade.
Try to reboot and workstation keep booting not showing list of available kernels.
I keep a daily copy of /boot directory and thanks to RescueCD I did a restore of my previous /boot directory, reboot and it works.
I kept a copy of the failing /boot directory for checking and using diff discovered quickly grub.cfg was misplaced as /boot/grub.cfg in place of /boot/grub/grub.cfg...

I suspect It could be a wrong packaging of the kernel upgrade or a wrong (read bug) of update-grub during post install

Any idea somebody ?

Ubuntu 10 something... 

I did not try yet to move grub.cfg to right place and rename my /boot directory to give it a try...

---

### Post by ajgreeny on 2011-01-26
So are you saying you have two versions of grub.cfg; the old one, which you have now restored in /boot/grub/grub.cfg, and the new one wrongly put in /boot/grub.cfg?  Are you also saying that the old grub.cfg was removed?

You could very quickly compare the files using ```
diff -y /boot/grub/grub.cfg /boot/grub.cfg
```which will open them side by side in a terminal and allow you to easily see differences line by line.  Ho9wever, I assume the boot is killed by the wrong siting of the grub.cfg file and perhaps is nothing to do with its detailed contents.

That situation, however, could easily have been a major problem for anyone who was not aware of how the system boot files work.  How did you find out what had happened?

I realise that kernel is in the proposed or backports, and not something everyone would install by default, but nevertheless it could be a disaster for some.

---

### Post by sapeurcamembert on 2011-01-26
Rightly so. The previous grub.cfg was not there anymore and the only one left at the wrong place was the one just installed by the kernel upgrade. It is pretty tricky to find what is wrong because in this situation grub2 probably fails without any message or grub2 try to reboot....and the system was just rebooting endlessly...I knew quickly that was linked to the last kernel upgrade and I simply restored everything under /boot directory.

I you do not well grub2 AND the boot process you are in murky waters...

---

### Post by tmr0 on 2011-01-27
I have the same symptoms after a kernel update to 32-28. I don't know enough to discover why the kernel is not working.  Fortunately I had previously enabled the Grub menu so I could boot using 32-27.  How do I fix this issue or uninstall 32-28?

---

### Post by sapeurcamembert on 2011-01-27
To fix ir (for me at least).

Copy grub.cfg from the place where it stands now (/boot/grub.cfg) to the place where it should be (/boot/grub/grub.cfg) and you should be able to reboot.

Other solution ( I did not try) is to do 

sudo update-grub

update-grub  is a stub for running grub-mkconfig -o /boot/grub/grub.cfg to generate a grub2 config file.

you should find the new grub.cfg at the right place after and reboot.

You do not need after to delete the kernel but if you absolutely want to do it you can refer to the following web link

[http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html](http://digitalpbk.blogspot.com/2008/11/ubuntu-remove-old-kernel-grub-list-long.html)

be very careful to the syntax....!!!  if you use this AND do not forget that the command explained by the web link is ALSO calling update-grub and recreating grub.cfg....

Hope this help

---

### Post by tmr0 on 2011-02-03
For me the issue ultimately turned out to be a motherboard/memory issue.

---

### Post by sapeurcamembert on 2011-02-03
Well I did some progress and guess...

I am running a BIOS with USB enabled (keyboard and mouse) NO problem 
but the following order in the grub.cfg makes grub2 crashing

if terminal_input usb_keyboard ; then true ; else
  # For backward compatibility with versions of terminal.mod that don't
  # understand terminal_input
    terminal usb_keyboard
fi
I proceed to change directly the grub.cfg by making terminal usb_keyboard in comments and it works.

I did upgrade to grub2 2.0 (Ubuntu Update Manager) and the upgrade process did change grub.cfg and..the system crashes again at restart..but now at least I know what to do....and I always keep a daily backup of /boot...

I do not know if it is a bug with grub2. I suspect that modules necessary for USB keyboard handling by grub2 are not loaded. See the following link

Thanks for you remark and help

Alain,Montreal

[http://grub.enbug.org/USBSupport](http://grub.enbug.org/USBSupport)

---

