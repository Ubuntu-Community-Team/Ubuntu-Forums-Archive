---
title: "shuts down while starting up"
date: 2008-07-19
forum: Installation &amp; Upgrades
---

### Post by marioandluigi206 on 2008-07-19
I am trying to install Ubuntu on my HP tablet pc, and whenever I try to run it off the cd or install, the orange bar starts to fill up like when it starts up, but then it starts to drain like when it shuts down. Then it tells me to remove my cd and press enter. Help?

---

### Post by Partyboi2 on 2008-07-19
Did you check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") and checked the cd for defects (option 5 I think at the main menu)
Another thing you could try is at the main menu press F6 and change the word splash to nosplash to see if you get any more info on whats happening.

---

### Post by wpshooter on 2008-07-19
> **Partyboi2 said:**
> Did you check the [[COLOR=Blue]md5sum[/COLOR]]("https://help.ubuntu.com/community/HowToMD5SUM") and checked the cd for defects (option 5 I think at the main menu)
Another thing you could try is at the main menu press F6 and change the word splash to nosplash to see if you get any more info on whats happening.

Not only should you do the sumcheck but you should also check the integrity of the Ubuntu CD by running the verification function that is found on the initial Ubuntu boot screen menu.

---

### Post by marioandluigi206 on 2008-07-19
I don't think it's an issue with my CD, because I've tried both a CD I made and a CD I requested. Both had the same issue on this computer, and both worked on the old computer. I'll try the nosplash later today when I get home and update w/ the results. Also, in case this helps, my computer has "AMD Turon X2 Ultra 64."

---

### Post by marioandluigi206 on 2008-07-19
OK, it keeps saying it reaches critical temperature over and over again at around 65 C, even though I am indoors in a very air conditioned room.

---

### Post by Partyboi2 on 2008-07-19
If you are running a desktop computer remove the casing and give it a good dust especially around the  fans

---

### Post by marioandluigi206 on 2008-07-22
It's a laptop. I got it to install using wubi, but now whenever i start up i get the same error. One fact I should have included earlier: its a tx2500 series computer. I've tried acpi=off but it doesn't recognize the command.

---

### Post by gali98 on 2008-07-25
use these:

noapic nolapic

you mixed up c and i :)
Kory

---

### Post by thegnark on 2008-07-29
Guide for installing Ubuntu on the tx2500:
[http://ubuntuforums.org/showpost.php?p=5468138&postcount=113](http://ubuntuforums.org/showpost.php?p=5468138&postcount=113)

---

