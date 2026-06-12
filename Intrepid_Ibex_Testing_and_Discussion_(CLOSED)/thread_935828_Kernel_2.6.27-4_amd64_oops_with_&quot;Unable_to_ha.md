---
title: "Kernel 2.6.27-4 amd64 oops with &quot;Unable to handle kernel paging request&quot;"
date: 2008-10-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by captive on 2008-10-02
Hi,
I'm on a x86/64 platform and just installed intrepid beta.
I got a kernel oops as in topic, no matter which boot option I add.
I tried safe mode, and the following switches:
[LIST]
[*]noapic
[*]noapictimer
[*]nolapic (x86/32 only??)
[*]nolapic_timer (x86/32 only??)
[*]acpi=off
[*]nohz=off
[*]highres=off
[*]hpet=disable
[/LIST]
and almost all possible permutations of the above parameters, with no luck. I filed a bug on [launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/276911").
Is there anybody with the same issue?

Edit:
With the old Hardy kernel (2.6.24) booting is fine and system works perfectly.

Edit 2:
Kernel 2.6.27-3-generic (the one on cdimage live cd) seems to work, But only if booting from usb stick. On a fresh-burned cd I got the same issue.

---

### Post by captive on 2008-10-04
Ok, I figured out how to solve this.
After a bit of searchiong and tweaking I added a 
```
iommu=noaperture
```
to the kernel options in grub, removing splash option.
Now everything seems to work.

---

