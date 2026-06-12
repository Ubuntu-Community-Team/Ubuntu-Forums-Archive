---
title: "Nvidia updates hosed my system"
date: 2022-01-02
forum: Installation &amp; Upgrades
---

### Post by watchpocket on 2022-01-02
A few days ago I updated to a long list of nvidia updates. 

When I re-booted, every time I entered my password in the login window, instead of logging in, I was repeatedly returned to the login screen.
 
This happened on both my drives (because I allowed those updates to come in on both):
 
The 1st drive *(nvme0)* was running Ubuntu-MATE 20.04.3 with ***the 5.11 kernel***;
 
the 2nd drive* (/dev/sda - on an internal SSD)* was running Ubuntu-MATE 20.04.3 with ***the 5.4 kernel***.
 
I managed to use Timeshift to somehow ***replace ***the **5.11 kernel **20.04 OS that was on nvme0, with** the 5.4 kernel** 20.04.  (So I do at least have one working system - on nvme0.)
 
But now on /dev/sda, I don't even get to the login screen.  I can't mount /dev/sda.
 
Instead, I get these error messages:
 
***run-init: can't execute '/sbin/init': no such file or directory***
 
***target filesystem doesn't have requested /sbin/init***
 
***Initramfs unpacking failed: decoding failed***
 
***Kernel panic - not syncing: attempted to kill init***
 
I tred to do: 
```
sudo update-initramfs -c -k $(uname -r) 
reboot
```
 
and:
 
```
sudo mount /dev/sda1  /mnt
```
 
but /dev/sda doesn't mount, so I have no way to run commands on it. 
 
