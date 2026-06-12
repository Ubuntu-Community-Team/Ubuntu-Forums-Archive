---
title: "Init errors"
date: 2010-03-11
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Vanishing on 2010-03-11
As I posted yesterday, I did a bunch of upgrades, which has initiscripts, sysvinit-utils, sysv-rc packages, no error messages poped up. Upon reboot, I am greeted by the following error in tty7:
> 
init: upstart-udev-bridge main process ended, respawning
init: udev main process ended, respawning
init: rsyslog main process ended, respawning
init: acpid main process ended, respawning
init: atd main process ended, respawning
init: cron main process ended, respawning

and sometimes these error tends to change, but the general ideas is there.
I had to go to tty1, login and startx, this will give me a working desktop, but some components disabled, and sometimes i can get network to work by issueing:
> sudo /etc/init.d/networking start
sudo /etc/init.d/network-manager start, while other times I can't.

I tried downgrading the 3 packages I mentioned, but nothing changes.

Any Idea where to start?

Much appreciated.

---

### Post by ranch hand on 2010-03-11
Have you run;
```

sudo update-initramfs -u

```
That will update the current version.  See the man page for other options.  Might help.

---

### Post by Vanishing on 2010-03-11
> **ranch hand said:**
> Have you run;
```

sudo update-initramfs -u

```
That will update the current version.  See the man page for other options.  Might help.

Hmm. I even tried to install a new kernel, which triggers this command...thanks for the idea.

Any other thoughts?

---

### Post by Vanishing on 2010-03-11
bump?
please,,anybody?

---

### Post by ww2 on 2010-03-30
I'm having the same problem after a update yesterday. Following the errors I'm greeted by the Recovery Menu. Then I can get a working terminal, to login and startx, but there seems to be no way to get networking functional.

Having to reinstall Lucid because of this would obviously be very unpleasant. Any help?

---

