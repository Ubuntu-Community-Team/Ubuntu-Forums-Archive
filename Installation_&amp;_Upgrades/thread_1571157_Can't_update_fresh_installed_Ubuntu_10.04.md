---
title: "Can't update fresh installed Ubuntu 10.04"
date: 2010-09-09
forum: Installation &amp; Upgrades
---

### Post by theevilbeast on 2010-09-09
Hi, I've started using Ubuntu 5 months ago and I couldn't understand what is repository and how to use it.
My first Ubuntu was 9.10 Karmic x64 and I had no problems updating it trough proxy. But recently I reinstalled it and put Ubuntu Lucid x64 and then everything changed. I wasn't able to update it and also  there was problem downloading from software center. I reinstalled it a couple of times but with no success of fixing the problem. Now I have internet but can't use any update software on ubuntu.  The problem is related with the repositories because the message that pops up is :

[COLOR=DarkOrange][I]W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) lucid-security Release: The following signatures were invalid: NODATA 1 NODATA 2

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://bg.archive.ubuntu.com](http://bg.archive.ubuntu.com) lucid Release: The following signatures were invalid: NODATA 3 NODATA 4

W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/lucid/main/i18n/Translation-en_US.bz2)  Bad header line

W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2](http://bg.archive.ubuntu.com/ubuntu/dists/lucid/universe/i18n/Translation-en_US.bz2)  Bad header line

W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/dists/lucid/Release](http://bg.archive.ubuntu.com/ubuntu/dists/lucid/Release)  

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/lucid-security/Release](http://security.ubuntu.com/ubuntu/dists/lucid-security/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.
[/I][/COLOR]
I don't understand how fresh installed Ubuntu will need new repositories. And I have no idea how fix this.
I've read articles about repository but could not understand a thing. So I am asking someone patient enough to explain to me what is that what is used for and how to fix that problem.
Thanks in advance.

---

### Post by tyblogger5 on 2010-09-09
Is this a clean install?  If not, try to run

```
sudo apt-get upgrade
```

That will upgrade the repositories.

-Tariq

---

### Post by theevilbeast on 2010-09-09
Yes, this is a clean install. After finishing the installation I set global proxy settings and tried to update Ubuntu, but with no luck.

---

### Post by tyblogger5 on 2010-09-11
Hmmm...maybe run

```
sudo apt-get upgrade
```

to update the repos, maybe the urls are bad (somehow).

-Tariq

---

