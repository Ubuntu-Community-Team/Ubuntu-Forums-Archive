---
title: "Apt-get : How to install to a particular directory or partition?"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by mohd.sadiq on 2007-07-26
**Apt-get : How to install to a particular directory or partition?**

I wanted to know if there is an option in apt-get to install files to a** particular directory/partition?**

To be more specific, is there any equivalent in apt-get for the command "*yum --intallroot=<dir> install <package>*" which will install all files in relation to the <dir> directory as root.

I understand that there is a 'fakeroot' option, but it just fakes root priviledges while installing packages, but this is not what I want.
I have searched a lot about this but couldn't find any information.

Any help would be appreciated.

---

### Post by az on 2007-07-26
Do you just want to unpack the files in the package or do you want to install it into another system (in a chroot, for example)?

I think you can do what you describe by changing apt's configuration.  Using dpkg, you do that by setting the --root option to point to your target directory.

If you just want a file from the package, just extract the package (use dpkg -X or open the deb in file-roller - it's just an ar archive.)

If you want a full-fledged apt in a different target directory, just chroot into that directory and run apt-get.

---

### Post by mohd.sadiq on 2007-07-26
Thanks for your help. Will try what you said.

---

