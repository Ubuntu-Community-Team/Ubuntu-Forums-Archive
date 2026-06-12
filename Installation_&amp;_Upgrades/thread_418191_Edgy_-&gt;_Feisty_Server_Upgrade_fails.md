---
title: "Edgy -&gt; Feisty Server Upgrade fails"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by FattyCNS on 2007-04-22
Hi all,

I'm attempting to upgrade an edgy server to fiesty using 

```
sudo apt-get install update-manager-core
sudo do-release-upgrade
```

via SSH.

The upgrade gets through the download stage but fails here:


```

Preparing to replace sasl2-bin 2.1.19.dfsg1-0.2ubuntu3 (using .../sasl2-bin_2.1.22.dfsg1-8ubuntu2_i386.deb) ...
Stopping SASL Authentication Daemon: (failed).
invoke-rc.d: initscript saslauthd, action "stop" failed.
dpkg: warning - old pre-removal script returned error exit status 1
dpkg - trying script from the new package instead ...
Stopping SASL Authentication Daemon: (failed).
invoke-rc.d: initscript saslauthd, action "stop" failed.
dpkg: error processing /var/cache/apt/archives/sasl2-bin_2.1.22.dfsg1-8ubuntu2_i386.deb (--unpack):
 subprocess new pre-removal script returned error exit status 1
Starting SASL Authentication Daemon: /usr/sbin/saslauthd already running.
Errors were encountered while processing:
 /var/cache/apt/archives/sasl2-bin_2.1.22.dfsg1-8ubuntu2_i386.deb

Could not install the upgrades
```


I'm guessing that it's failing due to the SASL daemon not running. Has anyone got any tips on how to fix it?

---

### Post by Big Ed on 2007-04-24
I also tried to dist-upgrade my serve to Feisty with "sudo do-release-upgrade" over an ssl connection.  But it gave me a rather severe warning about connecting remotely using ssl to perform an upgrade.  So I went down into the basement and did it locally.  Have you tried doing that?  I ran into a few problems (31 held-back packages), but I got them fixed with "sudo dist-upgrade" and a reboot (for the new kernel).  

HTH,
Ed

---

