---
title: "Upgrade 23.10 to 24.04 crashed, how to execute post upgrade scripts?"
date: 2024-05-01
forum: Installation &amp; Upgrades
---

### Post by franz_s on 2024-05-01
Hi,

I've upgraded from 23.10 to 24.04 and got while upgrading a "Oh no! Something has gone wrong"-screen.
I managed to clean my apt packages (dpkg --configure -a, apt --fix-broken install, apt dist-upgrade ...).

But ... I think there are post upgrade scripts which were not executed:
My /etc/apt/sources.list is still available and was not migrated to deb822 ...

Is there a chance to find out which steps I have to do to fully complete my upgrade?

Thanks,

Franz

---

### Post by grahammechanical on 2024-05-01
I would like to suggest that the reason the upgrade from Ubuntu 23.10 to 24.04 failed was because the upgrade path is not yet open and will not be open until 6 months after Ubuntu 24.04 LTS has been released.

The hassle free way to upgrade is to use Software & Updates set to notify of a new Ubuntu version = any new version or for long-term support versions.

Then in time when you run Software Updater the invitation to upgrade to 2404 LTS will appear.

In the meantime those wishing to run 24.04 LTS are best advised to do a new installation from the ISO image.

Regards


Regards

---

### Post by franz_s on 2024-05-01
Sorry, but your post was not very helpful for me. And upgrade to 24.04 is not released after 6 month. (release notes: "Users of Ubuntu 23.10 will be offered an automatic upgrade to 24.04 soon after the release.")

My question again: Is there a chance to find out which steps I have to do to fully complete my upgrade?

---

### Post by Claus7 on 2024-05-02
Hello,

during the same upgrade as the OP, I still have /etc/apt/sources.list available as well, so I suppose that this is not an issue. The commands you mention are the correct ones so as for someone to resume a "broken" upgrade. Have you noticed something that is not working properly so as to have a clearer picture of what is not working as it should?

Regards!

---

### Post by franz_s on 2024-05-03
Hi Claus7,

thank you for your reply. You are right, /etc/apt/sources.list still exists, but it should be migrated during upgrade to /etc/apt/sources.list.d/ubuntu.sources. /etc/apt/sources.list has afterwards only this comment in it: "# Ubuntu sources have moved to /etc/apt/sources.list.d/ubuntu.sources"

Up to now I don't have any issues, but I am afraid that something other might not be migrated/upgrated etc.

New installation is not possible for me, because the new installer doesn't support full disk encryption up to now ... :( And ... I would be happy, if I could save me from a new installation. :)

Regads, Franz

---

### Post by Claus7 on 2024-05-03
Hello,

I do have /etc/apt/sources.list.d/ folder with many contents inside. The uncommented lines of my /etc/apt/sources.list are:
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble main universe multiverse restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) noble-security universe main multiverse restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) noble-updates universe main multiverse restricted

I'm not aware about the migration you mention, yet things seem to be working fine.

Regards!

---

### Post by MAFoElffen on 2024-05-03
The content of Noble's /etc/apt/sources.list.d/ubuntu.sources is now:
```

# Ubuntu sources have moved to /etc/apt/sources.list.d/ubuntu.sources

```
The content of Noble's /etc/apt/sources.list.d/ubuntu.sources is now:
```

Types: deb
URIs: http://us.archive.ubuntu.com/ubuntu/
Suites: noble noble-updates noble-backports
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg
Types: deb
URIs: http://security.ubuntu.com/ubuntu/
Suites: noble-security
Components: main restricted universe multiverse
Signed-By: /usr/share/keyrings/ubuntu-archive-keyring.gpg

```
That is how that works now.

---

### Post by franz_s on 2024-05-04
Yes, Noble now uses deb822 format. See release notes:
> deb822 sources management

The sources configuration for Ubuntu has moved from /etc/apt/sources.list to /etc/apt/sources.list.d/ubuntu.sources in the more featureful deb822 format, aligning with PPAs that already migrated to deb822 last year. See the specification 61 for more details.

This I missed on my upgrade after it failed ... I have manually migrated it. But - are there other things - beyond apt-packages - I should migrate/upgrade etc.?

---

### Post by #&amp;thj^% on 2024-05-04
> **franz_s said:**
>  But - are there other things - beyond apt-packages - I should migrate/upgrade etc.?

That should be good enough for now.

Unless you have other questions..

---

### Post by franz_s on 2024-05-04
> **1fallen said:**
> That should be good enough for now.

Thank you very much!

---

### Post by franz_s on 2024-05-04
And sorry ... but this failed upgrade triggered my OCD (despite of the deep brain stimulation) ...
And yes, next time I will wait until upgrade gets fully released ... :)

---

