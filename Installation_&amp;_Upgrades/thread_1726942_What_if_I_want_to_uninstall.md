---
title: "What if I want to uninstall"
date: 2011-04-11
forum: Installation &amp; Upgrades
---

### Post by velt on 2011-04-11
Hi, I'm new around here, i was looking on information about the ubuntu instalation, specifically what happens if i want to uninstall ubuntu and go back to win7; what happens to the boot menu?
Will it simply go away and windows 7 is going to boot as usual?

---

### Post by poodoopealeoaph on 2011-04-11
Well grub boot installer should still stay where it is at so you may still have the same boot installer prompt but it would probably not give you any other options but windows.

The best way to go about this is to find a partitioning program.. usually those on hiren's disk are fairly good, and just look at your partitions. If you really want to get rid of ubuntu, which I really don't recommend, you can select the ubuntu partition and clear it out.... You would be completely rid of ubuntu and you would only have windows but you would have the ubuntu partition left blank. So, you would be better off to just keep ubuntu because you still wouldn't really be able to use that part of the hard drive unless you did a complete reinstall of windows and formatted the whole thing.

---

### Post by oldos2er on 2011-04-11
If you're looking for something like a demo, check out Wubi: [http://www.ubuntu.com/desktop/get-ubuntu/windows-installer](http://www.ubuntu.com/desktop/get-ubuntu/windows-installer)

---

### Post by Hedgehog1 on 2011-04-11
[SIZE="4"]Any good plans needs an exit plan.[/SIZE]

Here is how you uninstall a dual-boot of Ubuntu and return Windows to how it worked before:

First, get your PC to boot directly into Windows again:

To make a Windows 7 / Vista emergency repair disk (in case you don't already have one made):
[IMG]http://img641.imageshack.us/img641/9550/small50createrepairdisk.png[/IMG]

If you are unable to make a recovery disk, you can download the ISO for   [VISTA]("http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/") or [WINDOWS7]("http://neosmart.net/blog/2009/windows-7-system-repair-discs/")

Boot from the windows 7 / Vista  emergency repair disk, do the following:
[IMG]http://img10.imageshack.us/img10/5826/small51runningrecoveryd.png[/IMG]
[IMG]http://img856.imageshack.us/img856/3690/small52selectingwindows.png[/IMG]
[IMG]http://img826.imageshack.us/img826/3484/small53commandprompt.png[/IMG]
[IMG]http://img215.imageshack.us/img215/9547/small54bootrec.png[/IMG]

---

### Post by Hedgehog1 on 2011-04-11
To remove Ubuntu:
[IMG]http://img718.imageshack.us/img718/7687/small55diskmanagement.png[/IMG]
Remove Swap Partiton
[IMG]http://img97.imageshack.us/img97/4905/small56deleteswap.png[/IMG]
[IMG]http://img231.imageshack.us/img231/2992/small57freespace.png[/IMG]
Remove Ubuntu Partition
[IMG]http://img96.imageshack.us/img96/5986/small58deleteubuntu.png[/IMG]
Remove extended Partition
[IMG]http://img848.imageshack.us/img848/8053/small59deleteextended.png[/IMG]
Expand windows partition to use all the space
[IMG]http://img3.imageshack.us/img3/7880/small61extendwin7volume.png[/IMG]


***The Hedge***

:KS

[SIZE="3"]p.s. SO - now that you know how to undo it - give Ubuntu a try.[/SIZE]

---

### Post by velt on 2011-04-12
Thanks The hedge!

> **Hedgehog1 said:**
> To remove Ubuntu:
Remove Swap Partiton


***The Hedge***

:KS

[SIZE=3]p.s. SO - now that you know how to undo it - give Ubuntu a try.[/SIZE]

---

