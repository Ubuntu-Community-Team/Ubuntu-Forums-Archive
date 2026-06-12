---
title: "Hoary and Breezy on the same machine?"
date: 2005-10-14
forum: Installation &amp; Upgrades
---

### Post by ngms27 on 2005-10-14
I am currently using Hoary and it worka a treat.

Can I have Breezy installed aswell and have the option which to boot?

For example if I create a new partition and install Breezy on it, will the existing Grub be updated with both OS's? and keep the Windows XP option?

Cab Hoary and Breezy share the same swap partition?

Thanks

JT

---

### Post by Leif on 2005-10-14
the answer to all is yes, it works just fine (I'm doing it too). I had breezy write its own grub though, which recognizes all the rest

---

### Post by mitja on 2005-10-16
[QUOTE=Leif]the answer to all is yes, it works just fine (I'm doing it too). I had breezy write its own grub though, which recognizes all the rest[/QUOTE]

Few questions from a total n00b:

I'm planning to do the same as you. However, I have never created partitions before (yes, I started to use Linux for the first time just few weeks ago - and I have never been such a wizard with Windows either...). So what should I do? I have at the moment Hoary on hdb (Windows XP on hda), which size is 160GB and the partitions and filesystems go like this:

/dev/hdb1 ext3 Size 151GB, used 14GB unused 137GB
/dev/hdb2 extended Size 1GB
  /dev/hdb5 linux-swap Size 1GB

If I start to install Breezy from the cd, is there an option during the installation to make the partition for Hoary smaller and to create a new partition for Breezy? Or do I have to do it separately with GParted before I start to install Breezy? And if so, what should I do: How small partition should I make for Hoary and how big for Breezy? What filesystem should I use for Breezy, ext3? Will both distros use the same swap-partition or is Breezy going to make its own during its installation? What about the /home, will it stay shared with both distros? 

Sorry to bother you with these self-evident facts with my poor english, but what to do: have to start learning from somewhere.

---

### Post by Leif on 2005-10-16
mitja, I'm not sure I understand your filesystem. what's on hdb2 ? and where do you have your /home partition ?

I haven't run the breezy installer, so I don't know if there's a resizing option, but it would probably be best for you to do it beforehand. if I were you, I would have a 10 gb partition for hoary /, 10gb for breezy /, set aside another 10 just in case you want to experiment with something else at some point (gentoo ? suse ? fedora ?), 512mb-1gb for swap, and the rest to a separate /home directory.

I've suggested 10gb for the /s, you could probably do with less, but since you've got 160gb, you can afford it.

during installation, you can tell the installer to mount a partition as /home. this should obviously be the same partition for all installations. swap should be automatically shared, I think. and yes, I'd go with ext3, it's good and safe.

---

### Post by mitja on 2005-10-16
[QUOTE=Leif]mitja, I'm not sure I understand your filesystem. what's on hdb2 ? and where do you have your /home partition ? [/QUOTE]

When I installed Hoary, the hd was new and clean. I made the installation with default settings, and the installer made those partitions itself and took all the space from the hd for Hoary to use. If I understand right, the /hdb5 linux-swap is located inside the /hdb2. I suppose the /home is in the partition hdb1 with the rest of the Hoary. Of course it would have been better to have a separate partition for /home, but because this was my very first Linux installation I didn't no this at that point and the installer made everything automatically.

Here's the print for fdisk -l if it clears the situation for you:

```
Disk /dev/hda: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        1275    10241406    7  HPFS/NTFS
/dev/hda2            1276        4865    28836675    7  HPFS/NTFS

Disk /dev/hdb: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1   *           1       19293   154970991   83  Linux
/dev/hdb2           19294       19457     1317330    5  Extended
/dev/hdb5           19294       19457     1317298+  82  Linux swap / Solaris
```


> I haven't run the breezy installer, so I don't know if there's a resizing option, but it would probably be best for you to do it beforehand. if I were you, I would have a 10 gb partition for hoary /, 10gb for breezy /, set aside another 10 just in case you want to experiment with something else at some point (gentoo ? suse ? fedora ?), 512mb-1gb for swap, and the rest to a separate /home directory.

That sounds reasonable.

> during installation, you can tell the installer to mount a partition as /home. this should obviously be the same partition for all installations. swap should be automatically shared, I think. and yes, I'd go with ext3, it's good and safe.

But what to do because Hoary's /home doesn't have a separate partition now? Is it possible to create a new partition for a common /home, move all the contents from the old Hoary /home to the new and after that tell Hoary to use that one, sharing it with Breezy? Well, I suppose it is, but please tell me how to do it properly :) 

Anyway, thanks for your help, Leif. It's frustrating to be a totally green newbie, and because of that I really appreciate this forum and all you folks helping each other. I hope that after some time of studying the world of Linux I can do somebody same kind of favors too.

The main thing is to keep as much people as possible away from spending all their money to some extremely expensive, buggy and dangerous OS's which will probably just destroy their mental health with all the rebooting, right? :razz:

---

### Post by Leif on 2005-10-16
yes, unfortunately the default install does not give /home a separate partition. I made this mistake the first time around too. the first thing you need to do is resize hdb1 to make space for things to come. you will need to use gparted (or qtparted or some such) for this, but you can't resize the partition once you've logged in, as you're using it already.

ok, first off, backup everything !

what I'd suggest you do next is download the knoppix livecd if you can, it's a great tool to have anyway. boot using the livecd, start parted, and resize hdb1 to 15gb (because you've got 14 gb on it right now, you can trim it down later if you want to). create as many 10gb partitions for new OSs as you want (maybe 2?). allocate the rest to another partition, which will become /home. note which one this is - I'll assume hdb6, but change as needed.

also, since grub is on hdb1 right now, I assume its position won't be changed. if it does get changed, you'll need a bit more tweaking at this stage. let me know if so. (but this shouldn't happen, so don't worry)

boot into hoary, and create a temporary folder to mount your new home partition. type "sudo mkdir /media/temphome", "mount /dev/hdb6 /media/temphome". now copy everything from your existing home folder over using "cp -R ~/* /media/temphome".

type "sudo gedit /etc/fstab". this file tells which partitions to mount where by default during boot. add the line "/dev/hdb6       /home           ext3    defaults        0       2". save and exit. reboot.

you should now be using your new home partition !

now when you want to install breezy, go for "manual partitioning", tell it to use one of the 10gb partitions you created as /. turn the bootable flag on. scroll down to your /home partition, and tell it to mount it as /home. it should recognise the swap partition by itself, I think. the installer should only want to format the / partition, and not the /home partition. watch out for this 

let the installer do its thing, and you should now be able to boot from breezy, but if you scroll down in the boot menu, you should notice your old kernels, which will boot you to hoary.

mitja, I should warn you that I'm writing this from memory, and I may have forgotten some step or such. please opt for safety, and write back if you're not sure of anything.

good luck !

---

### Post by mitja on 2005-10-17
OK, thanks for the instructions. I will try them in couple of days right a way when I have enough time to do it, and I'll let you know then what happened.

---

