---
title: "Hardy 32 or 64bit won't boot after install"
date: 2008-05-01
forum: Installation &amp; Upgrades
---

### Post by sojourner_tim on 2008-05-01
Hi guys, first post here.

Here is a little background. I previously had Gutsy installed with no problems at all. I then upgraded using the update manager to hardy. Everything seemed to go according to plan until it asked me to reboot. I got to the ubuntu loading screen but instead of the loading bar going from left to right and then starting up, it froze in what i saw someone call "knightrider mode" (the bar just kept going back and forth). when loading in recovery mode, it stopped with an error that said, "unable to read partition table" and "unable to read rdb block 0".

i then searched on the internet and could not find a solution so i tried a clean install with both the 32 and 64 bit live cds. Both installs resulted in the same error. i then tried installing again and doing manual partitioning. I believe there was an option to create a new partition table (or something like that) so i tried that too, still have the same error.

I am just installing on an old 80gb ide Western Digital I have. there is nothing else on it and i disconnected my other to drives so they could not interfere. The drive is the primary master then i have two cdroms that are secondary master/slave.

Any ideas? If you do i'm pretty much a noob to ubuntu, just so you know.

Thanks, Tim

---

### Post by Pumalite on 2008-05-01
Check the offending drive with TestDisk: [http://www.cgsecurity.org/wiki/TestDisk_Download](http://www.cgsecurity.org/wiki/TestDisk_Download)

---

### Post by sojourner_tim on 2008-05-01
sorry i'm new to this program as well. what should i be looking for? I did the analyze option, then quick search and the 3 partitions turned green and it said structure ok. i then did the deeper search and the first partition turned green and said ok. 

anything else?

---

### Post by Pumalite on 2008-05-01
Your drive is well then . Your net culprit is your burner. Cleans it's lens. Burn new CD. Follow this guide:
ç[https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28](https://help.ubuntu.com/community/BurningIsoHowto?highlight=%28burn%29%7C%28)
Do md5sum, burn at 4x or less in good quality CD-R media, check CD integrity before install.

---

### Post by sojourner_tim on 2008-05-01
thank you, trying all that now. let you know how it goes. thanks again.

---

### Post by sojourner_tim on 2008-05-01
Well in the process of doing this i restarted and realized that my hd was actually secondary master and my cdroms were primary master and slave. I switched that around and made the HD primary master and it started right up. I feel like a retard but thank you for responding to me.

Tim

---

### Post by Pumalite on 2008-05-01
You are welocome. Good luck.

---

