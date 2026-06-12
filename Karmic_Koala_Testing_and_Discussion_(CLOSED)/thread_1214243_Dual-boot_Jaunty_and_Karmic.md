---
title: "Dual-boot Jaunty and Karmic"
date: 2009-07-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by foxy123 on 2009-07-15
I have installed Karmic to a spare partition alongside with my main Jaunty. What should I put in Jaunty's menu.lst to boot Karmic. Usually I have a path to a menu.lst of the parallel OS like:
```
title		Karmic Koala (development version)
root		(hd0,8)
configfle	/boot/grub/menu.lst

``` 

But it seems not to work for Karmic :(

---

### Post by flavouride on 2009-07-15
Should not there be something else like

root=UUID=0axxxxd2-xxx-4a81-9796-xxxxxxxxxxx ro  quiet splash
initrd    /boot/initrd.img-2.6.3x.x-generic

as well?

---

### Post by flavouride on 2009-07-15
or alternatively just upgrade to grub2 in Jaunty and then "sudo update-grub" to autoconfig
(you may need to umount your Karmic partition first)

---

### Post by ranch hand on 2009-07-15
Go to 9.10s /boot/grub/grub.cfg file and copy the stuff out of it as in;
```

menuentry "Ubuntu, Linux 2.6.31-3-generic" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 3e5c2219-c1d2-4bb8-ac5c-47a95201876b
	linux	/boot/vmlinuz-2.6.31-3-generic root=UUID=3e5c2219-c1d2-4bb8-ac5c-47a95201876b ro  quiet splash 
	initrd	/boot/initrd.img-2.6.31-3-generic
}
menuentry "Ubuntu, Linux 2.6.31-3-generic (recovery mode)" {
	set root=(hd0,8)
	search --no-floppy --fs-uuid --set 3e5c2219-c1d2-4bb8-ac5c-47a95201876b
	linux	/boot/vmlinuz-2.6.31-3-generic root=UUID=3e5c2219-c1d2-4bb8-ac5c-47a95201876b ro single 
	initrd	/boot/initrd.img-2.6.31-3-generic
}

```
Paste that to your grub file.  I believe that will do the trick.

I do not understand why you are not booting from 9.10.  Grub2 should have taken over when you installed it.  It is working quite well now and with no more than 2 OS' I don't think that you would have any problem.

---

