---
title: "Ubuntu 7.10 upgrade - error in packages?"
date: 2007-10-19
forum: Installation &amp; Upgrades
---

### Post by Fafnr on 2007-10-19
Hey,

I just updated to 7.10 - nice and easy, though the servers were ofc. overloaded. :-)

However, during the installation I got about 20 "package error"-messages.

During Update after the installation, I have 3 packages:
ede
rss-glx
semantic

There's a couple of issues for me in this:
1) rss-glx is deselected. And I can't select it.
2) I can't install the other packages.
First, I get the message "Error in package speedbar"
Then, the manager tries to install emacs22 since emacsen depends on it, and it says something about bytecode compiling or something that failed.
Verbatim:
!! Byte-compilation for emacs22 failed!
!! This indicates a bug ...
...
!! and attach the file /tmp/emacs22.F31150

At the end, I get this final error:
E: emacs22-gtk: subprocess post-installation script returned error exit status 1
E: cedet-common: dependency problems - leaving unconfigured
E: speedbar: dependency problems - leaving unconfigured

Regards,

Søren Andersen,
Denmark

---

### Post by Fafnr on 2007-10-21
Update, fixed.

I ran a sudo apt-get autoremove. It listed all the packages there were problems with.
I then removed each manually, and reinstalled it fine, so everything seems to work fine now.
Only problem was that ubuntu-desktop got uninstalled, somehow - but Synaptic fixed that.

Hope this'll help others!

Regards,

Søren

---

### Post by whistlerspa on 2007-10-30
I have exactly the same problem but your solution sounds too scary. Any other way to fix this?

---

### Post by whistlerspa on 2007-10-30
> **whistlerspa said:**
> I have exactly the same problem but your solution sounds too scary. Any other way to fix this?

Further research shows ede and semantic to be part of cedet - hence the conflict? 

Anyway i just removed these two packages and jde went as well. Hope this fixes it. Cedet is still installed.

---

