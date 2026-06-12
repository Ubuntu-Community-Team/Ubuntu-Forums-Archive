---
title: "Grub OS detection fail"
date: 2010-04-26
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by x-shaney-x on 2010-04-26
I just installed PCLOS 2010 to test and opted to install it's grub to partition (just in case chainloading ever works properly in grub2).

After a reboot I assumed lucid's grub would automatically pick up PCLOS but unfortunately not so, after booting into lucid I ran update-grub and sure enough it detected it and I rebooted, selected PCLOS from the menu and got a kernel panic.

After rebooting again and checking the menu entry, this is what lucid had put into grub.cfg:
```
menuentry "linux (on /dev/sda7)" {
    insmod ext2
    set root='(hd0,7)'
    search --no-floppy --fs-uuid --set ffbd631c-65ca-4169-86b5-ea437cb2e44f
    linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=ffbd631c-65ca-4169-86b5-ea437cb2e44f vga=788
    initrd (hd0,6)/boot/initrd.img
}
```

Note the "set root" and "initrd" lines point to different partitions, hd0,7 and hd0,6 respectively.

After changing both entries to hd0,7 it booted fine.
Why would grub get it wrong like that?

Incidentally, this is the lucid RC freshly installed this afternoon.

---

### Post by VMC on 2010-04-26
Interesting. I manage my grub.cfg another way, but after issuing the command '*sudo grub-mkconfig*' I got the following output from my PCLinuxOS:

```
Found PCLinuxOS on /dev/sda10
menuentry "linux (on /dev/sda10)" {
	insmod ext2
	set root='(**hd0,10**)'
	search --no-floppy --fs-uuid --set 309fc493-4675-41d3-a776-f1544d754eb0
	linux /boot/vmlinuz BOOT_IMAGE=linux root=UUID=309fc493-4675-41d3-a776-f1544d754eb0 splash=silent [COLOR="Red"]**vga=788**[/COLOR]
	initrd (**hd1,9**)/boot/initrd.img
}
```

Same kind of result as yours. And I don't even have a second hard drive attached?!

---

### Post by kansasnoob on 2010-04-26
Ouch! That's a definite bug!

Seems like things blew up the last few days.

What happened to that "anal retentive" super-duper check everything closely update policy?

---

### Post by VMC on 2010-04-26
I think I found the problem, but not the solution yet:

@shaney, notice you /boot folder and see the initrd.img is linked to initrd-2.6.32.11-pclos2.bfs.img in the same folder. Same also is vmlinuz.


Edit:
Both initrd.img and vmlinuz are both linked inside the same folder. If I move both links to the root "/" foler, as Ubuntu does it, then *grub-mkconfig* finds both correctly:

```
Found PCLinuxOS on /dev/sda10
menuentry "PCLinuxOS (on /dev/sda10)" {
	insmod ext2
	set root='(hd0,10)'
	search --no-floppy --fs-uuid --set 309fc493-4675-41d3-a776-f1544d754eb0
	linux /boot/vmlinuz-2.6.32.11-pclos2.bfs root=/dev/sda10
}

```

I'm not sure what to make of all this. If you notice my previous post, *grub-mkconfig*, also added vga=778, which is a bit strange since that has been depreciated in grub2.

---

### Post by VMC on 2010-04-26
Ok I ran into the same situation with PCLinuxOS as I did with Fedora. After linking vmlinuz and initrd.img from root, It picks up vmlinuz correctly. but *grub-mkconfig* misses initrd completely. 

The only other thing you can do is add PCLinuxOS to you 40_custom file the way it should be.

Edit: Way back when I filed a bug report when I had Fedora installed and it was unclear how to fix it at the time. Grub2 was in a beta stage. I will have to find my old bug report and add it back here....

---

