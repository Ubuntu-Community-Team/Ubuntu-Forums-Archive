---
title: "I can not to mount external hard drive"
date: 2017-10-23
forum: Installation &amp; Upgrades
---

### Post by ledisciple on 2017-10-23
Hello everybody

Sorry for my English

I have upgraded Xubuntu 17.04 to 17.10

At beging, I have created a folder in [COLOR=#000000][FONT=Arial]/media/francois@dd_livebox
[/FONT][/COLOR]After,  in /etc/fstab I have writed this line :

```
[COLOR=#000000][FONT=Arial]//192.168.1.1/dd_livebox/francois /media/francois@dd_livebox cifs _netdev,rw,users,iocharset=utf8,uid=1000,sec=none,file_mode=0777,dir_mode=0777 0 0[/FONT][/COLOR]
```

This device was automatically mounted, but not now.

Ii display this message : 
```
Impossible to mount "francois@dd_livebox
mount : /media/francois@dd_livebox: mount(2) system call failed: the target host is down or down."
```

In grub > Grub avanced option for Ubuntu
Linux 4.13.0.16 => Mount Hard disk runs
Linux 4.10.0.37 => Mount Hard disk does not run

My hard disk runs well when i plug it directly in my PC.

Can i automatically launch my ordinateur with Linux 4.10.0.37?

Can you help me?

Thanks  a lot

---

### Post by ledisciple on 2017-10-26
[This post]("https://forum.ubuntu-fr.org/viewtopic.php?pid=21813544#p21813544") provides me a [COLOR=#242424][FONT=Arial]work[/FONT][/COLOR][COLOR=#181818][FONT=Arial]aro[/FONT][/COLOR][COLOR=#0C0C0C][FONT=Arial]und[/FONT][/COLOR]

---

