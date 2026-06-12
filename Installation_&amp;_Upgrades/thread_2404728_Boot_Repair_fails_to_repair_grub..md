---
title: "Boot Repair fails to repair grub."
date: 2018-10-27
forum: Installation &amp; Upgrades
---

### Post by azjezz on 2018-10-27
i installed ubuntu about 2 months ago, this is my first time doing it so im not sure if i did it correctly the first time, but everything worked fine.

sometimes ubuntu fails to boot so i have to  run fsck manually.

yesterday the laptop shutdown and i was unable to boot it, getting a 'failed to read sector ...' error and it boots into grub terminal.
 
after doing some research i found that i can be fixed with boot-repair, so i made a boot repair disk.
after booting to it, it run successfully and generated the following url :
[http://paste.ubuntu.com/p/X6RxXndnVK/](http://paste.ubuntu.com/p/X6RxXndnVK/)

after restarting, it failed to boot again with the same error. 

now i tried to re-install ubuntu but the installation dialogue is not responding after choosing the WI-FI network. 

i my disk dying ? is it possible to fix this or do i just get a new hard driver ?

---

### Post by oldfred on 2018-10-27
Your unusual configuration may be contributing to issues.
It looks like you have an old MBR partitioned drive that used to boot Windows in BIOS mode.
And then you forced an UEFI install of Ubuntu.
Normally UEFI installs use gpt partitioning.
Windows only boots in BIOS mode from MBR, and only in UEFI mode from gpt.

Using Disks app and icon in upper right corner is Smart Status. It can run lots of tests, but all I know is if drive is good or bad as its summary.

---

### Post by azjezz on 2018-10-28
i was unable to do anything, at the end i was able to reinstall Ubuntu using OEM installation, it took about 6 hours for the dialogue to move to the next step, so i'm not sure if the normal installation would have worked if i waited that long, however i formatted the disk and now its working smoothly.

---

