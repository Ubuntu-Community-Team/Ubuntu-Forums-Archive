---
title: "Can't boot Ubuntu after a kernel upgrade"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by ihristov on 2007-06-28
I managed to hose my Ubuntu installation and can no longer boot into it. I bet it is my fault, cause I messed with the system, but if someone can point out what I missed I would appreciate it.

BTW: I ended up re-installing with the new partition setup and then the upgrade worked correctly.

This is a bit long, so hold on to your hats:)

Here is what happened:

1) A Sony desktop circa 2001. HDD is 200 GB. BIOS shows it as being 8 GB, but it has WinXP installed which was taking the whole disk
2) Installed Ubuntu. Selected manual partitioning. Resized Windows down to 6 GB. Created a root primary Ubuntu partition of 10 GB, a swap logical partition of 1.7 GB and installed it. Left the rest of the disk empty with the idea to create a new NTFS partition (drive D:) later
3) After it was done and rebooted GRUB menu would show up and I can boot WinXP. Attempting to boot Ubuntu however resulted in GRUB saying Error 18. I was not aware of this, but apparently when the BIOS has this limitation the whole boot partition has to be below the 1023 cylinder. In other words both the start and the end cylinder need to be < 1024
4) At this point I decided that I can simply copy the data from the root partition and reformat with different partitions. This is what I did. The end result was 

```

# before the upgrade
$ uname -a
Linux my-sony 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686 GNU/Linux

$ sudo fdisk -l /dev/sda

Disk /dev/sda: 200.0 GB, 200049647616 bytes
255 heads, 63 sectors/track, 24321 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         791     6353676    7  HPFS/NTFS
/dev/sda2             792         842      409657+  83  Linux
/dev/sda3             843        2291    11639092+  83  Linux
/dev/sda4            2292       24321   176955975    5  Extended
/dev/sda5            2292        2508     1743021   82  Linux swap / Solaris
/dev/sda6            2509       24321   175212891    7  HPFS/NTFS
```

Note: Not sure why the IDE disk is seen as sda right now. I was normally seeing it as hda. This is not important. Assume hda == sda

I then
1) copied all the files back to the root partition (hda3). 
2) copied the /boot folder to the new boot partition (hda2)
3) modified /etc/fstab to reflect the change and also update the UUID of the partitions, because I had to delete the original hda2

I then rebooted and was able to boot into Ubuntu. Can't remember it failed the first time and I had to fix the GRUB using [Super GRUB disk]("http://sgd.howto-linux.de/")

At this point all was working as expected. I could boot onto WinXP and onto the Ubuntu 2.6.20-15 kernel without problem.

Then automatic update told me I have pending updates and I installed them. It included a new kernel (2.6.20-16). After it was installed an I rebooted I could not longer boot into Ubuntu. Any GRUB item (with any changed boot parameter I could think of) would bomb. The error is:

```
mount: Mounting /root/dev on /dev/.static/dev failed: No such file or directory
mount: Mounting /sys on /root/sys failed: No such file or directory
mount: Mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
```

As far as I understand it for some reason the initrd is not mounting the partitions correctly. In other words it still thinks that there is only one root partition and the boot folder is on it.

I could not recover from this and had to re-install. 

I assume I could have tried to open initrd.img and modify something there, but I am not sure how.

Any comments?

---

### Post by Herman on 2007-06-28
Hello ihristov,
It looks like you did everything right but did you remember to edit your automagic kernels list in your /boot/grub/menu.lst file?
These are the sections of the menu.lst file I am referring to,  [kopt=]("http://users.bigpond.net.au/hermanzone/p15.htm#kopt") (kernel options) and                                                   [groot=]("http://users.bigpond.net.au/hermanzone/p15.htm#groot") (grub root device), especailly the groot one.  If you click on those links you will be able to read the explanation of what I am talking about.
Would that have been it?

