---
title: "Upgrade to 10.10 via Upgrade Manager"
date: 2010-11-23
forum: Installation &amp; Upgrades
---

### Post by joneslh on 2010-11-23
Now that the dust has settled somewhat on 10.10 release, I am looking to upgrade from 10.04 using the Update Manageras I normally do for upgrades.

However, it is still showing 10.10 as a Development Release.  Is this correct ?

---

### Post by sikander3786 on 2010-11-23
> **joneslh said:**
> Now that the dust has settled somewhat on 10.10 release, I am looking to upgrade from 10.04 using the Update Manageras I normally do for upgrades.

However, it is still showing 10.10 as a Development Release.  Is this correct ?
No it is not the development release, it is stable now.

Make sure you have applied all the updates.

```
sudo apt-get update && sudo apt-get upgrade
```

And also see this page before upgrading.

[https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes](https://wiki.ubuntu.com/MaverickMeerkat/ReleaseNotes)

Good Luck!

---

### Post by Hans Upp on 2010-11-23
> **sikander3786 said:**
> ```
sudo apt-get update && sudo apt-get upgrade
```
That does not update me from 10.04 to 10.10. The only thing it seems to try to update is that stupid gwibber thing.

Is there something missing?

---

### Post by joneslh on 2010-11-23
Thanks all for your replies.

I have now upgraded to 10.10 via update manager and everything seems to be working ok.

Only problem (as I was expecting) is the boot up splash screen which needs a bit of reconfig as I had to do for 10.04 as using a Nvida graphics card.

---

### Post by Quackers on 2010-11-23
> **Hans Upp said:**
> That does not update me from 10.04 to 10.10. The only thing it seems to try to update is that stupid gwibber thing.

Is there something missing?

If you go to Software Sources and go to the Updates tab does it say "Long term support releases only" in the box under "Release Upgrade". If so change to "Normal Releases"

---

### Post by sikander3786 on 2010-11-23
> **Hans Upp said:**
> That does not update me from 10.04 to 10.10. The only thing it seems to try to update is that stupid gwibber thing.

Is there something missing?
That will not upgrade your distro but it would apply all the updates for your present distro.

update-manager -d should bring up the distro upgrade option then.

Follow the procedure mentioned by Quackers and make sure you have the appropriate settings for release upgrades.

Then if you want to upgrade from command-line,

```
sudo do-release-upgrade
```

> **joneslh said:**
> Only problem (as I was expecting) is the boot up splash screen which needs a bit of reconfig as I had to do for 10.04 as using a Nvida graphics card.

There are multiple workarounds for fixing that. See here for one.

[http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/](http://linuxhub.net/2010/09/fix-ugly-plymouth-screen-on-ubuntu-10-10-using-a-simple-script/)

Good Luck!

---

