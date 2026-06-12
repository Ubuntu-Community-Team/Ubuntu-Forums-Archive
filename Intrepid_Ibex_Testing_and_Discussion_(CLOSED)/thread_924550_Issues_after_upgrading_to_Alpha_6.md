---
title: "Issues after upgrading to Alpha 6"
date: 2008-09-19
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Keithamus on 2008-09-19
Just updated to Alpha 6 from Hardy:

[LIST=1]
[*]The Synaptics touchpad "tap" sensitivity seems to be different to Hardy, I'm very used to Hardy's settings (have duplicated them in my Xorg) and this feels very different, and I can't seem to click easily
[*]I also have Synaptics TapButton2 = 2, so that when I tap my pad with two fingers, it middle clicks. This used to work 10/10 times, it now works about 2/10 (May be the same issue as #1)
[*]Don't know if it is a "feature" or a bug, but the new Network-Manager won't remember any of my wep passwords.
[*]When shutting down, the counter doesn't seem to count down!
[*]Firefox seems more sluggish than in hardy, takes about half a second to open a new tab.
[*]Used to have fprint in the /etc/auth/common.d file, but the file has changed syntax, and I can't seem to get it back.
[/LIST]

These are the only issues I have to report, I don't want to submit bug reports, because I'm not sure they're bugs, but if anyone has any clues how to fix them then I can't see any more problems with Intrepid!

---

### Post by wgrant on 2008-09-19
> **Keithamus said:**
> Just updated to Alpha 6 from Hardy:

[LIST=1]
[*]The Synaptics touchpad "tap" sensitivity seems to be different to Hardy, I'm very used to Hardy's settings (have duplicated them in my Xorg) and this feels very different, and I can't seem to click easily
[*]I also have Synaptics TapButton2 = 2, so that when I tap my pad with two fingers, it middle clicks. This used to work 10/10 times, it now works about 2/10 (May be the same issue as #1)
[*]Don't know if it is a "feature" or a bug, but the new Network-Manager won't remember any of my wep passwords.
[*]When shutting down, the counter doesn't seem to count down!
[*]Firefox seems more sluggish than in hardy, takes about half a second to open a new tab.
[*]Used to have fprint in the /etc/auth/common.d file, but the file has changed syntax, and I can't seem to get it back.
[/LIST]

These are the only issues I have to report, I don't want to submit bug reports, because I'm not sure they're bugs, but if anyone has any clues how to fix them then I can't see any more problems with Intrepid!

[LIST=1]
[*] Try my instructions at [https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/270002/comments/1](https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-input-synaptics/+bug/270002/comments/1). You'll probably need the new version of the package, and might need to run the xinput command if it still isn't perfect. Comment on the bug with your results.
[*] See 1.
[*] No idea, but it sounds like a bug. File it.
[*] It counts down in 10 second increments.
[/LIST]

---

### Post by Wise Ferret on 2008-09-19
I am experiencing same issues, including the wep password amnesia, on lg s1 laptop, 32-bit intrepid. I have also lost lately my multimedia keys, and cannot change the volume using them.

---

### Post by Keithamus on 2008-09-20
Installing the deb fixed the mouse problems right away. :KS

Unfortunately, I can't seem to resolve the problem with nm-applet's amnesia. I tried deleting all the network settings from gconf, hoping it was some issue with the old settings files. Didn't work though, it still forgets (luckily I don't so I can get my networks back!)

Think I've got a few bug reports to file now.

---

### Post by analystscouch on 2008-09-20
For the key amnesia see bugs:

[https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568](https://bugs.launchpad.net/ubuntu/+source/network-manager-applet/+bug/206568)

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/265127)

---

