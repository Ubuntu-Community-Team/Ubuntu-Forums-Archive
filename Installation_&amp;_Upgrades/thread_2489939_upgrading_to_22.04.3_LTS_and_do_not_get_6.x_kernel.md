---
title: "upgrading to 22.04.3 LTS and do not get 6.x kernel. Why ?"
date: 2023-08-15
forum: Installation &amp; Upgrades
---

### Post by georgesgiralt on 2023-08-15
Hello all,
I have this laptop whic stayed running 20.04LTS for more tha a year  for various reasons. Seing that the point release 22.04.3 was out, I thought it was time to upgrade. 
Process went without any glitches (of course I had to reinstall Unison and compile DisplayCal, and check configuration files for differences between my customised versionand the new one, but flawless)
I was surprised to find after the upgrade that I did not get the latest 6.2 kernel as promised. 
And I wonder if it has to do with Ubuntu Pro being enabled on this laptop or if I have something do do to get it ? 
Many thanks in advance for your help and insight on this matter ! 
have a nice and bright day !

---

### Post by oldfred on 2023-08-15
See this, both 22.04 & 22.04.1 keep same kernel for stability and those who must have stable system. 
Then .3 and later installs use new kernel for newer hardware. You can update original installs.

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

sudo apt install linux-generic-hwe-22.04

---

### Post by georgesgiralt on 2023-08-15
Thank you OldFred, I suspected something like that. So I must specifically ask for the HWE kernel. 
Have a nice day !

---

### Post by MAFoElffen on 2023-08-15
To check if you have the HWE stack installed, do this (since you are 22.04)
```

mafoelffen@Mikes-ThinkPad-T520:~$ apt list linux-*hwe-22.04 --installed
Listing... Done
[COLOR=#ff0000]linux-generic-hwe-22.04[/COLOR]/jammy-updates,now 6.2.0.26.26~22.04.7 amd64 [installed,automatic]
linux-headers-generic-hwe-22.04/jammy-updates,now 6.2.0.26.26~22.04.7 amd64 [installed,automatic]
linux-image-generic-hwe-22.04/jammy-updates,now 6.2.0.26.26~22.04.7 amd64 [installed,automatic]
linux-modules-nvidia-390-generic-hwe-22.04/jammy-updates,now 6.2.0-26.26~22.04.1+2 amd64 [installed]

```
To install it for your machine, you take the last LTS release # in the series... For example, releases 22.04, 22.10, 23.04, 23.10 would all be $LTS_RELEASE=22.04. Then do
```

LTS_RELEASE=22.04
sudo apt install linux-generic-$LTS_RELEASE

```

---

