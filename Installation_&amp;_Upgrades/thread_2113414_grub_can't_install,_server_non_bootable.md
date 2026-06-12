---
title: "grub can't install, server non bootable"
date: 2013-02-07
forum: Installation &amp; Upgrades
---

### Post by meeshkah on 2013-02-07
Hi all,

First post, first (real stuck-situation-like) problem. I'm not exactly sure what's happening.

I first installed my ubuntu server (11.10 amd64) using lvm but not fully mastering the concept of it. I think that's partly what made the mess of partitions on my two disks (seems to me). I installed everything using grub2 from the start to boot my Ubuntu, which I updated later to Ubuntu Server 12.04, no problem.

Here is the situation:

- As of today, I can't boot at all, stuck with no evolution at what seems to be just before the grub options (Edit: precision from Pavel A.);

- I can boot using the server install liveCD with option Rescue a broken system;

- I setup network access, but don't seem to have a /run folders (don't know if it's related but seemed abnormal in some forums);

- The devices map I built is as follows:

.VGa contains sda1 [Linux partition], sda2, sda3 [/] and sda5(the latter seems the same as sda3, same descriptors)
.VGb contains sdc1, sdc2 [/boot] and sdc3 [/home]
!(I'm about to merge the two VGs into one, but running lvchange -an on my lv hangs also...)

- Last thing I did to the boot environment was to (cleanly) remove older kernels from the boot partition (236MB large, was 99% full);

- I ran grub-install (after having mounted boot) but got various errors:

.can't install on /dev/sdabecause core.imgwon't fit (first partion starts on 32)
.output of grub-install on /dev/sdc exhibits error physical volume pv0 not found
.I even tried to grub-install directly to /dev/sda5, apparently with no error, but with no success at boot either

- tail /var/log/syslog  yields no output (blank), no new syslog is created that I can see

> I looked here [serverfault]: Grub2 reports physical volume pv0 not found when probing/installing
> I looked here [Ubuntu forums]: [SOLVED] Install kernel with liveCD & fix grub2
> I looked here [Ubuntu help] : Fixing a Broken System
> I looked here [ubuntu forums]: [SOLVED] 10.10 Maverick - Grub won't recognize my Windows partition

None of what I did changed anything to the stuck-boot-situation (I can't define it any better: it just hangs, for minutes and minutes and minutes).
I hope I've not left out any important detail.

I used the Boot Repair CD (Ubuntu Secure Remix version) and generated the following report on the state of my boot:

[http://paste.ubuntu.com/1620777](http://paste.ubuntu.com/1620777)


I have no idea what to do anymore, especially if installing grub doesn't work. I've not lost any data, but as it was a production(-ish) server (i.e. entirely personal), I now strongly feel the need for mirrors (I already set backups but... on the server :p).


Anyway, if any of you geniuses had any idea or lead, that would be a great help.

Thank you !

M

---

### Post by darkod on 2013-02-07
Wow you really did made a mess. :)

First thing I see, which might not be critical but you shouldn't have done it, is that it seems you used the disks sdb and sdd for LVM as a whole disk, even though most instructions say to use partitions, not the disk. Like create one single partition on the whole disk and use that as physical device for LVM, not the whole disk device.

Second, I don't know which partition tool you used, but it left too little space in front of the first partition. Always leave 1MiB space in front of the first partition, or in sectors that is 2048 sectors of 512B each. With parted you can control the start and end of a partition when creating it.

Even in this situation you should be able to install grub2 on /dev/sdc but only there. And you have to set bios to boot from this disk.

You can use ubuntu live cd (desktop version) to repair this, it's better to use 12.04 if that's what you have on the server right now. But to repair the bootloader from live mode you need to add the lvm2 package and activate the LVM with:
```
sudo apt-get install lvm2
sudo vgchange -ay
```

After that all VGs and LVs should be activated.

You should be able to install grub2 on /dev/sdc with:
```
sudo mount /dev/binomiale/root /mnt
sudo grub-install --root-directory=/mnt /dev/sdc
```

That should fix it temporarily if the commands above activated the LVM correctly. Don't forget that /dev/sdc needs to be first disk to boot from in bios.

In any case, you should consider arranging the partitioning better but that might require a new install, so it might be lot of work installing again clean and configuring everything again.

EDIT PS: I forgot to mention, if /dev/sdc2 is a /boot partition that you had configured and you are using it, you need to mount it too. In the second block of commands above, before running the grub-install command, run also:
```
sudo mount /dev/sdc2 /mnt/boot
```

It is needed for grub2 to install correctly. If you are not using sdc2 as /boot any more, forget about this command.

---

### Post by meeshkah on 2013-02-08
Gee thanks! I'm relieved not to be alone on that one...
Welcome in my mess, is that what I should say?

So first:

- the disks partitioning: I know, when I came to understand enough, that ugly scheme had my eyes wtering, but I know there's not much I can do about it. Though I didn't know about the free-first-1M (thanks!), I think sda1 is just for that and serves no other purpose, or maybe to host some rescue tool or I don't know, can't be mounted or anything so I just leave it alone and try to forget about it. I just want to add that this is all a result of automatic partitioning by the help of the lvm manager, none of this I did myself (as I didn't know what to do at the time).

I actually used the liveCD to reorganise my two new disks like you suggested.
I removed them from the lvm,
made a first partition from 1M to 4G on each (first 1M free)
```
(parted)mkpart primary ext4 1M 4G
```
 in case the lone disk needs to be bootable,
used up the rest of the space to create a data partition that I could add to the volume group 
```
mkpart primary ext4 4G -1s
```
then made ext4 partitions in it
```
mkfs.ext4 /dev/sdb2
mkfs.ext4 /dev/sdd2
```
then integrated those in the main volume group
```
pvcreate /dev/sdb2
pvcreate /dev/sdd2
vgextend binomiale /dev/sdb2
vgextend binomiale /dev/sdd2

```
Last I created a new logical volume for later use
```
lvcreate -C y -L 1500M -n dat binomiale
```
Only issue is I can't seem to mount those, using the path /dev/mapper/binomiale/dat or /dev/binomiale/dat, it keeps asking me for a filesystem type, but I can feed it pretty much anything, I won't get closer to mounting it.
I'm writing all that for the record, mainly. If you happen to have an idea about that too, I'll say don't hesitate :p

- I think I already overinstalled the grub to sdc but to no avail, with the boot partition properly mounted and all, anyway I did it once more, following your specific instructions. I'm still stuck at the same point, no change here: blinking cusror about 4 lines down, just before grub display time, I'd say. And my BIOS seems to detect only one bootable drive as when I wander over the BIOS options, the boot order I can specify only includes one disk, just not sure which one of sda or sdc.
Maybe it's sda that's detected by the BIOS as bootable, but not sdc ?

---

### Post by darkod on 2013-02-08
After creating the LV you still need to create a filesystem to use it. Imagine it as standard partition.

So, you didn't need to do mkfs.ext4 on the physical partitions, I don't know if that can create issues later.

You only need to create the partitions as LVM Members (in parted set the lvm flag), use pvcreate on them, then extend the VG on them, and that's it.

So, for using the new LV try first:
sudo mkfs.ext4 /dev/binomiale/dat

You will still have to mount it before using it of course.

I don't know why reinstalling grub2 didn't work. If you post the content of your /etc/fstab we can have a look.

---

### Post by meeshkah on 2013-02-08
Ok so:

- OK, great, I finally could create my partitions!) Although I'm also wondering what could be the side-effects of havnig done the same operation in the reverse, I mean I tried to create a fs via the device block descriptor /dev/sdb2, your working solution was to add the partition to the vg before creating a fs through the pv device block descriptor. If I see it correctly, I see there IS a difference, but I don't see WHAT is the difference... Know what I mean? Anyway thanks that worked. Now ultimate operation I'd like to perform is to move the home lv (in c vg) to the binomiale vg (vgmerge needs c/home to be inactive). Only thing is I can't seem to inactivate it, meaning lvchange -an generates no error but lvscan shows it is still active. 

- fstab is like that:

```
<file system>                <mount point> <type> <options>                  <dump> <pass>
proc                         /proc         proc   nodev,noexec,nosuid        0      0
/dev/mapper/binomiale-root   /             ext4   errors=remount-ro          0      1
# /boot was on /dev/sda2 during installation
UUID={very long uuid...}     /boot         ext2   defaults                   0      2
/dev/mapper/c-home           /home         ext4   defaults,usrquota,grpquota 0      2
/dev/mapper/binomiale-swap_1 none          swap   sw                         0      2
```

I checked the UUID (with blkid), it correctly points to the /dev/sdc2 /boot partition.

---

### Post by darkod on 2013-02-08
I don't think you can move /home while logged in because it uses some parts of your user home folder. I would do that from live mode.

So now you know that you are using sdc2 as /boot and need to point that out in any grub-install command when run from live mode (from inside the installation you don't need to). If you didn't do this earlier maybe that's why the newly installed grub2 on /dev/sdc didn't work.

I haven't worked much with LVM yet, so I'm not sure if you want to literary move the home LV to another VG, or to merge both VGs, or you can simply create new LV in binomiale, copy the content of the old home LV and change the fstab. You would need to do that from live mode I guess.

So, which of that would you like to do? Basically you have three options.

---

### Post by meeshkah on 2013-02-08
Right I won't be able to do anything to c-home sine even the liveCD seems to have loaded confi files from it. I'll see about it later, but I opted for solution #3. Much simpler.

So, grub has the high hand there.
I don't exactly see what you mean by 
> you are using sdc2 as /boot and need to point that out in any grub-install command when run from live mode
any specific command comes to mind? I though that was the point of the --root-directory directive, that somehow used the drive UUID for the reference to the boot drive ?
I have no good idea as to how to proceed / what to do next.

---

### Post by meeshkah on 2013-02-08
Actually, BEFORE I figured out the location of /boot, I made a full boot directory (linux images, grub install) under /boot, so that if I don't mount sdc2 under /boot, the /boot directory IS full and should start correctly...

---

### Post by darkod on 2013-02-08
> **meeshkah said:**
> Actually, BEFORE I figured out the location of /boot, I made a full boot directory (linux images, grub install) under /boot, so that if I don't mount sdc2 under /boot, the /boot directory IS full and should start correctly...

How did you make this new boot folder? Just copied the files in there?

The grub.cfg will be looking for sdc2 by UUID so simply creating a boot folder won't do. Also, fstab still has the /boot line and it will try to use it.

Yes, the --root-directory is used to point out the root location but you have to mount /boot before that.

If you created boot folder in /, first rename it to something like boot.custom. Otherwise it will clash with sdc2 which will try to be /boot.

Then, the exact commands to try install grub2 on sdc from live mode would be:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/binomiale/root /mnt
sudo mv /mnt/boot /mnt/boot.custom #(rename the folder)
sudo mount /dev/sdc2 /mnt/boot
sudo grub-install --root-directory=/mnt /dev/sdc
```

Make sdc first disk to boot from and it should boot up.

---

### Post by meeshkah on 2013-02-08
About the boot folder under /boot I juste filled it.

fstab has the line about the /boot folder but isn't it commented out ?
I looked for a mention about the location of the /boot folder in grub.cfg but did not see any occurence.

I was along your line of thought (and already emptied out the /boot folder) so this is what I typed:
```
sudo vgchange -ay
sudo mount /dev/binomiale/root /mnt/root
sudo mount /dev/sdc2 /mnt/root/boot
sudo grub-install --root-directory=/mnt/root /dev/sdc
```
It reported no error and successfully installed. Then it printed ou a device map, after which it said to correct it if inccorect and relaunch grub-install. This is the device map:

```
(fd0)    /dev/fd0
(hd0)    /dev/sda
(hd1)    /dev/sdb
(hd2)    /dev/sdc
(hd3)    /dev/sdd
```

I shutdown and restarted the server but still no boot, still the same situation as before. So I'm guessing something is wrong:
- maybe the BIOS is only seeing sda as bootable, so it won't even let me boot on sdc?
- maybe I should launch the boot-repair tool and use the grub removal option on sda?

---

### Post by darkod on 2013-02-08
Confirm in bios you are booting from sdc. Don't assume, look and check it out. :)

If it says you can set sdc as first option to boot from, then it must let you boot from it.

Note that usually there are two separate settings:
-One to select type of device order, like cd-rom, hdd, usb hdd, etc.
- Another to set the order of all the hdds you have. This is the setting you need to find and set sdc as first. It will not say sdc in there, you have to "guess it" by manufacturer and model.

otherwise, if you have hdd first as device it might try booting the first of the hdds, like sda. You have to make sure the disk order is sdc first.

If you want, you can try removing bootloaders from other disks so it has no choice but to use sdc. But that is little risky, if you get the command wrong you can delete the partition table. I would rather avoid it.

Double check the bios options and settings first.

---

### Post by meeshkah on 2013-02-09
Yeah thanks, I'll try that next time I'm able to work on it. I'll edit this post, in 2 days approx. Thx

---

### Post by meeshkah on 2013-02-11
Hi (can't edit last post :( ),

You are so right, I totally forgot about the second option of ordering the boot order of the drives themselves.

I changed the boot order to boot sdc first. Worked so far, but it got me to a grub prompt, even though I installed grub to sdc (you had me install*).

I surmise it does not have the correct boot partition to boot from, even though it was given at grub-install... As I'm really no expert at grub prompt, I'll ask you what to do?

---

### Post by darkod on 2013-02-11
Did you rename the boot folder in your root LV?

You earlier said you made a boot folder in / yourself. If you are using sdc2 as /boot then you can't have boot folder in /. They will clash.

---

### Post by meeshkah on 2013-02-11
I rebooted from the Ubuntu Secure Remix CD to remove that boot folder. (I thought that there needed to be a folder for the mount point just like in a mount operation.)

I'm still at the grub prompt.

---

### Post by darkod on 2013-02-11
If you don't use separate /boot partition yes, there needs to be a folder boot inside /.

But since you are using sdc2 as /boot, no.

This doesn't look like only a grub2 issue. When you say you are at a grub prompt, you mean the rescue> prompt?

Is there any error message by grub2 that can point you towards why it doesn't boot?

---

### Post by meeshkah on 2013-02-11
Nope, It just displays a message about the possibilities of the grub prompt (minimum bash-like completion, yatta yatta..) and I'm at a grub> prompt :)

---

### Post by darkod on 2013-02-11
And you are sure you are booting from the sdc disk? If you have more disks the same size, you might be booting from the wrong one.

You can try running the command to install grub2 to /dev/sdc again but it should already be installed there correctly.

Either you are not booting from the correct disk, or there is something else bothering it, some change that was made, etc.

How come you earlier had grub2 installed and now after an upgrade it says it can't install. Did you change disks, LVMs, anything?

---

### Post by meeshkah on 2013-02-11
I'm pretty sure I'm not booting from another disk, and I'm sure I made no change that could alter the grub install. All I ever did was to move the lv around. Now, I've only got one vg, containing all my lv, including home and root (I changed the fstab accordingly).

I think what messed it all up is that I removed old kernels in the first place, and it somehow jeopardized the grub config (although I could not see how).

I do believe on the other hand that sda1 which contains a partition that I cannot mount contained the original core.img from which the grub launched (if I understood correctly). I can't do anything with that partition and it kind of bugs me a litte.

On the other side, when I try to apply the method here ([https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot):](https://help.ubuntu.com/community/Grub2/Installing#via_ChRoot):)
.first, I have to create a boot folder as a mount point for the /boot partition (which clashes with what you explained to me),
.second after having mounted the /boot partition and been chrooted in the /mnt dir, when I run a grub-install --recheck /dev/sdc, grub-probe complains about "cannot find device for /boot/grub (is /dev mounted?)" even though there is definitely a /boot/grub folder (same complaint if I run recheck on /dev/sda)

PS: Is there a way to 1) check on which pv a lv spans? 2) ensure a lv will remain on only one pv? 3) be sure I will not lose my data if say half my lv 'home' is lost due to disk failure?

---

### Post by meeshkah on 2013-02-11
Edit: I was mistaken and forgot a step in my previous post (forgot to mount the virtual critical devices, i.e. /dev /proc etc...). Then when I run grub-install --recheck /dev/sdc it computes a little and end with a "Installation finished. No error reported". Must I assume that /dev/sdc is correctly configured? That the install was repaired in some way?

---

### Post by meeshkah on 2013-02-11
Duh! I'm not sure I understand everything but I now have a grub menu!
It suggests so:
```
Ubuntu, with Linux 3.2.0-35-generic
Ubuntu, with Linux 3.2.0-35-generic (safe mode)
Memory text (memtest86+)
Memory test (memtest86+, serial console 115200)
```

This corresponds to what showed in that infamous /boot (sdc2) folder.
Hurray?
Well, if I choose the first option, it goes blank screen then says:
```
error: file not found.
error: you need to load the kernel first.
```
and if I choose the second option, it goes blank screen then says:
```
Loading Linux 3.2.0-35-generic
error: file not found.
Loading initial memory disk (<== not sure of the translation!)
error: you need to load the kernel first.
```

This is undoubtedly progress, thanks.

---

### Post by darkod on 2013-02-11
You don't create any boot folders in live mode, if you are mounting root as /mnt. You simply mount the /boot partition at /mnt/boot.
Also, making any folders in live mode is not clashing with what I told you because those folders are temporary and exist only in the live session.

I said not to create boot folder on your actual root partition.

First, stop trying so many things at once. You can easily mess it up.

I didn't understand that you moved LVs, that could affect everything since changing only the UUID in fstab is not enough. The UUID is also inside grub.cfg.

Since at this point we can't understand and track all the mess, lets do a full grub2 purge and reinstall.

But it is also important whether correct kernels are in sdc2. So first boot in live mode and show me what you have in sdc2:
```
sudo mount /dev/sdc2 /mnt
ls /mnt
ls /mnt/grub
```

Don't run anything else, just that and post the result. I will prepare the commands for full grub2 reinstall.

---

### Post by meeshkah on 2013-02-11
Haha I'm driving you nuts. You're right sorry, I should not have increased the mess, I just did not think it would. That's because I thought the UUID was independent of the LVM fonctioning, and because the grub.cfg file used devices naming using the mapper (i.e. /dev/mapper/binomiale-root and such) so the moving around of the LV should not affect that.
Anyway, I'll do what you wrote. I just want to point out, in regards to my previous post, that it seems grub is correctly installed but, linked to what you said, it can't find the files in the /boot partition i.e. /dev/sdc2 so maybe a bad pointer?
...

```
$ ls /mnt
abi-3.2.0-35-generic               lost+found
config-3.2.0-35-generic            memtest86+.bin
grub                               memtest86+_multiboot.bin
initrd.img-3.2.0-35-generic        System.lmap-3.2.0-35-generic
initrd.img-3.2-35-030235-virtual   vmlinuz-3.2.0-35-generic
$
$ ls --hide=*.mod /mnt/grub
boot.img       efiemu64.o          jfs_stage1_5     pxeboot.img
cdboot.img     fat_stage1_5        kernel.img       resiserfs_stage1_5
command.lst    fs.lst              lnxboot.img      stage1
core.img       g2hdr.img           load.cfg         stage2
crypto.img     gfxblacklist.txt    locale           terminal.lst
default        grldr.img           minix_stage1_5   unicode.pf2
diskboot.img   grub.cfg            moddep.lst       video.lst
e2fs_stage1_5  grubenv             partmap.lst      xfs_stage1_5
efiemu32.o     installed-version   parttool.lst
```
Yes the grub folder contains many .mod files that I did not (manually) transcript here.

Sorry got to go for at least 2 hours.
Thanks

---

### Post by darkod on 2013-02-11
OK, you have the -35 kernel which should be fine.

When you are back, lets try completely reinstall grub2 from live mode, including the activation of LVM again:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/binomiale/root /mnt
sudo mount /dev/sda2 /mnt/boot
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

Now you should be chrooted inside the installation so everything you run is like run by root from inside (that's why you don't need sudo in this block of commands):
```
update-initramfs -u
apt-get remove --purge grub-pc grub-common
apt-get install grub-pc
update-grub
grub-install /dev/sdc
```

Exit the chroot and unmount everything:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt/boot
sudo umount /mnt
```

Reboot and hopefully you will have a fully working grub2 on /dev/sdc.

---

### Post by meeshkah on 2013-02-11
Ok, some error/warning messages:

update-initramfs -u
 it said it could not find file initrd.img-3.2-35-030235-virtual, but I kept on as I was about to perform a clean install.

apt-get remove --purge grub-pc grub-common
 when it asked something about config-something-whatever, I went too quickly and chose No, but no config file remains in /boot...

apt-get install grub-pc
 I'm at the config screen, where it asks where to install GRUB, but the drives order is all different:
```
/dev/sda (2000398 Mo; ST32000641AS)
/dev/sdb (2000398 Mo; ST32000641AS)
/dev/sdc (2000398 Mo; ???)
/dev/sdd (2000398 Mo; ???)
/dev/dm-0 (107374 Mo; binomiale-root)
```
I suspect sda and sdb are the same order as before I added the two more disks (which was why I restarted and discovered the problem), ans that the 2 unrecognized disks are the 2 new ones. But I'm not sure whether I should install on sda on sdb (sdb, I guess), and whether it would jeopardize the whole thing one more time if I try both

---

### Post by darkod on 2013-02-11
How can the order be different, isn't sdc the same sdc from the beginning?

Just a note, in a text menu you select with Space bar and a * will appear to mark the selection.

I think you should select sdc. It's easy to change it later.

I saw the file -virtual in sdc2 but I have no idea what it does. I haven't seen such file so far. Usually the initrd image syntax is initrd.img-3.2.0-35-generic and you have a file called like that in sdc2. Not sure if it has something to do with the LVM or not.

---

### Post by meeshkah on 2013-02-11
I have no idea why the order would be different. As you seem to think it sould not be, I'll select sdc. But it reads if I'm not sure I sould install to all drives. Should I do that?

Edit: I carried on with sdc. Only error/warning: ```
Found unknown Linux distribution on /dev/sda1
```/ I wonder if I could delete that partition someday.

Edit2: OK I missed a step (grrr!). I'll start over tomorrow.

---

### Post by darkod on 2013-02-11
Yeah, it doesn't hurt installing grub2 on all drives. The thing is that other drives that are GPT and without the bios_grub partition, will give error if grub2 tries to install on them.

To avoid those errors, it's best to select directly and only the gpt disk that has the bios_grub partition. That was the idea.

---

### Post by meeshkah on 2013-02-12
Ok I'll start over that clean install, now. But I don't get the concept of the "bios_grub partition". Is that a full-fledged partition on which the grub is installed or what? Wouldn't that be that sda1 partition then?

Edit: And I still don't get how you mount /dev/sdc2 to /mnt/boot without creating a mount point (i.e. mkdir /mnt/boot) first. I mean, if I don't create that folder, the mount tool just tells me there's no mount point and will NOT mount the /boot partition. So I understand that there should not be a boot folder on the binomiale-root partition but how do you suggest I cross this step? Create a mount point, mount there, grub-install and alll, then umount and delete the mount point?

---

### Post by darkod on 2013-02-12
The concept of the bios_grub partition on gpt disks is because gpt disks have smaller MBR than msdos disks, so grub2 doesn't fit there. It will look for a partition with bios_grub flag to put part of its files. That partition SHOULD NOT have any filesystem, grub2 uses it in raw format.

It doesn't necessarily need to be first on the disk, but yes, if it's first it will be sda1. If starting from scratch I would create it as first for example.

Also, because grub2 is not big, 1MiB is enough for this partition. You can make it 100GiB if you want, but that's waste of space since it has raw format you will not be able to use it for anything else. :)

As for the mount point, I actually never needed to use those restore commands myself but we have used them many times on the forum and I don't remember a single time that anyone said he gets an error message it doesn't exist. If you use something else than /mnt/boot you might get that message, but for /mnt/boot it should work.
Of course, you mount the root partition at /mnt first.

If your system really complains, you can try creating that folder before you start mounting anything. At the end you don't need to delete it since you are working from live mode anyway and it will be gone after you reboot.

---

### Post by meeshkah on 2013-02-12
Ok actually I think sda1 was the bios_grub partition at first and somehow lost the bios_grub flag, which is now displayed on sdc1 when using parted. Then as it is raw, sda1 can't be mounted or used for anything (it's 2G large).
If I understood correctly: on drives sdb and sdd I first created 4G partitions sdb1 and sdd1 beginning 1M from the start, thinking that if the disks were alone and I wanted to use it completely isolated I could install a small Ubuntu on that first partition and bios_grub would still install at the begining of the disk since I left it enough space, but as I follow you and since that space is not a partition, it will not install there but on the 4G partitions instead, resulting in a massive loss of space?
Additionally I have some unanswered questions for you about LVM: Is there a way to 1) check on which pv a lv spans? 2) ensure a lv will remain on only one pv? 3) be sure I will not lose my data if say half my lv 'home' is lost due to disk failure? (I'll take a link, too : )

I  confirm that if I follow your steps and don't have a boot folder in the root, it will complain. You mean I create the /mnt/boot folder BEFORE mounting the root partition to /mnt?

Edit: Creating the /mnt/boot folder before mounting /dev/binomiale/root doesn't work either. It says mount point /mnt/boot does not exist. And if I create the folder ON the partition, it will be written to the disk so it will not be temporary (that's why I suggest to remove it afterwards).

