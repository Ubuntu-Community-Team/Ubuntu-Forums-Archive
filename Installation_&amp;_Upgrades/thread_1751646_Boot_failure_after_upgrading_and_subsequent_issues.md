---
title: "Boot failure after upgrading and subsequent issues with Plymouth"
date: 2011-05-06
forum: Installation &amp; Upgrades
---

### Post by Qt410x on 2011-05-06
Hi all,

I'm a new member here, and fairly new to Ubuntu, so I apologize if I haven't done enough research on either my problem or the forum rules, but the recovery of this system is fairly time-sensitive. 

NOTE: This computer (a Toshiba L650 Satellite, if it matters) belongs to my girlfriend, and so I give you her report of what happened.

She was running a script in R (which was supposed to take a regression from R and output to LaTeX) but it failed, causing a "massive core dump" and shut down her computer. She rebooted, performed a recovery, but her system was still running slowly so she decided to upgrade to Narwhal. At this point she received an error message saying that the upgrade was interrupted by an eclipse package, and it failed, saying that her (disk? she couldn't remember) "may not be recoverable." 

Now, when I try to boot from GRUB, from any kernel listed ($22, $25, $27, and $28 ), I get the following error message:

```
Plymouth splash main process killed by TERM signal
udevtrigger main process (453) terminated with status 1
udevtrigger post-stop process (458) terminated with status 1
The disk drive for / is not ready or present, S for Skip, M for manual recovery
```

If I select skip it repeats the same thing with /tmp, and then returns mountall: Plymouth command failed, mountall: disconnected from plymouth and then hangs. 

I booted from a LiveCD, and it worked (including the splash screen). I then scanned the hard drive with smartctl, and looked at it in Gparted. Nothing seemed amiss. I could open files stored on the hard drive from the LiveCD, so I think there is something wrong with the boot process but I don't know how to fix it. One idea I've got is to run Super GRUB Disk and see if that fixes my boot problems. 

Thank you for reading this far, and thank you in advance for any advice you might have! Let me know if you need any more information, I'll be checking for replies to this thread for the next few hours.

---

### Post by mörgæs on 2011-05-07
There is some advice here which might help you:
[http://ubuntuforums.org/showthread.php?t=1580857](http://ubuntuforums.org/showthread.php?t=1580857)

---

