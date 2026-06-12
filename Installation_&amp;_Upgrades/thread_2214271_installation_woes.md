---
title: "installation woes"
date: 2014-03-31
forum: Installation &amp; Upgrades
---

### Post by night116 on 2014-03-31
I just re-installed ubuntu 13.10 on my main desktop, killing the duel boot windows8, now in my main Identity anything I have installed such as terminator or even firefox, will only work if I use gksudo or sudo.
But the other identities like my wifes one work just fine.
what have I done wrong and how do I fix this mess.

---

### Post by steeldriver on 2014-03-31
It sounds like the ownership of your home directory went awry - can you post from a terminal

```

id

ls -ld $HOME

```

---

### Post by night116 on 2014-03-31
night@night:~$ id
uid=1000(night) gid=1000(night) groups=1000(night),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),112(lpadmin),124(sambashare)
night@night:~$ 
night@night:~$ ls -ld $HOME
drwxr-xr-x 28 night night 4096 Mar 27 13:42 /home/night
night@night:~$

---

### Post by night116 on 2014-04-02
I just re-installed ubuntu 13.10 on my main desktop, killing the duel boot windows8, now in my main Identity anything I have installed such as terminator or even firefox, will only work if I use gksudo or sudo.
But the other identities like my wifes one work just fine.
what have I done wrong and how do I fix this mess. 

night@night:~$ id
uid=1000(night) gid=1000(night) groups=1000(night),4(adm),24(cdrom),27(sudo),30(di p),46(plugdev),112(lpadmin),124(sambashare)
night@night:~$
night@night:~$ ls -ld $HOME
drwxr-xr-x 28 night night 4096 Mar 27 13:42 /home/night
night@night:~$

---

### Post by QIII on 2014-04-02
Threads merged.

Please do not create duplicate threads.  It causes confusion and dilutes the community's effort to help.

---

### Post by mastablasta on 2014-04-02
> **night116 said:**
>  my main Identity anything I have installed such as terminator or even firefox, will only work if I use gksudo or sudo.
.


this could happen if you used sudo for graphical apps i believe.

---

### Post by steeldriver on 2014-04-02
^^^ yup check that the profile files for those apps didn't get owned by root. If you don't want to trawl through your dot files manually you could run something like

```
find ~ \( ! -uid $(id -u) -o ! -gid $(id -g) \) -ls
```

---

### Post by night116 on 2014-04-02
yep shows up as being owned by root.
so how to fix it, i did try
sudo chown -R night:night ~/.mozilla
but that didnt work

---

### Post by night116 on 2014-04-02
dont worry, I fixed it from another post that was similar using the above but on each DIR manually and it works now.
thanks for all your help every-one.

---

### Post by su:bhatta on 2014-04-02
If all your issues are solved, Please mark the thread as Solved using Thread Tools on the top right of the page.

---

