---
title: "Strange problem upgrading warty to hoary..."
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Posi on 2005-04-18
Hi Everybody!!

I've got a strange problem when trying to upgrade my wart to hoary. As I couldn't find any solution in the forums I hope this has not yet been discussed - otherwise please point me to the right thread...

I've got a well running warty installation (up to date) and wanted to upgrade to hoary this morning. So what I did is (like described on the many pages.. - and: I've years of experience in working with debian):

```

root@devil:~ # cd /etc/apt
root@devil:~ # vi sources.list

```
***(Changed sources.list...)***

```

root@devil:/etc/apt # cat sources.list

deb http://archive.ubuntu.com/ubuntu/ hoary main universe multiverse restricted

root@devil:/etc/apt # apt-get update
Get:1 http://archive.ubuntu.com hoary/main Packages [636kB]
Get:2 http://archive.ubuntu.com hoary/main Release [93B]
Get:3 http://archive.ubuntu.com hoary/universe Packages [2853kB]
Get:4 http://archive.ubuntu.com hoary/universe Release [97B]
Get:5 http://archive.ubuntu.com hoary/multiverse Packages [111kB]
Get:6 http://archive.ubuntu.com hoary/multiverse Release [99B]
Get:7 http://archive.ubuntu.com hoary/restricted Packages [4109B]
Get:8 http://archive.ubuntu.com hoary/restricted Release [99B]
Fetched 3604kB in 2s (1740kB/s)
Reading Package Lists... Done

```
***Still looks good to me...***

```

root@devil:/etc/apt # apt-get dist-upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
Calculating Upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
***I tried different variants of this but alway ending up 0 packages to upgrade. Whenever I tried to install something new:***

```

root@devil:/etc/apt # apt-get install inkscape
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  inkscape: Depends: libatk1.0-0 (>= 1.9.0) but 1.8.0-1ubuntu2 is to be installed
            Depends: libgcc1 (>= 1:4.0-0pre6ubuntu4) but 1:3.4.2-2ubuntu1 is to be installed
            Depends: libglib2.0-0 (>= 2.6.0) but 2.4.7-0ubuntu2 is to be installed
            Depends: libglibmm-2.4-1 (>= 2.6.1) but it is not going to be installed
            Depends: libgtk2.0-0 (>= 2.6.0) but 2.4.10-1ubuntu1 is to be installed
            Depends: libgtkmm-2.4-1 (>= 2.6.1) but it is not going to be installed
            Depends: libpango1.0-0 (>= 1.8.1) but 1.6.0b-0ubuntu1 is to be installed
            Depends: libpng12-0 (>= 1.2.8rel) but 1.2.5.0-7ubuntu1 is to be installed
            Depends: libxml2 (>= 2.6.17) but 2.6.11-3ubuntu1.1 is to be installed
E: Broken packages

```

Something seems to be totally **screwed** here -- any ideas how to solve this? I don't wanna to reinstall this machine again... 

Thanks you,
  Posi

---

### Post by Posi on 2005-04-18
Hi Again!

I'm back with the answer to my own question... :) 
Reason for this problem was that I already had a hoary repository while using warty and I used pinning:

```

root@devil:/etc/apt # cat preferences

Package: *
Pin: release a=warty
Pin-Priority: 60

Package: *
Pin: release a=hoary
Pin-Priority: 10

```

So after changing to priority for hoary to 100 it works like expected:

```

.....
724 upgraded, 99 newly installed, 12 to remove and 1 not upgraded.
Need to get 479MB of archives.
After unpacking 167MB of additional disk space will be used.
Do you want to continue? [Y/n]

```

Maybe this helps somebody running into similar problems...

Have a nice and enjoy you Ubuntu... :)
  Posi

---

### Post by TravisNewman on 2005-04-18
Glad you got that working.

I changed your first post to delete some dirty language. No big deal, but lets try to keep that to a minimum. Thanks!

---

