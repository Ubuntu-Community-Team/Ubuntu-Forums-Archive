---
title: "Ubuntu 22.04.1 LTS (Jammy Jellyfish) upgrade errors"
date: 2022-10-01
forum: Installation &amp; Upgrades
---

### Post by ardakiyat06 on 2022-10-01
First of all, I'm new to the forum. Sorry for grammatical mistakes :).


I get the following errors when I use the upgrade and update commands.

```
sudo apt update && sudo apt upgrade -y
[sudo] password for arda: 
Get:1 http://security.ubuntu.com/ubuntu jammy-security InRelease [110 kB]      
Hit:2 http://oem.archive.canonical.com jammy InRelease                         
Get:3 http://archive.ubuntu.com/ubuntu jammy-updates InRelease [114 kB]        
Get:4 https://esm.ubuntu.com/apps/ubuntu jammy-apps-security InRelease [7.520 B]
Ign:5 https://archive.ubuntu.com/ubuntu jammy InRelease                        
Get:6 https://esm.ubuntu.com/apps/ubuntu jammy-apps-updates InRelease [7.459 B]
Get:7 http://archive.ubuntu.com/ubuntu jammy-backports InRelease [99,8 kB]     
Hit:8 http://archive.ubuntu.com/ubuntu focal InRelease
Ign:5 https://archive.ubuntu.com/ubuntu jammy InRelease
Ign:5 https://archive.ubuntu.com/ubuntu jammy InRelease
Err:5 https://archive.ubuntu.com/ubuntu jammy InRelease                        
  Could not connect to archive.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused)
Fetched 339 kB in 8s (41,7 kB/s)                                               
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
All packages are up to date.
W: Failed to fetch https://archive.ubuntu.com/ubuntu/dists/jammy/InRelease  Could not connect to archive.ubuntu.com:443 (185.125.190.36). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::15). - connect (101: Network is unreachable) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::19). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (185.125.190.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2001:67c:1562::18). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (91.189.91.39). - connect (111: Connection refused) Cannot initiate the connection to archive.ubuntu.com:443 (2620:2d:4000:1::16). - connect (101: Network is unreachable) Could not connect to archive.ubuntu.com:443 (91.189.91.38). - connect (111: Connection refused)
W: Some index files failed to download. They have been ignored, or old ones used instead.
W: Target Packages (main/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (main/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (main/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (main/i18n/Translation-tr) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (main/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (main/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons (main/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (main/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (main/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (main/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (universe/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (universe/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (universe/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (universe/i18n/Translation-tr) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (universe/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (universe/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (universe/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons (universe/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (universe/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (universe/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (universe/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (restricted/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (restricted/i18n/Translation-tr) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (restricted/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (restricted/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons (restricted/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (restricted/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (restricted/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (restricted/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (multiverse/binary-amd64/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (multiverse/binary-i386/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Packages (multiverse/binary-all/Packages) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (multiverse/i18n/Translation-en_US) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (multiverse/i18n/Translation-en) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target Translations (multiverse/i18n/Translation-tr) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (multiverse/dep11/Components-amd64.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11 (multiverse/dep11/Components-all.yml) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-small (multiverse/dep11/icons-48x48.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons (multiverse/dep11/icons-64x64.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target DEP-11-icons-hidpi (multiverse/dep11/icons-64x64@2.tar) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (multiverse/cnf/Commands-amd64) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
W: Target CNF (multiverse/cnf/Commands-all) is configured multiple times in /etc/apt/sources.list:1 and /etc/apt/sources.list:4
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
Receive additional future security updates with Ubuntu Pro.
Learn more about Ubuntu Pro at https://ubuntu.com/pro
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

``` 



In the update application, when I select the main server and refresh, I get the screen of this output. There is no problem with my network connection. how can i solve this problem?

---

### Post by &amp;KyT$0P# on 2022-10-01
Please post the output from running the following command in Terminal -
```
cat /etc/apt/sources.list
```

---

### Post by mIk3_08 on 2022-10-02
ardakiyat06, As what halogen2 suggested please run the command below in your terminal and paste the results here in thread wrap with code. Regards and cheers.
```
cat /etc/apt/sources.list
```

---

### Post by ardakiyat06 on 2022-10-02
> **mIk3_08 said:**
> ardakiyat06, As what halogen2 suggested please run the command below in your terminal and paste the results here in thread wrap with code. Regards and cheers.
```
cat /etc/apt/sources.list
```
 


hi
my response was delayed because the response notification didn't drop

the output of this command is as follows

```
deb http://archive.ubuntu.com/ubuntu focal main universe restricted multiverse
deb http://security.ubuntu.com/ubuntu/ focal-security multiverse main universe restricted
deb http://archive.ubuntu.com/ubuntu focal-updates multiverse main universe restricted
deb http://archive.ubuntu.com/ubuntu focal-backports multiverse main universe restricted



```

---

### Post by tea for one on 2022-10-02
In post no. 1, you list jammy repositories (Ubuntu 22.04)
In post no. 4, you list focal repositories (Ubuntu 20.04)

Which Ubuntu version is installed?

---

### Post by deadflowr on 2022-10-02
Look at and post back the outputs for
```
ls /etc/apt
head /etc/apt/sources.list.d/*
```

The one thing I can tell you right off the bat is there is no https for the archive.ubuntu.
Those archives are plain http.
Which is why it shows those errors. It cannot connect to something that does not exist.

---

