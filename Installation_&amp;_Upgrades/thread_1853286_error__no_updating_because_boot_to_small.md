---
title: "error:  no updating because /boot to small"
date: 2011-10-02
forum: Installation &amp; Upgrades
---

### Post by ubto66 on 2011-10-02
OS:
ubuntu 10.04 lts pre boot authentication on 16gb usb flash drive.

On last updating this error message occured:
needs total of 19,9m space on /boot. Free at least
3.710k on
/boot.

And updating wasn't possible.

Disk usage analyzer says:
14,1gb used 6,7gb availiable 7,3gb.

total filesystem capacity (narked red) 100% 14,1
total filsesystem usage 47,7% 6,7

filesystem -> boot:
100% (marked red) 200,1mb 63 items
grub 2% 4mb 185 items
locale 0,1% 4kb 3 items
lost + found 0% 12kb 0 items

So isn't there space enough on the drive?
Solution?

Thanks.

---

### Post by 2F4U on 2011-10-02
Do you have several kernels stored in /boot? If yes, try to remove kernels you no longer need.

---

### Post by ubto66 on 2011-10-04
Thank you for answering.
The boot folder is full of
abi, config, initrl, system map, vmcoreinfo
and vmlinuz files.
How to I know which one to delete?

---

### Post by dino99 on 2011-10-04
is /boot a folder or a partition ?

standard installation:
[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by ubto66 on 2011-10-04
I know about partitions in windows, not ubuntu.
But to get to the boot folder you click "places"-> "homefolder"
->'filesystem'-> "boot",
and it gets listet. So I would say it is a system folder in
ubuntu.
During installation of ubuntu, I didn't make any changes regarding
partitions but just used default settings.
I don't know why the error happened. I haven't made many changes
to the system. And used the 'download manager'.
It puzzles me, that I have a mirror (same) ubuntu installation
running in a virtual box, on another computer.
And the size of the virtual hard drive is 15gb, so the same size.
The boot folder on the virtual ubuntu is close to the same size,
and also contains 63 items/files. But there are no update
errors. Is there any repair procedures I can run?+

---

### Post by ubto66 on 2011-10-06
I found a solution here:
[http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/](http://www.liberiangeek.net/2010/07/remove-kernel-ubuntu-10-04-lucid-lynx-grub/)

---

