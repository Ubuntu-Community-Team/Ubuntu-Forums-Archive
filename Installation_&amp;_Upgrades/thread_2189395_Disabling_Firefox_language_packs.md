---
title: "Disabling Firefox language packs?"
date: 2013-11-22
forum: Installation &amp; Upgrades
---

### Post by bugbear6502 on 2013-11-22
My home laptop is quite old, and quite limited. I like running Firefox, which it can manage. I also
have a only moderately fast internet link, and capped bandwidth.

For all these reasons:

Is there anyway to configure Ubuntu/Firefox to NOT keep downloading, storing
and using the language packs other than my own language?

 I appreciate (from a philosophical point of view) that my Firefox would be
immediately usable in Swedish or Lithuanian etc, but (to be frank) from
my POV it's just a waste of (various) resources.

I once manually purged out the packs, but on the next Firefox
update they all got downloaded and installed again :-(

 BugBear

---

### Post by vasa1 on 2013-11-22
Could you please paste the output from:
```
dpkg --get-selections | grep "chrome" > ~/Desktop/temp.txt
```

---

### Post by bugbear6502 on 2013-11-25
> **vasa1 said:**
> Could you please paste the output from:
```
dpkg --get-selections | grep "chrome" > ~/Desktop/temp.txt
```

```
dpkg --get-selections | grep "chrome" 
xserver-xorg-video-openchrome                   install

```

 BugBear

---

### Post by vasa1 on 2013-11-25
@Bugbear, my apologies! I should have asked for **dpkg --get-selections | grep "firefox" ** and not **chrome**. The purpose is to get a list of firefox-related packages on your system. Sorry once again :(

---

