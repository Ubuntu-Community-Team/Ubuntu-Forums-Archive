---
title: "dual booting 11.04 w/ MS Windows 7"
date: 2012-04-07
forum: Installation &amp; Upgrades
---

### Post by davidmaxwaterman on 2012-04-07
Hi,

I have looked up the advice on dual booting ubuntu with Window7, but they all seem to assume a rather more complex setup - I think mine is simpler :

1) I have been using my computer with several drives for a while
2) I unplugged the above drives and plugged in a separate drive onto which I installed W7[1]

I have not put the system back to the original drives and am now considering a dual boot set up so I can use W7 in future without having to unplug/plug anything.

I guess it's something simple with the grub menu.

Can anyone advise?

Regards,

Max.

[1] and used it for the immediate need I had (upgrade a WP7 phone)

---

### Post by Basher101 on 2012-04-07
If you have multiple drives, dualbooting is a piece of cake when the OSs are not on the same drive. Simply install Ubuntu on the other drive and choose it as the first in the Bootorder (in the BIOS) form there on Grub will scan all devices for bootable Operating systems.

---

### Post by davidmaxwaterman on 2012-04-07
> **Basher101 said:**
> If you have multiple drives, dualbooting is a piece of cake when the OSs are not on the same drive. Simply install Ubuntu on the other drive and choose it as the first in the Bootorder (in the BIOS) form there on Grub will scan all devices for bootable Operating systems.

I already have both Ubuntu and W7 installed, on separate drives (RAID1 for ubuntu and a single drive for W7).

As I have it now, it boots to Ubuntu, and the W7 drive isn't plugged in.

Are you then saying that W7 will just appear on my current grub menu?

I'm a little hesitant because W7 can be a bit single-minded and I worry it'll screw with my other drives (I'm not too familiar with W7 since I hardly ever have to deal with it).

Max.

---

### Post by Basher101 on 2012-04-07
no it will not just pop up on it's own. It will only happen automatically if you install a new kernel. You will need to re-create your grub config with the command ```
sudo update-grub
``` then it will scan all drives and partitions for bootloaders and take them in the list. From then on you can boot it.

And no worries, the Operating systems are on different drives, they wont mess with each other (unless you mount them and write the wrong stuff onto them). Keep in mind that windows **_cannot_** see Ubuntu partitions. It only sees that they are there, but cannot access them in any way.

---

### Post by davidmaxwaterman on 2012-04-07
> **Basher101 said:**
> no it will not just pop up on it's own. It will only happen automatically if you install a new kernel. You will need to re-create your grub config with the command ```
sudo update-grub
``` then it will scan all drives and partitions for bootloaders and take them in the list. From then on you can boot it.

And no worries, the Operating systems are on different drives, they wont mess with each other (unless you mount them and write the wrong stuff onto them). Keep in mind that windows **_cannot_** see Ubuntu partitions. It only sees that they are there, but cannot access them in any way.

Excellent. Thanks!
[edit: worked perfectly]

Max.
PS. So quick too!

---

### Post by Basher101 on 2012-04-07
> **davidmaxwaterman said:**
> Excellent. Thanks!

Max.
PS. So quick too!

no problem.

p.s. i spam the "New Posts" button all the time :D

---

### Post by davidmaxwaterman on 2012-04-07
One quick post-question question...

When I boot into ubuntu, it seems to think the Windows7 disk is a RAID array. It was from an array (RAID5 mdadm). I see from mdadm that it still thinks it is part of a RAID5 array, and this stops the boot sequence. I check from the busybox prompt which arrays are ok, so it isn't a big deal, but I'd like to make it so this doesn't happen unless it is one of the real arrays I have.

How can I make the system realise this isn't part of an array any more? Preferably without screwing up the MS Windows installation on that disk. I had thought installing Microsoft stuff on there would have completely wiped it, but seems not. Perhaps it's something else...

Max.

---

### Post by oldfred on 2012-04-07
RAID drives remember meta data that messes with everything else if you do not want RAID. Only run this on the drive that is not RAID or you will break your RAID. Double check which drive is not the RAID drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
In your case OR not both:
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

---

### Post by davidmaxwaterman on 2012-04-08
> **oldfred said:**
> RAID drives remember meta data that messes with everything else if you do not want RAID. Only run this on the drive that is not RAID or you will break your RAID. Double check which drive is not the RAID drive.

Presence1960 on remove old raid setting from HD
[http://ubuntuforums.org/showthread.php?t=1325650](http://ubuntuforums.org/showthread.php?t=1325650)
sudo dmraid -E -r /dev/sda
In your case OR not both:
sudo dmraid -E -r /dev/sdb
Also check BIOS for raid settings
More discusion:
[http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738](http://wwww.ubuntuforums.org/showthread.php?p=9274738#post9274738)

Anyway to do this using mdadm instead? I've never used dmraid for my arrays and dmraid isn't even installed, so I'm not sure it'll do the right thing.

---

### Post by oldfred on 2012-04-08
Good question. We have seen the dmraid solution work many times, even on drives users thought they never had RAID. I do not use RAID, but know there are a variety of versions. 

Is there a similar command in mdadm?

---

### Post by davidmaxwaterman on 2012-04-08
> **oldfred said:**
> Good question. We have seen the dmraid solution work many times, even on drives users thought they never had RAID. I do not use RAID, but know there are a variety of versions. 

Is there a similar command in mdadm?

well, the --zero-superblock option seemed to work.

--zero-superblock
If the device contains a valid md superblock, the block is overwritten with zeros. With --force the block where the superblock would be is overwritten even if it doesn't appear to be valid

I didn't use the force option.

Both OSes seemed to still work as expected.

---

