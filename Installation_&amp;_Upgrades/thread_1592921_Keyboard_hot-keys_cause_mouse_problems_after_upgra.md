---
title: "Keyboard hot-keys cause mouse problems after upgrade (10.04-&gt;10.10)"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by Kraxuntu on 2010-10-11
I upgraded Ubuntu from 10.04 to 10.10 and noticed a problem with my keyboard's hot-keys. If I press any of the additional hot-keys on the keyboard the first button on my mouse becomes stuck. It is as though I constantly pressed it. Any other input methods become unusable, except the power button.

The keyboard is Microsoft Digital Media Keyboard Pro Keyboard. This problem manifests whether hot-keys keys are assigned or not. The problem didn't appear in 10.04.

I'm not Linux-literate enough to reliably find the relevant logs, but I noticed that Xorg.0.log contains parts that seem to deal with the keyboard.

Any help is appreciated. I can simply not use the hot-keys but being accustomed in using them, I often hit them by accident and have to boot simply to have my machine operational again.

EDIT: Problem solved. [http://ubuntuforums.org/showthread.php?t=1575239&page=3](http://ubuntuforums.org/showthread.php?t=1575239&page=3)

---

### Post by flyver on 2010-10-17
[This]("https://bugs.launchpad.net/udev/+bug/637208/comments/40") fixed the problem for me.

---

