---
title: "update on Ubuntu 13.04 crash."
date: 2013-08-28
forum: Installation &amp; Upgrades
---

### Post by Pengwyn44 on 2013-08-28
Today 28/08/13, I responded to an update for Ubuntu 13.04 by clicking on the update icon called Software Updater. The result was a long download followed by a long automatic configuration. After the requested re-boot my computer was unusable!
I have had to wipe the hard drive and re-install from a backup with the aid of Clonezilla. I will not be updating again until I hear that Canonical have resolved the error, or until someone can say what the problem is.
The original OS is the one supplied by Linux Format Magazine LXF172 called the "Raring Ringtail LXF Privacy Remix". Could this be the basis of the problem?

---

### Post by grahammechanical on 2013-08-28
You do not say in what way the computer was "unusable." Therefore we have no idea what happened and you will never know if and when the problem will happen again or what to do about it.

You have now reverted back to an earlier version of 13.04 installed on your machine. An update will certainly make the same changes as the last one did and with the same result.

Installable images of Ubuntu are out of date because they represent the state of Ubuntu when the image was made. So, it is common for an update to be necessary to bring in any security fixes since 13.04 was released back in May 2013. The update may also bring in a more up to date Linux kernel which may not work with the proprietary video driver being used.

Add to all this the specialised version of Ubuntu that you installed and it is possible that updated Ubuntu libraries caused conflict with any specialised libraries installed by that special version.

Who knows? In what way was the machine unusable? Without this information no one can suggest what to do to prevent it happening again or how to fix things if it does happen again.

Regards.

---

### Post by Pengwyn44 on 2013-08-29
Thanks for your comments. The machine was unusable because the images of the home files were floating around the screen. I have had problems with my graphics card before. It is a Radeon HD6450. When installing any Linux OS I have to change the script "quiet splash" to "nomodeset" before loading, otherwise I will only see flashing colours on the screen. After installation and the required re-start I repeat the process and then install the Radeon driver.
The kernel never supplies a workable driver for this card. So whether the upgrade causes this problem or the "remix" I am not skilled enough to know.

---

### Post by Pengwyn44 on 2013-08-30
Working on the possibility that the new kernel may have clashed with my graphics card driver, as suggested by "grahammechanical", I repeated the upgrade and re-started using "nomodeset".
Then I re-loaded the commercial driver, and on the next re-start all was well. Therefore the original problem was not with the LXF version.

---

