---
title: "Updating from 13.04 to 13.10 is realy bad"
date: 2013-10-27
forum: Installation &amp; Upgrades
---

### Post by adscnet on 2013-10-27
I've updated my desktop from 13.04 to 13.10 & the problems started:
1- When I login using Ubuntu Default desktop environment, I get this message "Couldn't acquire name on session bus, logout" then it logs out 
2- I accessed Cinnamon DT environment in order to access my system
3- My system is slow with this new updates
4- I'm getting many errors "... experienced an internal error"

any suggestion how to solve this issues?

---

### Post by ptn107 on 2013-10-27
1) See if any required package is missing from the default 13.10 install.  Download the checker script [_here_]("http://www.filedropper.com/saucy-list-packagestar") (click download this file, and enter the captcha code).

Right-click the file and extract the contents.

From the terminal (CTL+ALT+T) run the *saucy-list-packages/list-missing* script which generates a *missing.packages* file.  Check out the list it makes with gedit.  These packages should be installed on all 13.10 systems.  They can be all installed by running:
```
sudo apt-get install `cat missing.packages`
```
from the same folder.

Last resort, backup your stuff and clean install.

---

### Post by adscnet on 2013-10-28
Thanks for your reply,
I've done that & get error when tried to install the missing packages using 'cat missing.packages', so I installed them manually one by one, rebooted the sys, but still same problem when I open the [COLOR=#000000]Ubuntu Default desktop environment [/COLOR]t & I tried to capture some of them, system crashes on the following files:
-ibus 1.5.3-6ubuntu2
-gnome-settings-daemon 3.8.5-0ubuntu9
-gvfs-backends 1.18.2-0ubuntu1
-hud 13.10.1+13.10.20131014-0ubuntu1


then shows "Permission denied" message, then it automatically logout.
I think the gnome environment is damaged/corrupted

---

### Post by adscnet on 2013-10-29
Hi,
Today I found some update from ubuntu by running Update-Manager & after installing the updates I got the following warning msg which again its related to the previous problem ibus:

update-manager:4837): IBUS-WARNING **: The owner of /home/adsc/.config/ibus/bus is not root!

any suggestion

---

### Post by adscnet on 2013-10-29
Hi,
Today I found some update from ubuntu by running Update-Manager & after installing the updates I got the following warning msg which again its related to the previous problem ibus:

update-manager:4837): IBUS-WARNING **: The owner of /home/adsc/.config/ibus/bus is not root!

any suggestion

---

### Post by ptn107 on 2013-10-29
my /home/phil/.config/ibus/bus folder is not root either.  It works fine here.

You can try to delete the /home/adsc/.config/ folder.  It will reset all of your desktop settings but it may solve the problem.  Prefix the following command with 'sudo' and run it:
```
rm -rf /home/adsc/.config/
```
and restart.

---

### Post by adscnet on 2013-10-30
unfortunately it didn't solve the problem.

**Note**: I'd like to highlight again that I'm facing this problem only when I login using [COLOR=#000000]Ubuntu Default desktop environment but, if I login using cinnamon desktop environment I don't see any problem. 

[/COLOR]I was thinking of (if nothing solved this problem): 
- Reinstall ubuntu directly 13.10 ver, but worried about (1) my dual boot & (2) my existing huge data under home 
- Downgrade to 13.04, but I'm sure I wont get the 100% of the 13.04

What do you suggest?

---

### Post by adscnet on 2013-11-01
I wondering if anyone can suggest a solution for this issue.

---

### Post by adscnet on 2013-11-20
Since I couldn't get any answer which can help me in solving the problem, in addition I had error message in every update I run in the system such:
```

(update-manager:6364): IBUS-WARNING **: Unable to connect to ibus: Could not connect: Connection refused


update-manager:5637): IBUS-WARNING **: The owner of /home/../.config/ibus/bus is not root!

```

finally I decided to re-install ubuntu 13.10 as fresh copy.

---

### Post by Joe Schoen on 2013-11-28
adscnet, how is that working for you? Did the fresh install solve all the problems mentioned above? I too am having a range of issues that wouldn't fit into just one ticket. Many internal errors and problems with the taskbars and desktop. I too upgraded from 13.04.

---