You did an excellent job coping with GRUB [error 18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18"), that can be a really tough one. I don't know if I would do as well myself. Have you got any tips about how I should edit my GRUB error 18 link to improve it? You probably have more experience than me now, especially with that error. Thanks in advance.

Regards, Herman :D

---

### Post by ihristov on 2007-06-28
I kept a copy of the boot folder as it was and I can see that I did not modify menu.lst.

I think however this is not relevant, because groot is supposed to point to the boot partition, which it did. As I mentioned, I am not 100% sure, but I think I was not able to boot the first time I rebooted after the repartitioning, but then I fixed it using the [Super GRUB disk]("http://sgd.howto-linux.de/"). Also tried several other "Super GRUB" options like trying to boot directly from the 2nd partition, etc.

I still think this has something to do with the initrd.img, because it's initrd.img which decides how to mount things.

---

### Post by ihristov on 2007-06-28
> **Herman said:**
> 
You did an excellent job coping with GRUB [error 18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18"), that can be a really tough one. I don't know if I would do as well myself. Have you got any tips about how I should edit my GRUB error 18 link to improve it? You probably have more experience than me now, especially with that error. Thanks in advance.

Regards, Herman :D

Now that I read your page it says that basically a 2001 computer BIOS should not have such stupid limitations, but this particular BIOS (Sony BIOS 1002LE for Sony PCV-RX460) can't see the disk as bigger than 8 GB no matter what you do and Sony does not have any updates for it. Actually on their web site the latest BIOS is listed as 1001, which is strange.

I should also mention that this computer came originally with Windows Millennium. Then about 6 months ago the HDD gave out and a new 200 GB HDD was installed and WinXP was installed from scratch. This computer belongs to a friend of mine. He purchased a retail copy of XP and when he installed it, it could not make a partition bigger than 128 GB. This was either because this XP installation CD was with SP1, or becase he formatted his disk in such a way that it has 'OnTrack Disk Manager' on it. This was either from copying his previous broken HDD content or from some "prepare your HDD" utility that came with the Seagate disk he purchased. I am not really sure, but at any rate the disk did have the dreaded 'OnTrack Disk Manager' and it was a pane to figure this out.

Now the reason I had to deal with my friends computer again was that his networking stopped working. It would behave in a very weird way. It would obtain an IP address from DHCP, but then the icon next to the clock would continue to spin and ping would not work. Pretty weird stuff. I tried to install a new network adapter with a new driver to no avail. At the end of the day we had to reinstall XP, cause nothing I did there helped.

This time I installed XP myself and I did it from a media that has SP2 on the CD. Since we were going to reinstall Windows I simply saved all the data and repartitioned from scratch. Of course, the first thing I did was to remove the stupid OnTrack manager crap

When I used this CD to install XP it managed to use the whole 200 GB without a problem and interestingly enough Windows was booting from it just fine, even though in this case obviously the partition end cylinder would be > 1024. My guess is that the Windows boot stuff is always at the beginning of the disk and the BIOS has no problem to address that, whereas the content of the /boot folder on an ext3 partition could actually reside on an inode that is beyond cylinder 1024.

So to summarize I believe that the fix for GRUB error 18 is simply to have a boot partition that fits entirely within the address space the BIOS is capable of handling.

---

### Post by Herman on 2007-06-29
>  kept a copy of the boot folder as it was and I can see that I did not modify menu.lst.
I think however this is not relevant, because groot is supposed to point to the boot partition, which it did. As I mentioned, I am not 100% sure, but I think I was not able to boot the first time I rebooted after the repartitioning, but then I fixed it using the [Super GRUB disk]("http://sgd.howto-linux.de/"). Also tried several other "Super GRUB" options like trying to boot directly from the 2nd partition, etc.
I still think this has something to do with the initrd.img, because it's initrd.img which decides how to mount things. Check this thread where Senesence  had the exact same error you have described and has apparently solved the problem, [/bin/sh: can't access tty; job control turned off]("http://ubuntuforums.org/showthread.php?t=478715&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit"). Does that sound like it could have been it? :D
Regards, Herman

---

### Post by ihristov on 2007-06-29
> **Herman said:**
> Check this thread where Senesence  had the exact same error you have described and solved the problem, [/bin/sh: can't access tty; job control turned off]("http://ubuntuforums.org/showthread.php?t=478715&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit"). Does that sound like it could have been it? :D
Regards, Herman

This is exactly the same problem. Not sure why this thread did not turn up when I searched.

So basically what this says in the [post #17]("http://http://ubuntuforums.org/showpost.php?p=2929285&postcount=17") is that it seems sometimes the kernel update manages to write a bad \n or something to the menu.list and this is why it stops working.

In my experience this is not the problem, because I definitely modified the grub boot line in edit mode as well as tried several different options with the "Super GRUB" disk. I think I did not edit the menu.list.

I can try to put back the "bad" menu.list and see if the problem will return.

---

### Post by Herman on 2007-06-29
>  I can try to put back the "bad" menu.list and see if the problem will return.:D If you want to it might be interesting. I found other threads with different opinions of what this error message means and some other apparent solutions as well. 
These two are among the best I picked out, [SOLUTION: missing /sbin/init causes boot to exit to busybox/initramfs prompt]("http://ubuntuforums.org/showthread.php?t=466603&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit") and [/bin/sh: can't access tty]("http://ubuntuforums.org/showthread.php?t=398487&highlight=Target+filesystem+doesn%27t+have+%2Fsbin%2Finit")

I wonder which of these is the correct solution or if they all work in different circumstances. This error doesn't seem to be well understood. More testing might help. Only if you want to though. :D

Thanks you for your feedback about the error 18, I modifed my GRUB error 18 info on the Super GRUB Disk Page here, [     Grub error 18]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#18"). to read 
>  The error message (above)  from the [GNU/GRUB manual]("http://www.gnu.org/software/grub/manual/grub.html") dates to the old days when new computers were just beginning to use hard disks that exceeded the 8.0 GB limit.  If you have an old computer that was made back in the late 1990's or earlier, this error message could be right. [COLOR=Red]Some computers made as late as 2001 report this error. There are still quite a few older computers running today that this applies to.
[/COLOR]
A famous Linux method for circumventing this problem in the old days when they had the 8.0 GB limit was to create a separate /boot partition[COLOR=Red] containing GRUB and the Linux kernel entirely within[/COLOR] the 8.0 GB limit. From there the Linux kernel could manage a Linux file system which was outside the limit. This way Linux users could still have Windows installed within the 8.0 GB limit and because Linux's kernel could run the root filesystem outside the limit, they could use much larger hard disks.  Thanks again for your input, I think that improved it. :D

If you can shed any more light on the [Target filesystem doesn't have /sbin/init]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Target_filesystem_doesnt_have_") error it would be great!
I was only able to reproduce the [busybox or tty error]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#busybox") when I tried booting  with a deliberately wrong UUID number for 'root='

Regards, Herman  :D

---

