---
title: "Ubuntu installation problem inside windows"
date: 2011-09-07
forum: Installation &amp; Upgrades
---

### Post by satyapramodh on 2011-09-07
Hi,
I am a newbie.. i want to install ubuntu11.04 along side windows7. I already have 4 local disks in windows.. i created one more for ubuntu..
Now when i go to the installation (after inserting cd and checking alongside/inside windows option) i find that it displaces only 2 partitions... 1 is the windows OS and the other is all the rest of my partitions(local disks) in one.... now i dont know how to make ubuntu install on the new local disk of 20gb i created in windows.. can anyone please help me in detail/step by step?

[IMG]http://i52.tinypic.com/2rr3rk4.png[/IMG]

---

### Post by nipunshakya on 2011-09-08
> **satyapramodh said:**
> Hi,
I am a newbie.. i want to install ubuntu11.04 along side windows7. I already have 4 local disks in windows.. i created one more for ubuntu..

Thats where you were left behind buddy...windows allows only 4 primary partitions in your HDD. 
Here's  my suggestion: -

1. First backup your data from the drives(all xcept c: ofcourse).
2. Format the extra primary partitions and merge it to just two(one with c: and next say d: as your partition for ubuntu installation)
3. Reboot your pc to windows once to let it configure your fresh partitions and installations...
4. Reboot again , this time from your ubuntu installation cd...
5. When you get to selecting partitions(as your image description), select the drive with free space....
 rest is given in the tutorial below....goodluck .

[http://members.iinet.net.au/%7Eherman546/p23.html](http://members.iinet.net.au/%7Eherman546/p23.html) . . .go through this once....you might not need my abouve suggestions:p

And yes, welcome to the furum):P

Regards, WinuxUser

---

### Post by nipunshakya on 2011-09-08
If you are interested, you can also see this solved thread i satrted which looks similar to u

[http://ubuntuforums.org/showthread.php?t=1838067](http://ubuntuforums.org/showthread.php?t=1838067)

---

### Post by ottosykora on 2011-09-08
>I already have 4 local disks in windows.. i created one more for ubuntu..<


as said, this is the problem if it is a computer with mbr boot system, it it is very new with the GUID partitions , then this is all different.

But how did you create one more partition? In general partitioning is not possible in case you have mbr boot system and 4 primary partitons.

W7 uses actually 2 primary partitions, one is small abut 300mb, and one id the one holding w7 itself and will be some gb size. It will work with one partition only, but MS seems to refuse to install certain updates as the sp1 to w7 if the small partition called 'system' is missing.

So if using mbr system, change one of the data partitions to extended and then you can set up inside it lot of logical drives and they will also be able to accomodate ubuntu.

---

### Post by Mark Phelps on 2011-09-08
Are you sure your PC uses GPT partitioning? OR did you accidentally force the conversion of your partitions to Dynamic Disks when you forced the creation of a fifth partition?

---

### Post by srs5694 on 2011-09-08
Given the description and the screen shot, my best guess is that when you created the fifth partition in Windows, Windows converted the disk to a [Logical Disk Manager (LDM)](http://en.wikipedia.org/wiki/Logical_Disk_Manager) (aka "dynamic disks") format. This makes it difficult or impossible to install Linux on the disk. If I'm right, you'll need to convert from LDM format to a standard MBR format. A couple of Windows disk utilities are claimed to be able to do this, but I've never used them. One is [EaseUS,](http://www.partition-tool.com/personal.htm) and the other is [Partition Wizard,](http://www.partitionwizard.com) IIRC.

Before attempting such a conversion, though, I recommend you launch the Linux installer in its "try it now" mode, open a Terminal window, and type the following command:

```

sudo fdisk -lu

```

Post the results here, between [noparse]```
[/noparse] and [noparse]
```[/noparse] tags to keep the results legible. This will show us in better detail how your MBR is currently laid out and therefore whether my diagnosis is correct.

In the future, my recommendation is to not use the Windows disk partitioner except possibly to shrink Windows partitions. It's got several known bugs and design problems (such as automatically converting disks to LDM format, which is OK for a Windows-only setup but terrible from a cross-OS compatibility perspective).

---

### Post by nipunshakya on 2011-09-08
> **srs5694 said:**
> 

In the future, my recommendation is to not use the Windows disk partitioner except possibly to shrink Windows partitions. It's got several known bugs and design problems (such as automatically converting disks to LDM format, which is OK for a Windows-only setup but terrible from a cross-OS compatibility perspective).

I would keep that piece of advice safe...thank you for that....and sorry for going off topic here...:)

---

### Post by ottosykora on 2011-09-08
>If I'm right, you'll need to convert from LDM format to a standard MBR format. A couple of Windows disk utilities are claimed to be able to do this,<

they were times when the windows refused to convert back to 'basic' from the GUI, I remember that time using the cli for that.
But this was w2k.

In today versions, I remember was able to do it from the GUI, just selected to convert back to what hey call 'basic' format of partition.

---

### Post by srs5694 on 2011-09-09
> **ottosykora said:**
> >If I'm right, you'll need to convert from LDM format to a standard MBR format. A couple of Windows disk utilities are claimed to be able to do this,<

they were times when the windows refused to convert back to 'basic' from the GUI, I remember that time using the cli for that.
But this was w2k.

In today versions, I remember was able to do it from the GUI, just selected to convert back to what hey call 'basic' format of partition.

My understanding is that Windows will let you do this, but in so doing, it will destroy all current partition definitions. This is fine if you want to re-use a disk for fresh data or if you have a complete and current backup that you plan to restore, but probably not for the OP.

Of course, if this has changed I'd like to know it. I've never used Windows LDM myself, though, much less converted back from it to a standard MBR system.

---

### Post by satyapramodh on 2011-09-16
> **Mark Phelps said:**
> Are you sure your PC uses GPT partitioning? OR did you accidentally force the conversion of your partitions to Dynamic Disks when you forced the creation of a fifth partition?

 Yes it said it was going to convert the basic drives to dynamic drives.. thank u all for d help.. ill convert the drives to basic n then try installing.

---

