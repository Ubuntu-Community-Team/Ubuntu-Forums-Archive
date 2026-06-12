---
title: "Two Broken Packages Prevent Upgrade"
date: 2024-08-23
forum: Installation &amp; Upgrades
---

### Post by wmichaelb2 on 2024-08-23
I just used the upgrade tool to upgrade Ubuntu Studio 22.04 to 24.04k, standard KDE desktop. The system boots and runs, but is blocking hundreds of updates because two packages are labeled as having unmet dependencies. Unfortunately, the package versions that are installed are the only ones available:

```
[FONT=monospace][COLOR=#000000]The following packages have unmet dependencies: [/COLOR]
 libfontconfig1 : Depends: fontconfig-config (>= 2.15.0-1.1ubuntu2) 
 libfontconfig1:i386 : Depends: fontconfig-config:i386 (>= 2.15.0-1.1ubuntu2) 
E: Unmet dependencies. Try 'apt --fix-broken install' with no packages (or specify a solution).
[/FONT]
```

Running apt --fix-broken install with no packages does nothing. Synaptic shows fontconfig-config 2.15.0-1.1ubuntu2 and fontconfig-config:i386 2.15.0-1.1ubuntu2 as both the  installed and latest versions. Can someone suggest where I can go from here? Thanks in advance.

---

### Post by grahammechanical on 2024-08-24
Do daily apt update/upgrade/--fix-broken install   and see if the situation rights itself over time. Does the OS work otherwise?

Regards

---

### Post by wmichaelb2 on 2024-08-26
Found out that Ubuntu 24.04 doesn't support the CLI upgrade tool yet. Redownloaded the iso, ran the checksum, and reinstalled. The new installation works. Thanks to all for your suggestions.

---

