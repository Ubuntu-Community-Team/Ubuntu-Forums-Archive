---
title: "Weird GPG-error on fresh install"
date: 2005-05-07
forum: Installation &amp; Upgrades
---

### Post by kamstrup on 2005-05-07
When I update my repositories I get the following error:

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release: Unknown error executing gpgv
W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: Unknown error executing gpgv

This is on a fresh installation. I don't know if this matters but: I did not have any network during installation. I added a wireless network afterwards. It seems to work superbly in every respect but this :-S

Please help. This is on my mom-in-laws machine :-)

---

### Post by kamstrup on 2005-05-07
Hehe... That was a lesson learned =D

I found out that the iso I had burned was actually an old Array-SOMETHING snapshot (o_O). The valuable lesson was: "Don't let old development-isos lie around named hoary-install.iso"!

Cheers!

PS: Yes - this means that I have resolved my issue.

---

### Post by foustware on 2005-05-14
i actually just started getting the exact same error and it happens everytime i update my list from the repositories. i don't have any iso images laying around, at least i don't think. how do i fix this? will i have to reinstall apt and synaptic from the installation disk?

---

### Post by kamstrup on 2005-05-16
All I did was to update via Synaptic. Just clicked the Mark All Updates and selected "Smart Update". I needed to do this two times as I recall...

Good luck

---

