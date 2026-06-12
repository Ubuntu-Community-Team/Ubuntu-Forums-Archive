---
title: "How do I reinstall every package"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by jdsommer on 2007-07-24
After upgrading to Fiesty and then having major errors with suspend, my root partition became very corrupt (but not entirely unusable). I have since run fsck on it, and "repaired" the errors, which is to say that the file system works now, though many of the files do not have the same contents that they used to. (This is evidenced by some libraries not loading, claiming that they are not in ELF format, icons that don't appear, etc.) I would like to force a reinstall of every installed package, but so far I have not been able to figure how to convince apt to do this, short of manually invoking it on every package.

Any suggestions?

Thanks,
Jason

---

### Post by ajgreeny on 2007-07-24
I don't know if this helps, but in the left sidebar of synaptic, in the status section you can see everything that is installed, and could mark all of them for reinstallation.  A bit long-winded, but it may be worth considering.  I'm sure there must be a way of doing it in the command line too, but I don't know how.

---

### Post by dannyboy79 on 2007-07-24
here's a way to list ALL installed apps, then it sounds like you should do a total reformat, reinstall, then use the list you created of installed apps and it will then reisntall everything frmo that list.
Don't forget to save the list of installed apps onto a disk or usb key before you reformat. good luck

[http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html](http://www.cyberciti.biz/tips/linux-get-list-installed-software-reinstallation-restore.html)

---

