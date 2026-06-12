---
title: "why dosent jaunty tell you theres updates available?"
date: 2009-04-06
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by krakk2k on 2009-04-06
is there any way to make it?

---

### Post by swoll1980 on 2009-04-06
Might be a bug. From what I heard Jaunty is supposed to ram updates down your throat.

---

### Post by regonzal on 2009-04-06
I have been wanting to ask this as well. I have read in the forum that some changes have been made.However, I can't seem to get a clear answer to the question of how the update-notifier now works in Jaunty, anyone?

---

### Post by damis648 on 2009-04-06
Every week Jaunty forcefully opens update-manager in a deal-with-me-now fashion.:popcorn:

---

### Post by regonzal on 2009-04-06
Really? I much liked the old system where it showed up to notify you instead of having to force-installing through the update manager in the System tab.

---

### Post by krakk2k on 2009-04-06
> **damis648 said:**
> Every week Jaunty forcefully opens update-manager in a deal-with-me-now fashion.:popcorn:

ugh, thats kind of screwy, the intrepid way was perfect. just a simple icon/message, and no FORCING you to restart ala windows xp/vista

---

### Post by Kareeser on 2009-04-06
Correct. In Jaunty, the update-manager will openn automatically whenever updates are available.

This is due to the new notification system, notify-osd, which is, by design, non-interactable.

People are working on a more graceful solution :)

See: [https://wiki.ubuntu.com/NotifyOSD#Update%20Manager](https://wiki.ubuntu.com/NotifyOSD#Update%20Manager)

---

### Post by krakk2k on 2009-04-06
> **Kareeser said:**
> Correct. In Jaunty, the update-manager will openn automatically whenever updates are available.

This is due to the new notification system, notify-osd, which is, by design, non-interactable.

People are working on a more graceful solution :)

See: [https://wiki.ubuntu.com/NotifyOSD#Update%20Manager](https://wiki.ubuntu.com/NotifyOSD#Update%20Manager)

it dosent auto open on my jaunty O,o

---

### Post by chucky chuckaluck on 2009-04-06
> **swoll1980 said:**
> Might be a bug. From what I heard Jaunty is supposed to ram updates down your throat.

> **damis648 said:**
> Every week Jaunty forcefully opens update-manager in a deal-with-me-now fashion.:popcorn:

"what's my name, *****?!?"

---

### Post by llamakc on 2009-04-06
> **chucky chuckaluck said:**
> "what's my name, *****?!?"

*"Do they speak Jaunty in what?"*

---

### Post by damis648 on 2009-04-06
> **llamakc said:**
> *"Do they speak Jaunty in what?"*

/me is confused... :confused:

---

### Post by caryb on 2009-04-06
Your problem is not isolated to Gnome/Ubuntu I have the same problem in KDE/Kubuntu, but on the machines I have done fresh installs it works flawlessly (in Kubuntu) So I'm thinking it's a legacy problem that something is not getting installed during upgrades?


Cary

---

### Post by rbmorse on 2009-04-06
I did a fresh install when the beta was released and the update notification still doesn't notify.

---

### Post by ktp on 2009-04-06
> **regonzal said:**
> Really? I much liked the old system where it showed up to notify you instead of having to force-installing through the update manager in the System tab.

Here is how you can enable the right behavior, i mean old one:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Here is the bug report in you are interested:
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by macogw on 2009-04-07
> **krakk2k said:**
> it dosent auto open on my jaunty O,o

It auto-opens one week after the last time you updated (even if that was from the command line).

---

### Post by RIchard James13 on 2009-04-07
On my Kubuntu system the kde-update-notifier always says I have 19 updates to install. Somewhere it must have some sort of broken cache of packages. I have looked at the code for it and if I run 
```
/usr/lib/update-notifier/apt_check.py
```
it returns 98 when there are 78 packages.

Like caryb said I believe this is a Legacy problem because it is not a fresh install.

Note you can also run
```
/usr/lib/update-notifier/apt_check.py -p
```

And it will list all the packages that it thinks it needs to update. If you run it without the -p it returns the number of packages a comma and then any security package updates.

---

### Post by jordicm on 2009-04-07
And for kubuntu??


> **ktp said:**
> Here is how you can enable the right behavior, i mean old one:

```
gconftool -s --type bool /apps/update-notifier/auto_launch false
```

Here is the bug report in you are interested:
[https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945](https://bugs.launchpad.net/ubuntu/+source/update-notifier/+bug/332945)

---

### Post by bcrook88 on 2009-04-07
The other option is launch gconf-editor and edit the following value:
Apps: update-notifier: regular_auto_launch_interval

The value of this key gives the interval in days that the update manager should forcibly open to show you available updates. 

Default value is 7 days, if you change it to 0 is launches when there are updates available. It seems to be open when I check in the morning.

---

### Post by dabl on 2009-04-07
> **caryb said:**
> Your problem is not isolated to Gnome/Ubuntu I have the same problem in KDE/Kubuntu, but on the machines I have done fresh installs it works flawlessly (in Kubuntu) So I'm thinking it's a legacy problem that something is not getting installed during upgrades?


Cary


I installed Kubuntu 9.04 Beta the day it was released, and have not seen anything unexpected with the notifier -- it pops up for a minute or two after I boot the system, then it goes away, and I can either run updates, or not, as I choose.

---

### Post by ktp on 2009-04-15
> **jordicm said:**
> And for kubuntu??

Sorry don't use KDE.  Is the new notification system in KDE?  I thought they were still considering but not including just yet.

---

### Post by FuturePilot on 2009-04-15
> **dabl said:**
> I installed Kubuntu 9.04 Beta the day it was released, and have not seen anything unexpected with the notifier -- it pops up for a minute or two after I boot the system, then it goes away, and I can either run updates, or not, as I choose.

> **ktp said:**
> Sorry don't use KDE.  Is the new notification system in KDE?  I thought they were still considering but not including just yet.

No, Kubuntu is not using the new notification system at this point.

---

