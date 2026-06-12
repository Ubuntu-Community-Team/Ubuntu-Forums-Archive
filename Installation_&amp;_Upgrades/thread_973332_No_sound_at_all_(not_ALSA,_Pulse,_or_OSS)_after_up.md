---
title: "No sound at all (not ALSA, Pulse, or OSS) after upgrade"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by Poilar on 2008-11-06
When I first upgraded I seemed to be having the same pulseaudio issues that many people had. As with everyone, my OSS still worked, however, so I could hear systems sounds and play music if I used OSS. I followed psyke83's directions ([http://ubuntuforums.org/showthread.php?t=866965&highlight=pulseaudio+intrepid](http://ubuntuforums.org/showthread.php?t=866965&highlight=pulseaudio+intrepid)) to get pulseaudio to work and that seemed to fix things somewhat at least. I still was having trouble getting sound in flash to work. I tried to killall pulseaudio and then force-reload alsa and that made the sound in flash work. However, after I restarted my computer I no longer had any sound working. OSS doesn't even work anymore, and killall/force-reload doesn't do anything either. 

Help!

Note: When I type "ossplay" on the command line I see "ossplay: command not found" Is this normal?

---

