---
title: "Software installer shows no Install button when old version already installed"
date: 2022-10-29
forum: Installation &amp; Upgrades
---

### Post by dagabrahamsson on 2022-10-29
When trying to install Google Chrome on Ubuntu 22.04, the GUI Software Installer showed no Install button when opening the downloaded .deb file, only the trashcan (Remove) button for the old version. The only thing shown was the old Chrome version 105.0.5195.102-1 which Chrome failed to update itself and therefore asked me to do a fresh install. Install of new latest version of Chrome 107.0.5304.87-1 was successful using "sudo dpkg" in terminal mode. According to the manual update instructions for Chrome, it should have worked to download latest .deb file and install it using GUI without first removing the old version, but this seems not possible. If this is the actual expected behaviour of the Software Installer to not allow install when an older version already exists I think it is confusing, at least for newbies to Ubuntu like me.

---

### Post by deadflowr on 2022-10-29
Open Software Updater and update chrome from there.
Chrome does not self update on linux.
Updates come through Ubuntu's updater mechanism.

---

### Post by dagabrahamsson on 2022-10-29
OK, I will try run Software Updater manually if Chrome again says it's version is outdated. I am regularily accepting Software Updater's requests to update. But I still find the behavior of the Software Installer strange

---

### Post by deadflowr on 2022-10-29
> But I still find the behavior of the Software Installer strange
Not really.
Why would it install something that is already installed.

> OK, I will try run Software Updater manually if Chrome again says it's version is outdated. 
I am regularily accepting Software Updater's requests to update.
Chrome automatically adds it's update information to Ubuntu so it should update without having to resort to reinstalling it.
If it's not updating correctly check if the information is disabled in the program Software and Updates >> Other Software section.
There should be an entry for something like dl.google.com/linux/chrome/deb, make sure it's checked.

---

### Post by dagabrahamsson on 2022-10-30
> **deadflowr said:**
> Not really.
Why would it install something that is already installed.


I find this perfectly understandable in my case. The downloaded .deb file contains a newer version than the already installed one, I would expect an option to "upgrade". Google Chrome explicitly told me that automatic updates (through Software Updater) failed and that I am running a too old version, and asked me to update the installation giving instructions to download the installation package and double click it. If I remember correctly I didn't even see any information about the new version, just about the old outdated version already installed when opening the new package. This is not logical to me

---

### Post by grahammechanical on 2022-10-30
Yesterday on my Ubuntu 20.04 Software Updater upgraded Chrome to 107.0.5304.87. I suggest that there is something we are forgetting. To install Chrome we first download a Chrome installer program. It must be that program that is insisting on removing the existing version of Chrome. Perhaps we first remove the existing version of Chrome and then run the Chrome installer again. Or we wait until Ubuntu Software upgrades Chrome which is what it should do.

[https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu](https://www.omgubuntu.co.uk/how-to-install-google-chrome-on-ubuntu)

Regards

---

