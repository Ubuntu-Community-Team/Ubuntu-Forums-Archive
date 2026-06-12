---
title: "update issues"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by toast-sama on 2005-10-14
I reciently installed v 5.04 this is my first real time on linux so i'm confused and going in circles... regardless... i have a broken package "language-support-en" and when i tried to re-install it i got this error:

W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


so i dont know what to do and was hoping one of you wonderful people might know.

JD
(in case it makes any difference I am running the 64 bit edition)

---

### Post by mlomker on 2005-10-14
> W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


Is that the only error, because that's not actually a problem.  That's just saying that the encryption key isn't installed on your machine to verify where the files came from...it's a feature for the paranoid.

Try:

```

sudo apt-get update
sudo apt-get -f upgrade

```

---

