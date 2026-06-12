---
title: "ubuntu locked up during an install"
date: 2009-03-16
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by deathsshadow77 on 2009-03-16
I was installing updates when my system completely froze. I rebooted and entered ubuntu to find that my current resolution is 1600x1200 when the monitor is really 1920x1200.

this is what I get after putting in apt-get upgrade
any help would be appreciated :)

> michael@michael-desktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  totem totem-common totem-mozilla
0 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
4 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up samba (2:3.3.2-1ubuntu1) ...
 * Starting Samba daemons                                                       Segmentation fault (core dumped)
                                                                         [fail]
invoke-rc.d: initscript samba, action "start" failed.
dpkg: error processing samba (--configure):
 subprocess post-installation script returned error exit status 1
Setting up yelp (2.25.1-0ubuntu3) ...
/usr/share/gconf/schemas/yelp.schemas:1: parser error : Document is empty

^
/usr/share/gconf/schemas/yelp.schemas:1: parser error : Start tag expected, '<' not found

^
dpkg: error processing yelp (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of ubuntu-desktop:
 ubuntu-desktop depends on yelp; however:
  Package yelp is not configured yet.
dpkg: error processing ubuntu-desktop (--configure):
 dependency problems - leaving unconfigured
Setting up winbind (2:3.3.2-1ubuntu1) ...
No apport report written because the error message indicates its a followup error from a previous failure.
                           * Starting the Winbind daemon winbind                Segmentation fault (core dumped)
                                                                         [fail]
invoke-rc.d: initscript winbind, action "start" failed.
dpkg: error processing winbind (--configure):
 subprocess post-installation script returned error exit status 139
Processing triggers for menu ...
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 samba
 yelp
 ubuntu-desktop
 winbind
E: Sub-process /usr/bin/dpkg returned an error code (1)


Edit: now that I look at this I think that it may be ext4 data loss

---

### Post by cariboo on 2009-03-17
Have you tried:

```
sudo   apt-get -f install
```

to see if the missing dependencies will get installed. If the above command works, then run:

```
sudo apt-get update &&  sudo apt-get dist-upgrade
```

Jim

---

### Post by deathsshadow77 on 2009-03-17
nope, unfortunately that didnt work

---

### Post by taavikko on 2009-03-17
try removing
```
sudo rm -r /var/lib/apt/list* && sudo apt-get update && sudo apt-get dist-upgrade
```

Note, there's transition going on, so it might be partial upgrade

---

### Post by deathsshadow77 on 2009-03-17
no luck either.
received:
> rm: cannot remove `/var/lib/apt/list*': No such file or directory

---

### Post by taavikko on 2009-03-17
Replace the previous command by
```
sudo rm -r /var/lib/{apt,aptitude}/lists/
```

If it fails, then it is removed already, and upgrade via apt.

---

