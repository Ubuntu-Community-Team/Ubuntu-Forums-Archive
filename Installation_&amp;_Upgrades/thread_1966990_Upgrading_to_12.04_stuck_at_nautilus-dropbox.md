---
title: "Upgrading to 12.04 stuck at nautilus-dropbox"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by kernco on 2012-04-27
I'm upgrading my system to 12.04, and the upgrader is stuck at setting up the nautilus-dropbox package. It looks like it's trying to download dropbox, and the download timed out or something. Here's the lines from the terminal (I had to type it out, couldn't copy-paste):

```
Setting up nautilus-dropbox (0.7.1-2) ...

Dropbox is the easiest way to share and store [blah blah blah]

[1K Downloading Dropbox ... 0%][1K Downloading Dropbox...0%]...
```

and it does that all the way up to 58%.

What should I do here? Is there a way I can safely kill the upgrade and then continue it?

---

### Post by preston777 on 2012-04-27
same here any luck fixing it?

---

### Post by poumtatalia on 2012-04-30
Same here.
Stuck while "Intalling the upgrades". 
Is it safe to reboot? Or to kill some process?

---

### Post by godthefather on 2012-04-30
Dropbox process must be stopped for it to be updated.

Right-click onthe Dropbox icon and select "Exit".
Then terminate the proccess.

I used gnome-system-monitor to end it.
(Open the terminal/konsole and type
```
sudo gnome-system-monitor
```then go to "Processes" tab and browse for Dropbox process and choose to terminate it.)

After this, (K)Ubuntu upgrade should continue smoothly.

---

### Post by ebierly on 2012-06-23
thank you thank you thank you

---

### Post by nipunshakya on 2012-06-24
Its better you not upgrade dropbox as there are repeatedly being told that dropbox installation is a failure in 12.04... only few gets installed too.. so be careful not to upgrade to dropbox when upgrading

---

