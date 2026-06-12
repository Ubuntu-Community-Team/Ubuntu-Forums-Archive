---
title: "how to acces the command line before boot?"
date: 2008-08-31
forum: Installation &amp; Upgrades
---

### Post by hkb on 2008-08-31
I have the same problem as in tis topic: [http://ubuntuforums.org/showthread.php?p=5698892](http://ubuntuforums.org/showthread.php?p=5698892)

It seems that the topic solves the problem but the is something in the solution i don't understand. As you can see below the solution is pretty simple but i can't figure out how to access the command line before the system boots. How do i do that?

> those boot options you used that allowed for a successful installation need to be added to the /boot/grub/menu.lst file.
The first reboot after installation, you will need to use the f6 option again. Then after the system boots run:

```
gksu gedit /boot/grub/menu.lst
```

```
## ## End Default Options ##

title		Ubuntu intrepid (development branch), kernel 2.6.26-5-server
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.26-5-server root=UUID=#'s ro quiet splash 
initrd		/boot/initrd.img-2.6.26-5-server
quiet
savedefault
```

Scroll down to this section, and where quiet splash is highlighted, above, delete quiet splash and add your kernel options. There are other suggestions as well, such as adding you options under kopt further up in the file, but I find this method is more reliable. You might also want to set the value savedefault=true, just above this section.

---

### Post by Too Late on 2008-08-31
You can edit the file with a LiveCD, for example.

But you don't have to do that. Just select the corresponding entry from the grub menu, and press 'e' key. Now you can edit that menu entry before booting, but that won't be saved anywhere, so you have to manually edit that menu.lst file after you've successfully booted into your system.

edit: Of course, you can also press 'c' if you want to go to the grub command line. There you can type the same lines that are in the menu.lst file. After typing those root, kernel and initrd commands, just type boot.

---

