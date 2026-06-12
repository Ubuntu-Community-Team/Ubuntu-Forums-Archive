---
title: "Can't install updates"
date: 2011-03-19
forum: Installation &amp; Upgrades
---

### Post by ten mooses on 2011-03-19
Hello!
I've been trying for a while to install my updates but can't get anything to install. It seems to download everything ok but after that i get this error message. 
Package operation failed
The installation or removal of a software package failed
details:
installArchives() failed:  Extract templates from packages: 14% Extract templates from packages: 29% Extract templates from packages: 44% Extract templates from packages: 59% Extract templates from packages: 74% Extract templates from packages: 89% Extract templates from packages: 100% 
Preconfiguring packages ... 
 Extract templates from packages: 14% Extract templates from packages: 29% Extract templates from packages: 44% Extract templates from packages: 59% Extract templates from packages: 74% Extract templates from packages: 89% Extract templates from packages: 100% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `linux-image-2.6.32-25-generic' contains empty filename 

The same happens when i try to install anything at all for example if i try to install the game assaultcube from the  software centre then i get the same error with this under the details section:

installArchives() failed: Selecting previously deselected package libopenal1. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `linux-image-2.6.32-25-generic' contains empty filename 

Any help would be very much appreciated. I never had this problem until a couple of months ago and have no idea how to fix it. I should warn you all that i'm a total noob when it comes to doing anything in the terminal.

---

### Post by ten mooses on 2011-03-19
please?

---

### Post by 5149.5 on 2011-03-19
See what "sudo apt-get check" does.

---

### Post by ten mooses on 2011-03-19
thanks for replying!

Reading package lists... Done
Building dependency tree       
Reading state information... Done

that seems to be it

---

### Post by 5149.5 on 2011-03-19
Try " sudo apt-get install -f linux-image-2.6.32-25-generic".

---

### Post by ten mooses on 2011-03-19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-image-2.6.32-35-generic
E: Couldn't find any package by regex 'linux-image-2.6.32-35-generic'

---

### Post by ten mooses on 2011-03-19
opps :)

---

### Post by ten mooses on 2011-03-19
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-image-2.6.32-25-generic is already the newest version.
The following packages were automatically installed and are no longer required:
  kdesudo update-manager-kde
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 198 not upgraded.
privateuser@privateuser-laptop:~$

---

### Post by ten mooses on 2011-03-19
bump

---

### Post by desana on 2011-03-19
try "sudo apt-get autoremove" and after that "sudo apt-get autoclean"

Hopefully this will sort it out

---

### Post by ten mooses on 2011-03-19
still the same error message

installArchives() failed:  Extract templates from packages: 14% Extract templates from packages: 29% Extract templates from packages: 44% Extract templates from packages: 59% Extract templates from packages: 74% Extract templates from packages: 89% Extract templates from packages: 100% 
Preconfiguring packages ... 
 Extract templates from packages: 14% Extract templates from packages: 29% Extract templates from packages: 44% Extract templates from packages: 59% Extract templates from packages: 74% Extract templates from packages: 89% Extract templates from packages: 100% 
Preconfiguring packages ... 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `linux-image-2.6.32-25-generic' contains empty filename

---

### Post by ten mooses on 2011-03-20
bump

---

### Post by ten mooses on 2011-03-20
bump

---

### Post by ten mooses on 2011-03-20
bump :(

---

### Post by ProntoAnthony on 2011-03-20
When I have a problem like this on Update Manager I try installing the packages using Synaptic Package Manager to do the deed.

---

### Post by sikander3786 on 2011-03-21
@ **ten mooses**:

Try using an older dpkg/status file.

Backup your existing one:

```
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status.bad
```

Setup the older one:

```
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
```

Now run and post the complete outputs of these commands please.

```
sudo apt-get update && sudo apt-get install -f
```
```
sudo dpkg--configure -a
```

---

