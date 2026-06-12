---
title: "libreoffice installation help?"
date: 2011-01-12
forum: Installation &amp; Upgrades
---

### Post by mbrown9412 on 2011-01-12
okay, I am attempting to install Libreoffice for my computer.

it was working fine, until i got this error, and this error persists no matter what i try to do:

```
The following packages have unmet dependencies:
  libreoffice-core: Depends: libreoffice-common (> 1:3.3.0~rc2) but it is not going to be installed
  libreoffice-java-common: Depends: libreoffice-common but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

what does this mean, how do i fix it, and how should i go about installing libreoffice?

---

### Post by TeoBigusGeekus on 2011-01-12
Have you tried [this]("http://drupal.txwikinger.me.uk/content/libreoffice-now-available-ppa-ubuntu-1010-and-1004")?

---

### Post by mbrown9412 on 2011-01-12
yes, thats exactly what i was trying

---

### Post by mbrown9412 on 2011-01-12
I also tried reinstalling openoffice, and that didnt work either, it said it need some dependencies or something like that...


for now, i would just be happy with either installed

---

### Post by TeoBigusGeekus on 2011-01-12
Try apt's suggestion
```
sudo apt-get -f install
```
and then try again.

---

### Post by mbrown9412 on 2011-01-13
I did exactly that - it still didnt help

---

### Post by swiftsam on 2011-02-03
I had the same problem, and it seems like the solution is to remove open-office first.  On my office computer installing libreoffice automatically removed open-office, but at home I got the same error as you.

I found this thread
[http://ubuntuforums.org/showthread.php?p=10406192](http://ubuntuforums.org/showthread.php?p=10406192)

that linked to these instructions
[http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26](http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26)

which include the instruction to run this first
sudo apt-get autoremove openoffice.org-*

It seems a bit of a strange solution to the error we're getting, but that's all it took for libreoffice to install for me

---

### Post by bookcrazy on 2011-04-20
Thanks for the post.

---

### Post by carra on 2011-07-06
> **swiftsam said:**
> I had the same problem, and it seems like the solution is to remove open-office first.  On my office computer installing libreoffice automatically removed open-office, but at home I got the same error as you.

I found this thread
[http://ubuntuforums.org/showthread.php?p=10406192](http://ubuntuforums.org/showthread.php?p=10406192)

that linked to these instructions
[http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26](http://maketecheasier.com/replace-openoffice-with-libreoffice-in-ubuntu/2011/01/26)

which include the instruction to run this first
sudo apt-get autoremove openoffice.org-*

It seems a bit of a strange solution to the error we're getting, but that's all it took for libreoffice to install for me

It did the trick for me too! :popcorn:
.

---

