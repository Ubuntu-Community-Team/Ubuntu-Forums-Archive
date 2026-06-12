---
title: "update sources failed"
date: 2012-01-25
forum: Installation &amp; Upgrades
---

### Post by johnsnels59 on 2012-01-25
Hello everyone

I tried to update my resources and i get this error

can someone pls help with this topic

A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://extras.ubuntu.com](http://extras.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 16126D3A3E5C1192 Ubuntu Extras Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) oneiric Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://fr.archive.ubuntu.com](http://fr.archive.ubuntu.com) oneiric-backports Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://extras.ubuntu.com/ubuntu/dists/oneiric/Release](http://extras.ubuntu.com/ubuntu/dists/oneiric/Release)  

W: Some index files failed to download. They have been ignored, or old ones used instead.

thanx in advance

johnsnels.tk

---

### Post by jerrrys on 2012-01-26
Open a terminal 
   
   [https://help.ubuntu.com/community/UsingTheTerminal#In_Unity](https://help.ubuntu.com/community/UsingTheTerminal#In_Unity)
   
   And enter these commands one at a time. Do not enter anything in ( ).
   
    sudo -i                                   
    (this command makes you a superuser)
    
    apt-get clean
    (cleans out a cache)
    
    cd /var/lib/apt
    (go back one directory)
    
    mv lists lists.old
    (rename folder)
    
    mkdir -p lists/partial
    (create a folder)
    
    apt-get clean
    ( as above)
    
    apt-get update
    (updates your system)
    
    That should fix it and welcome to the forum. :D

---

### Post by john.williams43 on 2013-02-06
Fantastic almost a year on to the day and you've solved my problem wonderfully. I'll bookmark this page for another day. ;)

---

### Post by wildmanne39 on 2013-02-06
Old thread closed.

---

