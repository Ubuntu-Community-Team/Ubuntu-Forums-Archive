---
title: "HELP! I think my repos are......"
date: 2007-11-16
forum: Installation &amp; Upgrades
---

### Post by TNakos on 2007-11-16
i think i maybe missing security 3rd party repos. this is the error message

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden


W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

---

### Post by taurus on 2007-11-16
[http://ubuntuforums.org/showthread.php?t=463944](http://ubuntuforums.org/showthread.php?t=463944)

---

### Post by TNakos on 2007-11-16
hold on i need it for gutsy

---

### Post by TNakos on 2007-11-16
nevermind i dont need anymore help, solved

---

### Post by John_5 on 2007-11-16
Having the same problem, how did you fix your's?

---

### Post by angryfirelord on 2007-11-16
Switch to another server. You can choose one from Synaptic.

---

### Post by taurus on 2007-11-16
> **angryfirelord said:**
> Switch to another server. You can choose one from Synaptic.

[http://ubuntuforums.org/showthread.php?t=463944&page=4#32](http://ubuntuforums.org/showthread.php?t=463944&page=4#32)

---

### Post by teknorah on 2007-11-16
> **taurus said:**
> [http://ubuntuforums.org/showthread.php?t=463944&page=4#32](http://ubuntuforums.org/showthread.php?t=463944&page=4#32)

Great post, taurus!

My thought on this is: errors aren't messages from the dark side, they are nice little messages telling you something unexpected is going on.  The little message fairy on my shoulder said: "hmmm.... maybe you should look this one up on the forums first before you continue...."  Then, upon my first search found that it was just an emergency pull of sw from the server and not to worry.  And also, it is good to see posts like this where it warns you from just changing configurations willy nilly. :)

---

### Post by angryfirelord on 2007-11-16
> **taurus said:**
> [http://ubuntuforums.org/showthread.php?t=463944&page=4#32](http://ubuntuforums.org/showthread.php?t=463944&page=4#32)
Yes yes, I'm aware of that now... :oops:

---

### Post by TNakos on 2007-11-17
so this is the message

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/smbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/samba-common_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden

W: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb](http://security.ubuntu.com/ubuntu/pool/main/s/samba/libsmbclient_3.0.26a-1ubuntu2.1_i386.deb)
  403 Forbidden
 albert said 15 hours ago:

A problem was detected in these update packages. Download of the packages has been blocked on purpose, to prevent problems for the users.
See bug 163042
 Tim Nakos said 15 hours ago:

is it also blocked on 7.10?
 albert said 15 hours ago:

Yes, that was added in comment 8:

Turns out that upstream's fix for CVE-2007-4572 was incomplete and Feisty and Gutsy are also affected. As such, feisty and gutsy packages have been disabled. I have also linked to the upstream bug report. Updated packages without this patch will be provided for all releases. CVE-2007-4572 is a DoS but believed to not be exploitable.








this was my convo with a launchpad guy... This cannot be fixed... that was a bad update

---

