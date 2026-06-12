---
title: "Post Installation Qeury"
date: 2010-03-29
forum: Installation &amp; Upgrades
---

### Post by bingo23 on 2010-03-29
Have installed Ubuntu 9.10 via the wubi installer - when I switch the Computer on, it gives me the option to then either load Windows 7 or Ubuntu - no problems.
 
I am then presented with a further screen with 3 Options on-:
 
1. Ubuntu, Linux, 2.6.32-14 - generic
 
2. Ubuntu, Linux, 2.6.32-14 (recovery mode)
 
3. Windows 7 (loader) (on dav/sdb1)
 
I assume that having already opted for Ubutu from the forst screen, I then select No 1 above - what are items 2 and 3 please.

---

### Post by tom4everitt on 2010-03-29
Any reason they would not be what they sound like? 

Number 1 is normal ubuntu. Number 2 is ubuntu in recovery mode, that you need to use only if something is so wrong you can not do a normal boot. Number 3 is Windows. 

Just try the different options if you're curious! :)

---

### Post by bingo23 on 2010-03-29
I was merely curious, that havnbg already decided to enter Ubuntu via the very first screen (Windows or Ubuntu), you were then presented with a further option(s).

---

### Post by tom4everitt on 2010-03-30
Oh, I see. I'm not entirely sure about how wubi works, but I think its the grub2 menu you're presented the second time.

If you want you can auto-hide that menu (and get it back by holding down shift when its supposed to come), by:


1. Open a terminal (Applications-Accessories->Terminal)
2. Open the file /etc/default/grub with with root permission, i.e type:
sudo gedit /etc/default/grub 
3. uncomment (remove the '#') or add the line: GRUB_HIDDEN_TIMEOUT=0
4. Save.
5. Run (in the terminal): sudo update-grub

Now that menu should only be presented in case you hold down shift.


If you want it back, just remove the line you added, and run sudo update-grub again.

---