Edit2: The menu of grub (when installing it) has slightly changed and now features the sdc2 partition (I assumed in your recipe that you meant sdc2 instead of sda2):
```
/dev/sda (2000398 Mo; ST32000641AS)
/dev/sdb (2000398 Mo; ST32000641AS)
/dev/sdc (2000398 Mo; ???)
- /dev/sdc2 (256 Mo; /boot)
/dev/sdd (2000398 Mo; ???)
/dev/dm-0 (107374 Mo; binomiale-root)
```
This is new! But is suppose this changes nothing as grub should be installed on sdc (on the disk, not the partition).

Edit3: Upon reboot, this does not get me to a grub menu but to a grub prompt, just like last time.

What should I do?

---

### Post by darkod on 2013-02-12
I'm not sure how to check on which PV an LV spans. As for making sure it stays on only one, I'm not sure you can do that and don't see much point.

The point of LVM is spanning over multiple PVs. If you limit one LV to one PV, you might as well create standard partition and use it like that. For example, if you want your /home LV to be only on PV made from /dev/sda1, simply format sda1 as ext4 and use it as /home without involving LVM. Limiting makes no point and I'm not sure it can support it.

I don't think LVM has any redundancy either, I don't think it's designed to be redundant. If you loose a disk (PV) I would expect that will mess up all VGs/LVs using that PV.
For redundancy you will have to look at something like mdadm SW raid for example.

