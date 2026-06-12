---
title: "where is my raid array????"
date: 2009-03-27
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xalaros on 2009-03-27
Ok, today i updated to latest jaunty release.
After reboot i saw my raid mount gone.
Probably latest update had a dmraid update into. my
currect dmraid release is:
dmraid version:		1.0.0.rc15 (2008-09-17) shared 
dmraid library version:	1.0.0.rc15 (2008.09.17)
device-mapper version:	unknown

also uname -a
Linux ubuntu-desktop 2.6.28-11-generic #37-Ubuntu SMP Mon Mar 23 16:40:00 UTC 2009 x86_64 GNU/Linux

the array consisted of 3x500gb drives sdb / sdc / sde
in /dev/mapper/ previously i had a device : isw_dicfecjcch_raid11
now nothing.

when i do dmraid -ay :

ERROR: isw: Could not find disk /dev/sde in the metadata
ERROR: isw: Could not find disk /dev/sdc in the metadata
ERROR: isw: Could not find disk /dev/sdb in the metadata
no raid disks

please i need help i have a lot of media on the raid array.

---

### Post by xalaros on 2009-03-27
forgot to mention that yesterday i did a conversion from ext3 to ext4 on all my drives expect my / drive.
but from what i can remember i also did a reboot and everything worked fine.
Also the raid drive appears normally on my bios.
any ideas on how to get this back??

---

### Post by xalaros on 2009-03-27
correct... i booted back to 2.6.28-9 kernel and everything seems to be working fine. So is there a bug in 2.6.28.11 or something???

---

### Post by Aenima99x on 2009-03-27
There's a known issue with RAID 10 and mdadm, but I don't believe it applies to your situation. Haven't heard of any other issues.

"The mdadm package in Ubuntu 9.04 Beta will fail to assemble RAID10 arrays on boot. Other types of RAID are not affected; investigation of this issue is ongoing. 316670"
[Info here]("http://www.ubuntu.com/testing/jaunty/beta")

---

### Post by xalaros on 2009-03-27
yes i saw that as well but it says only for raid 10.
I have a striping RAID. The funny thing is i don't get any errors in dmesg as well.

---

### Post by danwood76 on 2009-03-27
There is a break in the latest dmraid.
A patch was added that broke all dmraid devices:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/349516](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/349516)

Force the previous version and you should be fine.

---

### Post by ViRMiN on 2009-03-27
I've having problems with my RAID with that kernel too (RAID-0).  Can't remember the exact error but, I'm back on the -10 release and working.

Still, I've ignored all of the advice and been running Jaunty on my main box since Alpha 2!

---

### Post by danwood76 on 2009-03-27
If you are using dmraid the kernel shouldnt really effect you.
The dmraid is a software app that creates block devices that are seperate from the binary kernel pakcages.

It might be that the latest version of dmraid has correupted your intramfs and so you cant boot?
But jaunty is still in testing, the dmraid patch should filter through soon enough.

---

### Post by xalaros on 2009-03-27
If it was only dmraid fault why is it that when i got back to 2.6.28.9 kernel everything works fine even though i haven't downgraded dmraid i am still on rc15.
Anyway i will try upgrading again as soon as a patch comes out.

---

### Post by ViRMiN on 2009-03-27
I use dmraid, and that's part of the error message.  I've had this problem previously with it seemingly affecting only one kernel release but, equally when dmraid itself was updated.  There was a dmraid update earlier too...

---

### Post by chrisccoulson on 2009-03-27
> **xalaros said:**
> If it was only dmraid fault why is it that when i got back to 2.6.28.9 kernel everything works fine even though i haven't downgraded dmraid i am still on rc15.
Anyway i will try upgrading again as soon as a patch comes out.

That's because the old dmraid is still intact in the initramfs for the older kernel. If you carry on running the old kernel, you will have to remember to manually update the initramfs for the newest kernel after installing the fixed dmraid package, else it will still fail when you try to boot the latest kernel, even with the fixed dmraid package.

FWIW, I'm having exactly the same issues as you with dmraid right now, so I share your pain ;)

---

### Post by ViRMiN on 2009-03-27
Well, I was going to say, there is no pain, and I was looking forward to rebuilding my main box with the final release but, hmmm... I'd sooner be sticking with an alpha 6 with a few updates that works perfectly!

It was going so (too?) well!

---

### Post by almackska on 2009-03-27
I have a similar issue, My raid 0 setup isnt working. i have a photo with the errors. 
I really hope this doesnt mean my array is broken. I have lots of info i need.

[IMG]http://mackattack.terapad.com/resources/23780/assets/images/2.jpg[/IMG]

---

### Post by xalaros on 2009-03-28
ok seems latest update of dmraid to 1.0.0.r15.6ubuntu1 fixed the issue.

---

### Post by ViRMiN on 2009-03-28
Yes, that's done the trick, all's working fully again!

---

### Post by loraque on 2009-04-01
I am trying to install 9.04 beta to a RAID array, and I think I am getting this error as gparted does not see the raid, only the individual drives. Is there a way I can include the updated package that seems to resolve this onto my USB install drive (flash), or CD?

Can I just copy the updated file, or extract it, to the right spot? I suppose I can be patient and wait... but I am not good at that. Thanks!

---

### Post by danwood76 on 2009-04-01
> **loraque said:**
> I am trying to install 9.04 beta to a RAID array, and I think I am getting this error as gparted does not see the raid, only the individual drives. Is there a way I can include the updated package that seems to resolve this onto my USB install drive (flash), or CD?

Can I just copy the updated file, or extract it, to the right spot? I suppose I can be patient and wait... but I am not good at that. Thanks!

You need to install dmraid from the repos (update the sources list first)
then from a terminal run
```

sudo dmraid -ay

```
This will create the raid devices.
There is an issue with the installer in which you have to install the bootloader manually from this guide:
[https://help.ubuntu.com/community/FakeRaidHowto#Set%20Up%20the%20Bootloader%20for%20RAID](https://help.ubuntu.com/community/FakeRaidHowto#Set%20Up%20the%20Bootloader%20for%20RAID)

---

