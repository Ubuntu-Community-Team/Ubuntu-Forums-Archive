---
title: "Bootloader help (Grub &amp; Win bootloader) -Triple Boot-"
date: 2010-08-27
forum: Installation &amp; Upgrades
---

### Post by d3mncln3r on 2010-08-27
I installed my OS's backwards: W7 64-bit, W7 32-bit, and Ubuntu. I set the boot flag to the Ubuntu partition, so it loads Grub, giving me Ubuntu and Windows (bootloader) options to load from. If I select Windows (bootloader) it brings me to the next screen where I choose which windows I want to load. I would like to have all three choices available at the Grub boot screen. I've read up, and I know that optimally I should have installed Ubuntu first, then the two windows a few tweaks and I'd be there.

What I need to do is what Perturbed Penguin suggested in this thread: [http://ubuntuforums.org/showpost.php?p=8356708&postcount=12]("http://ubuntuforums.org/showpost.php?p=8356708&postcount=12")

but I can't quite figure it out.

---

### Post by presence1960 on 2010-08-27
It has nothing to do with the order in which you installed the OSs. It has to do with how windows works by default. When you installed the second windows OS you should have taken the boot flag off the current windows install and put it on the partition to which you were installing the second windows OS. Since you didn't do that your windows automatically combined the boot files for the second windows OS with the boot files of the first windows OS.

---

### Post by d3mncln3r on 2010-08-28
Ok, I understand that. From the thread I posted above and other threads, clearly that was the route I should have gone. But, it's a learning process and this time around I didn't get it perfect. Is there a way I can fix it? Somehow trick windows bootloader into thinking there aren't two copies of windows? Or maybe simply add both OS's to my Grub menu, bypassing the need for W. Bootloader?

---

### Post by oldfred on 2010-08-28
You could try moving boot flag and repairing but you may mess up windows. I have not tried it.

Herman says windows will still find the second install, even if you hide the windows partition.
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing]("http://members.iinet.net/%7Eherman546/p15.html#BOOTMGR_is_missing")

From the boot info script (in presence1960's signature) you need all three
/bootmgr /Boot/BCD /Windows/System32/winload.exe

Your second install is missing /bootmgr and /boot/BCD. Maybe EasyBCD will be more flexible than the windows bcd repair?

And if one of your windows is in a logical partition you will not be able to repair it at all.

---

### Post by d3mncln3r on 2010-08-28
Ok, well considering the fact that both my windows installs are completley fresh, and I haven't done anything to them, should I delete and then go ahead and reinstall, following methods suggested earlier? Or is it too late for this?

---

### Post by oldfred on 2010-08-28
That would be the easiest way. Be sure to use primary partitions for both windows. You should only have to reinstall one.

To get each MS to have its own boot loader make a primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

### Post by kelvinho on 2010-08-28
Not wishing to be a killjoy ... but you could always save time and tolerate the issue. It can't be that much of a bind can it?

Debian is a pretty good option too ...

---

