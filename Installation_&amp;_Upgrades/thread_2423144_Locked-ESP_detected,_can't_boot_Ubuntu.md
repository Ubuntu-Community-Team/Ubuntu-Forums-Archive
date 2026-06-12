---
title: "Locked-ESP detected, can't boot Ubuntu"
date: 2019-07-18
forum: Installation &amp; Upgrades
---

### Post by Bucky Ball on 2019-07-18
Hi all,

I have Windows 8.1 and Ubuntu 16.04.6 installed on an SSD (/dev/sda) in EFI mode, 'secure boot' off in BIOS. All has been working fine for years. The computer is used as a DAW (Digital Audio Workstation) and, apart from the SSD, it has five other hard drives installed, not SSDs, regular WD Black HDDs.

I needed to add a partition and change a few things around on a couple of the WD drives, NOT /dev/sda, the OS drive, and, whether coincidental or the cause, now I can't boot Ubuntu. The grub comes up, as usual, Windows boots from it normally, no problems, but Ubuntu won't boot. When I try to boot Ubuntu, I get this message.

```
can't request region for resource /dev/sda5
``` 

/dev/sda5 is my Ubuntu OS partition. 

I have tried Boot Repair using 'Recommended Repair' and 'Advanced' option to make sure things are going to the correct place (the EFI partition is /dev/sda2). No dice. Same result when I try to boot Ubuntu. 

I have tried booting into Ubuntu recovery mode, it takes me to the recovery options that start with 'Resume', etc., but keystrokes on my keyboard have no effect so I can't do much from there. 

Everything on /dev/sda appears to be as it should be (Ubuntu is there, the shim is in the EFI partition, all looks normal to me), but I'm still in the same place.

Here is the boot info. 

