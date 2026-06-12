---
title: "Problems with upgrading"
date: 2005-10-21
forum: Installation &amp; Upgrades
---

### Post by hauken on 2005-10-21
I'm trying to update from Hoary to Breezy, by following the steps at this pager: [https://wiki.ubuntu.com/BreezyUpgradeNotes]("https://wiki.ubuntu.com/BreezyUpgradeNotes")

While running the last command in the pre-upgrade section, I get this message:

------

hauge@dhcp-8-14-182:~$ sudo apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-base: Depends: libc6-i686 but it is not going to be installed
               Depends: locales but it is not going to be installed
  ubuntu-desktop: Depends: lsb but it is not going to be installed
E: Broken packages

------


Can anyone help a newbie wanting to try Breezy?

Thanks in advance!

---

### Post by Kyral on 2005-10-21
try

```
sudo apt-get -f install
```

---

### Post by hauken on 2005-10-21
Then I get this message:

hauge@dhcp-8-14-182:~$ sudo apt-get -f install ubuntu-base ubuntu-desktop
Password:
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-base: Depends: libc6-i686 but it is not going to be installed
               Depends: locales but it is not going to be installed
  ubuntu-desktop: Depends: lsb but it is not going to be installed
E: Broken packages



I tried

root@dhcp-8-14-182:~# apt-get install libc6-i686


But then I got this:


Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu13) but 2.3.2.ds1-22 is to be installed
E: Broken packages

---

### Post by Kyral on 2005-10-21
do the -f install without anything after it

So

```
sudo apt-get -f install
```

And only that :D

---

### Post by hauken on 2005-10-21
OK, but that does not make any difference:

root@dhcp-8-14-182:~# apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
root@dhcp-8-14-182:~# apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-base: Depends: libc6-i686 but it is not going to be installed
               Depends: locales but it is not going to be installed
  ubuntu-desktop: Depends: lsb but it is not going to be installed
E: Broken packages
root@dhcp-8-14-182:~#

---

### Post by Kyral on 2005-10-21
Hmm, I have verified that they are all in Hoary Main.

Can I see your /etc/apt/sources.list?

---

### Post by hauken on 2005-10-21
deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Kyral on 2005-10-21
[quote=hauken]deb cdrom:[Ubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary-updates main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary universe main restricted multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary universe

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe[/quote]

remove the CDROM line and then try

---

### Post by hauken on 2005-10-21
Still no difference. Now my etc/apt/sources.list is like this:


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe main restricted multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu](http://no.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

---

### Post by Kyral on 2005-10-21
[quote=hauken]Still no difference. Now my etc/apt/sources.list is like this:


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary-updates main restricted
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/]("http://archive.ubuntu.com/ubuntu/") hoary universe main restricted multiverse
# deb-src [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary universe

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security universe[/quote]

uncomment these lines

```

 # deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") hoary-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

```

Add "multiverse" onto the end of the universe line in the lines I told you to uncomment.

and uncomment these

```

deb [http://no.archive.ubuntu.com/ubuntu]("http://no.archive.ubuntu.com/ubuntu") hoary-updates main restricted

```

And change it to [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary-updates main restricted universe multiverse

Make sure you save it and then do a sudo apt-get update afterwards

---

### Post by hauken on 2005-10-24
Thanks for helping, but I still have the problem. My /etc/spt/sources.list looks like this:


```

## Uncomment the following two lines to fetch updated software from the network
# deb-src http://no.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu hoary-updates main restricted universe multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ hoary universe main restricted multiverse
# deb-src http://no.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
# deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe multiverse
# deb-src http://security.ubuntu.com/ubuntu hoary-security universe
```




After editing this file, I used these commands with results:

```

root@dhcp-8-14-182:/home/hauge # apt-get update
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Get:2 http://security.ubuntu.com hoary-security Release [16.9kB]
Get:3 http://archive.ubuntu.com hoary-updates Release.gpg [189B]
Get:4 http://archive.ubuntu.com hoary Release.gpg [189B]
Get:5 http://archive.ubuntu.com hoary-updates Release [16.8kB]
Get:6 http://security.ubuntu.com hoary-security/main Packages [73.4kB]
Hit http://archive.ubuntu.com hoary Release
Get:7 http://archive.ubuntu.com hoary-updates/main Packages [14.2kB]
Get:8 http://archive.ubuntu.com hoary-updates/restricted Packages [14B]
Get:9 http://archive.ubuntu.com hoary-updates/universe Packages [5836B]
Get:10 http://archive.ubuntu.com hoary-updates/multiverse Packages [14B]
Get:11 http://security.ubuntu.com hoary-security/restricted Packages [14B]
Get:12 http://security.ubuntu.com hoary-security/universe Packages [49.1kB]
Get:13 http://security.ubuntu.com hoary-security/multiverse Packages [14B]
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Fetched 177kB in 1s (116kB/s)
Reading package lists... Done

root@dhcp-8-14-182:/home/hauge # apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-base: Depends: libc6-i686 but it is not going to be installed
               Depends: locales but it is not going to be installed
  ubuntu-desktop: Depends: lsb but it is not going to be installed
E: Broken packages

root@dhcp-8-14-182:/home/hauge # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 116 not upgraded.

root@dhcp-8-14-182:/home/hauge # apt-get install ubuntu-base ubuntu-desktop
Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  ubuntu-base: Depends: libc6-i686 but it is not going to be installed
               Depends: locales but it is not going to be installed
  ubuntu-desktop: Depends: lsb but it is not going to be installed
E: Broken packages
root@dhcp-8-14-182:/home/hauge #

```

---

