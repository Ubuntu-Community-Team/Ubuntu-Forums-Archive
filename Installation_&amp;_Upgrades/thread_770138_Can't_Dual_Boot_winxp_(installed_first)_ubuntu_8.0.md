---
title: "Can't Dual Boot winxp (installed first) ubuntu 8.04"
date: 2008-04-27
forum: Installation &amp; Upgrades
---

### Post by benny999 on 2008-04-27
hello i just installed ubuntu the newest version and i had xp preinstalled. I resized my hard drive to have 100gb  partition free area and used the guided use the most free space option, when setting hard drive and tryed a couple of other ways all installed but wouldn't come up with the dual boot screen.

ps i had no errors when installing



Thanks for your help

---

### Post by ajmorris on 2008-04-27
hi there,
we are going to re-install your bootloader, grub.

open up a terminal and type in the following commands:
    ```

     1) sudo grub 
```
```

     2) find /boot/grub/stage1 
```

```
      3) root (hd#,#) Where #,# are the numbers found in step 2) 
```
```

     4) setup (hd0) 
```
```
      5) quit 
```
Then, when you reboot, XP should be an option in the boot menu. If it is not, we can add it :)

AJ

---

### Post by benny999 on 2008-04-27
oops should have said this windows xp was installed first so it boots in xp

but thanks for the help much appreciated

---

### Post by ajmorris on 2008-04-27
ah, in that case, do the same commands i outlined, but in a linux live cd :) (it doesnt have to be an ubuntu live cd, it can be any linux live cd)

AJ

---

### Post by benny999 on 2008-04-27
ok cool thanks got it working now i was wondering if i could move xp to the top of the list and have like a 20 second count down and it auto runs the os up the top

can you do that?

thank you very much oh im running my fresh ubuntu right now :)

---

### Post by thecheatah on 2008-04-27
I dont know if its a good idea to move it to the top of the list, as that list is automatically generated. (it might be smart enough to work with it), but what I do is modify the default choice.

File: /boot/grub/menu.lst

Find line:
default 0 
that basically says which item to select, the 0th being the first item in the list. So if you have 6 entries in there (including the other os thing which you cant select) you should set it to 5.

Find line:
timeout 10
This basically sets in second how long to wait before automatically making a selection.

---

