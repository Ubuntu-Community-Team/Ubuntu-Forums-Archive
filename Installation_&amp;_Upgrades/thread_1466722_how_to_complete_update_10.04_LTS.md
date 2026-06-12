---
title: "how to complete update 10.04 LTS?"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by anker on 2010-04-30
Hi All,  How can I be sure to complete the update?
Updating from 9.10 to 10.04 LTS with some 'stop' 
new kernel not in use, and grub setup, using 'local'
the now new 10.04 LTS as it calls itself is loading and large parts working.

anker

---

### Post by 98cwitr on 2010-04-30
*cat /etc/issue* If it says Ubuntu 10.04 /n /l you're good, just to be sure you can do

*sudo apt-get update && sudo apt-get upgrade*

---

### Post by anker on 2010-04-30
~$ cat /etc/issue
Ubuntu 10.04 LTS \n \l
was the answer,
I'l try your next line of update and upgrade however during update run there was stops
one with msg  new secure kernel was not loaded etc.
I believe most table 'notes' is now reflcting the new 10.04lts system, as a post 'repair' was apparently done?
anker

this is the essence , I think its not importent
[http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/libevdocument2_2.30.1-0ubuntu2_amd64.deb](http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/libevdocument2_2.30.1-0ubuntu2_amd64.deb) 404  Not Found
[http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/libevview2_2.30.1-0ubuntu2_amd64.deb](http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/libevview2_2.30.1-0ubuntu2_amd64.deb) 404  Not Found
[http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/evince_2.30.1-0ubuntu2_amd64.deb](http://ftp.klid.dk/ftp/ubuntu/pool/main/e/evince/evince_2.30.1-0ubuntu2_amd64.deb) 404  Not Found
[http://ftp.klid.dk/ftp/ubuntu/pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu2_all.deb](http://ftp.klid.dk/ftp/ubuntu/pool/main/p/pm-utils/pm-utils_1.3.0-1ubuntu2_all.deb) 404  Not Found
anker

---

