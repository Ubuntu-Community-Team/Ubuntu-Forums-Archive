---
title: "Migrate Software RAID"
date: 2008-09-17
forum: Installation &amp; Upgrades
---

### Post by jnusa on 2008-09-17
Hi

I'm looking to migrate from EAR OS to MythBuntu. I've optoined to not invest in a new hw based raid controller in my new system, to keep cost/power consumption at a minimum. However, now I need to migrate my current RAID5 (5xHD's) raid to the new operating system (OS on seperate HD). Is this possible by using MDADM and can anyone point me to a good tutorial/description (besides man)? 
A quick follow-up question: If migration is not possible - could any one recommend a hardware based raid controller (PCI-e, 6-8 ports) which is 100% supported by Ubuntu and supports spindown (including management software!)? I've looked at Areca cards, which has MAID (spindown). 
Any information is greatly appreciated.

/Jnusa

---

### Post by jnusa on 2008-09-23
Just wanted to follow up on my questions. After a couple of hours on #ubuntu IRC, I found out that mdadm will pick up the existing raid by it self. All you had to do is install mdadm and restart. It worked like a charm and I could mount /dev/mdo after the restart. Note that this migration was from 32bit to 64bit and there were no problems at all. Linux ftw :guitar:

---

### Post by santhony on 2009-07-05
I'm going thru the same issue now, but having problems.

I'm trying to move my Existing Raid5 from a Ubuntu 9.04 I386 system to Ubuntu 9.04 AMD64 based system.

I was hoping I could copy the MD0 portions from my fstab and mdadm.conf files and it would work... but no luck, receiving various error messages on boot(particulary that it doesn't see a ext2 files system on MD0) and unable to mount MD0..

Here's the entries in regaurds to MD0 of those files:

FSTAB:
/dev/md0	/mnt/raid	auto	defaults	0 3

MDADM.CONF:
ARRAY /dev/md0 level=raid5 num-devices=7 UUID=67350c39:89f0ac91:0f5b4e61:2c17f314
   devices=/dev/sdf1,/dev/sde1,/dev/sdg1,/dev/sdh1,/dev/sdb1,/dev/sdd1,/dev/sda1

I've tried several things, my last attempt was the following command with this error:

sudo mdadm --assemble --run --force /dev/md0/dev/sda1 /dev/sdb1 /dev/sdd1 /dev/sde1 /dev/sdf1 /dev/sdg1 /dev/sdh1
(this commands aborts, as it says sda1 has no Superblock)




Could anyone provide the "Best Practicies" for this procedure or point me in the right direction??  I believe this should be pretty easy and straight forward... but not sure why these issues.

Thanks in Advance.

FYI... I'm always able to go back to the original OS and mount the files with no problems.

---

### Post by santhony on 2009-07-05
Still trying here....

I suspect that when I move the raid set over, it sees the drives and assembles it into an unformatted MD0, that's why I can't mount it...

---

### Post by santhony on 2009-07-06
Anyone who has info, I would greatly appreciate it...

I'm currently still trying to mount my mdadm RAID5 in a new Ubuntu 9.05 Jaunty AMD64 Build, coming from Ubuntu 9.05 Jaunty I386 build.

I can always succesfully move and mount the Raid 5 configuration back to the old system, no problems.

When I put it into the new system, I've noticed that the OS does not recognize the partitions, such as in the old system, the drives are configged as sda1, sdb1, sdd1.   The new system only sees sda, sdb, sdd... And it gives me an OLD UUID on those.

On the old system, when I run mdadm -E /dev/sda1 vs /dev/sda, I'll get two outputs with sda1 the correct UUID and sda the wrong UUID.  This happens for all the drives.

Apparently, this looks to me like I've should of cleaned up and erased old RAID 5 config info on these drives.

Is there any way to clear this up?

---

### Post by colli419 on 2010-03-16
I have a similar problem and it would appear it is for the very same reason. I migrated all the configuration files but it doesn't seem to assemble correctly from the boot. Can you mount the array manually? If you found anything I would be most appreciative. Thanks!

---

### Post by santhony on 2010-03-16
Let me rattle my brain and remember what this problem was... 

I've gotten really good with MDADM since, where I no longer have any fear of picking up and moving my RAID sets...

I usually over complicate things that don't need too, but here's what I've learned with MDADM.

Since you've installed your old raid set into a new system or OS...

Normally All you would have to do, is install MDADM, then open a command prompt and type:

sudo mdadm --assemble --scan

DO NOT try to use the old mdadm.conf file or any of the old files....

That should automatically send MDADM to query the disks, identify them and assemble.

There is no risk in that command.

Hopefully your raid set will be recognized, mounted and you should have access to your files.

To save this, so you don't have to do again after reboot:

from command prompt do:
sudo su
sudo mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf

This should save the configuration detail into the mdadm.conf file.

Let me know how you make out..

---

### Post by santhony on 2010-03-16
> **santhony said:**
> Let me rattle my brain and remember what this problem was... 

I've gotten really good with MDADM since, where I no longer have any fear of picking up and moving my RAID sets...

I usually over complicate things that don't need too, but here's what I've learned with MDADM.

Since you've installed your old raid set into a new system or OS...

Normally All you would have to do, is install MDADM, then open a command prompt and type:

sudo mdadm --assemble --scan

DO NOT try to use the old mdadm.conf file or any of the old files....

That should automatically send MDADM to query the disks, identify them and assemble.

There is no risk in that command.

Hopefully your raid set will be recognized, mounted and you should have access to your files.

To save this, so you don't have to do again after reboot:

from command prompt do:
sudo su
sudo mdadm --detail --scan --verbose > /etc/mdadm/mdadm.conf

This should save the configuration detail into the mdadm.conf file.

Let me know how you make out..

If this doesn't work for you, or maybe you've already tried this..

I'll go back and find out what I did to fix, because I believe I had an unusual issue and was able to force it out...

I've never lost a MDADM raid set before....Knock on Wood!!

---

### Post by colli419 on 2010-03-16
Sadly I have tried this solution and it didn't work for me in the past. I think the problem might be the configuration of the array on the drives. I know that the data on the drives is fine, is it possible to auto create a new set of configuration files on the super blocks or something like that?

---

### Post by santhony on 2010-03-16
Ok.. I just went back thru my previous threads and found this recommendation given to me by user laluz.

Maybe it will work for you..


#reassemble raid
sudo mdadm --assemble --force /dev/md0 --uuid=use_your_uuid_from_config /dev/sd{a,b,c,d,e}1 #put here your disk names
sudo mdadm --query --detail /dev/md0
sudo fsck.jfs -v /dev/md0 # use here what is appropriate for your filesystem
sudo mount /dev/md0
sudo watch cat /proc/mdstat


Here's the link to the original thread...

[http://ubuntuforums.org/showthread.php?t=1333242&highlight=santhony](http://ubuntuforums.org/showthread.php?t=1333242&highlight=santhony)

Let me know what happens..

---

### Post by colli419 on 2010-03-17
I got it to work but for the stupidest reason possible. It turns out that when I was installing mdadm and assembling the RAID it was not storing it to the initrd file. So I decided to check the configuration line in mdadm.conf to make sure it was right, manually started the RAID, then ran: sudo update-initramfs -u

Now it works like a champ and it is like there was never a problem in the first place. All disks are healthy, happy, and carefree. Needless to say I am a very happy camper. Thank you so much for getting back to me, I had a lot of trouble finding help with this issue. It seemed like we had the same problem, but apparently not.

---

