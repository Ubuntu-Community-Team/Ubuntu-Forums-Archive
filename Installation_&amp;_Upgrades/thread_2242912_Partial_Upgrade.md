---
title: "Partial Upgrade"
date: 2014-09-04
forum: Installation &amp; Upgrades
---

### Post by sameermw on 2014-09-04
Today I got a partial upgrade message while updating Ubuntu 14.04 After that i upgraded and Installed every possible applications using terminal

```

sudo apt-get update
sudo apt-get upgrade

```

Then I checked for updates again and I got partial upgrade message again. because of that i clicked partial upgrade button and it says 

> Error authenticating some packages


It was not possible to authenticate some packages. This may be a transient network problem. You may want to try again later. See below for a list of unauthenticated packages.

```
libgcrypt20
ubuntu-desktop

```


when i tried to update from terminal 

```

Fetched 409 kB in 3min 32s (1,923 B/s)
Reading package lists... Done
W: GPG error: http://deb.playonlinux.com trusty InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY E0F72778C4676186
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: GPG error: http://dl.google.com stable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A040830F7FAC5991
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://archive.getdeb.net trusty-getdeb InRelease: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY A8A515F046D7E7CF


W: GPG error: http://extras.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 16126D3A3E5C1192
W: GPG error: http://archive.canonical.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://security.ubuntu.com trusty-security Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://lk.archive.ubuntu.com trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: GPG error: http://archive.canonical.com quantal Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32
W: An error occurred during the signature verification. The repository is not updated and the previous index files will be used. GPG error: http://lk.archive.ubuntu.com trusty-updates Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 40976EAF437D05B5 NO_PUBKEY 3B4FE6ACC0B21F32


W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY FC14671BA89CA06C
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 1DB8ADC1CFCA9579
W: GPG error: http://ppa.launchpad.net trusty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY AD41BB2746C478B9
W: Failed to fetch http://archive.getdeb.net/ubuntu/dists/trusty-getdeb/InRelease  


W: Failed to fetch http://lk.archive.ubuntu.com/ubuntu/dists/trusty-updates/Release  


W: Some index files failed to download. They have been ignored, or old ones used instead.



```

When i tried to upgrade from Terminal i got this,

```
sam@sam-Inspiron-N4050:~$ sudo apt-get upgrade
[sudo] password for sam: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  ffmpeg libvlc5 libvncserver0 vlc vlc-data vlc-nox vlc-plugin-notify
  vlc-plugin-pulse
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

```

After that i run these commands

```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get -f install
```

No any luck, how do i solve this problem.

---

### Post by Bashing-om on 2014-09-04
sameermw; Hi !

Partial upgrades are not generally something one should accept, as it can lead to these types of situations:
Let's see what we can do about the GPG key ( authorizations) issue, then address the 'held packages"
what returns from terminal command:
```

ls -al ~/.gnupg/

```
Because there are so many missing keys, does this directory, with files, even exist ?

[INDENT][INDENT]gotta start somewhere
[INDENT][INDENT][INDENT]here looks good to me
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by sameermw on 2014-09-04
> **Bashing-om said:**
> sameermw; Hi !

Partial upgrades are not generally something one should accept, as it can lead to these types of situations:
Let's see what we can do about the GPG key ( authorizations) issue, then address the 'held packages"
what returns from terminal command:
```

ls -al ~/.gnupg/

```
Because there are so many missing keys, does this directory, with files, even exist ?
[INDENT][INDENT]gotta start somewhere[INDENT][INDENT][INDENT]here looks good to me
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]



```
total 40
drwx------  2 sam sam 4096 Aug 24 17:31 .
drwxr-xr-x 98 sam sam 4096 Sep  5 08:49 ..
-rw-------  1 sam sam 7680 Apr 21 09:08 gpg.conf
-rw-------  1 sam sam 1221 Aug 23 10:39 pubring.gpg
-rw-------  1 sam sam 1221 Aug 23 10:39 pubring.gpg~
-rw-------  1 sam sam  600 Aug 23 12:05 random_seed
-rw-rw-r--  1 sam sam 1743 Aug 24 17:26 Sameera_Wijayasiri.gpg
-rw-------  1 sam sam 2599 Aug 23 10:39 secring.gpg
-rw-------  1 sam sam 1440 Aug 23 10:39 trustdb.gpg



```

---

### Post by grahammechanical on 2014-09-04
The partial upgrade offer gives 4 reasons for its appearance.

1) A previous upgrade which did not complete
2) Problems with some installed software
3) Unofficial software packages not provided by Ubuntu
4) Normal changes of a pre-release version of Ubuntu

On my system I see that partial upgrade offer every day because I am running a pre-release version of Ubuntu. Which of the other three reasons for a partial upgrade offer applies to your system? I would bring it down to either item 2 or 3. What do you say?

Regards.

---

### Post by Bashing-om on 2014-09-05
sameermw; Humm ..
See grahammechanical's last, has bearing on how we proceed.
The "/.gnupg/" appears intact to me

I am presently at a loss why this circumstance has arisen.
We see:
> 
NO_PUBKEY E0F72778C4676186
NO_PUBKEY A040830F7FAC5991
NO_PUBKEY A8A515F046D7E7CF
NO_PUBKEY 40976EAF437D05B5
NO_PUBKEY 16126D3A3E5C1192
NO_PUBKEY 3B4FE6ACC0B21F32
NO_PUBKEY FC14671BA89CA06C
NO_PUBKEY 1DB8ADC1CFCA9579
NO_PUBKEY AD41BB2746C478B9

Graham. recon we should innerate through " /var/lib/apt/lists/*Release " for " gpgv --keyring /etc/apt/trusted.gpg " .. see if there are any others ?
Should we investigate what is contained in the file " ~/.gnupg/gpg.conf " ? Where else might all these keys be maintained, that could cause this wholesale loss of the keys ?

Presently I do not know IF individually we will have to fix the missing keys.

Home work time.
[INDENT][INDENT][INDENT]see what I can learn
[/INDENT][/INDENT][/INDENT]

---

### Post by sameermw on 2014-09-08
No any luck about partial upgrade, somehow i solved GPG error Problem, but Partial upgrade problem still annoying. I removed all previously installed files and apps.
Then i ran, 

```
sudo apt-get clean
sudo apt-get update 
```

But no luck. How do i solve this.

---

### Post by Bashing-om on 2014-09-08
sameermw; Hey !

Making progress .

OK, let's get the exact errors and in context; updated:
Post back the outputs of terminal commands:
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install
sudo dpkg -C

```

and we see where we go from there.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by sameermw on 2014-09-08
I did that but no any luck gain, The i run```
 sudo apt-get autoremove
``` and cleaned up my system using **Ubuntu Tweak Tool** and [B]bleachbit,
[/B]Then i used ```
sudo apt-get update
``` and now i can upgrade files ad applications well.

i don't know how and thank you every one for staying with me.

---

### Post by Bashing-om on 2014-09-08
sameermw; Great !

As things have now worked out, and you have updated the system;
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT][INDENT]happy trails to you
[/INDENT][/INDENT]

---

### Post by sameermw on 2014-09-09
ok. It's done, I marked it as SOLVED. thank you 

> **Bashing-om said:**
> sameermw; Great !

As things have now worked out, and you have updated the system;
Please mark this thread solved; 
aides others seeking the solution, 
helps keep the forum clean and 
precludes others miss-directing efforts to aid.
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)
[INDENT][INDENT]happy trails to you
[/INDENT]
[/INDENT]


---

