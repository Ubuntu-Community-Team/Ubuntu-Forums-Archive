---
title: "Getting an error mess when trying to download mediubuntu packages from repository????"
date: 2011-03-13
forum: Installation &amp; Upgrades
---

### Post by Amil-Leone on 2011-03-13
Hello all,

I  am having some issues downloading from the repository. I am using ubuntu 10.10 (maverick) and I continue to get an error message stating that all indexes could not be downloaded.......

The repository may no longer be available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and ensure the repository address in the preferences is correct.


and then these messages........


Failed to fetch [http://packages.mediubuntu.org/dists/maverick/Release.gpg](http://packages.mediubuntu.org/dists/maverick/Release.gpg)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/free/i18n/Translation-en.bz2](http://packages.mediubuntu.org/dists/maverick/free/i18n/Translation-en.bz2)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2](http://packages.mediubuntu.org/dists/maverick/free/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2](http://packages.mediubuntu.org/dists/maverick/non-free/i18n/Translation-en.bz2)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2](http://packages.mediubuntu.org/dists/maverick/non-free/i18n/Translation-en_US.bz2)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/free/source/Sources.gz](http://packages.mediubuntu.org/dists/maverick/free/source/Sources.gz)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/non-free/source/Sources.gz](http://packages.mediubuntu.org/dists/maverick/non-free/source/Sources.gz)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/free/binary-i386/Packages.gz](http://packages.mediubuntu.org/dists/maverick/free/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Failed to fetch [http://packages.mediubuntu.org/dists/maverick/non-free/binary-i386/Packages.gz](http://packages.mediubuntu.org/dists/maverick/non-free/binary-i386/Packages.gz)  Something wicked happened resolving 'packages.mediubuntu.org:http' (-5 - No address associated with hostname)
Some index files failed to download, they have been ignored, or old ones used instead.



Can anyone pls be of help to me????? I have shifted through other posts to find solutions others used, but not getting anywhere...... I appreciate the help.

-Amil:confused:

---

### Post by kagerato on 2011-03-13
No address associated with hostname means that your system isn't resolving the host, in this instance "packages.mediubuntu.org" to a valid IP address.

Can you actually reach mediubuntu.org in a web browser?  (How about [http://packages.mediubuntu.org/](http://packages.mediubuntu.org/)  ? )  I can't, so I'm inclined to think that URL is wrong.

Shouldn't it be [http://packages.medibuntu.org/](http://packages.medibuntu.org/)  ?  That seems correct.

You'll need to update the repositories list in `/etc/apt/sources.list` to fix it.  You can do this with Synaptic or several other GUI package managers, or by manually editing that text file in a text editor (with root permission via sudo, gksu, or similar).

---

