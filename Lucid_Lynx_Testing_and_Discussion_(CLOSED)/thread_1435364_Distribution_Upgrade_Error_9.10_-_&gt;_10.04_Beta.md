---
title: "Distribution Upgrade Error 9.10 - &gt; 10.04 Beta"
date: 2010-03-21
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by puzzler995 on 2010-03-21
I had tried Lucid Alpha 2 and had some trouble, so I reverted to 9.10, and now that Beta 1 is out I would like to give it another go.
I used 'upgrade-manager -d' and clicked upgrade. The first thing I noticed was in the Release notes it still noted it was an "ALPHA release". 
[QUOTE=Release Notes]= Welcome to the Ubuntu 'Lucid Lynx' development release =

*** 
This is still a ALPHA release.
Do not install it on production machines.  
***
[/QUOTE]

not thinking much of it, I clicked Upgrade again and It started to run. It goes through the part where it tells me the 3rd party Repos are disabled and it then gets the software sources, tells me now unsupported software by Canonical, then calculates the changes. All of the sudden a box appears telling me:
[QUOTE=lucid]
An unresolvable problem occurred while calculating the upgrade:
Trying to install blacklisted version 'openoffice.org-filter-binfilter_1:3.2.0~rc4-1ubuntu1'

 This can be caused by:
 * Upgrading to a pre-release version of Ubuntu
 * Running the current pre-release version of Ubuntu
 * Unofficial software packages not provided by Ubuntu

If none of this applies, then please report this bug against the 'update-manager' package and include the files in /var/log/dist-upgrade/ in the bug report.[/QUOTE]

I have tried this on 3 different days at 3 different times. What is going on???

---

### Post by sdowney717 on 2010-03-21
Easy fix this happened to me.
In karmic, uninstall ALL open office programs, there are lots of them
I used synaptic to list them
Then it will upgrade.
Lucid will have OO installed.

---

### Post by whoop on 2010-03-21
We'll you are upgrading to a pre-release version of ubuntu. Did the upgrade process stop? If not, what is the problem...

---

### Post by puzzler995 on 2010-03-21
> **whoop said:**
> We'll you are upgrading to a pre-release version of ubuntu. Did the upgrade process stop? If not, what is the problem...
Yes it reverted

---

### Post by nanog on 2010-03-22
This is a known bug in *karmic* openoffice that has been fixed in lucid. I suggest you purge openoffice before you upgrade. 

beta == alpha

---

### Post by garvinrick4 on 2010-03-22
Copy and paste this code below to update from karmic to lucid.


sudo sed -i 's/karmic/lucid/g' /etc/apt/sources.list && sudo aptitude update && sudo aptitude dist-upgrade

---

### Post by puzzler995 on 2010-03-23
> **sdowney717 said:**
> Easy fix this happened to me.
In karmic, uninstall ALL open office programs, there are lots of them
I used synaptic to list them
Then it will upgrade.
Lucid will have OO installed.
This worked, thanks. Although I had to manually reinstall OO after

---

