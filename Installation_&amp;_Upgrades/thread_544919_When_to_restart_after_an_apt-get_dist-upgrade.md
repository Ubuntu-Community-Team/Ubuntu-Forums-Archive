---
title: "When to restart after an apt-get dist-upgrade"
date: 2007-09-06
forum: Installation &amp; Upgrades
---

### Post by martalli on 2007-09-06
I typically do office-wide updates every day or two, through ssh.  The GUI will tell me after an update whether I should restart the machine, but I have not been able to figure it out from the command line tools (sudo apt-get update && sudo apt-get dist-upgrade).  

I have figured that if a new kernel appears on the list of new updates, that a restart is in order.  However, I suppose there may be other times a restart might be in order.  Is there a way to check if a restart would be in order?  Maybe a flag on the apt-get command, or something else?  I figure that this ability must be built into Ubuntu, or the restart indicator would not appear so quickly on the GUI, but I have yet to figure out how to do this on my own from the CLI.

Thanks for any help.

---

### Post by reckless2k2 on 2007-09-06
restart is only necessary typically with new kernel. that's it.

---

### Post by Seisen on 2007-09-06
I agree that is basically the only time I believe I have seen where I have had to reboot my computer.

---

