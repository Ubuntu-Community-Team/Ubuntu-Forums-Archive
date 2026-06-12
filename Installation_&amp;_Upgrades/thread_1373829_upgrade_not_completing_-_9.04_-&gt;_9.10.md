---
title: "upgrade not completing - 9.04 -&gt; 9.10"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by cr0wn3r on 2010-01-06
I've started the upgrade process from Ubuntu 9.04 to 9.10, but the process seems to have got stuck.

The Distribution Upgrqade box has successfully worked through:
- Preparing to Upgrade
- Setting new software channels
- Getting new packages

But it has been on the next phase "Installing the upgrades" for hours.

Just under the progress bar (which apears completely empty) it says
"Running post-installation trigger libc6"

And in the attached terminal the output so far has been:
```

Extract templates from packages: 100%
Preconfiguring packages ...
console-setup failed to preconfigure with exit status 139
Extract templates from packages: 100%
Preconfiguring packages ...
(Reading database ... 207980 files and directories currently installed.)
Removing libmbca0 ...
Removing bluez-gnome ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place

```

I havent tried rebooting or killing the process as I noticed the stern warning that once started the process can not be cancelled. I did try opening another terminal but this doesnt work - the task bar item "starting terminal" appears, then disapears again after a few seconds.

Thanks.

---

