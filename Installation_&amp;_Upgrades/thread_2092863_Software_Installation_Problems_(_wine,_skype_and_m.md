---
title: "Software Installation Problems ( wine, skype and more .... )"
date: 2012-12-09
forum: Installation &amp; Upgrades
---

### Post by hammadmunawar on 2012-12-09
Hello all !

I recently installed Ubuntu 12.10 64-bit with wubi. After installation when I start my computer it asks me to choose between Ubuntu and Windows 7.

Ubuntu works fine. But software installation is a problem. I tried to install wine,  but there is always an error of missing package dependencies. Same happened with skype. 

When I install software, I am prompted to fulfil the 'i386' package dependencies. When I try to install the 'i386' packages, it says 'wrong architecture'.

Is it a limitation of running Ubuntu with wubi ?

Regards

---

### Post by ibjsb4 on 2012-12-09
Try this.

[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter:

```
sudo apt-get update
```

Then try to install again.

---

### Post by hammadmunawar on 2012-12-09
@ibjsb4

I have tried this. All packages got updated.But I still have dependency issues.

Need help real soon.

---

### Post by ibjsb4 on 2012-12-09
To me, this look like a bug with no solution.

[https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217](https://bugs.launchpad.net/ubuntu/+source/wine1.4/+bug/1004217)

[https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/990982](https://bugs.launchpad.net/ubuntu/+source/eglibc/+bug/990982)

Maybe someone else will come up with an idea, but the only immediate solution I can see is to install 32 bit.

---

### Post by hammadmunawar on 2012-12-09
ok ... thanks ...

i dont think wubi asked me whether I wanted to install 32-bit or 64-bit ... so how to manage this ?

---

### Post by diehardhoosier84 on 2012-12-09
Im also having this issue. Im duel-booting Ubuntu with Win7. Everything runs fine till i try to install anything. Ive run 

```
 sudo apt-get update 
```

and everything updates fine. Ive run the install again and still get the following :

"The following packages have unmet dependencies:

wine:"

Im really at a loss here. Any help would be great! I should also remind everyone the last Linux OS i ran was several years ago (RedHat 9). Thanks again guys!

---

