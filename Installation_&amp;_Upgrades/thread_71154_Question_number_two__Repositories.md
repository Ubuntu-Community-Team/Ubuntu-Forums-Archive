---
title: "Question number two:  Repositories"
date: 2005-10-02
forum: Installation &amp; Upgrades
---

### Post by augereffect on 2005-10-02
I'm following the directions in the ubuntuguide, and it tells me to add new repositories in order to get a bunch of the packages.  It tells me to replace a piece of sources.list, but when I do, I keep getting error messages.  Synaptic doesn't like it and apt-get doesn't like it.  It gives me this mess whenever I start synaptic:

: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_hoary-updates_restricted_binary-i386_Packages)

I also tried manually unticking the urls in the sources file.  Same problem.  How do I add the repositories I need to install the stuff on ubuntuguide?

---

### Post by JimmyBEng on 2005-10-02
as the error says you have the hoary-updates main and restricted repositories listed twice in your sources.list so open it and find the duplicate entries and delete them.  Or here is a sources.list set up to work with the ubuntuguide, it is the one i use.
```
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted

```

---

### Post by emperor on 2005-10-02
I found that the backport repo's need to be commented out right since there are no packages in backports right now. All backports for Hoary have been merged with the main repo's. There apparently will be no new backported packages until breezy is released.

---

### Post by TristanMike on 2005-10-02
Instead of using the sources.list from ubuntuguide, try using the sources.list from [here.](http://paste.ubuntulinux.nl/969). In my opinon, they are much nicer, of course, you'll still have to "uncomment" some of them here, it's just a very nice default sources.list.
Hope this helps.

---

### Post by Brando569 on 2005-10-02
i keep getting this error after i run apt-get update and dunno how to fix it

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

