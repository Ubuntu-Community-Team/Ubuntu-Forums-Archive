---
title: "Upgrade left me with &quot;Ubuntu Focal Fossa (development branch)&quot; instead of LTS"
date: 2020-05-29
forum: Installation &amp; Upgrades
---

### Post by lister171254 on 2020-05-29
The Upgrade to the latest (Ubuntu 20.04 LTS) Desktop from 19.04 didn't quite go as smooth as I hoped.

The upgrade to 19.10 crashed with the "Oops something went wrong" Window popping up. Rebooting left that kernel unbootable, so I booted to the latest bootable kernel and continued the upgrade from the command line.
Eventually everyhing worked ok, but I now have a development branch of 20.04 instead of LTS.

I'd appreciate any hints on how I can get to the LTS version.
Thanks

---

### Post by guiverc on 2020-05-29
Some details maybe necessary, such as what command you as using that tells you that you are using the development release, as well as your used command to upgrade you from 19.10 to 20.04/focal.

I booted a Lubuntu 20.04 LTS system (installed as a QA-test using a RC/beta ISO so technically a *focal fossa* install that was upgraded normally (ie. `sudo apt full-upgrade`) to become a 20.04 system, and it reported Ubuntu 20.04 LTS using both `neofetch` or `lsb_release` type commands.

Thus I'd expect your system to likewise say 20.04, so what command did you use that tells you your system is *focal fossa*&#8203;?

---

### Post by lister171254 on 2020-05-29
Sorry for being not more precise in the details, but not being a guru I clicked on the GUI interface that indicated an upgrade was available, selected to upgrade and after the failure used all sorts of commands (from feedback on other failures) to get the system back into a usable state.

I'm sure one of the commands was sudo do-release-upgrade.

Doing a "sudo apt full-upgrade" now indicates 0 to upgrade

The command I used to show the develpers version is

lsb_release -a

---

### Post by guiverc on 2020-05-29
I don't have a 19.10 system upgraded to 20.04 (anymore anyway, my main box I'm typing this into upgraded such last October, but bumped again to *groovy* last month), why I booted a QA-test install of *focal fossa*

Can you please `apt-cache policy base-files` and `cat /etc/lsb-release` and provide the output.

(I did a `dpkg -S /etc/lsb-release` to see the package that contained that output; a [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=base-files](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=base-files) shows what I'd expect your apt-cache command show)

---

### Post by lister171254 on 2020-05-29
```
apt-cache policy base-files
base-files:
  Installed: 11ubuntu2
  Candidate: 11ubuntu2
  Version table:
 *** 11ubuntu2 500
        500 [http://ubuntu.mirror.digitalpacific.com.au/archive](http://ubuntu.mirror.digitalpacific.com.au/archive) focal/main amd64 Packages
        100 /var/lib/dpkg/status
```

```
cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=20.04
DISTRIB_CODENAME=focal
DISTRIB_DESCRIPTION="Ubuntu Focal Fossa (development branch)"
```

---

### Post by grahammechanical on 2020-05-29
I have been running 20.04 development branch for most of its 26 weeks development period. At the right time it updated to 20.04 LTS. I can only guess that at some point you gave an instruction to upgrade to the 20.04 development version. I would have said that it was not possible to upgrade to a development version of a release that has already been released but you may have proved me wrong.

Try

```
sudo apt update
sudo apt upgrade
```

Regards

---

### Post by lister171254 on 2020-05-30
```
sudo apt upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 to upgrade, 0 to newly install, 0 to remove and 0 not to upgrade.
```

---

### Post by deadflowr on 2020-05-30
My guess is the mirror in use is out of whack.
Perhaps try switching mirrors.
[https://linuxconfig.org/how-to-select-the-fastest-apt-mirror-on-ubuntu-linux]("https://linuxconfig.org/how-to-select-the-fastest-apt-mirror-on-ubuntu-linux")

---

### Post by guiverc on 2020-05-30
I agree with @deadflowr

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors) shows the mirror is *unknown *(which usually means it's more days behind the official mirror than the counter can cope with thus its overflowed).

Switch to a better maintained mirror (from prior link).

---

### Post by lister171254 on 2020-05-30
Switched to the Australian main mirror; same result

---

### Post by guiverc on 2020-05-30
Are you getting any errors with `sudo apt update`?, or are the messages you get correct for your release (which should be focal).

(A quick look and au.archive.ubuntu.com appears to be hosted by AARNet which are up-to-date)

---

