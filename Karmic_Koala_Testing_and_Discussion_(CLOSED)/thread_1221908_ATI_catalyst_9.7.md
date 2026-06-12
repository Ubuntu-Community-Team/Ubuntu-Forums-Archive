---
title: "ATI catalyst 9.7"
date: 2009-07-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by waspbr on 2009-07-24
Well, 9.7 is finally available. I have just installed it on a machine running a radeon HD 3300 AGP.

for some reason karmic would not resume rebooting, the GDP progress bar would load completely but then fall into the console mode and get stuck in the boot sequence. 

Guess I am gonna have to stay tunned for the next edition.

Aside from that, the machine seems to boot well on jaunty with the drivers, tho I cannot enable compiz yet, video playback performance has not shown any issue, which is good in the sense that some progress has been made.

HAs anyone been able to get the drivers to work?

---

### Post by markbuntu on 2009-07-24
According to Phoronix support for the 2.6.30 kernel will not be available until the 9.8 driver.

---

### Post by waspbr on 2009-07-26
*shakes fist*

Damn you ATI

*sigh* another month of wait

---

### Post by dgf on 2009-07-26
> **markbuntu said:**
> According to Phoronix support for the 2.6.30 kernel will not be available until the 9.8 driver.

But why am I then running fglrx 9.6 with kernel 2.6.30 in Debian Sid? I know that 2.6.30 is officially not supported by ati, but somehow it does work.

---

### Post by rbmorse on 2009-07-29
Because somebody at Debian fixed the install script so FGLRX would install. 

The devs here could do it, too, if they wanted, but I really don't blame them for not pursuing it.  FGLRX works fine on 9.04 (at least on my machine). If you really need what FGLRX brings to the table, it's probably best to stay Jaunty.

---

### Post by dgf on 2009-07-31
Oh you misunderstand. I use Debian Sid on my desktop, and Ubuntu Karmic on my laptop which mainly has Intel-hardware. I was just wondering what Debian did to make it work.

---

### Post by dinxter on 2009-08-01
[#394176]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394176") is the patch used to get fglrx running on 2.6.30, which is in karmic already. 2.6.31 requires [#394985]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/394985") which isnt in a karmic package yet. there still willl be many many
[fglrx:firegl_find_any_map] *ERROR* Invalid map handle!
errors, though apparently it still works ok. that error is a binary driver issue and is the kernel support that ati need to add

---

