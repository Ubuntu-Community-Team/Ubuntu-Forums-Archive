---
title: "help finding kernal no."
date: 2005-11-11
forum: Installation &amp; Upgrades
---

### Post by amwil1024 on 2005-11-11
Ok, making small progress. So, it seems my modem is an HCF - Conexant that requires a new driver. Which can be purchase online, but, I need to find the kernal version? in order to download the best linux driver. They said to type in; uname -r, which doesn't help me at all! I need guidance to do this!

Remember that I'm running live cd until I can prove that all will work well with ubuntu, at which time I will ersae my harddrive, reload win 98 with minimal software and then installed ubuntu as the second os on my HD. 

Regards,

---

### Post by Buffalo Soldier on 2005-11-11
[QUOTE=amwil1024]Ok, making small progress. So, it seems my modem is an HCF - Conexant that requires a new driver. Which can be purchase online, but, I need to find the kernal version? in order to download the best linux driver. They said to type in; uname -r, which doesn't help me at all! I need guidance to do this!

Remember that I'm running live cd until I can prove that all will work well with ubuntu, at which time I will ersae my harddrive, reload win 98 with minimal software and then installed ubuntu as the second os on my HD. 

Regards,[/QUOTE]I'm not sure if the menu layout in the LiveCD is the same, I guess it's supposed to be the same. So here's what you should do:[list]
[*] Start a terminal: Applications - > Accessories -> Terminal.
[*] Type in the command: **uname -r**. Example: ```
firdaus@ubuntu:~$ **uname -r**
```
[*] It will then display your kernel version. Example: ```
firdaus@ubuntu:~$ **uname -r**
[color=red]2.6.12-9-686[/color]
firdaus@ubuntu:~$
```
[/list]

---