[http://paste.ubuntu.com/p/NZ5pyr4mT9/](http://paste.ubuntu.com/p/NZ5pyr4mT9/)

And here is the report after running Boot Repair ... again.

[http://paste.ubuntu.com/p/jc6hm7bHP5/](http://paste.ubuntu.com/p/jc6hm7bHP5/)

When that run finished, I am left with 'An error occurred during the repair' and this message, the same message I have received everytime I've run Boot Repair.

> Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair]. 

The first partition I have is /dev/sda1 and that is marked (in Gparted) as 'Basic data partition, ntfs, label = Recovery'. That partition is 300MiB. Not so sure about creating a /boot/efi partition over that, if that is what the instructions are asking me to do.

I'm in the middle of recording some audio in Bitwig in Ubuntu. Bitwig runs on Windows too, but Windows can't access the EXT4 partitions my Bitwig projects are stored on, so this is bad timing. Besides that, I prefer Bitwig on Ubuntu. 

Any more info required, just ask. In the meantime, any ideas appreciated, thanks for your time and I'll keep digging.

---

### Post by oldfred on 2019-07-18
Seen several locked ESP type issues.
Some just need fsck, some need delete & recreate of ESP, and then new UEFI entries.
Some systems also have an UEFI entry that somehow locks ESP to prevent writing.

And newer Ubuntu installs have changed from mounting ESP with defaults to umask=0077. I believe they changed as defaults allowed full access by anyone which is not the Linux way. But Boot-Repair changed setting to defaults & I normally change mine. But found I have to reboot for change to work as just remounting does not. I may later go back and change to 0077 for security, but like having access.

Using sda2 for ESP, is fine. Many installs use that as that seems to be a Windows default.

I would first check UEFI for any type of setting related. What brand/model system?
I see you have nVidia but use nouveau. I have older nVidia card GT620 and find little difference between nVidia & nouveau. And specs say my Intel driver has about same performance also.

I would try dosfsck to see it that helps. Need to do from live installer so unmounted.
       Must be unmounted
sudo dosfsck -t -a -w /dev/sda2
The -a seems to help in clearing dirty bit
[https://bbs.archlinux.org/viewtopic.php?id=164185](https://bbs.archlinux.org/viewtopic.php?id=164185)

---

### Post by Bucky Ball on 2019-07-18
Thanks for that, Oldfred.

I booted from the Boot Repair USB, opened a terminal and

```
sudo dosfsck -t -a -w /dev/sda2
```

but unfortunately it didn't seem to do much because when I boot Ubuntu, takes me to a screen with

```
can't request region for resource [mem followed by a #] /dev/sda5 
recovering journals: clean
```

/dev/sda5 is my Ubuntu partition. At the same time, I have the 'Checking file systems' on screen with 'Press control+c to ignore and continue' until that ends and it goes to

```
Welcome to emergency mode!
```

... and instructions for various options. In other words, in the same place as I was.

Everything seems to be okay until it tries to boot /dev/sda5, the Ubuntu partition, so wondering if I should run an fsck command on that. Seems to be an issue on that partition. I'm currently in Windows which I booted from the same grub menu screen I am trying to boot Ubuntu from, so the grub and boot process seems to be working ok from sda2. It tries to boot recovery and Ubuntu, but that's when the issues start.

(Gets to recovery screen and options, but keyboard unresponsive there so can't do anything.)

Brand/Model is a custom desktop. Has i7, 16Gb RAM, NVidia GTX 970 card. I occassionally use the machine for video editing in Ubuntu using Blender and last I looked, which was a couple of years ago, I was using the Cuda drivers.

---

### Post by #&amp;thj^% on 2019-07-18
Hello Bucky Ball, :)
When this happened to me on 16.04, I solved the issue running Ubuntu from DVD or USB:
Then Ran:
```

dosfsck -a /dev/"efipartition" #to fix the efipartition, remove ubuntu dir if necessary
sudo mkdir /boot/efi
sudo mount /dev/"efipartition" /boot/efi
cd /boot/efi/EFI/
rm -R ubuntu #if it's still there you must remove it
```
Then i ran:
```

boot-repair **_#must be installed first_**
```

After that, Ubuntu started to be available as a EFI option.
Since then I refuse to dual boot windows. (In fact no windows period.)
Hopefully oldfred will agree.

---

### Post by Bucky Ball on 2019-07-18
Hi 1fallen. ;)

Thanks for that. Before I try it, do you mean I enter "efipartition" or /dev/sda2, my existing "efipartition"?

Just checking.

PS: I trying all this from a Boot Repair USB.

---

### Post by #&amp;thj^% on 2019-07-18
> **Bucky Ball said:**
> Before I try it, do you mean I enter "efipartition" or /dev/sda2, my existing "efipartition"?

Just checking.



Yep.>>my existing "efipartition"
> **Bucky Ball said:**
> 

PS: I trying all this from a Boot Repair USB.
I would think that would be ok, but I used my Live installer to do all this.
PS: You know me, I'm not afraid of the nuclear approach. LOL
EDIT: I have to go to work now, and I hope all goes well. (Fingers Crossed)

---

### Post by ubfan1 on 2019-07-18
Try removing the boot0003 entry from the boot order too with efibootmgr.  The (bad?) entry seems to have been removed, but the boot order entry is still causing IO errors.

---

### Post by Bucky Ball on 2019-07-19
@ubfan1: Thanks for the suggestion. Removed 0003 with 'efibootmgr -b 0003 -B' to no avail. Made no difference, although when I run efibootmgr now, the 0003 entry is no longer there. The following is what is there. 

```
lubuntu@lubuntu:~$ efibootmgr
BootCurrent: 0007
Timeout: 1 seconds
BootOrder: 0001,0000,0007,0008
Boot0000* Windows Boot Manager
Boot0001* ubuntu
Boot0006  
Boot0007* UEFI: SanDisk Cruzer Switch 1.26, Partition 1
```

Tried running Boot Repair once more and still getting the 'An error occurred' and 'Locked-ESP' messages at the end. When I try to boot Ubuntu, still get the 'Can't request region for resource ... etc.'.
___

@1fallen: Thanks for the clarification. Tried your instructions and still getting same error at the end of the Boot Repair about Locked-ESP.

> Locked-ESP detected. You may want to retry after creating a /boot/efi partition (FAT32, 100MB~250MB, start of the disk, boot flag). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot/efi partition:] option of [Boot Repair]. 

