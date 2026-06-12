---
title: "Dapper alt disk, RAID (part 2)"
date: 2006-06-16
forum: Installation &amp; Upgrades
---

### Post by Panhead Bill on 2006-06-16
My boot drive, 80 gb ata (hda), is separate from the 3 intended raid drives, (hde, hdf, hdg) - each 120 gig seagate ata drives on a fastrack controller pci board.  I intended to run the array as a 360 gig RAID-0 for video recording.

In a thread on the Server Talk board, I found the basic steps outlined as follows (by LordHunter317):

1.  Partition the RAID array members
2.  Create the arrays
3.  Format the arrays via mkfs
4.  Create the mount points via mkdir
5.  Mount the arrays

I am trying (unsuccessfully) to get through the first item on the list.  

I fired up the dapper alternate disk in the fix broken system mode, and am now at the point of partitioning the array members, or at least attempting to do so.

If I select "Create software RAID" 
   then Create MD device
   then RAID-0 

I get the error "No RAID partitions available"  followed by the information that the partition should be "type: Linux RAID Autodetect"

If instead of selecting "Create software RAID", I highlight any of the three intended RAID drives and try to manually partition them, I get the following list of partition table types:

amiga, bsd, dvh, gpt, mac, msdos, pc98, sun, loop

None of these seem to be the aformentioned "Linux RAID Autodetect"

Can someone give me a peice or two of the puzzle?

---

