---
title: "Trouble: Install Open VMWare Tools on Ubuntu 8.04 Hardy"
date: 2008-10-16
forum: Installation &amp; Upgrades
---

### Post by haize on 2008-10-16
I run configure under vmware-tools, but it always encounters a error: checking for uriFreeQueryListA in -luriparser&#8230; no
configure: error: uriparser library not found or is too old. Please configure without Unity (using &#8211;disable-unity) or install the liburiparser devel package.

I did installed libuiriparser-dev and found its library in /usr/lib and its header files in /usr/include/uriparser

So I used the command: CFLAGS=&#8221;-I /usr/include/uriparser&#8221; CPPFLAGS=&#8221;-I /usr/include/uriparser&#8221; LDFLAGS=&#8221;-L /usr/lib&#8221; ./configure

But it doesn&#8217;t work yet. I googled a lot but no answer can be found.

my environment:
Ubuntu 8.04 hardy
Open VMware Tools 20080913
Uriparser 0.7.2
AMD 64 with 2 processors.

Help~~~~~ Help~~~~~ Help~~~~~

---

### Post by sefs on 2008-10-26
Same problem here.

---

### Post by pastrand on 2008-10-27
Looks like the latest version of vmware tools need a later version of uriparser lib.

From configure (line 17839):
```

  # Note that we look for uriFreeQueryListA because it's a relatively
  # new symbol that our code needs (it isn't present in the uriparser
  # that shipped with Ubuntu Hardy).

```

/Per

---

### Post by alex_dd on 2008-10-28
Try to get uriparser0.7.2 from sf
install it to def path - /usr/local
then try to build openvm again, but specify the CFLAGS AND LDFLAGS
in mycase it was like this:

CFLAGS="-I /usr/local/include/uriparser" CPPFLAGS="-I /usr/local/include/uriparser" LDFLAGS="-L /usr/local/lib" ./configure

uri issue passed!
good luck

---

### Post by rd1966 on 2008-10-28
Hi alex_dd,

I'm having this problem too.  Whilst I'm fine with apt-get packages, I'm new to manual installation.  Any chance you could give a step-by-step guide to installing uriparser?  

Many thanks,

rd

---

### Post by DieKatzeKotzt on 2009-02-25
Thanks for the trick... be careful it's CFLAGS="-I /usr/local/include/uriparser" CPPFLAGS="-I /usr/local/include/uriparser" LDFLAGS="-L/usr/local/lib" ./configure

... note that there is not space between -L and /.. LDFLAGS="-L/usr/local/lib"

best regards, André

---

### Post by packs on 2009-03-04
thanxs for this one:-)

---

