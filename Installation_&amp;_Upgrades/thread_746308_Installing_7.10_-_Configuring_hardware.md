---
title: "Installing 7.10 - Configuring hardware"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by ke.edwards on 2008-04-05
I've been installing 7.10 and the install process was going fine until it got to 94% - configuring hardware, where it has stopped.  
Can anyone help (I'm not a particularly experienced Ubuntu user)

Thanks

---

### Post by dstew on 2008-04-05
Are using a Live CD? Did you check the CD integrity (menu item at the beginning)? If the CD checks out OK, and if it's a Live CD, press F6 at the opening menu to edit the kernel line. Remove **quiet** and **splash** from the line, and boot again. You might be able to see an error message that will give us a clue as to what is happening.

Usually, a problem like this can be fixed by appending some parameters to the kernel line, to turn off some kernel "features" that do not work properly with your hardware (note: the real problem is that some hardware is not implemented in a standard fashion that the kernel expects). Commonly used kernel parameters are **acpi=off** to turn off the Advanced Configuration and Power Interface, and **noapic** and **nolapic** to turn off the Advanced Programmable Interrupt Controller.

If none of this works, try using the Alternate Install CD. It installs the same Ubuntu system using a text-based installer that is gentler on your system. Get it from the Ubuntu Download page, check the box below the Start Download button.

---

### Post by ke.edwards on 2008-04-09
Thanks for that.  I am using a Live CD and did check the integrity 1st which was fine.  
On the 1st reboot after editing the kenel it hung at 94% again - without any error messages.  
I tried modifying the kenel parameters with acpi=off, noapic and nolapic which completed installation, but there was then the following errors on start up: 
21.637176 crc error
21.638188 Kernel panic not syncing: VFS: Unable to mount root fs as unknown-block (0,0)

Can you suggest anything else worth trying? Otherwise I might try the alternate Install CD.

---

### Post by dstew on 2008-04-09
Try the same kernel parameters on your installed system. Enter them from the grub menu. Instead of 'enter', press 'e' to edit a menu item. Highlight the kernel line in the menu item, press 'e' again, and add the kernel parameters to the end of the line. Then press 'enter' to save the edit, then 'b' to boot. If this works, let me know, and I can tell you how to make the changes permanent by editing the grub /boot/grub/menu.lst file.

---

### Post by ke.edwards on 2008-04-10
Thanks, but unfortunately that didn't work - I had the same erros come up again.

---

### Post by dstew on 2008-04-10
Boot a Live CD, navigate to your hard disk, and open the file /boot/grub/menu.lst using a text editor. Post the contents on the forum.

---

### Post by ke.edwards on 2008-04-12
This is the contents of /boot/grub/menu.lst:

> title		Ubuntu 7.10, kernel 2.6.22-14-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c878ab10-9f8f-44dd-8ff8-ad4053c09b38 ro quiet splash
initrd		/boot/initrd.img-2.6.22-14-generic
quiet

title		Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=c878ab10-9f8f-44dd-8ff8-ad4053c09b38 ro single
initrd		/boot/initrd.img-2.6.22-14-generic

title		Ubuntu 7.10, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows NT/2000/XP (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1


---

### Post by dstew on 2008-04-12
Try adding **acpi=off** to the end of the kernel line in /boot/grub/menu.lst, save the file and boot again.

---

### Post by ke.edwards on 2008-04-12
Sorry - still not getting anywhere.  
When trying to save /boot/grub/menu.lst I'm told that I don't have sufficient permissions to save it.

---

### Post by dstew on 2008-04-12
You need to start gedit with```
gksudo gedit
```Then you will have privileges.

---

### Post by ke.edwards on 2008-04-14
I managed to change that, but on rebooting it's still giving me the same errors.

My computer's now randomly rebooting itself, both using the Live CD and Windows - but I suspect that's just coincidence.

---

### Post by prshah on 2008-04-14
> **ke.edwards said:**
> This is the contents of /boot/grub/menu.lst:

I'd suggest you run the "memtest" option from your grub menu. 10~15 mins is fine. If anything shows up in RED, you have memory problems.

---

### Post by ke.edwards on 2008-04-16
The memtest hasn't shown any issues.

---

### Post by prshah on 2008-04-16
> **ke.edwards said:**
> 
My computer's now randomly rebooting itself, both using the Live CD and Windows - but I suspect that's just coincidence.

> **ke.edwards said:**
> The memtest hasn't shown any issues.

Considering these, I'd say the issue is nothing to do with the OS and more to do with the hardware. Is it an old machine? Are the internal fans in working order? Do you feel the case becoming hot within 15~20 mins (Not warm; hot).

I used to face random (instant) reboots and such in both Windows and Linux because there was too much dust in the box. I took the cover off, used a vacuum cleaner on BLOW (Do _NOT_ use suck!!!) and give it a nice strong breeze for about 5 mins, concentrating on the fans. EDIT: OK just for this suggestion: [http://www.youtube.com/watch?v=euvuDQLaIsY](http://www.youtube.com/watch?v=euvuDQLaIsY)[/EDIT]

I don't know if this is your problem, but if all else fails.. worth a shot?

---

