---
title: "Registering a package that was compiled from source and installed"
date: 2014-03-22
forum: Installation &amp; Upgrades
---

### Post by sg42 on 2014-03-22
Hi, All,

I'm wondering if someone can help me out with this situation:

I'm trying to install a package (in this case, octave) by saying 

```
sudo apt-get install octave
```.

One of the dependencies for Octave is Gnuplot, and so, apt-get replies: 

```
The following new packages will be installed:
   .... gnuplot-x11 .....

```

However, I have already compiled gnuplot from source and installed it (because I wanted readline support). And so, I was wondering if there might be a way to tell apt-get that gnuplot is already installed.

Thanks.

SG.

---

### Post by TheFu on 2014-03-23
Debian has recommended using **aptitiude** over apt-get for years. It is smarter and can resolve dependencies that confuse apt-get. That doesn't mean it won't get confused for complex situations or when a PPA or directly installed .DEB files get in the way.

---

### Post by sg42 on 2014-03-23
Thanks for pointing me towards aptitude. However, the problem still remains even if I replace "apt-get" with "aptitude". Any other thoughts?

---

### Post by oldos2er on 2014-03-23
You could try ```
sudo apt-get install --no-install-recommends octave
``` but I can't guarantee it will work.

---

### Post by steeldriver on 2014-03-23
... perhaps you could reinstall gnuplot from source using checkinstall?

---

### Post by TheFu on 2014-03-23
> **sg42 said:**
> Thanks for pointing me towards aptitude. However, the problem still remains even if I replace "apt-get" with "aptitude". Any other thoughts?

Well, that is the risk we run when leaving the pre-built repositories for software.  Building from source should be a last resort, since it can break dependencies and exponentially increase maintenance stuff. 

Here are my priorities for getting software:
* Official Repos
* Official PPAs
* Non-official PPAs
* Don't run / use the software
* Install from source

Did you look for a PPA with the newer version of gnuplot?

Since we've already gone the "source route", we can also get the source for the package for the next one and compile it.  This will add to the maintenance liability.

I understand that installing source is sometimes needed.  I did it all the time in the 1990s, back when there wasn't much other choice. Those systems were a nightmare to maintain - we didn't have much choice.

---

### Post by sg42 on 2014-03-23
SteelDriver, I like the checkinstall suggestion, in which the manually installed package gets registered with the system package management system.

However, when trying to install octave, apt-get (and aptitude) still think that they need to install gnuplot-x11. I did manage to fool the system by naming the manually installed package "gnuplot-x11", using
 
```

sudo checkinstall --pkgname gnuplot-x11 make install

```

but this is a very dirty way of doing it, and is almost guaranteed to pose problems in the future.

I guess what I'm now looking for is a setting that tells apt-get that "gnuplot-MYVERSION" is an equivalent to "gnuplot-x11". Not sure if anything like this exists, but it would be great if someone knows of it.

Thanks.

SG.

---

