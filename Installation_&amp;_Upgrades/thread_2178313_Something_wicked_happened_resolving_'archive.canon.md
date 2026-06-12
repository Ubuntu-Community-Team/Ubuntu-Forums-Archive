---
title: "Something wicked happened resolving 'archive.canonical.com:http'"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2013-10-02
Since yesterday I cannot update ubuntu as I'm getting errors:

----------------------------------------------------------------------------------------------
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en_AU                                                                                    
Ign [http://archive.canonical.com](http://archive.canonical.com) raring/partner Translation-en                                                                                       
Fetched 18.9 MB in 32s (574 kB/s)                                                                                                                    
W: Failed to fetch [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'archive.canonical.com:http' (-11 - System error)

W: Failed to fetch [http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/raring/Release.gpg](http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu/dists/raring/Release.gpg)  Something wicked happened resolving 'ppa.launchpad.net:http' (-11 - System error)

E: Some index files failed to download. They have been ignored, or old ones used instead.
------------------------------------------------------------------------------------------------------------------------------------------

I don't think its dns related as I get fetch the png file

-------------------------------------------------------------------
llist@LeosLinux:~$ wget [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)
--2013-10-03 07:36:44--  [http://archive.canonical.com/ubuntu/dists/raring/Release.gpg](http://archive.canonical.com/ubuntu/dists/raring/Release.gpg)
Resolving archive.canonical.com (archive.canonical.com)... 91.189.92.150, 91.189.92.191, 2001:67c:1360:8c01::16, ...
Connecting to archive.canonical.com (archive.canonical.com)|91.189.92.150|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 933
Saving to: 'Release.gpg’

-----------------------------------------------------------

Thanks


100%[============================================================================================================>] 933         --.-K/s   in 0s      

2013-10-03 07:36:46 (221 MB/s) - 'Release.gpg’ saved [933/933]

---

