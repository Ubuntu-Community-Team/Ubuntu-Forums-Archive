---
title: "libnatpmp1 and upgrade"
date: 2013-05-09
forum: Installation &amp; Upgrades
---

### Post by Panawe on 2013-05-09
Don't normally have problems with regular upgrades but on my latest upgrade i got a "Requires installation of untrusted packakes" or some such. The offending package seems to be "libnatpmp1"
Any help appreciated.

---

### Post by dino99 on 2013-05-09
follow the ppas procedure to get them signed
that lib might come from one of them

---

### Post by Panawe on 2013-05-09
Um, what's the ppas procedure?

---

### Post by Panawe on 2013-05-10
> **Panawe said:**
> Um, what's the ppas procedure?

Still struggling with this and be grateful of anyone who can help a more or less complete beginner.

---

### Post by Panawe on 2013-05-10
Is this any help to problem. I tried...

sudo apt-get update && sudo apt-get install medibuntu-keyring && sudo apt-get update

And got...

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) maverick Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

 I'm pretty much flying blind here!

---

### Post by Panawe on 2013-05-10
I've been googling around and solved the problem in the following manner...

"cd /var/lib/apt
  sudo mv lists lists.old
  sudo mkdir -p lists/partial
  sudo apt-get update

This will rebuild the cache."

For the benefit of others.

---

