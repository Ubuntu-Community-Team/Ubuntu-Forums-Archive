---
title: "Upgrade from a local mirror"
date: 2007-10-18
forum: Installation &amp; Upgrades
---

### Post by dallingham on 2007-10-18
I have about 10 machines that I want to upgrade from 7.04 to 7.10. I have used apt-mirror to create a local mirror of the gutsy repositories. However, I'm having problems getting the upgrade to work. 

I understand that in order to get my machines to see the local repo, I must change the sources.list file to point to my local repository. That is easy. The problem is that the upgrade sees to expect to see feisty at the same location.

Is there a way to upgrade at the same time as switching repositories?

If I change to

   deb file:///my/path/ubuntu feisty main restricted universe

The I get an error that the feisty repositories cannot be found

If I change to:

   deb file:///my/path/ubuntu gutsy main restricted universe

It claims that everything is up to date.

---

