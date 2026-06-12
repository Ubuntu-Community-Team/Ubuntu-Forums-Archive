---
title: "Upgrading from 16.04 to 20.04 - &quot;inpur not supported&quot;"
date: 2021-03-14
forum: Installation &amp; Upgrades
---

### Post by jencdi on 2021-03-14
I am upgrading from 16.04 to 20.04 and after the file check section, a blue box pops up with the message that reads "input not supported"

Went back and reinstalled 16.04 and all works fine. Tried the reinstall of 20.04 and the same message appears.

Any thoughts?

---

### Post by CelticWarrior on 2021-03-14
Welcome.

Please post the hardware specifications.

---

### Post by jencdi on 2021-03-14
ASUS - M4A79XTD EVO
AMD - Phenom II x6 1090T 3.2 ghz
memory 16 gb
GeForce gt 240 video card
1 tb hardrive

---

### Post by CelticWarrior on 2021-03-14
The Nvidia GT240 graphics needs Nvidia 340.xx drivers. This is the oldest long term support Nvidia drivers branch still supported.
Maker sure to select the option to install third-party drivers, firmware, codecs, etc. when installing Ubuntu.

PS - Consider upgrading the graphics card. We don't know for how long it'll be supported.

---

### Post by jencdi on 2021-03-14
I never reach the prompt to install third party vendors so should I go ahead and replace the video card now?

---

### Post by CelticWarrior on 2021-03-14
You may use 'nomodeset' as a temporary workaround.
A the Grub menu select "Try Ubuntu", press "e" to edit and add "nomodeset" after "quiet splash".

---

### Post by jencdi on 2021-03-14
I never make it to the Grub menu

---

### Post by jencdi on 2021-03-14
Is there a supported video card page available somewhere?

---

### Post by CelticWarrior on 2021-03-14
All are supported. Any just a couple of years newer than the one you currently have can run with newer drivers.

---

### Post by grahammechanical on 2021-03-14
It is not possible to upgrade 16.04 to 20.04. How are you trying to do that? First upgrade 16.04 to 18.04 and then upgrade 18.04 to 20.04. We can go from one LTS release to the next one but we cannot jump a release. Unless we do a fresh install.

Ubuntu 16.04 is in standard support until April 2021. So, try opening Software & Updates>Updates tab and change the setting for Notify me of a new Ubuntu version to Long-term support versions. Close the utility and run Software Updater and see if you get an offer to upgrade to 18.04.

Regards

---

### Post by jencdi on 2021-03-14
I'm planning on doing a complete new install with 20.04 but cannot get past the "input not supported" message

---

### Post by TheFu on 2021-03-14
I updated about 5 systems from 16.04 to 18.04 the last few months.  I remember a light-desktop version getting into trouble where the mouse and keyboard didn't work after boot.  It appears the input library got left and the newer version wasn't installed.  I ended up going to a different system and logging in over ssh to the new 18.04 setup and installing some input libraries.  I don't recall what they were and it only became an issue after I started cleaning up old 16.04 libraries which were left behind.

Sorry. Let me search a bit.  My notes don't say what I did, sorry.  I found the answer the first time around by pasting the exact error into google, which took me to an AskUbuntu page and the last answer provided worked for my situation.  I don't think your situation is the same as mine other than "input" being in the error, so most of this post probably isn't useful.

I'll be waiting another year, at least, before 20.04.  New isn't always better.

---

