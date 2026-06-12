---
title: "Gutsy 7.10 Live CD Problem"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by zakaroo on 2008-01-04
Hi Everyone - I have 7.10 running on my Sony Vaio and I love it!!!  So, I was bragging at work about it.  One of my Co-workers said that he'd like to try it.  So, I gave him a copy of the LiveCD.  He puts it in his computer, it boots to the XFCE screen without a taskbar or panel, just the icons along the left hand side.  I didn't believe him when he told me, so I had him bring in the laptop so that I could see.  Sure enough, he's telling the truth.  I can pull up the terminal window and a whole host of apps, but can't get the taskbar and panel to show. I tried booting with different resolutions.  The liveCD works perfectly in my laptop.  There are a couple threads out there about this problem, deleting the desktop config folders in the home directory but since this is running off liveCD that option is not available.  His laptop is a Gateway Solo (kinda ancient)...any suggestions?  I bragged for weeks so don't let me be a liar!

---

### Post by njparton on 2008-01-04
Does he have onboard nvidia graphics?

If so install using the safe graphics option and hit F6 and remove quiet and splash from the command line.

---

### Post by LinuxGuy1234 on 2008-01-04
> **zakaroo said:**
> Hi Everyone - I have 7.10 running on my Sony Vaio and I love it!!!  So, I was bragging at work about it.  One of my Co-workers said that he'd like to try it.  So, I gave him a copy of the LiveCD.  He puts it in his computer, it boots to the XFCE screen without a taskbar or panel, just the icons along the left hand side.  I didn't believe him when he told me, so I had him bring in the laptop so that I could see.  Sure enough, he's telling the truth.  I can pull up the terminal window and a whole host of apps, but can't get the taskbar and panel to show. I tried booting with different resolutions.  The liveCD works perfectly in my laptop.  There are a couple threads out there about this problem, deleting the desktop config folders in the home directory but since this is running off liveCD that option is not available.  His laptop is a Gateway Solo (kinda ancient)...any suggestions?  I bragged for weeks so don't let me be a liar!

OK, (before he switches back to Windows or Mac) go to the Terminal and type in top. Do you see that all Xfce processes are running? If the panel and taskbar is missing type in the terminal:
```
xfce4-panel
```
and you will be alright.

---

### Post by zakaroo on 2008-01-04
Thanks so much - the xcfe4-panel command worked.  The removing quiet no splash showed the task bar momentarily then disappeared again.  

Thanks Again....

---

