---
title: "update process died; now won't load OS"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by wizarddrummer on 2010-03-16
Hi,

I started the update process in my new Ubuntu Studio install.

My understanding of the update process is:

1) Downloads all of the update files (in my case 214)
2) It performs the necessary installation of these files.

My machine locked up at the 70% done part during step 2.

Now, when I try to boot/load the OS it stalls at the splash screen.

I am not even sure I can get to the recover part from Grub yet, but if I can...

Is there a command that can start the update process without having to download the data again?


Thanks,

---

### Post by ManyuX95 on 2010-03-16
Mmm well If you have time, you can use Parted Magician or a soft like that to backup your important files, then install again. Hope you don't have to be in that situation but i think it would be better, and I hope that helped you :)

---

### Post by uRock on 2010-03-16
When you fisrt turn it on and hit esc for the grub menu(if not dual booting) select the topmost kernel with recovery mode and when it comes to the recovery menu, choose the fix broken packages selection.

---

### Post by wizarddrummer on 2010-03-17
> **iRock said:**
> When you fisrt turn it on and hit esc for the grub menu(if not dual booting) select the topmost kernel with recovery mode and when it comes to the recovery menu, choose the fix broken packages selection.

Thanks to all who replied and also to those individuals that wanted to but are in the same situation that I am; kind of new. :)

After selecting the fix broken packages do i enter  this text?
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

I am a little unclear.

---

### Post by uRock on 2010-03-17
> **wizarddrummer said:**
> Thanks to all who replied and also to those individuals that wanted to but are in the same situation that I am; kind of new. :)

After selecting the fix broken packages do i enter  this text?
gconftool-2 --set /apps/metacity/general/button_layout --type string menu:minimize,maximize,close

I am a little unclear.

Sorry about that. The text below the little line in my posts is my signature. It is for those who have installed Lucid testing and want to put the window buttons back on the right.

When you go into recovery mode, then chose the "fix broken packages" the machine will do all the work.

---

### Post by wizarddrummer on 2010-03-26
> **iRock said:**
> Sorry about that. The text below the little line in my posts is my signature. It is for those who have installed Lucid testing and want to put the window buttons back on the right.

When you go into recovery mode, then chose the "fix broken packages" the machine will do all the work.

thanks for the reply, sorry it took so long to thank you.

---