You mentioned you have a 4GB partitions sdb1 and sdd1 but that doesn't seem true. Look at this part of the bootinfo you posted in your first post:
```
=================== parted -l:

Model: ATA ST32000641AS (scsi)
Disk /dev/sda: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system  Flags
1      16.4kB  2097MB  2097MB  primary   ext3
2      2097MB  2359MB  262MB   primary
3      2359MB  2000GB  1998GB  extended
5      2359MB  2000GB  1998GB  logical                lvm



                                                                          
Error: /dev/sdb: unrecognised disk label

Model: ATA ST32000641AS (scsi)
Disk /dev/sdc: 2000GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name  Flags
1      17.4kB  1018kB  1000kB                     bios_grub
2      1018kB  257MB   256MB   ext2
3      257MB   2000GB  2000GB                     lvm



                                                                          
Error: /dev/sdd: unrecognised disk label

Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/c-home: 537GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End    Size   File system  Flags
1      0.00B  537GB  537GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/binomiale-root: 1992GB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system  Flags
1      0.00B  1992GB  1992GB  ext4


Model: Linux device-mapper (linear) (dm)
Disk /dev/mapper/binomiale-swap_1: 8485MB
Sector size (logical/physical): 512B/512B
Partition Table: loop

Number  Start  End     Size    File system     Flags
1      0.00B  8485MB  8485MB  linux-swap(v1)
```

That is your partitions layout according to the link in post #1. You can clearly see that the whole disks sdb and sdd were joined to the LVM as PVs, not partitions on them (compare that with sda and sdc which have partitions). Also in the blkid output you can clearly see the whole disks sdb and sdd are members of the LVM, not partitions like on sda and sdc:
```
=================== blkid:
/dev/loop0: TYPE="squashfs"
/dev/sda1: UUID="309baba6-60f5-48ff-87bd-b770567e9983" SEC_TYPE="ext2" TYPE="ext3"
/dev/sda5: UUID="fl6xtO-h3jA-34KH-1KLE-5mQb-2Tk4-NvrWLu" TYPE="LVM2_member"
/dev/sdb: UUID="Hqotkc-2GoY-Ef4t-6vH0-EvwL-Exrz-HpbDTo" TYPE="LVM2_member"
/dev/sdc2: UUID="5671c47f-2914-4387-a9e2-0d47061a4435" TYPE="ext2"
/dev/sdc3: UUID="OZUVJf-7Wss-Ofw5-1zVg-52oJ-QZlV-IqJXsf" TYPE="LVM2_member"
/dev/mapper/binomiale-root: UUID="d5b1caa0-de90-4909-91e2-b21d3f1591af" TYPE="ext4"
/dev/sdd: UUID="58MB95-o7ow-ypZE-JL5W-7Wuw-dNUU-FsxoZq" TYPE="LVM2_member"
/dev/mapper/binomiale-swap_1: UUID="eaa45363-1f34-4196-b2a4-dc4dae6a7b90" TYPE="swap"
/dev/mapper/c-home: UUID="6bc67054-69d8-403f-9653-9d2c296db39d" TYPE="ext4"
```

If you don't have too much data on the system, I suggest you copy it to an external hdd and redo everything from scratch. I'm not sure how it got so messed up, whether switching the LVs around, or something like that. You have to be careful when doing things like that.

On top of that, you shouldn't have joined sdb and sdd as whole disks to the LVM.
And the first partition on both sda and sdc starts very early, I haven't seen partitions that start so early at the start of the disk.
That doesn't leave space for grub2 on the MBR and I think there lies your grub2 problem.

If you do decide to redo everything, DO NOT rush. Sit down first, plan everything, especially the partitioning which is very important, and then start. Don't leave yourself making decisions during the install, everything should be already planned and decided before you even start.

Depending how much storage space you need, I would suggest you use mdadm SW raid1. From 4 physical 2TB disks that will give you 4TB usable space. You can still use LVM on top of the SW raid so that the 4TB are joined in single storage space and plus you have more flexibility with the LVs.

---

### Post by meeshkah on 2013-02-12
I created said partitions on sdb and sdd after post#1, that's what I meant when I said I was moving partitions around. Ok I think there is some misunderstanding due to incomplete information, so I'm currently issuing a new bootinfo report for you to has as a sound basis.
I made the new partitions on sdb and sdd for the very same remark you had on having a full disk used on a lvm. But now that I know the vulnerability of using lvm without redundancy, i really don't see the advantage of it (I try but I don't have utter faith in my disks).

But are you suggesting I should restart from scratch? That would clear the problem away for sure, but that would be quite a hassle, I think.
I don't really know the point of mdadm and how it integrates with lvm. But as I have 4 disks, why do you suggest raid 1 instead of raid 5? The bootinfo detects a raid install and suggests installing mdadm ```
sudo apt-get install -y --force-yes mdadm --no-install-recommmends
```.
I don't understand how such a mess could have happened as all I did at first was to use the recommended settings of the ubuntu server install...

From scratch and without losing any data, that would mean shrinking all partitions, removing one drive from the lvm, copying all partitions/data to that drive, erasing all three drives and setitng them up for lvm and mdadm use in raid config, then adding the data back, chrooting in the root partition and configuring mdadm there. Isn't that somewhere right?

Here is the bootinfo report: [http://paste.ubuntu.com/1639084/](http://paste.ubuntu.com/1639084/)

Edit: I don't understand why it couldn't mount any of the binomiale logical volumes. FYI, binomiale-web is a dedicated partition for /var/www, binomiale-cloud is another for ownCloud at /home/owncloud (personal dropbox), binomiale-home is the one for /home, all mount points exist and mount without difficulty in live mode.

---

### Post by darkod on 2013-02-12
> **meeshkah said:**
> 
I don't understand how such a mess could have happened as all I did at first was to use the recommended settings of the ubuntu server install...


It's not what you did at first but what you did later I guess. :)

But that's how we all learn. So, to summarize, what you would like to do now is convert to a 4-disk raid5 installation without LVM and without reinstalling everything?

One thing I see in the latest bootinfo is that you don't even have a kernel now on sdc2. And I still don't understand that -virtual initrd.img file. But lets forget about this for a moment and answer the question above.

---

### Post by meeshkah on 2013-02-12
Yeah! But the thing is, I could not possibly have done anything about the partitions, about sda1 and all. All I did, yes, was to use a script to remove old kernels installed on my boot partition so that i bould make an upgrade of my system and my kernel. Anyways I think I'm not about to use recommended settings anymore. You're only better served by youself (and those more knowledgeable than you :p ).

Well I DO see the benefit of using lvm on top of a raid array, I think this is the only setup in which it might be truly interesting (that is, if you have a crush on your data *pun intended*). What would be wonderful is that I wouldn't have to reinstall all my tools and use the root partition I already setup, in a new config, probably one using raid 1 or 5, without loss of performance. If that's not possible, I think I'll simply come back to a very standard and very boring setup on which I control on which disk each partition and each data resides, using transparent mount points (which will also become a mess from an organizational point of view).

Edit: And please what about the partitioning of sdb and sdd: what will become of the 4G partitions 1M from the start? Are those for nothing?

---

### Post by darkod on 2013-02-12
I'm not 100% sure the boot folder can be inside / if we use raid5. The point is that raid5 splits data over disks and i think the boot files can't handle that. I suggest having a 500MiB partition on all disks that will be used to create a 4-partition raid1 for /boot. I know for sure /boot can't be on raid0, I'm not sure about raid5.

So even if three disks fail, you still have /boot untouched. Of course, not the rest of the data since raid5 can't survive three failures. :)

Another option is having the whole / partition outside the raid5 by having a 50GiB partition on all disks for example and configured in raid1. I think 50GiB is more than plenty for / since all your major data will be inside the raid5/LVM.

If I'm not mistaken, you are using only a small part of all the space in the LVM right now. So, the plan would be:
1. Shrink the filesystem and then the size of all LVs depending how much data they have inside.
2. Remove three disks from the LVM one by one. Hopefully everything can fit on a single 2TB disk since you really are not using much space.
3. Create a 4-partition raid5 mdadm array with one partition member missing (the fourth disk that will be added later). Create a 4-partition raid1 array for /boot or /, depending what you decided.
4. Set up LVM on the new raid5 device.
5. Copy all the data from the one disk LVM (old one) to the new LVM.
6. Try to make it boot.
7. Once it's working, add the 4th disk to the mdadm raid too.

What do you think?

PS. Don't worry about the 4GB partitions, if we do this the whole layout will be changed. You will delete everything, trying not to lose the data. :)

---

### Post by meeshkah on 2013-02-12
Yep I like that plan since I think the main objective would be for the server to start whatever happens and independently of the loss of data, which would be reconstructed afterwards. But even in that config would it not be smart to separate the /boot and / partitions, with say a 250M /boot partition and a 20G root partition both in raid1 over the four disks with grub installed on all four disks if I get your drift correctly? Then a 3rd partition on all disks configured in raid5 with lvm. I think that's what would fit most closely to what I have in mind.

Do you see any drawback to such a configuration? Do you think it might be a little overdoing things? (Please consider being honest and to your mind :) ) What would be the time of adding a new disk to the array (assuming scripts would takeover the job)? Would the complexity of rebuilding a disk be linear or exponential with the load of data? How many disks can I afford to lose, only one? Do I get to choose?

I have a few questions about your plan though:
- since it's not possible to control on which PV LV data is, how am I sure that removing PVs from the VG would not lose LVs or data?
- binomiale-cloud is empty so removing it should clear 1 disk, so should I not rather create one partition on it (once clear of the vg), rebuild the root directory tree without mount points (i.e. copy data under corresponding folders) so that everything fits on one fs? I could then move home and /var/www on the lvm once all is setup
- is it not possible to make / in raid5 on all disks? If /boot is separated and in raid1 config, the root partition outside the lvm in raid5 could work, would it not?

---

### Post by darkod on 2013-02-12
If you create a small 20G root there is no point having /boot separate. It will only complicate things.

The setup I have on mind on all disks would be:
ALL disks with GPT table
partition #1 1MiB bios_grub
partition #2 20GiB for raid1 root
partition #3 2GiB for swap
partition #4 the rest, for raid5 LVM

As for the LVM manipulation. There are LVM commands which move all data from a PV partition/disk and then you can remove it. That's what you would need to do to make sure it doesn't corrupt any data on that PV/disk.

Why do you think -cloud PV is on one physical disk and that removing it will free one disk?

Besides, freeing one disk doesn't help, you need three to start raid5. If you are doing this only with raid1, one disk is enough to create array with missing member.

Yeah, with raid5 you can afford to lose only one disk. If you want to be able to lose two disks you have to use raid6. It allows two failures at the same time. But of course it brings down the usable space.
With 4-disk raid5 you have 3 disks usable (one parity), and with raid6 you have 2 disks usable (two parity).

PS. Yeah, it's possible to make / inside the raid5 if you have /boot outside. The choice is yours. But it doesn't make much sense to me. I think it's much better to have / as separate raid1 device.

---

### Post by meeshkah on 2013-02-12
Yes you are right, it probably doesn't make much sense, I was not thinking this through. I validate your suggestion. I created -cloud LV 1.5T large with the contiguous option so I thought that the only way for it to be was to oppupy one disk alone so I though removing it would free some space i.e. one disk, that could then be used to hold the / tree with all folders and used the three other disks to setup the configuration, then add the data to the config then add the fourth disk to the raid. That may be overreaching as if I reduce the vg to only one disk the same will be achieved, so let's go with it.

That config would make a (8T-4*20G)/4*3 = 5.94T lvm for data, spanning / on raid 5 would bring 5G more to that. Not relevant.
What about mdadm integration? I mean does it work below lvm, with lvm or over lvm?

---

### Post by darkod on 2013-02-12
mdadm will work below LVM. First mdadm will create the /dev/md0 device for root and /dev/md1 for raid5, and then you use the /dev/md1 as PV for LVM.

OK, so if you want to start the first thing is shrinking the filesystems so that you can shrink the LVs later. This is the extract from your latest bootinfo:
```
=================== df -Th:

