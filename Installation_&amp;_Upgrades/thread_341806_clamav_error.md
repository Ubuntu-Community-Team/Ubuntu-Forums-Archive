---
title: "clamav error"
date: 2007-01-19
forum: Installation &amp; Upgrades
---

### Post by shankar1023 on 2007-01-19
hi

please sugesst me how to recover clamav? it has broken in my ubuntu dapper mechine.when i trying to type apt-get install clamav it says

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  clamav: Depends: libclamav1 (>= 0.88.7) but it is not going to be installed
E: Broken packages
root@firewall:/home/shankar# clamscan <path>
bash: syntax error near unexpected token `newline'
root@firewall:/home/shankar# apt-get install clamav
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  clamav: Depends: libclamav1 (>= 0.88.7) but it is not going to be installed
E: Broken packages


I tried it from synaptic package too.but I got the same result.Please help.

Shan

---

### Post by jpeddicord on 2007-01-19
Try running `sudo apt-get update`. It is probably just a problem with an outdated package list.

It also looks as if you downloaded ClamAV from a source other than the repositories. Run `sudo apt-get remove clamav` and then run `sudo apt-get install clamav` to get the latest version from the Ubuntu repositories. If that isn't the case, then it is probably because of what I first mentioned above.

Jacob

---

### Post by shankar1023 on 2007-01-19
Yes I  did all these things but nothing is happen.Now I reinstalled parental control software and it works wonderfully.

But Now am getting this error:

The version off clamav is outdated

Dont panic read.....

and I read the page but I cant upgrade clamav.

Shan.

---

### Post by Handssolow on 2007-01-19
Perhaps I'm getting a related error. On boot-up today a balloon shows I've updates available and I select Update manager. There are 4 updated today but I get the error message-

E: clamav-base: subprocess post install script returned error exit status 1

Any suggestion as to what is the cause and possible solution?

---

### Post by Handssolow on 2007-01-19
Just tried a manual update with

sudo aptitude update
sudo aptitude dist-upgrade

and got these error messages towards the end this in the terminal


Initialising package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Setting up clamav-base (0.88.4-1ubuntu2.1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up clamav-base (0.88.4-1ubuntu2.1) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 clamav-base

Suggestions?

---

### Post by Handssolow on 2007-01-19
I removing clamav-base in Synaptic Package Manager and no errors now appear in either Terminal manual updates or using Update Manager GUI.

Any information? Should I reinstall clamav-base, is it essential?

---

### Post by djeten on 2007-01-27
I have the same problem :confused: 
Any one ?

---

