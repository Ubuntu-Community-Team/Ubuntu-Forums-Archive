---
title: "Ubuntu under Virtual PC 2007"
date: 2007-03-03
forum: Installation &amp; Upgrades
---

### Post by master_phruby on 2007-03-03
I've installed ubuntu 5.10 on Microsoft's Virtual PC 2007 under Windows XP Pro and it seems to be incompatible. Everything installs correctly but when the graphical interface comes up you get this weird 1600x600 8 colors resolution. Everything is working but you can't see what you are doing. I've tried this on several computers and get the same results. 

What a piece of junk this OS is! Even Windows can figure out a 640x480. I guess you get what you pay for.

---

### Post by jocko on 2007-03-03
The problem is not with ubuntu or linux, it is microsoft that made Virtual PC only support 16 bit colour depth, but still it emulates a graphic card that should support 24 bit.
According to [this]("http://channel9.msdn.com/ShowPost.aspx?PostID=260749") page it should work fine if you change the guest to 16 bit colors.
Try using another virtualisation software. vmware server or qemu should work better.


> What a piece of junk this OS is!
I totally disagree.

---

