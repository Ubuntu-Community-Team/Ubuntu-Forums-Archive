---
title: "Delete Ubuntu, but keep the GRUB"
date: 2010-01-06
forum: Installation &amp; Upgrades
---

### Post by M4up on 2010-01-06
Hello all,

First let me explain my situation.
I made a partition for Ubuntu to install on, but unfortunately Ubuntu did not recognize it. So it installed on my main partition.
Anyway, I checked to make sure that there was nothing on my new made partition and I then deleted it. (There where 0 bytes used)
My computer needed to reboot and then I got a GRUB error saying the GRUB could not be found..
So lucky for me I still had the Ubuntu CD, so I just installed Ubuntu again to install the GRUB (2 times now). So now I have 1x Windows and 2x Ubuntu.
So my question is: how do I get the last installed Ubuntu version deleted from my hard-drive without deleting the GRUB? Because I need the GRUB to dual-boot Windows and Ubuntu.

Thank you for reading,
Maup.

---

### Post by oldos2er on 2010-01-06
Are you saying you have Ubuntu installed twice? Could you boot from either one, and post the output from ```
sudo fdisk -l
``` ?

---

### Post by efflandt on 2010-01-06
I had a somewhat similar issue with both 32-bit 9.10 on sda3 and 64-bit on sda6 (with standard mbr, grub2 on sda3 marked as boot, configured from 64-bit on sda6).  Somehow kernel updates on 32-bit 9.10 it took over grub2 on sda3, so it could no longer be updated from 64-bit ubuntu on sda6.

A web search for "grub2 ubuntu" found the wiki at [https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2), and from that I found that I could get it back to setting up grub on sda3 from 64-bit on sda6 by doing sudo grub-install /dev/sda3 from 64-bit on the other partition.

But of course if your grub2 is in the mbr of your main drive, you should boot the ubuntu you want to keep, and do **sudo grub-install /dev/sda** from there.  Then **sudo update-grub** should work from there, and you should be able to remove or change the partition you no longer want.  But before removing/reformatting any partitions, make sure that the top of the grub menu boots to the ubuntu you want to keep and the alternate linux menu options farther down point to the partition you want to remove.  After you remove or reformat the unwanted partition, "sudo update-grub" should no long show the removed partition.

---

### Post by M4up on 2010-01-07
> **oldos2er said:**
> Are you saying you have Ubuntu installed twice? Could you boot from either one, and post the output from ```
sudo fdisk -l
``` ?

Yes I can boot from either one.
Here are the results (it's in Dutch, so if you cant understand any of it just say so and I will try to translate):
Schijf /dev/sda: 320.1 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
```
Schijf-ID: 0x64862885

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       26125   209848038+   7  HPFS/NTFS
/dev/sda3           26126       38913   102719610    5  Uitgebreid
/dev/sda5           32505       38645    49327551   83  Linux
/dev/sda6           38646       38913     2152678+  82  Linux wisselgeheugen
/dev/sda7           26126       32237    49094577   83  Linux
/dev/sda8           32238       32504     2144646   82  Linux wisselgeheugen

Partitietabel-items liggen niet in schijfvolgorde.
```

---

### Post by VastOne on 2010-01-07
> **M4up said:**
> Hello all,

First let me explain my situation.
I made a partition for Ubuntu to install on, but unfortunately Ubuntu did not recognize it. So it installed on my main partition.
Anyway, I checked to make sure that there was nothing on my new made partition and I then deleted it. (There where 0 bytes used)
My computer needed to reboot and then I got a GRUB error saying the GRUB could not be found..
So lucky for me I still had the Ubuntu CD, so I just installed Ubuntu again to install the GRUB (2 times now). So now I have 1x Windows and 2x Ubuntu.
So my question is: how do I get the last installed Ubuntu version deleted from my hard-drive without deleting the GRUB? Because I need the GRUB to dual-boot Windows and Ubuntu.

Thank you for reading,
Maup.

If you are wanting to get back to a Windows only machine you do not need grub

Follow this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=777135](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=777135)

---

### Post by kansasnoob on 2010-01-07
> **VastOne said:**
> If you are wanting to get back to a Windows only machine you do not need grub

Follow this thread

