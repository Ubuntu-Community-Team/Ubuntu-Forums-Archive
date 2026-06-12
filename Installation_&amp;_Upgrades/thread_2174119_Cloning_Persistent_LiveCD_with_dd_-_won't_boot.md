---
title: "Cloning Persistent LiveCD with dd - won't boot"
date: 2013-09-12
forum: Installation &amp; Upgrades
---

### Post by Zach_Feldman on 2013-09-12
Hi everyone!

I tried cloning a persistent Ubuntu 13.02 Live USB with dd. The clone executed semi-successfully, all the files seem to be there and written to the other USB drive. However, I can't seem to boot into the cloned drive using my Macbook Pro. Is there anything I need do to do the second drive to make it bootable? It would seem to me that since it is an exact copy of the other drive from DD, it should just boot right in, but it doesn't show up as an option when I hold down option on my mac like the other drive does.

If there's any way to fix this from within Mac OS X that would be far preferable but I can do it from Ubuntu if necessary.

Thanks in advance for any help!

---

### Post by sudodus on 2013-09-13
Welcome to the Ubuntu Forums :-)

Your problem might be

1. Bad command

Cloning with dd should work as you expect. But you must clone the whole drive, not only the partitions (so sdx and sdy, not sdx1 and sdy1 etc).

```
sudo dd if=/dev/sdx of=/dev/sdy bs=4096
```

where sdx is the source drive and sdy is the target drive.

2. Interrupted command. Maybe the drive has not finished writing when you unplugged it. Use sync and wait for the prompt until you unplug the pendrive.

```
sync
```

3. The target drive is smaller (even nominally the same size, but slightly smaller)

4. The target drive is of a brand and model, that has problems with linux. Some pendrives won't work at all, some work as mass storage devices but not for booting.

---

### Post by Zach_Feldman on 2013-09-13
Thanks for your reply @sudodus!

So you're saying that I can't just have the boot part on one part of the partition and free space on another?

The original drive that I installed the LiveCD to is 8gb and the new drives are 16gb that I want to clone the LiveCD to. The original drive only has one partition and the new drives have two, one for storing data and one for the bootable liveCD.

Is this setup possible to be cloned onto, or will I need a different setup? I can return the drives and buy 8gb ones I suppose.

---

### Post by sudodus on 2013-09-14
> **Zach_Feldman said:**
> Thanks for your reply @sudodus!

So you're saying that I can't just have the boot part on one part of the partition and free space on another?

I did not say that. And I think we mean different things with the word partition. The boot sector is a small space at the very beginning of the drive. Then there can be one or several partitions with file systems or swap space.
> 
The original drive that I installed the LiveCD to is 8gb and the new drives are 16gb that I want to clone the LiveCD to. The original drive only has one partition and the new drives have two, one for storing data and one for the bootable liveCD.

Is this setup possible to be cloned onto, or will I need a different setup? I can return the drives and buy 8gb ones I suppose.

Please reply to these questions! It makes it easier to give advice :-)

- What is your original source of the Ubuntu 13.04 desktop install system? Is it an iso file or do you only have a live CD?

- Is it a 32-bit or 64-bit system (i386 or amd64)?

- How did you create the 8 GB USB boot drive, and does it work properly? Or did someone give it to you?

- Do you remember the dd command you used to clone the 8 GB drive to the 16 GB drive? If so, please post it!

If you want to use the whole 16 GB drive, there might be better methods than to clone the 8 GB drive, for example you can use Unetbootin to make 16 GB drive an Ubuntu boot drive directly from the iso file (if you have it). It might also be possible to use gparted after the cloning to edit the partition table of the 16 GB drive and make the unallocated space available.

---

### Post by Zach_Feldman on 2013-09-14
Huh, I did not know that! Cool!

-The original source of the Ubuntu 13.04 peristent LiveCD system that I have on this USB hard drive was a .iso file from the Ubuntu website. I built the liveCD usb using UNetBootin on a Windows 7 laptop.

-Not exactly sure on this one, but I think 64 bit.

-I created it with UNetBootin and it works really well. I also set it to be persistent, which is why I want to just clone it because it has the perfect setup as is.

-I used the standard DD command with no options.


Something I just tried was to rip the .iso image from the 8gb drive and then put it on the 16gb drive using UNetBootin. Unfortunately, I got the message "This will not boot on a mac, only on a Windows PC." Tried it out anyway on my Macbook Pro and no joy.

Thanks for your help so far!

---

### Post by sudodus on 2013-09-14
> **Zach_Feldman said:**
> 
-The original source of the Ubuntu 13.04 peristent LiveCD system that I have on this USB hard drive was a .iso file from the Ubuntu website. I built the liveCD usb using UNetBootin on a Windows 7 laptop.

-Not exactly sure on this one, but I think 64 bit.

-I created it with UNetBootin and it works really well. I also set it to be persistent, which is why I want to just clone it because it has the perfect setup as is.

That's good.
> 
-I used the standard DD command with no options.

Was it like this?
```
sudo dd if=/dev/sdx of=/dev/sdy
```
> 
Something I just tried was to rip the .iso image from the 8gb drive and then put it on the 16gb drive using UNetBootin. Unfortunately, I got the message "This will not boot on a mac, only on a Windows PC." Tried it out anyway on my Macbook Pro and no joy.

Thanks for your help so far!

According to [another thread]("http://ubuntuforums.org/showthread.php?t=2168286") at these forums, Macs can be fuzzy about minor details with USB boot drives. And after the cloning there is a small difference between the drives. The cloned part of it is exactly the same, but the sizes are different. A PC won't bother about it, but maybe a Mac. Would it work if you use dd in MacOS as described by *Quackers* in that other tread?

---

### Post by Quackers on 2013-09-14
Hi there. 
As described above by sudodus I just dd'd the Ubuntu.iso direct to the usb on a Mac and it booted fine, but note that this was NOT a persistent type.

---

### Post by Zach_Feldman on 2013-09-15
Thanks for chiming in Quackers. Yeah, I tried DDing my persistent LiveCD as described above and it just didn't seem to work. All the files copied over but my Mac didn't pick up that the bootable partition was there - only when I plugged in the original USB.

---

### Post by Quackers on 2013-09-15
You're welcome.
I've found out a few things. Take a look at the thread below. It's probably a bit daunting and there are dangers, but it worked for me.
I would say though, that if you're not reasonably confident that you can do what's required then don't try - with all due respect to you.

[http://ubuntuforums.org/showthread.php?t=2174630]("http://ubuntuforums.org/showthread.php?t=2174630")

---

