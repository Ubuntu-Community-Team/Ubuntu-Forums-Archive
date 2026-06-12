---
title: "Error message when installing QQ on 12.04"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by More or Less on 2012-04-20
In 11.10  I was able to get QQ running from [http://im.qq.com/qq/linux/download.shtml](http://im.qq.com/qq/linux/download.shtml)

Now, I am using 12.04 and I get the following error message:

[B]"dpkg: error processing /tmp/linuxqq_v1.0.2-beta1_i386-1.deb (--install): 
 parsing file '/var/lib/dpkg/tmp.ci/control' near line 7 package 'linuxqq': 
 error in Version string 'v1.0.2-beta1': version number does not start with digit 
Errors were encountered while processing: "[/B]

I read somewhere that it might be due to the "v" not being a number.  However, I don't know where to edit this.  I tried opening files through Ark, but nothing showed the path listed in the error message.

---

### Post by dino99 on 2012-04-20
what did you got if you rename it ?

/tmp/linuxqq_v1.0.2-beta1_i386-1.deb   as /tmp/linuxqq.deb

---

### Post by More or Less on 2012-04-20
I get the same error message.  I think the location is "near line 7 package 'linuxqq': 
 error in Version string 'v1.0.2-beta1':"

If I can find that, then maybe I can remove the "v".

---

### Post by alazyrabbit on 2012-09-28
I found the solution here:


[http://liangsun.org/linux/resolve-error-version-number-does-not-start-with-digit/]("http://liangsun.org/linux/resolve-error-version-number-does-not-start-with-digit/")

---

### Post by oyster07 on 2012-10-21
Hello.
I am using ubuntu 12.04 but since i started using ubunt i never found a way to install qq.
Ideally i would like to install the english version.
If not the chinese version.
I tried to install qq linuxqq_v1.0.2-beta1_i386.deb but i get an error saying "the package is of bad quality".

Anyone can help. I almost gave up to use qq.
Thanks

---

