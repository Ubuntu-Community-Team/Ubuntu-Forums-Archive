---
title: "Update error: Cannot verify issuers authority: Certificate"
date: 2021-10-13
forum: Installation &amp; Upgrades
---

### Post by jacqpret on 2021-10-13
Good Morning

Please assist, cant find a solution in Google.


1 package can be upgraded. Run 'apt list --upgradable' to see it.
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  android-studio-2020.3.1
1 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/5,612 B of archives.
After this operation, 0 B of additional disk space will be used.
(Reading database ... 584516 files and directories currently installed.)
Preparing to unpack .../android-studio-2020.3.1_2020.3.1.25~hirsute+2_amd64.deb 
...
--2021-10-13 09:42:52--  [https://redirector.gvt1.com/edgedl/android/studio/ide-z](https://redirector.gvt1.com/edgedl/android/studio/ide-z)
ips/2020.3.1.25/android-studio-2020.3.1.25-linux.tar.gz
Resolving redirector.gvt1.com (redirector.gvt1.com)... 172.217.170.78, 2c0f:fb50
:4002:806::200e
Connecting to redirector.gvt1.com (redirector.gvt1.com)|172.217.170.78|:443... c
onnected.
ERROR: cannot verify redirector.gvt1.com's certificate, issued by ‘CN=GTS CA 1C3
,O=Google Trust Services LLC,C=US’:
  Unable to locally verify the issuer's authority.
To connect to redirector.gvt1.com insecurely, use `--no-check-certificate'.
SHA-256 Checksum mismatch, aborting installation
dpkg: error processing archive /var/cache/apt/archives/android-studio-2020.3.1_2
020.3.1.25~hirsute+2_amd64.deb (--unpack):
 new android-studio-2020.3.1 package pre-installation script subprocess returned
 error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/android-studio-2020.3.1_2020.3.1.25~hirsute+2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


Thank You

---

### Post by ActionParsnip on 2021-10-13
Looks like the site was missing one of it's intermediate certificates. I've been on  [https://redirector.gvt1.com](https://redirector.gvt1.com) and it shows a valid certificate. Is it working now?
What is the output of
```

lsb_release -a; uname -a

```
Thanks

---

### Post by ActionParsnip on 2021-10-13
To work around, you can add the 
```

--no-check-certificate

```
option as stated in your output

---

