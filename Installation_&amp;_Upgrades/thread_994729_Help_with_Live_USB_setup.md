---
title: "Help with Live USB setup"
date: 2008-11-27
forum: Installation &amp; Upgrades
---

### Post by iamringo on 2008-11-27
So I'm trying to set up a 16gb usb drive in a very particular way, and I'd like some help because I'm running into problems. I'm a computer-fixer-person (that's not the official title, haha) at my school, and so I want to have an ubuntu installation for rescue/diagnosis/hard-drive-reformatting/whatnot on the drive (and it'd be nice if that installation were persistent) but at the same time want to still be able to use the drive as I would a pen drive normally (just to transfer files back and forth between computers). Thus this is what I'm trying to do: create two partitions, and have the first be a FAT32 data partition (maybe 10 gb) to carry stuff around (has to be the first partition cuz windows machines seem to for some reason ignore every partition but the first), and then install a persistent ubuntu live installation on the second partition. Then I could access the files on the first partition from any computer I plugged the drive into, and even access them from the live installation...

So here's what I did, and the problem I've run into:
I used gparted to create two FAT32 partitions.
I used intrepid's built in usb startup disk creator to install ubuntu on the second partition
When I then try to boot from the usb stick, however, I just get a black screen with "_" and nothing else. If, however, I clear the usb drive and format the whole thing as one FAT32 partition and install ubuntu there, everything works fine. It looks to me like Ubuntu doesn't like being installed on a multi-partition pen drive (or maybe it just has to be first, I dunno). I suspect that the problem is in one of syslinux's config files, that syslinux is trying to boot from the first partition because I imagine that's how the usb creator set it up.

What do you guys think? Is that the problem? If so, what config file would you edit and how would you edit it?

I apologize for the ridiculously long post, and thanks for your help!

P.S. Can I maybe just get rid of syslinux on that drive and install grub? If so, how do I tell grub what the persistence file is?

Thanks again!

---

### Post by Patb on 2008-11-27
> **iamringo said:**
> ... at the same time want to still be able to use the drive as I would a pen drive normally (just to transfer files back and forth between computers).


Ringo, why not just create a directory on the live USB for transferring your files? That's exactly what I do with a live USB (with Hardy not Intrepid, and created using Unetbootin, so it's not quite the same). On a 16 gb drive there will be ample space. Sorry if I have misunderstood something. 

Cheers, Pat

---

### Post by iamringo on 2008-11-27
I would do that, except I can't then access any of the data from within the USB installation. Or at least I couldn't find it when I tried a setup like that...

---

