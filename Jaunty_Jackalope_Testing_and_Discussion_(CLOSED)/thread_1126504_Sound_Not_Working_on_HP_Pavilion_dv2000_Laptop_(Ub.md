---
title: "Sound Not Working on HP Pavilion dv2000 Laptop (Ubuntu 9.04)"
date: 2009-04-15
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by rcdegges on 2009-04-15
Hi all,

I just installed Ubuntu 9.04 on my HP Pavilion dv2000 laptop. The sound worked fine in 8.10, and on windows. When I do lspvi -vv | grep Audio I see:

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)

In my system->preferences->sound I have the device set to: HDA Intel (Alsa mixer), but when I run sound tests, or go to youtube to watch videos, I hear nothing.

Can anyone help me get sound working? Thanks a ton.

---

### Post by amano on 2009-04-15
Look at the pinned pulseaudio thread above in the channel. There are some experimental kernel .deb-files which might fix your problem (at least they should fix a lot of problems for Intel users). Report back, if the new kernel fixes your problem.

---

