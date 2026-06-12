---
title: "Lost sound after upgrade 10 mins ago."
date: 2011-08-11
forum: Installation &amp; Upgrades
---

### Post by brawd on 2011-08-11
Hi All,

I've just done an upgrade after noticing the Update manager thingee at the bottom of the screen. I was listening to my music when I noticed it.

I did the Restart now after upgrading.

Now I have no sound at all.
Checked headphones were turned up which they were.
Checked sound settings and found there were no Devices in Hardware and Input and a Dummy Output (stereo) listed in Output.
I would have thought that my onboard sound would have shown up as well as the sound bits on my HDMI card - not that I've ever managed to get sound out of my telly via the HDMI cable. (I do have Alsa sound installed).

Any suggestions gratefully recieved.

regards,

brawd

---

### Post by brawd on 2011-08-11
Sorted this by going to google which brought me back to this forum and a 'Solved' note.
I haven't a clue how to point to that solution but if you type into google 'Lost sound card in ubuntu 10.04' it should come up.

regards

brawd.

---

### Post by ~!geek!~ on 2011-08-11
Upgrade usually makes me think of upgrade from an older version to newer version of ubuntu. If this is the case, you could have mentioned the older version you upgraded from and the newer version you upgraded to (although obviously, updatemanager would upgrade you to 11.04 version).
If this is not the case and you just updated the system with minor updates possibly including a kernel update, you could boot with an older kernel listed in grub menu shown at the beginning after powering up the system. and trying to remove this kernel update and reinstalling it. I know a guy who faced this sound problem and  solved it this way. I m not sure if it will help you though.

Temporary solution in case you upgraded from one version to another: Selecting older kernel thing may work in this case also, but I m not sure if you could reinstall the kernel after purging it in this case.

---

### Post by ~!geek!~ on 2011-08-11
> **brawd said:**
> Sorted this by going to google which brought me back to this forum and a 'Solved' note.
I haven't a clue how to point to that solution but if you type into google 'Lost sound card in ubuntu 10.04' it should come up.

regards

brawd.

Great to know that you got your problem solved. You may avoid previous post of mine. Anyways, it would have been great if you could  post specific link to solution page.

---

