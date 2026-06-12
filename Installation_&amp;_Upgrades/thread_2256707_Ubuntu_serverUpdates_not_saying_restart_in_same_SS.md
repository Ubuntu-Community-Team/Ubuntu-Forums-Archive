---
title: "Ubuntu server/Updates not saying restart in same SSH session"
date: 2014-12-14
forum: Installation &amp; Upgrades
---

### Post by magpie03 on 2014-12-14
Hello all,
I'm running a small Ubuntu server, 12.04.5 LTS, from my home serving static web pages. I also use it as a print server. Five months ago I had minor problems so I did a clean install and and put my web pages back up. Every morning I check my site from my browser. I use my file manager on my main PC, running Ubuntu 14.04 LTS, to transfer updated pages and view the logs. I then use terminal and SSH to my server to see if any updates are available. If there are updates, I use "sudo apt-get dist-upgrade" to install them. When the installiation completes, I'm back at the prompt. If the update requires a reststart, it does not notify me. Now, when I SSH to it again later in the day or the next day, it says a restart is required. Is there a reason updates that require a restart won't notify me in the same session?

Thanks all

magpie.......

---

### Post by ian-weisser on 2014-12-14
Most upgrades that require restarts involve kernel updates (the same ones that require 'dist-upgrade' instead of normal 'upgrade').
You don't need to restart immediately, unless you want to use that new kernel.
Since the need for a restart is both predictable (kernel updates) and non-essential (the old kernel is still working), I don't see a reason to pester you for a restart at the time.

On my home server, I let apt do the daily updates automatically, without all that tedious SSHing-in-to-check. Once a month or so, when I ssh in for another reason and notice the message, then I schedule the restart.

---

### Post by magpie03 on 2014-12-14
Thank you very much ian-weisser,
Seems I remember in the old days it asked for a restart if required. SSH may be tedious, but its forcing me to learn. Thats one reason I'm running a server.
Thanks again ian-weisser

magpie

---

