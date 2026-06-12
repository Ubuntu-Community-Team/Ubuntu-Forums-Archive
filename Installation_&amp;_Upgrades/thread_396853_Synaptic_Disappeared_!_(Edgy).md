---
title: "Synaptic Disappeared ! (Edgy)"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by Daniel Song on 2007-03-29
Hello All,

I found a weird thing in Ubuntu 6.10 Edgy.

When you log in as root, then you will never activate Synaptic using menu layout.

Is there anybody knows why, and how I can enable it?

Daniel.

---

### Post by adam.tropics on 2007-03-30
Then don't log in as root! It's always run via gksu anyway, so there's no need!

---

### Post by gc1 on 2007-03-30
There's really no need to be logged in as root for many admin jobs. Do them as first user and when you bring up Synaptic it requires your password.
Have fun
Graham

---

### Post by Daniel Song on 2007-03-30
Thanks, guys,

I know the first user can do lot of thins relating to install some packages, but what I want to log in as root is not only the installation but also doing some root job such as compile linux kernel or other jobs. Whenever I access to /usr/local/src directory, the directory is also locked to root. Of course, going back to root and changing mode enable to do that, but it is a little bit tedious.

So, that is why I want to log in as root, which gives me a sort of freedom to explorer anywhere without interruption of password every time.

So, I am just curious about why the root login and general user login work differently in regarding to the menu.

---

### Post by zvacet on 2007-03-31
When you are administrator only thing that synaptic ask from you is your password.You don´t have to activate it ,it is allready active.If you want to be root in terminal
```
sudo -i
```

Just be carefull,because now you have all privileges and it is easy to mes up things.

---

