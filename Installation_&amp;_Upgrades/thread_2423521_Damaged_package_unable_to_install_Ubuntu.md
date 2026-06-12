---
title: "Damaged package unable to install Ubuntu"
date: 2019-07-24
forum: Installation &amp; Upgrades
---

### Post by ghettoburger on 2019-07-24
In an attempt to upgrade from Ubuntu 16.04 to Ubuntu 18 I have completely crashed the system.


The  problem initially started with Ubuntu 16 acting weird (after the attempted installation), I was able to  login to the OS but certain folders were inaccessible and I couldn't  drag windows around the screen and finally the sidebars and top bar  vanished. Afterwards I restarted the PC, which made matters worse,  whenever I attempt to login I'm shown a black screen then redirected  back to the login screen. Now whenever I attempt to login it display a  black screen and nothing else.



So  the only way to use the terminal is through the login screen (CTRL + ALT  + F1). I have attempted a fresh install using 2 different usb drives,  both 16 gb in size 1 is 3.0 and the other is 2.0.


Whenever  I attempt to install a new version I get the following error. [B]ACPI BIOS  Error (bug): Method parse/execution failed [\SHAD._STA.SDSO] ,  AE_NOT_FOUND
[/B]


So it seems the only way to resolve the issue is through the command prompt which again is only accessible through he login screen as I cannot login to ubuntu.



These are the commands I have attempted to use in order to fix this strange issue.


1) ```
sudo apt-get update
```. Returns expected results. Where as ```
sudo apt-get upgrade
``` states** E: Unmet dependencies. Try using -f**.


2) ```
sudo apt-get upgrade -f
``` after I press y to download some packages and upgrade others it returns an error.


[B]Errors were encountered while processing: /var/cache/apt/archives/libglx-mesa0_19.0.2-1ubuntu1.1~18.04.02_amd64.deb
[/B]
**E: Sub-process /ust/bin/dpkg returned an error code (1)**



3)  In order to solve this issue I attempt to purge the corrupt package  ```
sudo apt-get purge libglx-mesa0
```. Which in turn returns an error stating.

**E: Unmet dependencies try apt-get -f install with no packages (or specify a solution).**



4)  I try the command above ```
sudo apt-get -f install
```, which states that  there are [B]67 upgraded, 125 newly installed, 13 to remove and 464 not  upgraded.
[/B]
**150 not fully installed or removed.**
[B]I continue by pressing y.
[/B]

It gives me the same error in step 2.


**E: Sub-process /ust/bin/dpkg returned an error code (1)**



5)  Other commands I try include. ```
sudo apt --fix-broken install
``` and ```
sudo  apt-get -o Dpkg::Options::="--force-overwrite" install --fix-broken
``` both  of which give the same error


[B]E: Sub-process /ust/bin/dpkg returned an error code (1)

[/B]I'm open to suggestion and appreciate any help, I don't have important files on the PC so if any potential solution include completely formatting content that's alright I just want to be ableto use the PC again

---

### Post by kansasnoob on 2019-07-27
Try:

```
sudo apt-get clean
```

```
sudo apt-get update
```

```
sudo apt-get dist-upgrade
```

---

### Post by kansasnoob on 2019-07-27
Regarding that ACPI error when trying to install you might find that booting the installation DVD/USB with the acpi=off or noacpi boot parameter works. Or possibly, but less likely acpi=strict. More here about how to do that and other boot options:

[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

