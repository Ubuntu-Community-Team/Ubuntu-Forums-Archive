---
title: "error while installing"
date: 2024-01-17
forum: Installation &amp; Upgrades
---

### Post by krmnmaria on 2024-01-17
Hi to all, 
when I try to install any packages, I obtain this error:

Extracting templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 61996 files and directories currently installed.)
Preparing to unpack .../libc6_2.35-0ubuntu3.6_amd64.deb ...
dpkg (subprocess): unable to execute new libc6:amd64 package pre-installation script (/var/lib/dpkg/tmp.ci/preinst): Permission denied
dpkg: error processing archive /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb (--unpack):
 new libc6:amd64 package pre-installation script subprocess returned error exit status 2
dpkg (subprocess): unable to execute new libc6:amd64 package post-removal script (/var/lib/dpkg/tmp.ci/postrm): Permission denied
dpkg: error while cleaning up:
 new libc6:amd64 package post-removal script subprocess returned error exit status 2
Errors were encountered while processing:
 /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@Syslog-VMWare-SysServ:~# ^C
root@Syslog-VMWare-SysServ:~# sudo dpkg -i --configure -a
dpkg: error: conflicting actions  (--configure) and -i (--install)


Any help would be very appreciated, I've been searching information about this issue for hours.
Thnx
Carmen

---

### Post by MAFoElffen on 2024-01-17
I think your interim try for that mixed commands together as one... It told you that in the error

You tried 
```

root@Syslog-VMWare-SysServ:~# sudo dpkg -i --configure -a
dpkg: error: conflicting actions (--configure) and -i (--install)

```
That would be either of these
```

sudo dpkg -i /var/cache/apt/archives/libc6_2.35-0ubuntu3.6_amd64.deb
## But more correctly, since it was interupted
sudo dpkg --configure -a

```
What do either of those return? And please use CODE Tags to post commands or output.

---

### Post by krmnmaria on 2024-01-17
Yes, that was another error, I am trying to delete those 3 last lines but I am not able to. 
The real error is in the upper lines, please review

Thanks

---