Filesystem                  Type       Size  Used Avail Use% Mounted on
/cow                        overlayfs  3.9G   41M  3.9G   2% /
udev                        devtmpfs   3.9G   12K  3.9G   1% /dev
tmpfs                       tmpfs      1.6G  880K  1.6G   1% /run
/dev/sr0                    iso9660    761M  761M     0 100% /cdrom
/dev/loop0                  squashfs   717M  717M     0 100% /rofs
tmpfs                       tmpfs      3.9G   16K  3.9G   1% /tmp
none                        tmpfs      5.0M  4.0K  5.0M   1% /run/lock
none                        tmpfs      3.9G   76K  3.9G   1% /run/shm
none                        tmpfs      100M   48K  100M   1% /run/user
/dev/sdc2                   ext2       229M   33M  185M  15% /mnt/boot-sav/sdc2
/dev/mapper/binomiale-root  ext4        99G  4.8G   89G   6% /mnt/boot-sav/mapper/binomiale-root
/dev/mapper/binomiale-web   ext4      1008G  656M  957G   1% /mnt/boot-sav/mapper/binomiale-web
/dev/mapper/binomiale-cloud ext4       1.5G   35M  1.4G   3% /mnt/boot-sav/mapper/binomiale-cloud
/dev/mapper/binomiale-home  ext4       493G  2.4G  465G   1% /mnt/boot-sav/mapper/binomiale-home
```

You can see that you don't use much space. When shrinking, be careful on the MiB vs MB difference, and leave some reserve to avoid potential issues. From live mode you will have to activate the LVM but don't mount any LVs, you shrink the filesystem unmounted.

Also, if you can, make a full backup before you start because this whole operation has some risks if things go wrong.

For example, shrink the filesystems like:
```
sudo apt-get install lvm2
sudo vgchange -ay
sudo resize2fs /dev/binomiale/root 8G
sudo resize2fs /dev/binomiale/web 2G
sudo resize2fs /dev/binomiale/home 4G
```

I left out the cloud LV since it's 1.5G anyway, no need to shrink it.

After those three operations finish it should shrink the filesystems of the LVs root to 8G, web to 2G and home to 4G. As you see I left quite reserve compared to the used space on those LVs right now.

After the filesystem is shrinked, it's time to shrink the LVs with:
```
sudo lvreduce -L10G /dev/binomiale/root
sudo lvreduce -L3G /dev/binomiale/web
sudo lvreduce -L6G /dev/binomiale/home
```

As you can see I left reserve again because different commands can interpret GB differently, some as GB other as GiB. Better not to take risks especially since you have plenty of space.

Let us know after the shrinking finishes.

---

### Post by darkod on 2013-02-12
I just realised something I didn't pay much attention to. Talking about all these changes, we didn't even discuss a faster method to do them.

Since you seem to be using only about 8GB in total on all LVs, in fact it would be much faster if you copy all files to a usb stick or usb hdd, and redo the mdadm and LVM using all disks at once. In that case you won't need to move data to one disk to use the other three first, you don't need to do any LVM resizing, etc.

8GB is really small and if you can manage to find where to store it externally, that would be actually best.

I´ll start searching how to copy the files keeping all permissions and ownership, since we will need that anyway, sooner or later. Either to copy them on a usb stick (the files need to keep their ownership and permissions), or from LVM to LVM later.

---

### Post by meeshkah on 2013-02-12
I did a full backup of all data (i.e. -root, -cloud, -web, -home) on an external hdd. Resizing went well except: 1) lost+found folder not found on -web, I don't know its function but I must have removed it at some point, so it just recreated it, 2) resize2fs required to run sudo e2fsck -f on every fs before resizing, 3) I ran an additionnal resize2fs with no argument on every fs after having reduced the lv so that the fs occupies all the available space in the lv, but that's for aesthetics

Sorry I did not see your post, but as a matter of fact there are two way to copy files preserving ownership and timestamps and all:
sudo cp -rp : teh -p or --preserve keeps all metadata
sudo rsync -a : in archive mode, rsync keep all metadata, using special algorithms to mirror the two directory trees. Beware that rsync is a little sensitive to trailing slashes...

I saw that no one knew whether the two tools counted GB and MB the same way, so everyone recommends the same things :) I'd have done it that way, anyway.

So you suggest that I do everything from scratch? I didi not suggest that in the first place just to have the experience of adding a disk to a raid5 array :p

Edit: Just on a side note, I had to resize -web to 3G since 2G was below the minimum size for resize2fs (wow didn't know there was one!)

Edit2: Ready for the pvmove operations!

---

### Post by darkod on 2013-02-12
OK, since you did a backup, even if this whole operation fails, you can start over (I mean the partitioning not OS installation from scratch). :)

So, lets start in order, from disk sda. The pvmove should be like:
```
sudo pvmove /dev/sda5
```

In order not to type everything every time, just to remind you that if doing this in a new live session you have to install lvm2 first and activate the LVM. And not to mount anything.

EDIT PS: The pvmove can take long time, I guess depending on the size of LVM present on that device that needs to be moved. Lets see how it goes with sda5 first.

---

### Post by meeshkah on 2013-02-12
```
sudo pvmove /dev/sda5
 No data to move for binomiale
```

Next I suppose? :) I think everything is on /dev/sdc

Edit: Maybe next stage is to remove the pv? ```
sudo pvremove /dev/sda5
```?

---

### Post by darkod on 2013-02-12
I'm not sure if that command does the same, but you need to remove it from the VG first. Something like:
```
sudo vgreduce binomiale /dev/sda5
```

---

### Post by meeshkah on 2013-02-12
Yep, done, pvremove is actually to mark the disk as no longer usable by the lvm (wipes the label, no sure how it works in details)

So should I do the same with sdb and sdd? (pvmove / vgreduce)

Should I use pvremove? Or is it not necessary?

---

### Post by darkod on 2013-02-12
After vgreduce it says you can also physically remove the disk, so even without pvremove i think you are good. Don't worry whether it deletes the lvm flag on the partition or not, we will delete the partition tables anyway.

If you are sure everything is now on sdc, continue with the lvm partition of sdb and sdd, yes.

It seems you can see whether a PV has a LV on it with this:
```
sudo pvdisplay /dev/sdXY
```

If you want to, before continuing, run that command on each lvm partition on the rest of the disks (sdb-sdd). It might point you where the LVs are.

So that you continue removing the PVs that have no LVs, to save time not waiting for pvmove to finish.

---

### Post by meeshkah on 2013-02-12
Only PV standing is /dev/sdc3 in binomiale, all other pv removed, meaning sda sdb and sdd ready

---

### Post by darkod on 2013-02-12
OK.

Because disks from different manufacturers can have slightly different capacity, list all disks with parted with unit MiB and see which disk has the smallest size in MiB (it will be listed for each disk together with other data at the top):
sudo parted /dev/sda unit MiB print all

The command mentions sda but the print all will print all of them.

Let me know which is the smallest Mib size.

---

### Post by meeshkah on 2013-02-12
All drives are from the same manufacturer and are exactly the same size: 1907729MiB
Only difference is the physical and logical sectors:
- the 2 oldest  (bought together) drives have ```
Sector size (logical/physical): 512B/512B
```
- the 2 most recent (bought together, some 6 months later) drives have ```
Sector size (logical/physical): 512B/4096B
```
Actually, let's do the quicker install using all four drives from the start twomorrow, I don't have the time now, I need to go.

---

### Post by darkod on 2013-02-12
The logical sector is still equal at 512B, no problem.

OK, great.

To avoid future complications it's wise to leave about 50MiB unused at the end. If in the future when you buy a replacement disk it is little smaller, you can still add it to the array.

If you use 100% now and tomorrow you buy a disk only 2-3MiB smaller, it might not allow you to add it.

I think 50MiB is not much space to lose so that you cover this option.

So, on the sda, sdb and sdd disks, with parted write a new gpt table and create the needed partitions:
```
sudo parted /dev/sda
unit MiB
mklabel gpt
mkpart GRUB 1 2
set 1 bios_grub on
mkpart ROOT 2 20482
set 2 raid on
mkpart SWAP 20482 22530
mkpart RAID5 22530 1907678
set 4 raid on
quit
```

That will create new gpt table, and the partitions:
1MiB bios_grub
20GiB root
2GiB swap
the rest for raid5

Do that on all three disks. Don't forget to leave sdc alone. :)

---

### Post by darkod on 2013-02-12
I forgot to ask, did you decide to go with raid5 or raid6?

---

### Post by meeshkah on 2013-02-13
I think I will go with RAID5, I'd say covering one disk failure would be enough. I think covering two would be meaningful if I ever had 5 or 6 disks or more. Your opinion?

Operations done. However I have a little question: won't the beginning and ending partitions boundaries overlap?
What's more, I did not quit parted every time but merely used select /dev/sdX to switch disks, saved me a couple strokes :) That's aesthetics, for sure. Also, I checked all configurations with print afterwards.

Anyway, time to setup the raid1 (root) and 5 (data)?

Edit: BTW I left all boundaries calculations to you, thanks :)

Edit2: I was there [http://ubuntuforums.org/showthread.php?t=2115483](http://ubuntuforums.org/showthread.php?t=2115483) and I wondered if I have to do anything, the mb is pretty recent and I'd not be surprised if it had the controller for raid

---

### Post by meeshkah on 2013-02-13
I also wonder if I could switch the drives management to AHCI instead of SCSI, I'd like to be able to use eSATA and hotplug of disks. It is a system feature to enable before setting it in the BIOS, if I remember correctly.

I'm in the process of finding what in the Intel doc what I need to do to activate the Intel Matrix Storage functionalities.

Here: [http://download.intel.com/support/chipsets/rste/sb/intelr_rste_linux.pdf](http://download.intel.com/support/chipsets/rste/sb/intelr_rste_linux.pdf)

---

### Post by darkod on 2013-02-13
Yeah, it's better to use the sata mode in AHCI, but not the built-in bios raid. The mdadm SW raid works much better and gives you more options. including having root in raid1 and data in raid5. With fakeraid you can have one or the other, not both, because it works only on disk level. mdadm works on partition level.

OK, so to manipula mdadm from live mode you have to add the package first. After that we will create the arrays with one missing member (sdc):
```
sudo apt-get install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=4 /dev/sda2 /dev/sdb2 missing /dev/sdd2
sudo mdadm --create /dev/md1 --level=5 --raid-devices=4 /dev/sda4 /dev/sdb4 missing /dev/sdd4
```

That should create the arrays. You can check status with:
```
cat /proc/mdstat
```

Once the md devices are configured (the above command can show whether they are still being prepared or not), you can continue. Note that with the commands we only created them, but right now the system doesn't know how to assemble them on boot (the system is not booting by itself at all).

So, from live mode after every reboot you should be able to issue a command for the md devices to be assembled:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That will scan disks automatically and assemble the arrays. So, reboot once and try the command above to see if md0 and md1 will exist.

Let me know when you get so far.

---

### Post by darkod on 2013-02-13
> **meeshkah said:**
> 
Operations done. However I have a little question: won't the beginning and ending partitions boundaries overlap?


If you use those command to create partitions, they don't overlap because it continues from where the last partition ended.

If you use sectors as units, in that case the ending sector of one partition can't be the same as the starting of the next one.

---

### Post by meeshkah on 2013-02-13
But if I install it in live mode, it won't be installed on the partition?

I'm installing it now.

> **darkod said:**
> Yeah, it's better to use the sata mode in AHCI, but not the built-in bios raid. The mdadm SW raid works much better and gives you more options. including having root in raid1 and data in raid5. With fakeraid you can have one or the other, not both, because it works only on disk level. mdadm works on partition level.

OK, from what you tell me, the Intel raid options are like HW raid ? I was under the impression they worked in conjunction with the mdadm tool.

---

### Post by meeshkah on 2013-02-13
> **darkod said:**
> OK, so to manipula mdadm from live mode you have to add the package first. After that we will create the arrays with one missing member (sdc):
```
sudo apt-get install mdadm
sudo mdadm --create /dev/md0 --level=1 --raid-devices=4 /dev/sda2 /dev/sdb2 missing /dev/sdd2
```
I get
```
mdadm: Note: this array has metadata at the start and
    may not be suitable as a boot device.  If you plan to
    store '/boot' on this device please ensure that
    your boot-loder understands md/v1.x metadate, or use
    --metaadta=0.90
