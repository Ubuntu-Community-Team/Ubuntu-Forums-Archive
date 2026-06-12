---
title: "Xubuntu not offering upgrade"
date: 2024-04-27
forum: Installation &amp; Upgrades
---

### Post by peyre on 2024-04-27
I've been looking forward to the upgrade to 24.04 LTS.  Xubuntu was released on the same day as Ubuntu, but it's been a couple days now and none of my Xubuntu machines have offered the upgrade.  Software Updater insists I'm up to date, sudo apt update && sudo apt upgrade && sudo do-release-upgrade say there's nothing available.  I'm running 23.10 on my two laptops, and 22.04 LTS on my desktop.  Am I missing something, or is there maybe a delay before in-place upgrades are offered?  Like releasing the latest ISO is one thing, but in-place upgrades take extra preparation?

---

### Post by Impavidus on 2024-04-27
See [https://ubuntuforums.org/showthread.php?t=2497219](https://ubuntuforums.org/showthread.php?t=2497219) or [https://ubuntuforums.org/showthread.php?t=2497215](https://ubuntuforums.org/showthread.php?t=2497215)

The same applies to all flavours and it happens for every version.

---

### Post by peyre on 2024-04-27
Thanks!  I wondered if it might be something like that.

---

### Post by Tadaen_Sylvermane on 2024-04-27
If you are feeling frisky you can do the upgrade via the Debian method and and not use the provided upgrade tool. I did this to upgrade a chroot installed Jammy > Kinetic > Lunar > Mantic > Noble the other day. Was both an experiment and I had no desire to download another iso. Thus far it's running perfectly. In my case I have no non Ubuntu repositories installed so it was painless. The process I followed was simple.

Modify sources.list

```
apt update && apt upgrade && apt full-upgrade
```

Reboot

```
apt clean && apt --purge autoremove
```

Rinse lather repeat through each release or straight to Noble if coming from Jammy I suppose. Kept my streamlined sources.list if you want it as well.

```
#deb http://us.archive.ubuntu.com/ubuntu jammy main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu jammy-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ jammy-security main restricted universe multiverse 
#deb http://us.archive.ubuntu.com/ubuntu jammy-updates main restricted universe multiverse

#deb http://old-releases.ubuntu.com/ubuntu kinetic main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu kinetic-security main restricted universe multiverse
#deb http://old-releases.ubuntu.com/ubuntu kinetic-updates main restricted universe multiverse

#deb http://us.archive.ubuntu.com/ubuntu lunar main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu lunar-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ lunar-security main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu lunar-updates main restricted universe multiverse

#deb http://us.archive.ubuntu.com/ubuntu mantic main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu mantic-security main restricted universe multiverse
#deb http://security.ubuntu.com/ubuntu/ mantic-security main restricted universe multiverse
#deb http://us.archive.ubuntu.com/ubuntu mantic-updates main restricted universe multiverse

deb http://us.archive.ubuntu.com/ubuntu noble main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu noble-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ noble-security main restricted universe multiverse
deb http://us.archive.ubuntu.com/ubuntu noble-updates main restricted universe multiverse
```

There was a single hiccup I think in the upgrade from Lunar > Mantic. It hung up so I ran

```
apt install -fy
```

Then finished the upgrade with the previous command

```
apt upgrade && apt full-upgrade
```

Use this method at your own risk. Worked just fine for me through the 4  releases in a row. This method is not supported by Canonical or Ubuntu in  general.

---

### Post by peyre on 2024-05-23
I was able to upgrade my two Xubuntu laptops using **sudo do-release-upgrade -d**.  Took forever, but worked like a charm.

I'm not sure I want to do this on my main system, the desktop.  That's always a pain to reinstall from scratch.

---

