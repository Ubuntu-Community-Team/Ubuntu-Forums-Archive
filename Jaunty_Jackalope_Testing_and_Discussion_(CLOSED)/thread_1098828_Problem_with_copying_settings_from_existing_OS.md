---
title: "Problem with copying settings from existing OS"
date: 2009-03-17
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by hewhocutsdown on 2009-03-17
My laptop had Ubuntu 9.04 on it.

I was reinstalling 9.04 on the system and it asked if I wanted to preserver Pidgin and Firefox settings. I said yes, and proceeded with the install, reformatting the partitions that had been / and /home.

On boot, the settings were not there. I suspect this is by design, but it is not clear - perhaps a warning that "you are formatting the partition which stores this data, it will be unavailable and will not be copied" or some such would be beneficial for such situations?

---

### Post by Bakon Jarser on 2009-03-17
I did not format any partitions and it did not import my old settings.  It didn't do it when I upgraded from XP to 7.10.  It didn't when I went from 7.10 to 8.04....etc.  I always have to copy the settings manually.  Does this feature work for anyone?

---

### Post by nyarnon on 2009-03-17
First and for all, if you reinstall and format it is obvious you should at any time first backup your existing data.

That said, I have no idea what has gone wrong with both of you. I regularly install Ubuntu on a number of different systems, from XP and Older of equal Ubuntu's and I never encountered any problem with the settings.

Could you give a step by step example so I can recreate the problem?

---

### Post by Halow on 2009-03-17
It did work for me when I installed Jaunty alpha 4. It also worked on all the "upgrades" I've tried (except that one time I got so sick of Windows I recreated the partition table...) I stopped using it after a4 because apparently some of my gnome coloration settings (done by me, so I have no one else to blame) were being problematic from Intrepid to Jaunty.

---

### Post by Bakon Jarser on 2009-03-17
> **nyarnon said:**
> First and for all, if you reinstall and format it is obvious you should at any time first backup your existing data.

That said, I have no idea what has gone wrong with both of you. I regularly install Ubuntu on a number of different systems, from XP and Older of equal Ubuntu's and I never encountered any problem with the settings.

Could you give a step by step example so I can recreate the problem?

Did a clean install of alpha 6 onto unpartitioned space.  Home directory is shared on a separate partition.  It asked me if I wanted to import settings.  One strange thing is that it had my intrepid username listed twice.  I'm 99% sure that I chose the right partition that intrepid was installed on.  I went on with the installation and no firefox settings were imported.  As for the other upgrades, it always gets my hard drives mixed up for my grub settings so maybe it was looking on the wrong drive for these settings too (I'm only running one drive now).

---

### Post by nyarnon on 2009-03-17
Well sounds like a mockup of your other system. If ubuntu finds 2 users with the same name it probably tried to install the settings from the wrong user. You could get arround that by deselecting that wrong user.

---

