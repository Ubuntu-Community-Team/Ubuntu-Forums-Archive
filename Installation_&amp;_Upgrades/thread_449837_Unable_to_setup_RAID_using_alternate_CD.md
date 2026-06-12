---
title: "Unable to setup RAID using alternate CD"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by Kazol on 2007-05-20
I'm trying to install software RAID-1 using the alternate boot CD for a webserver with 2x10GB HDs. I setup a ~9.5GB and ~500MB primary RAID partition on each HD, and marked the first partition as bootable. I made sure they were exactly equal, since the total size of the HDs differed slightly, resulting in extra space on the 2nd. HD. 
When I click "Finish and write changes", I get the error msg "Root filesystem not defined." I guess it wants to know where the / path is, but online howtos described setting this up after this step, plus there is no other option when I select the RAID type of partition.

---

### Post by RTrev on 2007-07-08
> **Kazol said:**
> I'm trying to install software RAID-1 using the alternate boot CD for a webserver with 2x10GB HDs. I setup a ~9.5GB and ~500MB primary RAID partition on each HD, and marked the first partition as bootable. I made sure they were exactly equal, since the total size of the HDs differed slightly, resulting in extra space on the 2nd. HD. 
When I click "Finish and write changes", I get the error msg "Root filesystem not defined." I guess it wants to know where the / path is, but online howtos described setting this up after this step, plus there is no other option when I select the RAID type of partition.

As far as I can tell, software RAID support still seems to be broken.  I just ran through the drill twice in a VMware Server setup, and it worked like a charm.  So I took a deep breath and managed to blow away both of my 74G Raptors only to find that the stupid thing didn't work on the real hardware like it did in the virtual machine.

Now I'm tediously installing normally again, wihout RAID again, and wondering what the story is.

Will this ever be fixed?  Is it fixed now, and I just don't know where to download the fixed version of the alternate CD?

Anyway, you aren't alone.  I do suggest vmware server as a good way to experiment, though.  Get yourself right to where it's about to partition the disks, and then take a snapshot of it.  Whatever you try next, it can be undone by just rolling back to that snapshot.   Then, if this issue is ever resolved, you'll be an old pro at it.  :-)

Bob

---

### Post by RTrev on 2007-07-08
> **Kazol said:**
> I'm trying to install software RAID-1 using the alternate boot CD for a webserver with 2x10GB HDs. I setup a ~9.5GB and ~500MB primary RAID partition on each HD, and marked the first partition as bootable. I made sure they were exactly equal, since the total size of the HDs differed slightly, resulting in extra space on the 2nd. HD. 
When I click "Finish and write changes", I get the error msg "Root filesystem not defined." I guess it wants to know where the / path is, but online howtos described setting this up after this step, plus there is no other option when I select the RAID type of partition.

Reading your note again, and sorry I missed this the first time, it sounds like you might be skipping a step.

As I understand it, and as it works in VMware, you first create your actual partitions on the physical devices.  You mark them to be used as RAID, etc.

When you're done with that, you don't click "Finish and write changes", but instead you then go to the top where it says something like "Configure RAID."  At that point, you choose to create your MD devices, you pick which of your partitions go in which MD, and you change them from do not use to, for example, ext3 mounted as / (your root directory).

What I did, and I'm not sure this is necessary but it worked, is create one RAID-1 array for /boot and one RAID-0 array for / itself.

I know there are better ways to do it, but I also made a RAID-1 for swap.  I just wanted to get it working, and it didn't complain about this setup at all.  I would have then experimented and refined it later, had it not failed completely when trying to do it for real.

So maybe this will help...?

Bob

---

