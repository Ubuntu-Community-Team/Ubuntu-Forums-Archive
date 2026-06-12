---
title: "apt-get troubles..."
date: 2008-08-08
forum: Installation &amp; Upgrades
---

### Post by jesar_gacula on 2008-08-08
I always encounter these error messages whenever I use apt-get update/upgrade/distro-upgrade, even on setting up RiceyTweak on my EeePC.

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Failed to fetch http://ph.archive.ubuntu.com/ubuntu/dists/hardy-updates/universe/source/Sources.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

Oh please help me with this..I don't want to reinstall my OS again.. =(

---

### Post by GreenN00b on 2008-08-08
Try run ```
sudo apt-get update
``` in a terminal.

---

### Post by iaculallad on 2008-08-08
Try changing your download source, use the "Main Server".

---

### Post by jesar_gacula on 2008-08-08
> **GreenN00b said:**
> Try run ```
sudo apt-get update
``` in a terminal.

I tried it alreay, but same error message appeared

---

### Post by jesar_gacula on 2008-08-08
> **iaculallad said:**
> Try changing your download source, use the "Main Server".

I just tried it a while ago but this error message appeared...

```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://archive.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Some index files failed to download, they have been ignored, or old ones used instead.
```

---

### Post by iaculallad on 2008-08-08
Open your terminal and do the code below:

Do a backup first:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

Now, open sources.list for editing:

```
gksudo gedit /etc/apt/sources.list
```

Delete all contents of the original file and copy and paste contents of the quoted line of texts rows below:

> ## a “general” sources.list for Hardy Heron; all sources are uncommented.

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the ‘backports’
## repository.

## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical’s
## ‘partner’ repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted

Save and exit.

Then on the terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

```

---

### Post by jesar_gacula on 2008-08-08
> **iaculallad said:**
> Open your terminal and do the code below:

Do a backup first:

sudo cp /etc/apt/sources.list /etc/apt/sources.list.bak

Now, open sources.list for editing:

```
gksudo gedit /etc/apt/sources.list
```

Delete all contents of the original file and copy and paste contents of the quoted line of texts rows below:



Save and exit.

Then on the terminal:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo apt-get clean all
sudo apt-get autoremove

```

Another set of error messages appeared after I entered 'apt-get update'.
```
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: http://security.ubuntu.com hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch http://security.ubuntu.com/ubuntu/dists/hardy-security/Release  

W: Failed to fetch http://archive.canonical.com/ubuntu/dists/hardy/partner/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-updates/restricted/source/Sources.bz2  Hash Sum mismatch

W: Failed to fetch http://archive.ubuntu.com/ubuntu/dists/hardy-backports/multiverse/source/Sources.bz2  Hash Sum mismatch

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems

```

---

### Post by iaculallad on 2008-08-08
Try to unset your proxy on your terminal:

```
unset http_proxy
sudo apt-get update
```

---

### Post by jesar_gacula on 2008-08-08
> **iaculallad said:**
> Try to unset your proxy on your terminal:

```
unset http_proxy
sudo apt-get update
```

Same error message appeared..

---

### Post by Vorian Grey on 2008-08-08
Is this an apt problem or an internet problem? it seems to me that apt isn't able to access the internet. Does all your other internet stuff work.

---

### Post by jesar_gacula on 2008-08-09
i dunno..all i know now is that i've just finished reinstalling ubuntu in my eeepc. i umm..but i think it's the apt-get. because i've tried **iaculallad**'s list of sources yet i still receive the same errors..so i decided to reinstall ubuntu.

thanks to y'all who tried to help me out with this problem!

---

### Post by shrinathk87 on 2008-08-09
Hey.. i am kind of new to linux and i am tryin to learn, so i may be wrong..just sharing what i know..

i heard aptitude was better that apt-get .... because, aptitude keeps track of the installations and thus uninstallation of softwares installed with aptitude are easy..

so just giv it a try with aptitude.

like 

sudo aptitude file/application-to-download

Thanks.

Would be thankful if someone gives the difference between apt-get and aptitude. similarly the differnce between sudo and gksudo.

---

### Post by paletti on 2008-09-08
> **iaculallad said:**
> Try changing your download source, use the "Main Server".

This worked for me, thanks 
:)

---

### Post by linuxbastard on 2008-12-26
> **paletti said:**
> This worked for me, thanks 
:)
yep, it seems that most issues come from using the region specific server.

To change to the main server, just open system >> administration >> software sources and on the "Ubuntu Software" tab, go down to the "download from" area and select "Main Server".

Also, if you are using a terminal to update, you might want to try this:

```
sudo apt-get update -o Acquire::http::No-Cache=True
```

One of the above will likely work for you.

---

