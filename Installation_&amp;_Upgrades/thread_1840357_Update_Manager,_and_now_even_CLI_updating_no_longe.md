---
title: "Update Manager, and now even CLI updating no longer works please help"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by youWho on 2011-09-07
Hi. I've searched everywhere but nobody seems to have had this issue:

It started when one day I ran the "Update Manager" GUI app to install the regular updates, but somehow (I didn't do anything to interfere) there seemed to be a temporary file left in /tmp, and the update process would stop in the middle; it seemed that the updates had been downloaded, though I'm not sure anything else had been done, probably not. The only way to get out of that jam was to type return and/or ctl-c which would allow me to at least quit the Update Manager. For the last several weeks since this happened I've been updating by:
1. run the "Update Manager" and getting out of its stuck state by ctl-c and return;
2. restart, boot into recovery mode to "Fix broken packages";
3. restart.

That has worked, though it was a nuisance to have to do---until now. Just now it showed the same symptom in the console screen as was in the embedded terminal screen displayed by Update Manager: a seemingly leftover file in /tmp. Incidentally this file in /tmp changes name with each try. Now I seem to have no way to do a normal update---installing regular security updates for example.

If anybody has any solution for how I can get back to where the update process goes as it's supposed to please tell me. Thanks in advance.

---

### Post by Beacon11 on 2011-09-07
Is it possible your hard drive is low on space? You might try clearing the cache of files you downloaded via ```
sudo apt-get clean
``` Then try updating/upgrading again. If that doesn't help, can you simply run ```
sudo apt-get update
``` without errors?

---

### Post by youWho on 2011-09-07
My hard drive is not at all full. It's at about 51%. And I have no trouble at all running
sudo apt-get update
without errors. And
sudo apt-get clean
didn't help.

Thanks, but any ideas please let me know.

It seems that the downloading of updates works, but the downloads are not installed. It seems that it's the same whether the update is done from the Update Manager GUI app or the command line.

On a hunch I tried disconnecting the ethernet cable while in "recovery mode" (I used to have it configured where I'd have to connect manually, now I have it automatically connecting) and then doing "fix broken packages" and, huh, it worked! But what an inconvenient hack: I have to download the updates, then restart into recovery mode, disconnect from the internet, run the recovery, then reboot again into the normal system. So if anybody has any ideas... thanks!!

---

