---
title: "Remote downgrade from 18.04.4 to 18.04.2"
date: 2020-06-24
forum: Installation &amp; Upgrades
---

### Post by brasilino on 2020-06-24
Hello All:

Due to a very specific scenario, I need to downgrade a system from Ubuntu 18.04.4 LTS to 18.04.2 LTS or 18.04.1 LTS. That has to do with a proprietary software. They only support if you follow **precisely** the installation instructions.

I've found some information out there on rolling back from 19.04 to 18.04 or from 18.04 to 16.04 which weren't very helpful.

Also, please consider** I have remote access** (ssh or VNC) to the system. So I'm looking for some instructions that I can run on the shell and the reboot.

Any help? Any pointers?

Thanks a lot in advance!
Lucas

---

### Post by CelticWarrior on 2020-06-24
There's NO scenario where you would do what you think you must due to that proprietary software. And it's not really pdoable unless with a reinstallation and then not updating the system which is something you should do.

Worst case scenario, the specific software you're trying to install requires one specific kernel version or some up to a specific kernel version. So, if such kernel is still installed you can boot with it and then install the software. If said kernel has been removed previously you may need to reinstall it. In any case this is directly related to different updates points, the number after the LTS release number.

---

### Post by brasilino on 2020-06-24
Hello!

Thanks for the reply. I have already downgraded kernel from 5.3.0 to 4.15.0 but for some reason it didn't boot (I wasn't there physically, a co-worker just told me that). I'll then go after reinstalling the system.

Best,
Lucas

---

