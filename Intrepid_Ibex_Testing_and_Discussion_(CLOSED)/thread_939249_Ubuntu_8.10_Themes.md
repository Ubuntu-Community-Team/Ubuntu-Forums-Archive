---
title: "Ubuntu 8.10 Themes"
date: 2008-10-05
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by patrickaupperle on 2008-10-05
I upgraded to Ubuntu 8.10 today and now some of my themes are messed up. See screen shot.

---

### Post by Sef on 2008-10-05
Moved to Ibex forum.

---

### Post by FuturePilot on 2008-10-05
That's because the gtk2-engines-ubuntulooks has been removed from Intrepid because it is no longer maintained. However it is still in the repos. You can install it with
```
sudo apt-get install gtk2-engines-ubuntulooks
```

---

### Post by patrickaupperle on 2008-10-05
> **FuturePilot said:**
> That's because the gtk2-engines-ubuntulooks has been removed from Intrepid because it is no longer maintained. However it is still in the repos. You can install it with
```
sudo apt-get install gtk2-engines-ubuntulooks
```

Thank you, but that does not look like a good idea
```
patrick@patrick-laptop:~$ sudo apt-get install gtk2-engines-ubuntulooks
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common openssh-blacklist
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  human-theme ubuntu-artwork ubuntu-desktop
The following NEW packages will be installed:
  gtk2-engines-ubuntulooks
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 38.7kB of archives.
After this operation, 365kB disk space will be freed.
Do you want to continue [Y/n]? 

```
Any way to get these old themes working without that package?

---

### Post by smartboyathome on 2008-10-05
> **patrickaupperle said:**
> Thank you, but that does not look like a good idea
```
patrick@patrick-laptop:~$ sudo apt-get install gtk2-engines-ubuntulooks
[sudo] password for patrick: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  nvidia-kernel-common openssh-blacklist
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  human-theme ubuntu-artwork ubuntu-desktop
The following NEW packages will be installed:
  gtk2-engines-ubuntulooks
0 upgraded, 1 newly installed, 3 to remove and 0 not upgraded.
Need to get 38.7kB of archives.
After this operation, 365kB disk space will be freed.
Do you want to continue [Y/n]? 

```
Any way to get these old themes working without that package?

Nope, there is none. I guess you have to apply the colors to clearlooks or some other custom-color-aware theme.

---

### Post by patrickaupperle on 2008-10-05
> **smartboyathome said:**
> Nope, there is none. I guess you have to apply the colors to clearlooks or some other custom-color-aware theme.

Dang, oh well, newhuman looks pretty nice. It works.

---

