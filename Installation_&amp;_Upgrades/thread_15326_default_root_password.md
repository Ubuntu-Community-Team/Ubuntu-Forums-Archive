---
title: "default root password????"
date: 2005-02-13
forum: Installation &amp; Upgrades
---

### Post by particlehunter on 2005-02-13
Hi,

I have just installed Ubuntu 5.04 'Hoary' for AMD64, but I have a serious problem... everything runs perfectly, but I can't have access to the admin tools because it runs with my created user by default and there's no mention to the default root password used, tested with the typical passwords and... no use...

so, until I find the password I can't do anything like upgrading using apt-get or just... change the networking configuration within GNOME 2.9.91, so... can anyone help me?

thanks in advance, 

Julio

BTW: I forgot to mention an important thing... I used the NETBOOT iso to install Ubuntu

---

### Post by tim1 on 2005-02-13
There is no root account.

The graphical configuration tools promt for _your_ password.

and please use the search function, there are about a billion threads on that

greets, tim

---

### Post by drasko on 2005-02-13
Do #sudo passwd and change a password for root.
I belive you have gtk-su so after that you can use it...

Drasko

---

### Post by JamesRock on 2005-02-13
there is so a root account just do this

sudo passwd

then enter whatever as the password, then it will let you enter a new password

now you can just

su

or login as root!

screw this sudo ****

---

### Post by jdong on 2005-02-13
Since the Ubuntu main target audience (desktops, i.e. single user workstations) usually has a single login, making two accounts (root & user) makes little sense. Chances are, users start picking weaker passwords, forget passwords, etc.

Even in the professional world, it's always in your best interest to use sudo.

The biggest advantage is that sudo logs all commands issued, so if they mess something up, it's easy to see what went wrong.

---

