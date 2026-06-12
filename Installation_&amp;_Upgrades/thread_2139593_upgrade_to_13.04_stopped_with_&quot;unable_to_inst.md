---
title: "upgrade to 13.04 stopped with &quot;unable to install (supposed) new info file&quot;"
date: 2013-04-27
forum: Installation &amp; Upgrades
---

### Post by John Harrington on 2013-04-27
Upgrade stopped in the middle of package installation with error message about package libsoprano4:

unable to install (supposed) new info file `/var/lib/dpkg/tmp.ci/md5sums': Operation not permitted

I have googled for a solution.  There are a lot of postings on other sites for various distributions and packages having to do with errors involving installing new info file to /var/lib/dpkg/tmp.ci  The proposed solutions usually involve using apt-get to force installation, reinstallation, or removal, but whever I try any of those commands for libsoprano4, I get the same error.  One person proposed deleting the entry for the problematic package in /var/lib/dpkg/status, but that didn't have any effect for me.  I also tried to downgrade the libsoprano4 package, but got the same error.

I have added a ppa repository with a more recent version of libsoprano4, but now I get the same error message about that version of the package.

As the result of this error, a lot of packages can't be configured or installed.  In addition, thunar now displays squares rather than alphanumeric characters for all file and folder names.  Not sure whether that's related to the libsoprano4 problem.  Any suggested fix would be greatly appreciated.

---

### Post by dino99 on 2013-04-27
before upgrading a distro, always comment out (deactivate) the third party entries inside /etc/apt/sources.list, then update, and : clean the archives (clean/autoclean/autoremove)
so you should only have the Raring repo activated

---

### Post by John Harrington on 2013-04-27
Thanks for the reply Dino99, but I think you misunderstood my post.  I didn't add the ppa repo until after I had the problem.  The problem occurred when the upgrade process was trying to install the regular Raring version of libsoprano4.  I added the ppa repo in an unsuccessful attempt to solve the problem.

---

