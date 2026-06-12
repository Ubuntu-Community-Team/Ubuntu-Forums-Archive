---
title: "can't open the update manager and synoptic manager"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by PeterKogler on 2010-08-09
I got Linux version easypeasy for netbooks. I am new on Linux so have mercy with me if my questions are stupid. After downloading the proposed updates in the update manager it gave me a error message and I could not open my update manager after that (or my synaptic package manager). How can I solve this?
The error message was:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:error occurred when treating the modemmanager (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:Package list or the status file could not be interpreted or opened.'

How do I solve this.
Thankful for help
// Peter Kogler

---

### Post by garvinrick4 on 2010-08-09
> **PeterKogler said:**
> I got Linux version easypeasy for netbooks. I am new on Linux so have mercy with me if my questions are stupid. After downloading the proposed updates in the update manager it gave me a error message and I could not open my update manager after that (or my synaptic package manager). How can I solve this?
The error message was:

Could not initialize the package information

An unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:

'E:Problem parsing dependency Depends, E:error occurred when treating the modemmanager (NewVersion1), E:Problem with MergeList /var/lib/dpkg/status, E:Package list or the status file could not be interpreted or opened.'

How do I solve this.
Thankful for help
// Peter Kogler First open a Terminal and use this code:

```
sudo apt-get -f install
```

It is code to try to fix broken packages.

---

### Post by garvinrick4 on 2010-08-09
If that does not work in previous. Open a Terminal and code:

```
sudo apt-get purge synaptic
```
```
sudo apt-get purge update-manager
```
```
sudo apt-get clean
```
```
sudo apt-get install synaptic
```
```
sudo apt-get install update-manager
```

You have a cache of packages in your install you are removing them
and fetching new packages from repository:

---

### Post by PeterKogler on 2010-08-11
Than you for help but it still does not work
I tried it with the commands that you gave me but it did not seem to work
This was the message I recieved (It says that an error occurred when dealing with modemmanager:
peter@peter-laptop:~$ sudo apt-get -f install
[sudo] password for peter: 
Läser paketlistor... Fel!
E: Problem parsing dependency Depends
E: Fel uppstod vid hantering av modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.
peter@peter-laptop:~$ sudo apt-get purge synaptic
Läser paketlistor... Fel!
E: Problem parsing dependency Depends
E: Fel uppstod vid hantering av modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.
peter@peter-laptop:~$ sudo apt-get purge update-manager
Läser paketlistor... Fel!
E: Problem parsing dependency Depends
E: Fel uppstod vid hantering av modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.
peter@peter-laptop:~$ sudo apt-get install synaptic
Läser paketlistor... Fel!
E: Problem parsing dependency Depends
E: Fel uppstod vid hantering av modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.
peter@peter-laptop:~$ sudo apt-get install update-manager
Läser paketlistor... Fel!
E: Problem parsing dependency Depends
E: Fel uppstod vid hantering av modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: Paketlistan eller statusfilen kunde inte tolkas eller öppnas.
peter@peter-laptop:~$ ^C
peter@peter-laptop:~$ 

Is there another solution?

---

### Post by PeterKogler on 2010-08-11
Just fixed a translation so you do not need to learn swedish:
peter@peter-laptop:~$ sudo apt-get -f install
[sudo] password for peter: 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$

---

### Post by linux18 on 2010-08-11
```

sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center
sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade

```
run this twice

---

### Post by PeterKogler on 2010-08-11
it does not seem to work now either

this was the error message I recieved
peter@peter-laptop:~$ sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center
[sudo] password for peter: 
synaptic: no process found
peter@peter-laptop:~$ sudo killall synaptic && sudo killall aptitude && sudo killall mintinstall && sudo killall software-center
synaptic: no process found
peter@peter-laptop:~$ sudo rm /var/lib/dpkg/lock && sudo rm /var/cache/apt/archives/lock && sudo rm /var/lib/apt/lists/partial/* && sudo rm /var/cache/apt/*.bin 
peter@peter-laptop:~$ sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ') 
dpkg-query: parse error, in file '/var/lib/dpkg/status' near line 6261 package 'modemmanager':
 `Depends' field, syntax error after reference to package `libgudev-1.0'
dpkg: parse error, in file '/var/lib/dpkg/status' near line 6261 package 'modemmanager':
 `Depends' field, syntax error after reference to package `libgudev-1.0'
peter@peter-laptop:~$ sudo apt-get -f install && sudo apt-get clean && sudo apt-get autoclean 
Reading package lists... Error!
E: Problem parsing dependency Depends
E: Error occurred while processing modemmanager (NewVersion1)
E: Problem with MergeList /var/lib/dpkg/status
E: The package lists or status file could not be parsed or opened.
peter@peter-laptop:~$ sudo apt-get autoremove && sudo apt-get update && sudo apt-get --fix-broken upgrade

it there another way?
Thanks a lot

---

