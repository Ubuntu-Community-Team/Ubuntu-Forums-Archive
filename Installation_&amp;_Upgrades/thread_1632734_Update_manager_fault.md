---
title: "Update manager fault"
date: 2010-11-28
forum: Installation &amp; Upgrades
---

### Post by RuneLacroix on 2010-11-28
Hey..
I have a small alert sign in my notification area from update manager... I created the fault myself, which was very stupid and now i don't know how to fix it.

It says:
[B]Failed to download repository information

(INFO): 
W:Failed to fetch [http://ppa.launchpad.net/eee-control/eee-control/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/eee-control/eee-control/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/eee-control/eee-control/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/eee-control/eee-control/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.

 [/B]What i did wrong, because i know only very little about ubuntu, was: 
I was trying to ad another software source in Software center - edit - software sources -other software... And then by trying to delete what i added, because i was just playing around i think i deleted something else as well.... 


Can i do anything to restore it back??

KIND REGARDS, 
Rune lacroix

---

### Post by sikander3786 on 2010-11-28
Go to Software Center > Edit > Software Sources > Other Software Tab and disable any Launchpad PPAs from there.

Now go to Applications > Accessories > Terminal and do this command.

```
sudo apt-get update
```

If that still contains errors, post the output of above mentioned as well as this one.

```
cat /etc/apt/sources.list
```

---

### Post by geovino on 2010-11-28
I get this error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)

---

### Post by sikander3786 on 2010-11-28
> **geovino said:**
> I get this error:

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB141E2302FDF932

W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/maverick/Release](http://extras.ubuntu.com/ubuntu/dists/maverick/Release)
Add the missing GPG key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

And then,

```
sudo apt-get update
```

Good Luck!

---

### Post by Frogs Hair on 2010-11-28
Give this page a read the ppa is not being maintained.[https://launchpad.net/~eee-control/+archive/eee-control](https://launchpad.net/~eee-control/+archive/eee-control)

---

### Post by geovino on 2010-11-28
> **sikander3786 said:**
> Add the missing GPG key by

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys DB141E2302FDF932
```

And then,

```
sudo apt-get update
```

Good Luck!

That fixed the problem. Thanks. :)

---

### Post by RuneLacroix on 2010-11-29
> **Frogs Hair said:**
> Give this page a read the ppa is not being maintained.[https://launchpad.net/~eee-control/+archive/eee-control]("https://launchpad.net/%7Eeee-control/+archive/eee-control")


.... That is sad...

So it makes sense that the error disappeared when i disabled the PPA's

---

