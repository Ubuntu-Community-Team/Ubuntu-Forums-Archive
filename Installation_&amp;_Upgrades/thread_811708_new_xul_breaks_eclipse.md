---
title: "new xul breaks eclipse"
date: 2008-05-29
forum: Installation &amp; Upgrades
---

### Post by tjajab on 2008-05-29
I have been running Eclipse on sun's java (6) for quite some time now, and today after I did a regular update (including xulrunner and firefox3rc1) it crashes. It says error in libxul.so.

I use Eclipse Europa which is not yet in the Ubuntu repositories, so I guess the Ubuntu people cannot really be blaimed for this, but I wonder, does anyone have the same problem with the Eclipse 3.2.2 from the Ubuntu repository?

And I also want to know, what is xul, and is there anyway I could point Eclipse to use the old xul?

Appreciate any help or hint.

---

### Post by bammers on 2008-07-03
Hi tjajab,

Yes, I have the identical problem, also caused by a routine update.  I have hunted around for an answer, but to date have found nothing satisfactory.  This is hurting productivity as my workaround is to switch over to NetBeans just so I can keep working :-(

I too, would really appreciate a quick resolution to this issue.

---

### Post by tjajab on 2008-07-06
Hi bammers,

I actually solved my problem, because I had put libxul.so and some other libraries in a special folder to which I pointed Eclipse, in order to solve another problem. So I removed the folder and its contents, and let Eclipse use the original files, and so the problem was solved. I.e., my problem was because I had tried to solve another problem by telling Eclipse to use special libraries.

---

### Post by edvin on 2008-07-08
Hi.

What exactly did you do.
I have a similar problem, but I do not know how to tell eclispe to use /or not use) certain libs.

---

### Post by tjajab on 2008-07-08
In the /etc/environment, I had set LD_LIBRARY_PATH="/usr/lib/firefox;/home/andreas/lib" to solve another problem. In my lib directory I had put another libxul.so among other files. An update broke my system, but when I removed the ";/home/andreas/lib"-part above it started to work again.

---

### Post by edvin on 2008-07-09
Ok.

I don't think this will do the trick for me, but thanks anyway.

---

### Post by str238 on 2008-08-27
I'm experiencing the very same problem with Eclipse. Did anyone found a solution by now? Thank you for any advice.

---

### Post by predder on 2008-10-22
Came across this too while searching:
[http://mail.openjdk.java.net/pipermail/distro-pkg-dev/2008-June/002376.html](http://mail.openjdk.java.net/pipermail/distro-pkg-dev/2008-June/002376.html)

This only started happening for me when I put libxul.so in /usr/lib/ because firefox refused to run without that file there (even though the library is in the firefox folder with the binary). Will try removing that file and see if that's it for me.

---

