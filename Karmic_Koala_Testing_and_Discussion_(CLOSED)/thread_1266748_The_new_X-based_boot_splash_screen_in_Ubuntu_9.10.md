---
title: "The new X-based boot splash screen in Ubuntu 9.10"
date: 2009-09-15
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by wfp on 2009-09-15
Is this a regression, or is it just something effecting my box. So I know were only at alpha 5, and so far I am really enjoying this. I am actually using alpha 5 as my main desktop. I thought with ext4 boot times would be faster, but koala seems to take a lot longer to load than jaunty64. Seems like the new x-based splash screen is slowing things down.

---

### Post by 23meg on 2009-09-15
[QUOTE=wfp]Seems like the new x-based splash screen is slowing things down.[/QUOTE]

You can use [bootchart]("apt:bootchart") to check whether that's the case.

---

### Post by wfp on 2009-09-15
Just what I thought 29sec boot time with boot chart. I was getting about 24sec  with jaunty64. It's hanging on you udevd.

---

### Post by orlox on 2009-09-15
Pretty soon (I believe with beta), usplash wont load, and an xserver will load as fast as possible instead and take you to xsplash. There is an experimental PPA with this functionality that is managed by the main man involved in boosting boot time performance (the ppa is [https://launchpad.net/~ubuntu-boot/+archive/ppa](https://launchpad.net/~ubuntu-boot/+archive/ppa)).

It seems many people are having great success with this thing (and many other cant boot with it :P). So, if you're worried about boot time, just wait a sec. Perhaps you'll be impressed when the beta arrives.

---

