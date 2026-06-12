---
title: "Add entry to menu.lst automatically?"
date: 2010-03-09
forum: Installation &amp; Upgrades
---

### Post by vicG on 2010-03-09
Hi all

Update Mgr got me a bunch of updates today, including a kernel (2.6.31-20).  I was doing something else, and when it prompted me to do something with menu.lst, I accidentally accepted the default, which I think was to keep menu.lst unchanged.

As a result, the new kernel was installed but not added to menu.lst, so I guess I can't boot to it.

Is there a way to tell my computer, "I'm sorry, please make the entries into menu.lst automatically" :D

I guess I could put the entries in manually, but as a beginner, I'm pretty scared to be messing with that file...perhaps if someone has a link to an exceptionally understandable explanation...

Thanks for any tips!

---

### Post by uRock on 2010-03-09
If you can see it in Synaptic as being there, it should work. If it doesn't work you could try reinstalling the kernel.

---

### Post by jocko on 2010-03-10
There are a couple of things you can try:
1. Run this in a terminal to update the old menu.lst:
```
sudo update-grub
```
Then check menu.lst to see if the new kernel is listed.
If that didn't work:
2. Run this in a terminal to generate a completely new menu.lst:
```
sudo mv /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo update-grub
```Check the new menu.lst to see if all kernels are listed. Reboot.

---

### Post by kansasnoob on 2010-03-10
If that doesn't work post the output of:

```
grub-install -v && aptitude show grub|head -4 && aptitude show grub-pc|head -4 && aptitude show grub-common|head -4
```

And:

```
ls /boot/grub
```

And please use code tags as I did by clicking on the # above ;)

---

### Post by vicG on 2010-03-10
Thanks, gents -- update grub didn't make any changes to menu.lst for some reason, but following the backup plan and moving it / generating a new one worked perfectly.

Much appreciated!

---

