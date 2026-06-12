---
title: "Karmic GTK Version?"
date: 2010-03-14
forum: Installation &amp; Upgrades
---

### Post by JSeymour on 2010-03-14
So the version of JPilot that's in the repos mangles my Palm databases (incl. on the Centro, itself).  New versions of pilot-link and JPilot that address this have been released by their respective developers, but JPilot requires GTK-2.03 or better.  Near as I can tell, the repos have only 2.0.  I notice that GTK is up to 2.18.

Any chance there'll be an update to Karmic someday in the not-too-far-distant future, or am I back to having to build everything by hand, from tarballs?

Thanks,
Jim

---

### Post by Seq on 2010-03-14
> **JSeymour said:**
> (...) requires GTK-2.03 or better.  Near as I can tell, the repos have only 2.0.  I notice that GTK is up to 2.18.

Karmic has GTK+ 2.18.3. It was named libgtk2.0 so packaging systems could keep it installed alongside the older ("1.0") gtk. The package and library name is kept for compatibility, else you would have to rebuild every program when a new version of gtk came out.

```
$ aptitude show libgtk2.0-0 | grep Version
Version: 2.18.3-1ubuntu2.2
```

---

### Post by JSeymour on 2010-03-14
> **Seq said:**
> Karmic has GTK+ 2.18.3. 
...
```
$ aptitude show libgtk2.0-0 | grep Version
Version: 2.18.3-1ubuntu2.2
```Ah.  So the 2nd of the two version numbers:
```

>dpkg -l |grep libgtk
...
ii  libgtk2.0-0     2.18.3-1ubuntu2.2     The GTK+ graphical user interface library
...

```is the real version number.

Thanks!

So when this happens in a configure script:
```

checking for GTK+ - version >= 2.0.3... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: *** GTK >= 2.0.3 not found ***

```It's broken configure code?

But... waitaminute... isn't it traditional, when wants to achieve what you're referring-to,
to install the lib with it's real version number, and symlink to it?

Jim

---

### Post by Seq on 2010-03-14
You'll need the development packages installed as well.

Since jpilot is in the repositories already, you should be able to just instruct apt to grab everything required to build it.

```
sudo apt-get build-dep jpilot
```

---

### Post by JSeymour on 2010-03-14
> **Seq said:**
> You'll need the development packages installed as well.

Since jpilot is in the repositories already, you should be able to just instruct apt to grab everything required to build it.

```
sudo apt-get build-dep jpilot
```I think you missed an important point: The pilot-link and JPilot packages I'm building (well, trying to, in the latter case) aren't in the repos yet.  I'm building these from tarballs from their respective home sites.

Nonetheless: JPilot will not build because its configure script is not seeing what it wants to see for libgtk.

Thanks for the feedback, tho.

Jim

---

### Post by Seq on 2010-03-14
> **JSeymour said:**
> I think you missed an important point: The pilot-link and JPilot packages I'm building (well, trying to, in the latter case) aren't in the repos yet.  I'm building these from tarballs from their respective home sites.

Nonetheless: JPilot will not build because its configure script is not seeing what it wants to see for libgtk.

Thanks for the feedback, tho.

Jim

No, I'm not. `apt-get build-dep jpilot` tells apt to get the stuff required to build jpilot, not to install jpilot. That will fetch all the gtk headers, stuff for bluetooth, etc.

Distributions typically don't install header files with the actual package. Reason being that 90% of users will never need them, and it just takes up space (especially when targeting a live system on a single CD-ROM ). Since you are building software, you do need them. You can either track down every build dependancy jpilot and pilot-link have, or you can start with what the current version in the repository needs. Chances are they build-requirements have not changed. Even if they have, this still gets you 90% of the way there.

If you want to manually fetch headers, you will need to start out with installing "libgtk2.0-dev", which contains the headers needed to build against gtk. After running ./configure again, it will fail on another library and you'll have to track down what package contains it's header files.

---

### Post by JSeymour on 2010-03-14
> **Seq said:**
> No, I'm not. `apt-get build-dep jpilot` tells apt to get the stuff required to build jpilot, not to install jpilot. That will fetch all the gtk headers, stuff for bluetooth, etc.
...
If you want to manually fetch headers, you will need to start out with installing "libgtk2.0-dev", which contains the headers needed to build against gtk. After running ./configure again, it will fail on another library and you'll have to track down what package contains it's header files.Gah!  Of course!

I come from a Solaris and, before that, SCO and Motorola Unix background, and, to this day, keep forgetting that Linux distros don't usually include the necessary header files and other drek that more traditional Unix' usually do/did when you installed things.  You'd think that after having this happen to me several times, the light would come on, wouldn't you? :p

Turned out all I needed was libgtk2.0-dev.

Thanks!

Jim

---

### Post by Seq on 2010-03-15
No problem. I came from a source-based distro that included everything by default. A bit of an adjustment in process, but you get used to it.

---

### Post by zaivala on 2011-04-01
Sorry, stupid comment. Figured it out. Please ignore. I'd delete if I could.

---

### Post by jelabarre on 2012-06-07
[QUOTE=Seq;8967719]No, I'm not. `apt-get build-dep jpilot` tells apt to get the stuff required to build jpilot, not to install jpilot. That will fetch all the gtk headers, stuff for bluetooth, etc.
 
No go in Precise.
================================

:~/src/jpilot$ sudo apt-get build-dep jpilot
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to find a source package for jpilot

================================

So apparently not available in the repos now (yes, I have run apt-get update a number of times)



EDIT:  never mind, it looks as though either Precise/12.04 or Linux mint removes the "deb-src" lines in the repo list these days.

---

### Post by coffeecat on 2012-06-07
This thread is about Karmic/9.10, an obsolete version of Ubuntu.

Old thread closed.

---

