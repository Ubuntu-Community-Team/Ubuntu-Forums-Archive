---
title: "Problem with multiboot XP / Seven / Lucid"
date: 2010-07-02
forum: Installation &amp; Upgrades
---

### Post by Marie_75 on 2010-07-02
Hello ,

I try to explain trying be clear:

SATA1: XP (installed in 1st) / SEVEN (installed in 2nd)
SATA2: Lucid Lynx (installed in 3th)

my problem:

If I connect only SATA1: Windows Loader takes care and I can boot on XP as on Seven without any problem.
If I connect only SATA2: I can boot on Lucid.
If I connect the 2 DD: Grub takes care. If I choose Lucid, no problem. If I choose Seven,(Loader) I arrive, logically, on Windows Loader which makes me the proposition between previous versions of Windows (so XP) or Seven. 
If I choose Seven, no problem, but if I choose " previous Versions "the PC reboot. :sad:
                                                                                                                      
For my part it would be rather Windows Loader that work bad, on the other hand, it works when I don't connect the disk with Linux.... so ...?..?..

If any have an explication...:)

 Thank you by advance.

---

### Post by dino99 on 2010-07-02
so how was installed ubuntu ? with both hdd or only sata2 (which should be known as /dev/sdc into ubuntu/grub naming)

as you describe the problem i think that installation have been done with both hdd plugged and grub installation have overwritten xp loader

mini howto: [http://ubuntuforums.org/showpost.php?p=9216264&postcount=14](http://ubuntuforums.org/showpost.php?p=9216264&postcount=14)

---

### Post by oldfred on 2010-07-02
Because of the way you installed windows only one windows will be bootable. Windows combines its boot loaders and from grub you cannot directly boot the second windows install except thru the one with the boot flag where windows has combined its boot. If you ever delete the first install you will not be able to boot the second even with windows.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

---

