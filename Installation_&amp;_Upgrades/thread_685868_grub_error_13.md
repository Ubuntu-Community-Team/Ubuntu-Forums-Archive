---
title: "grub error 13"
date: 2008-02-02
forum: Installation &amp; Upgrades
---

### Post by jay3712 on 2008-02-02
I'm trying to install XP only because I need it for the windows mobile support. So, I followed [this tutorial]("http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp") but I get error 13 "invalid or unsupported executable format" when I try to boot into windows from grub. 
What info do I need to post up for you guys? 
Here is my /boot/grub/menu.lst:
```
title          Windows XP
root         (hd0,1)
makeactive
chainloader +1
```
thanks guys
Jason

---

### Post by Pumalite on 2008-02-02
[http://users.bigpond.net.au/hermanzone/p15.htm#13](http://users.bigpond.net.au/hermanzone/p15.htm#13)

---

### Post by jay3712 on 2008-02-02
Awesome I figured it out. Thanks for your help puma.

---

