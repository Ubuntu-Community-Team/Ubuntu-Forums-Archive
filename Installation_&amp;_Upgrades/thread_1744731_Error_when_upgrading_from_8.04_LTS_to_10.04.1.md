---
title: "Error when upgrading from 8.04 LTS to 10.04.1"
date: 2011-04-30
forum: Installation &amp; Upgrades
---

### Post by redmulberry on 2011-04-30
I'm attempting to upgrade from 8.04 to 10.04.1 (using upgrade manager).

I'm getting the following error message:
> Could not install the upgrades

Error during commit

'E: couldn't configure pre-depend jre for openoffice.org-writer2latex, probably a dependency cycle.'

Restoring original system state.According to Update Manager my system is up-to-date.

Any ideas on how I can fix this?

Thanks.

---

### Post by cgh2@cornell.edu on 2011-05-03
Have you found a solution to this problem?  I am seeing the exact same message when I try to do the same upgrade.  If you get an answer, could you post it here?

Thanks,
Caroline Hecht

---

### Post by Hagar Delest on 2011-05-06
Personally, I never upgrade with the soft upgrade. I've 2 partitions dedicated to the root for 2 OSes. That way, I can install the new version in parallel with the former one. If no problem, I keep working on that one before erasing the other partition with the next flavor.

I've experienced some troubles also the only time I've tried the soft upgrade.

---

### Post by terminal*optimist on 2011-06-18
hi

just posted a patchy solution to this problem on another thread: 

[http://ubuntuforums.org/showthread.php?p=10955085#post10955085](http://ubuntuforums.org/showthread.php?p=10955085#post10955085)

my problem seemed to be having an old version of java running independently of openoffice while java6 was sitting in synaptic package manager not installed, or somehow dormant (hence system claimed to be up to date). 

anyway, my computer has upgraded now and is running fine for the mo.

good luck!

---

