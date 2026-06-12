---
title: "Failed to fetch error during update -- Linux Mint 17.3 Rosa"
date: 2018-08-17
forum: MINT
---

### Post by bukaida on 2018-08-17
I am new to linux. So, I am listing up what I tried so far blindly following similar threads in this forum...

```
bash-4.3# lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa
```

Then the ping

```
bash-4.3# ping -c3 ubuntu.com
PING ubuntu.com (91.189.94.40) 56(84) bytes of data.
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=1 ttl=49 time=163 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=2 ttl=49 time=163 ms
64 bytes from ovinnik.canonical.com (91.189.94.40): icmp_seq=3 ttl=49 time=164 ms

--- ubuntu.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 2001ms
rtt min/avg/max/mdev = 163.332/163.682/164.350/0.576 ms
```

The sources

```

bash-4.3# grep "^[^#]" /etc/apt/sources.list{,.d/*}
/etc/apt/sources.list.d/getdeb.list:deb http://archive.getdeb.net/ubuntu wily-getdeb apps 
/etc/apt/sources.list.d/jonathonf-python-3_6-trusty.list:deb http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu trusty main
/etc/apt/sources.list.d/jonathonf-python-3_6-trusty.list:deb-src http://ppa.launchpad.net/jonathonf/python-3.6/ubuntu trusty main
/etc/apt/sources.list.d/official-package-repositories.list:deb http://packages.linuxmint.com rosa main upstream import 
/etc/apt/sources.list.d/official-package-repositories.list:deb http://extra.linuxmint.com rosa main
/etc/apt/sources.list.d/official-package-repositories.list:deb http://archive.ubuntu.com/ubuntu trusty main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://archive.ubuntu.com/ubuntu trusty-updates main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://security.ubuntu.com/ubuntu/ trusty-security main restricted universe multiverse
/etc/apt/sources.list.d/official-package-repositories.list:deb http://archive.canonical.com/ubuntu/ trusty partner
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main
/etc/apt/sources.list.d/ubuntu-wine-ppa-trusty.list:deb-src http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu trusty main



```

Tried to remove and perform clean update

```
rm -r /var/lib/apt/lists/*
apt-get clean && apt-get update
```

And got the following errors after few successful header updates

```
Failed to fetch http://archive.getdeb.net/ubuntu/dists/wily-getdeb/Release.gpg  Connection failed
Failed to fetch http://archive.getdeb.net/ubuntu/dists/wily-getdeb/apps/binary-i386/Packages  Connection failed
Failed to fetch http://archive.getdeb.net/ubuntu/dists/wily-getdeb/apps/i18n/Translation-en_IN  Connection failed
Failed to fetch http://archive.getdeb.net/ubuntu/dists/wily-getdeb/apps/i18n/Translation-en  Connection failed
Some index files failed to download. They have been ignored, or old ones used instead.
```

Please help. I am not being able to install/upgrade anything in the system.

---

### Post by deadflowr on 2018-08-17
*Thread moved to **Mint***

You need to remove the getdeb ppa, as it's listing it for the wily version of Ubuntu and that has not been supported for years now.
Once you remove the getdeb ppa, [s]you can try adding it again properly from here:
[https://www.ubuntuupdates.org/ppa/getdeb_apps?dist=trusty]("https://www.ubuntuupdates.org/ppa/getdeb_apps?dist=trusty")[/s]

scratch that, it looks like the getdeb repos are down and out. Maybe there is another getdeb repository somewhere, but the current one seems gone.

---

### Post by bukaida on 2018-08-17
This is the content of sources.list

*# deb cdrom:[Linux Mint 17.3 _Rosa_ - Release i386 20151129]/ trusty contrib main non-free*

---

### Post by Yellow Pasque on 2018-08-17
Delete the getdeb.list file:
```
sudo rm /etc/apt/sources.list.d/getdeb.list
sudo apt-get update
```
It contains only references to Ubuntu 15.10/Wily, which has long been EOL. I'm not even sure getdeb.net is around anymore. If it is around and you need something from it, you can add it back with a valid distro (like trusty or xenial).

---

### Post by bukaida on 2018-08-17
Thanks for the reference. I have removed getdeb.ppa via Administrator-->Software Manager. In your reference, I found a link for alternative mirrors. They specified it as 
```

Add the following software sources:

deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps

deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps

then get the software source key by copying and pasting the following in a terminal:

sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com A8A515F046D7E7CF

sudo apt-get update


```

And it worked.
I have run both 'update' and then 'upgrade' command. It is still running without any problem and doing lots of things. Hope it will upgrade everything to latest ( or does it require anything else?).
Thanks for the help.

Just found out my linux version is not upgraded, only modules were upgraded :(
```

bash-4.3# lsb_release -a
No LSB modules are available.
Distributor ID:    LinuxMint
Description:    Linux Mint 17.3 Rosa
Release:    17.3
Codename:    rosa


```

---

### Post by Yellow Pasque on 2018-08-17
> I found a link for alternative mirrors.
Once again, you are using an outdated/EOL version (lucid). Although the lucid repo may still exist, it's more likely to contain old packages and/or cause package conflicts with your trusty-based system.
You should use these repos if you really need something from getdeb on your Mint 17.x system:
```
deb http://mirrors.dotsrc.org/getdeb/ubuntu trusty-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu trusty-getdeb apps
```

> Just found out my linux version is not upgraded,

What do you mean? Are you trying to upgrade to a later version of Mint?

---

### Post by bukaida on 2018-08-17
> **Temüjin said:**
> Once again, you are using an outdated/EOL version (lucid). Although the lucid repo may still exist, it's more likely to contain old packages and/or cause package conflicts with your trusty-based system.
You should use these repos if you really need something from getdeb on your Mint 17.x system:
```
deb http://mirrors.dotsrc.org/getdeb/ubuntu trusty-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu trusty-getdeb apps
```



What do you mean? Are you trying to upgrade to a later version of Mint?

Yes, exactly :) just to get rid of all the obsolete stuffs without disturbing existing user files or softwares. Any method to do it online ?

---

### Post by Yellow Pasque on 2018-08-17
[https://community.linuxmint.com/tutorial/view/2316](https://community.linuxmint.com/tutorial/view/2316)

---

### Post by mörgæs on 2018-08-17
It seems like you have been upgrading in many iterations and various cruft is left behind. You might save yourself trouble by doing a fresh install.

---

