---
title: "Fake Raid Problems (dmraid)"
date: 2007-07-04
forum: Installation &amp; Upgrades
---

### Post by skattman83 on 2007-07-04
I've been trying to follow the wiki.ubuntu.com fakeraid howto, and I can't seem to get dmraid to work the way it does in the guide.  Am I doing something wrong, or did dmraid change in feisty?  When I run "dmraid -r" my output is 

root@ubuntu:/home/ubuntu# dmraid -r
/dev/sda: nvidia, "nvidia_deacahbg", stripe, ok, 312581806 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_deacahbg", stripe, ok, 312581806 sectors, data@ 0
root@ubuntu:/home/ubuntu# 

but from the guide, I am expecting: 
via_hfciifae  -- the raw raid volume
via_hfciifae1 -- the NTFS partition
via_hfciifae5 -- /boot
via_hfciifae6 -- swap
via_hfciifae7 -- /

Why does mine list the phyiscal disks, but the guide lists the partitions?

---

### Post by Pumalite on 2007-07-04
Even though there are some people that claim they have 7.04 'working fine' in Ubuntu, I still think that Raids are a problem: Raid 0> minimal improvement; Raid 1> double the danger of lost data. So, whoever wants to hear me: if you want Ubuntu working in your system, get rid of Raids; they are not worth the trouble. dmraid has never worked properly for me.

---

### Post by skattman83 on 2007-07-04
I don't mean to sound rude, but I am well aware of the risks of running a fakeraid.  If I wanted to run these as separate disks, I would have bought one large disk rather than two smaller disks.  Additionally, this computer dual boots, and Vista has no problems using this raid.  With that said, my question is why is the output from dmraid not matching that from the guide.  It doesn't appear that when I use -r I am even getting the same information as the person who wrote the guide.

---

### Post by Pumalite on 2007-07-04
You make my point.

---

### Post by skattman83 on 2007-07-04
I don't think you did... The installation seems to be going quite well other than that difference in the outputs.  Thanks for the "help" though.

---

### Post by chrisccoulson on 2007-07-05
skattman83: I've been running Ubuntu on a NVIDIA fakeraid chipset since Breezy, and I've never had a single problem. DMRAID has always worked fine for me, so don't listen to people who tell you that RAIDs are no good and there's no benefit of running them. I've got a 2-disk RAID-0 and a single disk (for important data) side-by-side in my machine. I get nearly twice the data throughput on my RAID compared to the single disk (disks are all the same model/age)

When I type 'dmraid -r' on my installed system, I get similar output to you, so it's probably nothing to worry about. Perhaps the wiki guide needs updating.

---

### Post by Totzo on 2007-10-27
Hi,

I'm having an odd issue with my nvidia fakeraid array. I have a 3 disc raid0 array with 2 partitions which works fine in windows. The odd thing with ubuntu is that the 1st partition won't mount but the 2nd one will. It's not a big show stopper as I'm using a separate disc for ubuntu but it would be nice to have read access to both of my ntfs partitions.

I get loads of errors at boot time about buffer 1/0 errors and "attempt to access beyond end of device"   as it seems to be trying to mount the 1st drive normally.

I've put entries in fstab with the uiid numbers from vol_id /dev/mapper/nvidia_blah blah and as I say the 1st partion isn't playing ball. Anyone else had a similar issue? Anyone have any suggestions.

Before I get laughed at for my daft setup, yes, I admit it's daft but it works really well for my needs at this point, apart from this. :)

---

