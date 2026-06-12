---
title: "Problem upgrading from 10.04 to 10.10"
date: 2011-06-03
forum: Installation &amp; Upgrades
---

### Post by sergiodavila on 2011-06-03
Hello,

Trying to upgrade from Ubuntu 10.04 to 10.10 (further I'll upgrade to 11.04 :P). After I start the Update manager the process starts until the stage Setting news software channels, when appears the message:

Error during update

A problem occurred during the update. This is usually some sort of network problem, please check your network connection and retry.

W:Failed to fetch [http://archive.canonical.com/ubuntu/dists/maverick/Release](http://archive.canonical.com/ubuntu/dists/maverick/Release)  Unable to find expected entry  (Source/binary-i386/Packages in Meta-index file (malformed Release file?)
, E:Some index files failed to download, they have been ignored, or old ones used instead.

And then the upgrade process stops.

Any suggestions how to solve the problem? Thanx in advance.

---

### Post by mörgæs on 2011-06-04
Have you thought of a clean install of 11.04?

---

### Post by bulldog on 2011-06-04
> **mörgæs said:**
> Have you thought of a clean install of 11.04?
 +1
It's the fastest and cleanest way of taking care of things.
In the process you could think of making a separate /home,if you didn't already.
Otherwise backup your important stuff in /home and do a clean install,wouldn't take more as half an hour or so.

---

### Post by linuxinstalledfromhdd on 2011-06-04
I'm sticking with 10.10 for now.  You might want to try it.

Here is a really handy walkthrough:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

---

### Post by bulldog on 2011-06-04
> **linuxinstalledfromhdd said:**
> I'm sticking with 10.10 for now.  You might want to try it.

Here is a really handy walkthrough:

[http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/](http://cinderbox.net/2010/12/23/to-do-list-after-installing-ubuntu-10-10-aka-maverick-meerkat/)

Yeah,well,I'm sticking with 11.04 with Gnome-Shell,which isn't gonna help the ts either.............

---

### Post by sergiodavila on 2011-06-04
Thank you folks I'll try the suggested and keep you informed of what's happening!:)

---

### Post by sergiodavila on 2011-06-04
> **mörgæs said:**
> Have you thought of a clean install of 11.04?

Ofcourse. Even tryed :D but without success. Probably the downloaded image of 11.04 has some bug (naturally I'm able to download another copy if tyhe problems persist). That's why I'm trying now the upgrading process. At least it's an adventure :)

---

### Post by mörgæs on 2011-06-04
You can test the ISO like this:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have tried installing 11.04 without success (assuming the ISO is all right), it is very unlikely that the upgrade works.

---

### Post by sergiodavila on 2011-06-04
> **mörgæs said:**
> You can test the ISO like this:
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

If you have tried installing 11.04 without success (assuming the ISO is all right), it is very unlikely that the upgrade works.

The case is I made a fresh install a week ago of 10.04 on the hard drive, because that was what I had at the moment, expecting to upgrade later to 10.10 and after that to 11.04. The install process was very OK and then I tried to boot from the CD with 11.04, and the process was interrupted. For now I do not have an explanation about the problem.

---

