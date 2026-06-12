---
title: "confused about partitions"
date: 2010-03-10
forum: Installation &amp; Upgrades
---

### Post by AaronDude on 2010-03-10
Hi I'm considereding installing linux mint or ubuntu and keeping windows 7.  I never used linux before and was recommened mint and ubuntu.  I'm sort of leaning towards mint.  Anywho, is it possible to access the main windows 7 partition from ubuntu after installing?  Do I have to import all my music or would it still work from my main windows 7 acer partition?  I've noticed on the live cd I can play mp3s located on my acer drive but I haven't tried writing to it.  Can I write to that drive or add more music later to it from ubuntu?  Or is the ubuntu partition the only usuable one from ubuntu?  I haven't tried shrinking my main partition yet but I imagine I'd only need about 25 gbs for the ubuntu partition?  I have 300 gbs of music and I really don't want duplicate files on my hard drive.

---

### Post by sikander3786 on 2010-03-10
> **AaronDude said:**
> Hi I'm considereding installing linux mint or ubuntu and keeping windows 7.  I never used linux before and was recommened mint and ubuntu.  I'm sort of leaning towards mint.  Anywho, is it possible to access the main windows 7 partition from ubuntu after installing?  Do I have to import all my music or would it still work from my main windows 7 acer partition?  I've noticed on the live cd I can play mp3s located on my acer drive but I haven't tried writing to it.  Can I write to that drive or add more music later to it from ubuntu?  Or is the ubuntu partition the only usuable one from ubuntu?  I haven't tried shrinking my main partition yet but I imagine I'd only need about 25 gbs for the ubuntu partition?  I have 300 gbs of music and I really don't want duplicate files on my hard drive.

You are more leaned towards linux mint so you should be asking linux mint forums.

However with Ubuntu you can read/write to your windows partition easily as mounting ntfs partitions is quite easy in linux nowadays.

You won't need to duplicate files if you don't want to. You will be able to play all your music from windows partition.

Sikander.

---

### Post by coffeecat on 2010-03-10
For mounting and read/writing an NTFS partition, you can mount it as and when you need it from the Places menu. You simply click on the partition where it is listed in the Places menu, enter your password where prompted and a Nautilus (file manager) window will open.

Or - if you want it mounted at bootup so that it is always available, you need to add a line to the configuration file /etc/fstab. Since you are new to Linux you probably won't want to do that manually. The easiest way is to use the GUI utility 'ntfs-config'. Have a look in Synaptic or in Ubuntu Software Centre and install it. It's easy to use.

With regard to keeping your music files on your Windows 7 partition, yes that is an option. But with one word of warning. When Vista came out there were some reports of Vista having a fit of the vapours if files had been written to in the user's folder from Linux. This was a Vista problem, not Linux. Linux read/write of ntfs is safe and reliable. I can't remember the details of why this happened. This may or may not be a problem now with Windows 7.

One alternative which gets around this problem is to have a separate data partition formatted NTFS in which you store all your personal files that you want to access from Windows and Linux. It would be seen by Windows as E:\ or F:\ or whatever and you will be able to mount it from Linux by one of the above methods. This separate data partition can be a logical partition if you are running out of primaries. Windows is happy for an E:\ (whatever) partition to be a logical one.

This is what I do. Although it is quite safe to read from a Windows C:\ partition using I try to avoid writing to it because of this alleged issue.

Lastly, a bookmark for you. Since you are new to Linux, I didn't want to alarm you with instructions on how to edit /etc/fstab. But if you really get into Linux, you may want to be playing with it with the rest of us. :wink: In which case, you may find this useful:

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

