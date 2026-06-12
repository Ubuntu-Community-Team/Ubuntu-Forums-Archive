---
title: "Ubuntu not booting"
date: 2007-02-05
forum: Installation &amp; Upgrades
---

### Post by Prinz on 2007-02-05
I installed ubuntu last night and everything was working just fine until this morning, when I go to boot ubuntu up I get this error:

/bin/sh: can't access tty; job control turned off

and then it has a command prompt (I guess in linux it would be called a terminal?)

So what does this mean and how can I fix it?

---

### Post by Rabbit_Alex on 2007-02-05
I think I'm having a similar problem.  When Ubuntu starts to boot it gets as far as the progress bar, then a cursor appears in the corner of the screen and it won't boot past that point.

Here's the thread I started for it last night:
[http://ubuntuforums.org/showthread.php?t=353640](http://ubuntuforums.org/showthread.php?t=353640)

Hopefully someone will come along and resolve our issues. :)

---

### Post by jd65pl on 2007-02-05
Have you tried booting in recovery mode? Does this yield any error messages?

---

### Post by Rabbit_Alex on 2007-02-05
I just restarted in recovery mode and got this error:

[17179579.176000] usb 3-2: new low speed USB device using uhci_hcd and address 2

The next line is the same except it says 4-1 instead of 3-2.

Any ideas?

---

### Post by Prinz on 2007-02-05
I decided to just reinstall everything again, I wasnt completly happy with the way I partitioned the drive anyways. 

@ Rabbit_Alex: If I'm wrong please correct me, but doesnt that just mean that you have a USB device connected using a slow port? Are you using an older computer with USB 1.0?

---

### Post by Rabbit_Alex on 2007-02-05
That is correct, my computer only has USB 1.0.  It's a 2.5 year old Dell Inspiron 9100 laptop.

I had my printer and the receiver for my wireless mouse in the ports so that's why the message came up.  I took them out and tried rebooting and it didn't give the message, but it still wouldn't get past the command line after the Ubuntu progress bar.

I tried using Alt+Ctrl+F1-F12 when it appeared that the computer froze, but that didn't do anything.  I found that that Alt+Ctrl+F1 makes the console say some normal boot messages and then "Uncompressing Linux,...Ok, booting the kernel".  Pressing Alt+Ctrl+F8 would clear the console, and the other F keys didn't do anything.

Booting in recovery mode also apparently freezes at this point.

Any ideas?

---

### Post by Rabbit_Alex on 2007-02-10
I reinstalled using the alternate CD, so no problems now.

---

### Post by Ossipon on 2007-02-10
I had the same problem and solved it a few minutes ago.:)  It happened after I upgraded my 2.6.17.10 kernel to 2.6.17.11. After detecting my usb devices, nothing happened for a while and then th following error message appeared:

```
/bin/sh can't access tty; job control turned off
```

Here's my solution:

boot a live cd or another linux installation
mount your broken ubuntu partition
open /boot/grub/menu.lst

Find your standard ubuntu entry; mine looked like this:


```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=UUID=8f5d70f8-1535-4b88-b58f-89748a89f0ba ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
savedefault
boot
```

The problem was the UUID part. I don't know what it's for, but I replaced it with my old partition name, like this:


```
title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
savedefault
boot
```

In other cases I've read on other forums, the problem can be that the partition names changed (/dev/hdb2 instead of /dev/hda2 for instance). In that case, execute ```
sudo fdisk -l
``` to find your installation.

---

### Post by shane2peru on 2007-02-10
I had the same problem this morning, and had to re-install grub.  See [this post here.]("http://www.ubuntuforums.org/showpost.php?p=2134220&postcount=5")

That is how I solved my problem.

Shane

---

