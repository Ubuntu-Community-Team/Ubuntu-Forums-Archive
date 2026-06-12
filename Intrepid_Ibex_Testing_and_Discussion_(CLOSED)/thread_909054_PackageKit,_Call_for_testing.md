---
title: "PackageKit, Call for testing"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by plun on 2008-09-03
Another call....

> **PackageKit: Call for testing**

Category: Ubuntu

The APT backend for PackageKit has made a lot of progress recently in the 0.3.x series. It nearly supports all features of PackageKit. 

Highlights of the 0.3.x series are:

    * Search for codecs and mime type handlers
    * Local file installation
    * Change log for updates
    * Group support
    * Repository handling
    * Notification of new distro releases
    * A lot of bug fixes

See the feature matrix for more infromation.

Currently we have got a quite outdated 0.2.4 version in Intrepid. Furthermore sharing the same version would help to reduce maintenance burden, since Fedora plans to ship 0.3.2 in the next release. But before proposing a freeze exception I would like to have some feedback.

So if you are interested in this piece of software and want to push packagekit forward please test it on your system and report bugs that you may encounter.

You can find packages of the upcoming 0.3.2 release for Hardy and Intrepid in this Personal Package Archive. Add the repository and install the packages 


Howto:
[http://www.glatzor.de/blog/blog-details/select_category/1/article/packagekit-call-for-testing/?tx_ttnews](http://www.glatzor.de/blog/blog-details/select_category/1/article/packagekit-call-for-testing/?tx_ttnews)[backPid]=4&cHash=394ae6b1d7


Posted on Ubuntu Planet.....

---

### Post by nightfrost on 2008-09-20
With the latest update (to 0.3.3), I get a lot of errors, basically I can't be doing anything. The error is this:

> The backend took too much time to process the synchronous request - you need to fork! 

For example when I attempt to install a package, I get that message. And the package won't be installed. Any ideas?

Aside from that, packagekit is really neat :-)

---

### Post by plun on 2008-09-20
Yup, PackageKit is handy for new users but also for experienced users in hurry to install something "on the run"....:)

A surprise for me that it was accepted

[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007176.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/007176.html)

Broken also for me,  can you please file a bug...:)

---

### Post by nightfrost on 2008-09-20
Well, I'm happy it was accepted, now Ubuntu will have the same version as Fedora and we can probably share some patches.
I'll file a bug report as soon as I can.

---

### Post by nightfrost on 2008-09-20
Here's the bug report: [https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/272410](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/272410)

Now, go confirm! :-)

---

### Post by plun on 2008-09-20
Done  :)

You must have the ppa installed to see this error

