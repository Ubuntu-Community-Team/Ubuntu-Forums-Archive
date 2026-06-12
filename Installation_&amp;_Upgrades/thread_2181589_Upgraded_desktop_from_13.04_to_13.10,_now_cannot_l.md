---
title: "Upgraded desktop from 13.04 to 13.10, now cannot login"
date: 2013-10-18
forum: Installation &amp; Upgrades
---

### Post by liquidcross on 2013-10-18
The upgrade went smoothly, but after it was completed and the PC restarted, there is nowhere for me to enter my username or password on the login screen. At first, it was just empty (save for the Ubuntu background and menubar items), but after a second reboot, all that's there is a box with the text "Remote Login," but nothing clickable and no text input fields. Any ideas?

---

### Post by evolutionv8-5 on 2013-10-18
> **liquidcross said:**
> The upgrade went smoothly, but after it was completed and the PC restarted, there is nowhere for me to enter my username or password on the login screen. At first, it was just empty (save for the Ubuntu background and menubar items), but after a second reboot, all that's there is a box with the text "Remote Login," but nothing clickable and no text input fields. Any ideas?
Try adding a new user via CTRL+ALT+F(1-6) and logging again. Then you could try readding your user / moving and chown'ing your home folder to the new one

---

### Post by liquidcross on 2013-10-18
Just tried that, still getting the same unusable login screen.

**UPDATE:**

Think I fixed the problem: I had lightdm.conf customized that the login screen would NOT show a list of users. Once I took that line out, the regular login screen came right back. Of course, now it's a list of users again, so I need to figure out a way to change that back to black input fields. Baby steps, I guess.

---

