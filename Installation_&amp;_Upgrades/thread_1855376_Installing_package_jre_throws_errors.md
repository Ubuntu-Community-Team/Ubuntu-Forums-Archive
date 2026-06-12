---
title: "Installing package jre throws errors"
date: 2011-10-06
forum: Installation &amp; Upgrades
---

### Post by sridharpandu on 2011-10-06
I ran the following command to install the open jre

$apt-get install openjdk-6-jre

The package manager throws error "404". This is surprising I am able to ping to the server using the IP and I am able to install other packages.  Is there something wrong? Any help would be appreciated. (BTW I am installing this on a Rackspace VM)

Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/main tzdata all 2011g-0ubuntu0.11.04
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/main tzdata-java all 2011g-0ubuntu0.11.04
  404  Not Found [IP: 91.189.88.40 80]
Err [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) natty-updates/main libcups2 amd64 1.4.6-5ubuntu1.3
  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011g-0ubuntu0.11.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2011g-0ubuntu0.11.04_all.deb)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011g-0ubuntu0.11.04_all.deb](http://archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata-java_2011g-0ubuntu0.11.04_all.deb)  404  Not Found [IP: 91.189.88.40 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.6-5ubuntu1.3_amd64.deb](http://archive.ubuntu.com/ubuntu/pool/main/c/cups/libcups2_1.4.6-5ubuntu1.3_amd64.deb)  404  Not Found [IP: 91.189.88.40 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

---

### Post by sridharpandu on 2011-10-10
Not a single reply! :-(

---

### Post by raja.genupula on 2011-10-10
Hi

please paste here what you got after 

```
sudo apt-get update
```

---

### Post by sridharpandu on 2011-10-11
Thank you. Appreciate it. It went through. How silly. I should have realised it. Not surprising people didn't find it worthy of answering!

---

### Post by raja.genupula on 2011-10-11
Hi please don't think like that.If we seen your thread & we are familiar with the problem then we are always going to help.The main thing is we need to saw the thread in many of threads .some times randomly we are unable to watch some threads.So my dear friend we are ready to help you always.I am glad that your issue got solved.

Enjoy the Ubuntu.

---

### Post by sridharpandu on 2011-10-12
Thank you.

---

