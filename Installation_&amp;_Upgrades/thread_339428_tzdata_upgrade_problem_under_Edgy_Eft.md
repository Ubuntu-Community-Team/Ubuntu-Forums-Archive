---
title: "tzdata upgrade problem under Edgy Eft"
date: 2007-01-15
forum: Installation &amp; Upgrades
---

### Post by rat_poison on 2007-01-15
I hope I've posted this on the proper place

I'm using Ubuntu 6.10
My update manager said that there were updates for some packages. I did the procedure, but package tzdata failed due to 404

Being a Linux newbie, I didn't know if using the terminal would make any difference, so that's what I did.

> ***@***:~$ sudo apt-get upgrade -f tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 313kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/main tzdata 2006p-0ubuntu6.10
  404 Not Found [IP: 147.102.222.211 80]
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2006p-0ubuntu6.10_all.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2006p-0ubuntu6.10_all.deb)  404 Not Found [IP: 147.102.222.211 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?
***@***:~$ sudo apt-get upgrade --fix-missing tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  tzdata
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 313kB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Err [http://gr.archive.ubuntu.com](http://gr.archive.ubuntu.com) edgy-updates/main tzdata 2006p-0ubuntu6.10
  404 Not Found [IP: 147.102.222.211 80]
Failed to fetch [http://gr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2006p-0ubuntu6.10_all.deb](http://gr.archive.ubuntu.com/ubuntu/pool/main/t/tzdata/tzdata_2006p-0ubuntu6.10_all.deb)  404 Not Found [IP: 147.102.222.211 80]


At which point there was no response for quite some time and I was forced to use ctrl+c

Am I doing something wrong, or is the address posted for tzdata wrong?

---

### Post by taurus on 2007-01-15
Remove the **gr** from the repos in /etc/apt/sources.list, update, and run that command again.

```
gksudo gedit /etc/apt/sources.list
sudo apt-get update 
sudo apt-get upgrade -f tzdata
```

---

### Post by rat_poison on 2007-01-15
I backed up sources.list before editing.

I then removed all gr. from any repository address. That's what happened.

> ***@***:~$ sudo apt-get upgrade -f tzdata
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


If I'm getting this right, it means that although there was an upgrade in the gr(eek) repos for tzdata, there was none in the original, default repos.

I'm guessing that the gr suffix on the addresses was there because of the localization for Greece. Since tzdata has to do with timezone info, I'm guessing I actually do need the localization. 
If I remove the ".gr" from the address, won't that mean that I won't be getting the localized packages, but the default (probably US) ones, not only this time, but in the future as well?

What do you suggest, that I keep the original, localized (and possible a bit buggy) addresses, or the edited ones?

---

### Post by taurus on 2007-01-15
Technically, you should use the mirror closest to where you live so if you're from Canada, you use put ca at the beginning.  However, I believe the generic one is the main server and somehow I get a much faster download speed then if I put the us in front of my repos.  I still get the same stuff though...

So, it's up to you if you want to put gr in front of your repos in /etc/apt/sources.list.

---

### Post by rat_poison on 2007-01-15
Thnx! Question Answered!

---

