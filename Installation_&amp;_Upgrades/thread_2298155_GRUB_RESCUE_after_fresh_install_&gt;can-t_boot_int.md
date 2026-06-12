---
title: "GRUB RESCUE after fresh install &gt;can-t boot into my PC at all, this is a notebk"
date: 2015-10-09
forum: Installation &amp; Upgrades
---

### Post by webwiller on 2015-10-09
Ciao!

After a fresh install 
of **ubuntu 14.04 in dualboot with windows10.** The smooth installation asks for reboot at the very end. I accept and the screen I get is
 
[B][I]grub rescue>
[/I][/B]
on a nice, plain, black screen. I googled around and found different pages with different commands but all of the at a certain point I got some sort of error or different result but there was noway to interact. They where just articles of a newspaper.

I-m a baby/ubuntu///it-s a week I-m breaking up both my PC-s with ubuntu...I love already....but I find myself stuck in every single situation. I need a step/by/step guide and if I get different results or error I can interact. I also believe the grub splash is set with english keyboard...so I get really MAD only to find a /.*Thx in advance to any CustodyAngel *do you say it in english too?*

web :D

---

### Post by yancek on 2015-10-09
You mention some sort of error but didn't post anything.  If you get errors, you need to post them to help you get help.  Is your windows 10 using UEFI to boot and did you install Ubuntu in UEFI?  If you don't know what that means, the best next step is to get more detailed information and you can do that by going to the Ubuntu site below and reading through the information, then downloading and running the boot repair software using the Ubuntu installation medium.  This will answer most questions about your system and should get you some help.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by egeezer on 2015-10-09
Try the following ..
  ```
[INDENT]grub rescue > ls
(hd0) (hd0,msdos5) (hd0,msdos3) (hd0,msdos2) (hd0,msdos1) (hd1) (hd1,msdos1)
grub rescue > ls (hd0,msdos1) # try to recognize which partition is this
grub rescue > ls (hd0,msdos2) # let's assume this is the linux partition *
grub rescue > set root=(hd0,msdos2)
grub rescue > set prefix=(hd0,msdos2)/boot/grub # or wherever grub is installed
grub rescue > insmod normal # if this produced an error, reset root and prefix to something else ..
grub rescue > normal
[/INDENT]

```
I found and used this some time ago, can't recall where, but it has been working for me ever since.  Good luck!
(The example shows a 4-partition setup)

---

