---
title: "No Signal to monitor problem with ATI cards"
date: 2007-12-08
forum: Installation &amp; Upgrades
---

### Post by tantryl on 2007-12-08
Just thought I'd share a little experience I had today with Mythbuntu 7.10.

While booting to the Live CD in preparation for installation the regular boot options come up - Regular, Safe Video, CD check, Memtest etc. Any choice other than Memtest or boot to HDD goes to a loading bar that is there and gone within a few seconds and then you get "No Signal" on the monitor. PC is still on, but CD has stopped spinning pretty much straight away. Only way out of it is to reset or turn it off.

First I tried a different monitor that could handle up to 1920x1200, no help. I hit F4 to manually set 1280x1024, nothing doing. Changed the CD drive and re-burned the CD in case it was a read/media error, no help. Swapped the graphics card from an ATI X1950GT to a nVidia 7300GT... loaded normally.

The interesting thing was that when you hit F4 on the ATI card it gave you every video option possible, including those the monitor wasn't able to display (on the 17" 4:3 it gave up to 1920x1200 options). When I switched over to the 7300GT it clearly detected the monitor and limited the resolution options to max 1280x1024.

So it would appear there's a problem with some ATI cards and detecting the monitor properly, likely defaulting to an absurd refresh rate or possibly resolution when it happens. I've searched around the forum and there's a fair few people who've described this problem but not found a solution to it. I'm installing now and hoping I'll just be able to switch over the graphics cards once it's on the HDD. Fingers crossed.

---

