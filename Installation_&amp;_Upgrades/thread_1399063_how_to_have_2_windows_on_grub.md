---
title: "how to have 2 windows on grub"
date: 2010-02-05
forum: Installation &amp; Upgrades
---

### Post by angelo05328390 on 2010-02-05
my laptop got broken... so i extracted my hard drive to use as an external ...

the problem is the computer i am using has windows xp on it... and my external has also a windows xp, ubuntu and kubuntu...

i need to have the xp from my external running because i use it for .net development...
any idea how i can  have 2 windows  on grub  with root (h0,0) and (h1,0)...
my ubuntu is (h1,6) and kubuntu is (h1,3). 



thanks.....  any reply is highly appreciated...

---

### Post by darkod on 2010-02-05
If you are running grub1 just make another win xp entry in /boot/grub/menu.lst

If you are running grub2, executing sudo update-grub should detect it.

---

### Post by Leppie on 2010-02-05
if the external drive wasn't attached to the system when grub2 was installed, you may have to recreate the device map before running update-grub:
```
sudo grub-mkdevicemap
sudo update-grub
```

---

