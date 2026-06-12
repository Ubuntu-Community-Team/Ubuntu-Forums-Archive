---
title: "find when a package was originally installed"
date: 2018-08-25
forum: Installation &amp; Upgrades
---

### Post by Skaperen on 2018-08-25
the file _**[SIZE=1][FONT=courier new]/var/log/dpkg.log[/FONT][/SIZE]**_ shows very recent package update dates.  but it only goes back so far.  my guess is that apt* commands are keeping it under some maximum size.  all the information in that file on my laptop is from this month, the earliest being 2018-08-06 18:44:59.  there are a bunch of history files in _**[SIZE=1][FONT=courier new]/var/log/apt[/FONT][/SIZE]**_ but they only go back about one year (2017-08) but i need to go back to about 2016-06.

**[FONT=century gothic]is there a way to find when a package was *originally* *installed*?[/FONT]**

i do *not* need this for packages included in the original system install (i did an install of this 16.04 LTS system fresh.  all partitions of this 1TB disk were wiped to binary zero before starting the install which then had to format everything.  so nothing remained from the previous 14.04 LTS system.  i plan to the same for my next major upgrade which will probably be 20.04 LTS a couple months after it is out (June/July tends to be a convenient time and it will have had a couple months of shaking out bugs).  yes, i am skipping 18.04.

---

### Post by ubfan1 on 2018-08-26
If you only need the date to determine if the package was part of the original installation, you can get that info with the following:
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u) 
assuming you still have the initial-status.gz file from the installation.
The showmanual tends to pick up package updates too, so the unique sort gets rid of those.

---

### Post by Skaperen on 2018-08-30
i had 2 reasons to get the original install date.  one was the curiosity of what packages were in the original install and what has been added on since then.  the other was to inter-sort them with pypi packages installed with pip (from package python3-pip) to see what has been done in the past, post-install, regarding a mess i have (common packages installed from both sources) to figure out how far back i can uninstall/remove packages and keep the system as coherent as i can.  my problem is that a recent ubuntu upgrade of all packages resulted in some kinds of breakage across the inconsistent mix of ubuntu and pypi packages i have.  for example i had packages python{,3}-{boto,boto3,botocore} all installed as well as the pypi packages (different names).  this duplicative mix somehow worked until a recent upgrade.  these and some other things written in python now do not work.  looking into why, i found the mess.  i uninstalled/removed all the boto packages and installed back just the pypi versions and just botocore and boto3 and a lot of things are back to working.

---

### Post by Skaperen on 2018-08-30
> **ubfan1 said:**
> If you only need the date to determine if the package was part of the original installation, you can get that info with the following:
comm -23 <(apt-mark showmanual | sort -u) <(gzip -dc /var/log/installer/initial-status.gz | sed -n 's/^Package: //p' | sort -u) 
assuming you still have the initial-status.gz file from the installation.
The showmanual tends to pick up package updates too, so the unique sort gets rid of those.

i am getting 2 error messages from that command:

```
comm: file 2 is not in sorted order
comm: file 1 is not in sorted order
```

that, and the list it outputs has packages i definitely installed well after the system was installed from a USB memory stick with the ISO image dd-d to it (bootable as a small hard drive).

this got me the list i expected:

```
(gunzip|egrep '^Package: '|cut -c 10-|sort) < /var/log/installer/initial-status.gz
```

thanks for the clue of what file to look at.  it was dated 2016-05-02 which is about when i remember doing the original install.

so my next project for fun is to install exactly that set of packages targeting an initially empty root directory and see how much that varies from an install of that ISO image in a virtual machine.

---

### Post by ubfan1 on 2018-08-30
Don't know what caused the out-of-order  errors, since a cut and paste of the command from above works as expected on my system.

---

