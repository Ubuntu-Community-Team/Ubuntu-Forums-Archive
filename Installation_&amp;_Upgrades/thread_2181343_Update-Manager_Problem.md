---
title: "Update-Manager Problem"
date: 2013-10-17
forum: Installation &amp; Upgrades
---

### Post by shallowthought on 2013-10-17
Using Ubuntu 12.04 
My Update-Manager has worked flawlessly - until now.

When I try to use Update-Manager I get the message:

Failed to download repository information
Check your internet connection [it seems to work fine]
Details
W:Failed to fetch [http://packages.medibuntu.org/dists/precise/Release.gpg](http://packages.medibuntu.org/dists/precise/Release.gpg)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-amd64/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages](http://packages.medibuntu.org/dists/precise/non-free/binary-i386/Packages)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, W:Failed to fetch [http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en](http://packages.medibuntu.org/dists/precise/non-free/i18n/Translation-en)  Something wicked happened resolving 'packages.medibuntu.org:http' (-5 - No address associated with hostname)
, E:Some index files failed to download. They have been ignored, or old ones used instead.

---

### Post by coffeecat on 2013-10-17
The medibuntu repository has closed. You need to remove references to medibuntu from your sources.list file. If you don't want to edit the sources.list file itself, you can disable medibuntu in update manager. I can't remember the exact details as I haven't used 12.04 for some time, but there should be a settings, preferences or options button in the main window of Update Manager from where you can disable medibuntu.

---

### Post by shallowthought on 2013-10-17
Thanks a lot. That took care of it.
Now, if I only knew how to say the problem is solved ...

---

### Post by Bashing-om on 2013-10-17
shallowthought; Hi !
Solved: 1st post -> thread tools.

[INDENT][INDENT]just my bit to help
[/INDENT][/INDENT]

---

