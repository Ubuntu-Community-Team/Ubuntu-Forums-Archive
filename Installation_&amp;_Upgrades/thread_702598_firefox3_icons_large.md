---
title: "firefox3 icons large"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by stu2004 on 2008-02-20
when i start firefox 3 the icons are massive and pixelated. have i missed something? i have a separate profile.

any idea what's wrong?

thx,

Stu

---

### Post by stefan1975 on 2008-03-01
hi,

i dont have a solution for your problem, i have the exactg same problem as you. Firefox 2.0.12 is running fine and normally. firefox 3b3 and a vanilla ff3b4 have insane huge fonts and icons. on windows ans Solaris it is fine however.

[img]http://i248.photobucket.com/albums/gg164/stefan1975/Screenshot.png[/img]

i hope some can give the answer for this odd problem. I have removed my .mozilla folder but that did not help, i have reinstalled it, downloaded the true ff3b4 from mozilla.org but all the same problem. Does anyone know what is doing this and how to fix it? icons are so large that it is even starting to get pixelated. I also tried <ctrl> - and <ctrl>/ and <ctrl>0 but none of those help either.

thx,
stefan

---

### Post by therpham on 2008-03-03
I'm having a similar problem. After I enabled fglrx drivers, everything in Firefox is huge and I can't get it to shrink back down. I just installed the newest Hardy Heron to mess around with. This is rather inconvenient!

Edit: Oh, thank God! From [https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/178558](https://bugs.launchpad.net/ubuntu/+source/xulrunner-1.9/+bug/178558)
> 
1) Go to about:config
2) Search "dpi". The value may be set to -1 (maybe auto-detection)
3) Change it to 96 (default dpi)
4) Enjoy Firefox 3!!!


---

