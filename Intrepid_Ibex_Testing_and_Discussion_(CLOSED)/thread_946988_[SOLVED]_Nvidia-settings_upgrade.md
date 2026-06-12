---
title: "[SOLVED] Nvidia-settings upgrade"
date: 2008-10-13
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by lvlo on 2008-10-13
Should I upgrade nvidia-settings package from 173.14.09 to 177.78 version if I use nvidia-glx-173 drivers?

---

### Post by Kow on 2008-10-14
> **lvlo said:**
> Should I upgrade nvidia-settings package from 173.14.09 to 177.78 version if I use nvidia-glx-173 drivers?

First of all use jockey for the upgrade (if you do it): System->Administration->Hardware Drivers. I would recommend trying the new version and if everything is fine then keep it. Otherwise you can revert to 173. Many hardware manufacturers suggest only upgrading the driver if you are experiencing problems. Personally, I don't obey that suggestion too often except in the case of performance issues.

**EDIT**: Jockey recommends a version for you. Try that one first.

**EDIT 2**: Misinterpreted initial post... I fail.

---

### Post by cmccauley on 2008-10-14
You mean should you mix versions of related packages? No I wouldn't do that. If the original supplier says that package A and package B should be at the same rev level then just accept that.

On a related note, Version 177 of the nvidia driver doesn't work well for me - partial screen updates, cursor problems etc. The 173 driver is not quite so bad but still pretty poor. I have an 8600M GT in a Dell Inspiron 1720.

Chris

---

### Post by lvlo on 2008-10-14
> **cmccauley said:**
> You mean should you mix versions of related packages? No I wouldn't do that. If the original supplier says that package A and package B should be at the same rev level then just accept that.

On a related note, Version 177 of the nvidia driver doesn't work well for me - partial screen updates, cursor problems etc. The 173 driver is not quite so bad but still pretty poor. I have an 8600M GT in a Dell Inspiron 1720.

Chris

Thank Chris for your reply. 

Then I have a question to developers: why if I use Nvidia drivers version 173, Update manager shows me **a distribution update** of nvidia-settings package from version 173 to 177?

Should I file a bug report in this case?

To **Kow**: no problem - it happens sometimes :)

---

### Post by plun on 2008-10-14
I think its the same, Ubuntus version is also a patched one

[http://packages.ubuntu.com/intrepid/nvidia-settings](http://packages.ubuntu.com/intrepid/nvidia-settings)

Install it and test.

Direct URL to bug reports within above URL (right menu -top)

-------------------------

@ Chris

Please check with Dells support about **BIOS updates**

[http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx](http://direct2dell.com/one2one/archive/2008/09/12/nvidia-gpu-update-limited-warranty-enhancement-details.aspx)

You are running a 1720 but check it !

---

### Post by lvlo on 2008-10-14
> **plun said:**
> I think its the same, Ubuntus version is also a patched one

[http://packages.ubuntu.com/intrepid/nvidia-settings](http://packages.ubuntu.com/intrepid/nvidia-settings)

Install it and test.

Direct URL to bug reports within above URL (right menu -top)

Thanks, plun. I've installed an update and it works fine. I was 	
muzzy because version of package.

---

### Post by master5o1 on 2008-10-14
i would suggest against the upgrade unless it is suggested to do so by synaptic


hmeh

---

### Post by plun on 2008-10-14
> **lvlo said:**
> Thanks, plun. I've installed an update and it works fine. I was muzzy because version of package.

Yup, I also noticed that and you can see within the change log that
its a patched version

[http://changelogs.ubuntu.com/changelogs/pool/universe/n/nvidia-settings/nvidia-settings_177.78-0ubuntu2/changelog](http://changelogs.ubuntu.com/changelogs/pool/universe/n/nvidia-settings/nvidia-settings_177.78-0ubuntu2/changelog)

(Change log can also be reached from repo description)

---

