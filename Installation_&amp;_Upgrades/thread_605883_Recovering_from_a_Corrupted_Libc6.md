---
title: "Recovering from a Corrupted Libc6"
date: 2007-11-07
forum: Installation &amp; Upgrades
---

### Post by rescdsk on 2007-11-07
Today I had a fun experience with libc6.  During a routine upgrade, apt downloaded a corrupted copy of the libc6 package.  Right before it tried to install it, it noticed that it was corrupt... but then installed it anyway!  It seemed to hang partway through unpacking it, or possibly right after unpacking it.  Anyway, at that point, no program would run on my system, they all segfaulted, including init and /bin/sh, when I rebooted.  O noes!

What follows is how I restored my system, in the hopes that it might be useful to someone.  If there's a better way of doing this, please say so!  Also, if this is a dumb place to post this, please tell me a better place.

Well, obviously, the right thing to do is to reboot from a live-CD and reinstall the package, right?  Sure.  You would normally:
1. boot from the live CD
2. mount your filesystem tree under, say, /target
3. download the package from the internet and then run a command like this:

```
dpkg --root=/target -i /path/to/libc6_2.6.1-ubuntu10-amd64.deb
```

Oops!  What that does is chroot to /target (your system) to run any maintainer scripts (look in /var/lib/dpkg/info/ to see a maintainer script).  But any command run with the libraries available under /target will segfault!  Darn!  So basically, the above procedure will work for most packages other than libc6 and some of the basic utilities.

Now normally you should always run the maintainer scripts (it's usually done automatically by dpkg whenever you install or remove anything).  But I looked at the preinst script for libc6 and decided I could do without it just this once.  That way, I wouldn't have to run any commands in /target.  Unfortunately, I couldn't find an option for dpkg not to run them, so I had to get into the package myself.

Debian and Ubuntu packages are really archives made by the ar(1) program, which is sorta like the more familiar tar.  The ar(1) archive contains two files, data.tar.gz and control.tar.gz.  data.tar.gz contains the actual files that the package is going to install, and control.tar.gz contains the maintainer scripts, the list of configuration files, and so on.  So I did what dpkg would normally do to extract all the files contained in the package:

```
$ ar x libc6_2.6.1-ubuntu10-amd64.deb
$ ls
control.tar.gz    data.tar.gz
$ cd /target
$ tar xzf /path/to/data.tar.gz
```

So now all the files from libc6 are installed in /target, which is my normal system.  NOTE that this will probably OVERWRITE ALL THE CONFIGURATION FILES from that package.  I was desperate, so I decided I didn't care.  I don't really know what ldconfig does, but it seemed vaguely important, so I ran it before I continued (you may not have to do this):

```
$ chroot /target ldconfig
```

Now that all of the libraries in /target were non-corrupt, I was able to run dpkg without a hitch.  I needed to run dpkg again because not only does it extract the files, but it also keeps track of what packages have been installed, and whether they're broken, so it's important to let dpkg in on the act:

```
dpkg --root=/target -i /path/to/libc6_2.6.1ubuntu10-amd64.deb
```

Now try rebooting and maybe everything will work again (it did for me).

Now the system is both working and in a consistent state but there is [COLOR="Red"]ONE MORE REALLY IMPORTANT THING TO DO[/COLOR]:

You must delete the corrupted copy of the package from the archives, so that apt doesn't try to install it again!  I forgot to do this, so I had to go through the above procedure twice.  To remove it, look in /var/cache/apt/archives for the package file that caused the problem.  If you don't know how to tell which one messed up the system, it's safe to delete them all:

```
apt-get clean
```

OK!  Now, it may be needed, once you've rebooted, to put the packaging system back in order a little bit by running ```
apt-get -f install
``` (the -f is for fix).

Well, hope this helps someone!
Love,
tgs at dontspam dot resc dot net

---

### Post by rescdsk on 2007-11-07
One more thing:  to find a copy of a package file online, look under:

[http://archive.ubuntu.com/ubuntu/pool/](http://archive.ubuntu.com/ubuntu/pool/)

Most important packages will be in the main subdirectory, then they are organized by the letter that their SOURCE PACKAGE starts with (i.e. the libc6 binary package comes from the glibc source package, so you'd look under g).  The source package name is often, but not always, the same as the binary package name.  If it's not, you could try searching for the binary package name at [https://launchpad.net/ubuntu](https://launchpad.net/ubuntu) .

---

