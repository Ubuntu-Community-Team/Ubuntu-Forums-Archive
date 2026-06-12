---
title: "Newest kernel update"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by hvacr on 2008-05-26
I did the newest software update tonight, but the newest kernel is not showing in the menu.1st. I can see that it is installed in synaptic. How  do I go about fixing this.

I went and added the new kernel into my menu.1st, leaving the old one just in case. All seems ok at this time, I will leave it for a few days, then remove the old kernel from menu.1st

---

### Post by dstew on 2008-05-27
Usually, the kernel will appear in menu.lst after installation because the program **update-grub** is run whenever you install or uninstall a kernel. However, if you have edited your menu.lst in the past, update-grub may not work properly, and you will have to add the menu item by hand as you did. If your new menu item works, that's fine, don't worry about it.

When you want to get rid of the old kernel, deleting the entry in menu.lst will only change the menu. If you want to get rid of the kernel image, use Synaptic to uninstall the kernel package. Again, since it is a kernel package, update-grub is run, and should remove the menu.lst item... unless menu.lst has been edited in such as way as to make update-grub useless.

---

### Post by hvacr on 2008-05-27
It was the original menu.1st, I had never edited it before, so this was an odd situation.

---

### Post by puzzledinmn on 2008-05-27
I now have 3 different kernels displayed by my 8.04 upgrade grub menu.lst every time I dual boot.  I have had to edit menu.lst twice now already because my default boot is to Windows.  Before I always had 1 kernel listed.  Users can search in Synaptic for linux-image and manually uninstall but that just doesn't seem the way to update properly.  Why aren't the old kernels being removed from grub? (or at least not listed)

---

### Post by dstew on 2008-05-28
The old kernels aren't removed because sometimes the new one doesn't work, and you need a backup. If you uninstall an old kernel using Synaptic, the grub menu will be edited for you, and the old kernel menu items deleted. That is the proper way to manage kernels.

---

