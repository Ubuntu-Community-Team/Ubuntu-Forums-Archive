---
title: "Making aptitude stop ignoring sources"
date: 2007-04-15
forum: Installation &amp; Upgrades
---

### Post by Darko-TheRaven on 2007-04-15
Is there anyway to make aptitude stop ignoring sources, i know the sources work but when i run the *aptitude update* command it has *Ign:* next to good sources

---

### Post by Darko-TheRaven on 2007-04-17
More information:

This ubuntu installation is now configured how i'd like it to be and would rather not have to reinstall ubutu to gewt the package manager working again.:(

---

### Post by Darko-TheRaven on 2007-04-20
bah, nevermind i'm upgrading to feisty now anyway. please ignore this thread.

---

### Post by motin on 2007-04-20
> **Darko-TheRaven said:**
> Is there anyway to make aptitude stop ignoring sources, i know the sources work but when i run the *aptitude update* command it has *Ign:* next to good sources

I have also wondered about this. However - I believe "Ignore" means "Ignore because the source hasn't changed since last time". At least I surely hope so...

The man-page of apt-get doesn't give any help:
```
       update
          update is used to resynchronize the package index files from their
          sources. The indexes of available packages are fetched from the
          location(s) specified in /etc/apt/sources.list. For example, when
          using a Debian archive, this command retrieves and scans the
          Packages.gz files, so that information about new and updated
          packages is available. An update should always be performed before
          an upgrade or dist-upgrade. Please be aware that the overall
          progress meter will be incorrect as the size of the package files
          cannot be known in advance.

```

---

### Post by Darko-TheRaven on 2007-04-21
well, i had hoped that. but since i use  wireless card on the box it is not always connected and it tries to sync offline. if it does that it never checks the source again. my always connected computer shows updates wnd the box in question refused to download the sources.

---

