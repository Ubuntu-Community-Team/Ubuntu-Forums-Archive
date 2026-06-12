---
title: "How do I update my subversion client from 1.6.6 (r40053) on Lucid Lynx ?"
date: 2011-09-19
forum: Installation &amp; Upgrades
---

### Post by sinnamary on 2011-09-19
**Context:**
I am running on Lucid Lynx. 10.04 LTS

**Goal:**
My subversion client is now at version 1.6.6 (r40053).
I want to upgrade it to a newer version like 1.6.16.

**Background:**
I have searched on [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and the latest is 1.6.6.
A few people like [this]("http://www.toosweettobesour.com/2008/09/04/svn-client-too-old-in-ubuntu"), have suggested that it is a matter of finding repositories that provide compiled binaries.

I have enabled backports etc.. and nothing is available.

Do you recommend I compile from source or do you perhaps have links to other repositories for Lucid Lynx ?

Your help is much appreciated.

Sinna

---

### Post by An Sanct on 2011-09-19
Lucid does not seem to be supported any more ...

but ...

> You can update your system with unsupported packages from           this untrusted PPA by adding **ppa:anders-kaseorg/subversion-1.6**           to your system's Software Sources.

Take a look at the source of that quote - [here]("https://launchpad.net/%7Eanders-kaseorg/+archive/subversion-1.6") or google a similar PPA for that.

---

### Post by linwhwylb on 2012-08-14
I had upgrade my subversion from 1.6.x to 1.7.x from [this]("http://askubuntu.com/questions/65468/where-can-i-find-a-subversion-1-7-binary") guide.
Hope it can help.

```
$ sudo apt-add-repository ppa:dominik-stadler/subversion-1.7
$ sudo apt-get update
$ sudo apt-get upgrade
```
assume you had install subversion in you system, otherwise use
```
$ sudo apt-get install subversion
```fristly.

---

