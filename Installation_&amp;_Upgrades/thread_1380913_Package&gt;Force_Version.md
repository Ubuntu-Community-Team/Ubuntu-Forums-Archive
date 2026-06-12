---
title: "Package&gt;Force Version"
date: 2010-01-14
forum: Installation &amp; Upgrades
---

### Post by badaveil on 2010-01-14
Issue:
I wish to upgrade my Quantum GIS 1.3.0-1 to 1.4 where the Karmic version is already available for download at the QGIS website. I thought of using Force Version but upon checking the common tab of QGIS package via Synaptic, it mentions the installed version and the latest available version are the same. 

Question:
Is that why it is not possible to click "Force Version" (being unbold).

---

### Post by dstew on 2010-01-14
My understanding is that the "Force Vesion" parameter is usually used to **downgrade** software. That is, you have Karmic, but you for some reason want to use a Jaunty driver or program. In that case, you have to use "Force Version". But, if you are installing the latest version, you won't need to use that parameter.

If there is an updated or more recent version that is not available in Synaptic, you may be able to install it, either by compiling from source, or by using **dpkg** if there is a Debian package available from the software developer. Sometimes Synaptic will not have the very latest version of a software package, because it has to be packaged and tested by someone in the development arm of Ubuntu, and that takes time.

---

### Post by badaveil on 2010-01-14
> **dstew said:**
> My understanding is that the "Force Vesion" parameter is usually used to **downgrade** software. That is, you have Karmic, but you for some reason want to use a Jaunty driver or program. In that case, you have to use "Force Version". But, if you are installing the latest version, you won't need to use that parameter.

If there is an updated or more recent version that is not available in Synaptic, you may be able to install it, either by compiling from source, or by using **dpkg** if there is a Debian package available from the software developer. Sometimes Synaptic will not have the very latest version of a software package, because it has to be packaged and tested by someone in the development arm of Ubuntu, and that takes time.

OIC, Thanks very much.

---

