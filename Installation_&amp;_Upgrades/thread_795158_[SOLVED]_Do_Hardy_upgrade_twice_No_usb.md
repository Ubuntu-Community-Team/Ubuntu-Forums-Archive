---
title: "[SOLVED] Do Hardy upgrade twice? No usb"
date: 2008-05-15
forum: Installation &amp; Upgrades
---

### Post by dansan on 2008-05-15
Hi all,

I've searched some in the forums, but I haven't spotted my problem there, which is that I chose to keep my old rather accept the new usb configuration during the upgrade. I  misread the text and can now "repent at leisure". I have no way, for example, to use my usb mics or other usb peripherals.

I'm not sure afterward what the explanation during the upgrade said. Can I retrieve the  text from the upgrade installation for more careful reading? I've located a pile of stuff in /var/log about the upgrade but if someone knows where it actually is, I'd be grateful for the pointer.

Is there a simple solution? Is a second upgrade possible, so I could just say update instead of keep?



Thanks,
Daniel

The solution was discovering what the problem actually was. The more I checked things, the more obvious it was that I had usb functionality inside Hardy but not inside VirtualBox. That was a much thinner slice of salami ;-), and I found the answer [here]("http://www.ubuntu1501.com/2007/12/installing-virtualbox-with-usb-support.html").

---

### Post by dansan on 2008-05-16
Bump!

Still stuck. How can I resurrect usb?

Daniel

---

### Post by dstew on 2008-05-16
You can look at ```
cat /var/log/dist-upgrade.log | grep usb
```

---

### Post by dansan on 2008-05-16
Great! I'll check this evening.

Daniel

> **dstew said:**
> You can look at ```
cat /var/log/dist-upgrade.log | grep usb
```

---

