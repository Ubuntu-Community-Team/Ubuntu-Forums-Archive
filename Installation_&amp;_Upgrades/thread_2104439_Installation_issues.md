---
title: "Installation issues"
date: 2013-01-13
forum: Installation &amp; Upgrades
---

### Post by sourcenz on 2013-01-13
Hi, im really not all that experianced with ubuntu.

Im having issues installing on a acer aspire one netbook 1gb ram, 250gb hdd with intel atom processor

Using windows i created a new partition for the ubuntu installation. Using the windows installer, i then installed ubuntu to that partition, which ended up dual booting windows 7 and ubuntu which is exactly what i was after

However when attempting to boot ubuntu i get the following error.

Keys: continue to wait or press S to skip mounting or M for manual recovery

I have tried multiple installations to no avail

Any help much appreciated.

Thanks

---

### Post by dino99 on 2013-01-13
Sorry i've no clue about wubi things

for a real installation:

[http://ubuntuforums.org/showpost.php?p=12448406&postcount=4](http://ubuntuforums.org/showpost.php?p=12448406&postcount=4)

---

### Post by darkod on 2013-01-13
This is wubi, not ubuntu dual booting with windows. It's only virtual ubuntu inside windows.

I can't help much since I am not using wubi.

If you want a proper dual boot, you need to delete that partition you created from windows, if you want to use the whole space for ubuntu. Windows can only create ntfs partitions and linux doesn't install on ntfs. The space needs to be unallocated, so that ubuntu can create linux partitions.

---

### Post by sourcenz on 2013-01-13
thanks for the replies

so could i "shrink a volume" in windows and leave the space unallocated.

I want to do away with installing ubuntu on the same partition as 7 incase things goo wrong i can easily format the ubuntu volume leaving my win7 installation untouched. (your thoughts?)

Then i will boot using the ubuntu ISO and choose "another option" and install ubuntu on the unallocated space (creating its own file system in fat32 or whatever it uses?)

Thanks guys!

---

### Post by Abhinav Kumar on 2013-01-14
Hi sourcenz,
> **sourcenz said:**
> 
so could i "shrink a volume" in windows and leave the space unallocated.

In windows partition manager, make it a separate drive by right clicking on the unallocated space and then assign some drive alphabet to the new drive.
Make sure you **don't** end up making **Dynamic Disk**.

Now double click on your wubi installer and follow
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Just a simple thing to note: The first screen shot in the above link installs ubuntu in C drive of windows. You need to change it to the drive alphabet which you had assigned for the unallocated space.

> I want to do away with installing ubuntu on the same partition as 7 incase things goo wrong i can easily format the ubuntu volume leaving my win7 installation untouched. (your thoughts?)
Yes this is possible since wubi installs ubuntu inside windows and so you can easily format the drives on which ubuntu is installed or even very easily uninstall ubuntu. 

> 
Then i will boot using the ubuntu ISO and choose "another option" and install ubuntu on the unallocated space (creating its own file system in fat32 or whatever it uses?)
You first need to make a live usb/cd and then you can have the option to try/install ubuntu.

Regards,
Abhinav

---

### Post by sourcenz on 2013-01-14
Thanks for the reply.

i have done all of the following in wubi installer. I have shrunk my windows volume and created a new volume (in fat32) named ubuntu.

run wubi and installed to that volume. But i am always being hit with these errors. I cannot even use the "Try ubuntu" option when booting from USB. Please note my netbook has no CD/DVD rom drive. So either USB or wubi install.

However same issues, one thing i noticed is installation take a long time 20 - 25 minutes, when complete and i find its not working, in windows 7 its take about 10 seconds to completely format the ubuntu volume which is meant to have ubuntu on it. Im sure this is TOO quick. Indicates a issues writing in same way too the drive to me.

I have a ASUS Aspire One netbook, ive seen a few issues running ubuntu on them. I am receiving different errors all the time during boot, usually gets stuck at "starting up cpu interupts balancing daemon" and other errors in the same manner!

any ideas? i know im not giving you guys much to go on but as i said im new to ubuntu and am really installing to get familiar and use for my networking purposes and troubleshooting etc.

Thanks again!

---

### Post by darkod on 2013-01-14
Unfortunately you got some bad advice. DO NOT create any partitions in windows, DO NOT assign any letters (windows can assign letters only to windows partitions as far as i know, and you don't want windows partitions).

Your question about shrinking ntfs was spot on. Yes, you can do that and that's what you need to do. Open Disk Management and right-clicking a partition will offer Resize option in the menu that opens.

Plan your disk carefully, because it depends for example whether you will shrink it from the start or the end, the unallocated space will show up on that side.

So, you want Disk Management only to shrink the windows partition, not for anything else. No creating drives (they are actually partitions, Microsoft stupidly calls them drives), assigning letters, nothing. Reboot few times after the shrink so that windows can detect it and do any disk checks if it want to.

Only after that boot with the ubuntu cd and start the install. You can use manual partitioning for better control of partition sizes, or the auto method "along side windows" which will automatically use your unallocated space.

FYI, the filesystem for the main root partition is usually ext4, and for swap it's simply swap area.

---

### Post by sourcenz on 2013-01-14
Thanks, the real problem im having is understanding the partitioning menu in ubuntu.

I have moved on to attempted to install xunbutu, but again am stuck at the confusing (for me) partitioning menu. Ive been using the wubi installer but thought i would try a manual install

Keep getting the error "no root file systems defined"

I have the unallocated space and double click

Fat 32 file system to mount to /boot

A little guesswork going on here

Cheers

Update: with ununtu and xununtu i have been unable to "try ubuntu" sucessfully.

Im beginning to wounder if its a video issue. I always get issues in what seems to be acpid

---

### Post by darkod on 2013-01-14
That's because you are not specifying root partition (mount point /).

You don't need separate /boot partition, and again it doesn't need to be fat32. If you do make separate boot, make it ext4.

Here is a simple example:
1. Create a partition from the unallocated space of 2Gb for example, select the Use As: swap area, there is no mount point set for swap, clocki the OK.
2. Create a partition from the rest of the unallocated space, all of it. Use As: ext4, mount point /.

Device for bootloader installation: /dev/sda if you have only one hdd.

That's it.

A good practice is to also create separate /home but only in cases you dedicate sufficient space to ubuntu. The total needs to be like 25GB minimum. In that case you can make the / partition 15GB for example, and create another 10GB ext4 partition with mount point /home. This can help future clean installs.

---

### Post by sourcenz on 2013-01-14
I have 30gb assigned to ununtu completely.

Is that enough?

Cheers

---

### Post by sourcenz on 2013-01-15
Ok i just installed with the advice you gave above. All seemed fine. All installed fine however no boot boot image is available. I am unable to select to boot into ubuntu, it boots straight into windows 7.

Any ideas??

Cheers

Ps. After installing, and booting into windows, i cannot see a second partition in windows (my computer).
Is this norman being in a ext4 filesystem. Can windows not see ext4 file systems?

Thanks

---

### Post by sourcenz on 2013-01-15
ok now im really starting to get irritated with this crap! ive spent 3 nights trying to install ubuntu and xubunt with both failing.

I get constant hangs with something called acpid, always a different error, also whenever attempting to run ubuntu using the option "try ubuntu", i get stuck again with this acpid crap.

I installed xubunu manually, create a swap partition at 2gb and create a partition at / at around 29gb. All seemed to install well how no boot record was created.

I attempted to create the boot image using EasyBCD, which create the boot image, but when attempting to boot into ubuntu, it would just show a blinking cursor and go NO furthur.

HAS ANYONE got any other ideas? Maybe the fact that i cant even run ubuntu off my flash drive is a sign, i dont know???? maybe a graphics issue.... when launching into this acpid thing aswell, it shows a bit of a fuzzy screen?

Getting really irritated

Would love some help!

cheers guys!

---

### Post by darkod on 2013-01-15
Did you put the bootloader to /dev/sda?

The acpi problem is separate, I think you need to boot with the acpi=off parameter. here you have some advice about entering parameters both in live mode (when trying the Try ubuntu), and in a hdd installation. ignore the part about nomodeset, you don't seem to need that parameter. Follow the instructions but the parameter to try is acpi=off:
ubuntuforums.org/showpost.php?p=10069997&postcount=1

As for windows, it can't read and open linux partitions but it should at least see them in Disk Management (not in Computer). DO NOT try to manipulate any linux partitions from Disk Management, you can just open it to see if there are 29GB and 2GB partitions. They might not be seen as logical even when they are, on my computer it's the same, but it should at least show unidentified 29GB and 2GB partitions.

If windows boots straight and you have one single disk, it seems the grub2 bootloader didn't install correctly. That's easy to sort out but lets leave it for later.

The first task is making live mode work, finding which parameter and how you need it to boot. You always need to have a way to boot to live mode for tests or reparations. Once you manage that, we can look at the grub2 issue.

If you do manage to boot into live mode you can also use boot-repair to make the bootinfo which will show many details. It will give you a link to post. Instructions how to do it from live mode are here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by sourcenz on 2013-01-15
> **darkod said:**
> Did you put the bootloader to /dev/sda?

The acpi problem is separate, I think you need to boot with the acpi=off parameter. here you have some advice about entering parameters both in live mode (when trying the Try ubuntu), and in a hdd installation. ignore the part about nomodeset, you don't seem to need that parameter. Follow the instructions but the parameter to try is acpi=off:
ubuntuforums.org/showpost.php?p=10069997&postcount=1

As for windows, it can't read and open linux partitions but it should at least see them in Disk Management (not in Computer). DO NOT try to manipulate any linux partitions from Disk Management, you can just open it to see if there are 29GB and 2GB partitions. They might not be seen as logical even when they are, on my computer it's the same, but it should at least show unidentified 29GB and 2GB partitions.

If windows boots straight and you have one single disk, it seems the grub2 bootloader didn't install correctly. That's easy to sort out but lets leave it for later.

The first task is making live mode work, finding which parameter and how you need it to boot. You always need to have a way to boot to live mode for tests or reparations. Once you manage that, we can look at the grub2 issue.

If you do manage to boot into live mode you can also use boot-repair to make the bootinfo which will show many details. It will give you a link to post. Instructions how to do it from live mode are here:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

Thanks for the reply.

I noticed extremely laggy graphics and updated the graphics driver. Its not much smoother now. This might ease my mind a bit about the graphics issues.

I will try the acpi=off option and see if that works. 

I just tries installing on a different pc using the "install alongside windows 7" option, and it appears to have damaged the volumes. I an unable to use the windows 7 partition manager to shrink or extend volumes now it says "the volume you selected to shrink may be corrupted". I am however able to still boot into windows 7

Thanks for the replies

---

### Post by sourcenz on 2013-01-16
**** this **** im over it

---

