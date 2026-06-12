---
title: "popularity-contest"
date: 2009-06-17
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by celticbhoy on 2009-06-17
I have just completed todays updates, and noticed a package called popularity-contest was installed/updated. This is the first I have heard of this package, and searched google for it and found a web site full of stats on packages - no surprise there then. Is this new or has it been in Ubuntu for a while?

---

### Post by Sealbhach on 2009-06-17
If you look in Add/Remove, all the apps have a star rating based on Popularity. This comes from popularity contest - it's been there since at least Hardy.

.

---

### Post by celticbhoy on 2009-06-17
Thanx - just never heard of it before. Should really be more known in the forums, especially when you consider the amount of threads that want to change the apps to something else.

---

### Post by ssam on 2009-06-17
remember you have to enable it. system->administration->software-sources go to the statistics tab.

---

### Post by autocrosser on 2009-06-17
Also---when you install, there is a option to enable it--you will need to look for advanced options just before the installer "really" installs things........

---

### Post by Col-1023 on 2009-06-17
I have the popularity contest enabled, so I assume that when I install something with synaptic, it will be registered.

I want to know if I install software using the command line, does this also get registered in the popularity contest?

---

### Post by ssam on 2009-06-17
> Description: Vote for your favourite packages automatically
 The popularity-contest package sets up a cron job that will
 periodically anonymously submit to the Ubuntu developers
 statistics about the most used Ubuntu packages on this system.
 .
 This information helps us making decisions such as which packages
 should go on the first CD. It also lets us improve future versions
 of Ubuntu so that the most popular packages are the ones which are
 installed automatically for new users.

i does not matter how you install the software once per week (i think) it uploads a list of which packages you have installed (and if they have been recently used (based on atime of their files))

---

### Post by celticbhoy on 2009-06-17
does that mean a package not in the repos will still get counted? ie chromium

---

### Post by ssam on 2009-06-17
```

wget http://popcon.ubuntu.com/by_inst.gz
zcat by_inst.gz | grep chromium

```

gives

```

3896  chromium-data                  29656     0     0     0 29656 (Debian Games Team)             
3939  chromium                       28949   471 27408  1017    53 (Debian Games Team)             
7818  chromium-browser                6224   405  2176  3642     1 (Unknown)                       
9499  cxchromium                      3776   298  3258   151    69 (Unknown)                       
14048 ia32-libs-chromium-browser      1497     0     0     0  1497 (Unknown)                       
17999 ia32-cxchromium                  848    57   733    42    16 (Unknown)                       
30263 chromium-testsuite               147     0    74    73     0 (Unknown)                       
30439 chromium-browser-dbg             144     0    56    88     0 (Unknown)                       
37313 chromium-testsuite-dbg            56     0    24    32     0 (Unknown)                       
39814 chromium-bsu-data                 39     0     0     0    39 (Unknown)                       
40595 chromium-bsu                      35     3    12    20     0 (Unknown)                       
81028 chromium-daily-ppa                 1     0     0     0     1 (Unknown)                       
81029 chromium-dbgsym                    1     0     1     0     0 (Unknown)

```

chromium-browser is the 7818th most popular ubuntu package. the ones above that are a game.

---

### Post by Col-1023 on 2009-06-17
Thanks Ssam, your replies were very helpful.

I didn't know it was possible to find out how popular a package was either.

---

### Post by Toe on 2009-06-18
> **ssam said:**
> based on atime of their files


Thanks for this interesting bit of information.
It made me realize that, since all my drives are mounted with the noatime option, I'm hit by this bug: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298760](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298760)

---

### Post by celticbhoy on 2009-06-18
Cheers for the advice on use Ssam. Having a look through with certain packages it just shows what is getting used and what isn't.

---

### Post by ssam on 2009-06-18
> **Toe said:**
> Thanks for this interesting bit of information.
It made me realize that, since all my drives are mounted with the noatime option, I'm hit by this bug: [http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298760](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=298760)

you could use relatime. it only updates atime once perday, so it is not as resource wasting as the old atime updates, but is enough to make things like popcon work.

see [http://lwn.net/Articles/244829/](http://lwn.net/Articles/244829/)

i think this is the ubuntu default, and now also the kernel default [http://thread.gmane.org/gmane.linux.kernel/813054](http://thread.gmane.org/gmane.linux.kernel/813054)

---

### Post by a11z on 2009-08-11
1) How do I disable popularity-contest?
2) Is there a way to uninstall popularity-contest pkg without removing other pkgs, such as ubuntu-desktop?

Thx.

---

### Post by qamelian on 2009-08-11
> **a11z said:**
> 1) How do I disable popularity-contest?
2) Is there a way to uninstall popularity-contest pkg without removing other pkgs, such as ubuntu-desktop?

Thx.
Unless you have specifically enabled it, you don't need to disable it. It isn't enabled by default on Ubuntu.

---

