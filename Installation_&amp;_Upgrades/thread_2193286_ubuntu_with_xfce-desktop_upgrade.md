---
title: "ubuntu with xfce-desktop upgrade"
date: 2013-12-12
forum: Installation &amp; Upgrades
---

### Post by GRbit on 2013-12-12
Once upon a time , I pulled up to the end of the brakes on my ancient Atom N260. I thought a bit, and decided to take it to hell  all the gnome and Unity, and install xfce.
Looked , thought and decided to demolish then half of xfce too.
And in general a rather big part of the system was purged, burned as after crusade, and other part was tuned manually.
Then I compiled newest kernel with pf patch and calmed down.


Since then, as the year has passed . Stability and speed constantly pleasing I must say) But less and less programs are building for 12.04, and the more tasty ones released under 12.10 , 13.04 , and their ilk . It's time to upgrade my friends.


But to my great regret, Google is full of **** about cutting ubuntu and install xfce-desktop, there is nothing good I could find.


Tried to refer to the documentation useful to study Debian. There I saw a lot of valuable advice, but unfortunately, I didn't find the detailed description of the processes occurring during upgrade or so. I can not even see what I eventually get , or ubuntu packages with xfce, whether installed packages just refresh ...


I just want to get system based on 12.10 or further. Not a bunch of newly installed packages, but only an opportunity to install bunch of new packages.


Good red-eyed brothers (and sisters , sisters in particular), please share the experience, and even better detailed manual. Manual explaining what actually happens at a time of upgrade, and how to make such manipulation in manual mode.


P.S.: Update this version, or to experience the process of updating necessary, other options are NOT CONSIDERED.

---

### Post by mastablasta on 2013-12-12
what are you saying? install xfce and then remove the gnome packages that are not needed (e.g.): [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu)

to get new packages into 12.04 you need to have PPA of the newer package. to witness the upgrade process as it happens do it via terminal.

---

### Post by GRbit on 2013-12-12
I've deleted more packages than it supposed by link you gave. I worried about upgrading process, if it will not find some package what will happen?

New packages just want more new packages. Sometimes that packages are from newer version of ubuntu. I don't want to install all of them manually like in Gentoo.

I'm just worried that when I'll do distro upgrade, It automaticaly install lots of packages I don't needed. I whnat to control this process and every new package.

Can I for example add PPA of 12.10 and delete the 12.04 PPA? What will happen?

P.S. Thank you for replying me)

---

### Post by Bucky Ball on 2013-12-12
I think an upgrade upgrades the kernel to the 12.10 kernel and the packages you currently have installed. Apart from the kernel I don't think it drags anything else in. I had a complete hybrid running on my desktop for about four years and did 8.04>10.04 upgrade and didn't notice anything new.

I can't say, though, that I can guarantee nothing is dragged in or can comprehensively answer your query.

---

### Post by Frogs Hair on 2013-12-12
> Can I for example add PPA of 12.10 and delete the 12.04 PPA? What will happen? What PPA ?

A distribution upgrade via the updtate manager is a complete package/library replacement and software repository change. I have watched an upgrade and what happens is the repository is changed to the new release with the upgrade prompt ,  download of the new release ISO packages , unpacking of replacements , installation/setup of new packages, cleanup, and reboot.This process is not subject to manual control.

 It reads like you want to add a newer repository to an older release to get newer software versions and it won't work because of dependency differences .  I run an XFCE PPA on 13.10 and the packages are listed on Lauchpad .  [https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12](https://launchpad.net/~xubuntu-dev/+archive/xfce-4.12)

---

