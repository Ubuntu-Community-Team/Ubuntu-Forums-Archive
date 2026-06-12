---
title: "everytime i check for updates i get a partial update"
date: 2009-10-06
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by joshuapbell on 2009-10-06
is this normal or is there something up with my machine, this is a fresh install, I have been told to avoid partial upgrades, anyone else getting these?

---

### Post by nhasian on 2009-10-06
personally i like to do a backup with clonezilla before applying distribution updates.  most of the time dist-upgrade works fine but sometimes it can break your system if the updates are not complete.  

i expect there to be a lot of updates between the beta and release candidate.

---

### Post by kansasnoob on 2009-10-06
> **joshuapbell said:**
> is this normal or is there something up with my machine, this is a fresh install, I have been told to avoid partial upgrades, anyone else getting these?

Everytime?

For how many days?

---

### Post by joshuapbell on 2009-10-06
> **kansasnoob said:**
> Everytime?

For how many days?

I just installed it today, but i had the same issue with the alpha version, probably for a week...

---

### Post by mikeyrb on 2009-10-06
Probably a package dependency can't yet be met because not all of the packages can be updated at exactly the same time.  If you give it some time, it will likely resolve.  If not, I would try using synaptic and mark all upgrades.  It will tell you what the conflict is when trying to apply all upgrades, which the upgrade manager will not.

---

### Post by ranch hand on 2009-10-06
Go to synaptic.  Click on status (bottom left of page).  Click on "installed upgradable".

Before going further Click on Settings>Preferences (upper left of page).  Should open in the general tab.  Make sure that "system upgrade" is marked "Smart Upgrade" (this should be default).

Click on "mark all upgrades".  Click on "apply".  This will let the FUN begin.

---

### Post by Longinus00 on 2009-10-07
I just apt-get upgrade and then hit NO when it asks me if I want to go ahead and upgrade. It should tell you what packages are being held back and from there you can try to work out if it's because a dependency is broken or if it wants to replace a library with a different version.

---

### Post by hanzomon4 on 2009-10-07
I did the partial... it was just removing one package, installing some new packages, and upgrading everything else.

---

### Post by blakamin on 2009-10-07
I currently have 5 packages held back... for the last 12-24 hours.
```

  evolution-plugins linux-generic linux-headers-generic
  linux-image-generic ubuntu-desktop
```
Definitely not running updates until these get sorted.

---

### Post by rex4u on 2009-10-07
Hi,
I would rather suggest that u give some time between updates. May be 3-4 days or even a week.

---

### Post by taavikko on 2009-10-07
> **blakamin said:**
> I currently have 5 packages held back... for the last 12-24 hours.
```

  evolution-plugins linux-generic linux-headers-generic
  linux-image-generic ubuntu-desktop
```
Definitely not running updates until these get sorted.

They're held back since they need new packages installed.
Use "sudo aptitude full-upgrade" to upgrade, if in doubt, paste the output here.

---

### Post by jocko on 2009-10-07
> **blakamin said:**
> I currently have 5 packages held back... for the last 12-24 hours.
```

  evolution-plugins linux-generic linux-headers-generic
  linux-image-generic ubuntu-desktop
```Definitely not running updates until these get sorted.
There is nothing that will "get sorted". The reason they are not automatically updated is that they need to install additional packages (the "linux-" packages wants to install a new kernel and new kernel headers, ubuntu-desktop wants to install a new dependency. not sure about evolution-plugins). Just install those packages manually:
```
sudo apt-get install evolution-plugins linux-generic linux-headers-generic linux-image-generic ubuntu-desktop
```
Just check what apt-get will do. Sometimes it just wants to install some new packages which are added as new dependencies to some package. Other times a new package will conflict with another package, which will force apt-get to try to solve it by removing that other package. Sometimes this is the intended behaviour but other times it's because the dependencies can not be met yet. So just think twice when apt-get wants to remove anything.

---

### Post by rex4u on 2009-10-07
> **jocko said:**
> there is nothing that will "get sorted". The reason they are not automatically updated is that they need to install additional packages (the "linux-" packages wants to install a new kernel and new kernel headers, ubuntu-desktop wants to install a new dependency. Not sure about evolution-plugins). Just install those packages manually:
```
sudo apt-get install evolution-plugins linux-generic linux-headers-generic linux-image-generic ubuntu-desktop
```just check what apt-get will do. Sometimes it just wants to install some new packages which are added as new dependencies to some package. Other times a new package will conflict with another package, which will force apt-get to try to solve it by removing that other package. Sometimes this is the intended behaviour but other times it's because the dependencies can not be met yet. So just think twice when apt-get wants to remove anything.

+1

---

### Post by Longinus00 on 2009-10-07
> **jocko said:**
> There is nothing that will "get sorted". The reason they are not automatically updated is that they need to install additional packages (the "linux-" packages wants to install a new kernel and new kernel headers, ubuntu-desktop wants to install a new dependency. not sure about evolution-plugins). Just install those packages manually:
```
sudo apt-get install evolution-plugins linux-generic linux-headers-generic linux-image-generic ubuntu-desktop
```
Just check what apt-get will do. Sometimes it just wants to install some new packages which are added as new dependencies to some package. Other times a new package will conflict with another package, which will force apt-get to try to solve it by removing that other package. Sometimes this is the intended behaviour but other times it's because the dependencies can not be met yet. So just think twice when apt-get wants to remove anything.

The first part of your post is not true. Partial upgrades don't happen just because a package wants to install something additional (unless you mean that their additional dependency is unable to be satisfied, in which case installing it manually won't do you a lick of good). I've never had to do a partial upgrade just to pull in the newest kernel update.

---

### Post by mc4man on 2009-10-07
Some (not all) partial updates/upgrades in the update manager are to due the need to **remove and replace **a package which the update manager will not do ( at least here

A few recent ex.'s are where the ubuntu desktop where libgd2-noxpm was removed and replaced by libgd2-xpm before ubuntu desktop was upwhatevered

Another was the name change(s) to what now is software-center.
synaptic handles those fine 

If a package or more is greyed out look up in synaptic to see why or post the name(s) and version(s)

---

