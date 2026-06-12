---
title: "Repos can't find beryl!"
date: 2006-12-01
forum: Installation &amp; Upgrades
---

### Post by spacepirates on 2006-12-01
after following the howto on installing beryl, i had it working. then i rebooted and lost beryl. now i am trying to reinstall it, however the repos can't find beryl, or just can't be contacted at all.

i get: 
```

Failed to fetch http://SeerOfSouls.com/dists/edgy/Release  Unable to find expected entry  e17/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://compiz-mirror.lupine.me.uk/dists/edgy/Release  Unable to find expected entry  main-edgy/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://ubuntu.moshen.de/dists/edgy/Release  Unable to find expected entry  flash/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://download.tuxfamily.org/3v1deb/dists/edgy/Release  Unable to find expected entry  beryl-svn/binary-amd64/Packages in Meta-index file (malformed Release file?)
Failed to fetch http://wine.budgetdedicated.com/apt/dists/edgy/main/binary-amd64/Packages.gz  404 Not Found
Reading package lists... Done
W: GPG error: http://ubuntu.lupine.me.uk edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

```

any ideas on what is wrong here?

both download.tuxfamily and compiz-mirror.lupine are supposed to have beryl in them.

I run Kubuntu Edgy on an amd 4400 x2 and an nvidia 6800 GS.

thanks!

---

### Post by loell on 2006-12-01
the repository

```
http://ubuntu.lupine.me.uk edgy
```

should have a public key , usually these public key is provided in the howto you followed

---

### Post by spacepirates on 2006-12-01
i added lupine's key from the howto, but i decided to go to the site anyways where it told me to enter the code 
```
wget http://ubuntu.lupine.me.uk/root@lupine.me.uk.gpg -O- | sudo apt-key add -
```

however i don't think adding the key ever finished as the terminal froze after i tried to add the code, as in i couldn't enter another command after it.

so the problem persists...

---

### Post by Johan! on 2006-12-01
deb [http://ubuntu.beryl-project.org/](http://ubuntu.beryl-project.org/) edgy main

This is the correct repository for Beryl.

[http://forum.beryl-project.org/viewtopic.php?t=51](http://forum.beryl-project.org/viewtopic.php?t=51)

---

### Post by spacepirates on 2006-12-01
Working updating/upgrading my system right now.

Thanks!

---

