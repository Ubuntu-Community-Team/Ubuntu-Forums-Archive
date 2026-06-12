---
title: "Install libhamlib2 1.2.15"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by Goldpin on 2012-05-28
I'm using the Oneric 64bit version and I've installed CQR Log 1.3.0.  I want to upgrade to CQR Log 1.3.1, but gdebi says I need libhamlib2 => 1.2.15.  The version currently installed is 1.2.14 (or so).

How do I download and install libhamlib2 1.2.15.  I know there is a version for Precise, but don't know if it will work in Oneric.  I've also tried installing CQR Log 1.4, but there is some bug to do with scrolling in the preferences.

Has anyone any advice?  Thanks in advance.

---

### Post by dino99 on 2012-05-28
you can download it from:

[https://launchpad.net/ubuntu/+source/hamlib](https://launchpad.net/ubuntu/+source/hamlib)

put it inside an empty folder, then from there install it with:

sudo dpkg -i *

---

### Post by critin on 2012-05-28
> **Goldpin said:**
> I'm using the Oneric 64bit version and I've installed CQR Log 1.3.0.  I want to upgrad to CQR Log 1.3.1, but gdebi says I need libhamlib2 => 1.2.15.  The version currently installed is 1.2.14 (or so).

How do I download and install libhamlib2 1.2.15.  I know there is a version for Precise,[COLOR=Red]** but don't know if it will work in Oneric.**[/COLOR]  I've also tried installing CQR Log 1.4, but there is some bug to do with scrollin in the preferences.

Has anyone any advice?  Thanks in advance.

I suggest asking here as it says .14. is supported in Oneiric and .15. is supported in Precise.

[https://answers.launchpad.net/ubuntu/+source/hamlib](https://answers.launchpad.net/ubuntu/+source/hamlib)

---

