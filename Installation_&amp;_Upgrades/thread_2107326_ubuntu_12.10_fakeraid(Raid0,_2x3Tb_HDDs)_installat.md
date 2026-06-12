---
title: "ubuntu 12.10 fakeraid(Raid0, 2x3Tb HDDs) installation"
date: 2013-01-21
forum: Installation &amp; Upgrades
---

### Post by Blackkitten on 2013-01-21
Hello, everyone.

The goal is to dual-boot **Windows 8** and **ubuntu 12.10** in **UEFI mode** om a PC with **fakeRAID(RAID0)** consisting of **two 3Tb** HDDs.

But as a first step it would be nice to learn how to install Ubuntu on this configuration.

My steps:

Main idea of how to do this is from here:
[http://ubuntuforums.org/showthread.php?t=1928562]("http://ubuntuforums.org/showthread.php?t=1928562")

**1.** Switching in bios **SATA mode to RAID** and then creating two volumes (RAID devices) (**"Windows"** ~ 1Tb for Windows 8 and **"Ubuntu"** ~4Tb for Ubuntu 12.10).

**2.** I  guess it must be windows 8 installation. There aren't any problems. Windows installs onto it's volume and boots in UEFI mode perfectly.

**3.** Booting from liveCD (actually from usb drive) with option "nodmraid".

**4.** As I'm using two 3Tb HDDs I need to use *mdadm* instead of *dmraid* (*dmraid* can't see Ubuntu volume (RAID device) properly showing only ~400Gb instead of ~4 Tb).

```
sudo apt-get remove dmraid
sudo apt-get install mdadm
sudo mdadm --assemble --scan
```

This gives: 
```
mdadm: Container /dev/md/imsm0 has been assembled with 2 drives
mdadm: Started /dev/md/Ubuntu with 2 devices
mdadm: Started /dev/md/Windows with 2 devices

```

And "disk" utility sees RAID config properly. Tried to bechmark it - everything works as one can expect.

**5.** Making a 500Mb FAT32 partiotion in the beggining of Ubuntu volume. For grub efi. Launching *Ubiquity* with **"-b"** option.

