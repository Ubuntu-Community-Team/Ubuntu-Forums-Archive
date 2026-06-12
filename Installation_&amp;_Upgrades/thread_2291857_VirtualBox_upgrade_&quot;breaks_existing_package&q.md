---
title: "VirtualBox upgrade &quot;breaks existing package&quot;"
date: 2015-08-23
forum: Installation &amp; Upgrades
---

### Post by didier.cabale on 2015-08-23
[ubuntu 14.04 LTS]

Hi all,
some weeks ago, I have installed VirtualBox version 4.3.10 via "Ubuntu Software Center". This VirtualBox runs fine -> Ok
Now I need to upgrade VirtualBox to a more recent version.
As I did not notice any "automatic upgrade" menu option from VirtualBox, I downloaded virtualbox-4.3_4.3.30-101610~Ubuntu~raring_amd64.deb from [https://www.virtualbox.org/wiki/Download_Old_Builds_4_3](https://www.virtualbox.org/wiki/Download_Old_Builds_4_3), then opened this file with "Ubuntu Software Center" (mouse right click, ...).
As the installation starts, I get the following Error message: "breaks existing package 'virualbox' that conflict: 'virtualbox'. ..."+
Note I read [http://ubuntuforums.org/showthread.php?t=2061955](http://ubuntuforums.org/showthread.php?t=2061955) and  [http://ubuntuforums.org/showthread.php?t=1957618](http://ubuntuforums.org/showthread.php?t=1957618)

Should I understand that there is no way to upgrade, without uninstalling the existing version?
Thanks for your help
Didier

---

### Post by Novitk on 2015-08-23
Remove everything related to the previous VirtualBox version.

---

### Post by howefield on 2015-08-23
What's the problem with removing the previous version ?

You won't lose the VMs if that is your concern.

---

