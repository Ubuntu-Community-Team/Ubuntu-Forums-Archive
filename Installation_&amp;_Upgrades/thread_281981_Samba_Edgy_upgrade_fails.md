---
title: "Samba Edgy upgrade fails"
date: 2006-10-21
forum: Installation &amp; Upgrades
---

### Post by jlhughes on 2006-10-21
I've updated from Dapper to EdgyRC.  There were several errors but I was able to repeat sudo apt-get upgrade until everthing was fixed EXCEPT...

Here's the error message I get when trying to upgrade:
```

john@ubuntu_laptop:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  samba
Recommended packages:
  smbldap-tools
The following packages will be upgraded:
  samba
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/2904kB of archives.
After unpacking 123kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Preconfiguring packages ...
Selecting previously deselected package samba.
(Reading database ... 122168 files and directories currently installed.)
Preparing to replace samba 3.0.22-1ubuntu3.1 (using .../samba_3.0.22-1ubuntu4_i386.deb) ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: warning - old pre-removal script returned error exit status 102
dpkg - trying script from the new package instead ...
invoke-rc.d: dangling symlink: /etc/rc2.d/K09samba
dpkg: error processing /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 102
Errors were encountered while processing:
 /var/cache/apt/archives/samba_3.0.22-1ubuntu4_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

When I attempt to REMOVE samba using Synaptic, I get this message:

E: samba: subprocess pre-removal script returned error exit status 102

---

### Post by LordYama on 2006-10-26
This problem was driving me around the bend. To fix it, I ran ```
sudo rm -f /etc/rc2.d/K09samba
```

---

### Post by jlhughes on 2006-10-26
That did the trick. Thanks

---

### Post by Ambimom on 2006-10-27
Thank you, thank you, thank you, thank you, thank you, thank you....a million times.  I was going nuts trying to figure this out.  It worked for me too!

I had the same samba problem.

---

### Post by chunkstyle on 2006-10-27
Thank you!

---

### Post by ztirffritz on 2006-10-28
> **LordYama said:**
> This problem was driving me around the bend. To fix it, I ran ```
sudo rm -f /etc/rc2.d/K09samba
```

I'm glad that I finally fixed this with your help, but I want to know how you knew to remove that file?  What led you to take that particular file out?

---

### Post by Sionide on 2006-10-28
Well I had this problem too... That Samba thing happened a while back on Dapper when the package was updated so I remembered that I had to remove the dodgy Symlink.

---

### Post by LordYama on 2006-10-28
> **ztirffritz said:**
> I'm glad that I finally fixed this with your help, but I want to know how you knew to remove that file?  What led you to take that particular file out?

When upgrading, dpkg complains about /etc/rc2.d/K09samba being a dangling symlink, i.e. a symbolic link that points to something non-existant. I tried removing it, and voilà! The upgrade worked.

---

### Post by clooch on 2006-10-30
Thank you so much, I have been pulling m hair out on this one.

---

### Post by daynah on 2006-11-01
Man you should have seen the hisses I made at my computer after it had this problem when I had fixed it after upgrading to dapper! I kept sitting there thinking, "I remember the solution was really easy but WHAT WAS IT!"

Thanks man. :) Does samba work after this? I've never tried it.

---

