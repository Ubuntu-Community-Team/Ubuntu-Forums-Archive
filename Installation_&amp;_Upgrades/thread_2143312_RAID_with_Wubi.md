---
title: "RAID with Wubi"
date: 2013-05-08
forum: Installation &amp; Upgrades
---

### Post by MeltedFlame on 2013-05-08
> Hi there, [INDENT]First post here in this beautiful domain. Shame it has to be such a desperate one...

[/INDENT]


[LIST]
[*]I have two HDD's in SATA 1&2 acting as a RAID 1 Device(virtually utilizing the smaller HDD only) and a HDD in SATA 5.
[*]Firstly, I installed Windows Vista x86
[*]Secondly, I installed Ubuntu 12.04.2 LTS(beautiful :-D)
[*]Third, I create my RAID Setup and it worked fine in Ubuntu, then didn't appear in Windows. Not a problem.
[/LIST]

So, I was switching back and forth as required, untill today when I try to boot into Ubuntu - I am automatically put into grub> mode with no way of getting into my Ubuntu System. The only reasons I can think of is that when I changed Permissions of the C:\ in Windows to my Windows User account, it's messed up some files along the way. Possible, that the RAID drivers I installed in Windows; attempting to see the invisible drive did something too? //noob. 

I would really appreciate some Feedback on this as I have a "$%! load of work on Ubuntu System!

...Here's what boot-repair-loader came up with;
 


[http://paste.ubuntu.com/5645465/](http://paste.ubuntu.com/5645465/)

---

### Post by MeltedFlame on 2013-05-08
I've noticed in the pastebin url, there's a lot mentioning the RAID device - I'm not quite sure but it looks like ubuntu/the boot-repair-loader is recognising the device as the root for the operating system(further down the log). If that is true, this was not the case, before the problem. The ubuntu system is on the SATA 5 HDD. Not the RAID.

At the beginning of the log, it states the loader was unable to mount or the sda is busy.

and then some unknown boot loaders.



[COLOR=#000000]Unknown BootLoader on sdc1/WubiUnknown BootLoader on [/COLOR][COLOR=#B8860B]pdc_djjihefgei1[/COLOR][COLOR=#000000]Could this have something to do with files I have on the c:\ ??Thanks,Dan.[/COLOR]

---

### Post by darkod on 2013-05-09
First, and before we go any further, you DON'T have ubuntu, you have wubi. It's not the same. Wubi is simply a virtual ubuntu inside windows, and it depends on windows, it's not a real dual boot with OSs running on their separate partitions. As you already saw, if windows breaks down or changes some wrong files, it will affect wubi also, which is not the case with dual boot.

if you plan any serious work in ubuntu you need to install a proper dual boot on its own linux partitions (it doesn't install on ntfs). Wubi is just for a quick try, and very soon issues start showing up especially if you try to upgrade to a newer release later.

---

### Post by mörgæs on 2013-05-09
Have changed the thread title accordingly.

---

### Post by MeltedFlame on 2013-05-09
> **darkod said:**
> First, and before we go any further, you DON'T have ubuntu, you have wubi. It's not the same. Wubi is simply a virtual ubuntu inside windows, and it depends on windows, it's not a real dual boot with OSs running on their separate partitions. As you already saw, if windows breaks down or changes some wrong files, it will affect wubi also, which is not the case with dual boot.

if you plan any serious work in ubuntu you need to install a proper dual boot on its own linux partitions (it doesn't install on ntfs). Wubi is just for a quick try, and very soon issues start showing up especially if you try to upgrade to a newer release later.

Ahh, daym - I realised it depended on the c:\ but not windows itsself, as it it has its own 'ubuntu' dir in the c:\. Oh my, I'm destroyed - is there no way I can retrieve my files from the Wubi?

---

### Post by MeltedFlame on 2013-05-09
TY, Sir.

---

### Post by darkod on 2013-05-09
No, the data is not lost. But I don't use wubi and don't know the procedure right now. Let me google something.

---

### Post by bcbc on 2013-05-09
You're missing the root.disk. You can review this:  [http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html](http://ubuntu-with-wubi.blogspot.ca/2011/08/missing-rootdisk.html)

---

### Post by MeltedFlame on 2013-05-09
Thank you for the replies!

In the end, my boot.disk was 0kb and the recovery of 'found.000' directory didn't give me enough information to retrieve the enitre boot.disk...

I will be reinstalling ubuntu using a USB stick, without the Wubi installer, on a completely different disk to my Windows OR just not using Windows, at all.

---

