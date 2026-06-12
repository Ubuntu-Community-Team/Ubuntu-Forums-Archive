---
title: "Dynamic partitions"
date: 2009-11-15
forum: Installation &amp; Upgrades
---

### Post by AllanP on 2009-11-15
I recently purchased an HP Pavillion dv600-2043 with a 500GB HD and 4GB RAM. The reason I went for the larger drive was so that I could partition it and have a substantial back up partition and a nice size partition for Linux. I've never heard of "dynamic partitions" but that's what it has and I digress but even my Acronis True Image won't work with it. Anyways I made a 40GB partition for Ubuntu 9.10 and tried to install. When it came to the partitioning I chose manual. It sees four other partitions, but not the one I made for Ubuntu. The reason for all the parts is HP and the way Windows 7 is loaded.:(:confused:

---

### Post by oldfred on 2009-11-16
Dynamic partitions are windows only. In windows you can convert standard MBR to dynamic but you cannot convert back. It was for raid or very large partitions probalby before GPT was standardized. MBR has a max of 2 TB and now they are selling 2TB drives so we all will be converting from MBR with its 4 primary partition limits in the future. GPT looks like it will be the new standard already used for Apple and some newer windows servers.

[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)

---

### Post by AllanP on 2009-11-16
> **oldfred said:**
> Dynamic partitions are windows only. In windows you can convert standard MBR to dynamic but you cannot convert back. It was for raid or very large partitions probalby before GPT was standardized. MBR has a max of 2 TB and now they are selling 2TB drives so we all will be converting from MBR with its 4 primary partition limits in the future. GPT looks like it will be the new standard already used for Apple and some newer windows servers.

[http://en.wikipedia.org/wiki/Logical_Disk_Manager](http://en.wikipedia.org/wiki/Logical_Disk_Manager)
Thanks; so are you saying that down the road we can expect Linux to be using dynamic, or am I misunderstanding?

---

### Post by ottosykora on 2009-11-16
I did convert dynamic to basic by the use of windows utility, is it called parted?
It is not possible with the GUI, but with the command line it is.

I read then some hwto on MS sites and then the task was possible.

---

### Post by oldfred on 2009-11-16
Dynamic is windows only, do not work for any other operating system that I know. It was purchased from some other company per the link. GPT is not related to dynamic partitions.

I thought the only way to convert back from dynamic was to copy all data to a backup and totally reformat, glad to here there is another way.

---

### Post by AllanP on 2009-11-16
> **ottosykora said:**
> I did convert dynamic to basic by the use of windows utility, is it called parted?
It is not possible with the GUI, but with the command line it is.

I read then some hwto on MS sites and then the task was possible.

Were you able to keep all your data along with the OS. I don't have a Windows 7 install disk. All I have is DVD's to restore laptop to original state.

---

