---
title: "Hardy shutdown button gone loopy"
date: 2009-11-16
forum: Installation &amp; Upgrades
---

### Post by tiggsy on 2009-11-16
I have a backup computer which runs windoze in a partition, and ubuntu in another partition. I dont use it very often, but the last few days I've noticed that when you hit the shutdown button to select a restart or whatever, the entire panel disappears, so you are left with a desktop, but no way to do anything except explore the folder on the desktop. You have to hit the button on the box to get it to close down.

I am not getting any messages when I do the updates.

The box is running Ubuntu 8.04 Hardy Heron (and win xp in the other partition).

---

### Post by spcwingo on 2009-11-16
I have no idea how to fix it, but when it does it again you can press ALT+F2 (which should open a run prompt) and enter this command:

```
xterm
```

That will open xterm (a terminal).  Within that terminal input this command:

```
gnome-session-save --kill
```

and if that doesn't work, then try this one:

```
poweroff
```

At least that way it will shutdown properly.  Hopefully someone else will be along shortly to help take care of the root of the problem.

---

### Post by tiggsy on 2009-11-21
Thanks for this. I tried what you said. It still stopped before it shut down (further down, though), and i still had to hit the button on the box to shut down. BUT the next time I went to close down, I got the shutdown menu, and all now seems to work.

So it's solved... my question is, how?

---

### Post by spcwingo on 2009-11-21
I'm not quite sure, but it does seem to be something to do with ACPI...what exactly, I have no clue.  I'm just glad to know it's now working for you.  If for some reason it keeps doing this let me know as we may have to edit your GRUB menu.lst.

---

### Post by tiggsy on 2009-12-29
This happened again after an update. I did shutdown now in a terminal on the next day when I wanted to close down and it's all back to normal??

---

### Post by spcwingo on 2009-12-29
I guess we can go ahead and try what I referred to in my last post.  Press ALT + F2 and in the run dialog box enter:

```
gksu gedit /boot/grub/menu.lst
```

Near the bottom you will see something like this:

```
## ## End Default Options ##

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=45c7b67e-537a-47ac-ac11-7e074f44f62b ro quiet splash
initrd		/boot/initrd.img-2.6.24-26-generic
quiet

title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=45c7b67e-537a-47ac-ac11-7e074f44f62b ro single
initrd		/boot/initrd.img-2.6.24-26-generic

title		Ubuntu 8.04.3 LTS, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Edit that first kernel line so that acpi=force is at the tail end of that line like this:

```
title		Ubuntu 8.04.3 LTS, kernel 2.6.24-26-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-26-generic root=UUID=45c7b67e-537a-47ac-ac11-7e074f44f62b ro quiet splash [COLOR="Red"]acpi=force[/COLOR]
initrd		/boot/initrd.img-2.6.24-26-generic
quiet
```

Finally reboot to let the changes take effect.  I sincerely hope that this solves the problem.  Please let me know either way.

---

### Post by tiggsy on 2010-03-03
I kept getting this problem on and off, and I now suspect that it relates to a really severe shortage of disk space - because when I uninstalled Open Office, releasing 336m of space, suddenly the button started working again. So if you are having this problem, check this first (can see by going into System->Admin->System Monitor and selecting the File Systems tab).

---

