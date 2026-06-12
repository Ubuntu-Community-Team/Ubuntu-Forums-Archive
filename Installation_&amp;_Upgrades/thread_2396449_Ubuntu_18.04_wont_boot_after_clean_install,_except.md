---
title: "Ubuntu 18.04 wont boot after clean install, except in recovery"
date: 2018-07-16
forum: Installation &amp; Upgrades
---

### Post by FLMKane on 2018-07-16
As stated in the title, I've performed a clean reinstall of Ubuntu 18.04 and the OS won't boot at all, EXCEPT when I go into the recovery menu, then select the 'resume normal boot' option. 

I go into grub, select the 'Ubuntu' option and then the screen just goes black and stays that way.

Obviously, Ubuntu is unusable in this state. For example, I'm stuck with very low screen resolution. 

I'd also like to be able to turn off the splash screen and any graphics prior to the login screen, just to be able see what's going wrong.

Thanks for any help y'all :)

---

### Post by mIk3_08 on 2018-07-16
For boot repair [Click Here]("https://help.ubuntu.com/community/Boot-Repair")

---

### Post by oldfred on 2018-07-16
Post report from Boot-Repair as posted above by mlk3_08.

What brand & model system? Some need boot parameters.
What video card/chip? Some need drivers.
If nVidia have you installed proprietary nVidia driver from Ubuntu repository?

---

### Post by mIk3_08 on 2018-07-16
Thanks oldfred...

---

### Post by FLMKane on 2018-07-17
Thank you oldfred

Installing proprietary Nvidia drivers solved my problem.

---

### Post by oldfred on 2018-07-17
Glad it worked.

Low screen resolution was a clue.

---

