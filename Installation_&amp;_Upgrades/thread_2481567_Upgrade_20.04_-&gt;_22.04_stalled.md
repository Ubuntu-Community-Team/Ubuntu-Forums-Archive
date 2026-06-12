---
title: "Upgrade 20.04 -&gt; 22.04 stalled"
date: 2022-12-03
forum: Installation &amp; Upgrades
---

### Post by mike40033 on 2022-12-03
I'm trying to upgrade from 20.04LTS to 22.04LTS, but it appears to have stalled.

The last log message in the terminal is something like this:

Qstandardpaths xdg_runtime_dir not set: Defaulting to '/tmp/runtime-root'

I don't know how to get the full log, I was using the GUI tool.

In the GUI it says it's up to Installing the Upgrades, the purple progress bar is nearly complete, and it sais it has "Installed gir1.2-handy-1 (amd64)

Any advice? Will I have a working system if I reboot? Can I continue or restart the upgrade somehow?

---

### Post by Bashing-om on 2022-12-03
mike40033; Ouch !

> 
... Will I have a working system if I reboot? Can I continue or restart the upgrade somehow?


Hard at this point to say.
However, let us take a gander and see if there is damage and a way forward,

Still waiting ? Key combo ctl+c to exit out and return to terminal -
now >>
post back:
```

sudo apt update
sudo apt upgrade
sudo dpkg --configure -a
sudo apt -f install
lsb_release -a

```

see where we go from here

[INDENT]hate when this happens
[/INDENT]

---

