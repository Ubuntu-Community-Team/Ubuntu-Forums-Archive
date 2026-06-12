---
title: "Dual Boot and Bootloader &amp; not network"
date: 2008-08-25
forum: Installation &amp; Upgrades
---

### Post by reggie777 on 2008-08-25
I'm very new to Ubuntu, here are my issues;
1) I have a dual boot situation after installing Ubuntu, I restart and the screen is there to choose what os. However, When I reboot the bootloader does not start and I am unabel to sign in.

2) I assumed that when I installed the os that there would be software on the os that would automatically detect my home network.
What do I do, since I have no internet access?

---

### Post by manishtech on 2008-08-26
> 1) I have a dual boot situation after installing Ubuntu, I restart and the screen is there to choose what os. However, When I reboot the bootloader does not start and I am unabel to sign in.
When you reboot what comes on the screen?

> 
2) I assumed that when I installed the os that there would be software on the os that would automatically detect my home network.
What do I do, since I have no internet access?
What network card you have? If you dont know, just open the terminal  (Application>Accessories>Terminal) and type in this command and tell me the output

```
lspci | grep -i network
```

---

