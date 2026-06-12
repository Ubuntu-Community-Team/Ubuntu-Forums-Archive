---
title: "Should i proceed to install ubuntu or no ...!!"
date: 2015-03-04
forum: Installation &amp; Upgrades
---

### Post by belal2 on 2015-03-04
Dear All,

i was trying to install ubuntu 14.04 LTS alongside windows 7 on a laptop, during installation i was prompted by the following message:

   [B][COLOR=#b22222]The partition tables of the following devices are changed:
[/COLOR][/B]
[B][COLOR=#b22222]SCI1 (0,0,0) (sda)

the following partitions are going to be formatted:

partition #5 of SCI1 (0,0,0)(sda) as ext4[/COLOR][/B]
**[COLOR=#b22222]partition #6 of SCI1 (0,0,0)(sda) as swap[/COLOR]**

and i was asked either to [COLOR=#008000]**continue**[/COLOR] or to **[COLOR=#008000]cancel[/COLOR]**

But i don't understand what does this mean?

so, what will happen if i continue, will the installer damage some of the partitions listed above? and will i be able to boot from windows 7 and ubuntu?

Thanks a lot

---

### Post by TheFu on 2015-03-04
Well, it depends on what is in those partitions, doesn't it?
The best idea is to free some space on the HDD, enough for 2-3 partitions and leave that space free. Then when Ubuntu says install to the disk - always, always, always "choose something else" and go into the partition manager.
* 20G for / - ext4
* 4G for "linux swap" - the optimal size depends on RAM, machine use, and if you hibernate or not.
* whatever is left for /home - ext4

If you are confused or stuck - boot into the liveCD (run without installing), then download and run boot-info - this script will create a URL with the details about your system - post that URL back here for better help. My signature has links for booting stuff.

---

### Post by belal2 on 2015-03-04
Thanks a lot "TheFu" for your reply :), but how could i know the equivalent partitions for "**[COLOR=#b22222]partition #5 of SCI1[/COLOR]**" in windows (i.e. partition c is equivalent to what?, and so on).

Another question: should i free the _*entire*_ partitions or left some space as you mentioned above?

last thing: why do you prefer to ignore the "[COLOR=#006400]install alongside X[/COLOR]" and always choose "[COLOR=#008000]something else[/COLOR]"?

Thanks :)

---

### Post by TheFu on 2015-03-04
1) Write down the sizes and the partition types. Use that to map between whatever Windows calls it vs the real name in Linux.

2) If your HDD is completely used, you need to shrink some partitions to make room.  There are hundreds of how-tos on the internet. Use youtube if you need visuals.  Be aware that MBR or GPT have different issues. GPT is less limiting and easier.

3) alongside x .... I've **never** used that and don't know exactly what it does.  Over the years, that has changed too.  With "something else" I'm in control and there aren't any surprises.

Partitioning is scary until you understand it and learn.  There's no way around it.  Get an overview by reading the wikipedia articles on it and MBR and GPT. Re-read them until it clicks. Again - lots of youtube videos out there.

But you didn't post that URL yet, so nobody here can say definitively what you have or what you should do.  That is your 1st task in the next 10 min to do. Run **boot-info**.

---

### Post by ajgreeny on 2015-03-04
Use your Win7 disk management utility to shrink the Windows partition and after doing so reboot into windows and run chkdsk, or whatever it's called at least twice to make surev that Windows is still working as it should.  

**DO NOT** make any partitions for Ubuntu in your Windows installation, that will not work properly; just leave unallocated space.

Now run the installer and I also recommend you use the Something Else option; it gives you a lot more control and you can be sure that your valuable Windows partitions will not be affected or touched in any way.

You will see all the partitions for windows in the installer and the unallocated space.
Click in the unallocated space and choose New.
Use all that partition as an extended partition.
Now click the extended partition and again click New and make a logical partition at the beginning of the space of 20GB using ext4 and mountpoint /
Now make another logical partition at the end of the extended partition of about 2 - 4GB and use as swap.
Finally click in the remaining unallocated space in the extended partition and make a final logical partition using ext4 again and this time mountpoint /home.

Continue installing.  You will still see that warning about formatting partitions, though perhaps the numbers will be slightly different, but that is normal and there is no need to worry, it just gives you a chance to check everything one more time before going ahead, and if you pointed the installer specifically to that unallocated space your windows partitions should be completely safe.

When editing partitions or installing a new OS on a disk that already has an OS, there is always, however, some risk so make sure that you have all personal and important files backed up somewhere first; nothing should go wrong, but strange things do happen sometimes and it's better to be safe than sorry.

---

### Post by belal2 on 2015-03-04
Thanks a lot "TheFu" for your time, i didn't post the URL as the laptop isn't currently with me, i'll understand first that partitioning basics and try again.

"ajgreeny", thanks for your concern, really good advice, i appreciate it.

:

---

