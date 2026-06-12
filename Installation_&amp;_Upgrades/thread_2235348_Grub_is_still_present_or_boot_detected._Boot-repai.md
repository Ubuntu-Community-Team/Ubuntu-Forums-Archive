---
title: "Grub is still present or /boot detected. Boot-repair."
date: 2014-07-20
forum: Installation &amp; Upgrades
---

### Post by neil-phillips5 on 2014-07-20
I need some help please.

I have the following error message;
```

error: symbol 'grub-term-highlight_color' not found.
entering rescue mode...
grub rescue?

```

I tried to solve the issue by following the steps provide by Mountaintree here;
[http://ubuntuforums.org/showthread.php?t=2218362](http://ubuntuforums.org/showthread.php?t=2218362)

That did not solve the issue.
I created a report which can be found here;
[http://paste.ubuntu.com/7825834/](http://paste.ubuntu.com/7825834/)

Googling lead me to;
[https://www.miskatonic.org/2014/04/18/ubuntu-1404-and-grub/](https://www.miskatonic.org/2014/04/18/ubuntu-1404-and-grub/)

I followed the link for boot-repair disk to;
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

I downloaded boot-repair-disk-64bit.iso and booted from it.
Selected the 64bit session (failsafe) option.
boot-repair desktop appears and boot-repair runs.

The first signs of a problem come with the error message;
```

/boot detected. please check the options.

```
I am unsure of which options I should use.

clicking ok takes me to the main boot-repair menu.
Select 'recommended repair'.
Eventually I get to the screen with lots of 'sudo chroot's.

Click forward.
New error message;
```

GRUB is still present. Please try again.

```

Click ok takes me back to the previous 'sudo chroot's screen with the only option to cancel.

Reboot pc.

Brings me back to;
```

error: symbol 'grub-term-highlight_color' not found.
entering rescue mode...
grub rescue?

```

I need some guidance with this one please.

---

### Post by oldfred on 2014-07-20
I do not know RAID, Boot-Repair knows it better.
But you do have to install the correct RAID drivers for it to work and that depends on whether you have BIOS RAID or 'fakeraid' or Linux RAID or some hardware based version.

And there is an update bug.
       Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.

Boot-Repair can do a full chroot with purge & reinstall of grub. 
But you also used grub customizer which adds many new script files into grub. All the ones with proxy in the name are from customizer.
Probably best to also copy grub folder so scripts all are new when chrooted and before you install new grub.


 mv /boot/grub /boot/grub_backup

---

### Post by neil-phillips5 on 2014-07-21
Thank you oldfed for your response.

> **oldfred said:**
> 
       Ubuntu 14.04 Update breaks grub, resulting in "error: symbol 'grub_term_highlight_color' not found" 
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1289977)
You need to chroot &   use dpkg-reconfigure grub-pc instead of grub-install directly, so that the system knows that it needs to run grub-install on that drive the next time grub is upgraded.


I read the bug comments and picked this method to resolve my problem;
[COLOR=#333333][FONT=monospace]```

# mkdir /tmp/drive[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount /dev/sdX1 /tmp/drive[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /dev /tmp/drive/dev[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /proc /tmp/drive/proc[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /sys /tmp/drive/sys[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo chroot /tmp/drive[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# dpkg-reconfigure grub-pc
[/FONT][/COLOR]
```[COLOR=#333333][FONT=monospace]

[/FONT][/COLOR]I am stuck at trying to work out sdX1.
/dev has entries for sda, sda1, sdb, sdc, sdd1.

sudo blkid has a number of entries, sorry cannot copy and paste as i am using another machine for these posts.
the /dev/sdX entries are only /dev/sda1 LABEL="new volume", dev/sdb TYPE="isw_raid_member", dev/sdc TYPE="isw_raid_member"

Gparted tells me there are /dev/sda. /dev/sdb, /dev/sdc, /dev/sdd
```

/dev/sda size is 921.75 GiB, contains sda1, ntfs
/dev/sdb size is 167.68 GiB, reports as unallocated
/dev/sdc size is 167.68 GiB, reports as unallocated
/dev/sdd size is 117.38 GiB, contains sdd1, ntfs

```

lots of information there, but i can make the following deductions,
sdb and sdc are the 2 disks forming the array.
sda is likely to be the 'general storage' disk.
sdd is likely to be the usb device i am using to boot into linux.

That accounts for all the /dev/sdX entries. None of which are any used for the above method.

However
.
.
Gparted also has an entry for, /dev/mapper/isw_daacbdffcg_volume1.
/dev/mapper/isw_daacbdffcg_volume1 size is 335.36 GiB, contains;
```

/dev/mapper/isw_daacbdffcg_volume1p1 size is 5.86 GiB, ntfs, LABEL="Recovery"
/dev/mapper/isw_daacbdffcg_volume1p2 size is 217.71 GiB, ntfs, LABEL="Windows"
/dev/mapper/isw_daacbdffcg_volume1p3 size is 1000.00 MiB, ext4
/dev/mapper/isw_daacbdffcg_volume1p4 size is 101.04 GiB, extended

/dev/mapper/isw_daacbdffcg_volume1p5 size is 78.12 GiB, ext4
/dev/mapper/isw_daacbdffcg_volume1p6 size is 20.51 GiB, ext4
/dev/mapper/isw_daacbdffcg_volume1p7 size is 2.41 GiB, linux-swap

```

Deduction leads me to believe /dev/mapper/isw_daacbdffcg_volume1 is where the linux and windows OS are located.
/dev/mapper/isw_daacbdffcg_volume1p4 is where linux only is located.
/dev/mapper/isw_daacbdffcg_volume1p3 might where grub is located.

I am tempted to do the following;
[COLOR=#333333][FONT=monospace]```

# mkdir /tmp/drive
```[/FONT][/COLOR]```

[COLOR=#333333][FONT=monospace]# sudo mount [/FONT][/COLOR]/dev/mapper/isw_daacbdffcg_volume1[COLOR=#333333][FONT=monospace] /tmp/drive[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /dev /tmp/drive/dev[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /proc /tmp/drive/proc[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo mount --bind /sys /tmp/drive/sys[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# sudo chroot /tmp/drive[/FONT][/COLOR]
[COLOR=#333333][FONT=monospace]# dpkg-reconfigure grub-pc
[/FONT][/COLOR]
```

[COLOR=#333333][FONT=monospace]But I am wary as this is working in an area I am not familiar with.
Hence me seeking further advice/assistance.

Sorry for the long post but I thought it prudent to provide as much information as I can.
Again apologies if some of the information is not needed.
[/FONT][/COLOR]

---

### Post by oldfred on 2014-07-21
I have seen this for fakeRAID with nVidia's BIOS RAID.
 "fakeRaid" with nVidia, note p1 is partition, without p1 is root of RAID volume
sudo mount /dev/mapper/isw_cdjacjeebj_VOLUME_0p1 /mnt
sudo grub-install --root-directory=/mnt /dev/mapper/isw_cdjacjeebj_VOLUME_0

So I think your mount of the RAID volume is correct, not a partition as the RAID is where everything exists. If you have a separate /boot be sure to mount it also as most chroot directions do not mention that.

I just do not know RAID well enough to know if you should use dmraid or mdadm RAID drivers. And that may make a difference?

I thought Boot-Repair had a chroot for the total uninstall and reinstall of grub which may also work or when in chroot you can run other commands?

---

### Post by neil-phillips5 on 2014-07-21
i think i follow what you mean.
I am not sure if it's fake raid or not.
or which driver to use.

I wonder [as previous] if like you say i can mount the mapper rather than the sdX.
I will think on it a bit before I bite the bullet.

In the mean time, and if anyone else is following this and wants to chime in,
here is some info on the raid.

intel(r) rapid storage technology - option rom - 12.7.0.1936
raid id: 0, volumes: name volume1, level: raid0(stripe) size: 335.4GB, status: normal, bootable: yes

physical devices
id:3 wdc, model: wd10jpvx-22j, size: 931.5GB, type/status(vol id): non-raid disk
id:4 intel, model: ssdmceac18, size: 167.6GB, type/status(vol id): member disk(0)
id:5 intel, model: ssdmceac18, size: 167.6GB, type/status(vol id): member disk(0)

So the 2 ssd intel disks are striped to form volume1, which is then partitioned as shown in earlier posts
the wdc is a 1GB storage disk.

---

### Post by oldfred on 2014-07-21
I cannot really help any more, hopefully someone that know RAID stops by.

But I also have seen this and a few users delete the RAID and just use two separate drives. But with RAID 0 part of data is on each drive so you cannot easily stop using it.:
       Do not use gparted on RAID.
[http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid](http://www.howtoforge.com/how-to-resize-raid-partitions-shrink-and-grow-software-raid)
Don't bother with RAID 0 unless you have a specific need for speed without data redundancy, since if one drive goes out, you lose the whole array.
[http://en.wikipedia.org/wiki/RAID](http://en.wikipedia.org/wiki/RAID)
[http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup](http://www.smallnetbuilder.com/nas/nas-features/31745-data-recovery-tales-raid-is-not-backup)

---

### Post by neil-phillips5 on 2014-07-24
I appear to have resolved this issue.

Solution.

[COLOR=#000000]I downloaded boot-repair-disk-64bit.iso and booted from it.[/COLOR]
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)[COLOR=#000000]
Selected the 64bit session (failsafe) option.[/COLOR]
[COLOR=#000000]boot-repair desktop appears and boot-repair runs.

message about /boot detected, basically I ignored the message.
Pick option to resore MBR.
Read what options are available for restore MBR.
in my case it picked for;
 restore mbr, mapper/isw....volume1 (generic mbr),
partition booted, mapper/isw...1p3

eventually reboot pc.

i now have the grub menu.
i picked the newly installed linux version.
login. 

then i ran
sudo dpkg-reconfigure grub-pc
[note, tab will help complete this line as you type]

i put nothing in the first place you are offered to add entries,
and i left the next one as quiet splash.
the final one is a list with entries like /dev/sda, i picked /dev/mapper/isw...1p3.
rebooted after it had finished its thing.

system appears to be running, sudo apt-get update reported nothing to update.

if you take a read of the paste bin url in the above posts you will probably see why those disks/partitions/mappings were used.
especially the last part of the long entry, it mentions
[/COLOR][COLOR=#666666]===================[/COLOR] Default settings
Recommended-Repair[FONT=Verdana]
[/FONT][FONT=Verdana]
initially i tried the reinstall option for grub, same iso as above.
i am not sure if they have to be run repair/reinstall grub then restore mbr or if restore mbr can be run on its own.

IMPORTANT,
your locations for root, boot, /boot WILL most likely NOT be the SAME as mine, so take it slow and read carefuly.[/FONT][COLOR=#000000]
[/COLOR]

---

