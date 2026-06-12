---
title: "Clean install of Ubuntu 16 over 14, but keep Windows"
date: 2018-08-08
forum: Installation &amp; Upgrades
---

### Post by Milleuros on 2018-08-08
Hi,

I have a quite old computer, which has the old 4 partitions limit. This is how gparted looks like right now:
[https://i.imgur.com/FqtGbhb.png](https://i.imgur.com/FqtGbhb.png)

What I want to do is remove the Ubuntu 14 partition and all the data it contains, then install Ubuntu 16 on a new, bigger partition. A bit afraid of messing up my computer tbh (I did save all my data on an external drive). Those are the steps I want to follow, from the Ubuntu 16 install disk.

1. Remove the Ubuntu partition.  I would right-click on /dev/sda4 and choose "delete". Will the 75 GiB be usable in the future, as in free to use for a new partition?  (**Edit**: First do step 2. Then remove all logical partitions under the extended one, then remove the extended)
2. Shrink the Windows partition to gain more space. I would right-click on /dev/sda3/ and choose "Resize/Move" then select a lower size, e.g. 200-250 GiB. Normally at this point I would have 200-250 GiB of "unallocated" space that I can use (**Edit**: Do this using Windows tools, see replies below)
3. Create a new "extended" partition using all this unallocated space. Would there be a problem where I have to "Move" partitions?  (**Edit**: Do this and step 4 using gparted, not Ubuntu installer)
4. Create swap (~4-6 GiB), root (~50 GiB) and home in the new extended partition. I don't remember how to do this exactly, I imagine once I create the extended I'll have a bunch of unallocated space inside the extended, which I'll have to select then choose "New Partition" ? Can't find the guides I might have used 4 years ago

I'm posting this to try and summarise what I've been reading/googling around and make sure that I haven't missed important details, or that this will achieve what I want to do. 

(Why Ubuntu 16 and not 18: old computer, low specs, and Ubuntu 16 will be supported for long enough for me). 

Thank you for your help :)

---

### Post by westie457 on 2018-08-08
Do things in roughly this order.

Shrink the Windows partition using Windows tools ie: Disk manager then reboot to Windows. Here Windows will run chkdsk as often as necessary for Windows to recognise its new partition size.
Then boot from your install media to try mode start Gparted and unmount all items that have a key next to them.
Delete the partitions for Swap, /(Root) and Home, then delete the extended partition. Click 'Apply' follow the prompts until finished.
Now in the unallocated space click new, Gparted should offer to create an 'Extended' or 'Logical' partition (cannot remember the exact wording), use all of the space.
From here you should be able to continue from your line number 4. creating your new partitions.
When doing the installation you must use the 'Something Else' option and selecting each of the partitions you created earlier, telling the installer to use them for /(Root) and /Home, the swap partition should already used by the installer.

Hope this helps.

---

### Post by Milleuros on 2018-08-08
Thank you for the infos :)

Is there an advantage in using Windows tools instead of gparted, for shrinking Windows?

---

### Post by westie457 on 2018-08-08
> [COLOR=#000000]Is there an advantage in using Windows tools instead of gparted, for shrinking Windows?[/COLOR]
Using Windows tools usually means the change is recognised immediately and Windows will only force a chkdsk if there is a problem.
Using Linux tools to shrink any Windows partition and Windows will force a chkdsk at next Windows boot of all NTFS partitions, this will run until the new sizes are recognised.

Windows will not allow the movement of hiberfil.sys if it exists, Linux will force the movement of all Windows system files which could cause major breakage to Windows.

---

### Post by Milleuros on 2018-08-08
Thank you again. I will give it a try

---

### Post by Milleuros on 2018-08-08
Solved, I managed to clean install Ubuntu 16 and at first glance it works.  Thank you!

---

