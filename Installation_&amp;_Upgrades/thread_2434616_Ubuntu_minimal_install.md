---
title: "Ubuntu: minimal install"
date: 2020-01-08
forum: Installation &amp; Upgrades
---

### Post by dandy-andy on 2020-01-08
Hello,

i wanted to istall a minimalist version of Ubuntu (network installer + mini.iso) but after command 

sudo apt-get install xorg

i got an ubuntu windows manager. And that's exactly what i didn't want to happen. I thougt it would  install x11-server and nothing else.

I wanted to use awesome windows manager instead of that. So how could  i avoid this happening?

---

### Post by TheFu on 2020-01-08
Did you try *--no-install-recommends* as an option?  It is in the manpage for apt-get.

---

### Post by dandy-andy on 2020-01-08
no, i didn't. 

i'll try it out.  thanks.

---

### Post by TheFu on 2020-01-08
If you choose not to read the output from commands and logs, Ubuntu is going to be really frustrating.

We all have that "wall of text" overwhelmed feeling at first.  Get over it.  Read what the messages say.  About 50% of the time, the exact resolution will be spelled out.

All system log files are under /var/log/ ... usually at that level, but they might be deeper. This is where hardware issues will show up like overheating of CPUs or failing disks.  help.ubuntu.com has a page about log files.

When you see a line with "error" or "warning" in it, that that line (copy it) and paste it into google. Add "ubuntu xx.xx" where xx.xx is the specific release being run and search.  That will usually find other users with the same issue and perhaps a solution.  The trick is to stay with reputable sources when searching for answers.

---

