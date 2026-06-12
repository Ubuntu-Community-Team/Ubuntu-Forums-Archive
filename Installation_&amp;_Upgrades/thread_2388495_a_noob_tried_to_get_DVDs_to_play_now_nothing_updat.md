---
title: "a noob tried to get DVDs to play now nothing updates or installs"
date: 2018-04-03
forum: Installation &amp; Upgrades
---

### Post by flyinghigh2 on 2018-04-03
hi a while back I tried apt-getting some dlls or codecs; cant rememer what but it was to get DVDs to play. I dont think it worked// anyhow I have a No Entry sign in the top corner and nothing seems to be downloading anymore, updating software releases doesnt work.. my scanner software doesnt work anymore

generally i have m,ssed it up a bit

any advice

---

### Post by DuckHook on 2018-04-03
It is not possible to help with so little to go on. Unless you remember all of the steps you took that caused the current problems, it will be almost impossible to play doctor here. There are so many things that could be the cause of your symptoms, which are very disparate indeed. dlls are Windows elements, so it is most unlikely that you installed any. Bad codecs should not give rise to broken updates or busted scanning. Therefore, I suspect that you did a lot more than just try installing codecs.

I recommend a tested data backup and a full reinstall at this point. The time it will take to reinstall will be a fraction of what it will cost you to try tracking down your previous steps. However, if you are intent on trying to salvage your existing install (perhaps for, say, learning purposes) then you can start by reviewing your bash history and telling us what previous steps you took. We will need clear and complete details.

Note, if you applied measures that did not involve the command line, then bash history won't tell you anything. You will have to recall those from memory and/or go through your dpkg log files to reconstruct what was installed.

On the very remote chance that the problem is simply an old apt database, open a terminal and: ```
sudo apt update && sudo apt upgrade
```Post the results back to this thread between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

---

### Post by wildmanne39 on 2018-04-03
Thread closed! Please get help in this thread.

[https://ubuntuforums.org/showthread.php?t=2387056](https://ubuntuforums.org/showthread.php?t=2387056)

---

