---
title: "Compiling the svn MPlayer under Karmic: gcc-4.3??"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrew.46 on 2009-10-02
Hi,

I have made several attempts to compile the svn MPlayer under Karmic's gcc 4.4.1 with a series of bizarre results including seg faults, odd video displays at times and a few other minor annoyances. I note that the MPlayer devs specifically recommend against compiling with either gcc 4.4.0 or 4.4.1.

Problem seems to be solved for me by downloading gcc-4.3 from the Karmic repository and running:

```
$ ./configure cc=gcc-4.3
$ make cc=gcc-4.3
```

Can anybody else confirm this experience and this solution? I would welcome any mention of potential problems of having more than one version of gcc installed as well! The MPlayer produced in this manner is as I remember it from compiling under Hardy and upwards: steady as a rock.

Edit: Better... I have posted an early version of this guide[ here]("http://ubuntuforums.org/showthread.php?p=8039829").

Andrew

---

### Post by andrew.46 on 2009-10-06
Just for the sake of completion I note here that both versions of gcc *can* safely co-exist on the one installation. And the syntax required for MPlayer is simply:

```
$ ./configure cc=gcc-4.3
$ make 
```

This setup has been running on my system with absolutely no errors, the *default* gcc being 4.4.1 and the other gcc-4.3 being called from the commandline when needed.

Andrew

---

### Post by Miguel on 2009-10-06
Yeah, different compilers can indeed coexist. Heck, even different library versions of the standard c++ library can coexist. This is very noticeable with proprietary drivers, which depend on a certain compiler. IIRC, flgrx used to depend on gcc-3.3 even when the ubuntu default was gcc-4.2. Installing it did pull gcc-3.3 as a dependency.

I'm worried however about the mplayer package in karmic. Have you tried using the package available in the repositories? Installing its build dpendencies doesn't seem to pull gcc-4.3. I fear that maybe we are getting a substandard quality package built with gcc 4.4.1 instead of the recommended 4.3.

---

### Post by andrew.46 on 2009-10-06
Hi Miguel,

> **Miguel said:**
> I'm worried however about the mplayer package in karmic. Have you tried using the package available in the repositories? Installing its build dpendencies doesn't seem to pull gcc-4.3. I fear that maybe we are getting a substandard quality package built with gcc 4.4.1 instead of the recommended 4.3.

I tried it briefly when I was tossing up whether or not to write another svn MPlayer guide and I did not encounter any problems. It will be interesting when Karmic is released if there are any widespread troubles. BTW the compiler version used should show up when you use the commandline MPlayer, just after the version string.

Andrew

---

