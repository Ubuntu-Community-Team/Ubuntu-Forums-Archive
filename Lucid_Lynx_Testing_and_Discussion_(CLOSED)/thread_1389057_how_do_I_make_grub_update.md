---
title: "how do I make grub update?"
date: 2010-01-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by DouglasAWh on 2010-01-23
At some point grub decided to stop updating my kernel list.  It still boots fine and I can change -5- to -11-, but that's rather annoying. Karmic is the default boot, running grub2 and lucid is the secondary.  It was running grub1, but just upgraded to grub2 to see if it would fix this problem...it didn't.  I assume this is more of a grub2 issue than a Lucid issue, but just in case, I put it here.  Updates are current on both systems.  I knew how to edit /boot/grub/menu.lst, but I don't know how to do it now...or on which system I need to do it.  As Karmic is the main one, it seems the changes should be on the lucid image.  Just don't know. Thanks!

---

### Post by kansasnoob on 2010-01-24
> **DouglasAWh said:**
> At some point grub decided to stop updating my kernel list.  It still boots fine and I can change -5- to -11-, but that's rather annoying. Karmic is the default boot, running grub2 and lucid is the secondary.  It was running grub1, but just upgraded to grub2 to see if it would fix this problem...it didn't.  I assume this is more of a grub2 issue than a Lucid issue, but just in case, I put it here.  Updates are current on both systems.  I knew how to edit /boot/grub/menu.lst, but I don't know how to do it now...or on which system I need to do it.  As Karmic is the main one, it seems the changes should be on the lucid image.  Just don't know. Thanks!

Run the command:

```
ls /boot/grub
```

You'll see a huge list in columns, it's in alphabetical order. Look for **grub.cfg** & **menu.lst**. If you have both then you have mixed legacy grub and grub2 files.

That screws things up! Whether or not that's the case I'd really like to see the output of the Boot Info Script as described here:

[http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)

It really is incredibly easy to fix but I need some specific system info.

BTW don't get impatient and just try removing one or the other. I've done this several times so just be patient.

---

### Post by VMC on 2010-01-24
I would also like to further suggest to change from hard links to symbolic links.

 That way after every new kernel update it will boot to the newest kernel automatically.

The symbolic links are found at the root directory as, "vmlinuz" and "initrd.img". You should see the *old as well. They point to the previous kernel.

---

### Post by DouglasAWh on 2010-01-24
> **VMC said:**
>  That way after every new kernel update it will boot to the newest kernel automatically.

oh it does that. Karmic is the default and no trouble updating that ever.  I got it fixed in Lucid too. Yay!

---