My current boot info after that Boot Repair run is here.

[http://paste.ubuntu.com/p/Sbs88DkmNY/](http://paste.ubuntu.com/p/Sbs88DkmNY/)

---

### Post by oldfred on 2019-07-19
If you have run dosfsck and double checked that there is not a UEFI setting that somehow locks the ESP, you may need to do the brute force delete & create new. But will have to also delete all UEFI entries & create new as GUID/partUUID of ESP will change & UUID uses that to know which partition to boot from.

You also are saving Boot-Repair logs into ESP. I would delete all but most recent. 

And back up ESP to know what entries you have and restore so you have files in "new" ESP.
If you restore /EFI/Microsoft you can use efibootmgr to create new "Windows Boot Manager" boot entry. If not you have to use your Windows repair flash drive to fully reinstall Windows boot files & loader.

And if you restore grub files to "new" ESP partition you can use efibootmgr to add new entries. Otherwise you have to do a full reinstall of grub, either manually or usually now easier with Boot-Repair.

So first delete Boot-Repair logs & backup ESP.

---

### Post by ubfan1 on 2019-07-19
Take a look at [https://askubuntu.com/questions/965059/ubuntu-16-04-boot-repair-error-locked-esp-detected](https://askubuntu.com/questions/965059/ubuntu-16-04-boot-repair-error-locked-esp-detected)
Might be bad hardware.
Also see [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1091477)
Suggested to just make a new ESP, move the boot flag and files.

---

### Post by #&amp;thj^% on 2019-07-19
Bucky Ball this is a tough one, but this is only a shot in the dark now.
Some Windows8 computers come with a locked ESP that prevents writing outside the /EFI/Boot and /EFI/Microsoft folders, thus preventing the creation of a /EFI/ubuntu folder.

This leads to a "Read-only" error when trying to install grub-efi.

*** WORKAROUND***:
[list]
[*]1) via Gparted create another EFI partition (FAT32, 200MB, located in the first 100GB of the disk)
[*]2) move the 'boot' flag on it
[*]3) make Ubuntu use this new ESP (eg via Boot-Repair --> Recommended Repair).[/list]
EDIT: OK just tried this myself with **_Boot-Repair from within a Ubuntu Live USB, _**I had to unmount using gParted (right-click on each partition -> unmount) which made the key icons disappear., and then ran Boot-Repair, it then succeeded in repairing my system (using Recommended Repair).
FTR:But then again I could never get to a "Locked-ESP" situation on my end. I just intentionally hosed my system for testing this.

---

### Post by Bucky Ball on 2019-07-21
Apologies for the belated reply and thanks for the input all. I couldn't seem to login to the forums for a day, even though staff tell me it looked like I was logged in from their end.

In any case, I meandered down another path in the meantime. Booting from the Boot Repair USB, I had a look at my fstab file and commented out every entry but the OS partition (sda5), swap and the efi partition (sda2). 

On booting Ubuntu this time, while I still got the 'can't access resource' message briefly, it went through to a login screen and I could login (the Ubuntu recovery option also works and I can move the cursor). Once I got to a desktop though, things were nasty. My Ubuntu settings seemed to be intact, but WAN not connected, even though it says I'm connected to the LAN and getting a good speed. Consequently, can't report directly from that machine.

When I click on one of the partitions in the file manager that is not mounted by fstab at boot, the partition mounts but I also get the message that the partition is already being used. I'll check the exact wording of that message later. Maybe this has something to do with my issue and explains why, when I removed the entries for those partitions from fstab, I could boot to Ubuntu. 

If those partitions are already in use from boot, removing their entries from fstab allows Ubuntu to boot. From this, I might assume that this is not a problem with either EFI (because I get to the grub menu) or the Ubuntu partition (because Ubuntu boots), but with Ubuntu trying to mount busy, or 'locked', partitions at boot. So maybe we are heading down the wrong track with EFI experiments. 

