---
title: "After upgrade to 14.04 Truecrypt doesn't mount container files: bad file desctriptor"
date: 2014-09-03
forum: Installation &amp; Upgrades
---

### Post by Gingalone on 2014-09-03
I have just upgraded my 2 PCs from Ubuntu 12.04 to 14.04 (got some system problem warnings afterward) but the worst is that Truecrypt doesn't mount encrypted container files giving the message "bad file descriptor", on both PCs. I used those container files a thousand times on 12.04 without any single problem....
What about? (I have lots of data and backups in those containers)
Thanks for any help!

---

### Post by uRock on 2014-09-03
Which PPA are you using for Truecrypt? I am using```
sudo add-apt-repository ppa:stefansundin/truecrypt
```You may need to uninstall, purge, then reinstall Truecrypt.

---

### Post by Gingalone on 2014-09-04
Thank you uRock, it was not necessary to reinstall Truecrypt (but I will keep the address of that PPA!), the problem came from the fact that I had set a no-user password request upon Truecrypt encrypted files opening and everything is OK now after putting:
username ALL = NOPASSWD: /usr/bin/truecrypt
in the file /etc/sudoers.d/README (which was reset to default upon the upgrade to Ubuntu 14.04).
I can't say why that caused the "Bad file descriptor" critical warning, but I am happy all my TC files are working now!

---

### Post by uRock on 2014-09-04
Excellent!

---

### Post by Musgrave on 2014-09-10
I had same problem however my files did mount when attempted a second time. 
Gingalone's solution worked for me. (updating the README file got rid of the first time mount failure).

Thanks

---

