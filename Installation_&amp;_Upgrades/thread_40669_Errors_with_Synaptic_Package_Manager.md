---
title: "Errors with Synaptic Package Manager"
date: 2005-06-09
forum: Installation &amp; Upgrades
---

### Post by twoseids on 2005-06-09
Every time I run the Synaptic Package Manager or the Ubuntu Update Manager, I get the following error message:

W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)

And another error message.  Today I tried installing the update "libmjpegtools0" from the Ubuntu Update Manager, and got the following message:

W: Failed to fetch [ftp://ftp.nerim.net/debian-marillat/pool/main/m/mjpegtools/libmjpegtools0_1.6.2-0.9_i386.deb](ftp://ftp.nerim.net/debian-marillat/pool/main/m/mjpegtools/libmjpegtools0_1.6.2-0.9_i386.deb)
  Unable to fetch file, server said ‘Can't open /debian-marillat/pool/main/m/mjpegtools/libmjpegtools0_1.6.2-0.9_i386.deb: No such file or directory  ’ [IP: 62.4.17.14 21]

It sounds like maybe the first error message is something I need to fix on my computer, but maybe the second message is something wrong on the uploading end?

---

### Post by defkewl on 2005-06-09
Try adding more repositories, even better if you could use repos that is from the same country as yours. This issue happens because perhaps you have slow internet connection and there is something wrong with the repo server ;)

---

### Post by twoseids on 2005-06-09
[QUOTE=defkewl]Try adding more repositories, even better if you could use repos that is from the same country as yours. This issue happens because perhaps you have slow internet connection and there is something wrong with the repo server ;)[/QUOTE]
 Hmm...well, I do have a broadband connection here, so speed isn't the issue.  How do I find local repositories?

---

### Post by defkewl on 2005-06-16
I don't know about the ones in your country. Perhaps you could try asking your ISPs near you :D

---

