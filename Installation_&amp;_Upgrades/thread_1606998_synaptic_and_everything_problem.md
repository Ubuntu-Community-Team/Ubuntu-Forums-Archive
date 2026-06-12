---
title: "synaptic and everything problem"
date: 2010-10-27
forum: Installation &amp; Upgrades
---

### Post by ashish789456 on 2010-10-27
machine: compaq c700
os: ubuntu 10.04 (lucid)

i tried using from a good broadband connection to install any packege
  - synaptic
  - gdebi
  - apt-get
also - keryx

all of them give same error --

"Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `com.mhwsoft.preader' contains empty filename".

I have been stuck around one more than month for this googling does not help either.

---

### Post by ashish789456 on 2010-10-27
machine: compaq c700
os: ubuntu 10.04 (lucid)

i tried using from a good broadband connection to install any packege
  - synaptic
  - gdebi
  - apt-get
also - keryx

all of them give same error --

"Reading database ... 95%dpkg: unrecoverable fatal error, aborting: 
 files list file for package `com.mhwsoft.preader' contains empty  filename".

I have been stuck around one more than month for this googling does not  help either.

---

### Post by cogier on 2010-10-27
Try the following in Terminal
```
sudo apt-get install -f
```
```
sudo apt-get autoremove
``` 
```
sudo apt-get clean
```
```
sudo apt-get update
```
Then run Update Manager,reboot if requested then try again.

---

### Post by drpjkurian on 2010-10-27
Hi
I googled it for you and found out that it is a bug. Please see follow the instructions in the launchpad [website]("https://bugs.launchpad.net/ubuntu/+source/dpkg/+bug/108189")

---

### Post by ashish789456 on 2010-10-27
ok i have follwed the steps but some of the the download were not done

output is attached

---

### Post by ashish789456 on 2010-10-27
[SIZE=2]what if the concerned list is removed
in my case com.mwsoft.preader as it is said that 
the these are not used and are not required
because i have install many program successfully after that
but the terminal gives the warning about the missing file
but the process complete 
and the installed application also works fine
[/SIZE]

---

