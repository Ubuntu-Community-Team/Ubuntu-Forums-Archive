---
title: "repos with more recent versions?"
date: 2006-09-06
forum: Installation &amp; Upgrades
---

### Post by KhaaL on 2006-09-06
Hi all

I wonder if there is some uber-secret repo that can be enabled so I can have more recent versions of the programs I use? I'm asking this because I ran into a major problem earlier today trying to install blender 2.42a on my 64bit ubuntu installation, i had to download it from [http://packages.debian.org/](http://packages.debian.org/) and thereafter I had to download *every* other package it depended (and the other packages those packages depend on, the grind!) only to find out that there was no way i could install the newer version of libsdl1.2debian since it conflicted with ubuntus version. So I ended up using the old (2.41) version of blender again, and with a lot extra unecessary packages on my system.

---

### Post by mlind on 2006-09-06
There might be 3rd party repository that provides newer version of the package. You should check if backports offers one, or request this through launchpad.net if it doesn't.
If you want to use the version that Debian offers, you need to build the source package on your Ubuntu distribution.

---

### Post by mssever on 2006-09-06
If you need the Debian version, enable the Debian source repos (I usually leave them commented out unles I need them): 
```
# Debian sources
deb-src http://http.us.debian.org/debian unstable main
deb-src http://http.us.debian.org/debian unstable non-free
deb-src http://http.us.debian.org/debian unstable contrib
``` 
Then you can get the blender source from there:
```
mkdir blender
cd blender
sudo apt-get update && apt-get source blender #assuming thats the package name
``` Then, either follow the instructions on pbuilder that mlind's signature links to (easiest, but requires more downloading and disk space), or
```
sudo apt-get install build-essential checkinstall
less *.dsc #make sure you have everything on the Build-Depends line
cd to the source directory
./configure && make
sudo checkinstall
```

---

### Post by mlind on 2006-09-06
what mssever said :mrgreen: 

If you plan to build package without pbuilder (or sbuild). I suggest to install **dpkg-dev** package and use dpkg-buildpackage instead.
```

sudo apt-get install build-essential **dpkg-dev fakeroot**
less *.dsc #make sure you have everything on the Build-Depends line
cd to the source directory
**dpkg-buildpackage -rfakeroot -us -uc**

```

---

### Post by mssever on 2006-09-06
> **mlind said:**
> dpkg-buildpackage -rfakeroot -us -uc

Thanks for the tip. I'm adding it to my aliases list (it's a little long to remember considering how infrequently I'll be using it).

---

### Post by KhaaL on 2006-09-06
thanks guys, I'll try this out and let you know how it went

---

### Post by KhaaL on 2006-09-06
while compiling with pbuilder, i got this error:

 -> Considering  debhelper (>= 5.0.37.2)
      Tried versions: 5.0.7ubuntu13
   -> Does not satisfy version, not trying

Is it complaining about the current version being too high? :|

---

### Post by mlind on 2006-09-06
> **Khalid Rashid said:**
> while compiling with pbuilder, i got this error:

 -> Considering  debhelper (>= 5.0.37.2)
      Tried versions: 5.0.7ubuntu13
   -> Does not satisfy version, not trying

Is it complaining about the current version being too high? :|

It looks like this package is updated to conform new python policy on Debian unstable.. And this is something that Dapper can't quite do, that's why debhelper is versioned so high.

I guess it's easiest to solve this by downloading Dapper's source package of blender and comparing debian/control and debian/rules files between the two releases. You'll need at least drop or remove debhelper version and remove python-support/python-central stuff.

Changelogs should provide you info about what's changed on packaging information and why. If you make a change to any of the files, you need to run *dpkg-source -b* and give source folder as a parameter, so that changes are included on the .diff.gz.

If you have trouble with this, post back and I'll try to walk you through it.

---

### Post by mssever on 2006-09-07
I remember now that I helped someone who was trying to install the same version of Blender as you. He found a .deb at [http://www.blender3d.org/forum/viewtopic.php?t=9285](http://www.blender3d.org/forum/viewtopic.php?t=9285). [Here's]("http://www.ubuntuforums.org/showthread.php?t=247698") a link to the thread where we discussed it, although I don't know how helpful it would be since Maxdark would never tell me enough so I could help him right.

The dependencies weren't so bad as using the Debian version. I believe that this deb was built for Dapper.

---

### Post by KhaaL on 2006-09-07
I tried to install the debhelper (5.0.37.3) package from [http://packages.debian.org](http://packages.debian.org), but it needed a newer version of dpkg-dev, which needed a newer version of dpkg. And I really didn't feel like taking the risk of toying with the dpkg.

@mlind 
I hate to say this, but little of the tings you're saying make much sense to me... If I download blenders source from dappers repos and compare it to debians version, what changes should I look for? :confused:  Sorry, I have some knowlege about computers, but very little about linux.


@mssever
Ah, I tried those packages long ago in hope that they'd make my life easier. However, even the amd64 optimized package is 32bit :rolleyes: why there isnt a 64bit package beats me...

---

### Post by jdong on 2006-09-07
Please, do not go into other distributions (like Edgy, Debian *, etc) installing binary packages onto your Dapper system. The never ending chain of dependencies is dpkg/apt's way of telling you that it's not supposed to work that way unless you turn your system into that distribution.

Once in a while, dpkg will not be perfect enough to stop you from installing incompatible packages, and you will render your system unbootable/unusable/seriously broken.

As others have mentioned, the correct way to get newer software is to build the package from source, or to compile the original program from source. In this case, Debian Sid packages can't be compiled because Dapper does not have new enough of debhelper. If you're daring enough, you can edit the debian/control file and strip the version requirements off debhelper and see if it'll build, but most likely you are going to be compiling the package without the help of debian tools, then installing it into /usr/local or (FHS anal-retentives, look away!) /opt.

---

### Post by mlind on 2006-09-08
> **Khalid Rashid said:**
> I tried to install the debhelper (5.0.37.3) package from [http://packages.debian.org](http://packages.debian.org), but it needed a newer version of dpkg-dev, which needed a newer version of dpkg. And I really didn't feel like taking the risk of toying with the dpkg.


debhelper and dpkg-dev are one of those packages that you shouldn't manually upgrade yourself.. And avoid installing foreign binary packages, those may break your entire system, but do it like jdong said, modify debian/control.


> **Khalid Rashid said:**
> 
@mlind 
I hate to say this, but little of the tings you're saying make much sense to me... If I download blenders source from dappers repos and compare it to debians version, what changes should I look for? :confused:  Sorry, I have some knowlege about computers, but very little about linux.


You should be looking changes of files in debian folder. But this is no easy task if you haven't got prior experience about the subject. I'll check out this later and see if it's worth the effort.

---

