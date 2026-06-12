---
title: "Transmission upgrade for Ubuntu?"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by asharpham on 2010-07-14
Can anyone tell me if Transmission 2.01 is available for Ubuntu 9.10? If so, where is it? I've checked the Transmission web site (also checked in Synaptic) and both places tell me the latest version is 1.75 even though the website has 2.01 plastered all over it.

Also, is there the ability to set daily start and finish times for downloading? This is imoportant for those on split download limits where you only want to download overnight. I can't find any reference to this in Help files or FAQs.

---

### Post by HenneBaby02 on 2010-07-14
> **asharpham said:**
> Can anyone tell me if Transmission 2.01 is available for Ubuntu 9.10? If so, where is it? I've checked the Transmission web site (also checked in Synaptic) and both places tell me the latest version is 1.75 even though the website has 2.01 plastered all over it.

Also, is there the ability to set daily start and finish times for downloading? This is imoportant for those on split download limits where you only want to download overnight. I can't find any reference to this in Help files or FAQs.


I don't use transmission, if a 2.01 is available but yours is sayin the latest version is 1.75. Did you check to see if 2.01 is available for windows only ?

EDIT: scratch what i said...

heres a link download the deb/ubuntu one [http://linux.softpedia.com/progDownload/Transmission-Download-4856.html](http://linux.softpedia.com/progDownload/Transmission-Download-4856.html)

after clicking the deb/ubuntu one (even tho it says 0kb click anyway, it`ll bring you to a PPA section, i haven't tried it though thats a trusted site) hopefully it`ll help.. If not go with Vuze or Deluge

---

### Post by mikewhatever on 2010-07-14
Add the ppa:
```
sudo add-apt-repository ppa:transmissionbt/ppa
```

I'd remove transmission related packages installed from the repositories first, then install 'transmission-common' and 'transmission-gtk'.
As for daily start and finish times, check out 'Temporary Speed Limits' under Preferences.

---

### Post by asharpham on 2010-07-16
Thanks guys. You both helped me update to version 2.01. Isn't it a pity that it isn't obvious how to find the update.

---

