---
title: "Ubuntu Netbook Remix 10.04 won't upgrade to 10.10"
date: 2010-11-20
forum: Installation &amp; Upgrades
---

### Post by daktari81 on 2010-11-20
I'm having a problem with my netbook; it has Netbook Remix 10.04 and doesn't seem to want to upgrade to 10.10 no matter what I try.  I've tried mounting the .iso for it as a cdrom drive, as well as the Update Manager, which doesn't tell me there's a new version out even after I check for updates.  Any ideas?

---

### Post by sikander3786 on 2010-11-20
You cannot do an upgrade from a Live CD image. However it can be done using the alternate disc.

Do these commands list any error?

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

Try starting update manager from terminal by,

```
update-manager -d
```

Also see under Software Sources > Update > Release Upgrade and select Show regular releases or something like that.

---

### Post by rajaiskandarshah on 2011-05-14
thanks,

```
sudo update-manager -d
```

worked

---

### Post by LouisBlank on 2011-12-17
Uug...

I didn't realize that this machine was still running Lucid.  I tried

 sudo update-manager -d

... and it says it wants to upgrade me to 12.04 - no thanks - been there tried that...

Is there anyway to force it to just upgrade one step?  I want to go to 10.10 - and stay there - until I can find another distro to replace Ubuntu now that it is inoperative (11.04 and above)

Thanks.

---

### Post by mikewhatever on 2011-12-17
Upgrading from the NBR 10.04 to 10.10 is an odd move. 10.10 NBR, aka Ubuntu Netbook Edition was an experimental release, unstable and barely usable. In addition, 10.10 is reaching End of Life in April 2012, while 10.04 will be supported till April 2013, though not the NBR components.

Anyway, if you still want to upgrade, open Software Sources/Updates Tab, and allow upgrades to non-LTS releases.

Best of luck.

---

