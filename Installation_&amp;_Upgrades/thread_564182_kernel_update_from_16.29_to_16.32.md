---
title: "kernel update from 16.29 to 16.32"
date: 2007-09-30
forum: Installation &amp; Upgrades
---

### Post by lsutiger on 2007-09-30
I have heard of some bad stories of this update. Before I consider installing it, I would like some input from anyone who has installed this update. 
I have a few concerns. They special things I am running on this box:
Restricted drivers for ATI video
native linux driver for broadcom wireless
Beryl core 0.2.0~0beryl1 (though I would LOVE to run compiz, but thats another post)

My computer is listed in my signature
Thanx for any input!

---

### Post by pay on 2007-09-30
If you update the linux kernel you'll have to reinstall all drivers that were installed as modules against it, i.e. ati fglrx driver.

---

### Post by lsutiger on 2007-09-30
Well, all I did for that was enable it through the restricted drivers menu. Will it still be available? If everything goes haywire, is there a way to revert?

---

### Post by pay on 2007-09-30
Here's a guide on howto install the latest ati driver [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)
(you might want to use 8.40 as 8.41 is only for hd2xxx cards)

---

