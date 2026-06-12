---
title: "Preseeding with 12.10 with Desktop ISO extracted"
date: 2013-02-01
forum: Installation &amp; Upgrades
---

### Post by skmah on 2013-02-01
For the past 4 years or so, I've been deploying machines with the Alternate CD extracted on a local http server. It's been working great with a bit of customization in the preseed file.

For 12.10, there does not seem to be an Alternate or DVD ISO, so I downloaded the Desktop version and extracted that.
I cannot find the boot kernel "linux" or the initrd.gz. I see only vmlinuz, and initrd.lz. Probably for the live CD (Casper).

I found the files from the netboot install, but it's not liking the local mirror that I extracted from the Desktop ISO.

Is there's a way to script the install from the Desktop ISO extracted on a Web server. I've heard you can use some sort of Ubiquity installer and a D-I preseed file? How do I do this?

I suppose I can go do a netboot install from the public Ubuntu Mirrors. This might be faster since I'm assumming I will always get the latest updates, rather than a static scripted install from the Alternate ISO/ bootup and apt-get update.

---

### Post by skmah on 2013-02-06
Does anyone have experience with using the Ubuntu 12.10 Live CD for automated installs?

---

