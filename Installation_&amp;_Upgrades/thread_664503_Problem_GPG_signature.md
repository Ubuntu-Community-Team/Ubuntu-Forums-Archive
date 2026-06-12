---
title: "Problem GPG signature"
date: 2008-01-11
forum: Installation &amp; Upgrades
---

### Post by Vispo on 2008-01-11
Hello,
seem to have a problem when i try to make apt-get update and download the update list. The error on the console is this:

```
W: GPG error: http://archive.canonical.com gutsy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://security.ubuntu.com gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ch.archive.ubuntu.com gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ch.archive.ubuntu.com gutsy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
```

I tried like told in the sources.list to add the key manualy but seems not to change at all.
I also changed completly the sources.list from another system that is running.
Here is my actual sources.list is in the attachement.
Does any one know where to find the public keys for the official repositories?

Thx for your help
                                        Vispo

---

### Post by zvacet on 2008-01-11
```
sudo apt-get update
```

---

### Post by mastapat11 on 2008-01-18
Try this if your problem still isn't solved:

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

```
sudo apt-get update -o Acquire::BrokenProxy=true
```

```
sudo apt-get update
```

---

### Post by Vispo on 2008-02-02
Ok,
seemed just to be the office proxy that got the old key somehow... 
:-) it now works again like a charm good to now the little proxy trick.
Thank you for your kind help and have a nice day

---

