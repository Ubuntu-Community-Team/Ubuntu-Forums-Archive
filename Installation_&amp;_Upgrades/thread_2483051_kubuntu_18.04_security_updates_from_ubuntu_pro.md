---
title: "kubuntu 18.04: security updates from ubuntu pro"
date: 2023-01-19
forum: Installation &amp; Upgrades
---

### Post by mallt on 2023-01-19
I activated ubuntu pro for my kubuntu 18.04 desktop installation, and when running the command pro security-status I notice the Universe/Multiverse packages are receiving security updates from Ubuntu Pro with 'esm-apps' enabled until 2028

Since f.ex. the plasma-desktop package belongs to the universe  repository I was wondering if this means my kubuntu 18.04 desktop  installation will receive security updates until 2028?
 
Thanks!

---

### Post by TheFu on 2023-01-19
[https://kubuntu.org/news/kubuntu-18-04-lts-bionic-beaver-reaches-end-of-kubuntu-support/](https://kubuntu.org/news/kubuntu-18-04-lts-bionic-beaver-reaches-end-of-kubuntu-support/)

> Kubuntu 18.04 LTS was released in April 2018, and reached ‘End of Life’ for its 3 years of flavour support on 1st May 2021. All Kubuntu users should therefore switch to a newer supported release. 

Seems pretty clear to me.  1.5 yrs without support is a long time to risk.

---

### Post by ian-weisser on 2023-01-19
> **mallt said:**
> I was wondering if this means my kubuntu 18.04 desktop  installation will receive security updates until 2028?

No: Some packages will. All packages won't.

You seem to be assuming that Ubuntu Pro is smart enough to determine that you are running Kubuntu, and that Ubuntu Pro will tell you up front that it does not provide support for Kubuntu, and that if you don't get such a warning you must be fully supported. That's a chain of invalid assumptions.

Some Ubuntu-related packages , including some Universe packages,  will continue to receive updates -- they are still in 5-year LTS support. The Kubuntu desktop environment won't -- it is outside of 3-year LTS support.

You should migrate to a fully-supported release.

---

### Post by TheFu on 2023-01-19
Gotta love optimists.  
Sadly, I'm 100% certain that computers are pessimists.

---

### Post by mallt on 2023-01-19
This is the output from the "pro security-status" command on my kubuntu 18.04 machine:

2772 packages installed:
     1564 packages from Ubuntu Main/Restricted repository
     963 packages from Ubuntu Universe/Multiverse repository
     240 packages from third parties
     5 packages no longer available for download

If I understand correctly Ubuntu Pro covers both the Main/Restricted repositories and the Universe/Multiverse repositories, so apart from the 240 packages from third parties (and 5 no longer available) most of my installed packages would receive security updates through Ubuntu Pro until 2028. 

Since the kubuntu packages belong to the Universe/Multiverse repositories I thought these packages would also receive security updates until 2028. But so that is not the case then?

Thank you!

---

### Post by TheFu on 2023-01-19
Try:
$ ubuntu-support-status

What does that say?

---

### Post by mallt on 2023-01-19
[FONT=monospace][COLOR=#000000]This is the output of the ubuntu-support-status command:

You have 1562 packages (56.3%) supported until april 2023 (Canonical - 5y) [/COLOR]

You have 5 packages (0.2%) that can not/no-longer be downloaded 
You have 1205 packages (43.5%) that are unsupported


But so it seems that command doesn't take the extended Ubuntu Pro updates into account, to get info about that the "pro security-status" needs to be used. And with that command they mention security updates for Universe/Multiverse packages until 2028 (963 packages).
[/FONT]

---

