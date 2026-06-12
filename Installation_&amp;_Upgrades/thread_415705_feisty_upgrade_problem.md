---
title: "feisty upgrade problem"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by creamcheeze77 on 2007-04-20
after upgrading from edgy to feisty fawn, i tried to reboot the computer.  on the "grub loading" screen, i got an error message that i'd never had before "PCI: failed to allocate memory resources...", then the screen goes blank.  i thought maybe it was a graphics problem, but i really don't know, does anyone have a solution? i have a nvidia 7800 card and i think i may have replaced the xorg file when i upgraded, but since i can't get into the file with no graphics i really don't know what to do.

---

### Post by anachreon_ on 2007-04-20
Ok so you can't even see a list of operating systems to load?  No GRUB menu at all?

---

### Post by creamcheeze77 on 2007-04-20
no, u get the grub menu.  but then, where the screen would normally change to the ubuntu load screen, i just get blank space.  i tried changing grubs and the load screen froze on the first bar.

---

### Post by anachreon_ on 2007-04-20
creamcheeze, can you explain what you mean by "i tried changing grubs"?  GRUB is the boot loader that allows you to select which operating system to load.

When you select an ubuntu linux kernel to load, and you get a "blank" screen, do you get any sort of prompt by typing ctrl+alt+F1?  Or is it just totally frozen?

Can you select a previous version of the kernel from GRUB and load successfully?

---

### Post by creamcheeze77 on 2007-04-21
if i let the computer load normally, it hangs on the Ubuntu load screen.  pressing ctrl-alt-F1 gives me an indefinate "loading, please wait."  if i change to an older version of the kernel, it loads with no error but then X fails, and if i go into the X error output it says the nvidia kernel (which is the most recent one i could get) and the version of X i'm using don't match.

---

### Post by jiazou on 2007-04-23
I have the same problem, except that it just hangs after it says GRUB loading. I get a blank page, and ctl+alt+f1 doesn't help either... Any ideas?
Thanks,

---

