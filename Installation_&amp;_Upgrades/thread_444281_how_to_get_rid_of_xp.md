---
title: "how to get rid of xp??"
date: 2007-05-15
forum: Installation &amp; Upgrades
---

### Post by ninjaprawn on 2007-05-15
hi,

im still fairly new to linux! i was using suse10.2 for 3months, never really felt comfortable, then feisty fawn came out, and i switched!

what adifference! so, after a month with feistyy fawn, i havent used my winxp boot once!!!!

i now want to get rid of xp! im guesing that the main part to do is to remove it from the grub and boot options, then 2 format the partitions,

but where would i start??

i made the mistake a long time ago, of just removing xp's partitions, with no extra work, and obviously couldnt boot from then on!!

just a little guidance if possible please?

thanks!!

---

### Post by taurus on 2007-05-15
First, make sure that partition is not mounted.  Then, use gparted (install it if you don't have it in System -> Administration) and format that partition to something like ext3.  

Now, you can mount that partition somewhere and use it as a storage if you wish.  And since there is no XP on your machine anymore, you need to edit /boot/grub/menu.lst

```
gksudo gedit /boot/grub/menu.lst
```
and remove the entry for XP.

[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by floke on 2007-05-15
I imagine that running 'sudo update-grub' from the terminal would have the same effect? (easier than editing the menu.lst file)

---

### Post by ninjaprawn on 2007-05-15
that was pretty simple, thanks!

---

