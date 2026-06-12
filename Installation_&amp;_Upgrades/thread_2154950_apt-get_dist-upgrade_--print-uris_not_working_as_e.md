---
title: "apt-get dist-upgrade --print-uris not working as expected"
date: 2013-06-16
forum: Installation &amp; Upgrades
---

### Post by spiralofhope on 2013-06-16
I can, for example, do this:  ```
\sudo \apt-get --print-uris --yes --reinstall install bash
``` ```
 Reading package lists... Done Building dependency tree        Reading state information... Done 0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 7 not upgraded. Need to get 643 kB of archives. After this operation, 0 B of additional disk space will be used. 'http://archive.ubuntu.com/ubuntu/pool/main/b/bash/bash_4.2-5ubuntu3_amd64.deb' bash_4.2-5ubuntu3_amd64.deb 642968 MD5Sum:55770c1cfb19e0853ddc2f30d7eb114e 
```  I want to do the same thing with dist-upgrade.  The other day I did this and could get _some_ URLs, but for some reason some  packages were not included.  Now those same packages refuse to print.  ```
sudo apt-get dist-upgrade --print-uris --yes
```  ```
 Reading package lists... Done Building dependency tree        Reading state information... Done Calculating upgrade... Done The following packages will be upgraded:   dbus dbus-x11 libdbus-1-3 libdbus-1-3:i386 libfm-data libfm-gtk-data linux-libc-dev 7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded. Need to get 0 B/1,771 kB of archives. After this operation, 67.6 kB of additional disk space will be used.
```   Why would some packages not work the same as others?  Do I need to pursue some other command-line way to do the same thing?  I can get more information by comparing with Synaptic's "Generate package download script".  ```
 wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.6.8-1ubuntu6.1_i386.deb wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/libdbus-1-3_1.6.8-1ubuntu6.1_amd64.deb wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus_1.6.8-1ubuntu6.1_amd64.deb wget -c http://archive.ubuntu.com/ubuntu/pool/main/d/dbus/dbus-x11_1.6.8-1ubuntu6.1_amd64.deb wget -c http://ppa.launchpad.net/mati75/lubuntu/ubuntu/pool/main/libf/libfm/libfm-data_1.1.0+git20130614-0ubuntu1_all.deb wget -c http://ppa.launchpad.net/mati75/lubuntu/ubuntu/pool/main/libf/libfm/libfm-gtk-data_1.1.0+git20130614-0ubuntu1_amd64.deb wget -c http://archive.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.8.0-25.37_amd64.deb 
```  (No I do not want to use Synaptic for this process, it must be command-line)  This reveals that these are valid packages to download, with dependencies which have been met.  Could the two PPA packages be interfering with apt-get --print-uri ?

---

### Post by gordintoronto on 2013-06-17
I don't understand where you specify uri or url.

---

### Post by spiralofhope on 2013-06-17
> **gordintoronto said:**
> I don't understand where you specify uri or url.  I don't.  I'm not trying to.

---

### Post by varunendra on 2013-06-17
Unless I'm missing something -

The first command -
```
\sudo \apt-get --print-uris --yes --reinstall install bash
```
..is forcing the reinstallation of the package "bash". Since it is not already in the apt cache (obviously), it needs to be downloaded, hence the URI is returned.

The second command -
```
sudo apt-get dist-upgrade --print-uris --yes
```
..only downloads those packages that are actually upgraded and are not already in the apt cache. So you will get relatively fewer URIs (or none if all the packages to be upgraded have already been downloaded and are present in apt cache.)

In your example post, the output of the second command suggests to me that the packages needed to be upgraded are already in the apt cache, hence no URIs were returned -
```
The following packages will be upgraded:
  dbus dbus-x11 libdbus-1-3 libdbus-1-3:i386 libfm-data libfm-gtk-data linux-libc-dev
7 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get **[COLOR="#FF0000"]0 B[/COLOR]/1,771** kB of archives.
```

---

### Post by spiralofhope on 2013-06-17
> **varunendra said:**
> In your example post, the output of the second command suggests to me that the packages needed to be upgraded are already in the apt cache, hence no URIs were returned

Aha.

I deleted /var/cache/apt and now the command returns a list of URLs as I expected.  I thought I had cleared the local cache already.. I'll have to check my scripting.

Thanks for your help.

---

### Post by varunendra on 2013-06-17
> **spiralofhope said:**
> I thought I had cleared the local cache already.. I'll have to check my scripting.

Thanks for your help.

Glad I could :)
Surprises of automation scripts ! :lol:

---

