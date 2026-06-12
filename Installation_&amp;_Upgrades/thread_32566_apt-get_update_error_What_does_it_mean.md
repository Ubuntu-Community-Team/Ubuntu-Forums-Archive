---
title: "apt-get update error: What does it mean?"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by m3jsh on 2005-05-08
> 
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>


What does this mean?

---

### Post by dave9191 on 2005-05-08
That the files that were downloaded had bad signatures. 

You can sign a file using a form of encrytpion so that you can verify the file hasnt been tampered with at the other end. IF you get a bad sig on the file its either been badly downloaded or tampered with by someone.

---

