---
title: "I get the edu (or k) ubuntu boot splash screen everytime I install artwork."
date: 2007-08-13
forum: Installation &amp; Upgrades
---

### Post by the_it on 2007-08-13
I installed edubuntu, xubuntu and kubuntu artwork just because.  The thing is, it's bothering my boot splash.  Whenever I boot up, I get the edubuntu splash screen, and I don't like it.

I did this a long time ago before and I ran into the same problem. I installed kubuntu artwork and I got the kubuntu boot splash.  But I'd rather have just plain ubuntu boot splash.

I did some searching, and it seems to me that I have to properly configure my usplash to use the ubuntu splash screen.  I checked the debian update-alternatives to find three splash screens installed on my system.

```
markd@trixie:~$ update-alternatives --display usplash-artwork.so 
usplash-artwork.so - status is manual.
 link currently points to /usr/lib/usplash/usplash-theme-ubuntu.so
/usr/lib/usplash/usplash-theme-ubuntu.so - priority 10
/usr/lib/usplash/usplash-theme-xubuntu.so - priority 10
/usr/lib/usplash/edubuntu-splash.so - priority 50
Current `best' version is /usr/lib/usplash/edubuntu-splash.so.
markd@trixie:~$ update-alternatives --display usplash-artwork.so 
```

so I already pointed my usplash to usplash-theme-ubuntu.

```
markd@trixie:~$ sudo update-alternatives --config usplash-artwork.so 

There are 3 alternatives which provide `usplash-artwork.so'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/usplash/usplash-theme-ubuntu.so
          2    /usr/lib/usplash/usplash-theme-xubuntu.so
 +        3    /usr/lib/usplash/edubuntu-splash.so

Press enter to keep the default[*], or type selection number: 1
Using `/usr/lib/usplash/usplash-theme-ubuntu.so' to provide `usplash-artwork.so'.
```

But I still get the edubuntu splash screen whenever booting.  I'm thinking either I have to fiddle around manually with the priority (that doesn't make sense) or I have to file this as a bug.  How do I do either, or what else should I have checked?

---

### Post by the_it on 2007-08-14
bump

---