[http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=777135](http://ubuntu-virginia.ubuntuforums.org/showthread.php?t=777135)

I believe the OP wants to get rid of only one Ubuntu.

---

### Post by kansasnoob on 2010-01-07
> **M4up said:**
> Yes I can boot from either one.
Here are the results (it's in Dutch, so if you cant understand any of it just say so and I will try to translate):
Schijf /dev/sda: 320.1 GB, 320072933376 bytes
255 koppen, 63 sectoren/spoor, 38913 cilinders
Eenheid = cilinders van 16065 * 512 = 8225280 bytes
```
Schijf-ID: 0x64862885

 Apparaat Opstart   Begin       Einde     Blokken   ID  Systeem
/dev/sda1   *           1       26125   209848038+   7  HPFS/NTFS
/dev/sda3           26126       38913   102719610    5  Uitgebreid
/dev/sda5           32505       38645    49327551   83  Linux
/dev/sda6           38646       38913     2152678+  82  Linux wisselgeheugen
/dev/sda7           26126       32237    49094577   83  Linux
/dev/sda8           32238       32504     2144646   82  Linux wisselgeheugen

Partitietabel-items liggen niet in schijfvolgorde.
```

You'll notice at the bottom of the fdisk -l output it says "Partition table entries are not in disk order", but if the partitions are actually:

sda1-sda3-sda5-sda6-sda7-sda8

And sda1 is windows, sda3 is extended, sda5 & sda6 are the root and swap partitions for one Ubuntu, and sda7 & sda8 are the root and swap partitions for the other Ubuntu then you need to figure out which Ubuntu you wish to keep.

Because moving or resizing SWAP causes UUID problems (we can fix it but why bother if not necessary) it would be easier to keep the Ubuntu that uses the SWAP that's furthest to the right in Gparted.

So first just take a look, if you haven't already done so install gparted (don't use it to make any changes just yet):

```
sudo apt-get install gparted
```

You'll then find it in System > Administration:

[ATTACH]142784[/ATTACH]

I know mine is a bloody mess but thought it might help you understand. You can see from the keychains toward the left that sda11, 12, 9 & 2 are mounted (note: I have a separate /home).

So if you look at yours you should be able to see which Ubuntu you're booted into, which swap is being used, etc. If in fact sda7 and sda8 are "married" and they are the furthest to the right they would be the easiest to keep.

Are you able to boot both Ubuntu's? Do you prefer one over the other?

Basically if you delete the one you don't want while mounted into the one you do want Gparted will stop you from deleting the one that is mounted, then you would have to boot a Live CD choosing "Try without changes .." and use Gparted from the Live Desktop to resize the Ubuntu you kept.

Notes of warning: If you move or resize SWAP you will probably have UUID problems, like SWAP won't mount at boot and you'll lose the "quiet splash".

**[COLOR="Red"]If your Windows is Vista or Win 7 it is best to resize it using only it's own tools![/COLOR]**

Have I confused you yet?????????

---

### Post by darkod on 2010-01-07
Depending whether you already started installing programs and personal data on the Ubuntus, I would actually delete both ubuntu installs. You can delete only one, but then you will have that space useless unless you expand the other ubuntu. This can be more complicated for someone new to linux, than another install.
If you decide to delete both of them, do:
Boot with ubuntu cd, Try Ubuntu option. Open Gparted. Both swap partitions you have will probably be mounted, /dev/sda6 and /dev/sda8. Right click on each and select Swapoff, that will make the keys symbol go away and you can work with the partition.
Delete all logical partitions, from /dev/sda5 to /dev/sda8. Then also delete the extended partition, /dev/sda3.
DO NOT create any partitions for ubuntu. Leave the space as unallocated.
Then boot with the ubuntu cd again, select Install Ubuntu, and tell it to use Largest Available Free space. That will install it in the unallocated space you created.

And for future reference, do NOT create partitions for linux in advance, especially if you did it from windows. Maybe that's why you say the installer didn't recognize it. Linux doesn't work like windows and it's more complicated to set it to use existing partitions (if you haven't done it before), than create them during the install.
That's why there is no need to create any partition in advance, even if you want to create them manually do it during the install process. Besides, standard ubuntu setup needs two partitions, root and swap, not just one.

---

### Post by M4up on 2010-01-07
> **kansasnoob said:**
> You'll notice at the bottom of the fdisk -l output it says "Partition table entries are not in disk order", but if the partitions are actually:

sda1-sda3-sda5-sda6-sda7-sda8

And sda1 is windows, sda3 is extended, sda5 & sda6 are the root and swap partitions for one Ubuntu, and sda7 & sda8 are the root and swap partitions for the other Ubuntu then you need to figure out which Ubuntu you wish to keep.

Because moving or resizing SWAP causes UUID problems (we can fix it but why bother if not necessary) it would be easier to keep the Ubuntu that uses the SWAP that's furthest to the right in Gparted.

So first just take a look, if you haven't already done so install gparted (don't use it to make any changes just yet):

```
sudo apt-get install gparted
```

You'll then find it in System > Administration:

[ATTACH]142784[/ATTACH]

I know mine is a bloody mess but thought it might help you understand. You can see from the keychains toward the left that sda11, 12, 9 & 2 are mounted (note: I have a separate /home).

So if you look at yours you should be able to see which Ubuntu you're booted into, which swap is being used, etc. If in fact sda7 and sda8 are "married" and they are the furthest to the right they would be the easiest to keep.

Are you able to boot both Ubuntu's? Do you prefer one over the other?

Basically if you delete the one you don't want while mounted into the one you do want Gparted will stop you from deleting the one that is mounted, then you would have to boot a Live CD choosing "Try without changes .." and use Gparted from the Live Desktop to resize the Ubuntu you kept.

Notes of warning: If you move or resize SWAP you will probably have UUID problems, like SWAP won't mount at boot and you'll lose the "quiet splash".

**[COLOR="Red"]If your Windows is Vista or Win 7 it is best to resize it using only it's own tools![/COLOR]**

Have I confused you yet?????????

Hey,

So I installed GParted and I got this:
[see attachment]

As you can see, I already have some personal files on my first Linux install. So it was fairly easy to recognize sda5+6 as my mount.
So I want to delete sda7+8.
I am able to boot both Ubuntu's. Although I don't know if I delete the last version (sda7+8 ), I also delete the GRUB. Because I need that for dual booting Vista and Ubuntu. Because could it be the other Ubuntu version (first one) doesn't have the GRUB anymore (because of deletion)?
Or is it installed separately from each other?

---

### Post by oldfred on 2010-01-07
Boot into the version you want to keep. It still has its grub files but the MBR points to the last ubuntu install.
sudo dpkg-reconfigure grub-pc

After you delete your old install you will have to run this to remove the entries from grub.cfg that pointed to the deleted install.
sudo update-grub.

You still have the space used by the second install and as darko said it can be difficult for a new user to expand the existing. You would have to move swap over and then expand the ubuntu partition. If you delete swap the UUID changes and you will not be able to boot without editing the fstab file. It may just be easier to create a new partition and use it for data.

---

### Post by kansasnoob on 2010-01-07
> **M4up said:**
> Hey,

So I installed GParted and I got this:
[see attachment]

As you can see, I already have some personal files on my first Linux install. So it was fairly easy to recognize sda5+6 as my mount.
So I want to delete sda7+8.
I am able to boot both Ubuntu's. Although I don't know if I delete the last version (sda7+8 ), I also delete the GRUB. Because I need that for dual booting Vista and Ubuntu. Because could it be the other Ubuntu version (first one) doesn't have the GRUB anymore (because of deletion)?
Or is it installed separately from each other?

While booted into the Ubuntu you want to keep (looks like the one on sda5 & 6) just go to terminal and run:

```
sudo grub-install /dev/sda
```

And:

```
sudo update-grub
```

Unless you see errors you'll know that the Ubuntu you're booted into now has control of boot.

Then go ahead and delete the two partitions you don't want, then reboot. Hopefully that'll work fine so just go to terminal and run:

```
sudo update-grub
```

That should get rid of the unwanted menu items, then use your Ubuntu Live CD, that is reboot into the Live desktop and expand the Ubuntu partition you kept (I think sda5) to the left.

Since there is data on that partition it could take a while, just be patient and if this is a laptop be sure it's either fully charged or plugged in!

You could experience data loss or the need to reinstall if there is a power outage or such!

---

### Post by M4up on 2010-01-07
> **oldfred said:**
> Boot into the version you want to keep. It still has its grub files but the MBR points to the last ubuntu install.
sudo dpkg-reconfigure grub-pc

After you delete your old install you will have to run this to remove the entries from grub.cfg that pointed to the deleted install.
sudo update-grub.

You still have the space used by the second install and as darko said it can be difficult for a new user to expand the existing. You would have to move swap over and then expand the ubuntu partition. If you delete swap the UUID changes and you will not be able to boot without editing the fstab file. It may just be easier to create a new partition and use it for data.

Okay so I did the first sudo command, and it gives me this:
[see attachment]

What do I do now?
I'm sorry if this is really basic stuff. I just started to use Ubuntu. So bare with me please.

---

### Post by kansasnoob on 2010-01-07
> **M4up said:**
> Okay so I did the first sudo command, and it gives me this:
[see attachment]

What do I do now?
I'm sorry if this is really basic stuff. I just started to use Ubuntu. So bare with me please.

Skip that and do what I said in the previous post.

---

### Post by kansasnoob on 2010-01-07
In fact I just tried "sudo dpkg-reconfigure grub-pc" and ran into a load of errors so I had to run:

```
sudo apt-get install --reinstall grub-pc
```

And:

```
sudo update-grub
```

To straighten things out.

---

### Post by M4up on 2010-01-08
> **kansasnoob said:**
> While booted into the Ubuntu you want to keep (looks like the one on sda5 & 6) just go to terminal and run:

```
sudo grub-install /dev/sda
```

And:

```
sudo update-grub
```

Unless you see errors you'll know that the Ubuntu you're booted into now has control of boot.

Then go ahead and delete the two partitions you don't want, then reboot. Hopefully that'll work fine so just go to terminal and run:

```
sudo update-grub
```

That should get rid of the unwanted menu items, then use your Ubuntu Live CD, that is reboot into the Live desktop and expand the Ubuntu partition you kept (I think sda5) to the left.

Since there is data on that partition it could take a while, just be patient and if this is a laptop be sure it's either fully charged or plugged in!

You could experience data loss or the need to reinstall if there is a power outage or such!

Thank you very much!
This did the trick for me :)

---

