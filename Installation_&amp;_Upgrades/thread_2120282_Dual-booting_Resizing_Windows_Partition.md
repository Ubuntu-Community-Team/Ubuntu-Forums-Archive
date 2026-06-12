---
title: "Dual-booting: Resizing Windows Partition"
date: 2013-02-26
forum: Installation &amp; Upgrades
---

### Post by charlescarroll1 on 2013-02-26
Currently, I'm dual-booting Ubuntu 12.10 with Windows 7. Initially I created two partitions and installed Win7 on the larger partition and Ubuntu on the smaller one. I did this because I figured I'd be installing several larger games which I never ended up doing (I don't play games as much as I thought I would). I still Win7 from time to time for random things, but for the most part I don't really use it much and I'd like to increase the size of my Ubuntu partition since it is my primary OS.

I have a 320GB hard drive - Win7 with 210GB and Ubuntu with the remaining amount. I've done some searching and have seen mixed opinions. Before I follow one of these guides, I want to be sure I don't end up screwing up either OS.

Is accomplishing this as simple as editing the partition sizes with GParted or must I do something else? Or is this even possible without deleting/screwing up one or both partitions/OSes?

Thanks!

---

### Post by schragge on 2013-02-26
> or must I do something else?Backup your data. :rolleyes:

---

### Post by charlescarroll1 on 2013-02-26
> **schragge said:**
> Backup your data. :rolleyes:

All my data is already backed on another hard drive :guitar::guitar::guitar:

---

### Post by darkod on 2013-02-26
Don't resize the win7 system partition with gparted. It doesn't like linux tools touching it.

Use windows Disk Management to shrink the partition for as much as you want to. You might need to turn off the hibernation and swap files if it doesn't let you shrink as much as you want, because it often puts system files towards the back of the partition. So, even if you have 100GB free space on that partition, you might find out that windows allows you to shrink 500MB only. :)

If you get into this situation google around for solutions.

You could resize with Gparted but windows needs chkdsk after that and it might not be able to boot without chkdsk but you need it running to run the chkdsk, so you might find yourself in catch 22.

That's why it's better to try windows Disk Management first.

Also, make a windows rescue cd which can help with basic issues, and it might even be able to open a command prompt for you to run chkdsk.

---

### Post by charlescarroll1 on 2013-02-27
Yeah I'll try that, thanks!

Like I said, Ubuntu is my primary OS, so if need be I can delete the Windows partition, resize, then reinstall - this is if I can't find an easier solution.

So, hypothetically if I do go the route where I delete windows and reinstall later, would I simply edit my Ubuntu partition from Gparted? And that's that?

---

### Post by carl4926 on 2013-02-27
Ideally, make all the right choices now.
Shrink windows (but defrag it first)
I do suggest you keep windows in place though.
Only shrink in half the free space you have. So if windows has 100GB of free space, only take 50GB...
(Regardless of what has already been said. I use Gparted) But I agree with the advice.

I carve my HD up so as to have 2 Linux OS side by side. On this I have openSUSE and Xubuntu. See
[http://paste.opensuse.org/75210480](http://paste.opensuse.org/75210480)

I use  separate / and /home for each

---

### Post by Mark Phelps on 2013-02-27
> **darkod said:**
> Don't resize the win7 system partition with gparted. It doesn't like linux tools touching it.

BIG +1 on this!!  Use ONLY the Win7 Disk Management tool; do NOT use GParted.  Don't be surprised if the Win7 tool doesn't let you shrink it much -- it probably won't let you go anywhere near a 50% reduction.  If you decide to use Gparted to get around that, you're likely to corrupt Win7.

BEFORE you do this, if you want to be able to get back to using Win7 after the dual-boot, do yourself a favor now and use the Win7 Backup feature to create and burn the WIn7 Repair CD.  At least with that, if the Win7 boot loader gets corrupted, you have a way to repair it.

---

### Post by carl4926 on 2013-02-27
I'm not advocating it.
But I've lost count of the number of windows installs I have shrunk with gparted and never a problem yet. I do have a fairly strict set of ground rules though. And have to hand all the things I might ever need to get me out of the (brown smelly stuff) should I need.

---

