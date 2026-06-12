---
title: "Why doesn't Ubuntu uses Debian repositories"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by xbaez on 2005-05-20
Hello

I will like to know why isn't Kubuntu/Ubuntu using the Debian repositories

I really like this phrase from debian.org
*"Debian GNU/Linux provides more than a pure OS: it comes with over 8710 packages, precompiled software bundled up in a nice format for easy installation on your machine."*

I want to use a distro that is based on Debian (I don't like the distros like Debian, were you can't even see the display of your computer without passing through hours of reading, investigating, tweaking... your os), but I don't want to use Debian, because I find it too difficult to install

Therefore, the question is
If mepis is entirely based on Debian, why does Kubuntu/Ubuntu has their own repositories?

Regards

Xavier

---

### Post by Strife on 2005-05-20
Quite simply, because the Ubuntu packages are maintained separately from the Debian packages. Debian is notorious for being out of date. Ubuntu on the other hand largely has up-to-date packages.

A perfect example is X. Debian remains (AFAIK) the only major distribution still relying on XFree86. All the others have long since switched over to Xorg.

---

### Post by NateC on 2005-05-20
Also I believe it is because that Ubuntu is not 100% compatiable with debian repositories.

---

### Post by kassetra on 2005-05-20
The Ubuntu distribution - like almost every other distribution, takes a library, application, etc. and fixes/enhances/alters it to work better with their distribution.

In Ubuntu's case - they take unstable debian packages and fix/enhance/alter them to work cleanly with an Ubuntu system.

This is why they have their own repository - they do their own work preparing a package for an Ubuntu system.

---

### Post by xbaez on 2005-05-20
ok but Debian has almost 9000 packages according to them

for example, I search for Eclipse, and I can't find it

When I used Mepis it used the us.debian repositories, and to be honest, I could find quite about everything

I will really like to be able to download stuff like Gambas, Glade, Eclipse, NetBeans

I know some of these programs are in the repositories, but some arent'

Regards

Xavier

---

### Post by the_clown on 2005-05-20
Try adding these extra repositories:
[http://ubuntuguide.org/#repositories](http://ubuntuguide.org/#repositories)

---