Continue creating array?
```

I continued because we do not plan to use it as /boot, but how come there is metadata on this device?

> **darkod said:**
> So, from live mode after every reboot you should be able to issue a command for the md devices to be assembled:
```
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

That will scan disks automatically and assemble the arrays. So, reboot once and try the command above to see if md0 and md1 will exist.

Is the next step to install the mdadm tool when chrooted in root (after having copied it over)? Are the disks now working raid?

Edit: All done, raid arrays correctly recognized after reboot

---

### Post by darkod on 2013-02-13
Yeah, I was going to try install mdadm after chrooted and after root is copied.

After you create md0 and md1 they should be working, only not assembled on boot. mdadm is strictly SW raid, the OS controls it and assembles the arrays from the partitions. That is why it has nothing to do with any of the motherboard raid settings. But mobo raid is also SW, hence it's called fakeraid. It has no dedicated HW card, CPU or memory. In this aspect, mdadm is much better option, and more flexible.

So, do you have both md0 and md1 created now? Can you post the results of:
cat /proc/mdstat

---

### Post by darkod on 2013-02-13
OK, if they are still there after reboot, that's a good sign. :) Don't forget that temporarily you will have to assemble them manually after every reboot because this is still only live mode.

So, now we format them, and the swap partitions too.
```
sudo mkfs.ext4 /dev/md0
sudo mkswap /dev/sda3
sudo mkswap /dev/sdb3
sudo mkswap /dev/sdd3
```

After that is done we can start thinking about copying. We will create temporary mounts in live mode to do the copying.
```
sudo mkdir /mnt/oldroot
sudo mkdir /mnt/newroot
sudo apt-get install lvm2
sudo vgchange -ay
sudo mount /dev/binomiale/root /mnt/oldroot
sudo mount /dev/md0 /mnt/newroot
cd /mnt/oldroot
sudo cp -ax * /mnt/newroot/
```

Wait for that to finish and let me know when it does.

EDIT PS: Initially I had a commnd to format /dev/md1 too, but later realised you want to use LVM on md1 right? In that case DO NOT format md1, only md0.

---

### Post by meeshkah on 2013-02-13
```
$ sudo mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 3 drives (out of 4).
mdadm: /dev/md/1 has been started with 3 drives (out of 4).
$
$ cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4] 
md1 : active raid5 sda4[0] sdd4[3] sdb4[1]
      5790779904 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UU_U]
      
md0 : active raid1 sda2[0] sdd2[3] sdb2[1]
      20955008 blocks super 1.2 [4/3] [UU_U]
     
```
So the raid disks are working on raid?
How/when do I set AHCI mode? Last, I suspect?
If I had created the raid with only 3 members how would I have added a 4th disk afterwards? Would it even have been possible? How is it even working knowing that one disk is missing? Is marking a disk as missing part of the process to replaced a fail drive?

---

### Post by darkod on 2013-02-13
> **meeshkah said:**
> ```
$ sudo mdadm --assemble --scan
mdadm: /dev/md/0 has been started with 3 drives (out of 4).
mdadm: /dev/md/1 has been started with 3 drives (out of 4).
$
$ cat /proc/mdstat
Personalities : [raid1] [raid6] [raid5] [raid4] 
md1 : active raid5 sda4[0] sdd4[3] sdb4[1]
      5790779904 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/3] [UU_U]
      
md0 : active raid1 sda2[0] sdd2[3] sdb2[1]
      20955008 blocks super 1.2 [4/3] [UU_U]
     
```
So the raid disks are working on raid?
How/when do I set AHCI mode? Last, I suspect?
If I had created the raid with only 3 members how would I have added a 4th disk afterwards? Would it even have been possible? How is it even working knowing that one disk is missing? Is marking a disk as missing part of the process to replaced a fail drive?

If you still haven't set AHCI, reboot and set it now.
It's working without one disk because raid5 array can work without one. By using the 'missing' word in the --create command we told it one is missing and to keep a place for it.
Adding a disk later in mdadm is very easy, that's the beauty of it.

---

### Post by meeshkah on 2013-02-13
Wait I have a question related to one of you posts on a forum about disks longevity: are there fs that will reduce the lifetime af disks? Will there be a difference between ext3 and ext4 fs? You wrote about increasing the wear/the write operations on disks using journalized fs. What are your thoughts?

---

### Post by darkod on 2013-02-13
> **meeshkah said:**
> Wait I have a question related to one of you posts on a forum about disks longevity: are there fs that will reduce the lifetime af disks? Will there be a difference between ext3 and ext4 fs? You wrote about increasing the wear/the write operations on disks using journalized fs. What are your thoughts?

I haven't posted about jounaling in any thread. :) You have me confused.

Usually those things matter with SSDs, not mechanical HDDs. I think using the latest ext4 is a good option. I have it on my home server for example.

Remind me, do you want to install LVM on top of the raid5 array, or you decided against it?

---

### Post by meeshkah on 2013-02-13
Oh yes I see many benefits to have from using lvm on that raid5 array, which really suppresses the need to bother with physical locations and makes sense with the integration of disks in raid arrays. Well if that was unclear, I'm sure we think along the same lines here.

