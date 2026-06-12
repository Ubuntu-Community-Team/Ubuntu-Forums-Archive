---
title: "Ardour missing a dependancy"
date: 2008-09-23
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Tatty on 2008-09-23
Ardour in Ibex is currently uninstallable due to a dependency not being met:

```
$ sudo apt-get install ardour
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
  ardour: Depends: liblo0 (>= 0.23) but it is not installable
E: Broken packages
```

Is the correct procedure now to file a sync request against liblo0 as explained on this page [https://wiki.ubuntu.com/SyncRequestProcess](https://wiki.ubuntu.com/SyncRequestProcess) ?

---

### Post by Nullack on 2008-09-24
Thats the process but generally I try to wait for a bit as with any Alpha, revisions change rapidly. I try to avoid causing the devs more time with it unless its become clear the problem is lasting some time.

---

### Post by Tatty on 2008-09-24
> **Nullack said:**
> Thats the process but generally I try to wait for a bit as with any Alpha, revisions change rapidly. I try to avoid causing the devs more time with it unless its become clear the problem is lasting some time.

So, are you saying that the devs may come across this and fix it anyway without a bug report being filed?

Also, what is the latest point in the development cycle you would leave something like this before reporting it yourself?

Sorry for asking lots of questions, im just trying to understand the development process a bit better. :)

---

### Post by Nullack on 2008-09-24
Its all good, Im happy to provide my views and for other people to share theirs. It all helps to improve how we test Intrepid :)

Most broken packages get sorted out pretty quick.Theres Launchpad functionality that highlights broken packages for them. Generally most get fixed pretty soon and you can get them by synching to the repos. Note that some mirrors seem to always be badly behind so I synch to main to keep my tests up to date.

---

### Post by Nullack on 2008-09-24
double post.

---

### Post by Tatty on 2008-09-24
Many thanks for the advice,  I shall just watch the package for a couple of weeks then before reporting.

Its all getting a little clearer :)

---

### Post by andrewsomething on 2008-09-24
A new version has just been uploaded. I think it should solve your issue. liblo0 has been renamed to ldbl128, so a rebuild was required.

[https://edge.launchpad.net/ubuntu/+source/ardour](https://edge.launchpad.net/ubuntu/+source/ardour)

```
ardour (1:2.5-0ubuntu3) intrepid; urgency=low

  * Make ardour buildable. This involves some aweful ugly hacks, such as
    prepacking locale and configuration files into uuencoded tarballs, as
    well as copying the binary files from the build tree into the staging dir,
    and all because the install stage of the ardour build fails at random
    places when built on the ubuntu build servers. These hacks should be
    easy to remove in the future if scons decides to behave.
  * debian/control: Add sharutils as a build dependency.

 -- Luke Yelavich < themuso@ubuntu.com>   Wed, 24 Sep 2008 11:58:34 +1000
```

It might take a little while for this to hit the archive. You should report a bug if version 2.5-0ubuntu3 doesn't install for you.

---

### Post by Tatty on 2008-09-24
> **andrewsomething said:**
> A new version has just been uploaded. I think it should solve your issue. liblo0 has been renamed to ldbl128, so a rebuild was required.

Oh excellent thank you.

Why was the package renamed?

Just curious :)

---

