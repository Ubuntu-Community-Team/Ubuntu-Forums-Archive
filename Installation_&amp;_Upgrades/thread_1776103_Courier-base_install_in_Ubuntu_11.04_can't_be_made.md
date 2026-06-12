---
title: "Courier-base install in Ubuntu 11.04 can't be made quiet"
date: 2011-06-05
forum: Installation &amp; Upgrades
---

### Post by TBA-UK on 2011-06-05
Hi everyone

I'm trying to get Courier-MTA to install unattended with apt-get but even with the -qq and -force-yes options the courier-base package still pops up and asks a question (about whether to use config directories instead of files). 

Is there any way to either specify these options up-front or have the default options chosen automatically?

Its happening with other unrelated packages too, I just haven't worked out which. I'm using a perl script which executes the command (using backticks) and captures the exit code and other output, but these interactive screens are proving difficult to workaround, and since perl is capturing the output the screens don't even actually appear, just my script hangs!

Thanks in advance
TBA

---

