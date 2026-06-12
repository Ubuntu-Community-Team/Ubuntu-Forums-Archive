---
title: "Are there problems if Ubuntu is not rebooted after kernel updates?"
date: 2013-06-11
forum: Installation &amp; Upgrades
---

### Post by giordan on 2013-06-11
I'm working through ssh on a remote machine running Ubuntu 12.04.2 that I use to run a lot of simulations.
The administrator of this machine has installed the last updates and the machine requires a reboot now. At the moment I'm the only user of that machine and I asked the administrator to reboot it since I'm not running simulations in these days, but even after a lot of solicitations he seems doesn't want to reboot it (he simply doesn't reply to my mails :confused:).
I cannot reboot it by myself since to connect that machine to the local network I need his credentials.
So it's a week that the machine is running with a warning message saying a reboot is required.
Are there problems if I continue to use that machine without rebooting it?

Thanks a lot. ):P

---

### Post by mörgæs on 2013-06-11
Hi, welcome to the fora. 

A reboot is required if for example the kernel is updated. Without a reboot the old kernel is still active, so security bug fixes in the new one are not applied.

---

### Post by giordan on 2013-06-11
> **mörgæs said:**
> A reboot is required if for example the kernel is updated. Without a reboot the old kernel is still active, so security bug fixes in the new one are not applied.

Thank you for your welcome. :)

Except the fact that bug fixes are not applied, are there other "practical" problems or the OS has the same reliability and performances as it would be after the reboot?

---

### Post by grahammechanical on 2013-06-11
The message says "for the updates to take effect." I would not worry about it. After all it is his problem. I doubt very much if the machine will be affected by malware in the mean time. And if it is infected you can rightly blame the administrator for his negligence. He may have a routine where he schedules the machine to be rebooted as part of regular maintenance. But then these machines should be set to update monthly or something like that so that he knows when any updates are being run and when he needs to check to see if a reboot is required.

Regards.

---

### Post by deadflowr on 2013-06-11
> **giordan said:**
>  are there other "practical" problems or the OS has the same reliability and performances as it would be after the reboot?

That can only be determined after a reboot.
You never know what might happen with an upgrade, though most times things perform the same, if not better.

I've held off restarts here and there, usually when I have something I want to finish, or I just plain forget or ignore the restart prompts.
But it's probably best to restart as quick as possible so any problems that may arise can be dealt with faster.

---

### Post by mörgæs on 2013-06-11
> **giordan said:**
> 

Except the fact that bug fixes are not applied...

Applying bug fixes as soon as possible should be first priority for everyone taking care of a server.

---

### Post by giordan on 2013-06-12
Thanks a lot to everybody.
I know it is his fault if something bad happens, however I was just afraid by possible reliability problems that would affect my simulations (if a run a simulation for two weeks and then unexpectedly the OS crashes for the missed reboot would not be much fun).
Nevertheless, from your comments I understand that the OS can continue to "normally" run even if not rebooted. ;)

Thanks!

---

