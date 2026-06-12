---
title: "How do I fix the dependencies on a deb package?"
date: 2006-05-22
forum: Installation &amp; Upgrades
---

### Post by KWTm on 2006-05-22
The version of Krusader that comes with (k)Ubuntu Breezy and Dapper is v1.60, which doesn't work for me due to a bug.  Version 1.70 is out, and I already have a .deb package for it.  It works great!

My problem is that my Deb package depends on kdelibs4c2, whereas Breezy and Dapper have been using kdelibs4c2a, which I'm sure is pretty much the same thing, but every time I try to install the newer Krusader 1.70, I get the error message that it can't be installed since I don't have kdelibs4c2.

So far I've been getting around this by using the "--ignore-depends" option, as in: (sudo) "dpkg --ignore-depends=kdelibs4c2 -i krusader_1.70.0-0kubuntu1_i386.deb"  This will successfully install the newer krusader, but every time I install anything else, apt-get (or Adept or whatever) will say, "Hey, I notice that the package database is screwed up, so let me help you by automatically removing this krusader 1.70 package!"  And then I have to re-install.

I was told to read the article on pinning, at "https://wiki.ubuntu.com/PinningHowto"; when I follow the instructions to edit "/etc/apt/preferences", I am indeed able to stop apt-get from removing the new Krusader, but apparently it also refuses to install any other packages.

How can I tell apt-get to continue to ignore the dependency on kdelibs4c2?  Better yet, how can I get inside the deb package and change wherever it says "kdelibs4c2" to "kdelibs4c2a" so that I don't have to keep reinstalling Krusader?

Thanks for any help you can give.  I asked at the Ubuntu IRC, but no one was able to help me (or even acknowledge my existence).  Thanks.


KWTm

---

### Post by Rui Pais on 2006-05-24
Hi,
i am problems too to pinning package versions.
The Ubuntu Howto, is just a copy of D[ebians Howto (sec. 3.10)]("http://www.debian.org/doc/manuals/apt-howto/ch-apt-get.en.html") and as far as i experiment didn't work for ubuntu, or at least with dapper.

The only way (not very good) i could found to "pin" a package was:
```
sudo apt-get install wajig
sudo wajig hold <packagename>
```

Alternatives:
At synaptic choose package and from menus set 'Force version'.
That work for synaptic, but neither apt-get or aptitude see the choice...

File /etc/apt/apt.conf.d/50unattended-upgrades, says:
> // never update the packages in this list
Unattended-Upgrade::Package-Blacklist {
//      "vim";
};

I didn't experiment this one, but i presume it works. I didn't find that much intuitive... i'm afraid if i pin a package there i no longer remember that and had troubles later...

---

