---
title: "how to install KDE on ubuntu from iso"
date: 2007-08-11
forum: Installation &amp; Upgrades
---

### Post by venkatat on 2007-08-11
hai i have installed ubuntu from iso bootable dvd. The same DVD contains KUBUNTU iso also.

I want to install KDE from kubuntu iso i.e on the DVD. I don't have internet connction ,so i can't use "apt-get'

please help me how to do it

Thanks,
....

---

### Post by matthew.lns1 on 2007-08-11
Can you delete things from the dvd? If so you can delete the ubutu iso and leave the kubuntu iso so that you can boot from it.

---

### Post by venkatat on 2007-08-11
Thanks for your quick reply!!

Ya..i can do that....

but is there any option to get data from iso of kubuntu to install KDE only. I don't want all applications from KUBUNTU. only KDE i want.

can you please help me?

---

### Post by ruibernardo on 2007-08-11
Hi venkatat,

just put the DVD on the drive and make one of the following:

- You want to move from Ubuntu (Gnome) to Kubuntu (KDE).

```
sudo aptitude install kubuntu-desktop
```

- You want to install KDE on Ubuntu but don't want to change the splash screens, the default login and starting window manager from gdm (Gnome) to kdm (KDE).

```
sudo aptitude install kde-core

```

Cheers.

---

### Post by venkatat on 2007-08-11
I will try that...

Thanks again...

---

