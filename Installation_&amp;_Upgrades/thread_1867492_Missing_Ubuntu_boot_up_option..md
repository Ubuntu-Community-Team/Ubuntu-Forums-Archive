---
title: "Missing Ubuntu boot up option."
date: 2011-10-23
forum: Installation &amp; Upgrades
---

### Post by zu5be on 2011-10-23
Hello Good people, couple of days ago, i installed Ubuntu:p 11.10 side by side of windows 7. It was working fine and just yesterday when i started my computer. windows 7 loaded directly. i restarted again and couldn't find the choosing option between windows 7 and Ubuntu. Now all the time windows 7 loads directly.

Any fix?

---

### Post by shadytv on 2011-10-23
when booting up try pressing and holding "shift" or "esc", its most likely shift this should force grub to load, any idea why its not loading?

---

### Post by zu5be on 2011-10-23
> **shadytv said:**
> when booting up try pressing and holding "shift" or "esc", its most likely shift this should force grub to load, any idea why its not loading?

shift did help to show the boot up option but without ubuntu..

---

### Post by staticd on 2011-10-23
If no menu turns up even after pressing shift, grub( the thingy that gives you the menu for choosing between ubuntu and Windows) might have got wiped by some windows soft ware. 

(If you have installed ubuntu to a separate partition)
you could try the instructions posted here [http://ubuntuforums.org/showthread.php?p=11264694.]("http://ubuntuforums.org/showthread.php?p=11264694")
your command will most probably be --boot-dir=/media/something/boot

Search around for restoring grub.

---

### Post by jyothishsv on 2011-10-23
You can try boot repair from a live cd or live usb. this helped me once to restore boot data:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by staticd on 2011-10-23
Have you installed ubuntu to a separate partition or is it a Wubi install?

If it is a separate partition boot from a live CD and check if the partition has the files /boot/vmlinuz-blah 
Depending on that we can proceed.

---

### Post by shadytv on 2011-10-23
from a livecd can you see your Ubuntu system? if so try running sudo update-grub

---

### Post by zu5be on 2011-10-23
> **staticd said:**
> Have you installed ubuntu to a separate partition or is it a Wubi install?

If it is a separate partition boot from a live CD and check if the partition has the files /boot/vmlinuz-blah 
Depending on that we can proceed.

Yes i have installed it on a separate partition. while checking for the file boot/vmlinuz-blah i found out, there is not Ubuntu folder! i actually hided the folder before, but now after changing the show hidden files opetion in windows, its not there... Wonder wonder:(

---

