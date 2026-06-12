---
title: "Multiboot Ubuntu, OPENsuse and Win 7"
date: 2011-03-27
forum: Installation &amp; Upgrades
---

### Post by ZekeGraal on 2011-03-27
Hey everyone, I started with windows 7 starter. Then I dualbooted that with Ubuntu 10.04, (Which is now 10.10). I'm currently making a live usb for opensuse just to try it out. If I like it, I can install it next to the other two correct? I believe I just have to choose not to install a bootloader and then run a grub update. Is this correct? Any advice is appreciated, and I'm no noob to Linux either, I've been running Ubuntu for probably 2 years, give or take a few months, now.

Thanks,
Zeke :]

---

### Post by Quackers on 2011-03-27
It may be better to install opensuse's bootloader (grub legacy) to the opensuse root partition. That is what I did. But that does mean that you will need to reboot into Ubuntu then run sudo update-grub (if grub is in control) so that the menu entry for opensuse appears in grub.
This way has the benefit of grub2 not having to fight with grub legacy.
There are, however, different ways to do it. Other people here will have used a different method and it may be advisable to wait for their responses before you make your decision.

---

### Post by coffeecat on 2011-03-27
As Quackers says, there are several solutions, but I  agree with his. The opensuse installer (in common with that of Fedora if you're ever tempted to try Fedora) makes no attempt to detect other Linux operating systems and will simply set up a dual-boot menu for Suse and Windows if you have Windows. Or Suse alone if there is no Windows.

If you allow the opensuse installer to install legacy grub stage 1 to the mbr of your sda drive, you will then have to manually edit suse's menu.lst to include an entry for Ubuntu. Easier, therefore, to do as Quackers suggests. Tell the opensuse installer to install its version of grub to the suse partition, not the mbr. When you are prompted to reboot you will be confronted with the Ubuntu grub menu but without an entry for suse. Boot into Ubuntu, run 'sudo update-grub' and then reboot and you will then see a menu entry for opensuse and you will be able to boot into it to finish the installation.

---

### Post by ZekeGraal on 2011-03-27
Thanks guys, but I decided that I wouldn't be using it. I'm kinda unused to the desktop, (I ran KDE live, the only time I've used KDE is when I tried the plasma desktop on Ubuntu). And it runs a bit slower than I'd like on my netbook. I will say, it looks very polished. I'm looking for a Linux that can handle an MMO with a 1000+ playercount when it only has an atom processor to use, so the appearance isn't much of a concern to me at the moment. I believe I'll stay with the Ubuntu OS family for now :D

Edit: I only tried it because it was the Linux distro that my friend first recommended to me. :P

---

### Post by coffeecat on 2011-03-27
There is a gnome version of opensuse, also available as a live CD if you want. The gnome desktop is configured somewhat differently from what you're used to in Ubuntu, but it's still recognisably gnome. 

Good luck with whatever you use. :)

---

### Post by ZekeGraal on 2011-03-27
> **coffeecat said:**
> There is a gnome version of opensuse, also available as a live CD if you want. The gnome desktop is configured somewhat differently from what you're used to in Ubuntu, but it's still recognisably gnome. 

Good luck with whatever you use. :)

Thanks, I knew that there was one, and I will try it. Not today though, haha, I live in the middle of nowhere, and downloading another flavor normally takes me about two hours xP (and it's even DSL!):lolflag:

---

