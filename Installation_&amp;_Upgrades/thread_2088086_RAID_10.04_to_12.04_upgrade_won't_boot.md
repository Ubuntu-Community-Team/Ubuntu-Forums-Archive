---
title: "RAID 10.04 to 12.04 upgrade won't boot"
date: 2012-11-25
forum: Installation &amp; Upgrades
---

### Post by balak on 2012-11-25
I am in this mess right now :( Can one of you guys help me out?

I have a 30GB SSD drive that has the OS (/ partition) and
2 2TB hard drives in RAID0 that have the other partitions (/home /data etc).

I set the RAID up in ubuntu 10.04, upgraded through each of the intermediate versions to 12.04 sometime in june/july. I didn't encounter this race condition till today - though boot used to take a long time after the upgrade. 

Right now, I cannot get it to boot at all. The system doesn't follow bootdegraded=true in the boot command line option. I am really stuck.

So far, I have tried dangriffin's fix in comment #18 through a live cd, chrooting and doing update-initramfs. Still gets to the degraded prompt and gets stuck there.

Also tried setting BOOT_DEGRADED=true in the mdadm file as suggested by somebody else and updating initramfs through live-cd. In this case, it gets stuck just 1-2 steps after noting the degraded raid. 

How do I get the system to boot again?

Thanks in advance.

---

### Post by oldos2er on 2012-11-25
Post moved to its own thread.

Just FYI for next time, you can upgrade directly from LTS to LTS.

---

### Post by darkod on 2012-11-25
Was you array made up of disks (like /dev/sdb and /dev/sdc for example), or partitions (like /dev/sdb1 and /dev/sdc1) ?

Also, can this attempt to assemble it?
sudo mdadm --assemble --scan

You are aware that raid0 doesn't offer any redundancy, right? If from what ever reason one disk failed, all is gone. And boot degraded won't help with raid0, as far as I know. You can't boot a raid0 array degraded.

Another issue was that you actually did 4 upgrades in a row to get from 10.04 to 12.04 when you could have done only one, from LTS to LTS. Doing many upgrades in a row is always asking for trouble, same like running raid0.

---

### Post by Wim Sturkenboom on 2012-11-25
> **oldos2er said:**
> Post moved to its own thread.
Can you please provide a link to the original post; as this is now split off, a reference to post #18 does not make sense.

---

