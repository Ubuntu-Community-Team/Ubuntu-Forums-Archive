---
title: "Can't access USB mp3 player after hardy (8.04) upgrade"
date: 2008-05-02
forum: Installation &amp; Upgrades
---

### Post by dkarnows on 2008-05-02
Hi,

On previous releases when I plugged my MP3 player (Sandisk Sansa Clip) into a USB port I'd get a desktop icon appear for it, which I could open to navigate and transfer files (i.e. Nautilus). Since upgrading to Hardy (8.04) that has stopped working. I no longer get a desktop icon for the player when it is attached.

Either Hardy is not recognizing the attached device, or it's possible that they've just changed the functionality to no longer show a desktop icon. If the latter then how can I access the device? If the former then help.

cheers,
David

---

### Post by Holzster on 2008-05-08
same issue here - any fix?

---

### Post by diwolfio on 2008-05-09
I am having the exact same issue with my Sansa E250. Any help would be appreciated. Thanks.

---

### Post by dkarnows on 2008-05-20
Just some more info on my original problem I described above. It appears that if the mp3 player is plugged in before (or very early on) in the Ubuntu boot process I will be able to access it. The desktop icon for it appears in this case, as does the folder "/media/SANSA M350". The problem occurs when I plug in the mp3 player after the boot process is over. If I plug it in once I'm already logged into the desktop I will not get an icon appear, nor will the "/media/" sub-directory mount. On Gutsy (7.x) this worked fine. It broke after upgrading to Hardy (8.04). It also doesn't work on a fresh Xubuntu Hardy install.

---

### Post by dkarnows on 2008-06-17
For those of you that stumble upon this thread with the same problem: see [this thread]("http://ubuntuforums.org/showthread.php?t=782998") for a couple of workarounds. Once you've connected the Sansa Clip either:[LIST=1]
[*]Run [FONT="Courier New"][COLOR="Blue"]lsusb[/COLOR][/FONT] at a command prompt (worked for me) or
[*]Press the middle button of the Sansa Clip (didn't work for me, but seems to have worked for others)
[/LIST]

---

### Post by fueg0 on 2008-06-24
> **dkarnows said:**
> For those of you that stumble upon this thread with the same problem: see [this thread]("http://ubuntuforums.org/showthread.php?t=782998") for a couple of workarounds. Once you've connected the Sansa Clip either:[LIST=1]
[*]Run [FONT="Courier New"][COLOR="Blue"]lsusb[/COLOR][/FONT] at a command prompt (worked for me) or
[*]Press the middle button of the Sansa Clip (didn't work for me, but seems to have worked for others)
[/LIST]

I've had the same issue, and I managed to get everything to automount by installing the patch here: [http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/]("http://tombuntu.com/index.php/2008/05/09/stop-flash-from-locking-system-audio/")

something to do with libflash taking over my soundcard, and turns out it was also keeping me from mounting ANY usb-based device. I installed this 'patch' and now everything works... automount of my sansa Clip & sandisk usb memory keys.

hth
--fueg0

---

