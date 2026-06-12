---
title: "Will drivers be upgraded when kernel upgrading?"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by ohshout on 2013-03-02
Hi everyone,

I kinda of wonder will drivers be upgraded when kernel upgrading.
Well, my guess is they will. Otherwise how can they still be loaded into new kernel successfully, because maybe some kernel APIs would be changed.
Am I right or wrong?

Thanks!

---

### Post by MAFoElffen on 2013-03-02
You are right --and-- wrong...

The modules included with the kernel are replaced with that kernel... Some other modules that had proprietary licensing, such as drivers for nVidia, and AMD/ATI video, some newtork cards and such...are not. Sometimes that is not a problem because the kernel change affect other areas... but sometimes it does affect those.  In those kernel update problems, if you remove and then install the same driver package, it will compile the driver on the new kernel and everything should work again. At least, that is the "logic" to that. That is the reason why some of those drivers stop working after a kernel upgrade.

Of course. since Linux itself tries to adapt and cover a wide range of hardware possibilities, it cannot expect to forecast all those different combinations... A logical improvement to the kernel upgrade process (as least my thoughts) would be to check which local modules are loaded on the upgraded system and to see if "other" loaded modules should be recompiled on that kernel. Of course, that would be more complicated and slow that process down. Of course, that might also fall back to the licensing thing...

---

### Post by QIII on 2013-03-02
In the specific case of the ATI drivers -- *when installed from the repository -- *the driver will be reinstalled during normal updates.  If the driver is installed from the ATI website, it is best to uninstall it first when you see that a kernel update is coming, do  your updates and then reinstall the driver.  Some other drivers behave similarly.

---

### Post by MAFoElffen on 2013-03-02
> **QIII said:**
> In the specific case of the ATI drivers -- *when installed from the repository -- *the driver will be reinstalled during normal updates.  If the driver is installed from the ATI website, it is best to uninstall it first when you see that a kernel update is coming, do  your updates and then reinstall the driver.  Some other drivers behave similarly.
Just FYI-

NVidia packaged .deb drivers are also.  That is- On package ATI and Nvidia packaged drivers- Yes, when there is a "version" update in those packaged driver "versions" in the restricted repo, they will update to the new version package through those repo's through the normal update/upgrade process.

But on "Linux kernel updates," it does not automatically re-install and recompile those already installed third-party restricted driver packages on that new kernel. As a user of high-end graphics hardware (both ATI and NVidia), I just expect and accept this as something that might happen... and might need to be resolved.

Yes, manually installed binary drivers are not automatically "version" updated. This may be good -or- bad. You can might also think of that as manual version control. On binaries, both NVidia and AMD/ATI also have manually invoked facilities within their proprietary installer's to check for updates, install driver upgrades or to force a re-compile of the same version driver... I lot of users aren't even aware of those seemingly hidden or obscurely documented functions.

On whether go packaged or binary... personal preference or hardware dependent. Pros and cons for each... But discussion would be off-topic of this thread.

Specifically, sometimes a normal Linux kernel upgrade *may* break an installed driver, immaterial whether it was installed via a package or manually from third-party binaries. That is a launchpad known upgrade process issue.

---

### Post by ohshout on 2013-03-02
Thanks, friends!

This is what I learn from this thread. Non-proprietary drivers are upgraded. And I found they are located under /lib/modules. When a kernel upgrades, drivers there will be replaced. As for proprietary drivers, they may need to be upgraded manually.

---

