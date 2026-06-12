---
title: "Unable to update. Not enough space."
date: 2015-12-23
forum: Installation &amp; Upgrades
---

### Post by PavelChehoff on 2015-12-23
Hi all. New problem for me so not sure how to solve it. Currently installed ubuntustudio and it has installed perefectly fine but now I am unable to update it. 
Gives me such message: 
> The upgrade needs a total of 133 M free space on disk '/boot'. Please free at least an additional 11.0 M of disk space on '/boot'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.

Tried to clean still no good. I guess I need to do something with partition but dont want to mess with it as not sure.


 Could someone give an advice with what to do? Thanks a lot

---

### Post by howefield on 2015-12-23
Try running

```
sudo apt-get autoremove
```

which may clear out some old and unused kernels from you /boot partition, if that fails it simply means that you will have to manually remove them but give the autoremove command a go first.

---

### Post by PavelChehoff on 2015-12-23
It has removed some packages but still not enough space. Is there any way to change boot partition size without destroying the whole system?

---

### Post by ian-weisser on 2015-12-23
> **howefield said:**
> if that fails it simply means that you will have to manually remove them

If autoremove didn't clear enough space, then follow the second half of Howefield's advice.
Changing your partitions won't help much, and is uneccessary for such a trivial fix.
Usually removing just *one* older kernel using dpkg provides apt enough space to work properly.
After apt is working properly again, remember to mark your calendar and run autoremove regularly to prevent recurrence.

Congratulations, you seem to have been bitten by [LP #1357093]("https://bugs.launchpad.net/bugs/1357093"). If you think so, please click on the 'Does this bug affect you?' link at the top of the bug report.

---

