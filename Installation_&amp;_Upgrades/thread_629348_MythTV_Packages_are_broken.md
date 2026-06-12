---
title: "MythTV Packages are broken"
date: 2007-12-02
forum: Installation &amp; Upgrades
---

### Post by 64mgb on 2007-12-02
This same issue was in a different thread about a month and a half ago, but that thread is closed.  I finally upgraded my MythTV box to gutsy and now I can't run or install MythTV.  I am using an AMD 64 bit processor and can't run MythTV.  Here is what I get when I try to do apt-get install mythtv:

The following packages have unmet dependencies:
  mythtv: Depends: mythtv-database (= 0.20.2-0ubuntu10) but it is not going to be installed
          Depends: mythtv-frontend (= 0.20.2-0ubuntu10) but 0.20.2+fixes14681-0ubuntu0~mythbuntu1 is to be installed
          Depends: mythtv-backend (= 0.20.2-0ubuntu10) but it is not going to be installed
E: Broken packages

Here is my sources.list file (with comments removed):

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

Can someone help me out here?  What's up with this?

Thanks,
Rich

---

### Post by 64mgb on 2007-12-02
Bump.

Any help here?  There must be something very basic wrong with my setup, but I don't know what it is.

Rich

---

### Post by 64mgb on 2007-12-02
Just in case someone else has this problem, here is how I fixed it.  I had to select various MythTV packages that were not marked as installed and select Package -> Force version and select the one for Gutsy, then mark them for installation and install them.  I don't remember what order I had to do them in, but I think I did this for mythtv-common, mythtv-database, mythtv-backend, and finally I could install the MythTV package and themes.  Now everything seems to be fine.

Rich

---

