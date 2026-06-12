---
title: "downgrading kernel or setting grub default kernel"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by chamstar on 2008-06-24
I recently allowed update manager to install a new kernel which has broken X, ie. I can only get to command prompt on boot. I have a dual screen setup which took me a fair while to get working. 

If I select the old kernel from GRUB everything is okay. Is there any way I can downgrade the kernel back to what it used to be? [Or maybe change the default kernel in GRUB?]

The same thing happened when I upgraded to Hardy, I'm currently on Feisty. When I have time I'll upgrade and get the dual monitors working again but for now I'm happy to stick to Feisty since it works well.

Many thanks, Cham.

---

### Post by Pumalite on 2008-06-24
Maybe all you need with your new kernel is reinstalling your video driver

---

### Post by chamstar on 2008-06-24
Maybe, but I tried for a couple of days to get nvida working with Hardy kernel a few weeks back. I don't have time at the moment to 'play' with it. I use Ubuntu for everyday work as a Ruby programmer. When I get more time I'll get it working, for now I just need to boot to a working kernel :) Cheers.

---

### Post by Pumalite on 2008-06-24
All you have to do is choose the kernel you want to boot at the Grub menu. Or edit menu.lst and change default=0 for the corresponding number keeping in mind that Grub starts to count from 0.

---

### Post by sdennie on 2008-06-24
An easy way to set the default is to edit /boot/grub/menu.lst:

```

gksudo gedit /boot/grub/menu.lst

```

Look for the line towards the top that says "default    0" and change it to "default    saved".  Then find the line towards the bottom of the huge comment block that says: "# savedefault=false" and change "false" to "true".  Save the file and then run:

```

sudo update-grub

```

The next time you restart, whatever kernel you choose will be become the default for future restarts.

---

### Post by chamstar on 2008-06-26
Cheers Vor, I just needed to change default to saved.

---

### Post by directcharitycontribution on 2008-11-09
then how do user set absolute not relative default kernel?

---

### Post by sdennie on 2008-11-09
Really, the instructions above are the equivalent of "absolute".  Setting default to a number is like setting it to "relative".  When it's at "saved" you will boot into the same kernel until you explicitly choose a different kernel in grub.

---

### Post by directcharitycontribution on 2008-11-09
cool. that sounds nice simple. then what does happen with those new kernel?

---

### Post by d_singo69 on 2008-11-12
Thanks for the info Vor It solved the problem of a kernel hiccup

---

### Post by directcharitycontribution on 2008-11-12
[http://ubuntuforums.org/showthread.php?t=215203](http://ubuntuforums.org/showthread.php?t=215203)

---

### Post by pkkid on 2010-02-14
This helped solve my problem as well with a recent kernel for the Macbook Pro.

I found that I could set "GRUB_DEFAULT=saved" in the file /etc/default/grub.  This means that each time grub loads, the default selected option will be whatever you choose last.  Don't forget to run update-grub after you make the change.

---

