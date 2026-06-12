---
title: "How to install updates without upgrading?"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by Roque on 2006-10-29
I cannot install Edgy at all. The md5sum of the burned .iso is perfect, but the installation hangs all the time. I installed ALL the previous releases Hoary, Breezy, Dapper, etc. in this machine (never changed a single hardware component) without ANY problem at all. 

Now I have tried all kind of combinations: clean install; installing a command line system and then adding with apt-cdrom; dist-upgrading from Dapper, from Breezy, etc. Nothing worked.

So here's the question: I want to keep my system up-to-date with regard to specific components, without ever having to go through these annoying, time consuming and error prone full upgrade attempts again. Eg.: why upgrade the kernel when I only want the latest Amarok version? In other words, I want (eg. next year) to write in my (then two years old) Breezy console: 

apt-get amarok 

and it will download the latest up-to-date version of Amarok (and all the required libraries) and install them without a glitch.

Is this possible?

---

### Post by JW_00000 on 2006-10-29
One possibility is to download Amarok from its official site. [http://amarok.kde.org/wiki/Download](http://amarok.kde.org/wiki/Download) lists a range of options, and you can always download a .deb file for Debian and install it on your Ubuntu system (using dpkg -i filename.deb), or an .rpm package (for example one for Fedora) and convert it with the alien command (alien filename.rpm and then dpkg -i filename.deb), or you can build the application from source (the Amarok wiki has detailed instructions on that).
It seems like you will be able to continue doing this for some time, however, Amarok 2.0 will depend on KDE 4 (planned for release somewhere in 2007), for which you will probably have to install the latest version of Kubuntu (or the latest kdelibs at least).

As a side note, if you don't like upgrading your system, you may consider a distribution like [Gentoo]("http://www.gentoo.org"). Gentoo doesn't release major versions, all applications are always updated from the repositories (portage), which I think keeps supporting older version (for at least some time).

---

### Post by mgolden on 2006-10-29
> **Roque said:**
> So here's the question: I want to keep my system up-to-date with regard to specific components, without ever having to go through these annoying, time consuming and error prone full upgrade attempts again. Eg.: why upgrade the kernel when I only want the latest Amarok version? In other words, I want (eg. next year) to write in my (then two years old) Breezy console: 

apt-get amarok 

and it will download the latest up-to-date version of Amarok (and all the required libraries) and install them without a glitch.

Is this possible?

I had no problems upgrading to Edgy, but even before that I was getting the new versions of KDE via the method described here):

[http://kubuntu.org/announcements/kde-355.php](http://kubuntu.org/announcements/kde-355.php)

I don't know if it'll work for Breezy.

---

### Post by Roque on 2006-10-29
Thanks for your help.

I know that you can do what you wrote, but of course dpkg doesn't manage the dependencies and you must do it "by hand". Sometimes there are hundreds of packages in the dependence tree and it gets quite tedious to work with.

Didn't know that about Gentoo. It makes a lot of sense: why copying the artificial, marketing-driven release model of traditional, closed source software companies when APT-type tools provide the ability to update your installation in a smooth and continuous, every day process of controllable small steps?  

It's a pity. I like Ubuntu a lot but sticking to these hard releases is an unnecesary constraint. WIll probably move to Gentoo to investigate in depth. 

Really great advice! Thanks again.

---

### Post by Roque on 2006-10-29
I just tried Gentoo. The installer is ridiculously convoluted, and the instructions are badly written. Many architectures are unsuported. Linux is going the wrong path again...

---

### Post by nimrod_abing on 2006-10-29
> **Roque said:**
> I cannot install Edgy at all. The md5sum of the burned .iso is perfect, but the installation hangs all the time. I installed ALL the previous releases Hoary, Breezy, Dapper, etc. in this machine (never changed a single hardware component) without ANY problem at all. 

Now I have tried all kind of combinations: clean install; installing a command line system and then adding with apt-cdrom; dist-upgrading from Dapper, from Breezy, etc. Nothing worked.

So here's the question: I want to keep my system up-to-date with regard to specific components, without ever having to go through these annoying, time consuming and error prone full upgrade attempts again. Eg.: why upgrade the kernel when I only want the latest Amarok version? In other words, I want (eg. next year) to write in my (then two years old) Breezy console: 

apt-get amarok 

and it will download the latest up-to-date version of Amarok (and all the required libraries) and install them without a glitch.

Is this possible?

Yes it is. But you will have to build the newer packages from source using dpkg-dev tools and maintain your own local repository. (see Edit below) It's not that hard and there are many tutorials on the web if you search for them. I suggest you start at the Debian website and look for the Debian Package Maintainer's Guide. It's a bit of a long read but it's really worth it.

To the poster who recommended you switch to Gentoo, shame on you :).

