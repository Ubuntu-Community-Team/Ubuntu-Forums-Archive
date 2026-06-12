---
title: "How to remove warnings after apt-get update?"
date: 2011-01-07
forum: Installation &amp; Upgrades
---

### Post by vigs on 2011-01-07
After running apt-get update, I get the following warnings. How do I get rid of them?

Fetched 374kB in 1min 14s (4,996B/s)
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6E871C4A881574DE Launchpad PPA for Bisigi
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Unknown error executing gpgv
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Unknown error executing gpgv
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6D975C4791E7EE5E Launchpad PPA for XBMC for Linux

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX

W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: Unknown error executing gpgv
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-backports Release: Unknown error executing gpgv
W: Failed to fetch [http://ubuntutym.u-toyama.ac.jp/ubuntu/dists/maverick-backports/Release.gpg](http://ubuntutym.u-toyama.ac.jp/ubuntu/dists/maverick-backports/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ubuntutym.u-toyama.ac.jp_ubuntu_dists_maverick-backports_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/conkyhardcore/ppa/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_conkyhardcore_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/flozz/flozz/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/flozz/flozz/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_flozz_flozz_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_doctormo_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg](http://ppa.launchpad.net/tualatrix/ppa/ubuntu/dists/maverick/Release.gpg)  rename failed, No such file or directory ( -> /var/lib/apt/lists/partial/ppa.launchpad.net_tualatrix_ppa_ubuntu_dists_maverick_Release.gpg).

W: Failed to fetch [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/maverick/Release](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/maverick/Release](http://ppa.launchpad.net/norsetto/ppa/ubuntu/dists/maverick/Release)  

W: Failed to fetch [http://ubuntutym.u-toyama.ac.jp/ubuntu/dists/maverick-security/Release](http://ubuntutym.u-toyama.ac.jp/ubuntu/dists/maverick-security/Release)  

W: Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/doctormo/ppa/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)

---

### Post by wojox on 2011-01-07
Use these commands:

```
sudo apt-get clean
cd /var/lib/apt
sudo mv lists lists.old
sudo mkdir -p lists/partial
sudo apt-get clean
sudo apt-get update
```

---

### Post by vigs on 2011-01-07
OK, this has definitely changed the warnings to some extent - now I get this:

etched 14.9MB in 5min 14s (47.2kB/s)                                                                                                                       
Reading package lists... Done
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6E871C4A881574DE Launchpad PPA for Bisigi
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG D6B6DB186A68F637 Launchpad JDownloader PPA
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 531EE72F4C9D234C
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG C41B720D95628707 Launchpad PPA for Cesare Tirabassi
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG F58DBE6EA8DF5CE3 Launchpad pdfmod
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6D975C4791E7EE5E Launchpad PPA for XBMC for Linux
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: BADSIG 6AF0E1940624A220 Launchpad PPA for TualatriX
W: GPG error: [http://ppa.launchpad.net](http://ppa.launchpad.net) maverick Release: The following signatures were invalid: NODATA 1 NODATA 2
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-proposed Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://ubuntutym.u-toyama.ac.jp](http://ubuntutym.u-toyama.ac.jp) maverick-backports Release: The following signatures were invalid: NODATA 1 NODATA 2
W: Duplicate sources.list entry [http://archive.canonical.com/ubuntu/](http://archive.canonical.com/ubuntu/) maverick/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_ubuntu_dists_maverick_partner_binary-i386_Packages)

---

### Post by sikander3786 on 2011-01-07
For the missing GPG keys, add them by,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE D6B6DB186A68F637 531EE72F4C9D234C C41B720D95628707 F58DBE6EA8DF5CE3 6D975C4791E7EE5E 6AF0E1940624A220 40976EAF437D05B5
```

There are still 2 more errors that need to be addressed. For the NODATA and Duplicate sources.list error, post the output of these commands.

```
cat /etc/apt/sources.list
```

```
ls -l /etc/apt/sources.list.d
```

---

### Post by vigs on 2011-01-07
> **sikander3786 said:**
> For the missing GPG keys, add them by,

```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 6E871C4A881574DE D6B6DB186A68F637 531EE72F4C9D234C C41B720D95628707 F58DBE6EA8DF5CE3 6D975C4791E7EE5E 6AF0E1940624A220 40976EAF437D05B5
```There are still 2 more errors that need to be addressed. For the NODATA and Duplicate sources.list error, post the output of these commands.

```
cat /etc/apt/sources.list
``````
ls -l /etc/apt/sources.list.d
```

When I run the 1st command (the apt-key one) it gives an error:
[FONT=Courier New]?: keyserver.ubuntu.com: Connection refused
gpgkeys: HTTP fetch error 7: couldn't connect: Connection refused[/FONT]
[FONT=Verdana](repeated 7 times) Maybe it's because I'm behind a proxy server of my institute. Any fix for this?

Output of [/FONT]```
cat /etc/apt/sources.list
``` is 
[FONT=Courier New]# added by the release upgrader
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) maverick main restricted #Added by software-properties
# deb cdrom:[Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)]/ karmic main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick universe
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick multiverse
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
## deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse
## deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) karmic-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner

deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security main restricted
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security restricted main multiverse universe #Added by software-properties
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security universe
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-security multiverse
# deb [http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu](http://ftp.osuosl.org/pub/pculture.org/miro/linux/repositories/ubuntu) karmic/ # disabled on upgrade to lucid
# deb [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) maverick main # disabled on upgrade to maverick
# deb-src [http://ppa.launchpad.net/jeffreyratcliffe/ubuntu](http://ppa.launchpad.net/jeffreyratcliffe/ubuntu) maverick main # disabled on upgrade to maverick
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-proposed restricted main multiverse universe
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-proposed restricted main multiverse universe #Added by software-properties
deb [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-backports restricted main multiverse universe
deb-src [http://ubuntutym.u-toyama.ac.jp/ubuntu/](http://ubuntutym.u-toyama.ac.jp/ubuntu/) maverick-backports restricted main multiverse universe #Added by software-properties[/FONT]

and output of ```
ls -l /etc/apt/sources.list.d
``` is 
[FONT=Courier New]total 160
-rw-r--r-- 1 root root  95 2011-01-07 17:38 bisigi-ppa-lucid.list
-rw-r--r-- 1 root root  58 2010-10-11 02:27 bisigi-ppa-lucid.list.distUpgrade
-rw-r--r-- 1 root root  95 2011-01-07 17:38 bisigi-ppa-lucid.list.save
-rw-r--r-- 1 root root 186 2011-01-07 17:38 clicompanion-devs-clicompanion-nightlies-maverick.list
-rw-r--r-- 1 root root 186 2011-01-07 17:38 clicompanion-devs-clicompanion-nightlies-maverick.list.save
-rw-r--r-- 1 root root 364 2011-01-07 17:38 conkyhardcore-maverick.list
-rw-r--r-- 1 root root 364 2011-01-07 17:38 conkyhardcore-maverick.list.save
-rw-r--r-- 1 root root  75 2011-01-07 17:38 cover-thumbnailer.list
-rw-r--r-- 1 root root  72 2010-10-11 02:27 cover-thumbnailer.list.distUpgrade
-rw-r--r-- 1 root root  75 2011-01-07 17:38 cover-thumbnailer.list.save
-rw-r--r-- 1 root root 130 2011-01-07 17:38 doctormo-ppa-maverick.list
-rw-r--r-- 1 root root 130 2011-01-07 17:38 doctormo-ppa-maverick.list.save
-rw-r--r-- 1 root root  84 2011-01-07 17:38 dropbox.list
-rw-r--r-- 1 root root  47 2010-10-11 02:27 dropbox.list.distUpgrade
-rw-r--r-- 1 root root  84 2011-01-07 17:38 dropbox.list.save
-rw-r--r-- 1 root root 176 2011-01-07 17:38 google-chrome.list
-rw-r--r-- 1 root root  48 2010-05-17 03:14 google-chrome.list.distUpgrade
-rw-r--r-- 1 root root 176 2011-01-07 17:38 google-chrome.list.save
-rw-r--r-- 1 root root 180 2011-01-07 17:38 google-talkplugin.list
-rw-r--r-- 1 root root 180 2010-10-11 02:27 google-talkplugin.list.distUpgrade
-rw-r--r-- 1 root root 180 2011-01-07 17:38 google-talkplugin.list.save
-rw-r--r-- 1 root root 140 2011-01-07 17:38 gwibber-daily-ppa-maverick.list
-rw-r--r-- 1 root root 148 2011-01-07 17:38 jd-team-jdownloader-maverick.list
-rw-r--r-- 1 root root 148 2011-01-07 17:38 jd-team-jdownloader-maverick.list.save
-rw-r--r-- 1 root root 175 2011-01-07 17:38 lucid-partner.list
-rw-r--r-- 1 root root 172 2010-10-11 02:27 lucid-partner.list.distUpgrade
-rw-r--r-- 1 root root 175 2011-01-07 17:38 lucid-partner.list.save
-rw-r--r-- 1 root root 146 2011-01-07 17:38 nilarimogard-webupd8-maverick.list
-rw-r--r-- 1 root root 146 2011-01-07 17:38 nilarimogard-webupd8-maverick.list.save
-rw-r--r-- 1 root root 130 2011-01-07 17:38 norsetto-ppa-maverick.list
-rw-r--r-- 1 root root 130 2011-01-07 17:38 norsetto-ppa-maverick.list.save
-rw-r--r-- 1 root root  78 2011-01-07 17:38 pdfmod-team-ppa.list
-rw-r--r-- 1 root root  75 2010-10-11 02:27 pdfmod-team-ppa.list.distUpgrade
-rw-r--r-- 1 root root  78 2011-01-07 17:38 pdfmod-team-ppa.list.save
-rw-r--r-- 1 root root  98 2011-01-07 17:38 team-xbmc-ppa-karmic.list
-rw-r--r-- 1 root root  61 2010-10-11 02:27 team-xbmc-ppa-karmic.list.distUpgrade
-rw-r--r-- 1 root root  98 2011-01-07 17:38 team-xbmc-ppa-karmic.list.save
-rw-r--r-- 1 root root  92 2011-01-07 17:38 ubuntu-tweak-stable.list
-rw-r--r-- 1 root root  89 2010-10-11 02:27 ubuntu-tweak-stable.list.distUpgrade
-rw-r--r-- 1 root root  92 2011-01-07 17:38 ubuntu-tweak-stable.list.save
[/FONT]

---

### Post by presence1960 on 2011-01-07
You can save yourself a lot of heartache by generating a new /etc/apt/sources.lst from [here]("http://repogen.simplylinux.ch/")

Make a backup of your original sources.list file. Then edit the original sources.list file by opening a terminal and running ```
gksu gedit /etc/apt/sources.list 
```

Remove existing text and copy/paste text from sources.list generator web page to the file. Click save on toolbar and close file.

Next run the commands from terminal that are under the sources.list text from the web page. This will download the keys necessary for specific repositories, Then run in terminal ```
sudo apt-get update
```

You can use this web page to generate a new sources.list file for any supported version of ubuntu

---

### Post by sikander3786 on 2011-01-07
Try this as you are behind a proxy.

```
gpg --keyserver keyserver.ubuntu.com --keyserver-options http_proxy=http://MY_PROXY:MY_PORT,honor-http-proxy,broken-http-proxy --recv 6E871C4A881574DE D6B6DB186A68F637 531EE72F4C9D234C C41B720D95628707 F58DBE6EA8DF5CE3 6D975C4791E7EE5E 6AF0E1940624A220 40976EAF437D05B5
```

Replace MY_PROXY:MY_PORT with your own proxy.

For the duplicate source.list entry,

```
sudo mv /etc/apt/sources.list.d/lucid-partner.list ~/lucid-partner.list
```

```
sudo mv /etc/apt/sources.list.d/lucid-partner.list.distUpgrade ~/lucid-partner.list.distUpgrade
```

```
sudo mv /etc/apt/sources.list.d/lucid-partner.list.save ~/lucid-partner.list.save
```

If you still get the errors, go to Software Center > Edit > Software Sources > Other Software Tab and disable any offensive PPAs. You won't be able to install from those PPAs then.

---

### Post by ojasmehta on 2011-10-15
Thanks a lot!

---

### Post by subehsharma on 2011-11-10
Best method to getaway from this problem is to install fix404. You can read about it more here:

Under Ubuntu, the APT package index is a database containing all packages of repositories (PPAs) defined in the /etc/apt/sources.list file. To update this database after adding some repositories, we need to use this command from the Terminal:

sudo apt-get update

Sometimes, when running the command given above, we get error messages (404 Not Found) that are the result of wrong PPAs, which may slow down the update process via the Terminal. In fact, this 404 Not Found error messages are not harmful at all, but you can use Fix404 to detect and remove these PPAs.

To install Fix404 on Ubuntu 11.04, launch the Terminal and run these commands:

sudo apt-add-repository ppa:lkjoel/fix404
sudo apt-get update
sudo apt-get install fix404

To install on Ubuntu 10.10/10.04, download this deb package here.

To start using Fix404, run this command (root privileges required):

sudo fix404

Then follow displayed instructions to disable PPAs causing the 404 Not Found Error.

[http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html](http://www.upubuntu.com/2011/07/remove-ubuntu-ppas-that-cause-404-not.html)

---

### Post by oaxacamatt1 on 2011-12-13
This saved me!!!

---

### Post by astrocrazy on 2013-01-15
Dear presence1960,

Yours is the best answer I found after searching so many sites...It solved my problem completely.. Thank you very much...

---

### Post by presence1960 on 2013-01-15
> **astrocrazy said:**
> Dear presence1960,

Yours is the best answer I found after searching so many sites...It solved my problem completely.. Thank you very much...

You are welcome. Enjoy Ubuntu!

---

