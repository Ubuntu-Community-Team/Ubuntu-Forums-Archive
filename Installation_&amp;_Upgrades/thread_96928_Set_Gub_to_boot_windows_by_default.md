---
title: "Set Gub to boot windows by default?"
date: 2005-11-29
forum: Installation &amp; Upgrades
---

### Post by bruce147 on 2005-11-29
Can I edit my Grub menu.lst to make windows xp my default choice? If I read things correctly, I could change "default 0" to "default 6" or what default number is my windows entry? I got 6 by counting from the "title" lines starting from 0.
Or could I just copy and paste the windows data to the 0 position? And then delete the non linux section?

I guess I would have to redo this whenever an upgrade happens? That is would an upgrade make the new linux kernel the default 0 option?

My menu.lst follows:
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0
.........
## ## End Default Options ##

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro quiet splash
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda3 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,2)
kernel		/boot/memtest86+.bin  
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Home Edition
root		(hd0,0)
savedefault
makeactive
chainloader	+1

---

### Post by Jimmy The Clown on 2005-11-29
You are correct. Just set it to 6 and all should be golden. I personally have mine set to "saved" as suggested by the comments in the file. This means that if I just booted windows and hit restart, windows will be selected by default and similar for linux. I like this because I tend to stay in one OS for awhile.

When you go through the whole upgrade procedure it will probably ask you if you want to replace you menu.lst so you might not have to do this again. I suppose if more kernels get added, the number for windows will change. I think easiest might be to copy paste windows entry to the top like you suggested.

Remember you are going to have to sudo in order to save this file after the changes. Simply do a "sudo gedit /boot/menu.lst".

-JTC

---

