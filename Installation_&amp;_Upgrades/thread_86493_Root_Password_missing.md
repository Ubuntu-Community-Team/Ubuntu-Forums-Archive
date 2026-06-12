---
title: "Root Password missing??"
date: 2005-11-05
forum: Installation &amp; Upgrades
---

### Post by flash2k5 on 2005-11-05
Well the problem goes like this :

I installed Ubuntu Linux 5.04 AMD64 version (on my dual processor Opteron based Server having nF4 professional mobo, 2GB DDR400 (ECC with Reg.) RAM and 4*200GB SATAII Hdds in Raid 1 & I have assembled it:D )

Now for the problem :
Installation went smoothly with no errors.

I don't remember it the installation asked for roo password (or may be it asked but what I entered I don't remember)
Now can anybody tell me what would be the default password of root (If the installation doesn't asks) or How to retrive the root password on Ubuntu (If the installation had asked) ??
or In other words, I need my root password back:( 

Plz I need help. I can't keep my server offline for long time:(

---

### Post by Xian on 2005-11-05
Read the [Wiki RootSudo Guide](https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges)

---

### Post by linbetwin on 2005-11-05
root password is your user password, the one you use to log in.

---

### Post by HJThis on 2005-11-05
Hi,To all

You know at first this seems like an odd way of doing things
but in the long run you will see the sense in the way
Ubuntu has it setup this way.

Best of luck

---

### Post by HJThis on 2005-11-05
Hi,Flash2k5

Here is more link you should have a look at you may need this
it has a tonn of info great stuff if your a newbie or not

[http://www.ubuntuforums.org/showthread.php?t=73885](http://www.ubuntuforums.org/showthread.php?t=73885)

the Thread was started by one of the members of this forum

Best of luck

---

### Post by malacandra on 2005-11-05
When you install Ubuntu, the first user (set during installation) gets the sudo privileges.

You don't need to know the root password to change it, because sudo will do it.

Do this: 

**sudo passwd root** and you can change the root password.

Then you don't have to do things as sudo and can use root.

If you are really paranoid, you can use root to remove your first account from the sudo privileges. As root, type **visudo** and remove your name from the list.

---

### Post by malacandra on 2005-11-05
When you install Ubuntu, the first user (set during installation) gets the sudo privileges.

You don't need to know the root password to change it, because sudo will do it.

Do this: 

**sudo passwd root** and you can change the root password.

Then you don't have to do things as sudo and can use root.

If you are really paranoid, you can use root to remove your first account from the sudo privileges. As root, type **visudo** and remove your name from the list.

---

### Post by malacandra on 2005-11-05
When you install Ubuntu, the first user (set during installation) gets the sudo privileges.

You don't need to know the root password to change it, because sudo will do it.

Do this: 

**sudo passwd root** and you can change the root password.

Then you don't have to do things as sudo and can use root.

If you are really paranoid, you can use root to remove your first account from the sudo privileges. As root, type **visudo** and remove your name from the list.

---

### Post by malacandra on 2005-11-05
When you install Ubuntu, the first user (set during installation) gets the sudo privileges.

You don't need to know the root password to change it, because sudo will do it.

Do this: 

**sudo passwd root** and you can change the root password.

Then you don't have to do things as sudo and can use root.

If you are really paranoid, you can use root to remove your first account from the sudo privileges. As root, type **visudo** and remove your name from the list.

---

### Post by malacandra on 2005-11-05
Agh! Severe apologies for the multiple posts. Had a hang from Ubuntu and wasn't sure it was being sent. And I don't see a way to delete.

(I don't have sudo privileges on the forums.) :D

---

### Post by konik134 on 2005-11-06
hi   simple try this comand  " sudo -s "  when ask  for password  just tipe password whot u tiping to log on ubuntu           :p

---

