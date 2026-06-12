---
title: "Acess prompt before x loads"
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by TheBigBentley on 2007-10-25
Okay total newb question here Ive installed ubuntu using wubi quite a few times now because whenever I screw something up I cant fix it because I cant get to a terminal prompt before x loads. My problem is that twice now ive tried to either update the ati drivers or use the fxgl drivers in an attempt to install beryl.  After making some changes to my xorg file it boots to ubuntu and show me a blank screen. I know its not locked because I can restart x with ctrl alt bksps and shut down safely with the power button. If I could get to a prompt to restore my original xorg.conf id be fine and would save me some time. Any help for the newb would be greatly appreciated. Thanks!

---

### Post by forestpixie on 2007-10-25
if you boot to recovery you should get a command prompt where you'll be able to move you xorg backup

don't forget case sensitivity - I did:)

---

### Post by jachymc on 2007-10-25
just like in any other unix: press ctrl+alt+f1

---

### Post by TheBigBentley on 2007-10-27
Thanks but I found the problem. Cause I had wubi installed I had to edit the config file in windows to allow more time to get to recovery mode.

---

