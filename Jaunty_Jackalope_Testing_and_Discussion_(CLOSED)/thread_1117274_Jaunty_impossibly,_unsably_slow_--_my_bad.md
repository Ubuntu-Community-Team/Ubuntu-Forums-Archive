---
title: "Jaunty impossibly, unsably slow -- my bad?"
date: 2009-04-05
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by pkirkaas on 2009-04-05
Hi,

I just installed my first Linux in 10 years, the latest Jaunty beta.  I'm running on a fairly modern machine; an HP Pavillion dv9000 with 2 GB ram, dual core AMD processor, 250 GB hard drive.  

Windows, the simplest windows, like "Operation complete, click to close" take 30 seconds to 2 minutes to open or close.  This includes gedit, opening a terminal window, etc.

I can't believe this is a general problem -- I wonder if there is something specific in my setup that causes this.

I had XP before hand, which I wanted to keep, so I repartitioned and gave Linux a 20 GB partition using the new ext4 filesystem, and 3 GB swap partition.  The main Linux partition is a logical partition rather than primary partition, because I had 3 XP partitions, which didn't give me the 5th partition for the swap space.

I get three Linux/Ubuntu boot options -- generic, generic [recovery] and memtest.  I select the first, "generic" option.  I get the login prompt reasonably quickly, but then it takes 5 - 10 minutes to get a start page.  I usually go get a cup of coffee & snack, then come back & wait patiently while it finishes getting ready. I installed the nvidia drivers, which gave a greater resolution, but the problems were the same before and after.

So basically, I can't use the system.  But does anything I described give any clues to what the problem might be?  It would be great to get it usable and working.

Thanks,

Paul

---

### Post by Cybie257 on 2009-04-05
Is it as slow as this if you were to boot from the LiveCD and open/close things? (taking in account that the LiveCD would be a little bit slower anyhow....

-Cybie

---

### Post by kevmitch on 2009-04-05
Since you say the login screen is reasonably fast, you might try disabling visual effects in System->Preferences->Appearance. These take effect on login by using a special window manager called compiz. Unfortunately the extra bling causes problems for some people and using the metacity window manager (no visual effects) is a better choice.

---

### Post by GreyGeek on 2009-04-05
Open the system monitor, click on the cpu% column header, and then right click the icon in the upper right corner and select "Advanced" and then "Keep above others".  Squeeze the dialog until just the process name and cpu% are showing and slide it to the left margin until those two columns barely show.

Now, use your distro and notice as you do things which process has the highest cpu%.  If you see a link between a process and the high cpu% you've found your culprit.

---

