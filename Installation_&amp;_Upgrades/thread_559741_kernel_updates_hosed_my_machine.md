---
title: "kernel updates hosed my machine?"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by Rotarychainsaw on 2007-09-25
SO I had some kernel updates in the update manager... THey didn't look like big upgrades or anything so I let it go. Now my computer wont boot.

I see a bunch of messages pop up before uspash comes up, and sometimes it makes it to GDM sometimes it doesn't. I was wondering if its just me experiencing this or if its something else.

---

### Post by reckless2k2 on 2007-09-25
hey jersey...burlington born and raised. 

are you able to get into a gui at all? if not you'll need to boot using the livecd or in recovery mode. we need some details about the messages. you can usually post dmesg from the cli and tell us waht's going on. if you boot livecd, you'll have to get it from /var/log/messages (i link it's messages) and tell us what's up. 

it's probably related to graphic driver. you could flip the xorg.conf driver back to vesa and you might be ok.

---

### Post by elsaturnino on 2007-09-25
Did you try booting into the previous kernel version?

---

### Post by Rotarychainsaw on 2007-09-25
yeah, previous kernel made it a little farther. That leads me to believe I might be having some hardware issues. Gonna mess with it now.

---

### Post by Rotarychainsaw on 2007-09-25
OK, I think it was hardware. I have a ide to sata converter that has to be sitting just right or else everything goes wonky. I thought it was the updates due to the timing. I'm checking the kernel log now and it says a lot of BUG: scheduling while atomic. Sounds cool haha.

---

### Post by Rotarychainsaw on 2007-09-25
```
Sep 25 16:44:28 localhost kernel: [ 1108.896000] BUG: scheduling while atomic: swapper/0xffff0000/0
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [schedule+1528/2704] __sched_text_start+0x5f8/0xa90
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [smp_reschedule_interrupt+13/16] smp_reschedule_interrupt+0xd/0x10
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [reschedule_interrupt+40/48] reschedule_interrupt+0x28/0x30
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [default_idle+0/96] default_idle+0x0/0x60
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [cpu_idle+141/208] cpu_idle+0x8d/0xd0
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [start_kernel+869/1056] start_kernel+0x365/0x420
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  [unknown_bootoption+0/608] unknown_bootoption+0x0/0x260
Sep 25 16:44:28 localhost kernel: [ 1108.896000]  =======================
```

I dunno, I'm still getting this with locks. Can that be because of the hard drive being disconnected unexpectedly? 

[http://kerneltrap.org/node/435](http://kerneltrap.org/node/435)

---

### Post by reckless2k2 on 2007-09-26
did you by chance have nvidia drivers?

---

