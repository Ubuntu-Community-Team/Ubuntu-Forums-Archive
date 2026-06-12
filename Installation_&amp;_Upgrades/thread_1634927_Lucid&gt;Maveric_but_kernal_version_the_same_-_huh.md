---
title: "Lucid&gt;Maveric but kernal version the same - huh?"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by ttguy on 2010-12-01
So I smoothly upgraded Lucid > Maveric last night using the Update manager.

And this evening I was curious as to what kernal version I now have. So 

```

$ uname -r
2.6.32-24-generic


```Which surprised me because that is the same version that uname reported before the update.  Is this normal? I would have thought I would get a new kernal version. I previously downloaded a live CD instance of Maveric and it has a 2.6.35-22-generic kernal.

I would have thought I would therefore have at least 2.6.35-22-generic after upgrading.

:-?

---

### Post by dino99 on 2010-12-01
sudo update-grub

so you may run startup-manager to select on which kernel you want to boot on

---

### Post by ttguy on 2010-12-02
> **dino99 said:**
> sudo update-grub

so you may run startup-manager to select on which kernel you want to boot on

Right. You refer the the grub menu - hit Esc to enter it.
If I do this the highest kernel available is still 2.6.32-24-generic.
But I now realize that this would be because when I was upgrading I got the option to overwrite or keep my modified /boot/grub/menu.lst and I choose keep. 

So how can I find out what kernels I have to pick from so I can edit up my own menu.lst ?

---

### Post by ttguy on 2010-12-03
So in the end I upgraded my grub from grub1 to grub2 as per [https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2.]("https://help.ubuntu.com/community/Grub2?action=show&redirect=GRUB2") And now I can boot to 2.6.35-23-generic

---

