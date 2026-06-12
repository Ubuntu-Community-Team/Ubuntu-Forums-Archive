---
title: "Karmic - how to edit GRUB?"
date: 2009-12-05
forum: Installation &amp; Upgrades
---

### Post by outerspacerace on 2009-12-05
Hi all,

I've just dual booted Karmic Koala on the same drive I have Windows 7 on.

Karmic works fine while 7 won't boot now, but I can see why.

Grub lists it as Windows 7 (loader) on /dev/sda1

(or something similar from memory)

Well, Windows 7 is actually on sdb1

I thought editing the grub config file would solve this one but I'm greeted with a message saying NOT to edit this file.

What's the best way to solve this problem?

Thanks in advance.

---

### Post by darkod on 2009-12-05
In terminal run
sudo update-grub

to update grub. It should pick it up. If it's still confused, here are the basics of grub2:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

Basically you can add entry in 40_custom something like:

echo "Adding Windows 43_custom" >&2
menuentry "Windows Vista 43_custom" {
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set CFFCFF9EECFF7F49
chainloader +1
}

Edit the title, the root(hd0,1) and the CFFCFF (which is the UUID) accordingly. Have in mind that grub2 is counting the partitions from 1 not from 0 like grub1. So your entry should be root=(hd1,1). Make sure what is hd0 and what hd1, it might not be what you expect. You can find out UUIDs with
sudo blkid

After editing 40_custom you still have to run sudo update-grub again.

---

### Post by outerspacerace on 2009-12-05
Wow!

Thanks for the quick reply.

The results of update-grub are:

Found linux image: /boot/vmlinuz-2.6.31-14-generic
Found initrd image: /boot/initrd.img-2.6.31-14-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Windows 7 (loader) on /dev/sda1
done

...Something doesn't seem right with it finding 7 there.

I'm fairly certain it was installed to sdb1.

What do you think?

---

### Post by darkod on 2009-12-05
OK, first of all, are you sure you are right about what ubuntu calls sda and sdb? It might not be what you expect. Another option is that small 100MB boot partition that win7 sometmes creates. That partition can be /dev/sda1 and your win7 installation to be on /dev/sdb1. Then grub2 would locate correctly the win7 boot files in /dev/sda1.

To take a quick look at your partitions on all drives and their filesystem, just run in terminal:
sudo fdisk -l (small L)

Post the result here if you need some clarification. That will give you just quick overview. If there is a need to look at the boot process in more details there are more advanced methods.

---

### Post by outerspacerace on 2009-12-05
No- I'm not sure actually... thanks for the help and here's the result:

Disk /dev/sda: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xfa057579

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1      969016   488384032+   7  HPFS/NTFS

Disk /dev/sdb: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd297accf

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       44619   358400000    7  HPFS/NTFS
/dev/sdb2           44620       48266    29294527+  83  Linux
/dev/sdb3           48267       60801   100687387+   5  Extended
/dev/sdb5           48267       48509     1951866   82  Linux swap / Solaris
/dev/sdb6           48510       60801    98735458+  83  Linux

Disk /dev/sdc: 500.1 GB, 500107862016 bytes
16 heads, 63 sectors/track, 969021 cylinders
Units = cylinders of 1008 * 512 = 516096 bytes
Disk identifier: 0xb971dd6f

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1      969018   488385040+   7  HPFS/NTFS

---

### Post by darkod on 2009-12-05
You can see from the results that both sda and sdc are 500GB with one single NTFS partition. You actually might have win7 on sda1.
On he other hand sdb1 is also NTFS partition and it might be there. But it's not marked with boot flag (the *) so it doesn't look like it.

I forgot to ask, did you try booting win7 from the grub menu? Only if it doesn't work you have a problem. Just because you expected it to be named sdb1 does not create a problem. :)

I think if you try booting it you will see it's fine.

PS. If the automatic existing entry doesn't work, try the manual entry like I suggested. With sudo blkid you will find the UUID for sdb1 to replace the CFFCFF value. Write it EXACTLY as it is. Do update-grub and reboot and check if the manual entry will work.

---

### Post by outerspacerace on 2009-12-05
It doesn't boot from grub, I checked before I posted.

It gives this error:

error:no such: device: c2d848dad848ce7b

press any key to continue

and 7 is definately - 100% on sdb1.

The other two drives are named Files 1 and Files 2, they both show up in gnome (and GParted) and still have all my files intact.

Here's the weird bit though - there is now a folder called Boot on Files 2 (sda1) which I don't think was there previously. It has files like memtest.exe and bootstat.dat in there.

I'm guessing they are some sort of Windows 7 MBR files (.exe?) and grub has found them, but somehow 7 itself is actually on sdb1.

Confusing stuff - I should have just unplugged all the other frives during the install but it was late and I was lazy.

WHat do you think, am I on the right track with my guesses?

---

### Post by darkod on 2009-12-05
You are. How about the manual entry for windows in 40_custom? Any luck with that?

---

### Post by outerspacerace on 2009-12-05
Hmmm whilst I could probably eventually work it out, it seems fiddly.

Plus I'm guessing if that folder named boot on sdb1 ever gets deleted accidentally I'll have no Windows 7 booting up.

I think the best plan is probably to just delete that boot folder from within ubuntu, unplug both extra drives and start again, installing 7 then Karmic.

What do you reckon?

Cheers.

---

### Post by outerspacerace on 2009-12-05
Actually just deleting that folder, reinstalling 7 then restoring grub should work more quickly I'd imagine.

---

### Post by darkod on 2009-12-05
Yeah, that seems like an easy solution. This can probably be salvaged but it all depends if it's worth the effort.

---

### Post by outerspacerace on 2009-12-05
Thanks heaps, you really helped me work through it, I'll report in as to how I go.

---

### Post by outerspacerace on 2009-12-07
Well that worked fine... for a while.

I had a perfectly working Windows 7/Karmic machine until just now.

Update manager kept asking me to upgrade so I let it run and now I can't boot into 7.

I get:

error: invalid signature

It's a sure thing one of the updates ruined my setup. There was even a message halfway through asking me what to do about grub and I selected the default "keep the local installed version" (from memory) option. 

I've always chosen that in the past with Jaunty and earlier releases and things had been fine, what are they needing to update in regards to grub anyway?


Does anyone know of the easiest way to solve this? 

I just spent a couple of days setting 7 up how I needed it...

Thanks in advance.

---

### Post by outerspacerace on 2009-12-07
Just a heads up for others, when update manager is installing kernel updates and ask you what to do about GRUB - choose use the package maintainers version (or similar option).

It's the first choice in the drop down.

I re-installed karmic, updated right away with that option and I can still get into Windows 7 via GRUB, so all is well.

If only I knew that earlier...

---

