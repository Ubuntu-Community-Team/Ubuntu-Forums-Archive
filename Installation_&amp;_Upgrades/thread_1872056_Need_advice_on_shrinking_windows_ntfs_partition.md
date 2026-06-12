---
title: "Need advice on shrinking windows ntfs partition"
date: 2011-10-30
forum: Installation &amp; Upgrades
---

### Post by pranav on 2011-10-30
Hi Everyone!

I have Ubuntu 11.10 installed on a lenovo s10-3t netbook. Everything is fine. However, the default windows 7 partition, the "C drive" is taking up a huge chunk of the space. The goal is to not break anything, windows, grub, etc. and also not lose any data and manage to do the following:

1. shrink the C drive to about 70 GB (if this is possible at all)

2. Create a new 120GB partition that will be accessible from windows as well as ubuntu, seeking your recommendations on the filesystem to choose?

3. I want to take ur advice on how to go about doing this using gparted or any other tool(preferably GUI). Since I will create a new partition, i am worried grub will break and i wont be able to login to anything at all!

I have a bootable pen-drive (thats how i installed ubuntu on the netbook) in case we need to use it at some point.

I have shared the breakup from Gparted in the attachment. 

[ATTACH]205848[/ATTACH]

Looking forward to your advice and suggestions to better utilize the space on my hard drive instead of letting it stay dormant in windows, the only catch is i dont want to format windows as other family members use the netbook occasionally and they hv certain things installed on windows n such that i dont want to meddle with. 

Thanks to the wonderful Ubuntu community in advance!

---

### Post by Megaptera on 2011-10-30
For 2.I think ntfs is the only simple option for a file system readable by both Ubuntu & Windows.

Useful guide here:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

---

### Post by papibe on 2011-10-30
I would start doing all you can do from Windows 7 first:
[LIST]
[*]In order to avoid any possible problem I would start defragmenting the partition. I would even do it a couple of times.
[*]Then I would use [Disk Manager]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") to reduce the partition.
[/LIST]
From experience, you may even need to repeat the process a couple of times since Windows7 kind of act 'greedy' when reducing its own partition (defrag -> reduce partition size).

I would only use gparted unless you can't get the size you want using Disk Manager.

Note that Windows 7 will probably complain the next time it boots with a smaller partition. Let it do its 'adjustments' and you'll be fine.

Hope it helps.
Regards.

---

### Post by pranav on 2011-10-30
> **Megaptera said:**
> For 2.I think ntfs is the only simple option for a file system readable by both Ubuntu & Windows.

Useful guide here:
[http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/](http://www.howtogeek.com/howto/35807/how-to-harmonize-your-dual-boot-setup-for-windows-and-ubuntu/)

Thanks for sharing the article, its actually useful and i will follow those steps once my partitioning is thru to have a seamless workflow irrespective of the OS i use.

Truly appreciate you sharing your thoughts! Cheers.

---

### Post by Quackers on 2011-10-30
Yes, defrag first (at least once) then using Windows Disk Management console shrink the C: drive. It will tell you how much it can be shrunk by in the pop-up window that shows. You can shrink by less than that amount if you want, but not more (without further jiggery pokery).

---

### Post by pranav on 2011-10-30
> **papibe said:**
> I would start doing all you can do from Windows 7 first:
[LIST]
[*]In order to avoid any possible problem I would start defragmenting the partition. I would even do it a couple of times.
[*]Then I would use [Disk Manager]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") to reduce the partition.
[/LIST]
From experience, you may even need to repeat the process a couple of times since Windows7 kind of act 'greedy' when reducing its own partition (defrag -> reduce partition size).

I would only use gparted unless you can't get the size you want using Disk Manager.

Note that Windows 7 will probably complain the next time it boots with a smaller partition. Let it do its 'adjustments' and you'll be fine.

Hope it helps.
Regards.

I will def. follow your defrag tip! I almost forgot about defrag. Its a great suggestion. Would you have any thoughts on my other question about the inclusion of a new partition breaking GRUB?

Thanks for sharing your suggestions! Absolutely appreciate it.

---

### Post by Quackers on 2011-10-30
My shared data partition is NTFS, though I think other types may now work too. Such a new partition would not break Grub if you are using a later version (and you are if using 11-10's version).

---

### Post by fdrake on 2011-10-30
never mind... i just noticed your screen shoot...

---

