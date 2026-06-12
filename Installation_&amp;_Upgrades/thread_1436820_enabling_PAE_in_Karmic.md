---
title: "enabling PAE in Karmic"
date: 2010-03-23
forum: Installation &amp; Upgrades
---

### Post by 0v3rfl0w on 2010-03-23
Hello everyone!
Ubuntu rocks but I am having trouble enabling PAE. 

I want to do it to have my full 4Gb RAM recognized by my 32bit OS. At the moment System Monitor only recognizes 3.2Gb and the command "free -m" shows the same value.

I followed these instructions but they don't seem to work: [https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

Can someone help? If you need more info, I'll provide it.
Thanks in advance!

0v3r

PS: The point is to really understand how to achieve this and not to start a debate "32bit vs 64bit OS choice"

---

### Post by 0v3rfl0w on 2010-03-23
Just got to add that it DID work in the sense that the new kernel is installed.
What didn't work is that the system still sees 3.2GiB..

---

### Post by coffeecat on 2010-03-23
Did you boot into the PAE kernel? It should be the default option in the grub menu, but double-check to see which is. Your old kernel is still installed and you may be booting into this.

To see which you are running, in a terminal:

```
uname -r
```

---

### Post by 0v3rfl0w on 2010-03-23
Thanks coffeecat but that was my first thought and the first thing i checked..
I am using the right kernel but the problem remains..

---

