---
title: "Downloading Package Information Error (Synaptic)"
date: 2008-01-18
forum: Installation &amp; Upgrades
---

### Post by kennycason on 2008-01-18
Hello, i installed Ubuntu 7.10 on my friends laptop. the i opened the synaptic package manager -> selected repositories -> and then checked the repositories "available from the internet" and the updates. then of course clicked reload.

after downloading 7/21 files it stops. then i have to cancel and get this "Could not download all repository indexes" message.
i found many many many solutions on the web, but nothing worked. so i reinstalled ubuntu only to have the exact same problem 

here is my etc/apt/sources.list after trying the reload. 
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe restricted multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe main multiverse restricted #Added by software-properties
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main multiverse restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
```


Sorry if this is a redundant post. ive tried everything. (3days now)

---

### Post by PmDematagoda on 2008-01-18
Re-enable all the repositories again, but this time, change the location of the server. After that is done, reload the sources list again using:-
```
sudo apt-get update
```

---

### Post by kennycason on 2008-01-18
it freezes here:

```
go@go-laptop:~$ sudo apt-get update
[sudo] password for go:
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_US
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_US
26% [Connecting to us.archive.ubuntu.com (91.189.88.46)] [Connecting to security.ubuntu.com (91.189.88.37)]

```

---

### Post by PmDematagoda on 2008-01-18
Did you try changing the location of the server?

---

### Post by kennycason on 2008-01-18
yes.
I have tried the 3 different ones now, and i get the exact same message

btw, i have not done anything other than install linux, not setting changes etc, and i'm using a recebt iso that i downloaded 3 days ago.
Thanks for replying so fast!

---

### Post by PmDematagoda on 2008-01-18
Could you please post the details of your internet connection?

---

### Post by kennycason on 2008-01-18
im not sure where or what specific information you would like to see. but i am connected through a proxy proxy2.kansaigaidai.ac.jp port 8080 at my japanese university. its a LAN line. sorry if its not enough info
my other computer is also connected through this proxy, and no problems.

---

### Post by PmDematagoda on 2008-01-18
I think the problem you are having is the fact that you are behind a proxy. Try connecting directly to the internet and see if that solves your problem.

---

### Post by kennycason on 2008-01-18
I dont really have an accessible locatoin to the internet other than using the proxy. so i will have to wait to try this. 
it seems strange to me that its a proxy problem because my other compter (sitting right by this one) works and updates fine under the exact same proxy. i just checked it again to confirm it. sorry for the trouble

---

### Post by kennycason on 2008-01-19
Problem fixed. it turns out that the Japanese students and foreign students proxy settings or something along those lines are different, and when we connected directly to the internet at his house, everything worked fine. 
Thanks for the help!

---

### Post by seijling on 2008-02-19
I am having a similar problem.  The funny thing is that I am not behind a proxy.


I think my problem stems from IPv6 (vs IPv4).  I was troubleshooting a connectivity problem with my 3945abg wireless card (or so i thought) and found that disabling IPv6 allowed me to connect to to the internet after hours of bashing. The thing is, I cannot seem to get the ipv6 disabled globally despite the description in the support doc:

[https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28guide%29%7C%28troubleshooting%29%7C%28wireless%29](https://help.ubuntu.com/community/WifiDocs/WirelessTroubleShootingGuide?highlight=%28guide%29%7C%28troubleshooting%29%7C%28wireless%29)

Mike

---

