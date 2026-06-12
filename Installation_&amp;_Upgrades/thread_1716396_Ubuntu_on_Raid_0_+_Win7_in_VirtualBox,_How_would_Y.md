---
title: "Ubuntu on Raid 0 + Win7 in VirtualBox, How would YOU do it?"
date: 2011-03-28
forum: Installation &amp; Upgrades
---

### Post by fisaacs on 2011-03-28
I'm waiting on a 2TB drive to come in so I can repurpose my gaming rig for Ubuntu. (Ok, its still going to be a gaming rig but I want to do 90% of my work/gaming in Linux)  I'm thinking that rather than dual-booting I want to run the windows side of the house from a VM via Virtualbox.

Ubuntu runs fine with my hardware atm (have 10.10 installed on a secondary sata drive) and recognizes the RAID array that windows is currently installed on (gigabyte 870A-UD3 motherboard, I think Ubuntu's using fakeRAID to mount and view the drive, not very knowledgeable on raid and had the system built for me, but I know I'm using the gigabyte on-chip bios configuration for the raid)

I'd like to know:

1) if anyone knows of a good guide for dealing with this particular RAID controller beyond my owner's manual.  (I read that 10.10 fakeRAID pretty much sets itself up)

2) should my win7 partition for the VM (I'd like it to be a dedicated partition so that I can boot into it if I have to do something in windows that Virtualbox can't handle) be on the Raid Array or the 2TB WD Caviar Green (low performance/power consumption drive)?

3. since I have a 2tb raid 0 array and a 2tb drive coming in, can I setup raid to mirror the contents of the 2 raid 0 drives onto the WD Caviar drive or do they all 3 have to be identical drives. (I think the other 2 are 1TB WD Caviar Black drives)

4. Any particular advice on partitioning?  I was just thinking of /, /home and swap being separate on the raid but otherwise leaving the standalone drive as one big partition or splitting between windows partition and an otherwise large storage space.

---

### Post by n1unqn on 2011-03-28
Beyond running Damn Small Linux from inside windows I have little experience of Virtual Machines but suspect they would be much slower than a dual boot and running solo.

I do have some experience of raid though. If it's hardware RAID it's taken care of in the BIOS setup and formatting stage and is transparent to the OS.

If you try to mirror (raid 1) you raid 0 (2 drives striped) with a single drive it will slow down the raid 0 to the speed of the large single drive!

If you want to do this properly you need 4 drives 1Tb drives you make two raid zeros and then mirror the raid zeros and that's called raid 10 (or raid 1+0)

With 3 drives you would be better going with raid 5 it will give the mix of speed and redundency you want and leave a 1Tb partition over.

(Raid 5[1Tb drive 0/0] + [1Tb drive 1/0] + [1Tb drive 2/0]) leaving [Normal 1Tb drive 2/1]

If one of the raid 5 drives dies it will keep your system running
(unlike raid 0 which may require you to swap the hard drive over or edit the boot strap) 
and when you replace the bad drive it automatically rebuilds (again rebuilding a mirror is a pain possibly requiring system downtime).

---

