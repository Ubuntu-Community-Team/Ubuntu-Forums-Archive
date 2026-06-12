---
title: "having trouble upgrading from 11.04 to 11.10"
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by caotropheus on 2011-10-13
Greetings

For several years I am an Ubuntu user and upgrading a distribution have been as easy as pressing the "upgrade" command and follow the instructions. Not this time it seems. I get this information
 "Failed to fetch [http://pt.archive.ubuntu.com/ubuntu/pool/universe/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb](http://pt.archive.ubuntu.com/ubuntu/pool/universe/g/gmp4/libgmp3c2_4.3.2+dfsg-2ubuntu1_amd64.deb) 403  Forbidden" inside an information window with this description: "Could not download the upgrades

The upgrade has aborted. Please check your Internet connection or installation media and try again. All files downloaded so far have been kept."


and the upgrade Aborts


I have 3 languages set in my system (English, Portuguese and Hebrew) and it seems that I have trouble with a package in Portuguese. 

Please guys, help me solve this problem

Thanks

---

### Post by ezramorris on 2011-10-13
This maybe due to the fact that, since 11.10 has just been released, the server cannot cope well with all the requests. It may just work if you try again later; personally if I'm upgrading like that, I wait a few days for things to calm down a bit.

You could alternatively try a different mirror by changing the "Download from" field in the "Software Sources" application.

---

### Post by caotropheus on 2011-10-14
I overcome the problem. 

It seems there is some issue with a file in the Portuguese server. To solve the problem, inside the "Update Manager" I pressed the command  "Settings..." then I choose "Ubuntu Software" and there I choose "Download from" "main server". It seems that there was some sort of fault in the Portuguese server where I was connected to by default.

Thank you guys for your help.

---

### Post by ezramorris on 2011-10-14
Glad you got it sorted. If you could mark the thread as solved, that would be great. :-)

Thanks.

---

