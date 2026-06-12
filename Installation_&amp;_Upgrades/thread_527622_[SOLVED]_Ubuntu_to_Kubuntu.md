---
title: "[SOLVED] Ubuntu to Kubuntu"
date: 2007-08-16
forum: Installation &amp; Upgrades
---

### Post by victor9098 on 2007-08-16
Hello All,

I have been using Ubuntu for a few months now but would like to give the Kubuntu flavour a try. I understand how to do it (use Synaptic to download the kubuntu-desktop) but I was wondering will I lose my current settings and/or information on my computer or should it all survive the upgrade? 

I use "Simple Backup" so if anything went wrong I should be able to recover my system. Any hints and tips would be very welcome!

Best regards...

---

### Post by merlinus on 2007-08-16
You will not lose settings, customizations and preferences as they are stored in /home/user, which both will share.

```

sudo aptitude update && sudo aptitude install kubuntu-desktop

```You can choose which one to use from Options at the login screen.

-merlin

---

### Post by victor9098 on 2007-08-16
That is great news! 

Thank you for putting me at ease, will give it a try.

---