I will fiddle around with fstab a bit more either later tonight or tomorrow and see what I come up with. Been a bit busy so haven't been able to get stuck in as I'd like. I mention this experiment in case it might give anyone a clue as to what's going on.
___

@1fallen  

*** WORKAROUND***:

    1) via Gparted create another EFI partition (FAT32, 200MB, located in the first 100GB of the disk)
    2) move the 'boot' flag on it
    3) make Ubuntu use this new ESP (eg via Boot-Repair --> Recommended Repair).

Yes, I was going to try this and the main reason I didn't was that I have an existing 300mb partition at the beginning of the drive (sda1) which is labelled 'Recovery' in Gparted. I'm guessing this partition has something to do with Win recovery. Not sure I need that as if I want to reinstall Windows, I'd do it from scratch as using Win recovery would wipe everything on the drive (from what I believe). 

Another reason is, in light of my experiments with fstab, the problem seems to be with the partitions Ubuntu's fstab is attempting to mount being busy at boot rather than with EFI or the Ubuntu partition. 

Just to refresh, this all started when I resized a couple of partitions and created an NTFS partition on one of the hard drives. My guess is that this has created confusion for Ubuntu and maybe it's looking for the wrong, or wrong sized or type, partition(s)? 
___

Any and all thoughts on any of this appreciated. In the meantime, I'll take a closer look at the other suggestions, experiment a little more with fstab and the messages from the unmounted partitions, and get back to this thread soon. 

Thanks again, people.

@ubfan1: Yes, I had seen that thread suggesting this could be a sign of hardware failure. Thought I'd nut out how to run smart tools soon and see what that coughs up. The SSD is about five years old so it's possible I guess. Hoping not.

---

### Post by Bucky Ball on 2019-07-22
Update: fixed ... I think. A simple oversight on my part so sorry to waste everyone's time. Would have been nigh on impossible for anyone else to guess this was the cause from the info given.

After booting successfully by changing my fstab to just the OS, EFI and swap partitions, I began to uncomment the other partitions in fstab one by one.

Then it hit me. At the bottom of the fstab was this line. I'd commented it out with the others and still hadn't put two and two together.

```
# /mnt/Win7Virt
# UUID=a5d96e1a-164b-4523-b0e7-67fa10e0fd73 /mnt/Win7Virt     ext4    errors=remount-ro 0     1
```

When I deleted a partition and resized and created others before the chaos, this is the partition I deleted. It doesn't exist. Must have been the issue as I uncommented the rest, rebooted and back to normal. 

So the problem appears to have been that Ubuntu fstab was trying to mount a partition that no longer existed and throwing a 'Locked-ESP'. Or was it? There were also these two entries.

```
UUID=A869-5E57  /boot/efi       vfat    umask=0077      0       1
#UUID=A869-5E57 /boot/efi       vfat    defaults        0       1
```

This is how they are now. I originally had the hashtags the other way around. Not sure if this made any difference and unsure why I have two EFI entries. 

For some odd reason I had connection to the router but not the internet and had to change the nameserver in /etc/resolv.conf to the same as my laptop (from 127.0.0.53 to 127.0.1.1) to get there, but that is another story.

Thanks all for all the input and sorry to lead us up the garden path. Guess I'm a little out of practice as all my machines pretty much 'just work'. :)

Solved.

(PS: Thanks oldfred, I will delete those boot infos from EFI.)

---

### Post by oldfred on 2019-07-22
Back with 14.04 and before the mount of the ESP used defaults. After that they changed to 0077 which is no permissions to write into it.

I change mine as I use ESP to have copies of my /EFI/ubuntu and the UEFI update files for my UEFI. 
But I think they changed it to 0077 for security reasons and am thinking I maybe should change back to 0077 and only use partition from live installer or another FAT32 for UEFI updates.

Boot-Repair automatically changes the mount  of the ESP also to defaults. It then may save its reports into that partition or into /var/logs.

---

### Post by Bucky Ball on 2019-07-22
Thanks for that further info, oldfred. ;)

---

