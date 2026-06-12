---
title: "[solved] Unable to install Swiftweasel under 7.04"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by Jay Jay on 2008-02-07
Hopefully this will help others who have encountered similar problems...

Recently I reverted to 7.04 after endless problems with 7.10 which had made it unusable. I was able to reinstall all of the applications that I used with Gutsy apart from Swiftweasel. It wasn't present in Synaptic, so I added the repository into my third party sources and assumed that would be enough. :)

Wrong! Still didn't show up in Synaptic, so I went to the Terminal and typed:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install swiftweasel
```

Close, but no cigar:

> Package swiftweasel is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  swiftweasel-nocona swiftweasel-athlon64 swiftweasel-k8 swiftweasel-pentium3m
  swiftweasel-pentium2 swiftweasel-pentium4m swiftweasel-pentium4
  swiftweasel-pentium3 swiftweasel-k6 swiftweasel-prescott
  swiftweasel-athlonxp swiftweasel-pentiumm
E: Package swiftweasel has no installation candidate


I needed to pick the specific package, In my case It was:

```
sudo apt-get install swiftweasel-pentium3
```

Success! Swiftweasel installed - I'm not sure why It didn't and still doesn't appear in Synaptic (any ideas?) but through this route I was able to get the program I wanted.

---

### Post by 1/0 on 2008-03-27
Well, not helpful in my case... 

```

$ sudo apt-get install swiftweasel-pentium4

```
Gives me:
```

Err http://download.tuxfamily.org gutsy/multiverse swiftweasel-pentium4 2.0.0.12
  404 Not Found
Failed to fetch http://download.tuxfamily.org/swiftweasel/pool/i386-gutsy/swiftweasel-2.0.0.12_pentium-4_ubuntu-i386.deb  404 Not Found
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

I checked out the homepage and no pentium4 file in that folder... Only prescott, petium-m and pentium-4m. I tried to install pentium-4m but same problem with that one...

---

