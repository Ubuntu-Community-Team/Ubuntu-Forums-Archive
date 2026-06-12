---
title: "Lucid and Clear (menu.lst)"
date: 2010-07-01
forum: Installation &amp; Upgrades
---

### Post by shnurui on 2010-07-01
Ok, completely fresh install of lucid (64bit) on my asus deluxe msi with dual audio cards, dual hds, dual cpu(3.0 amd2) and a whopping 3.5 ddr2...

Everything works wonderfully, Except:

The old method of making sure windows booted first... Gone with Sarah on that plane.

Is that Lst, 1st, Ist or what on /boot/grub/menu.xxx?

Since this is a clean and good install, should I be worried that it's completely blank when I edit it?

Oh, ps, knowing about 32x compatibility software would of been nice.

---

### Post by varunendra on 2010-07-01
Earlier it was menu.lst (small "L"), but not anymore. After Grub being replaced by Grub2 since Ubuntu 9.10 onwards, it is now /boot/grub/grub.cfg file that controls the menu.

However, you should not try to edit that since it is automatically generated complex script.
If you want to change the default choice or timeout, the correct way (for Grub2) is to edit the /etc/default/grub file instead:
```
sudo gedit /etc/default/grub
```Look up for the line that says > GRUB_DEFAULT=0Replace 0 with the number of your default choice. [Hint:]> 

[LIST]
[*]first item in the grub menu=0
[*]second .......................... =1
[*]third ............................. =2
[*]............... (so on)....
[/LIST]
Save and close the file. Now run the following command:
```
sudo update-grub
```

Now reboot to see the effect of the change.

Hopefully, Sarah would be glad to know that you figured it out all by yourself! :D


And yeah, the blank file you mentioned, it should actually be a new one you might be creating- useless for grub2 :( but definitely not a reason to worry.

Sorry for not being helpful about 32x compatibility issue.

---

### Post by dino99 on 2010-07-01
startup-manager can do that for you

---

### Post by varunendra on 2010-07-01
> **dino99 said:**
> startup-manager can do that for you

++1
(oops! I missed it!)

---