You are right, you did not directly speak about that journaling thing. I was referring to that thread: [Question about server HDDs] [http://ubuntuforums.org/showthread.php?t=2059484](http://ubuntuforums.org/showthread.php?t=2059484)

(BTW congrats for your application as a member, I think I see why you'd want that and you'd be right.)

Going with ext4 FS and LVm on raid5. I just set AHCI prior to making the partitions. I'm launching into that now, with all the copying and all.

Edit: Copying done. I preferred the use of ```
rsync -a [-v|--stat] /mnt/oldroot/ /mnt/newroot
``` as it has more powerful tool for managing interrupted copies. Habits die hard, I suppose :p All done. Next step? Chrooting and installing mdadm? Installing lvm and creating -home and -web and all?

---

### Post by darkod on 2013-02-13
If the copying is done and the mounts are still untouched (if you didn't unmount anything), first check if there is a boot folder in /mnt/newroot.

You remember your old root didn't have boot folder because you were using separate /boot partition. Not boot will be inside root so we need to create the /mnt/newroot/boot folder if it doesn't exist.

Also don't forget you need to adjust fstab:
```
gksu gedit /mnt/newroot/etc/fstab
```

Edit the / line to have /dev/md0 as /. Comment out the swap line at the moment, it's easy to add swap later in fstab. Save and close the file.

After that you are ready for the chroot. We will leave the LVM for later, lets handle root first.

If md0 is still mounted at /mnt/newroot to continue with chroot:
```
sudo mount --bind /proc /mnt/newroot/proc
sudo mount --bind /dev /mnt/newroot/dev
sudo mount --bind /sys /mnt/newroot/sys
sudo chroot /mnt/newroot
```

Inside the chroot lets try installing mdadm and add our arrays:
```
apt-get install mdadm
mdadm --examine --scan >> /etc/mdadm/mdadm.conf
```

Lets try installing the latest kernel, recreate grub2 config and install on sda, sdb and sdd:
```
apt-get dist-upgrade
grub-mkconfig
grub-install /dev/sda /dev/sdb /dev/sdd
update-initramfs -u
update-grub
```

I hope that should cover it. Exit the chroot and unmount md0:
```
exit
sudo umount /mnt/newroot/sys
sudo umount /mnt/newroot/dev
sudo umount /mnt/newroot/proc
sudo umount /mnt/newroot
sudo umount /mnt/oldroot #(if it's still mounted)
```

Reboot and set /dev/sda as first option to boot. With any luck, it should boot from md0.

---

### Post by darkod on 2013-02-13
From the previous post, I'm not 100% sure apt-get dist-upgrade installs the latest kernel when you have no kernels in /boot. We might need to use something like:
apt-get install linux-image

but I'm not sure if that's the correct syntax.

---

### Post by meeshkah on 2013-02-13
Some small issues, still, only warning level but still:
- when installing anything, the install process complains about open_pty() that can't be opened and asking if /dev/pts is mounted. Isn't that in /dev that I mount at the beginning? Not much importance anyhow, I think.
- grub didn't like being asked to install on multiple devices, so I had to install on each drive separately. Just FYI.
- the weirdest thing happened just after I rebooted after having setup the md devices: sdb and sdc "switched", meaning the partition and data disk holding the lvm and all previous install now appears as sdb not sdc anymore. I wonder how, I wonder why... But I think we can just ignore it.
- I ran apt-get update before dist-upgrade and some packages appeared and were updated THEN.
- there is still the matter of that linux-image-yattayatta-virtual that still show up as an error-like message when grub-installing. Should we do something about it?

One thing I don't understand: if mdadm manages sda2 sdc2 (now) and sdd2 as in raid 1, why did I have to grub-install to all disks? Wouldn't installing to only one have been sufficient?

About fstab, I made a backup (.bak) copy and removed in the actual file the line specifying the place of the /boot partition at install time (remember?), eventhough it was commented out. That would be cleaner.

I'm currently rebooting.

Edit: About linux-image virtual and all that, I can infer from a simple lookup that vmlinuz is needed at boot time, and in /mnt/newroot there are two: vmlinuz symlink to boot/vmlinuz-3.2.35-030235-virtual, and vmlinuz.old symlink to vmlinuz-3.2.35-030235-generic. I know for a fact that there has only been "generic" files in my boot and I am positive these virtual-things were introduced by myself at first when I tried to solve the boot problem on my own (I downloaded kernel images from an ubuntu repository and used dpkg to install them). I'm not sure now if I could safely delete those then overinstall the grub and all (making sure there is no hole in the install). Maybe that incorrect file gives me trouble to boot?

---

### Post by meeshkah on 2013-02-13
OK STUCK SITUATION HERE! ](*,)

Damn I feel tired :p

Whatever the boot hdd I select as first to boot, I get to a grub prompt just like before. And I installed the new kernel using apt-get install linux-image (I already did that, I remember it to be the correct syntax).

I'll be there tomorrow.

Thanks for holding together and bearing with me!

---

### Post by darkod on 2013-02-13
This was always a possibility, that's why I mentioned clean install would be a good idea too, if you don't have too much configuration to do after that.

I would remove those -virtual files in /boot. But we never copied /boot, how can they be there first of all? I left it as empty folder on purpose.

If the real latest kernel was installed it should have been something like 3.2.0-37-generic.

To go back to your question about installing grub2 on all MBRs, the point of installing to all is to keep working if disk(s) fail. For example, if you have it only on one disk, what if that disk fails? The raid5 and raid1 will keep going because they can work with one failure, but there is no bootloader for the system to boot. That's why it's usually installed on all.

I didn't know you installed kernels manually. You might try using dpkg to remove them now and using purge option too, so that everything is gone. Only removing the files might not remove everything. I leave the decision to you.

From live mode I would also take a look at /boot/grub/grub.cfg in /dev/md0 and check what UUIDs it uses, and compare them to the UUIDs of /dev/md0. And make sure there is no error in /etc/fstab after you edited it after copying.

If the UUID is wrong in grub.cfg, we might try purging grub2 totally and reinstalling it. I was hoping to avoid that with grub-mkconfig.

Let me know how it goes.

Double check the kernels in /boot, is there something similar to a latest kernel 3.2.0-37 or not? If there is, from the grub prompt you can try booting with manual commands. That will show us whether the problem is in grub, or in the kernels missing. If you can boot with manual commands, then it's only grub and it should be easy to fix. Also check in grub.cfg the Ubuntu menuentry and which kernel is has there.

---

### Post by meeshkah on 2013-02-14
Ok we might have a problem here:

```

ubuntu@ubuntu:~$ cat /mnt/boot/grub/grub.cfg | grep uuid
set root='(mduuid/07f4125b138587342bde397ec50ab288)'
search --no-floppy --fs-uuid --set=root 4d81ca46-2217-4ea2-a648-e1685064117c
  set root='(mduuid/07f4125b138587342bde397ec50ab288)'
  search --no-floppy --fs-uuid --set=root 4d81ca46-2217-4ea2-a648-e1685064117c
ubuntu@ubuntu:~$
ubuntu@ubuntu:~$ sudo blkid
/dev/loop0: TYPE="squashfs" 
/dev/sda2: UUID="07f4125b-1385-8734-2bde-397ec50ab288" UUID_SUB="6a11d957-1a94-f5be-b36f-42c09832abc6" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/sda3: UUID="d13307cc-06b3-48c9-8fdf-ac185a7d754e" TYPE="swap" 
/dev/sda4: UUID="bdf9f194-a55c-a760-ce37-eaaf6f418f18" UUID_SUB="e00c9f3b-032a-b912-ee1d-9be7640f0f0e" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sdb2: UUID="5671c47f-2914-4387-a9e2-0d47061a4435" TYPE="ext2" 
/dev/sdb3: UUID="OZUVJf-7Wss-Ofw5-1zVg-52oJ-QZlV-IqJXsf" TYPE="LVM2_member" 
/dev/sdc2: UUID="07f4125b-1385-8734-2bde-397ec50ab288" UUID_SUB="2885076e-9f90-973d-bbec-9b8ae33b5a77" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/sdc3: UUID="22d6b6a9-041e-4d89-a77a-c242288f22e1" TYPE="swap" 
/dev/sdc4: UUID="bdf9f194-a55c-a760-ce37-eaaf6f418f18" UUID_SUB="b8b15973-d656-158e-65a0-daa32a4634a7" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/sr0: LABEL="Ubuntu Secure 12.10 64bit" TYPE="iso9660" 
/dev/sdd2: UUID="07f4125b-1385-8734-2bde-397ec50ab288" UUID_SUB="7193bc8f-be3f-5a79-3b64-82f5954b1c91" LABEL="ubuntu:0" TYPE="linux_raid_member" 
/dev/sdd3: UUID="ffafcc46-852e-4081-b4cb-6b5478b1b6c0" TYPE="swap" 
/dev/sdd4: UUID="bdf9f194-a55c-a760-ce37-eaaf6f418f18" UUID_SUB="cc713dcc-f016-e288-2c2f-4b32ec46f6c0" LABEL="ubuntu:1" TYPE="linux_raid_member" 
/dev/mapper/binomiale-root: UUID="d5b1caa0-de90-4909-91e2-b21d3f1591af" TYPE="ext4" 
/dev/mapper/binomiale-swap_1: UUID="eaa45363-1f34-4196-b2a4-dc4dae6a7b90" TYPE="swap" 
/dev/mapper/binomiale-web: UUID="99acfc6c-d07b-4719-8c85-eb7c78826bf9" TYPE="ext4" 
/dev/mapper/binomiale-cloud: UUID="807bcd16-fc7d-4495-8091-c3b40df73752" TYPE="ext4" 
/dev/mapper/binomiale-home: UUID="f62d5eab-a8c1-436e-80ed-adb9e7055b99" TYPE="ext4" 
/dev/md0: UUID="4d81ca46-2217-4ea2-a648-e1685064117c" TYPE="ext4"
```So three things:
- sda2, sdc2 and sdd2 seem to have the exact same UUID? (sdb and sdc were interverted, remember?)
- the wrong uuid is set for the root in grub.cfg. Changing it would solve something, right?
- md1 has no UUID?

The kernels I installed manually were in the first place and as I did not mount the separate /boot, it filled the boot folder in / making the confilct appear. I now understand that simply switching the boot folder did no remove the references to those virtual images hence these curious appearances. I think removing the vmlinuz references in root in addition to purging and reinstalling the grub would solve something, would it not?

Edit: ```
$ ll /mnt
total 112
drwxr-xr-x  25 root root  4096 févr. 13 16:37 ./
drwxr-xr-x   1 root root   300 févr. 14 09:39 ../
drwxr-xr-x   2 root root  4096 févr.  6 11:44 bin/
drwxr-xr-x   2 root root  4096 sept. 20 10:11 bkp/
drwxr-xr-x   3 root root  4096 févr. 13 16:49 boot/
drwxr-xr-x   4 root root  4096 mars   7  2012 dev/
drwxr-xr-x 111 root root  4096 févr. 13 16:49 etc/
drwxr-xr-x   2 root root  4096 mars   7  2012 home/
lrwxrwxrwx   1 root root    38 févr.  5 12:33 initrd.img -> /boot/initrd.img-3.2.35-030235-virtual
lrwxrwxrwx   1 root root    38 févr.  5 12:33 initrd.img.old -> /boot/initrd.img-3.2.35-030235-generic
drwxr-xr-x  19 root root  4096 févr.  6 11:44 lib/
drwxr-xr-x   2 root root  4096 oct.  24 10:37 lib64/
drwx------   2 root root 16384 mars   7  2012 lost+found/
drwxr-xr-x   4 root root  4096 mai    8  2012 media/
drwxr-xr-x   3 root root  4096 févr.  6 12:33 mnt/
drwxr-xr-x   2 root root  4096 mars   7  2012 opt/
drwxr-xr-x   2 root root  4096 oct.   9  2011 proc/
drwx------   3 root root  4096 sept.  9 21:59 root/
drwxr-xr-x   6 root root  4096 févr. 13 16:44 run/
drwxr-xr-x   2 root root  4096 févr. 13 16:44 sbin/
drwxr-xr-x   2 root root  4096 févr.  5 14:16 sdc1/
drwxr-xr-x   2 root root  4096 juin  21  2011 selinux/
drwxr-xr-x   2 root root  4096 juil. 12  2012 srv/
drwxr-xr-x   2 root root  4096 juil. 14  2011 sys/
drwxrwxrwt  15 root root  4096 févr. 13 16:49 tmp/
drwxr-xr-x  10 root root  4096 sept. 19 15:08 usr/
drwxr-xr-x  13 root root  4096 févr. 11 18:18 var/
-rw-------   1 root root  1084 févr.  6 11:46 .viminfo
lrwxrwxrwx   1 root root    34 févr.  5 12:33 vmlinuz -> boot/vmlinuz-3.2.35-030235-virtual
lrwxrwxrwx   1 root root    34 févr.  5 12:33 vmlinuz.old -> boot/vmlinuz-3.2.35-030235-generic
$
$ ll /mnt/boot
total 14840
drwxr-xr-x  3 root root     4096 févr. 13 16:49 ./
drwxr-xr-x 25 root root     4096 févr. 13 16:37 ../
drwxr-xr-x  3 root root    12288 févr. 13 16:49 grub/
-rw-r--r--  1 root root 15173060 févr. 13 16:49 initrd.img-3.2.35-030235-virtual
```

Edit2: Most recent bootinfo [http://paste.ubuntu.com/1649285/](http://paste.ubuntu.com/1649285/)

---

### Post by darkod on 2013-02-14
1. md1 not having UUID is normal, we didn't format it yet. The formatting sets the UUID. We didn't format it on purpose because it will serve as PV for LVM, in which case you format the LVs, not the PV. So, forget about it at this moment.

2. The sda2, sdc2 and sdd2 having same UUID is not an issue I think. That UUID was set by mdadm when joining them into array. As you can see, they all have another UUID_SUB which is different for all partitions. The same goes for partitions #4 on those disks.

3. As we can see in /boot there was no new kernel installed. Still only the initrd.img -virtual file exists, further more there is no corresponding vmlinuz -virtual file.

I think the issue is there is no kernel in reality. The command to install a kernel might not have been what we thought it is.

Reinstalling grub2 might not be needed since grub.cfg points correctly. It's little confusing because it shows two UUIDs but as we can see one UUID is of the sda2,sdc2 and sdd2 partition that form md0, and the other is of md0. So that seems OK.

I think it's the missing kernel that is doing all the damage here. Once that is sorted, it should be a functioning system.

But how to get rid of -virtual and install the standard one is something we will have to learn together. :)

---

### Post by meeshkah on 2013-02-14
You are right I did not read correctly and did not notice the second uuid for md0, so as I'm not sure I fully understand that grub language, if you think it OK that's it for me.

I removed the grub packages (grub grub-pc and grub-common) with all the config to be as clean as possible. The boot folder is empty of grub-related stuff, and only contains initrd.img-3.2.35-030235-virtual.

I don't know the in-depth change when installing a new linux image but perhaps removing the vmlinuz things can cleanup a little more the mess? 
```

# sudo dpkg -l | grep linux
ii  libselinux1                             2.1.0-4.1ubuntu1                 SELinux runtime shared libraries
ii  linux-firmware                          1.79.1                           Firmware for Linux kernel drivers
ri  linux-headers-3.2.0-30                  3.2.0-30.48                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35                  3.2.0-35.55                      Header files related to Linux kernel version 3.2.0
ii  linux-headers-3.2.0-35-generic          3.2.0-35.55                      Linux kernel headers for version 3.2.0 on 64 bit x86 SMP
ii  linux-headers-3.2.35-030235             3.2.35-030235.201212061235       Header files related to Linux kernel version 3.2.35
ii  linux-headers-3.2.35-030235-generic     3.2.35-030235.201212061235       Linux kernel headers for version 3.2.35 on 64 bit x86 SMP
ii  linux-headers-3.2.35-030235-virtual     3.2.35-030235.201212061235       Linux kernel headers for version 3.2.35 on 64 bit x86 Virtual Guests
ii  linux-image                             3.2.0.37.45                      Generic Linux kernel image.
rc  linux-image-3.2.0-30-generic            3.2.0-30.48                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-31-generic            3.2.0-31.50                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-32-generic            3.2.0-32.51                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-33-generic            3.2.0-33.52                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-35-generic            3.2.0-35.55                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.0-37-generic            3.2.0-37.58                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-image-3.2.35-030235-generic       3.2.35-030235.201212061235       Linux kernel image for version 3.2.35 on 64 bit x86 SMP
ii  linux-image-3.2.35-030235-virtual       3.2.35-030235.201212061235       Linux kernel image for version 3.2.35 on 64 bit x86 Virtual Guests
ii  linux-image-extra-3.2.35-030235-virtual 3.2.35-030235.201212061235       Linux kernel image for version 3.2.35 on 64 bit x86 Virtual Guests
ii  linux-image-generic                     3.2.0.37.45                      Generic Linux kernel image
ii  linux-libc-dev                          3.2.0-37.58                      Linux Kernel Headers for development
ii  pptp-linux                              1.7.2-6                          Point-to-Point Tunneling Protocol (PPTP) Client
ii  util-linux                              2.20.1-1ubuntu3                  Miscellaneous system utilities
# exit
exit
$
$ sudo dpkg -l | grep linux
ii  libselinux1:amd64                         2.1.9-5ubuntu1                            amd64        SELinux runtime shared libraries
ii  libv4l-0:amd64                            0.8.8-2ubuntu1                            amd64        Collection of video4linux support libraries
ii  libv4lconvert0:amd64                      0.8.8-2ubuntu1                            amd64        Video4linux frame format conversion library
ii  linux-firmware                            1.95                                      all          Firmware for Linux kernel drivers
ii  linux-generic                             3.5.0.23.29                               amd64        Complete Generic Linux kernel and headers
ii  linux-headers-3.5.0-17                    3.5.0-17.28                               all          Header files related to Linux kernel version 3.5.0
ii  linux-headers-3.5.0-17-generic            3.5.0-17.28                               amd64        Linux kernel headers for version 3.5.0 on 64 bit x86 SMP
ii  linux-headers-generic                     3.5.0.17.19                               amd64        Generic Linux kernel headers
ii  linux-image-3.5.0-17-generic              3.5.0-17.28                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-extra-3.5.0-17-generic        3.5.0-17.28                               amd64        Linux kernel image for version 3.5.0 on 64 bit x86 SMP
ii  linux-image-generic                       3.5.0.17.19                               amd64        Generic Linux kernel image
ii  linux-libc-dev:amd64                      3.5.0-23.35                               amd64        Linux Kernel Headers for development
ii  linux-signed-generic                      3.5.0.23.29                               amd64        Complete Signed Generic Linux kernel and headers
ii  linux-signed-image-3.5.0-17-generic       3.5.0-17.28+signed2                       amd64        Signed kernel image generic
ii  linux-signed-image-generic                3.5.0.17.19                               amd64        Signed Generic Linux kernel image
ii  linux-sound-base                          1.0.25+dfsg-0ubuntu3                      all          base package for ALSA and OSS sound systems
ii  pptp-linux                                1.7.2-7                                   amd64        Point-to-Point Tunneling Protocol (PPTP) Client
ii  syslinux                                  2:4.05+dfsg-6                             amd64        collection of boot loaders
ii  syslinux-common                           2:4.05+dfsg-6                             all          collection of boot loaders (common files)
ii  syslinux-legacy                           2:3.63+dfsg-2ubuntu5                      amd64        Bootloader for Linux/i386 using MS-DOS floppies
ii  util-linux                                2.20.1-5.1ubuntu2                         amd64        Miscellaneous system utilities
```I think we need to achieve the second one. What do you think?

---

### Post by darkod on 2013-02-14
In your latest bootinfo I also noticed in the md0/etc/mdadm/mdadm.conf part that the ARRAY definitions are doubled. I guess it already detected them when you installed mdadm in the chroot, and when we did the --examine --scan it doubled them. You can edit the mdadm.conf and remove the bottom ARRAY definitions so that they are not doubled.

Curiously that dpkg shown limux-image-3.2.0-37-generic as present but you have no vmlinuz-3.2.0-35-generic and initrd.img-3.2.0-37-generic files present in /boot.

I would use dpkg to purge all related to 3.2.35-030235 since that is the one you installed manually.

After that we have to see why the vmlinuz and initrd.img files were not created for 3.2.0-37-generic when dpkg says it's installed. if we don't figure it out, you can always purge the kernel and install it again. The point is it has to create the vmlinuz and initrd.img files in /boot.

PS. if you removed and purged grub2, it will need to be reinstalled, but after the kernel, so that it can detect the kernel right away. But for that to happen the correct kernel files have to exist and right now they don't.

---

### Post by meeshkah on 2013-02-14
Ok I tried to uninstall those virtual ackages, here what came out:
```
# man dpkg
# dpkg --purge linux-image-3.2.35-030235-virtual
dpkg : a problem with the dependencies prevents the removal of linux-image-3.2.35-030235-virtual :
 linux-image-extra-3.2.35-030235-virtual depends on linux-image-3.2.35-030235-virtual.
dpkg : processing error of linux-image-3.2.35-030235-virtual (--purge) :
 dependencies problem - removal ignored
There were some errors processing:
 linux-image-3.2.35-030235-virtual
# dpkg --purge linux-image-extra-3.2.35-030235-virtual
(Reading database... 119963 files and folders already installed.)
Removal of linux-image-extra-3.2.35-030235-virtual ...
FATAL: Could not open '/boot/System.map-3.2.35-030235-virtual': No such file or directory
update-initramfs: deferring update (hook will be called later)
Purge of configuration files of linux-image-extra-3.2.35-030235-virtual ...
FATAL: Could not open '/boot/System.map-3.2.35-030235-virtual': No such file or directory
update-initramfs: deferring update (hook will be called later)
# dpkg --purge linux-image-extra-3.2.35-030235-virtual
dpkg : avertissement : there's no installed package matching linux-image-extra-3.2.35-030235-virtual
```(Sorry if some alerts seem weird, I had to do some translation...)

Edit: Well as you suggest we can still purge the kernel, if that's simpler?
> **darkod said:**
> PS. if you removed and purged grub2, it will need  to be reinstalled, but after the kernel, so that it can detect the  kernel right away. But for that to happen the correct kernel files have  to exist and right now they don't.
That was the idea :)

