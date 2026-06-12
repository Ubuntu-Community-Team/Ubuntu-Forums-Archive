---
title: "Is there any guidance for bypassing package management?"
date: 2009-11-23
forum: Installation &amp; Upgrades
---

### Post by aajax on 2009-11-23
One of the great things about Ubuntu is that inherits a pretty sophisticated package management system from DEBIAN.  However, there are times when I want to use software that has not been packaged.  A typical example is wanting to use a newer release of something that is contained within Ubuntu repositories.  Another of course involves using something that just isn't included in Ubuntu.

Is there any guidance (best practice) that has been documented for how best to go about it?

---

### Post by Cheesemill on 2009-11-23
If you want a newer version of software that comes with Ubuntu, there's a good chance you can still use the package management by adding a new repository to your sources.

This way the software will remain up to date whenever you perform a system update.

As an example to get the latest version of deluge you could just do the following:

```
sudo add-apt-repository ppa:deluge-team/ppa
sudo apt-get update
sudo apt-get install deluge
```This would install the latest version (1.2.0) instead of the version that comes with Ubuntu (1.1.9).

PPA's can be found here: [https://launchpad.net/ubuntu/](https://launchpad.net/ubuntu/)

There are obviously other ways to get later versions, manual .deb download, install from source, etc. But this way you don't have to keep manually checking for updates.

EDIT - Another good repository to use is the one provided by [GetDeb]("http://www.getdeb.net"), it provides software such as Songbird, FileZilla, Transmission.......

EDIT 2 - If you aren't using the latest version of Ubuntu you can also look at the Ubuntu Backports project. This will let you install the Karmic version of some software on Jaunty for example.
[https://help.ubuntu.com/community/UbuntuBackports](https://help.ubuntu.com/community/UbuntuBackports)

---

### Post by lykwydchykyn on 2009-11-23
A few of tips:

 - If it's in the repos and you just want to get a newer version, add a source repository for the next version up and use apt-src.  This allows you to still use the package manager, and get the default Ubuntu configurations and so forth, but you get a newer version compiled for your release.

In other words, I could add a Lucid source (and ONLY source, no binary) to my Karmic install, then use apt-src to download and build newer sources.

 - If it's not in the repositories, or you have the latest upstream source (newer than in the current unstable release), use checkinstall instead of make/makeinstall.  This will generate a deb file.

 - If it's not source that you compile, but just static binaries or similar, put it in /opt.

---

### Post by Backharlow on 2009-11-23
I can't send you to any specific documentation for this but I can give you some basic background on it and what I do.

Software outside of Ubuntu comes in 3 forms: packaged, unpackaged binary, or unpackaged source.

If the dev offers a .deb debian package for download you can easily install this using your Ubuntu packaging system. When you do this, Ubuntu will find any dependencies needed, for the foreign packaged from its own archive, and this almost always works.

Now, if they only offer a .deb but no software repository to add to your packaging system that means you are stuck with just that version they offer for manual download. I've been doing it this way for Blender from blender.org for a couple years.

If they do offer a debian-style repo, go ahead and do as instructed by adding their repo address to your Software Sources tool.

If you install a new repo that contains a package that also has a version (probably older) in the Ubuntu repos, Synaptic package manager will allow you to "Force versions" on that package so you can clearly choose of the two or more sources you want to get that package from.

Now, that said, you can use any .deb package, which includes stuff from Debian itself, however it isn't good practice since Ubuntu is already a migration from Debian. But I have found that for little things that are fairly standalone and not a big library that other stuff is dependent on, its perfectly find to do that.

If they don't offer a .deb but offer some other pacakge, use that other package and process it into a .deb with alien.

If it is unpackaged try to find a binary version that corresponds to your cpu architecture and get that version.

If it is unpackeged but source you'll need to compile it. For this use instructions from that dev.
What I do with unpackaged apps; I just have a directory in my home called apps. inside this each unpackeged app gets its own directory, and then I just add the paths to the executables in my Gnome menu. Of cource this is a one user configuration, but it works, and keeps a clear separation between the filesystem from packages and the fileystem from me experimenting. To keep this, be sure when you compile just do make, not make install after, that way the compiled binaries stay where they are. Apps in some random place where you want them to live as just folders like this will still generally "find one their own" whatever dependencies they need, assuming you have already installed them via package manager.

Often times (and this is getting increasingly more available),

---

