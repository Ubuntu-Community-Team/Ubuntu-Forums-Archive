---
title: "update manager crashed"
date: 2012-09-27
forum: Installation &amp; Upgrades
---

### Post by rig mechanic on 2012-09-27
Hi folks,
about a week ago software center refused to load when I clicked on it to look for a different photo display software. It began to load then the window shutdown and asked me to send an error report which I did. I then tried to check the update manager as I thought that this had not happened for some time and I also got an error report after it also failed to launch and I now have an icon on my task bar which when clicked gives the following description

:E:Encountered a section with no Package: header, E:Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages, E:The package lists or status file could not be parsed or opened.

so I tried to resolve the problem using terminal, it also didn't work and got the following message:
Fetched 21.0 MB in 48s (436 kB/s)                                              
Reading package lists... Error!
W: GPG error: [http://archive.canonical.com](http://archive.canonical.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) precise Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_precise_partner_binary-amd64_Packages
E: The package lists or status file could not be parsed or opened.

any help resolving this issue would be greatly appreciated thanks.

---

### Post by 2F4U on 2012-09-28
Try the solution mentioned in this thread:

[http://ubuntuforums.org/archive/index.php/t-2050688.html](http://ubuntuforums.org/archive/index.php/t-2050688.html)

---

### Post by rig mechanic on 2012-10-01
Thanks for the information ; It worked perfectly on the second attempt :)

---

