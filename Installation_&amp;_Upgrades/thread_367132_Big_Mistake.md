---
title: "Big Mistake"
date: 2007-02-21
forum: Installation &amp; Upgrades
---

### Post by Platinum89 on 2007-02-21
I followed the instructions using the installnewthunderbird.sh and everything seemed to go fine. Until however it asked me for the location. I noticed "ca" which I thought meant Canada, however after the upgrade process was complete, it wasn't in english. It was then I realized I should have selected "en-us" so I attempted to run the script again. Only now it fails and I have no idea what the menus say in Thunderbird.

Here's the output...

The most recent release of thunderbird is detected to be 1.5.0.9. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? y
Please choose the localization (language) for thunderbird. Enter the number of your choice from the list below.
0: [http://osuosl.org](http://osuosl.org)
1: <li
2: class="others">[http://suse.osuosl.org](http://suse.osuosl.org)
3: bg
4: ca
5: cs
6: da
7: de
8: el
9: en-GB
10: en-US
11: es-AR
12: es-ES
13: eu
14: fi
15: fr
16: ga-IE
17: gu-IN
18: he
19: hu
20: it
21: ja
22: ko
23: lt
24: mk
25: nb-NO
26: nl
27: pa-IN
28: pl
29: pt-BR
30: ru
31: sk
32: sl
33: sv-SE
34: tr
35: zh-CN
36: <td>http://www.tds.net">
37: <td>[http://osuosl.org](http://osuosl.org)
38: http://osuosl.org/contribute/rackathon"
39: target="_blank">
40: <div
41: class="info">Current
42: bandwidth
43: utilization
44: 206.85
45: Mbit/s
46: |
47: [http://osuosl.org](http://osuosl.org)
Enter your choice of localization: 10
You have chosen localization "en-US". Is that correct [y/n]? y

Updating repositories list

Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates Release
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/restricted Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper/universe Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://ca.archive.ubuntu.com](http://ca.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Fetched 3B in 2s (1B/s)
Reading package lists... Done

Making sure libstdc++5 and the old thunderbird are installed

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Do you want to make a backup of your old mozilla thunderbird profile (~/.mozilla-thunderbird)? Note that if you store your email there, this may take quite a bit of disk space. You may wish to check the size of that directory and the amount of free disk space before you answer this question. Make backup? [y/n]: nOK, proceeding without backup.
ln: creating symbolic link `/home/glenn/.thunderbird' to `/home/glenn/.mozilla-thunderbird': File exists
Previous command did not complete successfully. Exiting.

It doesn't matter if I choose y or n for the backup, it still results in the error above. Is there something I should change in the installnewthunderbird.sh file that will allow it to complete it's task and overwrite the present version so I can have the english version?

Thanks in advance all!

---

### Post by Kateikyoushi on 2007-02-21
Did you try to delete that symlink ?

---

### Post by Platinum89 on 2007-02-21
> **Kateikyoushi said:**
> Did you try to delete that symlink ?

Where would it be? In the script or ???   :)

---

### Post by Kateikyoushi on 2007-02-21
You could uncomment or delete it from the script as well, seems that's the command what stops the process.

---

### Post by Platinum89 on 2007-02-21
It worked well enough. Thanks for the help :)

---

