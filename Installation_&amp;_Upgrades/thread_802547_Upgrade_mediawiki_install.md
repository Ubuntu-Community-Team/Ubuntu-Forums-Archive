---
title: "Upgrade mediawiki install"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by archgriffin on 2008-05-21
Perhaps I just have not been able to word my searching correctly, but I can not find any simple answer on how to upgrade a current mediawiki install. Such as, we have 1.7 installed (through apt-get), how would I just tell it to upgrade to 1.10 (or other current version in Ubuntu repository). I can just install another version but then I have to manually migrate the data over. 

Is there a simple way for this? I apologize if I am missing a fundamentally simple thing here.

The system in use/question is:
Ubuntu 8.04 Server (x86)

---

### Post by zvacet on 2008-05-21
Do you have these lines in your source list 

>  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


If you do just

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by archgriffin on 2008-05-22
Thank you for your suggestion!

I was missing just these two lines:

> deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hardy universe multiverse

With those in I ran the update/upgrade. It upgrade apache, some libs, php5, some other things, but it did not upgrade the mediawiki to a newer version.

---

### Post by Tommy on 2008-05-22
> **archgriffin said:**
> It upgrade apache, some libs, php5, some other things, but it did not upgrade the mediawiki to a newer version.

Have you checked to see what apt thinks is installed now?

You can try 

```
dpkg -s mediawiki | less
```(there may be a better command... but toward the top dpkg will say what version is installed. I added less because it usually spews a lot of other stuff too.)

IF it turns out you already HAVE the latest package installed using apt --  [http://packages.ubuntu.com/hardy/mediawiki](http://packages.ubuntu.com/hardy/mediawiki) says 1:1.11.2 is the version in hardy -- then you may need to complete the upgrade to your data using instructions similar to [http://www.mediawiki.org/wiki/Manual:Upgrading](http://www.mediawiki.org/wiki/Manual:Upgrading)

(As you can see, there's a newer version at mediawiki, so if there's a feature you need in the latest, you may need to give up on using apt and go the manual route.)

---

### Post by archgriffin on 2008-05-22
This mediawiki was installed with 
```
apt-get install mediawiki1.7.
``` 
This was the current version at the time of install. Obviously, it's been a while. I would like to avoid manualling upgrading though if it is the only option then that is what I will do. I was just hoping apt would ease my pain for me, partly because I thought that was it's purpose. 



```

$ dpkg --get-selections | grep mediawiki
mediawiki1.7                                    install
mediawiki1.7-math                               install


$ dpkg -s mediawiki | less
Package `mediawiki' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.


$ dpkg --info mediawiki
dpkg-deb: failed to read archive `mediawiki': No such file or directory

Same happens with dpkg-deb --info

```

---

### Post by zvacet on 2008-05-22
It is little bit strange that package is not upgraded since it is in universe repository.Take a look [here.]("http://packages.ubuntu.com/search?keywords=mediawiki&searchon=names&suite=hardy&section=all")

---

### Post by Tommy on 2008-05-22
> **archgriffin said:**
> This mediawiki was installed with 
```
apt-get install mediawiki1.7.
```This was the current version at the time of install. 

AHA! so the command would be

```
dpkg --info mediawiki1.7
```

or

```
dpkg -s mediawiki1.7
```

THAT is why it's not going to upgrade. The package is probably "fixed" at a particular version number, and it probably is not automatically upgradeable.

I would back everything up -- as per the instructions at the mediawiki link above, then tinker with the upgrade.

There may be special upgrade instructions in a README file that gets installed with the mediawiki package -- most of the time those things end up in /usr/share/doc/packagename  -- look for a /usr/share/doc/mediawiki directory.

IMPORTANT -- I have not installed the ubuntu package myself, nor have I tried an upgrade on Ubuntu -- so far on my server I've managed mediawiki the "old fashioned way" as described at the mediawiki links. It will be really COOL if apt can handle the upgrade to the new version automatically -- that's what it's for!

After you've studied it, you MIGHT be able to just install the new mediawiki package -- if it's done right it may "just work." But be sure to have a good backup just in case....

---

### Post by archgriffin on 2008-05-28
> IMPORTANT -- I have not installed the ubuntu package myself, nor have I tried an upgrade on Ubuntu -- so far on my server I've managed mediawiki the "old fashioned way" as described at the mediawiki links. It will be really COOL if apt can handle the upgrade to the new version automatically -- that's what it's for!

Well, that last bit is what I was hoping for too, but oh well. I guess it's just a manual upgrade, or apt installing the newest version and manually converting the data over to it.

Thanks for the replies, and sorry it took so long to finish up the thread.

---

### Post by Tommy on 2008-05-28
> **archgriffin said:**
> Thanks for the replies, and sorry it took so long to finish up the thread.
maybe it's just me, but it seems like a lot of the more puzzling threads just hang forever, with the resolution unknown... 

I would really like to know how YOUR situation works out, however, so if you do find that one can upgrade mediawiki using the package manager, please update the thread!

P.S.: I was just looking through the package page at [http://packages.ubuntu.com/hardy/mediawiki](http://packages.ubuntu.com/hardy/mediawiki) to see if there were any clues about the upgrades, and in the list of bugs, it looked like there are some filed -- especially if you're using postgresql. I was going to suggest you could write to the person who packaged it, but launchpad discourages that, giving some other options.

If you have a spare system sitting around you could copy your existing mediawiki setup to it and try doing an aptitude install mediawiki -- apt should detect the existing package and either upgrade it OR make you uninstall and reinstall. I suspect there will be some manual cleanup to do, but maybe it will mostly "just work."

You could test the same thing on your live system if you are very confident about the integrity of your backups, and your ability to restore one!

---

