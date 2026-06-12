---
title: "Installing on second hard drive"
date: 2011-11-20
forum: Installation &amp; Upgrades
---

### Post by Scott Swinyard on 2011-11-20
It's been a while but I was thinking I might like to install Ubuntu on my second hard drive (pata ide system slaved on the primary channel). I took a look at Unity on a live cd and it looks pretty nice to me. The thing is I have another distro (openSUSE 12.1) on my first drive and I don't want to mess around changing bootloaders. Besides, I like the one I have... Can I install Ubuntu on my second drive and not install a bootloader with it or affect the one I already have? 

How? 

Hopefully the bootloader that's already installed will see Ubuntu and give me the option to boot it too.

---

### Post by Elfy on 2011-11-20
When you install - choose something else at the partitioner.

Pick your partitions to install to - at the bottom there is an option to change bootloader, choose whatever partition you are installing to - eg if / is on sdb1 then install grub to sdb1 - when I am installing other things and want to keep grub as it is I install grub to the partition.

Then add it to the opensuse bootloader - not looked at that in detail for a long time - I have to assume you can do so.

---

### Post by Scott Swinyard on 2011-11-20
I am assuming that you are telling me that if I install the Ubuntu bootloader to sdb1 that it will not be the active one.The openSUSE bootloader will be the active one since it's on the master drive.

If so that makes sense to me, but is there no option to simply tell it not to install a bootloader?

---

### Post by Elfy on 2011-11-20
> **Scott Swinyard said:**
> I am assuming that you are telling me that if I install the Ubuntu bootloader to sdb1 that it will not be the active one.The openSUSE bootloader will be the active one since it's on the master drive.

If so that makes sense to me, but is there no option to simply tell it not to install a bootloader?

I am saying that.

I'm not sure if there's an option to not install a bootloader as I've never looked that far.

If there is perhaps you'd be good enough to let me know :)

---

### Post by Scott Swinyard on 2011-11-20
Sure thing.


Thanks.

---

### Post by darkod on 2011-11-20
In the latest 11.10 there is no option not to install the bootloader. Earlier there was.
I'm not sure if it's a bug in 11.10 or they decided not to offer the option any more. So you have to install it somewhere.
If it's on a partition it's more or less the same as inactive.
Another option is to install it on the MBR of /dev/sdb. I guess the suse bootloader is on /dev/sda. If you keep booting from /dev/sda it makes no difference what bootloader is on /dev/sdb.
And in case of emergency, if you boot from /dev/sdb it will work. Putting it on a partition will make the computer unbootable if anything happened to the suse bootloader.

---

### Post by Scott Swinyard on 2011-11-20
That's pretty much what I thought, but I just didn't want to get into it not be able to find out and fubar my setup. 

Thanks for the info.

---

### Post by Scott Swinyard on 2011-11-21
Nope. No option not to install. I don't remember the exact options given but that one wasn't there. Anyway it's in there and happily running alongside the other distro with a little help form the openSUSE forum with setting up the bootloader.

 It would seem that Ubuntu is using a newer more sophisticated form of grub though.

---

### Post by Elfy on 2011-11-21
Glad you're all ok then. Can you mark the thread solved.

---

### Post by Scott Swinyard on 2011-11-21
Oh.. O.K. How do I do that?

---

### Post by Elfy on 2011-11-22
Thread tools - at the top of the thread.

---

