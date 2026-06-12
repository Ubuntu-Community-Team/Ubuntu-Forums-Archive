---
title: "/etc directory"
date: 2011-04-28
forum: Installation &amp; Upgrades
---

### Post by Anonimous on 2011-04-28
Good evening. First of all, apologies for this question... I know it's quite silly...
I updated from 10.04 to 11.04 and in Nautilus, in /etc directoty, while trying to use the scroll bar, I'm afraid I moved a couple of directories into anothers. Of course, I don't know which ones have been moved. I've checked the backup I made yesterday to try to discover them, but there are too many differences. How can I restore it to the previous state? What if I leave it as it is now?
Thank you for your help

---

### Post by coffeecat on 2011-04-28
First, you could only have moved directories in /etc if you were running a root nautilus opened with 'gksudo nautilus' or 'gksu nautilus'. Were you?

If you were, whether and when it matters will really depend on what you moved. And if you were running a root nautilus, one way of trying to find out what was moved would be to boot up the live CD and choose "try Ubuntu". When you get to the desktop, mount your permanent Ubuntu root partition and open two nautilus windows - one for the permanent installation root directory and one for the live session root directory ("file system"). Now compare them laboriously folder by folder.

Ideally you should use a Natty live CD to compare with an installed Natty system, but you may find some differences anyway. Installed apps which are not on the live CD will have their own configuration folders and files in /etc.

---

### Post by Anonimous on 2011-04-28
Thanks for your quick reply. Errrrr, yes..., I was using Nautilus as root...
It seems to be dificult to restore things to where they were... I tried comparing my backup and the /etc directory of another Ubuntu installation (6.06 in another partition), but as you say it depends on the applications I have installed.
I found two directories, /config.d and /couchdb that I think should be directly in /etc I hope that's all...
Thank you again

---

