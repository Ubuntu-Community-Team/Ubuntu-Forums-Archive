---
title: "Ubuntu from SCRATCH"
date: 2005-10-26
forum: Installation &amp; Upgrades
---

### Post by JOKe on 2005-10-26
hello can i build ubuntu from scratch ? is there any project like DFS or LFS for Ubuntu  ? becouse im with Athlon 1700+ and i and many people in my country we want i686 version , when this is not possible to be done by ubuntu team we need to build our own but there is no project Ubuntu from Scratch and we still use DFS.


or how can i rebuild my installed ubuntu system to be a i686 ?

---

### Post by Jenda on 2005-10-26
> or how can i rebuild my installed ubuntu system to be a i686 ?
I'm quite sure this is possible. Look around - I'm no help.

---

### Post by JOKe on 2005-10-26
anyone else know somethink ?

---

### Post by MetalMusicAddict on 2005-10-26
I would like to know also.

---

### Post by JOKe on 2005-10-26
i think nobody know :+)  :+((

---

### Post by Jenda on 2005-10-26
I'll look around...

---

### Post by JOKe on 2005-10-27
in distros like debian or bsd`s like freebsd/openbsd and etc there is a command for Rebuilding EVERYTHINK :) with some optiomisation if there is no such tool in debian/ubuntu/or some other deb distro it will be nice to make one :) .

i`m speaking for some tool like "ReBuild the hole system for me with march=i686" the tool must see what is installed ( use apt-cache ) download all sources ( from deb-src urls present in source.lst ) and make apt-build or other command for all of them .. 

will be nice if there is somebody with good knowage for bash scripting to make script like this ( if there is no program like this yet ).

---

### Post by Jenda on 2005-10-27
[EDIT]This is not factually correct - I left the contents for completeness' sake[/EDIT]
JOKe:
I asked around. And I found this: (source: nalioth)

There is an i686 kernel out there. Use that and you're all set. You can install it through synaptic. or
```
sudo apt-get install linux-686
```

---

### Post by MetalMusicAddict on 2005-10-27
[QUOTE=Jenda]JOKe:
I asked around. And I found this: (source: nalioth)

There is an i686 kernel out there. Use that and you're all set. You can install it through synaptic. or
```
sudo apt-get install linux-686
```[/QUOTE]
Sorry dude thats not the same thing. :) This thread is looking for a way to compile *everything* for i686. Not just the Kernel.

---

### Post by Jenda on 2005-10-27
Indeed... I was a little suspicious.
I don't know, in that case. nalioth (#ubuntu @ freenode) said this was all that was needed.

---

### Post by Curufir on 2005-10-27
[http://julien.danjou.info/article-apt-build.html](http://julien.danjou.info/article-apt-build.html)

Adjust for Ubuntu. Good luck

---

### Post by JOKe on 2005-10-28
[QUOTE=Jenda]Indeed... I was a little suspicious.
I don't know, in that case. nalioth (#ubuntu @ freenode) said this was all that was needed.[/QUOTE]
yes i have installed linux-i686 ( k7 ) version of the kernel but i want to rebuild the hole system ( i mean for i686 Xorg and i686 gnome packages and etc i will check the aptbuild howto in a sec. )

---

### Post by riggsd on 2005-10-28
```
riggs@ubuntu:~ $ [COLOR="Red"]apt-cache show apt-build[/COLOR]
Package: apt-build
Priority: optional
Section: universe/devel
Installed-Size: 176
Maintainer: Julien Danjou <acid@debian.org>
Architecture: i386
Version: 0.12.9
Depends: perl, apt (>= 0.5), gcc, g++, dpkg-dev (>= 1.9), libappconfig-perl (>= 1.5), libapt-pkg-perl (>= 0.1.11), debconf, devscripts, apt-utils
Recommends: fakeroot, build-essential
Conflicts: pentium-builder
Filename: pool/universe/a/apt-build/apt-build_0.12.9_i386.deb
Size: 31324
MD5sum: ebfc5635b851b0b45ce4f4be224a9f0f
Description: frontend to apt to build, optimize and install packages
 This is an apt-get front-end for compiling software optimized
 for your architecture by creating a local repository with built packages.
 It can manage system upgrades too.
Bugs: mailto:ubuntu-users@lists.ubuntu.com
Origin: Ubuntu

```

---

### Post by grexk on 2006-06-20
I will be trying this one I'll just inform you for my success.

---

### Post by brandt on 2006-06-22
I took a look at the tutorial, but the current version of apt-build doesn't seem to work exactly the same.  If I put march= -march=<my proc> or mcpu = -mcpu=<my proc> I get an error saying apt-build doesn't have those variables.  Does anyone know more about using apt-build?  I can't seem to find that many resources on it.  I'd also like to know how to set which compiler is uses because I have distcc installed and hopefully using that would come in handy for this.

---

### Post by weisunding on 2006-12-28
Sure we can, but we need the debootstrap package

root@debian ~# mkdir /root/chroot_env
root@debian ~# debootstrap dapper /root/chroot_env [http://cn.archive.ubuntu.com/ubuntu/](http://cn.archive.ubuntu.com/ubuntu/)
I: Retrieving Release
I: Retrieving Packages
I: Validating Packages
I: Resolving dependencies of required packages...
I: Resolving dependencies of base packages...
I: Found additional required dependencies: libtext-iconv-perl zlib1g
I: Checking component main on [http://debian.cn99.com/debian](http://debian.cn99.com/debian)...
I: Retrieving adduser
I: Validating adduser
I: Retrieving apt
I: Validating apt
....
I: Installing core packages...
I: Unpacking required packages...
I: Configuring required packages...
I: Installing base packages...
I: Base system installed successfully.
root@debian ~#

Now, we can chroot into the new system

root@debian ~# chroot /root/chroot_env
root@debian /# ls
bin dev home lib mnt proc sbin sys usr
boot etc initrd media opt root srv tmp var
root@debian /# apt-get clean
root@debian /# du -sh
111M .

---

