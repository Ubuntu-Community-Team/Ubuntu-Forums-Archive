---
title: "[SOLVED] New &amp;quot;kernal&amp;quot; added when updates are installed"
date: 2008-06-26
forum: Installation &amp; Upgrades
---

### Post by JBEvermore on 2008-06-26
Greetings.

I run a dell inspiron 6000 with an xp/hardy dual boot. The system itself runs fine (minus my impossible to configure broadcom wireless, ugh).

However, whenever the update script is run I've noticed that it adds another Ubuntu kernal option in the boot screen. It's up to four Ubuntu 8.04 choices and one xp. Seems to add about one a week.

The strange thing is, each option takes me to the same up-to-date install. They all point to the same thing.

My linux voodoo is decent, but this one is making me scratch my head. Any ideas?

---

### Post by jualin on 2008-06-26
This is totally normal dude, ubuntu updates the **kernel** whenever a new one is available. Every time a new kernel is installed a new line will appear in the Grub for safety reasons. Greetings from Miami, FL.

*edit* And every time you choose to start with your old kernel, the old kernel is the only thing that will be old on your comptuer, all the updates that you applied will show up when you boot up the old kernel. This is not like "Restore Windows" which took you back on time and gave you a system which only had the programs that you had on that date.

---

### Post by JBEvermore on 2008-06-26
Uh huh...that said is there a way to clear it back to one boot option to keep the loader from getting cluttered?

---

### Post by jualin on 2008-06-26
As suggested in this thread [http://ubuntuforums.org/showthread.php?t=837485&highlight=kernel+lines+grub]("http://ubuntuforums.org/showthread.php?t=837485&highlight=kernel+lines+grub") you need to install start up manager and do it from there, which is easier than doing it from the Command Line (editing Grub's menu.lst). To install the start up manager type > sudo apt-get install startupmanager.

---

### Post by JBEvermore on 2008-06-26
Ahh, much thanks. That's what I was looking for.

---

### Post by jualin on 2008-06-26
No problem, just remember to mark your thread solved using the "thread tools" at the top of the page.

---