Yes, I want to install *Grub* later ("-b"). Because *Ubiquity* fails to install it with some "can't install grub-dummy package" error.
Trying to use several links to install grub efi:
Main tutorial:
[http://superuser.com/questions/376470/how-to-reinstall-grub2-efi]("http://superuser.com/questions/376470/how-to-reinstall-grub2-efi")
Some information about efi partion neeed:
[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")

[B]
6.[/B] Complete installation. Don't restart. And then trying to install *Grub*.

By the way: 
/dev/md125   - is my Windows volume.

In order they are placed on the disk:
/dev/md126   - ubuntu volume.
/dev/md126p1 - partition 1 for efi system partition type for grub.
/dev/md126p3 - partition 3 for root directory
/dev/md126p4 - partition 4 for home directory
/dev/md126p2 - partition 2 for swap


```
sudo mount /dev/md126p3 /mnt
sudo mount /dev/md126p1 /mnt/boot/efi
for i in /dev /dev/pts /proc/ /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/
modprobe efivars
sudo chroot /mnt

apt-get update
apt-get install --reinstall grub-efi-amd64

```

This gives me some errors:
```
Unpacking replacement grub-efi-amd64 ...
Setting up grub-efi-amd64 (2.00-7ubuntu11) ...
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-3.5.0-17-generic
Found initrd image: /boot/initrd.img-3.5.0-17-generic
/usr/sbin/grub-probe: error: disk `md126,3' not found.
/usr/sbin/grub-probe: error: disk `md126,3' not found.
/usr/sbin/grub-probe: error: disk `md126,3' not found.
grub-probe: error: disk `md126,4' not found.
Adding boot menu entry for EFI firmware configuration
done

```

Here is the first problem. I don't know why it looks for *md126,3* disk instead of *md126p3* which exists. 


**7.** Let's try to move futher and try next:

```
grub-install /dev/md126p1
```

But again:

```
grub-install /dev/md126p1
/usr/sbin/grub-probe: error: disk `md126,1' not found.
/boot/efi doesn't look like an EFI partition.
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.

```

Same error and new ones. What is wrong here?

/boot/efi is empty after this. But /boot/grub consist of next:

```
fonts  grub.cfg  locale  x86_64-efi
```

Anyway in order to install grub efi I also to use *efibootmgr*. It gives no errors I guess:

```
efibootmgr -c --disk /dev/md126 --part 1
BootCurrent: 0002
Timeout: 0 seconds
BootOrder: 0000,0002,0001
Boot0001  Hard Drive 
Boot0002* UEFI:  USB FLASH DRIVE PMAP
Boot0000* Linux

```

And bios sees "Linux" along with "Windows boot manager" but nothing happens if one tries to load "Linux" from bios.

That's it, I'm stuck here and need some serious help as I don't understand a lot in this. 

P.S. Next steps would be making RAID assemble on start up as described in the first link. 
Also I found some advices for shutdown and unmounting RAID on ubuntu shutdown. I think I need them later?
[http://www.kevinmccaughey.org/?p=182]("http://www.kevinmccaughey.org/?p=182")

Actully this guy managed to install ubuntu 12.10 on fakeRAID(RAID5). I almost followed his instructions but failed...
Would appreciate if he writes his thoughts here.

---

### Post by darkod on 2013-01-21
I'm no expert in fakeraid especially with the new uefi, but are you usre you need to use mdadm instead of dmraid? I always thought mdadm is for linux software raid, and dmraid for fakeraid. I am actually running mdadm on my home server (single boot of course).

Also, it's not clear from your post whether you actually created a 4TB ntfs partition for ubuntu, or only a raid device. I guess you have a single raid0 device of 6TB. If you did make a 4TB ntfs for ubuntu (if you made it from windows it would be ntfs), you need to delete it and leave the space as unallocated. It doesn't install on ntfs and maybe that's why it sees much less space then you expect.

Also, the fat32 efi system partition should be the same for both OSs, there should be only one. You don't create fat32 efi for ubuntu. That's what I have figured out reading uefi threads here.

---

### Post by Blackkitten on 2013-01-21
I created two RAID0 devices using intel RST utility (CTRL-I during POST). One for windows ~ 1 Tb, another for Ubuntu ~4Tb.

Maybe it's better to create only one? In this case I think you are right and only one FAT32 efi partion needed. I think windows creates one. How should I use it after windows installation?

I thought that dmraid do not sees large RAID devices. But I see you point. Will try now.

---

### Post by darkod on 2013-01-21
The grub install on fakeraid at the end of the install fails with the live cd, that is well known. But you should be able to add it later.

That's why the alternate cd was used for raid installs but for 12.10 I don't think there is an alternate ISO file.

---

### Post by Blackkitten on 2013-01-21
Yes, Alternate installer gives an option to skip booloader installation.

But I wanted to use 12.10 instead of 12.04( there is an Alternate iso for this release ) that's why I'm running Ubiquity with "-b" options wich skips grub installation. Is there any differences?

Anyway I can't install it later as my first post states.

So, using intel RST utility I made one 6Tb RAID0 device. Then installed windows 8 on ~1Tb partition leaving 4Tb unallocated.
Then I booted of liveCD (ubuntu 12.10) without any modifications.

And I guess dmraid can't see unallocated 4Tb. There is only 1.6 Tb dm-0 block device.

Here is thread about it:
[http://ubuntuforums.org/showthread.php?t=1783548]("http://ubuntuforums.org/showthread.php?t=1783548")

So everything is for mdadm. The problem is how to install **grub efi** and how many devices create in Intel RST utility? Is it better to have only one device or two for each system?

P.S. Am I right thinking of one raid device as usual HDD? The only difference is need of using mdadm.
Will tutorials for dual-boot with one or two HDDs work here?

---

### Post by darkod on 2013-01-21
Yes, you are right in considering the raid array/device as single hdd. That's the point, the raid does its job, and the resulting device is like a single hdd.

That thread you linked mentiones specifically that mdadm is for linux software raid, which is my opinion too. It never explicitly says the OP is trying to use dual boot. For only ubuntu, I agree, go with mdadm, much better. And that thread never said if the mdadm install was successful and how was it done.

However, the last post mentions that dmraid supports only limited disk size, which I never thought about. Not really a fan of dmraid. If that is true, it might affect you with such large disks.

Another possible issue is Intel RST. You mentioned it. Is that the only raid option you have? I remember threads here about new laptops coming with Intel RST configured as one big hdd and one small ssd for caching drive. Until people disabled IRST they were not able to install ubuntu and use it as dual boot.

Do you have any option to disable IRST but still use raid (have the sata mode in RAID)? Look around in the bios. If there is a specific setting for IRST, disable it but leave the sata mode to RAID. Then try entering the raid bios (option) and set up a new array, just in case.

Sorry I can't help much, I still think dmraid is the way to go with fakeraid. You might wanna google around for using dmraid on such a big array.

---

### Post by Blackkitten on 2013-01-21
Maybe you're talking about **intel rapid start technology**? If so I'm not using it, maybe I should check for it's state.

I was talking about **intel rapid storage technology option rom utility**. It's the only way for me to use raid.
And, of course, I have SATA controller in RAID mode.

---

### Post by oldfred on 2013-01-21
I try to avoid RAID as I know little about it. 

But they were trying to eliminate the alternative installer and do everything with the gui version. But RAID did not make it into 12.10. See comments on RAID.
[https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)

Are your sure you want RAID 0?
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
parted (3.0) completely removes filesystem creation and modification support, except for filesystem probing to determine what's in a partition.

---

### Post by darkod on 2013-01-21
Yeah, you are right. That's what I meant, it got me confused for a bit.

Sorry, I have no other ideas. As I said, I still think dmraid is the right way but I wouldn't know if the array size it supports is limited, and whether in your case you can configure working mdadm dual boot at all.
Being a linux software raid package, I thought windows can't even see mdadm devices.

On the other hand, having them as separate raid devices/arrays might help. It would be like using one disk with ntfs and windows, and the other as linux software raid. But the thing is that the raid setup has already created the second raid device, so mdadm shouldn't do it again.

---

### Post by Blackkitten on 2013-01-22
Data redudancy is not important for me. That's why I want RAID0.
And I do not use mdadm for software RAID. RAID is managed by intel RST. mdadm is helping to see it right.

I tried 12.04 alternate cd but received same error while installing grub.

So I think mdadm works fine. I can even mount and use RAID devices I created with intel RTS when booting from liveCD. The problem is how to avoid grub installation problem with ubiquity or how to install grub later.

And the one thing that complicates it all that I need to use grub efi.

---

### Post by tentimes on 2013-01-22
Kitten:

I don't think my guide would apply to your planned configuration.

The reason for this is that I had a separate drive for the OS's that I could boot from. I was not trying to boot from the RAID drive, as I believe this adds an extra level of complexity. My RAID volume was for storage.

I would try this with my guide ([http://www.kevinmccaughey.org/?p=182](http://www.kevinmccaughey.org/?p=182)) and a separate drive for installing and booting the OS's on. I also installed the OS's *before* attempting to assemble the RAID drive.

In answer to those asking why I switched to MDADM instead of DMRAID, this is because it is explicitly recommended by Intel for several reasons (see [http://download.intel.com/design/intarch/PAPERS/326024.pdf](http://download.intel.com/design/intarch/PAPERS/326024.pdf)). The most compelling reason for me is that DMRAID is not under active development, whereas MDADM is. MDADM is no panacea though and it doesn't even have a proper manual (just a confusing syntax guide).

I spent many (>200) hours on this and feel I now understand it to some degree. Most of the problem is caused by the fact that Ubuntu does not boot the RAID code in time for FSTAB or any other operating system components that initialise drives. This is a serious flaw and means you have to bring the volume up yourself, and turn it off yourself, with scripts. IMPORTANT: It also means that I cannot myself see how you can boot from a RAID drive using MDADM. Maybe it is possible with DMRAID, but slecting DMRAID then introduces other problems. I suspect that this is the reason Ubuntu still ships with DMRAID.

My guide gives a lot of information and links, but essentially RAID in Ubuntu is extremely tricky, badly executed and poorly documented. You only have to search to find thousands of threads by people who are stuck with it. Then someone gives a guide, and no one guide (including my own) is the answer to all problems. Each guide addresses a specific circumstance.

I'm a programmer and pretty technically proficient and I found getting this working extremely difficult.

Ubuntu need to address this and integrate and document the process properly. At present it is a real difficulty for the vast majority of users that attempt it.

---

### Post by darkod on 2013-01-22
> **tentimes said:**
> 

My guide gives a lot of information and links, but essentially RAID in Ubuntu is extremely tricky, badly executed and poorly documented.

I have to react a little bit on this. I think you are being quite unfair.

The issue as I see it (and I might be wrong of course), is that fakeraid is designed more towards windows. If that is the case, I wouldn't say it's a piece of cake making linux "understand" it fully and work with it easily. Hell, windows can't even see a simple linux partition, let alone linux SW raid. Why don't they do that for example? If they do, you can have a dual boot on a SW raid array. Fakeraid is SW raid anyway.

I would say linux pays more attention to SW raid, and it looks to me it's more flexible and efficient. Saying raid is tricky and badly executed in general, is very unfair, since you can set up mdadm SW raid in 5mins. I've done it on few occasions and I'm far from linux expert.
Including, I have installed Server 10.04 on Dell Poweredge 850 with HW raid1, worked straight off. But of course, since that is proper HW raid, the device is seen simply as /dev/sda instead of /dev/mapper/...

So, both SW raid and installing on proper HW raid seems the work very well, at least in my experience. Where you get stuck seems to be fakeraid, and it's not called fakeraid for nothing. But you don't have other options since windows doesn't even want to consider allowing you to install differently on raid.

But back to the OP topic, reading the whole thread again I noticed in the first post it reports the assembled md devices as /dev/md/Windows and /dev/md/Ubuntu. Why do you use /dev/md126 later? What is the actual device after you do the --assemble --scan?

Can you post the output of parted after you have assembled the devices with mdadm?
sudo parted -l (small L)

---

### Post by tentimes on 2013-01-22
Even if it was not fakeraid, most of the difficulties would still remain: e.g. mdadm booting *after* the drives are initialised. You could blame mdadm for this, but really ubuntu should make sure it boots early if it envisions anyone using this option for raid.

The whole raid setup in general is extremely difficult, with thousands of people having problems (intel or not). If Ubuntu is to be adoptable for normal users then this is something that needs to be ironed out. Where the blame lies exactly doesn't really matter.

Perhaps it is a bug, but the system for filling bugs is off-putting. I have filed a few, but they have all resulted in arguments and infighting, saying it is someone else's problem, and never a solution. Maybe this is the nature of open source, but Ubuntu is pushing their OS for adoption. Because of this I have not even bothered this time to file a bug for MDADM booting too late to initialise drives. It just wasn't worth the result.

Don't get me wrong, I love Ubuntu and use it every day. But, every problem I have had and fixed is one that you could not expect a normal user to be able to do. That needs to change - and it is to some extent. Ubuntu becomes more user friendly as the years go on, but there are too many "normal" things people need to do that require specialized knowledge (and hours of reading guides) to accomplish. My development system took me 2 days to set up, as opposed to a couple of hours for a comparable system in windows. I need some Linux only features though, which is why I use Ubuntu VM's.

---

### Post by tentimes on 2013-01-22
> **darkod said:**
> I have to react a little bit on this. I think you are being quite unfair.

The issue as I see it (and I might be wrong of course), is that fakeraid is designed more towards windows. If that is the case, I wouldn't say it's a piece of cake making linux "understand" it fully and work with it easily. Hell, windows can't even see a simple linux partition, let alone linux SW raid. Why don't they do that for example? If they do, you can have a dual boot on a SW raid array. Fakeraid is SW raid anyway.

I would say linux pays more attention to SW raid, and it looks to me it's more flexible and efficient. Saying raid is tricky and badly executed in general, is very unfair, since you can set up mdadm SW raid in 5mins. I've done it on few occasions and I'm far from linux expert.
Including, I have installed Server 10.04 on Dell Poweredge 850 with HW raid1, worked straight off. But of course, since that is proper HW raid, the device is seen simply as /dev/sda instead of /dev/mapper/...

So, both SW raid and installing on proper HW raid seems the work very well, at least in my experience. Where you get stuck seems to be fakeraid, and it's not called fakeraid for nothing. But you don't have other options since windows doesn't even want to consider allowing you to install differently on raid.

But back to the OP topic, reading the whole thread again I noticed in the first post it reports the assembled md devices as /dev/md/Windows and /dev/md/Ubuntu. Why do you use /dev/md126 later? What is the actual device after you do the --assemble --scan?

Can you post the output of parted after you have assembled the devices with mdadm?
sudo parted -l (small L)

No offence meant, but is there any point in him continuing with this system if it can't boot? I don't think he can boot using mdadm - as it stands it does not start until after the entire file system is initialised, so can only be used in a system with a separate OS disk. He might be better changing direction and trying a DMRAID solution. I am unsure if that will boot though with fakeraid.

---

### Post by darkod on 2013-01-22
> **tentimes said:**
> No offence meant, but is there any point in him continuing with this system if it can't boot? I don't think he can boot using mdadm - as it stands it does not start until after the entire file system is initialised, so can only be used in a system with a separate OS disk. He might be better changing direction and trying a DMRAID solution. I am unsure if that will boot though with fakeraid.

My expectance all the way is that dmraid is the correct setup for fakeraid. But I don't use it, and I don't know whether it has limitations for 6TB array.

As for your comment about mdadm booting above, I fail to understand it. Of course there will be situations where an unfortunate HW combination might make issues for you, but in general mdadm works quite well (for SW raid, not like the OP is trying to use it for fakeraid, I've never tried that with mdadm honestly).
I recently reinstalled my home server with 2 x 2TB disks in SW raid1 with mdadm, and it simply works. Created the array, installed, rebooted, off you go. I never needed to touch even one letter, or type even one command to make mdadm boot correctly. I do not agree it's a general situation, but of course there can be cases where issues happen.

---

### Post by tentimes on 2013-01-22
What I mean is that if the raid array has not booted, and the OS is on the raid array, it cannot boot. It's chicken and egg. Kitten was saying that he has his OS on the RAID array - that is the problem.

On my system (and in my guide) my OS is on a 1TB separate drive, that boots as normal with the file system. I then have to run a script to assemble the array. Mdadm only kicks in near the end of boot, and even then it will not assemble a fakeraid array - this must be done manually via script. I know it *should* but in practice it does NOT assemble the array, even when it's daemon is started, no matter how much tinkering you do - it just won't do it. You need to run an assemble afterwards and on every boot. You also need to run a script on logoff to pull the array down. If you leave it up it will fail on shutdown and go into integrity check on reboot. It's effectively semi-broken for fakeraid. This is due to the handling of the descriptors and an indirection it used to handle fakeraid.

---

### Post by Blackkitten on 2013-01-22
tentimes, thank you for replying on my comment.

darkod, I'll post parted output later, maybe this evening or tommorow.

To all.

This link has been already posted [http://ubuntuforums.org/showthread.php?t=1928562]("http://ubuntuforums.org/showthread.php?t=1928562") but I think he managed to boot using fakeraid with mdamd.

Or I'm wrong and he also uses separate disk, like tentimes ?

The thing that is confusing me is his chrooting:

```
sudo mkdir /target/
sudo mount /dev/md126p2 /target/
sudo mount /dev/md126p4 /target/home/
sudo mount /dev/sdd4 /target/boot/
sudo mount --bind /dev/ /target/dev/
sudo mount --bind /sys/ /target/sys/
sudo mount --bind /proc/ /target/proc/
sudo chroot /target
```

What is /dev/sdd4 ? Is this separate drive/partition outside of the RAID device? 
If so then it looks like the only option with mdadm is to have separate /boot partition outside of the RAID device ?

Or try to use dmraid as here [http://ubuntuforums.org/showpost.php?p=8643812&postcount=40]("http://ubuntuforums.org/showpost.php?p=8643812&postcount=40") ?

---

### Post by Blackkitten on 2013-01-22
I did it/ But only with one RAID device called Raid_2x3Tb

> **darkod said:**
> 
...

But back to the OP topic, reading the whole thread again I noticed in the first post it reports the assembled md devices as /dev/md/Windows and /dev/md/Ubuntu. Why do you use /dev/md126 later? What is the actual device after you do the --assemble --scan?

Can you post the output of parted after you have assembled the devices with mdadm?
sudo parted -l (small L)

This command gives an error. 

```
sudo parted -l
Error: Invalid argument during seek for read on /dev/sda                  
Retry/Ignore/Cancel? i                                                    
Error: The backup GPT table is corrupt, but the primary appears OK, so that will
be used.
OK/Cancel? o                                                              
Backtrace has 8 calls on stack:
  8: /lib/x86_64-linux-gnu/libparted.so.0(ped_assert+0x2e) [0x7fa2679ab48e]
  7: /lib/x86_64-linux-gnu/libparted.so.0(+0x4127b) [0x7fa2679dd27b]
  6: /lib/x86_64-linux-gnu/libparted.so.0(ped_disk_new+0x58) [0x7fa2679b1698]
  5: parted() [0x406d5f]
  4: parted() [0x407b5a]
  3: parted(main+0x148a) [0x40648a]
  2: /lib/x86_64-linux-gnu/libc.so.6(__libc_start_main+0xed) [0x7fa26719476d]
  1: parted() [0x4064d9]
                                                                          

You found a bug in GNU Parted! Here's what you have to do:

Don't panic! The bug has most likely not affected any of your data.
Help us to fix this bug by doing the following:

Check whether the bug has already been fixed by checking
the last version of GNU Parted that you can find at:

	http://ftp.gnu.org/gnu/parted/

Please check this version prior to bug reporting.

If this has not been fixed yet or if you don't know how to check,
please visit the GNU Parted website:

	http://www.gnu.org/software/parted

for further information.

Your report should contain the version of this release (2.3)
along with the error message below, the output of

	parted DEVICE unit co print unit s print

and the following history of commands you entered.
Also include any additional information about your setup you
consider important.

Assertion (last_usable <= disk->dev->length) at
../../../libparted/labels/gpt.c:980 in function _parse_header() failed.

```

But in /dev there is still md126, m126p1 ... devices.
And in /dev/md there's next:
```
/dev/md$ ls
imsm0  Raid_2x3Tb  Raid_2x3Tb1  Raid_2x3Tb2  Raid_2x3Tb3  Raid_2x3Tb4
```

---

### Post by darkod on 2013-01-22
Those Raid_2x3Tb devices ending in 1-4 look like four partitions on the Raid_2x3Tb array device. So, the bootloader destination would be /dev/md/Raid_2x3Tb if I'm not mistaken. It should always be the whole raid array, not a partition on it.

As for the /dev/md126 devices, they might mean the same, but since installing grub2 on it failed, try it with Raid_2x3Tb.

---

### Post by Blackkitten on 2013-01-22
So, no good news but I have a hope (We'll talk later about it).

Trying to *grub-install* in different ways doesn't help.

So, I'm on step **six**. If you refer to the firtst post of the thread you'll can find the beggining.

Here what I have after chrooting to the installed system and installing grub:

```

root@ubuntu:/# grub-install /dev/md126
/usr/sbin/grub-probe: error: disk `md126,1' not found.
/boot/efi doesn't look like an EFI partition.
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
root@ubuntu:/# grub-install /dev/md/Ubuntu
/usr/sbin/grub-probe: error: disk `md126,1' not found.
/boot/efi doesn't look like an EFI partition.
Path `/boot/grub' is not readable by GRUB on boot. Installation is impossible. Aborting.
root@ubuntu:/# 

```

Now something about hope.

Previosly I had only one RAID device called Raid_2x3Tb. With windows 8 installed on the first 4 partitons.
I booted from **AlternateCD** (Ubuntu 12.04 LTS) and clicked in the grub menu install ubuntu without any additional preparations. The only thing that is important I chose **auto partioning** with **highest free space priority.** 

And it worked ! This gives me a hope.

The bad part is that *dmraid* was used ( not all space on RAID device was  located ) and windows installation was vanished.

But somehow grub was installed by the installer and dmraid was used for managing RAID devices. And in the end the system was booting.

I think it's quite possible to use mdadm instead. And when this will be achieved ( with grub installed ) to dual-boot Windows with ubuntu will not be a problem...

Any guesses, ideas ?

---

### Post by tentimes on 2013-01-22
Try boot repair to clean up GRUB, it looks at what you have and tries to create a working GRUB configuration:

[http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/](http://www.howtogeek.com/114884/how-to-repair-grub2-when-ubuntu-wont-boot/)

If necessary, launch boot repair from a live install USB stick (I have done that).

I have to admit I don't totally understand what you have done, but it sounds like you are getting somewhere and any knowledge you get from it will always come in useful ;)

---

### Post by darkod on 2013-01-22
I forgot to mention earlier, since you have win8 in uefi mode (it has to be in uefi because of the gpt table), are you booting the ubuntu cd/usb in uefi mode too?

You need to boot the uefi cd/usb, not the legacy device (there will be two separate) so that ubuntu can install in uefi including grub-efi instead of grub-pc.

Your limited success with dmraid doesn't surprise me. It would always be my first huntch with fakeraid. It might be better to investigate why does it limit the raid device to 1.6TB instead of investigating mdadm. If you solve the wrong space reported by dmraid, the rest should go fine I guess.

One option that shouldn't be discarded, is the partition table. Windows is sometimes a chaos with gpt tables, and I'm close to not trusting it at all. For example, if the disk has gpt table and you use windows to make msdos table, it deletes only the primary but not the backup gpt table. It leaves it on the disk and later linux tools are confused what is going on.

On your place, I would also try writing a new blank gpt table on the raid array with the ubuntu live mode. Of course that would delete your current win8. And give dmraid a second chance. Something like this:
1. Boot the ubuntu cd in live mode (in this case doesn't matter legacy or uefi mode), open terminal, activate the raid array with dmraid if necessary, note down the main array name (not partitions), and write new gpt table with parted:
```
sudo dmraid -ay
sudo parted /dev/mapper/.....
mklabel gpt
quit
```

That should write a new blank gpt table if you get the device right.

After that reboot with the win8 dvd and try uefi install. When done, try uefi ubuntu install (with 12.04 alternate or 12.10 live cd, your choice). Note that the live cd could fail installing grub, but that can be added later by chroot easily, if that's the only issue.

---

### Post by Blackkitten on 2013-01-23
If somehow I reach the goal of this topic I'll update the first post with instructions. By the way in step 6 there is no need to use *efibootmgr*...

Anyway, back on topic.

1. Boot-repair didn't help. I installed it in live session, but it gave same error about **/boot/grub** being unreachable for grub on boot. 

Forgot to say, it looks like boot-repair uses *dmraid*...

2. I didn't try anything with *dmraid* because of the same reasons tentimes dropped it. With intel saying to use *mdadm* I think maybe it will be standart feature in future releases. But if there will be nothing to do, I'll try to use it.

3. Good news, I've managed to install *grub-efi* (**grub-efi-amd64**). Honestly, it remains mystery for me how I did it. Maybe rebooting PC after running ubiquity helped maybe not. But if things keep going I'll figure out.

4. Grub installed. Reboot. Entering BIOS. There *ubuntu* (UEFI mode) boot opyion appeared. Booting...

5. That's it. Problems again.

I've been drooped to busybox with next output:```

mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: Devices UUID-x:x and UUID-x:x have the same name:/dev/md/RAID_2x3Tb # x:x is some long similar numbers
mdadm: Duplicate MD device names in conf file were found.

 Gave up waiting for root device. Common problems:
# guess this info is nt useful just standart error output.
# but then there is line
ALERT! /dev/disk/by-uuid/y-y-y-y-y does not exist. Droping to a shell # y-y-y-y-y is another long nubmer. Made a picture of them :-)

```

If I try to ```
mdadm -assemble --scan
``` in busybox I have same output:
```

mdadm: CREATE user root not found
mdadm: CREATE group disk not found
mdadm: Devices UUID-x:x and UUID-x:x have the same name:/dev/md/RAID_2x3Tb # x:x is some long similar numbers
mdadm: Duplicate MD device names in conf file were found.
```

I'm not familiar at all with this stuff but I think grub (at least and at last) is installed ?

Need any help :-).

P.S. This guy [http://ubuntuforums.org/showthread.php?t=1928562]("http://ubuntuforums.org/showthread.php?t=1928562") definitly knows something. I PM'ed him.

---

### Post by darkod on 2013-01-23
Duplicate md device names in conf file sounds like you have duplicate devices in mdadm.conf. The file location is /etc/mdadm/mdadm.conf

Take a look from live mode if you can see what you have inside.

---

### Post by Blackkitten on 2013-01-23
Here it is (booted from liveCD, starting array, mounting /dev/md126p3 to /mnt, looking for /mnt/etc/mdadm/mdadmconf):

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=0517aeb4:88466ba9:ecbb499e:20ecf9d7
ARRAY /dev/md/RAID_2x3Tb container=0517aeb4:88466ba9:ecbb499e:20ecf9d7 member=0 UUID=075353bc:34c7c81a:246876ce:edf27e5d

# This file was auto-generated on Wed, 23 Jan 2013 19:58:53 +0700
# by mkconf $Id$
ARRAY /dev/md/imsm0 metadata=imsm UUID=0517aeb4:88466ba9:ecbb499e:20ecf9d7
ARRAY /dev/md/RAID_2x3Tb container=/dev/md/imsm0 member=0 UUID=075353bc:34c7c81a:246876ce:edf27e5d
```

In comparison here is mdadm.conf from liveCD setup (/etc/mdadm/mdadm.conf):

```
# mdadm.conf
#
# Please refer to mdadm.conf(5) for information about this file.
#

# by default (built-in), scan all partitions (/proc/partitions) and all
# containers for MD superblocks. alternatively, specify devices to scan, using
# wildcards if desired.
#DEVICE partitions containers

# auto-create devices with Debian standard permissions
CREATE owner=root group=disk mode=0660 auto=yes

# automatically tag new arrays as belonging to the local system
HOMEHOST <system>

# instruct the monitoring daemon where to send mail alerts
MAILADDR root

# definitions of existing MD arrays
ARRAY metadata=imsm UUID=0517aeb4:88466ba9:ecbb499e:20ecf9d7
ARRAY /dev/md/RAID_2x3Tb container=0517aeb4:88466ba9:ecbb499e:20ecf9d7 member=0 UUID=075353bc:34c7c81a:246876ce:edf27e5d

# This file was auto-generated on Wed, 23 Jan 2013 14:58:26 +0000
# by mkconf $Id$
```

There is a difference, although they must be identical 'cause I executed previously ```
mdadm --detail --scan >> /etc/mdadm/mdadm.conf
```

But what is wrong here?

P.S. I think this post has something interesting [http://www.linuxquestions.org/questions/linux-newbie-8/%5Bubuntu-10-04-amd64%5D-cannot-setup-grub-on-raid-0-set-up-disks-812206/]("http://www.linuxquestions.org/questions/linux-newbie-8/%5Bubuntu-10-04-amd64%5D-cannot-setup-grub-on-raid-0-set-up-disks-812206/")

And maybe because of some read/write restrictions or dumb moves (from my side :-)) I had problems with grub.

---

### Post by darkod on 2013-01-23
I am not sure which array definitions are correct, but there shouldn't be two. The error message said that clearly. Since we don't know which one is correct, lets try only to comment out some of them, but not deleting them fully.

In the mdadm.conf comment out the last two ARRAY definitions by putting # at the start of the line. Save and close the file. Reboot and see how it goes.

If it doesn't work, try commenting out the first two ARRAY definitions, and uncomment the last two.

---

### Post by Blackkitten on 2013-01-23
I think I've half made it. So it's possible! Ubuntu, fakeraid, booting of RAID) device in UEFI mode! 
I'll skip detailed explanation for now (but for later they will be detailed) and pass to the things that seem imprortant to me.

First of all there is still problems. And talking about setting dual-boot with Windows 8 is too early (at least for me, if you have some knowledge, please share).

Problems:

**1.** Duplicated array definitions in **/etc/mdadm/mdadm.conf**. Darkod, it's quite possible you were right about double definition. I've reinstalled *mdadm* and changed the command in **./raidplease** script. The command wasn't right so I had to assemble array manualy in **busybox**. But now **mdadm.conf** is right and I hope the problem is gone.

**2.** I'm not sure if I can boot again. When booting from **bios** I'm loaded into **grub menu**. If I choose **ubuntu** nothing but puple(or whatever color this is) screen happens.

So I have to prees **'e'** and delete some stuff in grub command line. And in general there is some dark or uncertain stuff for me.

That is a big problem. I reinstalled **grub** but this stuff is still there. Here is grub.cfg:
```
#
# DO NOT EDIT THIS FILE
#
# It is automatically generated by grub-mkconfig using templates
# from /etc/grub.d and settings from /etc/default/grub
#

### BEGIN /etc/grub.d/00_header ###
if [ -s $prefix/grubenv ]; then
  set have_grubenv=true
  load_env
fi
set default="0"

if [ x"${feature_menuentry_id}" = xy ]; then
  menuentry_id_option="--id"
else
  menuentry_id_option=""
fi

export menuentry_id_option

if [ "${prev_saved_entry}" ]; then
  set saved_entry="${prev_saved_entry}"
  save_env saved_entry
  set prev_saved_entry=
  save_env prev_saved_entry
  set boot_once=true
fi

function savedefault {
  if [ -z "${boot_once}" ]; then
    saved_entry="${chosen}"
    save_env saved_entry
  fi
}

function recordfail {
  set recordfail=1
  if [ -n "${have_grubenv}" ]; then if [ -z "${boot_once}" ]; then save_env recordfail; fi; fi
}

function load_video {
  if [ x$feature_all_video_module = xy ]; then
    insmod all_video
  else
    insmod efi_gop
    insmod efi_uga
    insmod ieee1275_fb
    insmod vbe
    insmod vga
    insmod video_bochs
    insmod video_cirrus
  fi
}

if [ x$feature_default_font_path = xy ] ; then
   font=unicode
else
insmod part_gpt
insmod ext2
if [ x$feature_platform_search_hint = xy ]; then
  search --no-floppy --fs-uuid --set=root  daa36270-4c12-4ca1-90d8-c2bbffcef46e
else
  search --no-floppy --fs-uuid --set=root daa36270-4c12-4ca1-90d8-c2bbffcef46e
fi
    font="/usr/share/grub/unicode.pf2"
fi

if loadfont $font ; then
  set gfxmode=auto
  load_video
  insmod gfxterm
  set locale_dir=$prefix/locale
  set lang=en_US
  insmod gettext
fi
terminal_output gfxterm
if [ "${recordfail}" = 1 ]; then
  set timeout=-1
else
  set timeout=10
fi
### END /etc/grub.d/00_header ###

### BEGIN /etc/grub.d/05_debian_theme ###
set menu_color_normal=white/black
set menu_color_highlight=black/light-gray
if background_color 44,0,30; then
  clear
fi
### END /etc/grub.d/05_debian_theme ###

### BEGIN /etc/grub.d/10_linux ###
function gfxmode {
	set gfxpayload="${1}"
	if [ "${1}" = "keep" ]; then
		set vt_handoff=vt.handoff=7
	else
		set vt_handoff=
	fi
}
if [ "${recordfail}" != 1 ]; then
  if [ -e ${prefix}/gfxblacklist.txt ]; then
    if hwmatch ${prefix}/gfxblacklist.txt 3; then
      if [ ${match} = 0 ]; then
        set linux_gfx_mode=keep
      else
        set linux_gfx_mode=text
      fi
    else
      set linux_gfx_mode=text
    fi
  else
    set linux_gfx_mode=keep
  fi
else
  set linux_gfx_mode=text
fi
export linux_gfx_mode
if [ "${linux_gfx_mode}" != "text" ]; then load_video; fi
menuentry 'Ubuntu' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-simple-daa36270-4c12-4ca1-90d8-c2bbffcef46e' {
recordfail
	gfxmode $linux_gfx_mode
	insmod gzio
	insmod part_gpt
	insmod ext2
	if [ x$feature_platform_search_hint = xy ]; then
	  search --no-floppy --fs-uuid --set=root  daa36270-4c12-4ca1-90d8-c2bbffcef46e
	else
	  search --no-floppy --fs-uuid --set=root daa36270-4c12-4ca1-90d8-c2bbffcef46e
	fi
	linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=daa36270-4c12-4ca1-90d8-c2bbffcef46e ro   quiet splash $vt_handoff
	initrd	/boot/initrd.img-3.5.0-17-generic
}
submenu 'Advanced options for Ubuntu' $menuentry_id_option 'gnulinux-advanced-daa36270-4c12-4ca1-90d8-c2bbffcef46e' {
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-advanced-daa36270-4c12-4ca1-90d8-c2bbffcef46e' {
	recordfail
		gfxmode $linux_gfx_mode
		insmod gzio
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  daa36270-4c12-4ca1-90d8-c2bbffcef46e
		else
		  search --no-floppy --fs-uuid --set=root daa36270-4c12-4ca1-90d8-c2bbffcef46e
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=daa36270-4c12-4ca1-90d8-c2bbffcef46e ro   quiet splash $vt_handoff
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
	menuentry 'Ubuntu, with Linux 3.5.0-17-generic (recovery mode)' --class ubuntu --class gnu-linux --class gnu --class os $menuentry_id_option 'gnulinux-3.5.0-17-generic-recovery-daa36270-4c12-4ca1-90d8-c2bbffcef46e' {
	recordfail
		insmod gzio
		insmod part_gpt
		insmod ext2
		if [ x$feature_platform_search_hint = xy ]; then
		  search --no-floppy --fs-uuid --set=root  daa36270-4c12-4ca1-90d8-c2bbffcef46e
		else
		  search --no-floppy --fs-uuid --set=root daa36270-4c12-4ca1-90d8-c2bbffcef46e
		fi
		echo	'Loading Linux 3.5.0-17-generic ...'
		linux	/boot/vmlinuz-3.5.0-17-generic root=UUID=daa36270-4c12-4ca1-90d8-c2bbffcef46e ro recovery nomodeset 
		echo	'Loading initial ramdisk ...'
		initrd	/boot/initrd.img-3.5.0-17-generic
	}
}

### END /etc/grub.d/10_linux ###

### BEGIN /etc/grub.d/20_linux_xen ###

### END /etc/grub.d/20_linux_xen ###

### BEGIN /etc/grub.d/20_memtest86+ ###
### END /etc/grub.d/20_memtest86+ ###

### BEGIN /etc/grub.d/30_os-prober ###
if [ "x${timeout}" != "x-1" ]; then
  if keystatus; then
    if keystatus --shift; then
      set timeout=-1
    else
      set timeout=0
    fi
  else
    if sleep --interruptible 3 ; then
      set timeout=0
    fi
  fi
fi
### END /etc/grub.d/30_os-prober ###

### BEGIN /etc/grub.d/30_uefi-firmware ###
menuentry 'System setup' $menuentry_id_option 'uefi-firmware' {
	fwsetup
}
### END /etc/grub.d/30_uefi-firmware ###

### BEGIN /etc/grub.d/40_custom ###
# This file provides an easy way to add custom menu entries.  Simply type the
# menu entries you want to add after this comment.  Be careful not to change
# the 'exec tail' line above.
### END /etc/grub.d/40_custom ###

### BEGIN /etc/grub.d/41_custom ###
if [ -f  ${config_directory}/custom.cfg ]; then
  source ${config_directory}/custom.cfg
elif [ -z "${config_directory}" -a -f  $prefix/custom.cfg ]; then
  source $prefix/custom.cfg;
fi
### END /etc/grub.d/41_custom ###
```

Why this happens, why it can't load? The UUID number that is  everywhere isn't present in my system.

I hope and think that this problem with **grub** is last real problem and after solving it I can move to setting dual-boot configuration.

But for now, until I'll go to  sleep, what *.cfg files are important? Is there anything I can do on running OS to help understand the problem?

Will be happy with any advices opinions!

---

### Post by darkod on 2013-01-23
Did you install in UEFI or I misunderstood that? With UEFI you shouldn't get grub as far as I know. The uefi boot manager does the booting.

Also, if the purple screen starts loading after you have made your selection in the grub boot menu, I think it's not a grub issue. The boot process already continued but gets stuck somewhere.

Use the 'e' to edit the grub ubuntu entry again, delete the 'quiet splash' from the end of the line starting with linux. Then boot like that with F10 or Ctrl+X.

That will show the scrolling text while loading. Take notes where does it get stuck (it will probably stop there, for a while). It might give you a hint.

---

### Post by Blackkitten on 2013-01-23
Yes in **UEFI**. I checked that by this command ( from [https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")):

```
[ -d /sys/firmware/efi ] && echo "EFI boot on HDD" || echo "Legacy boot on HDD"

```

which returns:

```

EFI boot on HDD

```

I don't know if it was **grub** or **UEFI boot manager**. There was some kind of a menu...

I reinstalled **grub** again and corrected command in **raidplease** script. Then restarted. This time there wasn't any menus but again busybox appeared. I typed "exit" and ubuntu loaded.

Will try your advice and post the results.

P.S. I start to think that problem is caused by **/dev/md127**. It's not my array device it's some kind of a container for it:

```

sudo mdadm -D /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid0
     Array Size : 5860528128 (5589.04 GiB 6001.18 GB)
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K


           UUID : 075353bc:34c7c81a:246876ce:edf27e5d
    Number   Major   Minor   RaidDevice State
       1       8        0        0      active sync   /dev/sda
       0       8       16        1      active sync   /dev/sdb
#:~$ 
#:~$ sudo mdadm -D /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 2

Working Devices : 2


           UUID : 0517aeb4:88466ba9:ecbb499e:20ecf9d7
  Member Arrays : /dev/md/RAID_2x3Tb

    Number   Major   Minor   RaidDevice

       0       8        0        -        /dev/sda
       1       8       16        -        /dev/sdb


```

And if we watch /proc/mdstat:
```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid0 sda[1] sdb[0]
      5860528128 blocks super external:/md127/0 128k chunks
      
md127 : inactive sdb[1](S) sda[0](S)
      4776 blocks super external:imsm
       
unused devices: <none>

```

This **/dev/md127** device/arrary/comtainer (do not know how to name it properly) is always inactive but it looks like somehow this fact stops OS loading and results in busybox. And  that's why here [http://ubuntuforums.org/showthread.php?t=1928562]("http://ubuntuforums.org/showthread.php?t=1928562")
the guy had no use **bootdegraded=true** option.

P.P.S. I can't enter that menu anymore. Loading Efi shell from bios doesn't help.

---

### Post by Blackkitten on 2013-01-23
So addind **bootdegraded=true** option to linux line in **grub.cgf** helped. My PC restarts and boots properly. 

Deleting **quite splash** didn't changed anything.

I still can't enter efi shell. Is this okay ? 

Maybe the reason is in fakeraid configuration?

And in general my **grub.cfg** seems suspicious to me.

**In general:**

Only 3 questions remained:

**1.** Is my *grub.cfg* looks ok ?

**2.** This /dev/md127 container. And **bootdegraded=true** option it forces me to use.
Is this ok, how to avoid this?

**3.** How to enter Grub menu or EFI manager menu or whatever menu for modifying boot optioms there instead of **grub.cfg**

---

### Post by darkod on 2013-01-23
The grub.cfg has the root UUID starting with daa36270. I don't see that UUID in mdadm.conf.

Can you also check fstab what does it expect to mount?

I really don't know what is the issue, I can't help more. I have never actually tried a fakeraid with mdadm. So, how do you install and how the bootloader works is unknown to me.

If you suspect grub-efi is a problem, you can try with legacy boot. Ubuntu can use legacy boot with gpt tables. Windows can't. So, legacy boot wouldn't be a real solution for dual boot, even if you make ubuntu to work perfectly.

---

### Post by Blackkitten on 2013-01-23
I was inattentive. It's almost morning! have to go to sleep! 

This UUID is actualy my **/dev/md126p3** which is a root partition. So **grub.cfg** is okay I guess.

The problem is how to get access to boot menu? And what to do with **/dev/md127** container?

I'll continue my research later and update/correct the first post with instruction. It's dual-boot ahead :-).

Anyway, darkod and others, I appreciate your help. Will be glad to see you helping me again.

```

cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/md126p3 during installation
UUID=daa36270-4c12-4ca1-90d8-c2bbffcef46e /               ext4    errors=remount-ro 0       1
# /boot/efi was on /dev/md126p1 during installation
UUID=19AA-FDA7  /boot/efi       vfat    defaults        0       1
# /home was on /dev/md126p4 during installation
UUID=99593296-0b69-4681-9165-aaf8bf0860b0 /home           ext4    defaults        0       2
# swap was on /dev/md126p2 during installation
UUID=3568697f-c09f-4a3d-94c4-c638f72effab none            swap    sw              0       0


```

---

### Post by Blackkitten on 2013-01-24
So, I used google and found that **errors=remount-ro** is actually not an error. It just an option tham nount filesystem in read-only mode if any errors exist. Link:[http://ubuntuforums.org/showthread.php?t=845912]("http://ubuntuforums.org/showthread.php?t=845912")

Also holding "**shift**" during boot will bring in grub menu. 

In  the end only one problem remained - **/dev/md127** and **bootdegraded=true** option I had to use.

Moving onto dual-boot configuration...

---

### Post by tenmoi on 2013-01-24
Hi blackkitten,

Here is what you did in step 6:
```

[B]sudo mount /dev/md126p3 /mnt
sudo mount /dev/md126p1 /mnt/boot/efi[/B]
for i in /dev /dev/pts /proc/ /sys; do sudo mount -B $i /mnt$i; done
sudo cp /etc/resolv.conf /mnt/etc/
modprobe efivars
**sudo chroot /mnt**

apt-get update
apt-get install --reinstall grub-efi-amd64
```

Why did you ever do this? You BLINDLY followed the instructions for rescuing a broken system.:shock:

So, please do a clean install following the instructions as quoted from the UEFI Ubuntu document.

```

General principle

To install Ubuntu in EFI mode:

    Use a 64bit disk of Ubuntu (32bit installer does not detect EFI)

    Use the last version of Ubuntu. Support for UEFI appeared in 11.10, but has become more reliable in next versions. Support for UEFI SecureBoot appeared in 12.10.

    Set up your firmware (BIOS) to boot the disk in UEFI mode (see the "Identifying if the computer boots the HDD in EFI mode" paragraph below)
    Then:
        nothing special is required if you use the automatic installer of Ubuntu ("Install Ubuntu alongside others" or "Erase the disk and install Ubuntu"). Important: if you have a pre-installed Windows and you want to keep it, do not choose "Erase the disk and install Ubuntu".

        if you use the manual partitioning ("Something else"), the difference is that you will have to create and use an EFI partition (see the "Creating an EFI partition" paragraph below). 

```
Here's the full link again: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

WARNING:
Do not repeat your error in step 6. That is 'Do not CHROOT in order to install grub-efi'.

Cheers,

---

### Post by Blackkitten on 2013-01-24
Hello, tenmoi. I'm far from understanding how all this stuff works. And my knowledge about linux and it's commands is miserable. Almost every step I had to google a lot about everything...even  for what is fstab and how to enter grub menu...

So don't be too strict to me.

I've read the page you're reffering to. But the problem is that I'm using **fakeraid** and *mdadm*, not *dmraid*. Due to some bug (launchpad has it I think) grub isn't installing properly during ubiquity execution. 
So I started google how to install it later. That's how I found that ubiquity has "-b" option.

The method I used was also used by several another people(there are links in my first) and it seems quite logical to me:

I mount all the needed directories and then chrooting gives me the opportunity to install needed packages into the system instead of liveCD enviroment.

If I did something bad, please explain me. But i do not see other way to install grub for me.

P.S. By the way everything is working. I had to use **boot-repair** to dual-boot ubuntu and windows using grub...

The only problem is I have to use **bootdegraded=true** option. If somebody knows how to avoid this please share. I think this is because of **mdadm** and it's arrays organisation stucture:

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid0 sda[1] sdb[0]
      5860528128 blocks super external:/md127/0 128k chunks
      
md127 : inactive sdb[1](S) sda[0](S)
      4776 blocks super external:imsm
       
unused devices: <none>
#:~$ 
#:~$ sudo mdadm -D /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid0
     Array Size : 5860528128 (5589.04 GiB 6001.18 GB)
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K


           UUID : 075353bc:34c7c81a:246876ce:edf27e5d
    Number   Major   Minor   RaidDevice State
       1       8        0        0      active sync   /dev/sda
       0       8       16        1      active sync   /dev/sdb
#:~$ 
#:~$ sudo mdadm -D /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 2

Working Devices : 2


           UUID : 0517aeb4:88466ba9:ecbb499e:20ecf9d7
  Member Arrays : /dev/md/RAID_2x3Tb

    Number   Major   Minor   RaidDevice

       0       8        0        -        /dev/sda
       1       8       16        -        /dev/sdb

```

Will update thread later with instructions.

---

### Post by darkod on 2013-01-24
With a failure of more knowledge, I guess the situation is a result of using mdadm for fakeraid. The raid array seems to be "recognized" as an array inside a container, effectively making it a device inside a device. Because of this, it might consider it degraded, even when it actually isn't. Hence it doesn't boot until the bootdegraded option is =true.

Maybe this doesn't happen every time you use mdadm with fakeraid, but in your case it seems it does.

---

### Post by dubsides on 2013-01-24
yes you will have to use the bootdegraded=true option

I have to do that on all flavors of linux even though I now run centos mostly.  (at least to boot the / partition off of a mdadm configured drive)

---

### Post by darkod on 2013-01-24
> **dubsides said:**
> yes you will have to use the bootdegraded=true option

I have to do that on all flavors of linux even though I now run centos mostly.  (at least to boot the / partition off of a mdadm configured drive)

Just for clarification, are you talking about fakeraid?

Because you can definitely use mdadm without bootdegraded=true, but when running a SW raid. Not sure about fakeraid.

---

### Post by tenmoi on 2013-01-24
> **Blackkitten said:**
> Hello, tenmoi. I'm far from understanding how all this stuff works. And my knowledge about linux and it's commands is miserable. Almost every step I had to google a lot about everything...even  for what is fstab and how to enter grub menu...

So don't be too strict to me.

I've read the page you're reffering to. But the problem is that I'm using **fakeraid** and *mdadm*, not *dmraid*. Due to some bug (launchpad has it I think) grub isn't installing properly during ubiquity execution. 
So I started google how to install it later. That's how I found that ubiquity has "-b" option.

The method I used was also used by several another people(there are links in my first) and it seems quite logical to me:

I mount all the needed directories and then chrooting gives me the opportunity to install needed packages into the system instead of liveCD enviroment.

If I did something bad, please explain me. But i do not see other way to install grub for me.

P.S. By the way everything is working. I had to use **boot-repair** to dual-boot ubuntu and windows using grub...

The only problem is I have to use **bootdegraded=true** option. If somebody knows how to avoid this please share. I think this is because of **mdadm** and it's arrays organisation stucture:

```
cat /proc/mdstat
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md126 : active raid0 sda[1] sdb[0]
      5860528128 blocks super external:/md127/0 128k chunks
      
md127 : inactive sdb[1](S) sda[0](S)
      4776 blocks super external:imsm
       
unused devices: <none>
#:~$ 
#:~$ sudo mdadm -D /dev/md126
/dev/md126:
      Container : /dev/md/imsm0, member 0
     Raid Level : raid0
     Array Size : 5860528128 (5589.04 GiB 6001.18 GB)
   Raid Devices : 2
  Total Devices : 2

          State : clean 
 Active Devices : 2
Working Devices : 2
 Failed Devices : 0
  Spare Devices : 0

     Chunk Size : 128K


           UUID : 075353bc:34c7c81a:246876ce:edf27e5d
    Number   Major   Minor   RaidDevice State
       1       8        0        0      active sync   /dev/sda
       0       8       16        1      active sync   /dev/sdb
#:~$ 
#:~$ sudo mdadm -D /dev/md127
/dev/md127:
        Version : imsm
     Raid Level : container
  Total Devices : 2

Working Devices : 2


           UUID : 0517aeb4:88466ba9:ecbb499e:20ecf9d7
  Member Arrays : /dev/md/RAID_2x3Tb

    Number   Major   Minor   RaidDevice

       0       8        0        -        /dev/sda
       1       8       16        -        /dev/sdb

```

Will update thread later with instructions.

Hi Kitten,

I'm not strict to you. Never:p.
And I'm not a linux expert. Nor have I ever had a chance to install an OS in UEFI mode. I'm just trying to help. So please excuse my errors.

I recommend that you reinstall Ubuntu. And when you get to step 6, do not install grub in a chrooted environment. If you use the alternate CD, do not restart just now. You can presss Alt + F2 to start a shell. Make sure that the array is up and running.
```

cat /proc/mdstat

```
You will know that it works if there's the word 'Active'.
```

fdisk -l

```
to see if the following partitions are present:

```

/dev/md126p1 - 
/dev/md126p3 - 
/dev/md126p4 -
/dev/md126p2 -

```

By the way, How did you create the efi partition in the first place? Did the installer offer you the option to create it? From all the documents that I read, people use gparted to create it before installing grub. 
Here's a guide.
```

Launch Gparted (a gui tool is much easier than the text one) and select the drive you're willing to install the system into. (Be sure to select the right one!) Point to the top menu and select Device>Create Partition Table... A warning message pops out. Click on Advanced and select "gpt". Say OK A new GPT disk layout had been created. Now you need to create partitions on it. It's very important that you create as the first and primary partition, a FAT32 volume and you need to assign the label EFI to it. Once the partition is created, right click on it and select "manage flags". Check the "boot" flag and say OK. Move on to the creation of the / partition (you may want to separate /home and /boot. Do it as you usually do. In my case I've just created the / partition), and a swap area. Always prefer primary partitions cause with GPT the 4 primary partition limitation has been removed. Close Gparted.

```

Now move on to installing grub
```
apt-get install --reinstall grub-efi-amd64
```

And see if there remain any errors.

You should pass all of these steps without errors.

For further information please read this:
[http://www.garyhawkins.me.uk/?p=185](http://www.garyhawkins.me.uk/?p=185)

Cheers,

---

### Post by geohei on 2013-02-02
Hi.

After some attempts and lots of googling, I found this thread, though I believe it's more complicated as for what I need.

2 HDDs each 2 TB.
With these 2 HDDs, I created a FakeRAID 1 array (GA-Z77X-UD5H).
The array is only supposed to be a data HDD (no system is installed on it).

An SSD contains dual boot Win7 & Ubuntu 12.10.

Win7 recognizes the FakeRAID 1 properly as one HDD.
Ubuntu 12.10 sees 2 HDDs.

What's the most easiest way to include the FakeRAID 1 HDD into Ubuntu so as it sees it (as Win7) as one single HDD?

Many thanks!

---

### Post by darkod on 2013-02-02
> **geohei said:**
> Hi.

After some attempts and lots of googling, I found this thread, though I believe it's more complicated as for what I need.

2 HDDs each 2 TB.
With these 2 HDDs, I created a FakeRAID 1 array (GA-Z77X-UD5H).
The array is only supposed to be a data HDD (no system is installed on it).

An SSD contains dual boot Win7 & Ubuntu 12.10.

Win7 recognizes the FakeRAID 1 properly as one HDD.
Ubuntu 12.10 sees 2 HDDs.

What's the most easiest way to include the FakeRAID 1 HDD into Ubuntu so as it sees it (as Win7) as one single HDD?

Many thanks!

Try activating it with:
```
sudo dmraid -ay
```

If that reports the device(s) as activated, create a mount point that you want to use, and create an entry in /etc/fstab to mount it on boot. You might need to update the initramfs too:
```
sudo update-initramfs -u
```

---

### Post by geohei on 2013-02-05
Thanks a lot for the reply.

To my surprise, I just had to install dmraid. I didn't even run it. The array became visible as one drive.

Is that the way it should be done, or do I need to run the command "dmraid -ay"?

If I run it ...
```
root@xxx:/home/geohei# dmraid -ay
RAID set "isw_caaijgbgga_Data" already active
```

---

### Post by darkod on 2013-02-05
If partitioning tools like parted can see the array and all partitions on it correctly, no need to run it. Basically that's only to activate the array. I guess installing dmraid did it automatically.

---

### Post by geohei on 2013-02-05
parted?
Also gparted doesn't seem to like the GPT.

Can I use parted and gparted with GPT HDDs (or RAID1 like in my case)?

gdisk seems (!?) to work.

```
root@xxx:/home/geohei# parted /dev/mapper/isw_caaijgbgga_Data
GNU Parted 2.3
Using /dev/mapper/isw_caaijgbgga_Data
Welcome to GNU Parted! Type 'help' to view a list of commands.
(parted) print                                                            
Error: The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating
system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
Fix/Ignore/Cancel? c                                                      
(parted) quit                                                             
root@xxx:/home/geohei# gparted /dev/mapper/isw_caaijgbgga_Data
======================
libparted : 2.3
======================

** (gpartedbin:2964): WARNING **: Unable to create Ubuntu Menu Proxy: The connection is closed

(gpartedbin:2964): LIBDBUSMENU-GLIB-WARNING **: Unable to get session bus: The connection is closed
The backup GPT table is not at the end of the disk, as it should be.  This might mean that another operating system believes the disk is smaller.  Fix, by moving the backup to the end (and removing the old backup)?
root@xxx:/home/geohei# gdisk /dev/mapper/isw_caaijgbgga_Data
GPT fdisk (gdisk) version 0.8.5

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.

Command (? for help): p
Disk /dev/mapper/isw_caaijgbgga_Data: 3907023112 sectors, 1.8 TiB
Logical sector size: 512 bytes
Disk identifier (GUID): 49E842A8-BB2B-46CD-A9B1-85CDBD3D5F8E
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 3907022814
Partitions will be aligned on 8-sector boundaries
Total free space is 4029 sectors (2.0 MiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1              34          262177   128.0 MiB   0C01  Microsoft reserved part
   2          264192      3907020799   1.8 TiB     0700  Basic data partition

Command (? for help):
```
Does all this look normal to you?

---

### Post by darkod on 2013-02-05
You can definitely use parted with GPT. In fact I prefer it sometimes over GUI tools.

I am not sure about that message about the backup gpt table not being at the end of the disk. Some partitioning tool might have not created it in the expected location. Sometimes windows can mess up little bit with GPT.

It looks harmless to accept the Fix option and move it to the end, but I have never done it myself. Or seen that message.

Apart from that, the partitions on it look good.

---

### Post by geohei on 2013-02-05
I believe the error shows with gparted because this tool (as opposed to gdisk and parted) scans all devices. Since both HDDs for the array are /dev/sdb and /dev/sdc, parted fails since these have RAID1 meta data, meaning not properly formatted according GPT rules. The array should be addressed using the /dev/mapper entry. gparted tries both ways, which can't work.

What do you think?

---

### Post by darkod on 2013-02-05
I don't think so. With both parted and gparted you tried to open the exact device, not just Gparted in general. And both showed the same warning message.

Further more, as part of fakeraid, the physical disks shouldn't have any partition table at all, it's the raid device that has the table.

The message is not that ANY table wasn't found on sda and sdb, the message is specific that there is a gpt table but the backup is not in the position where it needs to be.

---

### Post by Blackkitten on 2013-02-12
geohei, did you manage to get your hdds work?

At first I thought that dmraid will not see all the space on your hdds. But they are only 2Tb and you are using RAID1, so I guess everything works.

By the way, gparted also gives some warnings ( similar to yours ) for my setup. But everything works.

P.S. Actually the system is quite stable. I had some poweroffs and resets but the raid configuration still works properly.

And the error with grub I had here is gone. I could not reproduce it.

This thread has all the instructions to make it work. I have to add that I stopped at one raid0 device with single efi partion for ubuntu and windows.

---

