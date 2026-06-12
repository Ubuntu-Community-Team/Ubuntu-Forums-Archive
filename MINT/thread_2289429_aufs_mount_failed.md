---
title: "aufs mount failed"
date: 2015-08-04
forum: MINT
---

### Post by Ketirs on 2015-08-04
Hello! I'm trying to make my own variant of the Linux Mint 17.2 MATE x64, but have problems with kernels 4.x.x and above. When I'm making iso with "remastersys", and then trying to load from it, it writes:
```
(initramfs) unable to open 'dev/sda'
stdin: Not a typewriter
mount: mounting aufs on /root failed: No such device
aufs mount failed
```

But when I searched for aufs, I had found this:> 
[TABLE="width: 75%"]
[TR]
[TH]linux kernel version[/TH]
[TH] aufs version[/TH]
[/TR]
[TR]
[TD] 4.0 and later[/TD]
[TD] aufs4     
 Currently aufs4 supports these kernels. 

[TABLE]
[TR]
[TH] version[/TH]
[TH] status in mainline[/TH]
[TH] support status[/TH]
[/TR]
[TR]
[TD] linux-4.x-rcN[/TD]
[TD] latest[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[TR]
[TD] linux-4.1[/TD]
[TD] latest[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[TR]
[TD] linux-4.0[/TD]
[TD] stable[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[TR]
[TD] 3.14 and later[/TD]
[TD] aufs3     
 Currently aufs3 supports these kernels. 

[TABLE]
[TR]
[TH] version[/TH]
[TH] status in mainline[/TH]
[TH] support status[/TH]
[/TR]
[TR]
[TD] linux-3.19[/TD]
[TD] stable[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[TR]
[TD] linux-3.18.1+[/TD]
[TD] for v3.18.1 and later[/TD]
[TD] supported but little tested[/TD]
[/TR]
[TR]
[TD] linux-3.18[/TD]
[TD] longterm[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[TR]
[TD] linux-3.17[/TD]
[TD] [EOL][/TD]
[TD] supported but little tested[/TD]
[/TR]
[TR]
[TD] linux-3.16[/TD]
[TD] [EOL][/TD]
[TD] ditto[/TD]
[/TR]
[TR]
[TD] linux-3.15[/TD]
[TD] [EOL][/TD]
[TD] ditto[/TD]
[/TR]
[TR]
[TD] linux-3.14.40+[/TD]
[TD] for v3.14.40 and later[/TD]
[TD] ditto[/TD]
[/TR]
[TR]
[TD] linux-3.14.21+[/TD]
[TD] for v3.14.21 and later[/TD]
[TD] ditto[/TD]
[/TR]
[TR]
[TD] linux-3.14[/TD]
[TD] longterm[/TD]
[TD] supported and fully tested[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]


[http://aufs.sourceforge.net/](http://aufs.sourceforge.net/)

So, basicly, aufs are supported and tested (maybe only by aufs) and run good on kernerls 3.19+, 4.x.x. So, what is going wrong?

Can someone help me please? I'll be much gratefull!

The base of the Linux Mint 17.2 is Ubuntu 14.04.2 LTS.

Maybe aufs version, that remastersys works with is not enough (just my guess)? 

P.S. I also want to edit "install menu" that remastersys makes, to add function (basically, i want what ubuntu / mint usus for it's install).
P.S.S I also have tried with kernel 3.19.0-25 - and it worked just fine!

---

### Post by lordbink on 2015-08-18
It looks like aufs was taken out of the Ubuntu kernel in favor of overlayfs. Overlayfs has been a work in progress since 2.6 kernels. I find it rather buggy and inconsistent between stable kernel versions, which makes this all the more frustrating. I, myself, am struggling to get overlayfs working without much luck.

---

### Post by dj--alex on 2015-10-13
Please help anybody

me and my friend still using remastersys , this is only in world software with 
excellent work for me and my users (ubuntu repack). Wonderful tool. Best from 2008 to 2015 !

If you can help we and many other users can continue use remastersys
and creating normal own distros.

At this moment distros have 3.16 kernel with aufs + separate archive with 4.2
IT'S NOT NORMAL! 

We tries many times compile 4.x kernel with aufs support which requirest to run 
and 4.1, 4.2 kernel have crash results ^( 

I think some of this links can be useful
[https://github.com/sfjro/aufs4-standalone/tree/aufs4.2](https://github.com/sfjro/aufs4-standalone/tree/aufs4.2)

I tries kernel 4.2.3 compiled with aufs for deb x64 files  by another use
[https://drive.google.com/folderview?id=0BypQwP0us6vqX1VfeHppVl9Nd0U&usp=sharing&tid=0B9C1WK1FQhjfcXNrbzN6djQzajg](https://drive.google.com/folderview?id=0BypQwP0us6vqX1VfeHppVl9Nd0U&usp=sharing&tid=0B9C1WK1FQhjfcXNrbzN6djQzajg)
but this crappy kernel cannon EVEN load system
i see black screen and cursor

---

