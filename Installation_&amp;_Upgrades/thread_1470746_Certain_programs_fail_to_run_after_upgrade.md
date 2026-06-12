---
title: "Certain programs fail to run after upgrade"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by Chris62 on 2010-05-03
Hi,

I have a laptop running Ubuntu 10.04 and also two dual boot desktop machines, both running Windows XP and Ubuntu. I have upgraded one of the desktops to Ubuntu 10.04 and since doing so Thunderbird will not run on the laptop or the desktop. On clicking the launcher there are signs of activity for a few seconds and then they stop and Thunderbird fails to open. Also there is no longer any sound on the desktop that I have upgraded. I am reluctant now to upgrade the remaining desktop in case I have the same problems

Can anyone suggest how to get Thunderbird running again, please. I have already spent a week unsuccessfully trying to get the sound working and have abandoned it, but I would like Thunderbird to start running again.

---

### Post by ncrowdy on 2010-05-04
Chris62,

I found this post, [http://www.rebelzero.com/fixes/thunderbird-3-0-4-fails-to-start-after-upgrade/264]("http://www.rebelzero.com/fixes/thunderbird-3-0-4-fails-to-start-after-upgrade/264"), helpful.

In addition to having a circular reference, I couldn´t find any of my old mail folders. After some poking about I found them in a sub-directory, something like ~/.thunderbird-2.0-replaced/.thunderbird-3.0 , I copied this to ~/ and renamed it to be ~./thunderbird .

Things seemed to be back to normal after that.

Hope this helps some.

---

