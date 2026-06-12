---
title: "update manager quits half way"
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by donaldt on 2012-08-30
My update manager will not complete an update.  Even just one or two items.  It stops 1/2 way and locks up the computer.

If I go to terminal before I use update manager and launch:  

[sudo apt-get update && sudo apt-get dist-upgrade]

Then launch update manager, it works fine and completes the update.

What do I need to do to clean this up so it will work without the terminal upgrade???

Thanks!

Donaldt

---

### Post by darkod on 2012-08-30
dist-upgrade is to upgrade to a newer release, not to update the current one.

To update in terminal:
```
sudo apt-get update
sudo apt-get upgrade
```

Does that help or at least shows you with which packages it has a problem?

---

### Post by nariub on 2012-08-30
apt-get update
   checks the repos

apt-get upgrade
   installs the updates it found in the previous step
   minus the kernels.

apt-get dist-upgrade
   installs any updates -and- kernels it found

update-manager -d
or 
do-release-upgrade -d 
   this will upgrade you from one version to another..

---

### Post by critin on 2012-08-30
> **donaldt said:**
> My update manager will not complete an update.  Even just one or two items.  It stops 1/2 way and locks up the computer.

If I go to terminal before I use update manager and launch:  

[sudo apt-get update && sudo apt-get dist-upgrade]

Then launch update manager, it works fine and completes the update.

What do I need to do to clean this up so it will work without the terminal upgrade???

Thanks!

Donaldt

The terminal is quicker.  I used to dread it but find the advisors were correct, it's easier.  I use this for standard updates.  

sudo apt-get update && sudo apt-get upgrade

It's only one line, one entry.

The update manager may need an update.  Does it give an error?

---

### Post by donaldt on 2012-08-30
OK.  I just did your one line update via the terminal.  It is exactly what I have been doing to get update manager to work, as noted in my message.

But I still have the red icon that says ten important security updates are available via update manager.  Update manager will work now and complete all the updates.  So, I just tried it, and sure enough, it worked fine and now there are no more updates.  

The next batch of updates I get will require the same process.  If I launch update manager and don't do the terminal update first, it will once again hang half way through the process.

I'm using Ubuntu 12.04 and upgraded about 4 months ago.  Any insight anyone can provide will be very much appreciated.

Thanks!

donaldt

---

