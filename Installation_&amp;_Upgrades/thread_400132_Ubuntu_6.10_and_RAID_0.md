---
title: "Ubuntu 6.10 and RAID 0"
date: 2007-04-03
forum: Installation &amp; Upgrades
---

### Post by yt404 on 2007-04-03
Hello

I have used ubuntu in the past (5.10 - 6.06) and liked it.

I am currently running windows vista and am wanting to get rid of vista completely and install ubuntu 6.10.

My current hardware setup is working fine with windows but I'v never tried it with linux of any flavour. I currently have an Asus M2N-E nforce 570 motherboard which has SATA RAID. Because of this SATA RAID i am running 2 Western Dig Raptors in a RAID 0 (Striped) array which i setup in the BIOS.

This is recognized by vista without the need for the RAID driver from nvidia or asus so I assumed linux would be the same, it isn't.

I placed the ubuntu disk in my cd-rom drive last night and booted into the graphical desktop/install and after choosing install ubuntu recognizes both of my raptors as seperate drives and not as one (as it should with them being setup in a RAID 0)

Can anyone give me any advice as to how I can get ubuntu to recognize my RAID 0?

I read that the alternative iso might work, an anyone confirm this or give further advice as to how to get this working how I want, I really want ubuntu, sick of windows.

Thanks in advance

Chris

---

### Post by webjames on 2007-04-03
The problem is actually with the RAID, what you have is FakeRAID, there are lots of posts about solutions using fakeraid, real raid is hardware raid, these hardware controllers tend to be quite expensive. more info can be found here: [http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks](http://en.wikipedia.org/wiki/Redundant_array_of_independent_disks)
and more: 
[http://tomshardware.co.uk/2004/06/25/cheap_and_reliable_raid_5_storage_compared/page12.html#benchmarks](http://tomshardware.co.uk/2004/06/25/cheap_and_reliable_raid_5_storage_compared/page12.html#benchmarks)

however don't give up! 

I currently have a 4 disk raid5 array mounted as my home partition with Linux software raid! what you want to research is: mdadm

however i installed the whole boot system to another hard drive, i believe booting from software raid can be problematic, but things are improving all the time.

anyway i hope this has given you somewhere to go from!

Good Luck - let us know how it goes!
regards,

James

---

### Post by yt404 on 2007-04-03
it has helped yes, thank you.

I was just reading about this on the nforce 570, what a bummer, it seems ill be sticking with windows for now then, no point having raptors if i cant boot from them.

Thanks

---

