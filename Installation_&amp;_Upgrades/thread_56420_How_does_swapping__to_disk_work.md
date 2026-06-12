---
title: "How does swapping  to disk work?"
date: 2005-08-12
forum: Installation &amp; Upgrades
---

### Post by cjoshuav on 2005-08-12
I just did a clean install of Ubuntu and decided not to create a swap partition since I assume 2GB of RAM is plenty.

I installed the system monitor on my GNOME panel to track memory usage, and I noticed that 22% of my memory use "is cache".  Is the "cache" to which it refers a swap file of some kind on the hard drive?

If so, I'd rather keep that in a separate partition.

Next question, if I make a swap partition now, will Ubuntu automatically recognize it on reboot and us that instead of one on my primary Ext3 partition? 

If I do the above, do I need to delete or disable a swap file of some kind on my Ext3 partition?

Thanks very much.

Joshua

---

### Post by jdodson on 2005-08-12
[QUOTE=cjoshuav]I just did a clean install of Ubuntu and decided not to create a swap partition since I assume 2GB of RAM is plenty.[/quote]

Yeah you more than likely cant go wrong with 2G, though to be safe I always create a swap 2 times my ram size.  Seems like a lot, but I have a 250 G drive.

[QUOTE=cjoshuav]I installed the system monitor on my GNOME panel to track memory usage, and I noticed that 22% of my memory use "is cache".  Is the "cache" to which it refers a swap file of some kind on the hard drive?[/quote]

No, memory caches(if I understand them correctly) are when Linux takes that ram and puts it into standby instead of not using it at all.  So when you need to allocate more memory, you have it ready to go.

[QUOTE=cjoshuav]If so, I'd rather keep that in a separate partition.[/quote]

Yeah so you dont have a swap partition, your memory is just being cached, which is what is supposed to happen.

[QUOTE=cjoshuav]Next question, if I make a swap partition now, will Ubuntu automatically recognize it on reboot and us that instead of one on my primary Ext3 partition? [/quote]

No, you will have to do some fiddling with you "/etc/fstab" after you set the partition and format it correctly.

[QUOTE=cjoshuav]If I do the above, do I need to delete or disable a swap file of some kind on my Ext3 partition?[/quote]

Not sure what you mean, but the preferred way(as in the only way I know how to create a swap) is to partition out the area and make the file system a "Linux Swap" and then tell "/etc/fstab" where it is located.

---

### Post by cjoshuav on 2005-08-12
Thanks!  That's exactly the help I needed.  If I start running out of RAM, I'll use Partition Magic to make a swap file and then set it up in fstab.

Joshua

---

### Post by heimo on 2005-08-12
jdobson already answered, but I'll add a link to thread that discusses creating swap partition and alternatively how to make swapfile:
[http://www.ubuntuforums.org/showthread.php?t=54307]("http://www.ubuntuforums.org/showthread.php?t=54307")

Swapfile:
[http://www.ubuntuforums.org/showpost.php?p=287528&postcount=6](http://www.ubuntuforums.org/showpost.php?p=287528&postcount=6)

---

