---
title: "libwraster6 denying upgrades to my system"
date: 2017-06-04
forum: Installation &amp; Upgrades
---

### Post by killnine2 on 2017-06-04
```
The following additional packages will be installed:
  libwraster6
The following NEW packages will be installed:
  libwraster6
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
38 not fully installed or removed.
Need to get 0 B/76.1 kB of archives.
After this operation, 141 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 439533 files and directories currently installed.)
Preparing to unpack .../libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb ...
Unpacking libwraster6:amd64 (0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb (--unpac
k):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwraster.so.6.0.0', which is also in package libwraster5:amd64 0.95.7+201703102031-0pp
a201703102109~ubuntu16.04.1
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```



even using:

sudo apt-get -f install 

does not work:

```
Jupiter% sudo apt-get -f install
Reading package lists... Done
Building dependency tree        
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libwraster5 linux-headers-4.4.0-62 linux-headers-4.4.0-62-generic linux-image-4.4.0-62-generic linux-image-extra-4.4.0-62-generic
  linux-tools-4.4.0-62 linux-tools-4.4.0-62-generic
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libwraster6
The following NEW packages will be installed:
  libwraster6
0 upgraded, 1 newly installed, 0 to remove and 25 not upgraded.
38 not fully installed or removed.
Need to get 0 B/76.1 kB of archives.
After this operation, 141 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
(Reading database ... 439533 files and directories currently installed.)
Preparing to unpack .../libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb ...
Unpacking libwraster6:amd64 (0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1) ...
dpkg: error processing archive /var/cache/apt/archives/libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb (--unpac
k):
 trying to overwrite '/usr/lib/x86_64-linux-gnu/libwraster.so.6.0.0', which is also in package libwraster5:amd64 0.95.7+201703102031-0pp
a201703102109~ubuntu16.04.1
Processing triggers for libc-bin (2.23-0ubuntu7) ...
Errors were encountered while processing:
 /var/cache/apt/archives/libwraster6_0.95.8+201703220926-0ppa201703170258~ubuntu16.04.1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Impavidus on 2017-06-04
You have 38 packages not fully installed or removed. That's bad, try to keep that number at zero, but it may be fixed automatically when we fix your problem. You have 25 upgrades available, which is OK, but don't wait too long before you install them.

Your problem is that you cannot install libwraster**6** because it has a file in common with libwraster**5**, which is installed too. The file in casu is libwraster.so.**6**.0.0, which shouldn't be in libwraster**5**. It seems you have installed a faulty version of libwraster5, coming from some PPA. I suggest you try reverting your libwraster5 to the version supplied from the official Ubuntu repositories. Have you got synaptic installed on your system? That would make it not too difficult.

And do you really need both libwraster5 and libwraster6 installed?

Actually, I wouldn't use a PPA that puts a file belonging to libwraster6 in the package for libwraster5.

---

### Post by killnine2 on 2017-06-04
It wont let me upgrade any of the other packages until libwraster whatever is fixed. I dont have synaptic. how do I revert?

---

