---
title: "Installed Ubuntu 21.04 Now I have problems with OBS."
date: 2021-07-09
forum: Installation &amp; Upgrades
---

### Post by irv on 2021-07-09
This problem started right after I upgraded to version 21.04. Maybe others are having the same problem.
I use OBS all the time for recording podcasts, but I can't capture my screens all I get is a black box.
Is there a way to fix this? Another problem I have found is the drag and drop in the Chrome Browser has an issue. Sometimes I need to do it half a dozen times before it will do the upload.
The two things I do the most I have problems with. Does this have anything to do with "Wayland?"

---

### Post by irv on 2021-07-09
I found a fix. OBS is supported by Xorg, not Wayland.
> An upgrade from 20.10 to 21.04 indeed automatically has you switch to Wayland. OBS Studio does not (yet) work in Wayland. To switch to X11, log out. Select your username so the password field appears. At that point, you will see a cog wheel in the bottom right of the login screen. It allows you to select "Ubuntu on Xorg". After that, enter your password to log in.



---

