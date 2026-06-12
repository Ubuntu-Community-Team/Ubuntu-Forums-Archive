---
title: "Video Drive Installation Issues"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by JMorg on 2010-01-21
This may be a dumb question, however I recently installed Karmic Koala and am not able to successfully install my video Drivers. I am running on an Nvidia 8400M GS and I want the 3D support for CUBE and whatnot to run properly. Many tutorials state to enter what is known as "real terminal mode" by hitting control + alt + F1 but that never works for me. I've tried hitting it then logging out and back in, etc. 

When I perform the "sh Nvidia..." command it will go through and then state that X needs to be stopped.

Could my problem simply be fixed by understanding how to enter "real terminal mode"? I'm not sure, but any help would be greatly appreciated =). If it is necessary to know, I am running via a virtual machine.

Thanks in advance.

---

### Post by hemimaniac on 2010-01-21
I install the nvidia.run package by booting into recovery, selecting root shell and go through it that way.

i just ignore the error about x.org not running (9.04) and then resume normal boot, all sorted

---

### Post by JMorg on 2010-02-02
Hmm interesting, I honestly have not tried to continue passed the warning. Thinking on it though, what's the worst that could happen? Nothing crippling to this current system by any means. Thanks for the reply, I will try it out.

---

