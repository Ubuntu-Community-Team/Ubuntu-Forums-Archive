---
title: "How to repair Update Manager?"
date: 2011-06-19
forum: Installation &amp; Upgrades
---

### Post by Dave Reynolds on 2011-06-19
I have Ubuntu 11.04 on an AMD64 machine (HP Pavilion DM1). It worked fine for a while but recently any time I try to invoke the Update Manager I get:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I have had some incidents of being unable to resume after sleep (until I disabled the catalyst driver) so possibly in one of those that file got hosed.  

Is there some way to repair this?

Dave

---

### Post by ashok.joglekar on 2011-06-19
> **Dave Reynolds said:**
> I have Ubuntu 11.04 on an AMD64 machine (HP Pavilion DM1). It worked fine for a while but recently any time I try to invoke the Update Manager I get:

```
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_natty_main_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.
E: _cache->open() failed, please report.
```

I have had some incidents of being unable to resume after sleep (until I disabled the catalyst driver) so possibly in one of those that file got hosed.  

Is there some way to repair this?

Dave
I am also having exactly same problem

Jogy

---

### Post by TheDoctorX on 2011-06-19
maybe is your connection ... try to see if it's ok... if it's ok backup your files and reinstall ubuntu ... for this things is the only real solution ...

---

### Post by dino99 on 2011-06-19
clean the system might help

sudo apt-get autoremove

or at last remove the conflicting package seen into the path

---

### Post by Dave Reynolds on 2011-06-19
TheDoctorX: Thanks for the advice. Connection is fine. Hoping not to have to do a full re-install.

dino99: Thanks, sudo apt-get autoremove just gives a similar error message and aborts.

Looking at the file it seems the update must have tried to run when I was behind a hotel paywall, the package list contains a very messed up web page with bits of hotel sign-in html screens in it :( Does apt not verify the format of the lists it fetches?

In the end tried "sudo mv /var/lib/apt/lists/*.* ~/tmp", that allowed Update Manager to run enough to download new cached package lists. Result looks promising but not sure if this is just storing up problems for the future.

Dave

---

### Post by Rubi1200 on 2011-06-19
In future, you can use these commands to deal with the problem:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

---

### Post by Dave Reynolds on 2011-06-19
> **Rubi1200 said:**
> In future, you can use these commands to deal with the problem:

```
sudo rm /var/lib/apt/lists/* -vf
sudo apt-get update
```

Thanks. Happy now I know those files can be rebuild if they missing.

Dave

---

