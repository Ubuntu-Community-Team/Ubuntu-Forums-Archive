---
title: "Can't Install OpenShot Because of Dependencies"
date: 2012-07-14
forum: Installation &amp; Upgrades
---

### Post by Utnubu42 on 2012-07-14
After I updated to 12.04, OpenShot wouldn't open, so I uninstalled it. Now, when I try to reinstall it in terminal, the installation fails and the following appears: 
```
The following packages have unmet dependencies:
 openshot : Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable or
                     python-mlt but it is not installable
E: Unable to correct problems, you have held broken packages.
```I currently have python-mlt5 installed. When, in Synaptic, I try to replace it with the older python-mlt3, it says python-mlt depends on libmlt4 and libmlt++3. However,those two packages are irreconcilable because libmlt++3 depends on libmlt5, not libmlt4.

How can I install Openshot?

Thanks.

---

### Post by Utnubu42 on 2012-07-19
Bump.

---

### Post by ptn107 on 2012-07-19
Remove python-mlt5.  Since you're using 12.04 you have absolutely no reason to be running quantal packages.  This is causing your problems.  Make sure your sources.list contains sources for only precise.  Then you can install the appropriate versions of the packages this way:

```
sudo apt-get update
sudo apt-get install libmlt4=0.7.6+git20120204-2 libmlt++3=0.7.6+git20120204-2 libmlt-data=0.7.6+git20120204-2 python-mlt3=0.7.6+git20120204-2
```

---

### Post by Utnubu42 on 2012-07-21
Thanks, ptn107. I followed your instructions and also inputted the following:
```
sudo apt-get install melt=0.7.6+git20120204-2
```because OpenShot requires melt.

OpenShot installed, but it crashes whenever I try to open it, showing the following message:
```
------------------------- ERROR 1 ------------------------------
Failed to import 'from openshot import main'
Error Message: cannot import name main
----------------------------------------------------------------
--------------------------------
   OpenShot (version 1.4.2)
--------------------------------
Process no longer exists: 19444.  Creating new pid lock file.

Detecting formats, codecs, and filters...
Segmentation fault (core dumped)
```How could I determine the source of this problem?

---

### Post by Utnubu42 on 2012-07-23
Bump.

---

### Post by ptn107 on 2012-07-24
Make sure openshot is the correct version.  Your version 1.4.2 (1.4.2-1.1build1) is from quantal.  In precise it's 1.4.0-1ubuntu1.
I think your getting the error because 1.4.2 is supposed to use python-mlt5 and were trying to make it use python-mlt3.

```
sudo apt-get install openshot=1.4.0-1ubuntu1 openshot-doc=1.4.0-1ubuntu1
```

---

### Post by Utnubu42 on 2012-07-24
I downgraded to OpenShot 1.4.0 as you suggested, but the same error occurs with the same message (with 1.4.2 changed to 1.4.0.)

---

### Post by tw.engel@gmail.com on 2012-07-24
> **Utnubu42 said:**
> After I updated to 12.04, OpenShot wouldn't open, so I uninstalled it. Now, when I try to reinstall it in terminal, the installation fails and the following appears: 
```
The following packages have unmet dependencies:
 openshot : Depends: python-mlt3 but it is not going to be installed or
                     python-mlt2 but it is not installable or
                     python-mlt but it is not installable
E: Unable to correct problems, you have held broken packages.
```I currently have python-mlt5 installed. When, in Synaptic, I try to replace it with the older python-mlt3, it says python-mlt depends on libmlt4 and libmlt++3. However,those two packages are irreconcilable because libmlt++3 depends on libmlt5, not libmlt4.

How can I install Openshot?

Thanks.

Hi, I am a Ubuntu newbie, but I just resolved a similar problem myself. I had problems with installing the package librapi2-tools. It depends on librapi2, which depends on libsynce0, which is installed, but not detected by APT when trying to install librapi2. The solution I found was to use apt-get build-dep librapi2 (suddenly 45 Mb to download though).

Best wishes!

---

### Post by Utnubu42 on 2012-07-24
That does share similarities with my installation problem. However, I'm now having trouble actually running the program I installed.

---

### Post by tw.engel@gmail.com on 2012-07-24
I am sorry,

my suggestion did not help much for myself either. Now I try to run apt-get dist-upgrade ... 

I hope it helps!

---

### Post by Utnubu42 on 2012-07-28
Can anyone explain why the following message appears when I start up Openshot via Terminal? (it crashes every time):```
------------------------- ERROR 1 ------------------------------ 
Failed to import 'from openshot import main' 
Error Message: cannot import name main
 ---------------------------------------------------------------- --------------------------------    
OpenShot (version 1.4.2) 
-------------------------------- 
Process no longer exists: 19444.  Creating new pid lock file. 
 
Detecting formats, codecs, and filters... 
Segmentation fault (core dumped)
```

---

### Post by Janiporo on 2012-09-23
Somewhere it said that your error message is a problem with outdated MLT. I had it my self. Tryed to update it and it uninstalled openshot + kdenlive.

Result is here --> [http://ubuntuforums.org/showthread.php?p=12256229#post12256229](http://ubuntuforums.org/showthread.php?p=12256229#post12256229)

---

