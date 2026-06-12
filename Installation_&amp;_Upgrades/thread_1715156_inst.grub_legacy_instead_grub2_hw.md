---
title: "inst.grub legacy instead grub2 hw?"
date: 2011-03-26
forum: Installation &amp; Upgrades
---

### Post by ottosykora on 2011-03-26
I need to ninstall the grub into the root partition and not into the mbr.

From the instruction during work on grub2 I found that this seems not to work properly with grub2, only grub legacy.

How can I install grub legacy into the root partition?

Tried to install ubuntu 10.04, then uninstall grub2 and install grub legacy from repository, but this seems not to work. Have performed grub update, this did work, but the ubuntu will not boot this way, it still seems to beleive the grub2 is around.

Any help with that pls

---

### Post by oldfred on 2011-03-26
You can force grub2 into a partition. The issue is that grub2 is larger and then has to use blocklists which are hard coded addresses. If then the grub files are moved by an update or even a fsck the address may change & you have to reinstall the boot loader.

How will you boot as computers only boot from the MBR. You will have to chainload from the MBR to the PBR. I used to do that a lot with old grub legacy but grub2 is so good at finding other installs I stopped using grub legacy.

HowTo: Revert from grub2 to Legacy Grub or grub to grub2 kansasnoob
[http://ubuntuforums.org/showthread.php?t=1298932](http://ubuntuforums.org/showthread.php?t=1298932)

Revert from grub2 to legacy grub - not a tutorial! 
[http://ubuntuforums.org/showthread.php?t=1247994](http://ubuntuforums.org/showthread.php?t=1247994)

---

### Post by ottosykora on 2011-03-26
I do not want to install any grub into the mbr on this particular machine. I use other bootmanager. I need botmanager which is deinstallable so any grub in mbr on this machine is not possible.

However I need to boot the ubuntu with something. As grub2 is for that purpose not very useful, tried today twice and everytime on an upgrade of ubuntu it fails completely, I am up to installing legacy grub to the pbr.

But earlier it was possible with boot cd of older linux, now I have only 8.04 and this is of little help, as it does not recognise network card of the computer and so any dwonloads are not possible.

So yes I forced grub2 to partition, but it did fail on next update.

---

### Post by ottosykora on 2011-03-26
OK oldfred, it is done!

Many thanks for the first link particularly. I reinstalled the 10.04 with the grub2 into root, then when it started I carried out all the ops to purge and reinstall the grub (0.97 this time) and after some tries it now works, my 3rd party bootmanager find it imediately and all seems to work as expected. 
Now all updates etc are runnig, so hope all will be fine after.

Hope grub 0.97 will still stay in the repos for long time since it seems that there still no way without it.
The grub2 is too fragile and lilo is tied to the last kernel too, so there is no alternative to legacy grub if it has to go to the PBR.

Particularly when using number of installations on one drive, separate grub partitions has to be used and then each installation has to have its own bootloader, if grub2 is too fragile for that?

---

### Post by oldfred on 2011-03-26
Actually grub2 is much better. It finds the kernels and directly boots them from all installs in your system. It only chainloads windows as it has part of its boot code in the PBR.

But I have 3 drives & have 3 different grub2's installed. I have old Ubuntu, current Ubuntu & Natty's boot loaders in a MBR. I do have a chainload to the other MBR, so if I miss the f12 to choose which drive I can use grub menu to switch to other drive.

---

### Post by ottosykora on 2011-03-28
yes it can be better for some things, ok, legacy grub will also find other os without problem, but when it goes to more then two or three os on one system, then one has to have bootloaders in each partition and one common bootmanager partition. This can be done with grub2 sure, but when it is also used as bootloader in the pbr, it seems to fail.
It might be great if it is just used to arrange dual boot, started from mbr and sitting in one linux partition. But it seems to fail if used as bootloader only and as in my case does not survive upgrades (see many threads in the forum).
If used as bootloader only in the partition, it does not matter if it finds this and that OS, it has to start the only one, as linux is delivered without any means to be started otherwise.
The messages grub2 produces during install to pbr do clearly state, that it should not be used this way and might fail. So as the grub2 does not provide any alternative (yet?) we have to stick with grub legacy for those tasks apparently.

---

