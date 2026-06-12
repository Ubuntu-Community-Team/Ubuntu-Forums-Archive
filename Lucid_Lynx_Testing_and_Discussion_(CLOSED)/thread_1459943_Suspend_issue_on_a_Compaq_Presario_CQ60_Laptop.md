---
title: "Suspend issue on a Compaq Presario CQ60 Laptop"
date: 2010-04-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by James2k on 2010-04-22
Hey all,

Im currently running 10.04 BETA 2 and have noticed that suspend does behave well when I close my laptop lid. In Power management I've got it set so when laptop lid is closed go into suspend (On both power options), however when I close the laptop lid the laptop doesn't go into suspend instead it remains on but has my screensaver displayed when I open the lid. Whats strange is that suspend on close of the laptop lid sometimes works and sometimes it doesn't.

I've also noticed that when my laptop does come back from a suspended period (and hibernation) my display is dimmed as if it's running on Battery power when infact the AC adapter is connceted.

Suspend worked fine on 9.10 though my display dimming issue has been since 9.10.

Wondered if anyone else had experienced the above?

Thanks,

James

---

### Post by yellow5nake on 2010-04-26
Although I haven't tried on battery power, I am having the same issue on an Asus K50IE. If I close the lid the screen blanks and asks me for password when I open it again, even though I've set it to suspend. Also worked fine on 9.10.

Does CQ60 have an Nvidia GPU? I've noticed my lappys a little buggy with the propriety drivers enabled now ... occasionally X fails to start on boot and I have to manually restart it.

I'm no linux expert but seems kinda a coincidence to me.

---

### Post by James2k on 2010-04-26
> **yellow5nake said:**
> Although I haven't tried on battery power, I am having the same issue on an Asus K50IE. If I close the lid the screen blanks and asks me for password when I open it again, even though I've set it to suspend. Also worked fine on 9.10.

Does CQ60 have an Nvidia GPU? I've noticed my lappys a little buggy with the propriety drivers enabled now ... occasionally X fails to start on boot and I have to manually restart it.

I'm no linux expert but seems kinda a coincidence to me.

Yes I do have an nVidia GPU, it's rather hit and miss on if the laptop is to suspend or not when the laptop lid closes. I'll have to look out for the final release of 10.04 on Thursday to see if the problem is solved, if not I'll consider a bug report if I can't find a solution.

I do know the nVidia drivers have been changed in 10.04, so perhaps this could the starting point.

---

