---
title: "Software center not responding"
date: 2011-12-23
forum: Installation &amp; Upgrades
---

### Post by gameguy on 2011-12-23
I just installed 11.10 onto a laptop I got. It's running in wubi, if that makes a difference. I have not been able to start software center at all. It comes up with a white background when I start it, and the window name is software center. It appears to be responding, but is doing nothing. All the other programs on it work fine, but this one doesn't. I tried uninstalling and reinstalling using apt-get, and also tried
```

sudo apt-get clean all
sudo rm /var/lid/apt/lists/*

```It appears to be responding, however, but I don't know what else to call it. It does nothing. I was letting it start up for 2 hours or so, but it never finished.

The CPU is 5% usage on each of the 1.06GHz cores. The RAM usage is only 600MB / 2GB, so it appears to be running smooth.

---

### Post by Paddy Landau on 2011-12-23
I have seen someone else have this problem on WUBI. Unfortunately, I have not seen a solution.

There is an alternative workaround (but it is not as user-friendly). Open a terminal with Ctrl-Alt-T and type the following command (or copy-and-paste):
```
sudo apt-get update && sudo apt-get install synaptic
```Then you can open Synaptic Package Manager (you may need to log out and in again; restart is not required).

Or, you can also browse the [Ubuntu Software Centre on-line]("https://apps.ubuntu.com/").

A word of warning. WUBI is great for testing Ubuntu, but it makes a poor long-term solution because it is unstable, especially with regard to updates. If you wish to use Ubuntu long-term, I would suggest you uninstall WUBI (back up your data first) and do a native installation. Be sure to back up your Windows data first, though; although the installation process is well tried and tested, there is always a tiny chance of data loss.

---

### Post by gameguy on 2011-12-23
> **Paddy Landau said:**
> I have seen someone else have this problem on WUBI. Unfortunately, I have not seen a solution.

There is an alternative workaround (but it is not as user-friendly). Open a terminal with Ctrl-Alt-T and type the following command (or copy-and-paste):
```
sudo apt-get update && sudo apt-get install synaptic
```Then you can open Synaptic Package Manager (you may need to log out and in again; restart is not required).

I just tried that command - synaptic works. I'm not sure if it was nessecary to install synaptic, but I found another solution which works. I tried starting software center normally, didn't work. Tried in terminal, still didn't work. I need to start it as sudo for it to work
```
sudo software-center
```
Not sure if it would have worked without synaptic.

> **Paddy Landau said:**
> 
Or, you can also browse the [Ubuntu Software Centre on-line]("https://apps.ubuntu.com/").

Unfortunately, they seem to be links that need to be opened with software center, but you could always apt-get them.
> **Paddy Landau said:**
> 
A word of warning. WUBI is great for testing Ubuntu, but it makes a poor long-term solution because it is unstable, especially with regard to updates. If you wish to use Ubuntu long-term, I would suggest you uninstall WUBI (back up your data first) and do a native installation. Be sure to back up your Windows data first, though; although the installation process is well tried and tested, there is always a tiny chance of data loss.
I wish I could install it on a seperate partition, but to tell the truth, I'm not really supposed to be installing it even in wubi.

---

### Post by Paddy Landau on 2011-12-23
I'm glad you got it working. You should not have to start Ubuntu Software Centre with sudo (btw, for GUI programs you should use gksudo instead of sudo), but there you go.

---

### Post by gameguy on 2011-12-23
Thanks for your help.

PS. if I'm doing a sudo nano/vim, should it be gksudo? Cause they operate within terminal, but have their own window.

---

### Post by Paddy Landau on 2011-12-23
Correct, nano and vim work within the terminal and do not require the GUI interface, so for them sudo will suffice.

---

### Post by lisati on 2011-12-23
There's some good information about sudo, gksudo, and kdesudo to be found here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by tonyguntrum on 2012-01-07
Software center stopped working after the recent upgrade.  It starts to load then just hangs there, have tried everything I can find on the boards nothing has worked  when I try to start it manually this is what I get


tony@tony-LT:~$ sudo software-center
2012-01-07 20:17:11,234 - softwarecenter.ui.gtk3.em - INFO - EM's: 17 15 21
2012-01-07 20:17:12,014 - softwarecenter.ui.gtk3.app - WARNING - database format '6' expected, but got ''
Traceback (most recent call last):
  File "/usr/bin/software-center", line 151, in <module>
    app = SoftwareCenterAppGtk3(datadir, xapian_base_path, options, args)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 226, in __init__
    self._rebuild_and_reopen_local_db(pathname)
  File "/usr/share/software-center/softwarecenter/ui/gtk3/app.py", line 383, in _rebuild_and_reopen_local_db
    from softwarecenter.db.update import rebuild_database
  File "/usr/share/software-center/softwarecenter/db/update.py", line 91, in <module>
    cataloged_times = pickle.load(open(CF))
cPickle.UnpicklingError: invalid load key, ''.
tony@tony-LT:~$

---

### Post by bluexrider on 2012-01-07
It is better to post a new thread then one that has been (SOLVED)

---

### Post by bluexrider on 2012-01-07
It is better to post a new thread then one that has been marked (SOLVED)

as a suggestion ```
sudo apt-get update && sudo apt-get -y reinstall software-center
```

---

