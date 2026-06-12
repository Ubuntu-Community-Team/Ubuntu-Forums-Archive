---
title: "error 17"
date: 2010-02-14
forum: Installation &amp; Upgrades
---

### Post by lanark95 on 2010-02-14
Have upgraded ubuntu, using grub for dual boot ..Vista..when I ask for ubuntu get error 17...I edit root to (hd0,0) and Ubuntu will boot...but the next time I start Ubuntu, I get same error and have to change boot to (hd0,0). It always comes up as (hd1,0)

---

### Post by oldfred on 2010-02-14
What versions? It sounds like hard drives got reversed somehow, but the way to update grub varies depending on grub legacy or grub2 with Karmic.

Grub version:
```
grub-install -v
lsb_release -a
dpkg -l 'grub*'
```

---

### Post by lanark95 on 2010-02-15
Thanks for the reply. How do I determine the grub version?
Why is it that when I edit the grub to change (hd1,hd0) back to (hd0,hd0) the changes do not stay and each time I boot I have to edit it manually to get UBUNTU to load?

---

### Post by oldfred on 2010-02-15
Copy and paste each line I had in the code box into a terminal and press enter. Each gives slightly different info.

---

### Post by lanark95 on 2010-02-16
grub ver: 0.97
lab release: 8.04   Hardy
 dpkg -l "grub*" 
Desired=unknown/install/remove/purge/hold
status=not/installed/config-f/unpacked/failed-cfg/half-inst/t-await/t-pend
/err?=(none)/hold/reinst-required/x=both-problems (status,Err: uppercase=bad
 grub                 0.97-29ubuntu2 GRand Unified Bootloader
un grub-doc           none
un grub2              none

---

### Post by oldfred on 2010-02-17
Follow the instructions here for reinstalling grub.

How to restore the Ubuntu grub bootloader (9.04 and older)

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by meierfra. on 2010-02-17
Edit: Ignore this post.  See post 9.

> Follow the instructions here for reinstalling grub.
Grub is installed correctly. So reinstallung grub will not help


> Why is it that when I edit the grub to change (hd1,hd0) back to (hd0,hd0) the changes do not stay and each time I boot I have to edit it manually to get UBUNTU to load?
Editing  grub at the Grub menu  is only  a temporary change.
You need edit "menu.lst"


```
gksudo gedit /boot/grub/menu.lst
```

Look for your Vista item: It is at the end of the file and  looks  something like

title Windows Vista
root (hd1,0)
makeactive
chainloader +1
savedefault


change it to


title Windows Vista
root (hd0,0)
chainloader +1

 and save the file. Just use those three lines. You don't need any of the others.

---

### Post by oldfred on 2010-02-17
Is it Vista that will not boot or Ubuntu?

Your original post:
I edit root to (hd0,0) and Ubuntu will boot...but the next time I start Ubuntu, I get same error

If it is Vista Meierfra is correct.

---

### Post by meierfra. on 2010-02-17
> I edit root to (hd0,0) and Ubuntu will boot
Oops. Overlooked that.   (Just assumed it was Vista, since Ubuntu should be using UUID's.)

So do this instead:

```
gksudo gedit /boot/grub/menu.lst
```

Look for the line

# groot=(hd1,0)

Change it to

# groot=(hd0,0)


Save the file and then

```
sudo update-grub
```


Thanks to olfred for catching my mistake.

---

### Post by lanark95 on 2010-02-20
Thank You!..that worked for me....all is well in Lanark

---

### Post by meierfra. on 2010-02-20
> .that worked for me..
Great. Have fun with Vista and Ubuntu

---

