---
title: "Scrolling is weird"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by scotty32 on 2006-10-28
ok, not sure where to put this (so if need be, please move)

but i had a failed upgrade to edgy from dapper - so my impaitentness took over and i did a reinstall (i still use WinXP as primary till i get ubuntu set up workin)

am really likin edgy (got my PocketPC to sync with evo at last :mrgreen: )

but one thing thats doin my head in is - when ever i scroll in a webpage (or scroll in a folder, but not as bad) it doesnt flow nicely, it kinda does a "wipe" affect, so reading posts on here is slow and painfull.

am not sure what would course this - so hense my post - as i have an ATI Radeon card, would it be i need to install the driver? or do i have to fiddle with the x.org config file?

am a newbie, so if fairly comlicated, could you give full instructions - or link to a howto ;) 

thanks - bye

---

### Post by tribaal on 2006-10-30
Seconded.
I'm experiencing the same problem. Any help would be greatly appreciated.

- trib'

---

### Post by scotty32 on 2006-10-30
if you have an ATI Radeon (8500 atlest) dont install the drivers.

i got zero display.

and my xorg.conf file says "Generic Video Card" forgot the driver vesa is it?

---

### Post by mjezell on 2006-10-30
I'm having the same problem and no luck in finding an answer...will continue search

---

### Post by alx23 on 2006-10-30
I had the same problem, and solved it by reconfiguring xorg:

```
sudo dpkg-reconfigure xserver-xorg
```

After going through this (and generally accepting the defaults), everything worked properly.

-alx

---

