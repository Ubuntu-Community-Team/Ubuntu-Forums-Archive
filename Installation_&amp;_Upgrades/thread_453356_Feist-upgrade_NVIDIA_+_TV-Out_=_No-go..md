---
title: "Feist-upgrade: NVIDIA + TV-Out = No-go."
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by 8086 on 2007-05-24
Today I upgraded 6.10 to 7.04. This broke my Nvidia-setup as well as several other packages. 

The problems I am facing are described in this post (my post): [http://ubuntuforums.org/showpost.php?p=2711989&postcount=373](http://ubuntuforums.org/showpost.php?p=2711989&postcount=373)

I run my system with the TV as the *only* visual output device. That means no LCD to fix things. And as far as I can tell, the "nv" driver doesn't drive the TV-OUT for my Geforce 440MX.

As described in the post above, the syntax seems to have changed (or the meaning of the Options) for the xorg.conf file in the Device Section. After fixing the error messages that come up with feisty, it simply says it can't find the module. Hurray. And the nvidia-glx package (+the kernel-common binary, and third party package) is installed. Any clues?

---