---

### Post by darkod on 2013-02-14
Yeah, we can purge the repo kernel 3.2.0-37 but I don't know if that overwrites the virtual kernel or not. If it doesn't it will not matter. Since you went the manual route for the kernel, I'm really not sure what happens.

That's why I would stick to repo kernels and installing them with apt-get, not manually. What ever boot problems you have, in most cases it can be solved by using the regular kernel. Only in special cases you would need to do it manually.

Try purging and reinstalling linux-image-3.2.0-37-generic to see what happens.

---

### Post by meeshkah on 2013-02-14
Wow I don't get that one:
```
# dpkg --purge linux-image-3.2.0-37-generic
dpkg : a problem with the dependencies prevents the removal of de linux-image-3.2.0-37-generic :
 linux-image-generic depends on linux-image-3.2.0-37-generic.
dpkg : processing error of linux-image-3.2.0-37-generic (--purge) :
 dependencies problem - removal ignored
There were some errors processing:
 linux-image-3.2.0-37-generic

```Isn't that message biting into itself?

Edit: Going the manual route for installing a specific kernel was just a matter of downloading specific files. The install process was then done with the dpkg utility.

---

### Post by darkod on 2013-02-14
I would try apt-get instead of dpkg for the kernel from the repo. Try:
apt-get purge linux-image-3.2.0-37-generic

---

### Post by meeshkah on 2013-02-14
Ok removed -virtual and 3.2.0-35 kernels without error:
```
# sudo dpkg -l | grep linux
ii  libselinux1                      2.1.0-4.1ubuntu1                 SELinux runtime shared libraries
ii  linux-firmware                   1.79.1                           Firmware for Linux kernel drivers
ri  linux-headers-3.2.0-30           3.2.0-30.48                      Header files related to Linux kernel version 3.2.0
rc  linux-image-3.2.0-30-generic     3.2.0-30.48                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-31-generic     3.2.0-31.50                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-32-generic     3.2.0-32.51                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
rc  linux-image-3.2.0-33-generic     3.2.0-33.52                      Linux kernel image for version 3.2.0 on 64 bit x86 SMP
ii  linux-libc-dev                   3.2.0-37.58                      Linux Kernel Headers for development
ii  pptp-linux                       1.7.2-6                          Point-to-Point Tunneling Protocol (PPTP) Client
ii  util-linux                       2.20.1-1ubuntu3                  Miscellaneous system utilities

```I think this is a success.
However, should it not be able to boot from an older kernel image?

Edit: Ok I'm done remove all traces of -35 kernel, I was not sure at first that the headers could be removed. Actually apt-get treats headers and images separately, contrary to the dpkg utility

---

### Post by darkod on 2013-02-14
Not sure, try removing the headers packages with the exact syntax and see how it goes.

It's able to boot from an older image, but as I already said you don't have ANY vmlinuz and initrd.img files in /boot, not just from the last kernel.

That's why i also suggested purging and installing the linux-image-3.2.0-37-generic hoping that would create the correct vmlinuz and initrd.img files.

After purging the virtual headers, try:
apt-get install linux-image-3.2.0-37-generic

---

### Post by meeshkah on 2013-02-14
Ok, I'm installing the 37 kernel, no error. Plus it installed grub and asks (pkg config) where to install grub. I'm selecting sda sdc and sdd and see how it goes.
[...]
GOOD, it installed to all three disks, and it also found the Ubuntu install on /dev/mapper/binomiale-root:
```
Found linux image: /boot/vmlinuz-3.2.0-37-generic
Found initrd image: /boot/initrd.img-3.2.0-37-generic
Found Ubuntu 12.04.2 LTS (12.04) on /dev/mapper/binomiale-root
done
```\o/?