To get you started here is what you do:

```
sudo apt-get install build-essential dpkg-dev
```

This will install the basic tools that you will need to build packages from source (gcc, binutils, etc). Then for the package that you wish to build from source go do:

```
sudo apt-get build-dep <package-name>
```

This will install all the **build-time** dependencies for the package (e.g., header files, link libraries). Once you have them, you can download the source package of the **current version** of the package:

```
apt-get source <package-name>
```

This will get at least 3 files from the repository:

1 file ending with .orig.tar.gz or .zip or .bz2 - this is the original/upstream sources
1 file ending with .diff.gz - this contains the patches for the control files for the build system.
1 file ending with .dsc - this is the control file for the Debian packager

Once you have all the necessary files, do:

```
dpkg-source -x <package-name>.dsc
```

This will extract the package source to a directory and apply the .diff.gz. to provide a complete Debian build package.  Then you can change to the directory where the source package is unpacked and do:

```
dpkg-buildpackage -tc -uc -us -rfakeroot
```

If the package was properly done by its maintainer, it should build without problems. Otherwise you will get an error like this:

```
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 2.40-1
dpkg-checkbuilddeps: Unmet build dependencies: ftgl-dev libglut-dev libsdl-dev
dpkg-buildpackage: Build dependencies/conflicts unsatisfied; aborting.
dpkg-buildpackage: (Use -d flag to override.)

```

In this case, I am missing ftgl-dev, libglut-dev, libsdl-dev. So I need to install those to satisfy the build time dependencies. A side note with build-time dependencies: if you are short on disk space, you can remove them when you are done building the package.

When the package is done building, it will have left you with a .deb file in the directory above the source directory. You can install that with:

```
dpkg -i <package_name>.deb
```

But wait! You wanted to have the latest and greatest amarok. There are two ways of going about with this.

First, you can go to [http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/](http://archive.ubuntu.com/ubuntu/pool/main/a/amarok/) and download all the files needed to build the latest version. You will need the *.dsc, *.diff.gz and the *.orig.tar.gz file for the version you want to build. Once you have them, you can extract the source and build it as above.

Alternatively, you can download from mainstream (the main Amarok website) once you have the latest tarball, copy it to the directory where dpkg-source unpacked the **old version**. Change to the directory of the **old version** and do:

```
 uupdate <package_name>-<version>.tar.gz
```

This is usually tricky as there are times when the .diff.gz will **not** apply cleanly to the upstream source and you need to resolve this by hand. If you do not know what to do in case of uupdate failing, then you are better off downloading the official Ubuntu source archives.

If uupdate proceeds cleanly, it will tell you what to do next. At this point you can build the package and install it with dpkg -i.

As for maintaining your own repository, there are tutorials for that too. Start in the Debian website docs. Everything you need is there, you just have to look for it.

[COLOR=SeaGreen]EDIT: You can also try "pinning" packages to a specific version, but in my experience this creates a lot more dependancy problems than building from source:

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

[/COLOR]

---

### Post by Roque on 2006-10-29
Thank you a lot Nimrod. I appreciate your consideration to write such detailed instructions!

I am now slowly installing Edgy by hand. I'll examine your post in detail later. Meanwhile at least, it's good to know that an "update without upgrade" can be done.

---

### Post by Roque on 2006-10-30
Nimrod, 

I restarted from scratch again. I am following your method:

1) Installed Breezy, 
2) Changed all "Breezy" to "Edgy" in my sources.lst
3) sudo apt-get update
4) sudo apt-get install build-essential dpkg-dev
5) sudo apt-get build-dep amarok

E: Build-dependencies for amarok could not be satisfied

If I change back "Edgy" to "Breezy" then everything goes fine of course, but it can't find amarok 1.4.3 (Edgy's) and installs 1.3.2 (Breezy's) in its place. Any ideas?

---

