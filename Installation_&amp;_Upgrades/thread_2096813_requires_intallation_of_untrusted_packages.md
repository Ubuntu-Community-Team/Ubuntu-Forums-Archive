---
title: "requires intallation of untrusted packages"
date: 2012-12-21
forum: Installation &amp; Upgrades
---

### Post by marsgorski on 2012-12-21
I am using Ubuntu 12.04 and when I try to update some packages through update manager I get the message "requires intallation of untrusted packages" and does not let me proceed unless I uncheck the "other updates" boxes (see screenshot.)

When I run "apt-get update" I get the errors

```
W: GPG error: http://archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://us.archive.ubuntu.com precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```I tried following the solution found [here]("http://www.liberiangeek.net/2010/10/fix-requires-installation-untrusted-packages-error-ubuntu-10-10-maverick-meerkat/") (I even have the same key missin, 40976EAF437D05B5) but that did not fix the problem.

Any suggestions are appreciated!

---

### Post by cwsnyder on 2012-12-21
According to your thumbnails, these are not Ubuntu packages, they are from the YPPA manager from WebUpD8.  To quote from W8:> There is a delay when adding a PPA on a computer which has the GPG key server port blocked. It eventually works but you'll have to wait a bit - this is not a bug in Y PPA Manager (you'll experience the same thing when using the "add-apt-repository command). Hopefully the Ubuntu GPG keyserver will change the port sometime to prevent such issues.If waiting doesn't fix the issue, again quoting from W8:> Don't forget to report any bugs you may find @ Launchpad. Also if you have an idea / suggestion, let me know in the comments![http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html](http://www.webupd8.org/2010/11/y-ppa-manager-easily-search-add-remove.html)

You are using software which is NOT IN STANDARD UBUNTU.  Use at your own risk.

---

### Post by marsgorski on 2012-12-21
When I I first installed Y-PPA (maybe about 6-8 mos. ago) it worked without a problem. I guess this means it is likely a bug??

How could I disable/uninstall Y-PPA manager? This is also causing me trouble when I try to install software from the Software Center; I get the same "requires intallation of untrusted packages" error.

---

### Post by oldos2er on 2012-12-21
BADSIG errors and NO_PUBKEY errors are two different things. Try this to fix BADSIG errors: [http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html](http://www.ubuntugeek.com/how-to-fix-the-ubuntu-gpg-error-badsig.html)

---

### Post by marsgorski on 2012-12-21
Awesome! Method 1 worked. Thank you so much!

---

