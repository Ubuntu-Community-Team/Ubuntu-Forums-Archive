---
title: "Managing Settings via the GUI fails"
date: 2022-04-20
forum: Installation &amp; Upgrades
---

### Post by securitydad on 2022-04-20
I am attempting to establish the screen sharing which is part of this link:

[https://linuxhint.com/enable-screen-sharing-ubuntu/](https://linuxhint.com/enable-screen-sharing-ubuntu/)

When I select the Settings->Sharing I am not able to move the slider switch.  If I click on the Sharing link to update the information under the Sharing menu I can modify the information on the pop-menu as well.  Yes, I see the pop-up Screen-Sharing has a slider at the top left, but that does not move either.

Additionally, I cannot disable the screen lock from (requiring a password) using the GUI as well.  I can handle the Command line, just don't know what is needed to perform this from the command line as well.

Thank you.

---

### Post by securitydad on 2022-04-20
This issue seems to come from the upgrade of 18.xx to 20.04 LTS.  The files in ~user/.config were owned by root, and not user.  changing ownership clear the issue.

---

