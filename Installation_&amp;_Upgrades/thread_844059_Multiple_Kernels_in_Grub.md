---
title: "Multiple Kernels in Grub"
date: 2008-06-29
forum: Installation &amp; Upgrades
---

### Post by jskandhari on 2008-06-29
:( I get all the updates my kernel also updates but the problem is my previous kernels are also present and ultimately i have appx 13 linux ubuntu options

please solution ne1 coz i am on a cleaniness drive and am having lots of time for next few weeks

---

### Post by Partyboi2 on 2008-06-29
You can remove the kernels you know longer want by opening up Synaptic Package Manager and doing a search for
linux-image
then remove the ones you know longer need.
I would also suggest leaving the last version before the current one you are using.

You can also change how many kernels are displayed at the grub menu by editing this part of your /boot/grub/menu.lst
> ## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=2
More info [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall")

---

### Post by firebone on 2009-07-31
> **Partyboi2 said:**
> You can remove the kernels you know longer want by opening up Synaptic Package Manager and doing a search for
linux-image
then remove the ones you know longer need.
I would also suggest leaving the last version before the current one you are using.

You can also change how many kernels are displayed at the grub menu by editing this part of your /boot/grub/menu.lst

More info [[COLOR=Blue]here[/COLOR]]("http://users.bigpond.net.au/hermanzone/p15.htm#_howmanyall")

Can I just remove or do I need to choose remove all from the package manager?

---

### Post by Partyboi2 on 2009-07-31
> **firebone said:**
> Can I just remove or do I need to choose remove all from the package manager?
Just use the remove option. :)

---

### Post by drs305 on 2009-07-31
There is also a gui menu editor for grub called StartUp-Manager. It doesn't physically remove the kernels but you can decide how many you see, as well as being able to tweak many other aspects of the boot menu. All without manually editing the grub menu.lst file.

The post also has details of how to manually edit the file, and how to remove old kernels, if you prefer to do that.

For details, click the "SUM" link in my signature line.

---

### Post by firebone on 2009-08-01
Thanks for the quick answers.

---