(Won't that create a conflict somehow?)

---

### Post by darkod on 2013-02-14
No conflict. It will just create dual boot menu. It knows the LVM installation is still there.

If you reboot you should be able to boot into md0 without problems now? Is it working?

---

### Post by meeshkah on 2013-02-14
Rebooting now.
[...]
Shouldn't I have run update-grub or something the like?
All I get is a blank (actually black) screen, no grub menu, seems like grub time (Ctrl+Alt+Del reboots).

Edit: And no blinking cursor this time

---

### Post by darkod on 2013-02-14
That message about found kernels is from update-grub usually. It runs it during the process of installing grub2.

One think that you might need to run after the kernel was installed is:
update-initramfs -u

Do that from chroot and see if it helps. Run update-grub again just in case.

Before updating the initramfs double check if there are now kernel files in /boot but the previous message was precise that it found kernel files there.

---

### Post by meeshkah on 2013-02-14
Ok there is definitely something wrong. I checked the file in boot: OK. I update-initramfsed: OK. I ran update-grub to be sure: OK.
I still have a blank screen. No grub menu, no boot.

I wonder if we could just remove the sdb1 (bios_grub) and sdb2 (/boot) partitions that are now only leftovers from the first install that went wrong afterwards? That way we would be sure this is not conflicting in any way.

---

### Post by darkod on 2013-02-14
That is not conflicting. As far as the new system is concerned, it doesn't use sdb1 nor sdb2.

What could be an issue, is if you are actually booting from sdb since that disk contains broken grub2, remember. The working grub2 should be on sda, sdc and sdd.

I know during the grub2 install it asked you where to install it, but I wonder if it can help if you try in chroot to do again the grub-install /dev/sdX on all three disks.

Other than that I am running out of ideas.

The black screen can be video driver issue sometimes, did you have any video issues first time you installed on this machine?

---

### Post by meeshkah on 2013-02-15
Well I tried to boot from all disks and did not get the blank screen when booting from sdb.
I wonder if if could wipe completely the grub and boot partitions (sdb1 and sdb2) using parted, just to be sure that the bios won't even try to boot from sdb and will switch to another?
- In /mnt/etc/mdadm/mdadm.conf i found the line:
```
# automatically tag new arrays as belonging to the local system
HOMEHOST <system>
```Is there something missing? Should <system> be replaced here?

I never had problems with video drivers (mobo-included graphics) and I really don't suspect that. Do you mean there could be a problem in the install on md0 (new root)?
I do not see an equivalent to the mdadm --assemble --scan command at boot; are the arrays correctly assembled?

Ultimately what option will I have if everything else fails? Before reinstalling a whole system anew could I include the fourth disk in the array and restore root from my usb backup in live mode? Would that change anything?

I'm currently trying you suggestion to reinstall grub.

Edit: The LiveCD seems to be 12.10 and my systems appears to be 12.04. Should we concern ourselves about that?

---

### Post by darkod on 2013-02-15
I don't think <system> is an issue.

Yeah, the last option is installing new clean on md0. You can add the fourth disk before that or not, up to you. Your arrays work fine without one disk, so you can add it before installing or add it later.

The fact that the live cd is 12.10 doesn't matter much when working from chroot. As long as it's the same architecture, like 64bit, with the installed system you are accessing.

When working outside chroot, from terminal in live mode it could install different version of grub2 on the MBR but even that is not an issue and can work. Plus you are doing all from chroot.

---

### Post by meeshkah on 2013-02-15
Yes I agree with that all.

One thing though that troubles me: when looking (all in chroot) at blkid and at grub.cfg, like you noticed there are two references to root, the first one is the UUID of the partitions that are in raid5, the second one that I did not notice at first is the UUID of md0. The thing is mdadm "creates" md0 when running mdadm --assemble --scan that is AFTER the system is loaded. How can grub know about md0 if it is not generated yet? Let me rephrase that: is there a way to generate/how is generated md0 "at grub time"? I mean it the reference is the UUID of something that does not yet exists, wouldn't there a "hang" of the system?

Edit: Additionally, is there a way to pruge grub from sdb?
[...]
I found an answer here: [http://davestechshop.net/blog/dave/how-to-uninstall-grub-from-my-hard-disk-drive](http://davestechshop.net/blog/dave/how-to-uninstall-grub-from-my-hard-disk-drive)
Using the dd utility (and with respect to my config):
> Using Linux

You can also use dd command from Linux itself (it removes partition table):
```
# dd if=/dev/zero of=/dev/sdb bs=512 count=1
```
Just remove MBR, without removing the partition table (thanks to Martijn van Vliet at original site):
```
# dd if=/dev/zero of=/dev/sdb bs=446 count=1
```

---

### Post by darkod on 2013-02-15
I think the UUIDs are fine, that's how mdadm works. First it looks for the partitions, the first UUID is the partition, then once assembled it looks for the root partition that's why the second UUID is of the md0 filesystem.

Last night I checked on my home server and it's the same.

I don't like using dd to purge bootloaders since you can really mess up if the commnd is wrong.

This is not a grub issue, something else happened here. Not sure whether you did something after grub2 was failing to install on your disks with gpt and without the bios_grub partition, but the system looks messed up. We copied it, so we copied over the mess too.

I don't think deleting grub2 can help at all, we already reinstalled it, and it got the correct UUIDs which it put in grub.cfg.

If you don't have too much configuration to redo, I suggest a new clean install at this point. It will be much faster even including the time to redo the config.

As we mentioned, you can join the fourth disk first, or not. it doesn't matter. I would actually reinstall first, copy over the data which will still be on sdb, and then repartition sdb with the same partitions as we did for the other disks and join the partitions to the arrays.

---

### Post by meeshkah on 2013-02-15
Ok well let's do a clean install. Maybe I'll be able to cleanly do things now. Messing is learning, in the end :)

Is there some config reset in Ubuntu LiveCD to reset the config in root? (and hopefully make it working again?)

The last iso I have of Ubuntu Server is 11.10 LTS (x64), will I be able to upgrade to 12.04 LTS only? Is there some config I need to do for the new install to use the raid arrays? If I want to name the lvm I will set on the raid5 binomiale, will I have to rename the one on sdb?

When done, I will edit the first post to reflect the changes.

---

### Post by darkod on 2013-02-15
I would avoid upgrading from 11.10. The point of a clean install is also not tp upgrade right away. I would download 12.04 LTS server and keep it at hand. And I wouldn't try upgrading to 12.10 either, I stick to LTS for servers.

I think the raid will be picked up, but I'm not sure. The partitions with the raid flag will be picked up definitely, so to configure new raid you might need to go into Configure Software Raid while in the partitioning menu.

I'm also not sure if you need to create new raid whether the installer will allow you to have a missing member, like the --create command allows you. You will have to find that out for yourself.

At the end of they day you can always create the raid from all four disks and copy files from your usb backup. In that case i suggest booting the server in live mode first and partition sdb with exactly the same partitions as we did with the other three disks using parted. After that start the server install and create the md0 raid1 of 4 partitions for root, and the md1 raid5 of four partitions for /data.

After you create md1 you can go into Configure LVM and use it as physical device for LVM. If you already deleted sdb you can call the VG the same, the old one will be gone anyway. And don't make the LVs too big for start, only as big as you need them and you barely had few GBs used. The point of LVs is that they can grow as you need them, shrinking is little more complicated. So, start small and grow, not start big and then get into trouble how to shrink them best.

Don't forget in the partitioning step to specify all four swap partitions to be used as swap area, one by one.

That should be all.

---

### Post by meeshkah on 2013-02-15
OK I'll try one last thing. As there semms to be no hope of booting off sdb anymore, I'll repartition it and add it to the raid arrays once configured. Then I will copy the previous root to sdb2 just like the others, install grub to sdb1 and give it a shot. If it still does not boot, then I will do a clean install like you said. I already downloaded the Ubuntu Server 12.04.2 LTS CD.

Questions for you (still):
- if I add sdb (assuming correct partitioning) to md0 and md1, will the mirroring of md0 propagate to sdb2 and populate it with the copy of the root? Or will I have to copy it from the USB? (Am I clear?)
- how do I add sdb2 (assuming correct partitioning) to the raid arrays?

---

### Post by darkod on 2013-02-15
Correct, simply adding it to the array makes it sync. You will see in /proc/mdstat that it will say md0 Syncing until it finishes.

You should add sdb2 and sdb4 with something like:
```
sudo mdadm --manage /dev/md0 --add /dev/sdb2
sudo mdadm --manage /dev/md1 --add /dev/sdb4
```

That will do all the work and resync the array onto the new partitions.

---

### Post by meeshkah on 2013-02-15
Oh my, I'm getting now that syncing raid 1 is much more faster that syncing raid 5 since mdadm has to "restripe" all data onto 4 disks instead of 3 for raid5.
So it's a complexity in n squared (n²) = the amount of data to the power of 2. If I'm not mistaken.

It has already synced md0 and is forecasting a 255min-long syncing for data on md1, even though it has no data!
Would it be bad to reboot now or is there no need to wait for mdadm to finish working?

Edit: Damn! I forgot to mkfs.ext4 a partition in sdb2 BEFORE adding it to the md0 RAID array. And the mirroring still occurred.

---

### Post by darkod on 2013-02-15
> **meeshkah said:**
> 

Edit: Damn! I forgot to mkfs.ext4 a partition in sdb2 BEFORE adding it to the md0 RAID array. And the mirroring still occurred.

That's ok, you don't make the filesystem on the partition. md0 contains it.
I'm not sure if restarting can mess up the syncing. I think it will continue when it boots. The syncing would have been needed in any case when adding the disk, sooner or later.

---

### Post by meeshkah on 2013-02-16
Ok GREAT NEWS! The syncing finished so I could reboot off the Ubuntu Server 12.04.2 LTS amd64 CD. Instead of going with the Ubuntu install I chose for a try to go with the "Boot from first hard disk" option. AND IT DID! The system could not mount /home nor /var/www nor /home/ownCloud as all these were deleted and are on the usb recovery. I'm logged in right now.
In teh end what did the trick was to remake the partitions on sdb from scratch. I'm not sure I understand it fully but it worked.

I think I only have to create the lvm and the lv on the raid5 array in order to mount these volumes. The thing is I don't know how to setup an lvm on md1. mdadm is installed OK and /proc/mdstat returns the arrays OK. The lvm2 package is installed too.

As LVM is already installed, I used the following commands:
```
$ sudo pvcreate /dev/md1
$ sudo vgcreate binomiale /dev/md1
$ sudo lvcreate --name home --size 200G binomiale # etc for -web and -cloud
```
(Thanks [http://www.howtoforge.com/linux_lvm_p3](http://www.howtoforge.com/linux_lvm_p3) !)

I am now wondering what would be best between using ext4 of XFS filesystems? Is there one which could be better for RAID5 use?
The wiki for XFS seems to feature more write optimisation, is that correct?

Your advice?

Edit: And how do I make sure the swap is correctly used?

Edit 2: Based on the conversations and considerations here: [http://lwn.net/Articles/476263/](http://lwn.net/Articles/476263/) I decided to stick with ext4 fs. Seems much more reliable to me. Quick explanation: bottom line XFS does A LOT more caching than ext4 that may result is A LOT more data loss than ext4. Although that was over a year ago, I fear some of the issued pointed out there are still not solved. So I stick with ext4.

---

### Post by darkod on 2013-02-16
I haven't investigated too much about ext4 vs XFS. If I remember correctly, XFS was more efficient for big files, while ext4 is universal.

So, if you have 85-90% big files, I guess XFS might be better for you. But I haven't used it and and don't know much about it.

Also don't forget you need to do the mkswap on /dev/sdb3 so that it is formatted as swap area and gets an UUID assigned.

I have attached an image of fstab on my home server, you can see how both swap partitions are mounted and with which options. You will need to do that for all four swap partitions.

And after you create and format the LVs you will need to add them to fstab of course (unless you already did that).

Glad you got it going. :)

---

### Post by meeshkah on 2013-02-18
Ok great news, I'm managed to retrieve my original install without any need for a start from scratch concerning the system. I could get everything back on.

I'm finally back to normal. Ahhh! 

Thank you so much for all your help and all your time helping me. Know that you have been my only hope of wiggling my way around a new install for a very long time. I truly thank you for bearing with me that long.

Just one more thing I'd like to do to (hopefully) increase my HDDs life: to make idle hard disks go into standby: [http://zackreed.me/articles/60-spin-down-idle-hard-disks](http://zackreed.me/articles/60-spin-down-idle-hard-disks)
I'm not sure that would be very helpful since the root, which is on all disks woudld probably keep all four disks "awake".
May I ask your thoughts on that?

---

### Post by darkod on 2013-02-18
With root on the disks it will be difficult if not impossible to spin them down. For disks that are only for data, should be very easy following the link you posted.
To make them spin down when root is on them would involve palying around and probably disabling many log services, since if various logs write on the disk it will be used and won't spin down.

But later you might regret disabling logging if a problem occurs and you can't troubleshoot it.

---

