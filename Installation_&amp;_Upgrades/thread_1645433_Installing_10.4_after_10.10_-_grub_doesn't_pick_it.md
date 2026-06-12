---
title: "Installing 10.4 after 10.10 - grub doesn't pick it up"
date: 2010-12-14
forum: Installation &amp; Upgrades
---

### Post by liverpoolfc on 2010-12-14
I have 10.10 installed on my machine.  I'm trying to install 10.4 on another partition.  Install completes, but when I reboot, there's no entry in the grub menu for the 10.4 install.  I tried adding an entry to 40_custom in /etc/grub.d, but it still doesn't show up.  I'm pasting my 40_custom below.  Did I do something wrong?  Is there another way to do this?  Thanks in advance.


#!/bin/sh
exec tail -n +3 $0
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
menuentry 'Ubuntu 10.4' --class ubuntu --class gnu-linux --class gnu --class os {
	recordfail
	insmod part_msdos
	insmod ext2
	set root='(hd0,msdos10)'
	search --no-floppy --fs-uuid --set be888928-a477-4b31-b478-13271009c032
	linux	/boot/vmlinuz-2.6.32-24-generic root=UUID=be888928-a477-4b31-b478-13271009c032 ro   quiet splash
	initrd	/boot/initrd.img-2.6.32-24-generic
}

---

### Post by tommcd on 2010-12-14
> **liverpoolfc said:**
> I have 10.10 installed on my machine.  I'm trying to install 10.4 on another partition.  Install completes, but when I reboot, there's no entry in the grub menu for the 10.4 install.  I tried adding an entry to 40_custom in /etc/grub.d, but it still doesn't show up.  I'm pasting my 40_custom below.  Did I do something wrong?  Is there another way to do this?  
There is a much easier way of doing this.
Just create custom boot files in the /etc/grub.d/ directory. See this tutorial:
[https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries](https://help.ubuntu.com/community/Grub2#Custom%20Menu%20Entries)
For reference, here is my custom boot entry in /etc/grub.d/ for booting Slackware's generic-smp kernel:
```

menuentry "Slackware32-13.1 on /dev/sda5" {
        set root=(hd0,5)
        linux  /boot/vmlinuz-generic-smp-2.6.33.4-smp root=/dev/sda5 ro 
        initrd  /boot/initrd.gz
}

```
That is all you need. Note that you do not need to mess with those stupid UUIDs. Just use the much easier and less problematic /dev/sdXY format for the root= entry. 
I named this file *32_Slackware* so it would show up after *31_WindowsXP*.
Be sure to make your custom boot file executable with:
```
sudo chmod +x 31_Ubuntu10.04
```
Or whatever you decide to name your custom boot file. Then be sure to run: ```
sudo update-grub
``` to update your /boot/grub/grub.cfg file.

Where did you install Ubuntu 10.04's grub to? Did you install it to the MBR? Or somewhere else? 
If both versions of Ubuntu have their grub installed to the MBR, then whenever there is a kernel update for Ubuntu each version will try to update the grub.cfg file to control the MBR.

---

### Post by wilee-nilee on 2010-12-14
First try in the bootable Ubuntu in the terminal.
```
sudo update-grub
```

If that doesn't show all the OS's then do this.

So from a booted live Ubuntu cd or thumbdrive lets see the bootscript read out; in my signature just click on it and follow the instructions. Come back to the thread and click on the # in the reply panel this makes code tags  paste all the text in between. Can be run in a live Ubuntu install as well.

---

