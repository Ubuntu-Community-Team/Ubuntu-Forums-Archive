---
title: "Upgrade from 19.10 to 20.04"
date: 2020-04-18
forum: Installation &amp; Upgrades
---

### Post by carusoswi on 2020-04-18
I ran in terminal 'Apt-get Upgrade, and 19.10 seemed to download the proper files.  I slected 'N' when prompted because I wanted to check with forum members before proceeding.

If I select Y, will 20.04 be installed to replace my 19.10 without disturbing my installed applications?

I know this may be a silly question to ask, but I upgrade so infrequently, I never remember the process, and do not want to mess up my dual boot system (Windows 10 is the other OS).

I do not remember the last time I had a serious issue with either side of my computer.

Also, I see a DD option online.  If I want that option, what must I do in addition to the terminal request to upgrade?

Thanks in advance for any advice.

Love Ubuntu,

Caruso

---

### Post by Bashing-om on 2020-04-18
carusoswi; Hello

You have a misunderstanding of the apt command(s).
'apt upgrade' updates installed packages,

The command to run the release upgrade - when the system is prepared - is:
```

sudo do-release-upgrade -d

``` where in this invocation the -d is "development"; as 20.04 remains in that state until the 20.04.1 release,

[INDENT]my bit to try and help
[/INDENT]

---

### Post by ajgreeny on 2020-04-18
You will not move from 19.10 to 20.04 by running ```
sudo apt-get update
sudo apt-get upgrade
```
It will simply make sure all your 19.10 packages are fully upgraded and secure.

If you have made no changes to the default upgrade system 19.10 will automatically have been running the unattended-upgrades system so all security upgrades will have been performed without input from you.

---

### Post by Dennis N on 2020-04-18
I would wait until the Software Updater informs you that a new release is ready and offers to do the upgrade. This notification should be a week or two after the 20.04 release date.

---

### Post by mörgæs on 2020-04-18
Please run the two commands from by Ajgreeny and post their results in CODE tags.
It will tell if your system is secure or not.

---

### Post by SeijiSensei on 2020-04-19
If you do decide to use "do-release-upgrade" you'll need to first run "apt full-upgrade" to insure everything on your 19.10 system is up-to-date.

---

### Post by guiverc on 2020-04-19
If you like watching videos, I'll suggest the following

Alan Pope's command line upgrades with do-release-upgrade, Alan goes from 18.04 to 20.04
[https://www.youtube.com/watch?v=pr3HA3jw1vg](https://www.youtube.com/watch?v=pr3HA3jw1vg)

Alan Pope's Upgrading Ubuntu 18.04 to Focal (20.04)
[https://www.youtube.com/watch?v=f7DmV7V2rts](https://www.youtube.com/watch?v=f7DmV7V2rts)

I haven't re-watched these, but it'll be applicable from 19.10 to 20.04

---

