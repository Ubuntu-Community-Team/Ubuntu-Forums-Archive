---
title: "Running old apps on new OS 10.04 Lucid...?"
date: 2010-04-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by brucewagner on 2010-04-16
What generally happens when you try to install programs written for Ubuntu 9.04 and 9.10 on 10.04...? Will it not install? Will it not run?

---

### Post by Silent Warrior on 2010-04-16
That depends. If, for some reason, the programs are compiled against the same version of the relevant libraries present in Lucid, or said libraries are backwards-compatible, you shouldn't have serious problems. But if those libraries are API-unstable (as the terms seems to be), you'll surely run into problems. Dependencies are also a factor - package-names do change, and if the .deb you're installing is looking for a library that strictly speaking exists, but under a different name... it's inadvisable to keep trying.

---

### Post by 3rdalbum on 2010-04-16
> **brucewagner said:**
> What generally happens when you try to install programs written for Ubuntu 9.04 and 9.10 on 10.04...? Will it not install? Will it not run?

It will probably work, but it's less likely to work the other way around (using 10.04 software in 9.04). It all depends on what libraries have been used, and whether these have changed too much since last year.

Debian packages with a strict set of dependencies are also much less likely to work than "binary installers" or packages with a looser set of dependencies. If the package "depends" on libfoo-1.6.12, then you may be in trouble; if it depends on "libfoo" or ">libfoo-1.6.12" then you're more likely to have luck.

The best answer I can give you is to try your old software and see.

---

### Post by anaconda on 2010-04-16
You can also easily install old version of ubuntu to virtualbox...
and run the program there..

---

### Post by coffeecat on 2010-04-16
> **anaconda said:**
> You can also easily install old version of ubuntu to virtualbox...
and run the program there..

+1 - A case in point:

The last version of Handbrake to support Xvid and AVI was 0.9.3, but 0.9.3 doesn't run in Karmic, for which you need 0.9.4. Handbrake 0.9.4 only supports H264/MP4 (and ffmpeg) but my media player doesn't recognise H264/MP4. :sigh: So I'm running Jaunty in VirtualBox on my Karmic desktop (and will do so in Lucid) simply to be able to render AVIs in Handbrake. :rolleyes: I've tried other apps to encode AVIs - they simply don't measure up to Handbrake.

---

### Post by brucewagner on 2010-04-17
This has been very informative.  Thanks, guys!

---

### Post by ranch hand on 2010-04-17
I do not have them on my test platform now (they served their purpose) but I upgraded from clean installs of 8.04.4 (2 of them) and a copy of my old 8.04 (fully updated) to 10.04.

I had no trouble with anything I have installed on my Hardy and it is still our "main" OS (it is not used that much anymore but it is used for secure bussiness as I have it set up to be extra secure which is, frankly, a pain in the butt to use for everyday activities.

Security upgraded just as well as the apps though so I was very happy with that.

There were some small problems with the upgrade itself.  If you are thinking of doing this there are a couple things you should think about.

Wait until a little after final release to do this to make sure it is working without a hitch if this is your main OS.

Also you are going to end up on ext3 which is not optimal for 10.04.  I did do what is claimed to be an "on the fly" upgrade to ect4.  This is a waste of time if you compare it to a clean install.  It will improve with time but I still think it is a waste.

A clean install will give you a better OS.

I would check the repo for lucid and see if all your apps are there.  If so, I would install debfoster on 8.04 and have it generate the file of all installed packages and save that list to a back up.  Us it to install those packages, fresh from the lucid repo.

Have FUN.

---

### Post by brucewagner on 2010-04-17
So.....   You simply did a 

 sudo debfoster -q     ( to create the initial keepers file )

Then the file appeared as

/var/lib/debfoster/keepers


But then....  What did you do with that file?

How did you go about adding all those packages from the Lucid repositories?

Manually?

---

### Post by jkxx on 2010-04-17
To the above posters, those are good points!

One of my problems with Linux is the lack of compatibility across releases. With supplied software, your best bet is Synaptic/KPackageKit and just use the version that comes up. This is the closest to a pain-free route.

For apps I totally depend on, I generally go with a win32 app (run unmodified under Wine), some compiled java app (run unmodified under a JVM) or at worst a .NET app (run unmodified under something like Mono - you get the general idea though).

For apps to be guaranteed to run, you need something that is not tied to a current Linux distro release. Otherwise, the latest version is your best bet.

I'm still looking for a better solution to this myself, but until there is one I'll still with the above.

---

### Post by ranch hand on 2010-04-17
> **brucewagner said:**
> So.....   You simply did a 

 sudo debfoster -q     ( to create the initial keepers file )

Then the file appeared as

/var/lib/debfoster/keepers


But then....  What did you do with that file?

How did you go about adding all those packages from the Lucid repositories?

Manually?
If you have it installed the best thing to do is go to the man page;
```

man debfoster

```
I am sorry it is a long time since I used it and do not remember how it goes.  There is a way to do in automaticly if you install debfoster on your new install, I think, but just do not remember.

Of coarse you could simply run;
```

apt-get install <copy/paste entire list>

```

---

### Post by brucewagner on 2010-04-17
@ranch hand  

So if you just do an apt-get install <paste entire list> ....  It will always get the current/newest version of those apps... for the Lucid version.....  because it is using the Lucid repositories now...  

Is that the idea?

---

### Post by Longinus00 on 2010-04-17
debfoster isn't used for that. debfoster is used to remove unwanted installed packages that were only pulled in as dependencies.

Your apps will be updated so long as you got them from a repository and the repository is up to date.

---

### Post by ranch hand on 2010-04-17
> 
debfoster is a wrapper program for apt and dpkg.  When first run, it
will ask you which of the installed packages you want to keep
installed.

After that, it maintains a list of packages that you want to have
installed on your system.  It uses this list to detect packages that
have been installed only because other packages depended on them.  If
one of these dependencies changes, debfoster will take notice, and
ask if you want to remove the old package.

This helps you to maintain a clean Debian install, without old
(mainly library) packages lying around that aren't used any more.

Canonical does not provide updates for debfoster. Some updates may be provided by the Ubuntu community.

From Synaptic

Yes that is the very idea.

---

### Post by brucewagner on 2010-04-17
@Longinus00  It sounds as if that tool can be used for more that one purpose.  In this case, it can be used to simply provide you will a list of all the packages you have installed.  (This according to the documentation man pages.)

And using it to get a list of all the packages you have installed on your OLD system...  You can then install all those packages on your NEW lucid 10.04 system...  which will grab them from the new Lucid repositories.

If I am understanding correctly.  :)

---

### Post by Longinus00 on 2010-04-17
If you want a list of all installed packges and save it just use dpkg.
```
$ dpkg --get-selections > selections.txt
```
You can even use dpkg to set the packages that should be installed.
```
$ dpkg --set-selections < selections.txt
```

Doing this blindly is not a good idea, however. Just upgrade via update manager.

---

### Post by brucewagner on 2010-04-17
I'm not clear on what you mean by...

> **Longinus00 said:**
> Doing this blindly is not a good idea, however. Just upgrade via update manager.

---

### Post by Longinus00 on 2010-04-17
Because you can't just copy over the package list from hardy (or any other version) to lucid and expect it to work well. Many packages have been obsoleted and are replaced by newer ones (e.g. usplash->plymouth). I'm not sure how dpkg will handle being told to install non existent packages and I'm not sure I trust dpkgs conflict resolution.

If you're set against upgrading then you can get the description of packages installed and then trim the dpkg output down to packages you know you installed yourself and exist in lucid.

```
$ aptitude search '?and(?installed,!?automatic)'
```

---

