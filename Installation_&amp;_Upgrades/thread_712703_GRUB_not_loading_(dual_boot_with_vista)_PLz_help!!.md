---
title: "GRUB not loading (dual boot with vista) PLz help!!"
date: 2008-03-02
forum: Installation &amp; Upgrades
---

### Post by tilldawn on 2008-03-02
guys i'm here again ...b4 anything else i want to say tnx to all people helping me to install ubutu on my pc...i already install ubuntu 7.1 gusty and its seems that i finished it correctly but one thing happened when i restart my pc and go to vista and install easy BCD and add liux to mbr when i restart it again i found 2 system in my MBR 1st is vista and 2nd is UBUNTU but when i choose UBUNTU nothig happen and its failed on loading ubuntu can u tell me what exactly the problem is.....the vista is quite normal upon booting only ubuntu fails plzzzz help me i really appreciate you people....ciao more power ubuntu users!!

---

### Post by confused57 on 2008-03-02
> **tilldawn said:**
> guys i'm here again ...b4 anything else i want to say tnx to all people helping me to install ubutu on my pc...i already install ubuntu 7.1 gusty and its seems that i finished it correctly but one thing happened when i restart my pc and go to vista and install easy BCD and add liux to mbr when i restart it again i found 2 system in my MBR 1st is vista and 2nd is UBUNTU but when i choose UBUNTU nothig happen and its failed on loading ubuntu can u tell me what exactly the problem is.....the vista is quite normal upon booting only ubuntu fails plzzzz help me i really appreciate you people....ciao more power ubuntu users!!
You could try installing grub to the Ubuntu root partition, using the Ubuntu live cd:
```
sudo grub
find /boot/grub/stage1
```
this should return something like "root (hd0,1)", then enter:
```
root (hd0,1)
setup (hd0,1)
quit
```

Of course, replace the "root (hd0,1)" with the results of "find /boot/grub/stage1...

---

