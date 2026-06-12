---
title: "Still getting message about doing 12.10 upgrade"
date: 2012-12-30
forum: Installation &amp; Upgrades
---

### Post by neddfreddy on 2012-12-30
I upgraded from 12.04.1 LTS to 12.10 and I still get the login message to run do-release-upgrade. When I did the upgrade, it ran through all the way and rebooted fine. When I check the release file it still shows me at the same version.

> $ cat /etc/*release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
NAME="Ubuntu"
VERSION="12.04.1 LTS, Precise Pangolin"
ID=ubuntu
ID_LIKE=debian
PRETTY_NAME="Ubuntu precise (12.04.1 LTS)"
VERSION_ID="12.04"

$ uname -a
Linux ubuntu-01 3.2.0-35-generic #55-Ubuntu SMP Wed Dec 5 17:42:16 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
If I run the do-release-upgrade command again it tells me no new release found.

Did I do something wrong? If not, how can I get rid of this message?

I just had the thought, that maybe 12.10 is not LTS and so all it did was update the packages or something?

Thanks!

---

### Post by Cheesemill on 2012-12-30
By the looks of things you are still on 12.04, as 12.10 uses the 3.5 series kernel.

If you go to Update Manager > Settings and click on the Updates tab what does it say next to 'Notify me of a new Ubuntu version' ?

---

### Post by neddfreddy on 2012-12-30
> **Cheesemill said:**
> By the looks of things you are still on 12.04, as 12.10 uses the 3.5 series kernel.

If you go to Update Manager > Settings and click on the Updates tab what does it say next to 'Notify me of a new Ubuntu version' ?

I'm running the server version, w/o the GUI.

---

### Post by ibjsb4 on 2012-12-30
Go to:

/etc/update-manager/release-upgrades

And make sure prompt is set to normal.

Prompt=normal

---

### Post by darkod on 2012-12-30
> **ibjsb4 said:**
> Go to:

/etc/update-manager/release-upgrades

And make sure prompt is set to normal.

Prompt=normal

Why? You would usually use only LTS on a server and it's better that way. Unless you specifically want to upgrade to 12.10, leave the prompt at lts.

But in that case it shouldn't prompt you to upgrade to 12.10.

How can you not be sure whether you upgraded to 12.10 or not? If you did only:
sudo apt-get upgrade

that only upgrades/updates the packages, not the ubuntu version. It will not try to upgrade until you try do-release-upgrade. But as already mentioned, whether to run that or not depends on whether you really want to upgrade from LTS to non-LTS version or not. If you want to stick only to LTS, leave the prompt to lts and it should not prompt you about a new release until the next LTS.

---

### Post by ibjsb4 on 2012-12-30
> **darkod said:**
> Why? You would usually use only LTS on a server and it's better that way. Unless you specifically want to upgrade to 12.10, leave the prompt at lts.

I would agree with that, but the way I am reading it, the OP wants to do-release-upgrade.

---

### Post by neddfreddy on 2012-12-30
> **darkod said:**
> Why? You would usually use only LTS on a server and it's better that way. Unless you specifically want to upgrade to 12.10, leave the prompt at lts.

But in that case it shouldn't prompt you to upgrade to 12.10.

How can you not be sure whether you upgraded to 12.10 or not? If you did only:
sudo apt-get upgrade

that only upgrades/updates the packages, not the ubuntu version. It will not try to upgrade until you try do-release-upgrade. But as already mentioned, whether to run that or not depends on whether you really want to upgrade from LTS to non-LTS version or not. If you want to stick only to LTS, leave the prompt to lts and it should not prompt you about a new release until the next LTS.

So 12.10 is not LTS like I was thinking? If so, yea my issue is that I am being erroneously prompted to upgrade.

I did run the do-release-upgrade command to run the upgrade, and it did upgrade a whole bunch of stuff. Took at least 20 minutes, rebooted, and the prompt is still there. I have logged back in several times and it's not going away on it's own :D

In the file  /etc/update-manager/release-upgrades the following is set:

> Prompt=ltsI changed it to never just for grins and rebooted the server. Logged back in and the message is still there.

It's not a huge issue obviously, but it is kinda annoying if anyone has any other ideas.

---

### Post by ibjsb4 on 2012-12-30
```
sudo apt-get remove --reinstall update-manager-core
```

See if that will clear it up.

---

### Post by neddfreddy on 2012-12-30
> **ibjsb4 said:**
> ```
sudo apt-get remove --reinstall update-manager-core
```See if that will clear it up.

Yep that fixed 'er up. Thank you! :D

---

### Post by ibjsb4 on 2012-12-30
And welcome to the forums  :)

---

