---
title: "Annoying Trolls in Lucid"
date: 2010-10-14
forum: Installation &amp; Upgrades
---

### Post by ausmuso on 2010-10-14
I recently upgraded one of my computers from Karmic to Lucid. On the whole the upgrade worked quite well but except for two annoying little trolls. I've kludged my way around one of them but the other one mystifies me.

1. Something is wrong with the automatic speed setting of my wireless LAN
chip Ralink RT2561. Somehow the speed setting dialogue doesn't work and the connection defaults to the lowest possible speed of 1Mb/s.
This is a problem I have never had with the RT2561. It used to be a common
problem with the RT2500. Fortunately it is easy enough to fix by including an extra line in one of the boot scripts to force the connection to a higher speed. This shouldn't be necessary, though.

2. I like my clocks to be synchronised so I always use NTP as a matter of course. NTP has always worked perfectly for me up to and including Karmic. With Lucid, however, NTP suddenly didn't work anymore. Signals from the NTP servers arrive as before and they seem to be digested normally. However, the clock is not actually corrected and you can watch the divergence grow over time.
The troubleshooting pages on [www.ntp.org](www.ntp.org) list a bewildering number of possible causes, both on the hardware and OS/kernel side. However, what bugs me is that I didn't have this problem with karmic.
	Has anybody else come across this problem in Lucid and found a workaround?

---

