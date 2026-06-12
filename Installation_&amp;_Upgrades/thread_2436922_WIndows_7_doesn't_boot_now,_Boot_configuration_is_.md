---
title: "WIndows 7 doesn't boot now, Boot configuration is corrupt"
date: 2020-02-15
forum: Installation &amp; Upgrades
---

### Post by rva1945 on 2020-02-15
This might be caused by an improper shutdown.

System Repair says it can't fix the problems, in the details I see

Boot configuration is corrupt.
Repair action: partition table repair

Before trying to fix it running chkdsk at the command prompt and ruin Ubuntu, is there something I can do from Ubuntu?

Thanks

---

### Post by yancek on 2020-02-15
I doubt there is anything you can do from Ubuntu but you might try downloading and running boot repair using the 2nd option at the site below to obtain it using the ppa.  Make certain you only run it with the Create BootInfo Summary option and post the link you get when it finishes here.  Someone may be able to make a suggestion with that information.

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

I'd run chkdsk from windows since it is a windows problem.  More info is needed.

---

