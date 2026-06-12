---
title: "install/demo bootup problem"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by chemicall on 2008-10-18
okay guys,

decomissioned my moms p3 733 last week, it was running fine but too slow for her nowadays.  So I took the old one, I plan to stick a 1000 chip in it.
i'm trying to get 8.04 going, on trial of install or the desktop demo etc I get this:

81.88976 ata 2.01 exception emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
81.890049 ata 2.01 cmd a0/01:00:00:80:00/00:00:00:00:00:00/bo tag0 dma 128 in
81.890102 ata 2.01 status {DRDY}

this happens with hard drives plugged in or not, tried diff drives on diff cables, and this was a functioning pc last week.

any thoughts? thanks all

---

### Post by cariboo on 2008-10-18
Did you perhaps do an unclean shutdown in windows?

Jim

---

### Post by chemicall on 2008-10-19
nope,

final shutdown from windows was proper, as the old harddrive  was also used in her new pc. (all her data etc)

i've tried 3 different hard drives. still getting the same thing. Same error without a hard drive. weird.

thanks again for the help

---

### Post by Bucky Ball on 2008-10-19
How much ram?

---

### Post by chemicall on 2008-10-19
its got 768 and im down to 256 right now just trying to get this baby going. Ran memtest86 on 512mb of it last nite and came out okay. motherboard has a via chipset.vid card is 128mb nvidia mx 4000.

Just tried a 4th HD i KNOW was working, same error, also says busybox and (initramfs) before all the errors I get(in first post)

also it's been doing this with the original and the 1000 cpu. no bad caps on motherboard, etc, the voltages are stable as could be. they DO NOT fluxuate 1 bit and are all good. thanks to that trusty old antec psu I had installed back when this system was new.

Also I should note the cas timings are all proper on my ram, not trying to run it faster than it should.

---

### Post by Bucky Ball on 2008-10-19
> **chemicall said:**
> its got 768 and im down to 256 right now

Try Xubuntu and see if you get the same issue. That RAM is not officially adequate to install Ubuntu desktop, if 256 is the ram at your disposal. Once you have Xubuntu up, you can install:

**ubuntu-desktop**

This is what I did on the admin machine with very similar specs to yours and VIA chipset also. I would advise the alternate iso and it sounds like you have got the defect checking under control. Best is a torrent from:

[http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/](http://torrent.ubuntu.com/xubuntu/releases/hardy/release/alternate/)

:)

---

### Post by chemicall on 2008-10-19
okay, but i do have 768 for this machine that belongs in it. That's not enough? But I can try xubuntu. it's probably gonna get server edition after work, see what happens there.

only reason I pulled the ram was to see if it got me any further. it didn't.

---

### Post by Bucky Ball on 2008-10-19
Got ya. Try the alternate iso for Ubuntu in that case, with all the RAM in, and see if it makes any difference. Good chance it won't but curious. Bottom of this page:

[http://releases.ubuntu.com/8.04/](http://releases.ubuntu.com/8.04/)

The similar machine I mentioned has 1Gb RAM and I ended up going that way around anyhow: Xubuntu alternate, ubuntu-desktop from Synaptics or 'apt-get install' in a terminal once I was up and running in Xubuntu.

---

### Post by chemicall on 2008-10-21
well now I have tried ubuntu, ubuntu alternate cd, xubuntu, ubuntu server, all giving me the exact same thing as on the first post.

freebsd installed fine, so it's not the system?

any more ideas? I have been running it again now with 768mb ram.

---

### Post by chemicall on 2008-10-22
bump - any help?

got the xubuntu alternate burnt now, I tried that, still the same error.

Also - it seems an old FC6 cd is booting up just fine to install.

But I want ubuntu.... :(

---

