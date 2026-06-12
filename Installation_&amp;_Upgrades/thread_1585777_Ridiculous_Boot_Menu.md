---
title: "Ridiculous Boot Menu"
date: 2010-10-01
forum: Installation &amp; Upgrades
---

### Post by Luther786 on 2010-10-01
I set up my computer a few months ago. I am running a dual boot of windows 7 and ubuntu 10.04. I have noticed that my boot menu is rather strange. Instead of having just two choices, the windows and linux, I have six choices of linux and one of windows. Things are randomly added to my boot menu as well. 

Why is this happening and how can I clean up my boot menu?

---

### Post by sid.mallya on 2010-10-01
^ I think those are the new kernel version you've downloaded / updated over time. The top one is the newest version of your kernel .. prolly x.25

---

### Post by Goolie on 2010-10-01
> **sid.mallya said:**
> ^ I think those are the new kernel version you've downloaded / updated over time. The top one is the newest version of your kernel .. prolly x.25

Yes, they are the different kernel versions, I'm not sure of the exact instructions, but google removing kernel options (if you want) from the boot menu and you should only have 3, One for linux, one for linux recovery, and one for your windows partition.

I did this, but I don't remember how, haha, but yea it confused me at first, but if you don't remove the other extra kernel version, the top on is usually the best (newest kernel) choice.

---

### Post by Rubi1200 on 2010-10-01
It is always best to leave at least 2 entries just in case an update/upgrade goes wrong so you can then still boot into an older kernel.

That said, post the results of the /boot/grub/grub.cfg file and I will help you clean things up.

Oh, by the way, it is quite normal for these entries to appear in the GRUB menu.

---

### Post by Luther786 on 2010-10-01
Thanks guys, that's good to know. I just thought my computer was going to explode or something. 

It's silly to have six linux kernels to boot from on there so I think I'll take a few off :)

---

### Post by efflandt on 2010-10-01
If you want to uninstall old kernels, I just use Synaptic with **linux** in Quick search.  That still provides a lengthy list, but you can go through that and mark images, generic, headers, etc. for removal of the specific old version(s) you want to remove.  That will automatically run update-grub so removed kernels will no longer appear on the grub menu.

It is normal for each kernel version to show a regular boot and (recovery) boot, the latter for boot to text console in case you are having some problem with X or you need to install/uninstall something when X is not running.

---

### Post by Chris1274 on 2010-10-01
To narrow down the list, you can just search in Synaptic for 2.6.32-XX, where 'XX' is the version of the kernel you want to remove.

---

### Post by Rubi1200 on 2010-10-01
You also need to remove the linux-headers for the kernel version you are removing; in other words, 3 files in total for each version.

---

### Post by Alver on 2010-10-01
> **Rubi1200 said:**
> You also need to remove the linux-headers for the kernel version you are removing; in other words, 3 files in total for each version.
One of the "simpler" methods to remove unwanted versions and headers is to install "Ubuntu Tweak" and to remove from within this programme. One word of caution though, UT is quite powerfull in removing almost anything. Hope this helps.

Alver

---

### Post by Rubi1200 on 2010-10-01
I strongly advise against using programs like Ubuntu Tweak; as pointed out they can do more harm than good.

Use the built-in tools in Ubuntu; they are quite powerful enough to accomplish this task.

---

### Post by wilee-nilee on 2010-10-01
> **Alver said:**
> One of the "simpler" methods to remove unwanted versions and headers is to install "Ubuntu Tweak" and to remove from within this programme. One word of caution though, UT is quite powerfull in removing almost anything. Hope this helps.

Alver

+1 on the Ubuntu Tweak, I know how to install and remove kernels, but I just use UT to remove them it's much easier and safer for beginners, I think personally.

---

### Post by Luther786 on 2010-10-01
Thanks for the help guys. I thought ubuntu tweak was the easiest to work with and easiest way not to screw things up. It sounds counter-intuitive, but the layout is easier to navigate so I am less likely to delete things without knowing I just deleted them. 

I can see how ubuntu tweak could really screw up your system though, which is why I am being very very selective on what I delete.

Thank you again :)

---

