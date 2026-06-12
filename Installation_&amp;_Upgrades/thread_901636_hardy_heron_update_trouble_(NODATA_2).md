---
title: "hardy heron update trouble (NODATA 2)"
date: 2008-08-26
forum: Installation &amp; Upgrades
---

### Post by Dopaque on 2008-08-26
I have the latest version of hardy heron, according to the sticky thread above. My system tells me that there are four updates for me to install, but when I try to install them I get a myriad of error messages.

> W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy-updates Release: The following signatures were invalid: NODATA 2

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release: The following signatures were invalid: NODATA 2
W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/restricted/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2](http://us.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.31 80]

W: Failed to fetch [http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2](http://security.ubuntu.com/ubuntu/dists/hardy-security/universe/i18n/Translation-en_US.bz2)  Error reading from server - read (104 Connection reset by peer) [IP: 91.189.88.37 80]

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release](http://us.archive.ubuntu.com/ubuntu/dists/hardy-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

Where do I even begin?

---

### Post by gustavolinux on 2008-09-02
I get the same error... someone have a clue? plzzzz...

[]`s

---

### Post by Dopaque on 2008-09-20
I think I figured it out--it has to be some kind of server error. When I tried the updates again with a different internet connection they worked flawlessy.

---

### Post by mcavady on 2008-10-20
I have the same error I did find a post on the net about changing the server to the best server but this did not fix the problem!!!

Just to let you know. 

Still looking for a solution to this problem, I think that it has something to do with the keys for the downloading of the software and not the actual server type or server location. 

I am still a bit of a noob to this and will post again if I find solution.:confused:

If you want to get rid of the error then you can edit the software sources, I unchecked the software source relating to the play on linux. After all is does say that the older files will be used and wine still works fine. This does not fix the error but however it does remove the error in the update part !!

Not a fix

---

