---
title: "anyone else tried to install beta from *.iso?"
date: 2009-10-02
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by gexi on 2009-10-02
hmm, so i downloaded  the **desktop-i386.iso** today, joyously planning to finally make a fresh and clean install. well. live-cd worked, i even checked its integrety. but install-process always crashed when it was about to partition my harddisk. didn’t matter if i installed out of the live-de or directly.

anyone else had this problem?

---

### Post by MTGap on 2009-10-02
Try formating the disk off the livecd and then try to install with the livecd.

---

### Post by NormanFLinux on 2009-10-02
If you kept current with updates to Alpha6, you already have the beta.

---

### Post by MTGap on 2009-10-02
Yes but do realize, that if you do a completely new install you will actually get some new packages and configuration. Grub2 wasn't installed unless you did it manually and there were changes to xserver I believe which screwed over my old setup.

---

### Post by gexi on 2009-10-02
> **NormanFLinux said:**
> If you kept current with updates to Alpha6, you already have the beta.

i know.

---

### Post by gexi on 2009-10-02
well, thanks i'm gonna try that tomorrow. and i'm gonna file a bug if there hasn't been anything similar posted yet. it's late now. i'm sleepy. :)

---

### Post by markbuntu on 2009-10-02
I had no problems myself installing the beta from iso. In fact it was the first Karmic iso that actually worked for me.

---

### Post by kansasnoob on 2009-10-02
> **gexi said:**
> hmm, so i downloaded  the **desktop-i386.iso** today, joyously planning to finally make a fresh and clean install. well. live-cd worked, i even checked its integrety. but install-process always crashed when it was about to partition my harddisk. didn’t matter if i installed out of the live-de or directly.

anyone else had this problem?

Would it be possible for you to post a screenshot of gparted and the output from terminal of:

```
sudo fdisk -l
```

I've done 8 installs of the Beta on nearly identical hardware and had no problem with partitioning.

---

### Post by talkingwires on 2009-10-02
> **MTGap said:**
> Yes but do realize, that if you do a completely new install you will actually get some new packages and configuration. Grub2 wasn't installed unless you did it manually and there were changes to xserver I believe which screwed over my old setup.I'm downloading the Beta ISO now because X/GDM has been borked for two weeks on my machine. I have to boot into the recovery console, kill GDM manually, then start X. I haven't seen anybody else complaining about this, so some package must've failed to update everything it was supposed to on my machine.

For those of you coming into this thread to say, "just dist-upgrade and you're running the latest alpha/beta/whatever", that's only true to an extent. I dist-upgraded one of my machines daily from Warty to Gutsy (three years, or six releases) before I wiped it and did a fresh install. And lemme tell ya, there's a lot to be said for doing a fresh install.

---

### Post by rturner on 2009-10-02
I had the exact same problem trying to do a clean install;  it stopped after starting the partitioning.  I'll mess around with it some more tomorrow.

---

### Post by Nobby on 2009-10-02
I've encountered the same problem too.  I thought it might have been a bad cd burn, but second disc produced same results.  Once I click the Ok on the last step, the partitioner starts but then disappears an instant later.  The progress bar gets to about 1% or 2%.  I choose to do a manual partition (keeping my home partition in tact).

Someone has entered this as a bug: [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/440922](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/440922)

---

### Post by Bert Mariën on 2009-10-03
I did not install the beta myself (updated from an installation a week ago) but I got a mail from the devs today with this message:

Hi folks,

the karmic changes in the toolchain (gcc-4.4, newer eglibc) have sadly 
produced a lot of fallout: The number of packages that failed to build during 
the latest rebuild test is enourmous. You can see the list at

<http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20090909-karmic.html>

---

### Post by Bert Mariën on 2009-10-03
I better let you in on the complete email:

Hi folks,

the karmic changes in the toolchain (gcc-4.4, newer eglibc) have sadly 
produced a lot of fallout: The number of packages that failed to build during 
the latest rebuild test is enourmous. You can see the list at

<http://people.ubuntuwire.org/~wgrant/rebuild-ftbfs-test/test-rebuild-20090909-karmic.html>

The list is refreshed every two hours, marking uploaded packages in the 
superseded section.

Please help fixing these, and please also forward your changes to Debian.

A large number of issues can be dealt with easily. The most prominent ones 
are:

* C++ packages failing due to the new (ISO compliant) definitions of c string
  methods. In C, these functions receive a const char * and return a char *,
  hence allowing an implicit const-cast.
  g++-4.4 together with our new eglibc have overloaded counterparts, which
  - either use a char * as argument and return a char *
  - or use a const char * as argument and return a const char *.
  Often the solution is to simply add a const somewhere.

* Local definitions of getline: While getline used to be a GNU extension, it's
  nowadays part of POSIX, living in <stdio.h>. Sadly getline is quite a common
  name, and is defined in a number of packages.
  The solution here is likewise simple: Just rename the definition in the
  package.


Martin Michlmayr did a rebuild of unstable against gcc-4.4 (using an older 
eglibc than we have though), so a number of failures might already have 
patches sitting in BTS or are already fixed in unstable.
You can find the complete list of gcc-4.4 related bug reports from the 
unstable rebuild at

<http://bugs.debian.org/cgi-bin/pkgreport.cgi?users=debian-gcc@lists.debian.org;tag=ftbfs-gcc-4.4>

Please also take a look at the sponsors queues 

for main:
<https://bugs.launchpad.net/~ubuntu-main-sponsors/+subscribedbugs>
and for universe:
<https://bugs.launchpad.net/~ubuntu-universe-sponsors/+subscribedbugs>

and preferrably sponsor bugs fixing FTBFS issues.

Cheers,
   Stefan - on behalf of motu-release.

---

