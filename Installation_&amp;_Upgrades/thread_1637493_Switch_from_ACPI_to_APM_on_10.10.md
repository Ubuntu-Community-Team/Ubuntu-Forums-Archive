---
title: "Switch from ACPI to APM on 10.10"
date: 2010-12-04
forum: Installation &amp; Upgrades
---

### Post by Kurtismonger on 2010-12-04
I've installed 10.10 on a laptop and everything is working except for suspend. The laptop will go into suspend, but will not wake up. I have to hard reboot to recover. From my research it appears to have something to do with ACPI and I would like to switch to APM. However all the instructions I found for doing this seem to apply to older versions of Ubuntu before the switch to Grub2 so there is no menu.lst file to make changes to. So I'm looking to understand how to switch to APM in 10.10?

---

### Post by Steve Main on 2011-01-12
Hi. Check out [bug #642091]("https://bugs.launchpad.net/bugs/642091") at bugs.launchpad.net and refer to comment #0, and #45 for a summary with a few different workarounds to choose from, including the instructions you are seeking (however, I found the first workaround easier than replacing ACPI). 
Keep in mind, you may have to redo the workaround after an update.
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/642091)

If #642091 is the same problem you are having and the workaround solves your problem, and if you are not using an Acer Aspire One 721 or a Dell Mini 1012, please add a post to that bug listing your machine.

Hope that helps!
--Steve

---

