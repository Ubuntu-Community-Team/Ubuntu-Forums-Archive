---
title: "Win98 sees Ubuntu partition"
date: 2005-10-30
forum: Installation &amp; Upgrades
---

### Post by Mujaheiden on 2005-10-30
Good morning,

Everytime I ask grub to startup my win98 partition, Scandisk is launched, and says it cant do anything with my E-drive, which is  in fact correct, because that's where Ubuntu is residing. Subsequently, "My Computer" lists E: with no specs, and tries to make me format it, the moment I accidently click it.

Is there a way I can hide my Ubuntu partition for Windows, as W98 won't be able to work with it anyways?  That would be chique.

---

### Post by SilentCacophony on 2005-10-31
Hi. Grub has a 'hide' which makes the partition invisible to the OS. I'd say that some care should be used with it, as I think it directly modifies the partition table.

I've never used it, but I know it can be useful, for example, to boot multiple installations of Windows.

I believe that once you hide a partition when booting from another partition, you must explicitly 'unhide' it when booting from that partition. I have a link which contains example material:

[http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html](http://www.faqs.org/docs/Linux-mini/Multiboot-with-GRUB.html)

also, goggling 'grub hide' should provide more info, and the online grub docs are here:

[http://www.gnu.org/software/grub/manual/html_node/index.html](http://www.gnu.org/software/grub/manual/html_node/index.html)

---

