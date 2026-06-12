---
title: "GNU GRUB command line after update"
date: 2011-09-06
forum: Installation &amp; Upgrades
---

### Post by NobleRooster on 2011-09-06
Long time since I've played around with Ubuntu and decided to put it on an old Dell Inspiron 2200 laptop I had for my parents to use around the house.

Well, installation went fine and I did an update check once I had an internet connection established and installed a bunch of updates.  Went to reboot and now I'm getting a screen on bootup like the following:

[[IMG]http://img856.imageshack.us/img856/5130/img20110906151343.th.jpg[/IMG]](http://imageshack.us/photo/my-images/856/img20110906151343.jpg/)

Uploaded with [ImageShack.us](http://imageshack.us)

I'm guessing somehow something happened with GRUB, but I'm not sure.  Any help on this would be greatly appreciated.

---

### Post by YesWeCan on 2011-09-06
[https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage](https://help.ubuntu.com/community/Grub2#GRUB_2_Prompt_Usage)

---

### Post by drs305 on 2011-09-06
Since you are at the "grub" and not the grub rescue prompt, you may be able to get the grub menu to display by typing this:
```
insmod (hd0,1)/boot/grub/normal.mod
```

If that doesn't display the Grub menu, or the menu fails, proceed with the manual boot options in the section(s) referenced by *YesWeCan*
It looks like your Ubuntu partition should be on **(hd0,1)** in Grub2 language.

---

