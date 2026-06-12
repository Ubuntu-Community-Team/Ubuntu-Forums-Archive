---
title: "libgstreamer0.10"
date: 2016-10-20
forum: Installation &amp; Upgrades
---

### Post by lucedan on 2016-10-20
I upgraded to Ubuntu 16.10.
Now I am trying to install SuperCollider on it. Building the source, it reports this error:

/usr/bin/ld: warning: libgstreamer-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libgstapp-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libgstbase-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
etc...

As I understand, I should install libgstreamer0.10-dev and libgstreamer-plagins-base0.10-dev
But is it possible I read that this library is not supported anymore in Ubuntu 16.10?

$ sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
is indeed unable to locate the package

How can I install this library in my OS?

---

### Post by T.J. on 2016-10-20
> **lucedan said:**
> I upgraded to Ubuntu 16.10.
Now I am trying to install SuperCollider on it. Building the source, it reports this error:

/usr/bin/ld: warning: libgstreamer-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libgstapp-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
/usr/bin/ld: warning: libgstbase-0.10.so.0, needed by /home/luca/Qt5.4.2/5.4/gcc_64/lib/libQt5WebKit.so.5.4.2, not found (try using -rpath or -rpath-link)
etc...

As I understand, I should install libgstreamer0.10-dev and libgstreamer-plagins-base0.10-dev
But is it possible I read that this library is not supported anymore in Ubuntu 16.10?

$ sudo apt-get install libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev
is indeed unable to locate the package

How can I install this library in my OS?




You are not using the supported copy of Qt, but rather a personal one that was compiled against an old version of GSteamer.  You will either have to backport the old GStreamer, rebuild your version of Qt with the existing GStreamer, or simply use the Ubuntu version of Qt when rebuilding SuperCollider.  

First I would see if Ubuntu supports SuperCollider in the multiverse archive.  If not, the second best thing to do in my opinion, would be to recompile SuperCollider against the Ubuntu version of Qt - less bugs - using the Debian source code for SuperCollider (because the Ubuntu PPA is out of date).  Ubuntu comes from Debian and their source packages should - at least in theory - build cleanly.

It's easy enough to do.  Do you require help?

The other thing you can do is install an old version of Ubuntu in a chroot or VM.  Any of these will work.

---

### Post by monkeybrain20122 on 2016-10-20
gstreamer-0.1.0 has been removed from Ubuntu 16.10 repo, You can gab the .debs from xenial's repo and install them . See [here]("https://ubuntuforums.org/showthread.php?t=2340161").

> As I understand, I should install libgstreamer0.10-dev and libgstreamer-plagins-base0.10-dev

In your case you need to grab 4 debs. libgstreamer0.10, libgstreamer0.10-dev,   libgstreamer-plagins-base0.1.0, libgstreamer-plagins-base0.10-dev  since the -dev packages require the libs. Install the libs first then the -devs, or put all of them in one folder. cd into it and run ```
sudo dpkg  -i *.deb

```

---

### Post by lucedan on 2016-10-20
Thank you T.J. for your suggestions. The thing is that Qt > 5.4 has broken in SuperCollider in Ubuntu, as some shortcuts don't work.
Definitely we should update everything to the new standards, and I will try to find time maybe to work at that.
But meanwhile, it is nice to understand a few workarounds to solve imminent issues for other users as well.

---

### Post by T.J. on 2016-10-20
> **monkeybrain20122 said:**
> gstreamer-0.1.0 has been removed from Ubuntu 16.10 repo, You can gab the .debs from xenial's repo and install them . See [here]("https://ubuntuforums.org/showthread.php?t=2340161").



In your case you need to grab 4 debs. libgstreamer0.10, libgstreamer0.10-dev,   libgstreamer-plagins-base0.1.0, libgstreamer-plagins-base0.10-dev  since the -dev packages require the libs. Install the libs first then the -devs, or put all of them in one folder. cd into it and run ```
sudo dpkg  -i *.deb

```

Just for the record, that is a very bad idea.  

Not only can you cause inconsistencies in your package manager, but you could have unpredictable bugs in the 0.10 libraries even though there is some backward compatibility.  If you want to do that, you should install it in a chroot (using a tool like debootstrap) with the matching system libraries from Xenial - especially since we are talking about Qt, which is a C++ library.  C++ is far more picky than C when it comes to linking.

---

### Post by T.J. on 2016-10-20
> Thank you T.J. for your suggestions. The thing is that Qt > 5.4 has  broken in SuperCollider in Ubuntu, as some shortcuts don't work.
Definitely we should update everything to the new standards, and I will try to find time maybe to work at that.
But meanwhile, it is nice to understand a few workarounds to solve imminent issues for other users as well.

No problem.  I could lend a hand porting whatever if you need.  Let me know.

---

