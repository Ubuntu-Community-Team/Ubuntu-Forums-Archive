---
title: "how to get exclusive lock"
date: 2012-05-15
forum: Installation &amp; Upgrades
---

### Post by Varad Vyapari on 2012-05-15
i m an amateur ubuntu user and while updating to 12 04, i paused the update once and when i resumed the update again after a shut down, it was unable to update and gave the message

Unable to get exclusive lock

This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

what should i do to resume the update...please help..
thanks in advance

---

### Post by Paddy Landau on 2012-05-15
As the message says, it means that it is already running. By default, Ubuntu runs a check after you reboot -- not immediately, but some time within (I believe) the first 30 minutes.

If you get this error, all you need do is wait a few minutes and try again. If there is a lot to load, you may have to wat a bit more than a few minutes.

Generally, it is not advised to pause an update. Once an update has started, allow it to run its course.

---

### Post by Lisiano on 2012-05-15
In case the update takes a while, open a terminal (Ctrl+Alt+T) and type this
```
ps aux | grep dpkg | grep -v grep
```If it shows any text then it means your system is still updating, just wait. If not, then report back with issuing just ```
ps aux > ~/ps.result.txt
``` and copy pasting the contents of a file in your home directory called ps.results.txt. Either put it in code tags (The hash (#) button) or via [http://paste.ubuntu.com](http://paste.ubuntu.com) and posting the URL here.

---

### Post by Varad Vyapari on 2012-05-16
thanks indeed for all ur suggestions and today when i started the update, it is working fine. Actually here i do not have fluent internet connectivity and so have to cancel the update many a time. Could u pls suggest any proper way of pausing the upgrade so that the process doesn't get disrupted the next time i resume a download.
thanks again for ur suggestions.

---

### Post by Paddy Landau on 2012-05-17
> **Varad Vyapari said:**
> Could u pls suggest any proper way of pausing the upgrade so that the process doesn't get disrupted the next time i resume a download.
Ah, unreliable Internet connectivity can make it harder.

If I recall correctly, when you run Update Manager, there is a box to tick that says to download updates only. If you tick it, it will not install; it will just download the updates. Once that has successfully finished (however many tries you need), only then install.

---

### Post by Varad Vyapari on 2012-05-17
yes dat would be wise..thanks for the help...

---

### Post by Paddy Landau on 2012-05-17
If we have answered your questions, please [mark this thread as solved]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads").

---

### Post by Varad Vyapari on 2012-05-19
as you would see i have successfully updated to 12.04 and thanks for ur help..but as u suggested, i checked if there was indeed a provision to download the updates first and then install them but unfortunately i couldn't find any such provision..would u be able to advise me if i can use terminal to do this?

---

### Post by Paddy Landau on 2012-05-19
Use the download-only option:
```
sudo apt-get update
sudo apt-get --download-only upgrade
```

---

### Post by Varad Vyapari on 2012-05-26
well, thanks a lot.

---

