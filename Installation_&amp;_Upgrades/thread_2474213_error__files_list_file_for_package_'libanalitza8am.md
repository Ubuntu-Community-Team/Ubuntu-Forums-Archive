---
title: "error : files list file for package 'libanalitza8:amd64' is missing final newline"
date: 2022-04-24
forum: Installation &amp; Upgrades
---

### Post by El Bartolomew on 2022-04-24
I am having difficulties, my boot sector is full and I am unable to remove old linux headers.


```
[FONT=monospace][COLOR=#000000]sudo apt list --installed | grep linux-image    [/COLOR]

WARNING: apt does not have a stable CLI interface. Use with caution in scripts.

[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.11.0-43-generic/focal-updates,focal-security,now 5.11.0-43.47~20.04.2 amd6[/COLOR]
4 [installed]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.11.0-44-generic/focal-updates,focal-security,now 5.11.0-44.48~20.04.2 amd6[/COLOR]
4 [installed]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-30-generic/focal-updates,focal-security,now 5.13.0-30.33~20.04.1 amd6[/COLOR]
4 [installed]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-37-generic/focal-updates,focal-security,now 5.13.0-37.42~20.04.1 amd6[/COLOR]
4 [installed]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-39-generic/focal-updates,focal-security,now 5.13.0-39.44~20.04.1 amd6[/COLOR]
4 [installed,automatic]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-5.13.0-40-generic/focal-updates,focal-security,now 5.13.0-40.45~20.04.1 amd6[/COLOR]
4 [installed,automatic]
[COLOR=#FF5454]**linux-image**[/COLOR][COLOR=#000000]-generic-hwe-20.04/focal-updates,focal-security,now 5.13.0.40.45~20.04.25 amd[/COLOR]
64 [installed,automatic]

[/FONT]
```

[FONT=monospace]are my installed kernels

When trying to remove one of them I get the following message

[/FONT]```
[FONT=monospace][COLOR=#000000]sudo apt remove linux-headers-5.13.0-30-generic  [/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-5.13.0-30-generic
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 24,5 MB disk space will be freed.
Do you want to continue? [Y/n] y
[COLOR=#000000]**dpkg**[/COLOR][COLOR=#000000]: [/COLOR][COLOR=#FF5454]**unrecoverable fatal error, aborting:**[/COLOR]
 files list file for package 'libanalitza8:amd64' is missing final newline
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]

[/FONT]
```

Trying the reinstall or remove libanalitza8 all give same error

```
[FONT=monospace][COLOR=#000000]sudo apt-get reinstall libanalitza8    [/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
Need to get 0 B/255 kB of archives.
After this operation, 0 B of additional disk space will be used.
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'libanalitza8:amd64' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)
[/FONT]
```

I guess it has to do with my boot sector which is full

```
[FONT=monospace][COLOR=#000000]df -h | grep boot                            [/COLOR]
/dev/sda2                   705M  633M   22M  97% /[COLOR=#FF5454]**boot**[/COLOR]
/dev/sda1                   511M  5,3M  506M   2% /[COLOR=#FF5454]**boot**[/COLOR][COLOR=#000000]/efi[/COLOR]
[/FONT]
```

What ever I try I am not able to remove / update etc 

Does anyone know a solution to this problem.

Thanks for your help.
[FONT=monospace]
[/FONT]

---

### Post by SeijiSensei on 2022-04-24
I just remove the stale images from /boot directly.

```

cd /boot
sudo rm *5.11*
sudo rm *5.13-30*
sudo rm *5.13-37*

```

Usually a "sudo apt dist-upgrade" will sort out any issues.

It does seem like the distribution permits the proliferation of kernel images again. It used to do a good job of keeping only the current and (t-1) images. Now I see stale images on my machines again.

I use KDE Neon which is derived from 20.04, but I don't think this problem is limited to Neon.

---

### Post by El Bartolomew on 2022-04-26
Thanks a lot for your help. When trying to upgrade or in this case for example do a dist-upgrade I keep getting the same errors

```
[FONT=monospace][COLOR=#000000]sudo apt dist-upgrade[/COLOR]
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  openjdk-11-jre openjdk-11-jre-headless
2 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
2 standard security updates
Need to get 37,5 MB of archives.
After this operation, 130 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
Get:1 http://be.archive.ubuntu.com/ubuntu focal-updates/main amd64 openjdk-11-jre amd64 
11.0.15+10-0ubuntu0.20.04.1 [175 kB]
Get:2 http://be.archive.ubuntu.com/ubuntu focal-updates/main amd64 openjdk-11-jre-headle
ss amd64 11.0.15+10-0ubuntu0.20.04.1 [37,3 MB]
Fetched 37,5 MB in 5s (7.824 kB/s)
[COLOR=#000000]**dpkg**[/COLOR][COLOR=#000000]: [/COLOR][COLOR=#FF5454]**unrecoverable fatal error, aborting:**[/COLOR]
 files list file for package 'libanalitza8:amd64' is missing final newline
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR]
[/FONT]
```

---

### Post by SeijiSensei on 2022-05-05
```
files list file for package 'libanalitza8:amd64' is missing final newline
```
I'd try removing that package manually, running the update, then reinstalling the package.

---

### Post by El Bartolomew on 2022-05-06
I tried everything

[FONT=monospace][COLOR=#000000]sudo apt remove libanalitza8[/COLOR]
[/FONT][FONT=monospace][COLOR=#000000]sudo apt purge libanalitza8
[/COLOR]
It always ends with the same thing

[/FONT]```
[FONT=monospace][COLOR=#000000]Reading package lists... Done[/COLOR]
Building dependency tree        
Reading state information... Done
The following packages will be REMOVED:
  kalgebra* kalgebra-common* kde-full* kdeedu* libanalitza8* libanalitzagui8*
  libanalitzaplot8* libanalitzawidgets8* qml-module-org-kde-analitza*
0 upgraded, 0 newly installed, 9 to remove and 27 not upgraded.
After this operation, 4.422 kB disk space will be freed.
Do you want to continue? [Y/n] y
[COLOR=#000000]**dpkg**[/COLOR][COLOR=#000000]: [/COLOR][COLOR=#FF5454]**unrecoverable fatal error, aborting:**[/COLOR]
 files list file for package 'libanalitza8:amd64' is missing final newline
[COLOR=#FF5454]**E: **[/COLOR][COLOR=#000000]Sub-process /usr/bin/dpkg returned an error code (2)[/COLOR][/FONT]
```

[FONT=monospace]I am going to reinstall, put my files on a separate partition so I can dump ubuntu any time for a reinstall without worries.

I spend hours searching and trying.

Anyway, thanks for all the help.


[/FONT]

---

