---
title: "Update Manager wants &quot;Partial Distribution Upgrade&quot; but Synaptic OK for Updates?"
date: 2007-08-12
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2007-08-12
OK, had an error in Update Manager yesterday - being the "Dynamic MMap ran out of room" error that is fixed by adding/changing "APT::Cache-Limit 33554432;" in /etc/apt/apt.conf. So now it loads, but keeps going on about Partial Distribution Upgrade coz either some things aren't installed properly, or yadayadayada. Some of the things in the list simply can't be deselected, and we're talking some basic, non-system type stuff like updates to Gimp. In the end I got it to install 11 of 15, but then keeps looping on the rest (though the error it throws up tells me it couldn't get info on a whole lot more packages). So then I thought I'd try Synaptic and mark all upgrades... which apparently isn't any problem, as they are downloading now without complaint of any sort.

If Synaptic can get the updates - so there is nothing wrong there or with the installed packages - and Update Manager was broken yesterday - is there still something I should be doing to get Update Manager back on track?

---

### Post by jmate24 on 2007-08-12
Update Manager Wants "Partial Distribution Upgrades"

Try reinstalling Update Manager in Synaptic...

---

