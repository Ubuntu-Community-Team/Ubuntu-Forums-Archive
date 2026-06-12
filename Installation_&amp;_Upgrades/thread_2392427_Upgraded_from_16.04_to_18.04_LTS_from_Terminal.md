---
title: "Upgraded from 16.04 to 18.04 LTS from Terminal"
date: 2018-05-21
forum: Installation &amp; Upgrades
---

### Post by soal159 on 2018-05-21
The commands I used were:

sudo apt-get install update-manager-core

sudo nano /etc/update-manager/release-upgrades

sudo do-release-upgrade -d


I tried this method and my dvd’s/cd’s or usb’s won’t mount or mount very  delayed, not even a prompt. Also now my computer takes the full 30mins  to reboot or shutdown. I have used 16.04 as a sole OS on my machine for  the full two years. I was trying not to do a reimage of my computer. Everything just doesn't work right anymore. Nothing mounts without responding 20 minutes later and it stalls on shutdown with stopping cryptswap1. If anyone has a way to solve this without erasing my hard drive and starting over please help.

---

### Post by oldos2er on 2018-05-21
> sudo do-release-upgrade -d would've updated you to 18.10, if it's available to the updater. I don't know if it is or not.

Can you post outout of ```
cat /etc/apt/sources.list
``` ?

---

### Post by cruzer001 on 2018-05-21
sudo do-release-upgrade -d 

That is the correct command for LTS to LTS upgrade to 18.04

[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

Is this a server install?

---

### Post by oldos2er on 2018-05-21
The -d flag updates to the development release,  but as I said I don't know if 18.10 is available through the update manager yet.

---

### Post by PaulW2U on 2018-05-21
> **cruzer001 said:**
> sudo do-release-upgrade -d 

That is the correct command for LTS to LTS upgrade to 18.04
I'm not sure that is always the case and I think it depends on exactly when during a development cycle the command is issued.

See [http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/do-release-upgrade.8.html)
```
      -d, --devel-release
              If  using  the  latest  supported  release,   upgrade   to   the  development release

```
I used that command to upgrade Xubuntu 16.04 to 18.04 two days after 18.04 was released but before the 18.10 repositories had been opened. There was no development release at that time but it seems it was still set to being 18.04 so that was what I was offered.

The man page doesn't say what happens if the -d switch is used from anything other than the latest supported release, i.e. 14.04, 16.04 or 17.10.

The man page for update-manager is equally vague - [http://manpages.ubuntu.com/manpages/bionic/man8/update-manager.8.html](http://manpages.ubuntu.com/manpages/bionic/man8/update-manager.8.html)

If I had a 16.04 installation to upgrade I would be very careful accepting what I was being offered at this time.

---

### Post by monkeybrain20122 on 2018-05-21
Back up your data and do a clean install.

---

### Post by cruzer001 on 2018-05-21
> -d, --devel-release
              If  using  the  latest  supported  release,   upgrade   to   the  development release
That is correct for the latest supported release, but for lts to lts before 18.04.1 comes out you use the -d switch.  Its in that link I posted.  I have used it in the past, the only problem is it sometimes will do nothing.

---

### Post by PaulW2U on 2018-05-21
> **cruzer001 said:**
> That is correct for the latest supported release, but for lts to lts before 18.04.1 comes out you use the -d switch.
I've just installed Ubuntu 16.04.4 in Virtualbox and the -d switch does indeed prompt an upgrade to Ubuntu 18.04 at this time. It's a shame that the documentation isn't a little more complete and consistent across various sources. 

Just for the record:

1) When I was set to be notified of any new version then **do-release-upgrade** notified me of Ubuntu 17.10 but **do-release-upgrade -d** advised me that upgrades to the development release are only available from the latest supported release.

2) When I was set to be notified of a new LTS version then **do-release-upgrade** told me that a new version was not available but **do-release-upgrade -d** prompted me to upgrade to Ubuntu 18.04.

3) At no time did I see any prompt to upgrade to Ubuntu 18.10.

Confused? I am. But thanks cruzer001 for pointing out that link. I just had to check.  :)

I think more needs to be advised when telling people what command to use such as the notification setting and the time of the .1 release.

---

### Post by cruzer001 on 2018-05-21
^^^
Well said Paul

---

### Post by oldos2er on 2018-05-21
Thanks!

---

### Post by soal159 on 2018-05-21
> **oldos2er said:**
> would've updated you to 18.10, if it's available to the updater. I don't know if it is or not.

Can you post outout of ```
cat /etc/apt/sources.list
``` ?

```
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic restricted multiverse universe main
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) bionic-security restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-updates restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) bionic-backports multiverse restricted universe main
```

---

### Post by PaulW2U on 2018-05-21
soal159, so you have 18.04 as intended and not 18.10 as some of the documentation implied might be the case.

---

### Post by soal159 on 2018-05-22
> **PaulW2U said:**
> soal159, so you have 18.04 as intended and not 18.10 as some of the documentation implied might be the case.

I'm starting to think the issue is with my full disk encryption sda5_crypt. everytime I shutdown or reboot the machine I get hang up at 

```
A Stop Job is running for Cryptography setup for Cryptswap1 ( time/no limit)
```

it is this and the delayed response for usb's and cd/dvd's. I didn't have this issue on 16.04.

---

