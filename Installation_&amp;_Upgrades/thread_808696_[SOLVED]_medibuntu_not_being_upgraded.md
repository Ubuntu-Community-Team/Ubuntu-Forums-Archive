---
title: "[SOLVED] medibuntu not being upgraded"
date: 2008-05-26
forum: Installation &amp; Upgrades
---

### Post by fballem on 2008-05-26
I'm getting a message that the medibuntu repositories cannot be accessed. Is anyone else having the problem and is there a fix?

---

### Post by Pumalite on 2008-05-26
Do you have this Medibuntu?:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)
[https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f](https://help.ubuntu.com/community/Medibuntu#head-7486ed038a9becc1dff10a24cc07a38a00d70e9f)

---

### Post by fballem on 2008-05-26
Yes, and when I do, I get the following errors:

Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  404 Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  404 Not Found
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by iaculallad on 2008-05-26
> **fballem said:**
> Yes, and when I do, I get the following errors:

Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/free Packages
  404 Not Found
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) hardy/non-free Packages
  404 Not Found
W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/free/binary-i386/Packages.gz)  404 Not Found

W: Failed to fetch [http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz](http://packages.medibuntu.org/dists/hardy/non-free/binary-i386/Packages.gz)  404 Not Found

E: Some index files failed to download, they have been ignored, or old ones used instead.

You have a missing Repo so you're not being able to download updates from Medibuntu.

Try this on the terminal (You can copy and paste this on the terminal):
[B]
When you're using Gutsy:[/B]

> sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

[B]
When you're using Hardy:[/B]
> 
sudo wget [http://www.medibuntu.org/sources.list.d/hardy.list](http://www.medibuntu.org/sources.list.d/hardy.list) -O /etc/apt/sources.list.d/medibuntu.list
[B]
And lastly, add the GPG key:[/B]

> sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

That will solve your problem.

---

### Post by fballem on 2008-05-26
Don't know what happened, but thanks for the fix!

---

### Post by iaculallad on 2008-05-26
> **fballem said:**
> Don't know what happened, but thanks for the fix!

The Medibuntu repositories does not exist in your sources.list (that's the default). So you issued those commands to automatically add it for you.

You're welcome and Goodluck. Go Ubuntu

---

### Post by fballem on 2008-05-27
Cute kid, by the way!

---

