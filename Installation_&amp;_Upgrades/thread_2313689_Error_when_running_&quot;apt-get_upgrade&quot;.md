---
title: "Error when running &quot;apt-get upgrade&quot;"
date: 2016-02-15
forum: Installation &amp; Upgrades
---

### Post by Victor_Inyang on 2016-02-15
I ran the command: "apt-get upgrade" and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these.
The following packages have unmet dependencies:
 cpp-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.1 is installed
 gcc-4.8 : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.1 is installed
 libgcc-4.8-dev : Depends: gcc-4.8-base (= 4.8.4-2ubuntu1~14.04) but 4.8.4-2ubuntu1~14.04.1 is installed
 libnss3-1d : Depends: libnss3 (= 2:3.19.2.1-0ubuntu0.14.04.2) but 2:3.19.2.1-0ubuntu0.14.04.1 is installed
 libnss3-nssdb : Depends: libnss3 (= 2:3.19.2.1-0ubuntu0.14.04.2) but 2:3.19.2.1-0ubuntu0.14.04.1 is installed
 libsmbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.11) but 2:4.1.6+dfsg-1ubuntu2.14.04.9 is installed
 samba : Depends: samba-common (= 2:4.1.6+dfsg-1ubuntu2.14.04.9) but 2:4.1.6+dfsg-1ubuntu2.14.04.11 is installed
         Depends: samba-common-bin (= 2:4.1.6+dfsg-1ubuntu2.14.04.9) but 2:4.1.6+dfsg-1ubuntu2.14.04.11 is installed
 samba-common-bin : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.11) but 2:4.1.6+dfsg-1ubuntu2.14.04.9 is installed
 samba-dsdb-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.11) but 2:4.1.6+dfsg-1ubuntu2.14.04.9 is installed
 samba-vfs-modules : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.11) but 2:4.1.6+dfsg-1ubuntu2.14.04.9 is installed
 smbclient : Depends: samba-libs (= 2:4.1.6+dfsg-1ubuntu2.14.04.11) but 2:4.1.6+dfsg-1ubuntu2.14.04.9 is installed
E: Unmet dependencies. Try using -f.
```

I then ran: "apt-get upgrade -f" and got this:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
Calculating upgrade... Done
The following packages will be upgraded:
  adobe-flashplugin cpp-4.8 firefox firefox-locale-en gcc-4.8 gir1.2-ibus-1.0
  ibus-gtk:i386 ifupdown libgcc-4.8-dev libnss3 libnss3:i386 linux-libc-dev
  openssh-client opera python-samba samba samba-libs ssh-askpass-gnome
18 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
40 not fully installed or removed.
Need to get 0 B/87.8 MB of archives.
After this operation, 411 kB of additional disk space will be used.
Do you want to continue? [Y/n] y
E: Invalid archive signature
E: Internal error, could not locate member control.tar.{gzbz2xzlzma}
E: Prior errors apply to /var/cache/apt/archives/python-samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb
E: Invalid archive signature
E: Internal error, could not locate member control.tar.{gzbz2xzlzma}
E: Prior errors apply to /var/cache/apt/archives/samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb
E: Invalid archive signature
E: Internal error, could not locate member control.tar.{gzbz2xzlzma}
E: Prior errors apply to /var/cache/apt/archives/samba-libs_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/ifupdown_0.7.47.2ubuntu4.3_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/openssh-client_1%3a6.6p1-2ubuntu2.6_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/adobe-flashplugin_1%3a20160209.1-0ubuntu0.14.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/libgcc-4.8-dev_4.8.4-2ubuntu1~14.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/gcc-4.8_4.8.4-2ubuntu1~14.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/cpp-4.8_4.8.4-2ubuntu1~14.04.1_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/firefox_44.0.2+linuxmint1+rosa_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/firefox-locale-en_44.0.2+linuxmint1+rosa_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/gir1.2-ibus-1.0_1.5.5-1ubuntu3.2_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/ibus-gtk_1.5.5-1ubuntu3.2_i386.deb
E: Prior errors apply to /var/cache/apt/archives/linux-libc-dev_3.13.0-77.121_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/opera_12.16.1860-1linuxmint_amd64.deb
E: Prior errors apply to /var/cache/apt/archives/ssh-askpass-gnome_1%3a6.6p1-2ubuntu2.6_amd64.deb
debconf: apt-extracttemplates failed: No such file or directory
(Reading database ... 172847 files and directories currently installed.)
Preparing to unpack .../libnss3_3.19.2.1-0ubuntu0.14.04.2_amd64.deb ...
De-configuring libnss3:i386 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Unpacking libnss3:amd64 (2:3.19.2.1-0ubuntu0.14.04.2) over (2:3.19.2.1-0ubuntu0.14.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/libnss3_3.19.2.1-0ubuntu0.14.04.2_amd64.deb (--unpack):
 cannot copy extracted data for './usr/lib/x86_64-linux-gnu/nss/libnssdbm3.so' to '/usr/lib/x86_64-linux-gnu/nss/libnssdbm3.so.dpkg-new': unexpected end of file or stream
Preparing to unpack .../libnss3_3.19.2.1-0ubuntu0.14.04.2_i386.deb ...
De-configuring libnss3:amd64 (2:3.19.2.1-0ubuntu0.14.04.1) ...
Unpacking libnss3:i386 (2:3.19.2.1-0ubuntu0.14.04.2) over (2:3.19.2.1-0ubuntu0.14.04.1) ...
dpkg-deb (subprocess): decompressing archive member: lzma error: compressed data is corrupt
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing archive /var/cache/apt/archives/libnss3_3.19.2.1-0ubuntu0.14.04.2_i386.deb (--unpack):
 cannot copy extracted data for './usr/lib/i386-linux-gnu/nss/libfreebl3.so' to '/usr/lib/i386-linux-gnu/nss/libfreebl3.so.dpkg-new': unexpected end of file or stream
dpkg-deb: error: `/var/cache/apt/archives/python-samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb' is not a debian format archive
dpkg: error processing archive /var/cache/apt/archives/python-samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `/var/cache/apt/archives/samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb' is not a debian format archive
dpkg: error processing archive /var/cache/apt/archives/samba_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
dpkg-deb: error: `/var/cache/apt/archives/samba-libs_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb' is not a debian format archive
dpkg: error processing archive /var/cache/apt/archives/samba-libs_4.1.6+dfsg-1ubuntu2.14.04.11_amd64.deb (--unpack):
 subprocess dpkg-deb --control returned error exit status 2
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

What's the problem and how can I fix it?

---

### Post by ian-weisser on 2016-02-15
I see two problems:

1) Corrupt packages in your local cache.
2) Version conflict

Let's fix the the corrupt packages first by simply deleting them from your local cache.
```
sudo apt-get clean
```

Then try apt-get upgrade again. Some of the error messages should be different. Show us the new output.

---

