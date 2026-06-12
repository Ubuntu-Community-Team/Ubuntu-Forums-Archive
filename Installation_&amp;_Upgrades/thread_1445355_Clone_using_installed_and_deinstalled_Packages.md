---
title: "Clone using installed and deinstalled Packages"
date: 2010-04-02
forum: Installation &amp; Upgrades
---

### Post by LeFish on 2010-04-02
Hi!

I was curious if there is any way to clone my system by simply writing into a file which packages are installed AND deinstalled on the source system.

The reason is that I configured a system which fits me just right (I installed some additional packages and removed some standard packages like OpenOffice...) and was wanting to back it up - even for a newer Ubuntu-Version.

Most of the changes are already gone in /var/log/dpkg.log... so this option does not exist...

Does anyone know where Synaptic stores the information which package is installed and which is not? It is possible to view those packages by applying a filter, so this information gotta be somewhere =)

Thanks for your help!

LeFish

---

### Post by ajgreeny on 2010-04-02
You can either:-

CREATE A LIST OF INSTALLED PACKAGES
```
sudo dpkg --get-selections > installed-software
```
will list everything on the computer and if you want to use the list to reinstall this software on a fresh ubuntu setup,
```
sudo dpkg --set-selections < installed-software
```
followed by:-
```
sudo apt-get dselect-upgrade
```

Or:-

```
sudo -i
cd /root/.synaptic/log
cat /root/.synaptic/log/*.log > /home/andrew/dpkg-$(date +%F).log
```

Will produce file called dpkg-2010-02-11.log (dpkg-year-month-day.log) in home listing everything that has been done with synaptic, or update-manager, but not, I think anything that you've done with apt-get

---

### Post by LeFish on 2010-04-02
hi!

Thanks for your reply!

I have a list now of all installed packages - that's a very good start...

The thing is that I also need a list of all packages that are NOT installed, so that they are removed, if installed by default (i.e. OpenOffice...) - The problem is that i removed such packages as OpenOffice with apt-get so your last option does not work in my case...

Is there any way to get such a list?


Thank you so much!

LeFish

---

### Post by LeFish on 2010-04-02
Hi!

I think I found an answer on my question myself

Using this selfwritten script I get two lists, importable to Synaptic

```
#!/bin/bash

for i in `dpkg -l "*" | egrep -oh '^ii  [[:graph:]]*' | cut -b 5-`; do
	echo -e "$i\t\tinstall" >> ./install.txt
done

for i in `dpkg -l "*" | egrep -oh '^un  [[:graph:]]*' | cut -b 5-`; do
	echo -e "$i\t\tdeinstall" >> ./deinstall.txt
done
```

What do you guys say?

LeFish

---

