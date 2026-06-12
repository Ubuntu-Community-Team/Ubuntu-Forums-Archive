---
title: "ubunut 12.04 works fine from live cd but doesn't after install to hard drive"
date: 2012-06-17
forum: Installation &amp; Upgrades
---

### Post by shwallace on 2012-06-17
I can run ubuntu 12.04 just fine from the live cd but when it's intalled to the hard drive it will only work with the ubuntu 2d login. When I do an lspci -k call from the live cd I seem to be using the nouvea kernal driver. I do the same from an installed version and for some reason I'm using the nvidia-current driver. Can anyone tell me how to fix this?

24 Jun12 A recent update that included a kernal update seems to have solved my issues.

---

### Post by mikewhatever on 2012-06-17
You can only be using nvidia-current because you have installed it. I am not quite sure what's the problem. It seems like the installation works as well according to what you've written above. What exactly do you want fixed?

---

### Post by shwallace on 2012-06-18
I would like to be able to run 12.04 in 3d mode like it does from the live cd. Apparently I need t uninstall the nividia-current driver but not sure how to do this.

---

