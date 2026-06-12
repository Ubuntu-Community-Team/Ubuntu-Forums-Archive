---
title: "apt-get install ERROR!"
date: 2011-06-15
forum: Installation &amp; Upgrades
---

### Post by subchief on 2011-06-15
Hey guys,
i installed natty and run synaptic but my Internet got disconnected before the download was complete. Now if i try install an application from the terminal i get this error message.

"Reading package lists... Error!
E: Encountered a section with no Package: header
E: Problem with MergeList /var/lib/apt/lists/archive.canonical.com_ubuntu_dists_natty_partner_binary-i386_Packages
E: The package lists or status file could not be parsed or opened."

Any help?
Thank u!

---

### Post by falko on 2011-06-15
Please try if ```
sudo apt-get update
``` dolves the problem.

---

### Post by mörgæs on 2011-06-15
[http://ubuntuforums.org/showpost.php?p=10938431&postcount=7](http://ubuntuforums.org/showpost.php?p=10938431&postcount=7)

---

