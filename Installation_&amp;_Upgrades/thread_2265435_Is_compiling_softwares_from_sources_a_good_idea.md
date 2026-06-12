---
title: "Is compiling softwares from sources a good idea?"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by remmas-sido on 2015-02-15
For any Linux distribution, such as Ubuntu,Mint,Fedora,Centos,Opensuse  and let's say for example I'm running Ubuntu 12.04 and I'm using VLC  2.0.8 my question is can I install VLC 2.1.5 from source without any  troubles like it's not an obligatory to have the latest version of the  distro to compile the latest version of the software?

---

### Post by TheFu on 2015-02-15
> from source without any troubles
That completely depends on your skills.  Packages in the ubuntu repos do more during install than just put the program file into a directory. BTW, video programs are notorious for difficult compiles due to extremely specific dependencies.  In 1995, I compiled a bunch of programs because it was required to get anything done. Around 2000 compiling software just wasn't needed anymore for most things.

Once in a long while, there is a newer version of something that I will compile or the software doesn't have any pre-packaged version. Then I'll install it from source and keep the software under /usr/local/ so I know it wasn't packaged and so it doesn't break any other tools on the system which require the repo version of the same software.  Sometimes these newer programs will require a newer version of a core library. When that happens, I usually punt. It isn't worth destablizing my system over a new gnome or libc needed for 1 program on the box.

Installing from source complicates management in the future. Installing from source means you must manually maintain the package forever. For me, that defeats the primary reason I prefer Linux over the competition - trivial software management.  [http://blog.jdpfu.com/2015/02/08/linux-package-install-preferences](http://blog.jdpfu.com/2015/02/08/linux-package-install-preferences)  explains a few other options and considerations.

---

### Post by sudodus on 2015-02-15
The version of software in the repositories is tested (to work with that particular version of the operating system). If you want a newer version (maybe the bleeding edge version) of the software you can install it (compiled) from a PPA or download the source code and compile it. It may or may not work with your version of the operating system. Maybe it is more likely to work with a newer version of the operating system.

I think trial and error is the only way to find out what works best in each case :-)

-o-

Almost always I to use the version in the repositories, but other people have other preferences and needs.

---

### Post by oldos2er on 2015-02-15
> **remmas-sido said:**
> For any Linux distribution, such as Ubuntu,Mint,Fedora,Centos,Opensuse  and let's say for example I'm running Ubuntu 12.04 and I'm using VLC  2.0.8 my question is can I install VLC 2.1.5 from source without any  troubles like it's not an obligatory to have the latest version of the  distro to compile the latest version of the software?

If you've never compiled anything before, expect troubles, especially with a program as complex as vlc. Might be best to do what I do: look on it as a learning experience.

For distros like Ubuntu and Debian that use APT, it's possible to use ```
sudo apt-get build-dep vlc
``` which will install dependencies for you (RPM-based distros might have a similar capability, but I'm ignorant on that subject). But if vlc 2.1.5 requires any newer library files than 2.0.8 does, and those newer libraries aren't in the repositories, you'll quickly find yourself in dependency hell--having to track down, compile and install those dependencies first before compiling vlc. I don't know if that's the actual situation or not, but it's a possibility. 

Consider compiling something simpler in the meantime, maybe a nice CLI app like htop or ncdu.

---

