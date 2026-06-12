---
title: "Ubuntu 11.10 64 bit can't update anymore?"
date: 2011-10-15
forum: Installation &amp; Upgrades
---

### Post by xtracool_protik on 2011-10-15
I was trying to update Ubuntu 11.10 64 bit but I keep getting error:

> installArchives() failed: Preconfiguring packages ...

Preconfiguring packages ...

Preconfiguring packages ...

(Reading database ... 

dpkg: warning: files list file for package `ubuntu-docs' missing, assuming package has no files currently installed.


(Reading database ... 5%%
(Reading database ... 10%%
(Reading database ... 15%%
(Reading database ... 20%%
(Reading database ... 25%%
(Reading database ... 30%%
(Reading database ... 35%%
(Reading database ... 40%%
(Reading database ... 45%%
(Reading database ... 50%%
(Reading database ... 55%%
(Reading database ... 60%%
(Reading database ... 65%%
(Reading database ... 70%%
(Reading database ... 75%%
(Reading database ... 80%%
(Reading database ... 85%%
(Reading database ... 90%%
(Reading database ... 95%%
(Reading database ... 100%%
(Reading database ... 323646 files and directories currently installed.)

Preparing to replace ubuntu-docs 11.10.4 (using .../ubuntu-docs_11.10.4_all.deb) ...

Unpacking replacement ubuntu-docs ...

dpkg: ../../src/archives.c:978: tarobject: Assertion `r == stab.st_size' failed.



I tried a solution around forums to remove ubuntu-docs from info but it appear again next time.

Thanks

---

### Post by xtracool_protik on 2011-10-15
bump?

I hate to bump but couldn't find any replies so had to or Is it just me with this issue?

---

### Post by SheamusPatt on 2011-10-15
The message 'Assertion `r == stab.st_size' failed.' looks suspiciously like a filesystem problem of some kind. Have you tried running a filesystem check (fsck)?

You'll likely want to do this from a live or recovery CD, since  you need to check your default filesystem.

---

### Post by xtracool_protik on 2011-10-17
It surely is not a file system corruption.
As you can see [http://ubuntuforums.org/showthread.php?t=1580470](http://ubuntuforums.org/showthread.php?t=1580470)

and [http://ubuntuforums.org/showthread.php?t=1518301&page=2](http://ubuntuforums.org/showthread.php?t=1518301&page=2)

Anyways still I tried fsck and it turned out to be clean.

The problem is even after using above mentioned method I can't get anything to install/remove cause /var/lib/dpkg/status will have ubuntu-docs section as soon as I do sudo dpkg --configure -a

The section in /var/lib/dpkg/status looks:
> Package: ubuntu-docs
Status: install reinstreq half-installed
Priority: optional
Section: doc
Version: 11.10.4


Any thoughts?

I even tried downloading and installing package but same error :(

---

### Post by xtracool_protik on 2011-10-17
[http://askubuntu.com/questions/43066/how-to-get-dpkg-working-again](http://askubuntu.com/questions/43066/how-to-get-dpkg-working-again) is an accepted solution for this issue. But frankly I don't understand solution itself.

Can anyone elaborate? Thanks :)

---

### Post by xtracool_protik on 2011-10-18
bump...

---

### Post by raja.genupula on 2011-10-21
hi that means it sounds similar to,they are broken and actually  we must have to careful with the remove commands because they are really very harmful if you dont care them while dealing with rm command 

  [http://ubuntuforums.org/announcement.php?f=331](http://ubuntuforums.org/announcement.php?f=331) look at jdong post.

---

