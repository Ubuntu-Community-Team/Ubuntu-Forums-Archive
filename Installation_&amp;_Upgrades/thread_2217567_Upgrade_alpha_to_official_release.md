---
title: "Upgrade alpha to official release?"
date: 2014-04-17
forum: Installation &amp; Upgrades
---

### Post by felgro on 2014-04-17
The blessed release is now out. I have been running an alpha quite happily since January. Should I nuke and pave, or is upgrading known to be safe?

---

### Post by cariboo on 2014-04-17
If you've been doing regular updates, you will have the final version already.

---

### Post by dawgfan16 on 2014-04-17
I did it both ways and had no issues. Upgraded on my desktop and did a fresh install on the laptop. Both went smoothly.

---

### Post by felgro on 2014-04-18
> **cariboo907 said:**
> If you've been doing regular updates, you will have the final version already.

Nope. Been fetching updates but its still alpha.

---

### Post by felgro on 2014-04-18
> **dawgfan16 said:**
> I did it both ways and had no issues. Upgraded on my desktop and did a fresh install on the laptop. Both went smoothly.

So it won't necessarily explode and is worth a shot? Thanks, all I needed to know.

---

### Post by Elfy on 2014-04-18
> **felgro said:**
> Nope. Been fetching updates but its still alpha.

try a dist-upgrade

---

### Post by deadflowr on 2014-04-18
> **felgro said:**
> Nope. Been fetching updates but its still alpha.

Where is it telling you that it's still alpha?

Anyway, a dist-upgrade should pull you up to the final release.
As will simply running software updater.
Make sure to click install when the packages are listed.


Though, I wouldn't be surprised to see a partial upgrade wanted(needed)
I would suspect, though, that if a partial upgrade was needed, it should be okay. But tread lightly.
Here's a quick overview of those
[https://wiki.ubuntu.com/U%2B1/partial_upgrade](https://wiki.ubuntu.com/U%2B1/partial_upgrade)
just in case.

---

### Post by rifak on 2014-04-18
Is anyone getting the new wallpapers? Did a full update this morning and everything went smoothly, but I still see the 13.10 salamander wallpapers...? It's making me think that the full update is not occurring by simply updating throughout.

---

### Post by felgro on 2014-04-28
> **elderflower said:**
> Where is it telling you that it's still alpha?

It was telling me it was 13.10 on the startup screen - which is what I had on the clean alpha install. Which I only installed as a last resort due to [AMD misery]("http://ubuntuforums.org/showthread.php?t=2204332&p=12923072#post12923072"). This is the status -

Discovered that the software update service scheduler was completely broken, hence no updates. Launched manually and there was ~600mb of updates, which I fetched - and which necessitated a reboot. Rebooted only to discover the AMD proprietary driver and xorg were completely trashed - back to the state I was in when I first got this machine, no graphics whatsoever, just a shell. The update was only partial, so not really expecting much, ran -

```
sudo apt-get update && sudo apt-get dist-upgrade
```

and rebooted. Then I received first pleasant surprise - the desktop loaded, told me I had 14.04 and the xserver AMD driver had downloaded, installed and configured itself. Not just that, my machine can now recover from sleep instead of going into a coma - this has always been a problem for me on Dells. I find it odd that the LiveCD option fails to load graphics though.

So a final question - is there a simple way to verify I have the full LTS release installed correctly?

---

### Post by coffeecat on 2014-04-28
As 14.04 is now released...

*Thread moved to **Installation & Upgrades**.*

To answer your last question, run this in a terminal:

```
cat /etc/lsb-release 
```

This is the output I get on a 14.04 system upgraded from 13.10:

```
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=14.04
DISTRIB_CODENAME=trusty
DISTRIB_DESCRIPTION="Ubuntu 14.04 LTS"

```

---

### Post by jerrylamos on 2014-04-28
I did a zsync for the latest tahr amd64.

Fresh install.

sudo gedit /etc/apt/sources.list

did a replace all trusty to utopic

save.  

sudo apt-get update

sudo apt-get dist-upgrade

Then reboot. It's running.  Past experience a new development release will run O.K. soon after it is available - then Wham!  The dread updates begin.

I re-install often....

---

