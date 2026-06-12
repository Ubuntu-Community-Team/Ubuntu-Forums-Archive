---
title: "Power went off while upgrade and now getting E:The package linux-headers-4.15.0-51-ge"
date: 2019-06-09
forum: Installation &amp; Upgrades
---

### Post by kaysar on 2019-06-09
Hi,
I run apt-get upgrade and before it was finished the electricity gone and my PC went off (I do not have UPS). When electricity came back and I start my PC and run apt-get upgrade again I got following error:

dpkg: error processing package linux-headers-4.15.0-51-generic (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration

After few search in google I tried apt-get clean, dpkg --configure -a etc. but no luck. Now I am getting following messages:

sudo apt-get upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package linux-headers-4.15.0-51-generic needs to be reinstalled, but I can't find an archive for it.

I downloaded the header package deb file and tried to install it but it didn't work and says newer version is already installed.

Is there any solution for this issue or do I need to re-install Lubuntu?
-----------------------------------------------------------
[SOLVED]

Thank you guys for the replies, after few more search I figured out the  solution. Simply reinstalling the package solved the issue. Here is the  command:

```
sudo apt-get install --reinstall linux-headers-4.15.0-51-generic
```

---

### Post by dino99 on 2019-06-09
you can select it and download it from: [https://launchpad.net/ubuntu/+source/linux](https://launchpad.net/ubuntu/+source/linux)
then use 'sudo dpkg -i ...' for installing

---

### Post by cmcanulty on 2019-06-09
Did you try a simple command that often solves problems?

```
sudo  dpkg   --configure  -a
```

---

### Post by kaysar on 2019-06-09
> **cmcanulty said:**
> Did you try a simple command that often solves problems?

```
sudo  dpkg   --configure  -a
```

Thank you for your feedback. Yes I tried that and here is what I get:

```
sudo dpkg --configure -a
dpkg: error processing package linux-headers-4.15.0-51-generic (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.15.0-51-generic; however:
  Package linux-headers-4.15.0-51-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.15.0.51.53); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 linux-headers-4.15.0-51-generic
 linux-headers-generic
 linux-generic
 linux-signed-generic
```

--------------------------------------
and for apt-get upgrade here is what I get:

```
sudo apt-get upgrade 
[sudo] password for nk: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 1,111 kB of archives.
After this operation, 0 B of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 [http://mirror.dhakacom.com/ubuntu-archive](http://mirror.dhakacom.com/ubuntu-archive) bionic-updates/main amd64 linux-headers-4.15.0-51-generic amd64 4.15.0-51.55 [1,111 kB]
Fetched 1,111 kB in 7s (168 kB/s)                                              
dpkg: error processing package linux-headers-4.15.0-51-generic (--configure):
 package is in a very bad inconsistent state; you should
 reinstall it before attempting configuration
dpkg: dependency problems prevent configuration of linux-headers-generic:
 linux-headers-generic depends on linux-headers-4.15.0-51-generic; however:
  Package linux-headers-4.15.0-51-generic is not configured yet.

dpkg: error processing package linux-headers-generic (--configure):
No apport report written because the error message indicates its a followup error from a previous failure.
                          No apport report written because the error message indicates its a followup error from a previous failure.
                                                     dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-generic:
 linux-generic depends on linux-headers-generic (= 4.15.0.51.53); however:
  Package linux-headers-generic is not configured yet.

dpkg: error processing package linux-generic (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of linux-signed-generic:
 linux-signed-generic depends on linux-generic; however:
  Package linux-generic is not configured yet.

dpkg: error processing package linux-signed-generic (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 linux-headers-4.15.0-51-generic
 linux-headers-generic
 linux-generic
 linux-signed-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Hi,
Thank you guys for the replies, after few more search I figured out the solution. Simply reinstalling the package solved the issue. Here is the command:

```
sudo apt-get install --reinstall linux-headers-4.15.0-51-generic
```

Editing the post with this solution so that someone might find it helpful.

---

### Post by cruzer001 on 2019-06-09
Also a neat way to check kernel status that may help in future kernel problems.
```
dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
```
[https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels](https://help.ubuntu.com/community/RemoveOldKernels#Safely_Removing_Old_Kernels)

---

### Post by kaysar on 2019-06-09
It shows the followings:

dpkg -l | tail -n +6 | grep -E 'linux-image-[0-9]+'
rc  linux-image-4.15.0-20-generic         4.15.0-20.21                                amd64        Signed kernel image generic
rc  linux-image-4.15.0-48-generic         4.15.0-48.51                                amd64        Signed kernel image generic
ii  linux-image-4.15.0-50-generic         4.15.0-50.54                                amd64        Signed kernel image generic
ii  linux-image-4.15.0-51-generic         4.15.0-51.55                                amd64        Signed kernel image generic

---

### Post by cruzer001 on 2019-06-09
```
sudo apt autoremove
```
Should clean that little bit up.  Leaving the current and last kernel.

If those "rc" kernels were added manually, then it may be necessary to remove them manually.

---

### Post by deadflowr on 2019-06-09
(RC stands for removed | configurations, which means the package was removed but still leftover configurations exist on the system, 
I personally call it residual configs (rc) even though that's incorrect) 
To remove those a simple one-liner will do
```
dpkg -l | grep ^rc | awk '{print $2}' | xargs sudo apt purge -s
```
run that first as a test run (-s stands for simulate) then if all good switch the -s to -y (-y stands for yes) like
```
dpkg -l | grep ^rc | awk '{print $2}' | xargs sudo apt purge -y
```

---

### Post by cruzer001 on 2019-06-09
My bad, I had release candidates in my head

Thanks deadflowr

---

### Post by deadflowr on 2019-06-09
*apt autoremove --purge* might also work to clear those, but I periodically have used the above commands since before autoremove could clear old kernels.
Truth be told the rc entries are quite negligible in size as config files are small compared to the overall package size.
Typically they're the documentation files for the package in the /usr/share/doc directory.
Clearing them is more an aesthetic thing than a need to free up space.
(dpkg --list output just looks better, and not as confusing without them listed)

---

