---
title: "Custom live CD: smart select proprietart restricted video driver"
date: 2007-07-02
forum: Installation &amp; Upgrades
---

### Post by mburris on 2007-07-02
Recently, I took on and conquored a project where I needed to build a LiveCD that had the Nvidia proprietary video driver installed and enabled automatically at boot.
[Read about it HERE]("http://ubuntuforums.org/showpost.php?p=2947662&postcount=4")

Now I was wondering... how about building a live CD that incorporates envy into the pre-boot process here is how the default ubuntu LiveCD works with regard to video detection:

isolinux -> initrd -> casper -> casper_bottom (scripts) -> 20xconfig -> auto dectec video and configure xorg.conf -> hand boot over to root inside rofs

Basically if we could run a script before 20xconfig that will detect what the video card is, then if the card is ATI or Nvidia, the 20Xconfig is bypassed and ENVY is called to auto config and install the video card and configure X.  if the card is not ATI or Nvidia, 20xconfig will do its job as normal.  

The problem we may run into is that using ENVY requires user interaction to agree to the nvidia user agreement... work arounds would have to be implemented.

Let me know what you think

---

