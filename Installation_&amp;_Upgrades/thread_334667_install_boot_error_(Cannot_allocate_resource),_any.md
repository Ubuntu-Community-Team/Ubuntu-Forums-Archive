---
title: "install boot error (Cannot allocate resource), any ideas ?"
date: 2007-01-09
forum: Installation &amp; Upgrades
---

### Post by _jB on 2007-01-09
I, still, have a little boot problem with ubuntu 6.06/.10. 

**Hardware**
[INDENT]AMD 3400+
1.5 gb PC3200 (3x512)
Asus K8N4-E Deluxe (onboard lan/audio, no pci-slots in use)
inno3d 7900GT (pci-e)[/INDENT]

**Boot error**
> [36.164989] PCI: Cannot allocate resource region 4 of device 0000:00:06.0
[36.165031] PCI: Cannot allocate resource regien 0 of device 0000:05:0a.0
[36.165618] Error while updating region 0000:00:060/9 ( 00001001 != 0000f001 )
[36.165648] PCI: Failed to allocate I/O resource #0:8000@10000 for 0000:05:0a.0
[36.165705] PCI: Failed to allocate mem resource #1:40000000@c0000000 for 0000:01:00.0
cp: unable to open '/root/var/log' : no such file or directory

mount: mounting /root/dev on /dev/.static/dev : failed no such file or directory
mount: mounting /sys on /root/sys : failed no such file or directory
mount: mounting /proc on /root/proc : failed no such file or directory
Target filesystem doesn't have /sbin/init

[pauses a bit]
[58.502065] hda:cache flushes not supported

hda: dma.timer_expiry: dma status 0xff
hda: dma.timer_expiry: dma status 0xff
hda: dma.timer_expiry: dma status 0xff
hda: dma.timer_expiry: dma status 0xff
[repeats x-times]

If I boot the livecd with **dma=off acpi=off** it boots fine (although my mouse dies after 10-15minuts of using the system).

I tried booting without any hard-drives, ran memtest (no errors), different settings in bios (but mayby i haven't found the correct setup yet), different cd's (burned at different speeds) a.s.o., still same problem. 

+ Should I just install 6.10, edit grub to boot without dma and acpi or ?
+ Is it my motherboard that is linux unfriendly ?
+ or ??

I really hope soneone can help out, getting "tired" of ubuntu 5.10 :)

*[SIZE="1"]p.s.; the machine is in use everyday and 5.10 is working fine[/SIZE]*

---

### Post by _jB on 2007-01-28
Finally got a new system installed (debian etch) but that also had to have **dma=off acpi=off ** when booting. But today i finally found a solution to it @ [http://forums.gentoo.org/viewtopic-t-418790-highlight-ehcihcd+0000+00+02+1+init+0000+00+02+1+fail+16.html]("http://forums.gentoo.org/viewtopic-t-418790-highlight-ehcihcd+0000+00+02+1+init+0000+00+02+1+fail+16.html")

> Remove support for mmconfig config space access in the kernel configuration, it's broken on Asus boards with recent kernels apparently (I have this board, and nothing that's connected on PCI works with mmconfig enabled). It's here in the kernel configuration:
Code:
Bus options (PCI etc.)  --->
  [ ]   Support mmconfig PCI config space access
You can also boot with "**pci=nommconf**" added to the kernel parameters, it should disable mmconfig too.

So now dma is on and so is acpi :)

---

