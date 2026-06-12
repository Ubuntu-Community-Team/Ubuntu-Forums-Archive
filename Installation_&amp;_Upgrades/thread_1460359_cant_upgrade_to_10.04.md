---
title: "cant upgrade to 10.04"
date: 2010-04-22
forum: Installation &amp; Upgrades
---

### Post by andru183 on 2010-04-22
trying to try out the new release but when i try to upgrade i get

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.1.42-0ubuntu3_all.deb](http://ie.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/ttf-symbol-replacement_1.1.42-0ubuntu3_all.deb) 404  Not Found

and

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.1.42-0ubuntu3_i386.deb](http://ie.archive.ubuntu.com/ubuntu/pool/universe/w/wine1.2/wine1.2_1.1.42-0ubuntu3_i386.deb) 404  Not Found

is there a fix or is sumit up?

---

### Post by andru183 on 2010-04-22
kept retrying and now im up to a windows error that says

E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.'
Restoring original system state

---

### Post by jaco223 on 2010-04-22
> **andru183 said:**
> kept retrying and now im up to a windows error that says

E:Couldn't configure pre-depend openoffice.org-core for openoffice.org-filter-binfilter, probably a dependency cycle.'
Restoring original system state

Are you upgrading from the terminal using:

```
sudo apt-get update
sudo apt-get -f dist-upgrade
```
Jaco

---

### Post by andru183 on 2010-04-22
no, alt-f2 update-manager -d

another fella that lives round here got me on the way with it, thanks anyway

---

### Post by MisFitt on 2010-04-22
I'm doing it the same way at this moment.
At what point did you get these errors?

---

### Post by andru183 on 2010-04-22
[http://tweetmeme.com/story/209830534/fix-for-openofficeorg-dependency-blocking-jaunty-to-karmic-ubuntu-upgrade-httpbitly10uitr-linux-muralis-scratch-pad](http://tweetmeme.com/story/209830534/fix-for-openofficeorg-dependency-blocking-jaunty-to-karmic-ubuntu-upgrade-httpbitly10uitr-linux-muralis-scratch-pad)
solved it but now ive a network manager applet error

just seems uve to uninstall some packages that are stopping it, and you wont know till you get the errors

sorry forgot to add, it was during the getting new package stage and the installing new package stage

---

