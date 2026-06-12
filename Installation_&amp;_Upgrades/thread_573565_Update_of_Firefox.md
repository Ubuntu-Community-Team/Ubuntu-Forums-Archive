---
title: "Update of Firefox"
date: 2007-10-11
forum: Installation &amp; Upgrades
---

### Post by GoranI on 2007-10-11
I`m using Ubuntu 7.04 and Firefox 2.0.0.6. Under HELP--CHECK FOR UPDATES button is disabled. System Update Manager don`t update Firefox on version 2.0.0.7. How can I update ?

---

### Post by perlluver on 2007-10-11
Wanted to know the same thing.  It is not in the repos.  And I tried doing it manually, but can not get that tar.gz file to work.

---

### Post by taurus on 2007-10-11
> **perlluver said:**
> Wanted to know the same thing.  It is not in the repos.  And I tried doing it manually, but can not get that tar.gz file to work.

Applications -> Accessories -> Terminal
```
cd ~/Desktop
tar xvzf firefox-2.0.0.7.tar.gz
cd firefox
./firefox
```

---

### Post by GoranI on 2007-10-11
I d-loaded this from firefox central and it`s working. U have to extract from package and start with Alt-F2 with selection of "firefox.sh", but I think this don`t fix my problen (also your`s !! )

---

### Post by perlluver on 2007-10-11
[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)  This site might help.  I am trying it now, I will let you know.

---

### Post by perlluver on 2007-10-11
It worked for me, picked the wrong language the first time, other than that update to 2.0.0.7.  If it works please mark as solved.

---

### Post by rsambuca on 2007-10-11
> **GoranI said:**
> I`m using Ubuntu 7.04 and Firefox 2.0.0.6. Under HELP--CHECK FOR UPDATES button is disabled. System Update Manager don`t update Firefox on version 2.0.0.7. How can I update ?

The Firefox Version in the Ubuntu repositories is still patched with the security fixes, but the version number doesn't generally change.  I guess what I am saying is that you needn't worry that your Firefox version doesn't correspond to the latest one from Mozilla.  As long as you are updating your Ubuntu you should be OK.

---

### Post by perlluver on 2007-10-11
Well that makes sense too!  Thanks for the help!

---

### Post by DJ_Peng on 2007-10-11
> **rsambuca said:**
> The Firefox Version in the Ubuntu repositories is still patched with the security fixes, but the version number doesn't generally change.  I guess what I am saying is that you needn't worry that your Firefox version doesn't correspond to the latest one from Mozilla.  As long as you are updating your Ubuntu you should be OK.

> **perlluver said:**
> Well that makes sense too!  Thanks for the help!
Is there some reason the version numbers aren't updated when the patches are applied? That way the users can know what level of patching their browser has gotten.

---

### Post by rsambuca on 2007-10-11
I think it is because not all new ***features*** are integrated into the patches.  Security with no new toys.

---

### Post by DJ_Peng on 2007-10-11
That may be for some patches, but most patches lately have concentrated on security/stability. In th non-Ubuntu world there's a big difference between 2.0.0.4 and 2.0.0.7. Much better security and stability, with nary a single toy added. And I can say this so confidently because I use the code straight from Mozilla so I know what toys get added each version. And there's no toys getting added for 2.0.0.8 (which I'm helping to test), just more security and better stability.

Now Firefox 3? ***BIG*** difference. So much so that I don't even use it for most of my daily browsing, although I do try to keep up with the nightly builds.

---

