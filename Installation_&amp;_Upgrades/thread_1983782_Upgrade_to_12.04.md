---
title: "Upgrade to 12.04"
date: 2012-05-20
forum: Installation &amp; Upgrades
---

### Post by G0DBR3AK3R on 2012-05-20
I recently upgraded from 11.04 to 11.10 . . . But the installation failed horribly and not one suggested fix solved the issues (the OS booted directly into terminal, showing various errors, and would not bring me even to the basic boot screen). While running 11.04 on my Sony VAIO laptop, my touch-pad and audio did not work whatsoever.
Following the Forum suggestions, I ran an upgrade to 12.04lts directly from the terminal. That also failed, resulting in the same issues that I encountered originally.
After spending 20 straight hours attempting in vain to work through and repair the code in the terminal, I finally opted to revert back to 10.04lts. At that point, I wasn't able to reach even the terminal; my OS crashed entirely, with no apparent hope of recovery.

However . . .

Using UNetBootin, I downloaded a fresh ISO (of 12.04lts) to a 4gig USB in a last desperate attempt to save my system. I booted into the base BIOS screen and selected "Try Ubuntu Without Installing." 12.04 booted up without a single error. I then selected the installation option from the desktop. At that point, I encountered a plethora of errors, and wasn't able to even restart my computer. I performed a hard shut-down (held the power button down for approximately ten seconds), then rebooted in the same fashion.
To my pleasant surprise, 12.04 booted almost flawlessly. I got one error at the boot screen, which I know many users attempting this upgrade have encountered "/dev/mapper/cryptswap1 does not exist or is not ready yet" (or something to that effect) but only on the first boot, and after a minute or so it seemed to figure it out and booted without problems.

If anyone is experiencing nerve-wracking grief that I did while installing this upgrade, I urge you to contact me so that we can, together, work this out for the benefit of all Ubuntu users. Also, I will be glad to explain (as best I can) the details of my struggle and the path to the resolution that I have stumbled across.
DON'T GIVE UP!!!

---

### Post by G0DBR3AK3R on 2012-05-20
>> Also (sorry, forgot this bit) . . . After I FINALLY got it up and running again, my audio and mouse are working perfectly!

---

### Post by ken78724 on 2012-05-20
at reboot/on closing out upgrade, a crash report was detected - one line described it as "ica crashed with the SIGSEGV in the gtk_container_add () Executable Path". An auto report to the lauchpad went out. A note said the matter had closed, whatever that means. 

I elected to examine the issue locally at which Termnal opened and I ran a conf correction that popped up as an alternative. At near the end of that 17 m correction, it crashed again and I came here to get over to launchpad. Not finding how to get there, I posted here. Apologies for coming on a thread with a different type upgrade problem. Ask for any guidance that comes to mind. 

oh yes, on reboot, ubuntu came up in 11.10 and did not go to 12.04 though I believe a full build had been achieved besides this.  Reiterate, I would be grateful to receive guidance that comes to mind. 

ken78724
:popcorn:

my old HP 4000 laser jet printer keeps tripping out after I uninstall and reinstall. and my reboots come up with torn displays and a sys, which is terribly slow or frozen. Been unable to do basic check out of the sys and get work out on this PC. Am heavily burdened and cannot pull this out.

---

### Post by ken78724 on 2012-05-20
Hmmm, well the 12.04 status took after all. But, I could not log out to learn the affects of that process. had to do a control. Alt, Delete to log out. 

no problem logging in to this account. speed is good. 

:popcorn:

---

### Post by ken78724 on 2012-05-20
Logged out again. This was the 4th shut down, in which I could not get the icon to show upl I did not find it when I did a find "Shut down search". Had to do it with control, alt delete 

and on logging back in, It was apparent I have lost the Kubuntu status as there is nothing mentioned on the monitor .. this 4th reboot.

---

### Post by ken78724 on 2012-05-21
Still have a crash report indicated at this time as mentioned above, the instant the upgrade alleged the upgrade was complete. 

Doing solely composition work the program performs. But Libre Officer 3.4 does not make my printer print.

---

### Post by ken78724 on 2012-06-02
Have a Slower OS after Upgrade from 11.04 to 12.04 LTS
Still see "crash report detected". And, still get a wragged skin just before login. Can't find a correction even with three efforts at updating.

Analyzed my network on Terminal as of 6-2-12 9:30 PM

ken@kenpc:~$ lspci -nnk | grep -iA2 net
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
Subsystem: ASUSTeK Computer Inc. Device [1043:8234]
Kernel driver in use: forcedeth


Fast I can I am backing up to cloud so I may do a new install.
__________________
Mirus P5GC-MX with 750 giB HD; Linux User 470205 since 2002; Get a Linux User # @ [http://counter.li.org](http://counter.li.org)

---

