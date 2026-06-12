---
title: "Multi Bootable Flash Drive"
date: 2008-10-04
forum: Installation &amp; Upgrades
---

### Post by basnet2 on 2008-10-04
Hello everyone,

I have been yanking my hair out over the past week trying to figure out how to create a multi boot flash drive.

What I want to achieve: take my 8GB Sandisk Cruzer Titanium hold my data, and on other paritions hold UBCD, Backtrack 3, and Knoppix.

I am new to Ubuntu/linux and don't really know anything about terminal commands, but I have been reading a lot and have tried various things such as GAG, GRUB, and Lilo but with no success :(

What I have right now is my flash drive partioned into 2 primary partitions (the first for all my data, the second which is only 8MB where I plan to hold the bootloader), and then a Extended partition broken into 3 logical paritions, one for each UBCD, Knoppix, and BT3.

Where I am getting hung up is installing and configuring a bootloader.  Although like I said I am a complete noob to linux and have very little knowlege of what I am doing haha.  All I have tried I have read online the past week.  So any help would be greatly appreciated.  Thanks!

---

### Post by basnet2 on 2008-10-05
So I have made some real headway and now have Backtrack 3 and Knoppix booting from my flash drive.  Now all I need is to get UBCD running.  I googled around on configuring the menu.lst for BT3 and Knoppix but I can't find anything for UBCD as far as Grub goes.  Here is my menu.lst so far:
```

title		Ultimate Boot CD
root		(hd0,4)
kernel		/boot/baslinux root=/dev/ram0 
initrd		/boot/baslinux.gz
boot

title		Knoppix
root		(hd0,5)
kernel 		/boot/isolinux/linux ramdisk_size=100000 init=/etc/init lang=pt apm=power-off 			vga=791 initrd=minirt.gz nomce quiet pci=nommconf BOOT_IMAGE=knoppix
initrd 		/boot/isolinux/minirt.gz
boot


title		Backtrack 3
root		(hd0,6)
kernel		/boot/vmlinuz vga=791 root=/dev/ram0 rw initrd=/boot/initrd.gz init=linuxrc
initrd 		/boot/initrd.gz		
 


```

I completely made up the whole UBCD part hoping that it would magically work lol.  Any guidance on this is appreciated!

Thanks

---

### Post by cariboo on 2008-10-05
I don't know if this will help, but I have used this to create several multiboot cd's

[http://www.nu2.nu/bootcd/](http://www.nu2.nu/bootcd/)

It should with flash drives.

Jim

---

### Post by basnet2 on 2008-10-05
I really just want to figure out how to code for the booting of UBCD through Grub, not to start all over with a different bootloader.  Its taken me many hours to come this far and I don't want to through all my progress away when I'm so close :D

---

