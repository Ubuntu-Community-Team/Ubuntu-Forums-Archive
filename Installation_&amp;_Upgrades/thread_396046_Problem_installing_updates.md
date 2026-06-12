---
title: "Problem installing updates"
date: 2007-03-29
forum: Installation &amp; Upgrades
---

### Post by JasonOng on 2007-03-29
Hi

My ubuntu edgy running on xfce's been doing fine until recently when I cannot run update manager properly even though it keeps telling me that I've got updates available. Tried running sudo apt-get update and found these errors.

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) edgy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

Anybody know what's wrong?

---

### Post by zorkerz on 2007-03-30
Im just shooting in the dark here but if you go to system->Administration->Software_Sources and the authentication tab
you could restore the defaults  -if you have added othrer repositories this may cause problems

Otherwise you could check out your sources.list file
in a terminal type
```
sudo nano /etc/apt/sources.list
```

---

