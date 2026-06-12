---
title: "Ubuntu security update failed"
date: 2010-06-01
forum: Installation &amp; Upgrades
---

### Post by calavero on 2010-06-01
Hi all,

I have install my own local repository using debarchiver.

In my /etc/apt/source.list I add this line:

deb [http://mycomputer-repository.local/debian/](http://mycomputer-repository.local/debian/) hardy main contrib non-free

But when I run the first time:

aptitude update

# all is ok, i can install the package my local repository.

When I run the second time I have this error:

Ign [http://BUILD.local](http://BUILD.local) hardy Release.gpg
Ign [http://BUILD.local](http://BUILD.local) hardy/main Translation-en_US
Ign [http://BUILD.local](http://BUILD.local) hardy/contrib Translation-en_US
Ign [http://BUILD.local](http://BUILD.local) hardy/non-free Translation-en_US
Get:1 [http://BUILD.local](http://BUILD.local) hardy Release [5127B]
Ign [http://BUILD.local](http://BUILD.local) hardy/main Packages
Ign [http://BUILD.local](http://BUILD.local) hardy/contrib Packages
Ign [http://BUILD.local](http://BUILD.local) hardy/non-free Packages
Get:2 [http://BUILD.local](http://BUILD.local) hardy/main Packages [29B]
Hit [http://BUILD.local](http://BUILD.local) hardy/contrib Packages
Get:3 [http://BUILD.local](http://BUILD.local) hardy/non-free Packages [29B]
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy Release.gpg
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/main Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/restricted Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/universe Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy/multiverse Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates Release.gpg
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/main Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/restricted Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/universe Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) hardy-updates/multiverse Translation-en_US
  Could not resolve 'fr.archive.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_US
  Could not resolve 'security.ubuntu.com'
Err [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_US
  Could not resolve 'security.ubuntu.com'
Fetched 59B in 39s (1B/s)
Reading package lists... Done
:confused:

Does some one can help me please ?

Calavero.

---

### Post by dino99 on 2010-06-01
only click on these url and you will understand your error :confused:

use genuine repo: [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

