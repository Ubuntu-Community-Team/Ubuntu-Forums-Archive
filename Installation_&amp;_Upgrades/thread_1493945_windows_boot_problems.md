---
title: "windows boot problems"
date: 2010-05-26
forum: Installation &amp; Upgrades
---

### Post by HoboGod on 2010-05-26
I began running a triple boot system - installed in this order

Windows xp - x64
Windows Vista - x64
Ubuntu - 8.10 - 9.10(current)

I was preparing to upgrade my Vista partition to Windows 7, and figured since I never used it I would delete my Xp partition - once it was gone I lost the ability to boot into Vista, as of right now I only have access to my Ubuntu partition. Is there any way to fix this through Ubuntu, or will I have to reinstall Windows then retrieve the grub loader with a live cd?

---

### Post by oldfred on 2010-05-26
Windows combines it boot into the first install. So when you deleted XP you also deleted the files Vista needs to boot. You can repair it with a Vista CD, but the only way from linux would be a total recovery of the XP partition if it has not been overwritten.

To get each MS to have its own boot loader make a second primary partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run check disk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by HoboGod on 2010-05-26
I kinda figured thats what I did but did not know how to fix it, and it is possible to restore the partition, did not know that, I'll give it a try. Thanks.

---

### Post by HoboGod on 2010-05-26
hhhmmmmm, I tried to use a program to restore the missing partition, and it seems that It tried to reformate the whole HD, right now i'm in a live cd, if it is possible and what should I use to restore my partitions, so far nothing has been written over, so as far as I know everything is still there. please help if you can. I really dont want to loose almost a TB of data

---

### Post by darkod on 2010-05-26
Install testdisk in live mode and start it:

sudo apt-get install testdisk
sudo testdisk

After that this should help you:
[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

---

### Post by HoboGod on 2010-05-27
I've tried testdisk but I seem to be going around in circles. I've read through a bunch of the wiki on testdisk, but have gotten nowhere. Testdisk is what killed the rest of my Hd when I tried to recover my first XP partition. Testdisk has found everyone of my partitions but I am still unable to undelete them as shown in the wiki.

---

### Post by darkod on 2010-05-27
I don't know what to say. People have reported good success with it.

I know it sounds dumb but I can only advise to pay attention and do the procedure(s) correctly. I have never needed to use it, luckily. :)

As you might be aware, the point of a 'deleted' partition is that it's simply deleted from the partition table, otherwise it's there. If it wasn't, no piece of software could return it. :)

So, testdisk finding the partitions is very good start. That manual outlines the process how to write a new partition table where your 'deleted' partition will exist. And that's it basically.

I think it's worth it to give it another shot.

You can skip some parts like looking at files first to make sure you are looking at correct partition. You want to restore all partition you had as I understand. Just do the parts important for you, writing the found partition into a new partition table. And correctly labeling them as primary, logical, boot, etc. Maybe that is where you got it wrong?

---

### Post by WinRiddance on 2010-05-27
> **darkod said:**
> As you might be aware, the point of a 'deleted' partition is that it's simply deleted from the partition table, otherwise it's there. If it wasn't, no piece of software could return it. :)

.
Yeah, but if somewhere along the line you decide to "accidentally" create a new partition table because new sounds better than old ... then you just hosed everything because in that case anything and everything is irretrievably lost until you reformat the entire disk again with the new partition table, followed by creating new partitions for new data. Although primarily for partitioning I actually prefer this because of the documentation and added tools. [http://partedmagic.com/](http://partedmagic.com/)

---

### Post by darkod on 2010-05-27
You can also try with this:
[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

Even though it has photo in the name, it's not just for photos.

@winriddance
I didn't get your point exactly. The current partition table is fine, as long as you want to forget about the deleted partitions. If you want them recognized, yes, you do need to write new partition table over the current one. At least that is how I understand it.
Or use some specialist software which actually scans the disk. But that's different topic.

---

### Post by HoboGod on 2010-05-28
ok I've kinda accepted that I wont be getting my computer back to original. Will that PhotoRec allow me to retirve whole directories, without a working partition, or should I install linux on a USB drive and burn my data on CDs?

---

### Post by darkod on 2010-05-28
> **HoboGod said:**
> ok I've kinda accepted that I wont be getting my computer back to original. Will that PhotoRec allow me to retirve whole directories, without a working partition, or should I install linux on a USB drive and burn my data on CDs?

I don't know what exactly do you mean by using linux from usb. The thing is that you deleted that partition(s), either by mistake or on purpose.

Any OS now will look at the partition table and act accordingly. They do not exist in the partition table so it will not show you anything to copy.

On the other hand, Photorec should work like similar software for retrieving deleted data, it actually reads the hdd sector by sector, and offers to save on another disk any data it retrieves. Sometimes it won't be 100%, but you still end up with most of your data back as long as you haven't started overwriting it.

---

### Post by HoboGod on 2010-05-28
what I mean is I don't really have a way of saving the data I retrieve just using a live cd. so I was thinking that I'd use a usb os to brun the recovered data to cds.

but I kinda see what you mean. perhaps I'll have to transfer the retrieved data over my network

---

### Post by darkod on 2010-05-28
Well that was my point. If I understand you correctly, what you call usb OS is the sme as the live CD. It doesn't matter whether you boot it from cs or usb. The point is that if the partition is not in the partition table, you can't open the files just like that and copy them.

How Testdisk and Photorec work, they don't rely what is or is not in the partition table, they actually scan the disk for partitions and data found.

That's why I initially suggested testdisk, and you also confirmed it found the partition. But you also need to do the step of writing that partition in the table. From that point on, any live cd or usb os will be able to open it and copy files from it.

---

### Post by HoboGod on 2010-06-08
Ok at this point I have yet to make any progress in recovering anyting. I've searched around and found a few things that may help me out but as of now I really only want to recover my data in my linux partition, it was a logical partition, 596 gig for data(plus ubuntu 9.10) and 4 gig for swap, it was also the last paprtion I made on my drive. this is the only partiton I care about right now. Testdisk has failed me several times, so is there any way to recover using gparted(recomended by a friend) or some other program I could use with or in lue of a live disk.

---

