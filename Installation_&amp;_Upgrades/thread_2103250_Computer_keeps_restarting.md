---
title: "Computer keeps restarting"
date: 2013-01-09
forum: Installation &amp; Upgrades
---

### Post by Lokhtar on 2013-01-09
So I have windows 7 and I installed Ubuntu last week.  It worked fine, and I haven't had to use windows all week.  Today I had to do something so I booted into windows, and that worked too.  But rebooting after that - the computer keeps restarting. I think windows rewrote my MBR or something.  Now I can't boot into any os!  Please help, I don't have my Ubuntu cd anymore but I do have access to another computer and a USB drive (and my pc does support USB boot).

---

### Post by rmil on 2013-01-09
The question is what is the really reason for restarting. If the restarting is happening too fast it can be the problem with motherboard.

Anyway you have to get installation CD or USB and boot into try or rescue mode. Personally I prefer try mode and terminal.

Then you use ```
sudo grub-install /dev/sda
```sda is the first disk. Generally you can visit also here
[http://ubuntuforums.org/showthread.php?t=2103164&highlight=install+grub+windows](http://ubuntuforums.org/showthread.php?t=2103164&highlight=install+grub+windows)

---

### Post by Lokhtar on 2013-01-09
It's not the motherboard I'm almost sure because it gets to the point where it would normally display the boot menu.  

I will try that and report back -  thank you.

---

### Post by Lokhtar on 2013-01-09
I was able to boot via USB. However when I try to run that command (with any disk: /dev/sda, /dev/sda1, etc) it gives me the error:

Path '/boot/grub' is not readable by grub on boot.  Installation is impossible.  Aborting.

---

