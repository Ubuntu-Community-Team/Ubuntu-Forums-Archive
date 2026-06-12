---
title: "GRUB Menu not showing up - Help! :("
date: 2007-12-11
forum: Installation &amp; Upgrades
---

### Post by lauzz on 2007-12-11
Hi There,

I just installed Ubuntu (now have XP/Ubuntu dual booting laptop).

The first time i rebooted the computer - the menu appeared at the start asking me to choose an operating system. I chose XP and ever since then when I restart the computer, XP loads by default.

How can I fix this? I can't get into Linux at all however i know it's there as my drive is pationed into C: and D: (120GB all up). During the installing partioned C:/ into two lots of 30GB and D into 60GB. When i look at the C:/ properties it shows only 30GB of space, so Linux i'm assuming is definately there (taking up the other 30GB)

how do I get Ubuntu to load (or the grub menu [i think thats what it's called?])

---

### Post by PmDematagoda on 2007-12-11
You can try using [Super GRUB]("http://supergrub.forjamari.linex.org/?section=download") to repair GRUB.

---

### Post by Schalken on 2007-12-11
So you have how many drives with how many partitions?

---

### Post by lauzz on 2007-12-11
Just one HDD partioned into C:/ and a D:/ (thats what shows up in "My Computer") but C:\ then has 2 partitions one with xp and one with linux (i'm assuming as C:/ is only showing 30GB when its supposed to be 60GB)

---

### Post by Schalken on 2007-12-11
I didn't realise a partition ("C:\") could have multiple partitions *inside* it. :?

What I recommend you do is boot into the Ubuntu live CD, go to System > Administration > Gnome Partition Editor, select your hard drive if it isn't selected all ready in the top right of the window, and take a screenshot. From there we will be able to see which partition is Ubuntu and therefore what device to pass to grub-install to reinstall the bootloader.

---

### Post by lauzz on 2007-12-11
Ok here is the screenshot.

I'm totally lost - with windows I can figure out anything, but come linux, I have NO clue!

---

### Post by Schalken on 2007-12-11
the command ```
grub-install /dev/hda
``` (install grub on your hard drive) from the live cd may be enough to fix your problem.
[B]
OR[/B]

because except that it does work, I personally don't understand *how* the "grub-install" command works, you can also try the following from the live cd:

```
sudo grub
``` which will start the grub command line, followed by (in the grub command line) ```
find /boot/grub/stage1
``` this will find the partition which the bootloader configuration (which is part of Ubuntu) is on, which I think should be (hd0,1) according to the screenshot, but if it says something else use what it says instead. ```
root (hd0,1)
``` again, if the "find" command said something other than (hd0,1), use that instead. then ```
setup (hd0)
``` will setup grub on your hard drive. use ```
quit
``` to get out of the grub command line, then just close the terminal.

what i said above was pretty much copied from the GRUB manual: [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

which also has info on the grub-install command: [http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively](http://www.gnu.org/software/grub/manual/grub.html#Installing-GRUB-natively)

tell me what happened :P

---

### Post by lauzz on 2007-12-11
Well that solved it - the grub menu now shows up and asks me which OS I want to use HOWEVER now when I chose linux it comes up with "Error 17" can't mount ....." so now im even more lost!

I do appreciate your help - especially to use newbies!

---

### Post by spai on 2007-12-11
Will this help?
[http://ubuntuforums.org/archive/index.php/t-135348.html](http://ubuntuforums.org/archive/index.php/t-135348.html)

---