[https://edge.launchpad.net/%7Epackagekit/+archive](https://edge.launchpad.net/%7Epackagekit/+archive)

The following NEW packages will be installed:
  **packagekit-backend-apt**
The following packages will be upgraded:
  packagekit packagekit-gnome

> The backend took too much time to process the synchronous request - you need to fork!


There is no backend within Ubuntus repo....it might be the problem and
now its a mismatch between repo and ppa.

The developer works really hard with this....

[http://blogs.gnome.org/hughsie/](http://blogs.gnome.org/hughsie/)

---

### Post by plun on 2008-09-29
With todays update there was a scary message...

E: Syntax error /etc/apt/apt.conf.d/20packagekit:2: **Extra junk after value**


:D

---

### Post by Bou on 2008-09-29
I just started testing packagekit, and I find it pretty neat except, maybe, for a couple things:

-When a package can't be installed, you don't get an error message. Instead, PK seems to keep "checking" forever. Try to install Elisa (there is a dependency problem right now) and see.

-It seems to have installed entries all over the menus: you have a log viewer in system tools, update options in preferences, update system and repositories in administration. Is this really necessary? Couldn't most of this stuff be reached directly from PK? Do we need to crowd the menus?

---

### Post by plun on 2008-09-29
> **Bou said:**
> I just started testing packagekit, and I find it pretty neat except, maybe, for a couple things:

-When a package can't be installed, you don't get an error message. Instead, PK seems to keep "checking" forever. Try to install Elisa (there is a dependency problem right now) and see.

-It seems to have installed entries all over the menus: you have a log viewer in system tools, update options in preferences, update system and repositories in administration. Is this really necessary? Couldn't most of this stuff be reached directly from PK? Do we need to crowd the menus?

Ok...its heavily broken within ppa for the moment so I cannot test.

[https://edge.launchpad.net/~packagekit/+archive](https://edge.launchpad.net/~packagekit/+archive)

"Crowding" menus is a "Gnome challenge" and for sure its enough with 1 entry.   


The main developers blog is a good place for understanding how this project develops.

[http://blogs.gnome.org/hughsie/](http://blogs.gnome.org/hughsie/)


I am testing it just for fun and I don't believe that this will be included or backported... but maybe...:)

---

### Post by gnomeuser on 2008-09-29
One of the primary reasons PackageKit is a good idea is that it will give us all one set of tools which we can improve with UI experience, translations and the interaction experience also is improved (little things like your app now runs as user, looks the part without hacks and is more secure in addition to giving us very customizable policy for what a user might be allowed to do without authorization).

You can also do advanced integration to install support as it is missing in apps - say codec support as you attempt to play a movie or compression support in fileroller. 

Lots of little nice things, I doubt we will see it by default in Intrepid, that boat seems to have sailed but the next release definitely.

---

### Post by ibizatunes on 2008-09-29
I have done a major cock up
I set up the repo's , did a update, then did ONLY installed packagekit NOT packagekit-gnome. and now my machine has this error! 

E: Syntax error /etc/apt/apt.conf.d/20packagekit:2: Extra junk after value

Can any one help me fix this? I really dont want to rebuild my machine tonight

---

### Post by plun on 2008-09-29
> **ibizatunes said:**
> I have done a major cock up
I set up the repo's , did a update, then did ONLY installed packagekit NOT packagekit-gnome. and now my machine has this error! 

E: Syntax error /etc/apt/apt.conf.d/20packagekit:2: Extra junk after value

Can any one help me fix this? I really dont want to rebuild my machine tonight

I solved it this way  , at least apt is working again.


```
gksudo nautilus

>>>

/etc/apt/apt.conf.d

>>>

delete the file 20packagekit

sudo apt-get update
```


Another way is probably to remove packagekit with the **purge** option.

---

### Post by nanog on 2008-09-29
Very cool!

---

### Post by PRGUY85 on 2008-09-29
I have been testing PackageKit on Fedora.  I think it's even better than synaptic and that's saying a lot.  It is great to have a standarized and universal install configuration for the major Linux packages.  

In Fedora 10, at times it is quite buggy but I hope further updates makes it stable.

---

### Post by gnomeuser on 2008-09-29
> **PRGUY85 said:**
> I have been testing PackageKit on Fedora.  I think it's even better than synaptic and that's saying a lot.  It is great to have a standarized and universal install configuration for the major Linux packages.  

In Fedora 10, at times it is quite buggy but I hope further updates makes it stable.

In the community's defense, F10 is currently pre-beta, don't expect it to be flawless, that sadly includes the package frontend. Also when you find a bug it would make you an intergalactic superstar if you filed them as a supplement to complaining on a forum for another distribution.

That being said, I am very happy you enjoy PackageKit, I to find it a superior offering and one with a great potential to integrate package handling in interesting places.

---

### Post by PRGUY85 on 2008-09-29
> **gnomeuser said:**
> 
Also when you find a bug it would make you an intergalactic superstar if you filed them as a supplement to complaining on a forum for another distribution.



Didn't get if you were being bitchy, arrogant or attacking me for just mentioning Fedora.  I don't care.  Packagekit is great software and I hope to see it as default on Ubuntu soon.

---

### Post by Bou on 2008-09-29
After using it this evening, there is just one thing I miss from Synaptic: being able to browse packages by state (new packages, upgradable, orphaned dependencies).

Do you guys know if they're planning to include this, too?

---

### Post by plun on 2008-09-30
Yesterdays break for the ppa version fixed but the "dbus-fork" error
remains....

> The backend took too much time to process the synchronous request - you need to fork!

Moved to upstream
[https://bugs.freedesktop.org/show_bug.cgi?id=17750](https://bugs.freedesktop.org/show_bug.cgi?id=17750)


Also a "Freeze exception" maybe...
[https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/276264](https://bugs.launchpad.net/ubuntu/+source/packagekit/+bug/276264)

---

### Post by olskar on 2008-09-30
I get "error while loading shared libraries: libpackagekit.so.5: cannot open shared object file: No such file or directory" in Hardy when trying to open it

Edit: But now it works! Love how it uses policykit so I dont have to write password each time!

---

### Post by ibizatunes on 2008-10-05
Does anyone get this error? Or should i file a bug?

---

### Post by plun on 2008-10-05
> **ibizatunes said:**
> Does anyone get this error? Or should i file a bug?

I am on ppa version and its complete broken.

Its nevertheless better to file too many bugs then miss a bug.

This is what we have
[https://bugs.edge.launchpad.net/ubuntu/+source/packagekit/+bugs](https://bugs.edge.launchpad.net/ubuntu/+source/packagekit/+bugs)

---

### Post by ibizatunes on 2008-10-06
if anyone else gets this bug i have filed in at launchpad
[https://bugs.edge.launchpad.net/ubuntu/+source/packagekit/+bug/279168](https://bugs.edge.launchpad.net/ubuntu/+source/packagekit/+bug/279168)

---

### Post by plun on 2008-10-28
Well, PackageKit works again for me after switching to a new kernel,

No racing conditions with apt-backend.  (The fork message...)

No need for ppa, everything within Intrepids repo 

packagekit and packagekit-gnome  are needed install packages.

---

