---
title: "update manager and add/remove programs not working"
date: 2007-04-25
forum: Installation &amp; Upgrades
---

### Post by drexegar on 2007-04-25
Hey guys whats up I was trying to install wine in 7.04, I followed the instructions on the site to type everything in the terminal. When I press enter it kept asking me for my administrator password, but it did it over and over so I could not type it in. So I restarted the computer and now I cant get into my update manager or go into my add/remove programs.

I search and hour on this site and havent found a solution in one of the many post that was similar to this.

I found out that winehq.list and the winehq.list.save does exist but I cant remove them, I get a permissions denied error. On my desktop I have a orange box on the upper right corner with an error about opening the cache for the winehq.list and that the list of sources cant be read. Also when I open that file I can read it but I cant alter it.

Is there a way I can remove these files or reset the update manager and get the update manager and my add/remove programs working again with out having to reinstall everything?

Thank you for your time reading this.

---

### Post by mikewhatever on 2007-04-25
Can you post a link to the how-to you followed. Have you typed the commands one by one hitting Enter after each one? Are there any error messages when going to the update manager or Add/Remove?

---

### Post by Jussi Kukkonen on 2007-04-25
drexegar, there's not enough info here, details please.
* Link to the instructions you followed.
* The commands you tried to run (and their outputs) would be useful too, if it's possible to get them (the command *history* may help).

I can make a guess at what went wrong, but this might be wrong because of lack of info:
the files you want to remove are probably in */etc/apt/sources.list.d/*. You can remove them like this:
```
sudo rm /etc/apt/sources.list.d/winehq.list
sudo rm /etc/apt/sources.list.d/winehq.list.save

```

---