[B]Here is a boot-info report:
[/B][https://paste.ubuntu.com/p/gZ7KN9jGT2](https://paste.ubuntu.com/p/gZ7KN9jGT2)
 
Please note, when looking at it, that:
 
***nvme0*** is now ubuntu-MATE 20.04 with the 5.4 kernel (previously with 5.11 kernel, and I'd like to restore it to the 5.11 kernel);

***nvme1 ***is an empty drive that I'll eventually put 22.04 LTS on, please ignore it; 

***/dev/sda** *is the internal SSD that now won't boot, and previously held the 5.4 kernel and 20.04 Ubuntu-MATE; (***sda1*** is the EFI partition; ***sda2 ***is the ext4 partition);

***/dev/sdb1*** ("WeirdBeard") is a non-booting SSD used only for storage.

 
***My question is:  How can I restore the SSD OS (/dev/sda)?  ***(with the 20.04, 5.4 kernel.) I don't want to have to re-install, I have too much to lose there.  

Thanks.

---

### Post by grahammechanical on 2022-01-02
I have to ask this question: What did you do to sda? You say:

> **/dev/sda** is the internal SSD that now won't boot, and previously held the 5.4 kernel and 20.04 Ubuntu-MATE;

You include Ubuntu-Mate as being previously on sda. From the error messages you are getting the Linux kernel is crashing because it cannot find certain componants.

Boot Repair shows that sda has an efi partition with efi boot files but boot repair also says:

>  => Grub2 (v1.99-2.00) is installed in the MBR of /dev/sda and looks at sector 
    1634575840 of the same hard drive for core.img, but core.img can not be 
    found at this location.

I do not think that Grub should be installed in the MBR of a GPT partitioned drive with an efi boot partition. Grub on sda is looking for core.img but it is not at the place that grub is looking for it. You have on the same drive two conflicting boot loader systems.

All this is my opinion. I would disconnect nvme0 before allowing Boot Repair to do its repair. Other may disagree and offer better solutions.

Regards

---

### Post by watchpocket on 2022-01-03
> **grahammechanical said:**
> I have to ask this question: What did you do to sda?

When I couldn't log in to either drive, I went into the Grub menu's rescue mode and from the root shell prompt, I ran Timeshift, which was awkward (doing it from the console's root prompt), and I think I got drives/partitions mixed up when I ran Timeshift.

> You include Ubuntu-Mate as being previously on sda.

I think it's still there.  I sure hope it is.

> I do not think that Grub should be installed in the MBR of a GPT partitioned drive with an efi boot partition.

I do need a Grub on sda, though, correct?  I don't know off the top of my head what the correct location for it should be ( /boot/efi/EFI/  ??? )

> You have on the same drive two conflicting boot loader systems.

I will run boot-repair to see if that can be fixed.  

> I would disconnect nvme0 before allowing Boot Repair to do its repair.

I think that would mean removing the nvme0 drive.  I mean, with an SSD, you can just unplug its SATA cable.  Is there a way to disconnect nvme0 without physically removing it?

---

### Post by tea for one on 2022-01-03
> **watchpocket said:**
> I think that would mean removing the nvme0 drive.  I mean, with an SSD, you can just unplug its SATA cable.  Is there's a way to disconnect nvme0 without physically removing it?

Does your UEFI Set Up allow devices to be enabled/disabled (as screenshot)?

---

### Post by watchpocket on 2022-01-03
Oh, yes -- excellent. I'm 99% positive (without looking at it just now) that I can do that in the BIOS / UEFI.  Many thanks for the tip. Meanwhile I'll be digging down for a firmer understanding of all these boot files.

---

### Post by oldfred on 2022-01-04
Ubuntu installer Ubiquity only install grub to first drive. Its a changeable default with BIOS, but with UEFI, it only installs to ESP on first drive, even though change options are shown.
With UEFI/gpt you should never boot in BIOS mode as that would try to repair in BIOS mode. Grub should not then be installed to gpt's protective MBR, but if it is and you never try to boot in BIOS mode, it will not matter. Useing dd to erase it is more dangerous than just leaving it.

With multiple drives & multiple installs, you should only use Boot-Repair's advanced mode. Then you can choose which install & which drive to install its boot loader into. You can have all boots thru one grub as Ubuntu default is, or have an ESP on every drive & choose the install on that drive to boot. May need to change default names in UEFI or you get multiple ubuntu entries but using different ESP and difficult in menu to tell which is which.
To see details:
sudo efibootmgr -v
UEFI uses GUID aks partUUID to know which ESP to look for boot files. Compare partUUID to entry in efibootmgr -v.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

How are you installing nVidia driver?
You always install from Ubuntu repository, so every kernel update gets driver. 
If you use the version from nVidia, you have to manually purge & reinstall with every kernel update.

---

### Post by watchpocket on 2022-01-04
I want to respond to this once I think about it a bit more, but right now I'm wondering if anyone here is able to look at [my pastebin link]("https://paste.ubuntu.com/p/gZ7KN9jGT2/") and determine if the system & files & so on that I previously had on nvme0 (UbuntuMATE 20.04 w/ 5.11 kernel) are retrievable.  

I think what I *may have* done with Timeshift was copy what was on sda and put it on nvme. I might thereby have wiped and installed over the 5.11 kernel OS & its files.  If that's true, if/when I re-gain access to sda, it seems I will likely have the same files & 5.4.0 kernel setup now on both sda and nvme0.

---

### Post by watchpocket on 2022-01-04
> **oldfred said:**
> Ubuntu installer Ubiquity only install grub to first drive.

When you say "first drive," is this the first drive that the installer *detects?*  Or is it what's always the first drive in the "chain" (for lack of a better word) of drives?

And does the installer then show you which drive it's about to install on, so that you know which one it is?

> with UEFI, it only installs to ESP on first drive,

In my case, it sounds like this would likely be my nvme0 drive.  The ESP partition on that drive.

> Grub should not then be installed to gpt's protective MBR, 

That means that the first line of my [pastebin boot info summary]("https://paste.ubuntu.com/p/gZ7KN9jGT2/") that says:[I]

No boot loader is installed in the MBR of /dev/nvme0n1

[/I]is as it should be, since it's referring to a UEFI/GPT drive, would that be correct?

> but if it is and you never try to boot in BIOS mode, it will not matter. Useing dd to erase it is more dangerous than just leaving it.

If Grub shouldn't be on the MBR of /dev/sda, I'd frankly like to get it out of there.  Is there a safer way to remove it than using dd?

> With multiple drives & multiple installs, you should only use Boot-Repair's advanced mode. Then you can choose which install & which drive to install its boot loader into.

This is valuable info, thanks, will do.


> You can have all boots thru one grub as Ubuntu default is, or have an ESP on every drive & choose the install on that drive to boot.

Right now I have an ESP partition on both my OS drives. I thought an ESP was necessary on any drive I format as UEFI/GPT.  So if I use just one Grub, located on one of my drives, I don't need an ESP on the 2nd or 3rd drive I put an ubuntu OS on?  

> How are you installing nVidia driver?

I think I originally installed Nvidia driver v. 495 off of the Nvidia site, but for the updates I use the Launchpad.net graphics-drivers PPA.
(whose updates, btw, caused my whole problem and made both my installs un-log-into-able.)

Also, this raises a question: 

Under "Additional Drivers," I currently have the choice to use nvidia drivers 460, 460-server, 470, and 495.  (And of course the nouveau driver).  Shouldn't I get rid of 460 and 460-server?  Where in the file system do I go to do that?  (And would I want to keep 470 as a backup to the 495 driver that I'm currently using?)


> You always install from Ubuntu repository, so every kernel update gets driver. 

I think my kernel updates *have* been getting the driver OK.

---

### Post by tea for one on 2022-01-04
> **watchpocket said:**
>  if the system & files & so on that I previously had on nvme0 (UbuntuMATE 20.04 w/ 5.11 kernel) are retrievable.
  
[COLOR="#0000FF"]Line 80[/COLOR] - OS#1:   The OS now in use - Ubuntu 20.04.3 LTS CurrentSession on nvme0n1p2
[COLOR="#0000FF"]Line 386[/COLOR] - Ubuntu, with Linux 5.11.0-37-generic (on nvme0n1p2)   07041e0f-1cde-4caf-9b1d-86851e9601ed
[COLOR="#0000FF"]Line 387[/COLOR] - Ubuntu, with Linux 5.11.0-27-generic (on nvme0n1p2)   07041e0f-1cde-4caf-9b1d-86851e9601ed

According to the report, you have booted into your nvme0n1 drive and you are using the 5.11 kernel.

You can list installed kernels with a terminal command:-
```
ls /boot | grep vmlinuz-
```
However, the boot-repair report will not tell you if you have replaced your data from sda.
Are you able to ascertain that for yourself?

---

### Post by oldfred on 2022-01-04
I always like to have an ESP on every drive. If only as backup of a drive fails. But my default boot is always first drive. And I have multiple flash drives to make repairs. Full installs on flash drive & external SSD, rEFInd on very old tiny flash drive that I had retired. 

I manually update grub's 40_custom to boot other installs & turn off os-prober. Grub updates are now turning off os-prober for some security issue. I think Boot-Repair is turning it back on. I also have grub installed to my sda drive for all installs on sda, but have to do a work around. You can edit fstab & then reinstall grub manually or with Boot-Repair to have other drive's ESP used.

In my case it saw NVMe drive as first. But that depend on UEFI and what order it presents drives. Several ways to mount alternative ESP in comments on bug report. Easiest may be to turn off esp flag on  other drives. I use terminal in middle of install to unmount first drive's esp & mount desired esp.
[https://ubuntuforums.org/showthread.php?t=2470524](https://ubuntuforums.org/showthread.php?t=2470524)


If you look you will see two "ubuntu" entries using different partUUIDs. Lines 101 & 102
You see same info with 
sudo efibootmgr -v
And which partUUID refers to which partition.
lsblk -e 7 -o name,fstype,size,fsused,label,partlabel,mountpoint,uuid,partuuid

I only know dd to zero out a MBR, but just beginning where boot code is and not end where partition table is. With gpt & protective MBR, there is one MBR entry saying drive is gpt, so old MBR only partition tools will seen drive as partitioned and not erase it. 

dd's nickname is Data Destroyer. Any typo totally erases whatever you tell it. Sometimes drives mount in different order. My drives all change if I plug in a sdf flash drive which on reboot is then sda & every other drive changes. Have not had NVMe drives change but only have one. Some have accidentally put an extra space in & totally erased system. Double & triple check entry. And if you erase drive & do not have backups, do not ask for help as data is gone.
Zero out MBR only of sda 512 includes partition table, Use 440 if windows as serial number is between 440 & 446. Change sdX to correct drive:
sudo dd if=/dev/zero of=/dev/sdX bs=440 count=1

These are the changes in grub I typically make. I may have different names for different installs. Only showing lines I change.

```
sudoedit /etc/default/grub
GRUB_TIMEOUT_STYLE=menu
GRUB_TIMEOUT=3
#GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
GRUB_DISABLE_OS_PROBER=true
GRUB_DISTRIBUTOR=kubuntu


```

---

### Post by watchpocket on 2022-01-04
> **tea for one said:**
> According to the report, you have booted into your nvme0n1 drive and you are using the 5.11 kernel.

I'm booted into nvme0, yes, but according to ***uname -r*** and ***ls** **/boot | grep vmlinuz-***  nvme0 is using kernel 5.4:

*--> uname -r*   
```
5.4.0-7642-generic
```

 *--> ls /boot | grep vmlinuz- * 
```
11388 vmlinuz-5.4.0-7642-generic
```

--> *ls /boot | grep vmlinuz * 
```
     0 vmlinuz@
11388 vmlinuz-5.4.0-7642-generic
     0 vmlinuz.old@
```


> However, the boot-repair report will not tell you if you have replaced your data from sda.
Are you able to ascertain that for yourself?

What was replaced was the whole 5.11 kernel and everything else that was on nvme0.  The 5.4 kernel was originally on sda.
Now the nvme0 drive is using the 5.4 kernel, and I can't boot sda.  I believe sda still has the 5.4 kernel also.  I think my old working nvme0 / 5.11 is gone.

I'm pretty sure that what I did with Timeshift is wipe nvme0 and put sda's contents on it.  So that if/when I recover sda I'll likely have the same everything on both drives.

Also, for now, in "Other Software"  I've UN-checked the graphics-drivers PPA because it keeps wanting to update that load of nvidia libraries that originally hosed both my installs (I should have updated one and rebooted before going ahead w the same update on my 2nd drive).  I'm only going to let those in once I'm sure I've got TWO working installs - let them update on ONE of the installs to see what happens.

---

### Post by tea for one on 2022-01-04
> **watchpocket said:**
> I'm booted into nvme0, yes, but according to ***uname -r*** and ***ls** **/boot | grep vmlinuz-***  nvme0 is using kernel 5.4:

Your boot report is dated 02 January 2022 and you used Timeshift after you ran the report?
If so, then it would be helpful to supply a revised report with the current situation.

---

### Post by watchpocket on 2022-01-05
Thanks for responding, but I must say that the damage I did with Timeshift was done before I ran the report.  I ran Timeshift a few days before I created the report.  

(I say damage, but running Timeshift was the one thing that has provided me with a working install.)

I ***have*** run Timeshift 2 or 3 times now and I ***may*** have run it once after the report.  

However, SINCE I ran it the first time  (and only since then), my nvme0 drive has been using the 5.4 kernel.  

Before the trouble began, before I installed the nvidia updates that made it impossible for me to log into either install, my installs were always that (my newer) nvme0 contained the 5.11 kernel;  and /dev/sda (a slightly older, internal SSD) contained the 5.4 kernel.

I always had the latest kernel on the newest (NVMe) drive, the older kernel on my older, internal (2.5-inch SSD) drive.

I'm going to clone my one working install (UbuntuMATE 20.04.3 OS, which is using the 5.4 kernel on my nvme0 drive) onto a bootable external SSD drive.  

Then I'll see about bringing my internal SSD /dev/sda back to life.

---

### Post by deadflowr on 2022-01-05
Your kernel version is weird.
Not the normal generic kernel version.

---

### Post by oldfred on 2022-01-05
Also if you clone an install, you cannot reboot with both plugged in.
You cannot have duplicate UUIDs.

I typically suggest a new install, and restore data, list of installed apps & /home from your normal backup to the new install.
If server apps/data, you would also need those from / (root) and maybe some settings from /etc. I edit grub and a couple of files in /etc, but just copy those to /home so backed up.

---

### Post by watchpocket on 2022-01-05
> Your kernel version is weird.

Can you elaborate?  

The 5.4.0 version originated, I believe, when I installed UbuntuMATE 20.04.1 on an SSD (and later upgraded to 20.04.3).  On my nvme0, I first installed 20.04.3, and that came with kernel 5.11.

---

### Post by deadflowr on 2022-01-06
> > Your kernel version is weird.

Can you elaborate?

Current version is only 5.4.0-92-generic. (Though it looks like it will be upgrading to something newer soon as kernel security updates are being rolled out right now)
Your version doesn't exist anywhere in the Ubuntu kernels builds.
Closest I can find about your Kernel is this one: [https://launchpad.net/~system76/+archive/ubuntu/proposed/+build/19851655]("https://launchpad.net/~system76/+archive/ubuntu/proposed/+build/19851655")
Which is a System76 built kernel.
(And also very old by the looks of it)
Do you have any PPAs?

Edit: I should have stated that this really/probably has nothing to do with the nvidia issue as far as I know, but it's just that the kernel version is odd.

---

### Post by MAFoElffen on 2022-01-06
I read the posts in this thread and reviewed the boot-info report...

This is interesting, odd and evolving.

[My disclaimer: Martin Wimpress and Alan Pope (the founders of Ubuntu MATE) have voiced to my son and I that they wish that users of Ubuntu MATE would address issues with their flavor on their Community Forum, so they are aware of what is going on and can address them. I know they are very dedicated to what they feel is their own.]

To ask and answer at the same time... Correct me if I am wrong or misread...

This started out as a problem with an NVidia updated. In trying to resolve that, it evolved into a booting problem when early attempts caused that.

What I read:

There was a kernel change on the OS located on NVMe0 by the OP. That explains the kernel version to DeadFlower and how that happened. That kernel version may be not the norm, but it now works and boots on that drive.

The OP said he got confused on the drive nomenclature, when he did a Timeshift restore... Then he had booting problems... 

I see on the report, that it is booting from the NVMe0 drive as the primary...

On the same report, /dev/sda has both an MBR boot record, and ESP(?) Hmmm.That MBR boot record is invalid, which is not surprising.That might have also been when the disk was an MBR, then later redone as GPT. That may been a leftover from an installation long ago, possibly even when that disk was on another machine. Because that same disk is 'GPT' now. If grub-pc was installed now to GPT, then there would have been a bios_boot partition, which would be the replacement for that on GPT disks. Right? (Thinking out loud.)

Removing or disabling disks... If it were me... I would backup drive /dev/sda. I would then isolated /dev/sda from everything and work on it alone. See what is has on it, and deal with it, without risk to any of the other two drives. I see where /dev/sda1 is EFI, but cannot see where it is marked as bootable(?) I can see where there is a (suspected) good fstab  found in /dev/sda2, but have now idea if what is there is good, or what is there besides that.

Worst case, wipe /dev/sda to clean it up. New GPT partition table. reinstall the OS on /dev/sda and restore the data and config from the backups.

Is that a fair assumption of what was said and discussed?

And what of the status of the graphics drivers on nvme0? I assume they are working with the previous kernel there (an assumption, because once the kernel was installed there, then that was no longer discussed as a problem).

---

### Post by watchpocket on 2022-01-06
> **oldfred said:**
> Also if you clone an install, you cannot reboot with both plugged in.

You cannot have duplicate UUIDs. I typically suggest a new install, and restore data, list of installed apps & /home from your normal backup to the new install.


Point taken, thank you.  I'll definitely do it the way you're suggesting.

---

### Post by watchpocket on 2022-01-06
> **MAFoElffen said:**
> [My disclaimer: Martin Wimpress and Alan Pope (the founders of Ubuntu MATE) have voiced to my son and I that they wish that users of Ubuntu MATE would address issues with their flavor on their Community Forum, so they are aware of what is going on and can address them. I know they are very dedicated to what they feel is their own.]

Understood. I do often post issues in the MATE forum. I haven't yet with this issue but probably will.

> There was a kernel change on the OS located on NVMe0 by the OP. That explains the kernel version to DeadFlower and how that happened. That kernel version may be not the norm, but it now works and boots on that drive.

And I take it that the "weird kernel" Deadflower was referring to is * kernel 5.4.0-7642*, not kernel 5.11.

> On the same report, /dev/sda has both an MBR boot record, and ESP(?) Hmmm.That MBR boot record is invalid, which is not surprising.That might have also been when the disk was an MBR, then later redone as GPT. That may been a leftover from an installation long ago, possibly even when that disk was on another machine. Because that same disk is 'GPT' now. If grub-pc was installed now to GPT, then there would have been a bios_boot partition, which would be the replacement for that on GPT disks. Right? (Thinking out loud.) 

You are totally on to something because this SSD was on my old BIOS computer.  I assumed that making the drive GPT, and creating an ESP partition and an ext3 partition, that an older pre-existing grub would be wiped away.  I guess not.

> Removing or disabling disks... If it were me... I would backup drive /dev/sda. I would then isolated /dev/sda from everything and work on it alone. See what is has on it, and deal with it, without risk to any of the other two drives. 

Yes! thank you.

> I see where /dev/sda1 is EFI, but cannot see where it is marked as bootable(?) 

Looking at /dev/sda1 in gparted, the boot and esp flags are on.

> Worst case, wipe /dev/sda to clean it up. New GPT partition table. reinstall the OS on /dev/sda and restore the data and config from the backups.

This is the exact plan right now.

> Is that a fair assumption of what was said and discussed?

Indeed!  Thanks for your input.

> And what of the status of the graphics drivers on nvme0? 

These Nvidia updates keep coming up every time I run
```
sudo apt update && sudo apt full-upgrade
```
even though I've removed the launchpad graphics-drivers PPA from /etc/apt.sources.list.d,  and that's annoying.

I actually did allow them to update again today (to see if the same thing would happen) and when I rebooted, same problem, these updates caused it so that when I enter my password into the login screen, I get put back at the login screen, so I restored back to yesterday again with Timeshift.

---

### Post by watchpocket on 2022-01-06
> **deadflowr said:**
> Closest I can find about your Kernel is this one: [https://launchpad.net/~system76/+archive/ubuntu/proposed/+build/19851655](https://launchpad.net/~system76/+archive/ubuntu/proposed/+build/19851655)
Which is a System76 built kernel.

That is very interesting, because that has to be where my 5.4.7642 kernel is from.  I pulled this SSD off of my old machine which was in fact a System76 (BIOS-only) machine dating from 2009.

> (And also very old by the looks of it)

Yep.

> Do you have any PPAs?

Yes (actually I have a bunch of them set up), but I deleted the graphics-drivers PPA and I still see the long list of nvidia updates every time I try to do the software updates.  I can't seem to make it so they don't appear when I do updates.

---

### Post by watchpocket on 2022-01-12
I've now recovered my sda drive using Timeshift.   But now, every time I run the Software Updater,  or  whenever I run:

*sudo apt update && sudo apt full-upgrade*

on the command line, the whole suite of Nvidia upgrades (that originally caused me not to be able to login to my install) gets listed for updating, even though I've removed the *Graphics Drivers* PPA, and I've made sure that PPA is in neither /etc/apt/sources.list nor in  /etc/apt/sources.list.d .

These are the updates that caused my original problem of not being able to login, the first time I allowed them to upgrade. 

 Later, after I'd recovered my NVMe drive, I again allowed those upgrades in (as a test, just to see what would happen this time), and the same thing happened. 

And I was able again at that time to recover my NVMe install with Timeshift.

My question:  ***How can I stop these nvidia upgrades from showing up every time I want to run a software upgrade?***

---

### Post by watchpocket on 2022-01-14
*Bump**.*

---

### Post by deadflowr on 2022-01-14
> My question: How can I stop these nvidia upgrades from showing up every time I want to run a software upgrade?
Use apt-mark hold <package-name-here>
```
sudo apt-mark hold nvidia-###
```
replace ### with whatever the version is. Or replace nvidia-### with whatever the proper nvidia package name is.

After that he package will show in the apt command line output as being held back.
And in the update-manager/software updater, it will be shown but greyed out , unchecked and unclickable.

---

### Post by watchpocket on 2022-01-14
Much appreciated.   Re my System76 kernel* (Linux 5.4.0-7642-generic)*, what would you (or anyone else here) do if you discovered you were running a System76 kernel on a non-System76 machine?

Things seem to be working OK for the most part, but for all I know, there may be hazards to using this kernel. What kernel might it make sense to move to?

---

### Post by MAFoElffen on 2022-01-15
if it is "working" okay, the question would be, why fix something that is not broke? If it was manually installed, then the path forward will upgrade your current line of kernels and it will be purged eventually on it's own... right?

---

### Post by watchpocket on 2022-01-15
> **MAFoElffen said:**
> if it is "working" okay, the question would be, why fix something that is not broke?

True, though for all I know, the fact that the batch of nvidia upgrades that made it so I couldn't get past the login screen could be related to this System76 kernel that I'm using on a non-System76 machine.

However, unless I learn something more about how running this kernel is bad, I'll take your advice and leave it in place.

> If it was manually installed, then the path forward will upgrade your current line of kernels and it will be purged eventually on it's own... right?

The only problem there is that I don't remember if it was manually installed or not.  For now, I'll leave it.

---

