---
title: "new laptop,  reinstall everything anew?"
date: 2007-02-25
forum: Installation &amp; Upgrades
---

### Post by flygin on 2007-02-25
What can you do when you change hardware and do *not* want to reinstall everything by hand?

Is there a way to "clone" just the content of your old hard drive, i.e. the personal files AND the installed programs so that you will have the identical settings on a new machine?

Of course you can copy the conf files but thats not the question. I had about 2000 packages installed on my previous laptop. That means I have to install about 1000 ?!@ 

the script should import all the old settings and copy as much as possible from the old hard disk (speed), fetch updates from the net when needed and so on. In the end you will have all the programs that you had before, the passwd files in your browsers, the add-ons and extentions ... 

if you change architecture it will have to fetch more, of course...


the shellscript below will use lots of bandwith ... and it is not optimized.

#!/bin/bash
# installs all programs that are not found in old.dpkg.txt (output of dpkg -l in old system)
dpkg -l > dpkg.txt

for u in `cat old.dpkg.txt `
do

if ! grep "$u" dpkg.txt >/dev/null 
then
	apt-get install "$u"
fi
done

---

### Post by gasull on 2007-02-26
[How to back up and restore your Ubuntu machine]("http://www.arsgeek.com/?p=637").

HTH.

---

