---
title: "Hangs on GRUB"
date: 2020-03-03
forum: Installation &amp; Upgrades
---

### Post by rikkzazz on 2020-03-03
Hello experts,

I have a strange one for you.

I had a working installation of Ubuntu 18.04, on an old Dell Dimension 9150.

But an evil automatic upgrade broke everything. Anyway, I prodeeded to reinstall, with my USB key, used to build my machine in the first place.

Well now, as soon as I pass BIOS, I get a black screen with "GRUB" and a flashing cursor besides it. Nothing else. It just sits there.

Tried another version, same thing. I suspect it hangs on a GRUB partition on the disk.

Any thoughts?
Rikk

---

### Post by oldfred on 2020-03-03
Do not run any auto fix suggestions until someone has reviewed report.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by rikkzazz on 2020-03-04
I ran an old version of Ubunto, on DVD, and destroyed the old partition. So now, I’m trying to do a pristine install, with a clean disk. But, I still get that black GRUB screen with the flashing cursor. 

It didn’t do this, the first time I use this USB image. Very odd!

---

### Post by CelticWarrior on 2020-03-04
If it's the exact same USB you used before (without additional kernel parameters) and now is not loading the graphical desktop, I would say it's corrupt. Better redo it in another computer.

Of course, now that you removed all the partitions the only solution is a reinstallation. It probably could be easy solved without the nuclear option but you didn't do what the expert advised and you didn't wait....

---

### Post by rikkzazz on 2020-03-04
Hey CelticWarrior,

I didn't really care for the OS. It was shot anyway with that OS upgrade that totally screwed up my graphics card setup.

I figured out what the problem was. Turns out that I built my USB key with ImageUSB whereas, last time, I used Rufus.

I guess no two USB Imaging softwares aren't built alike. Live and learn.

BTW, since this is a DAW system for my son ( who isn't particularly linux saavy) , I disabled automatic updates. S'good enough!

Thanks for your response.!!
:)

---

