---
title: "Upgrade to 11.04 freezes on boot"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by jeisma on 2011-04-30
hi!

i saw a couple of threads about upgrade problems. but none i found that is similar to my issue.

i upgraded from 10.10. after all the upgrades/updates and went to reboot. the system would freeze when starting the services, i would turn it off and on again. the freeze is random. i.e. starting apache2 [ok]..then later..checking battery state..then later..starting nfs [ok]...

i went to recovery mode and removed some of the services. but it still wont work.

any ideas how to go fix this?


thx!

joey

---

### Post by protoiyer on 2011-05-01
I am also facing the same issue. I too upgraded from 10.10 two days back. The system now starts (when I switch ON), displays Sony Vaio start screen, and then most of the time would just display either a violet screen of death or just a blinking horizontal prompt. I have to turn the box off and start again, and if I am lucky, I would get the option to select the Ubuntu version**.

Just once, it didn't ask me anything and gracefully logged me in (which is how 10.10 worked _always_!

I tried the recovery option, and believe it or not, that too *hanged* after displaying a line about "fixing recursive boot issue, but requires a reboot!" [or something similar -- short line -- about recursive issue and needing reboot].

I am a bit worried about whether my decision to switch from 10.10 was a tad stupid or not. I hope it is a bug and would be fixed soon. Any help would be appreciated. Thanks!

Details of my box: Sony Vaio CS series [VGN-CS15GN/B] laptop with Intel Centrino 2 with 2GB RAM. I don't have any OS other than Ubuntu 11.04 installed.

---

### Post by multisystem on 2011-05-01
Exactly the same problem, except that this is happening while booting from live cd.

---

### Post by protoiyer on 2011-05-01
It would be great if someone can point out any other sources where we are supposed to raise this or look for answers. Thanks. It repeats every time I try to boot the system -- a violet screen of death, I kill and try recovery next, I kill and get normal boot! I am worried I would end up corrupting my hard disk by all these forced kills.

---

### Post by benjamimgois on 2011-05-01
I have this problem on 11.04 too, on 10.10 it works OK. My laptop has 2 GPUs (I5 and Radeon 4550) i thought it might have something with it. I tried to update to the latest 2.6.39rc5 kernel but the problem remains.

---

### Post by californium on 2011-05-01
Try initially disabling the network and wireless.



[http://ubuntuforums.org/showthread.php?p=10753620](http://ubuntuforums.org/showthread.php?p=10753620)

---

