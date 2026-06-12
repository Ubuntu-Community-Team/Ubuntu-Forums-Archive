---
title: "Grub problem on LVM?"
date: 2014-11-14
forum: Installation &amp; Upgrades
---

### Post by MAFoElffen on 2014-11-14
Now boots to a Grub prompt:
[http://paste.ubuntu.com/8997748/](http://paste.ubuntu.com/8997748/) 

Migrated system to new disks. Primary is now a 4TB Seagate, 2nd is a 1TB WD on LVM2. I had moved the root LVM VG from a 120G drive. I still have the old drive. If a put that drive back in SAS Tray 0, it will boot  and run fine (w/ the LVM reporting as fine), but trying to get that drive out of the picture. That drive is getting old enough that I have concerns about it. Metal is a Dell PowerEdge 2900 Gen 3. BIOS and firmware is up to date. OS is Server 14.04LTS.

When I set the 4TB up, it shows in GDisk as a 2TB w/ 512 logical/[COLOR=#ff0000]512[/COLOR] physical, but if I take that drive out and look at it on one of Win2012 boxes, the drive shows it reports as 4TB w/ 512 logical/[COLOR=#ff0000]4024[/COLOR] physical. Even though the Grub install on the new primary didn't report any errors during the Grub install, I'm thinking the problem might be that Grub may not be pointing to /boot in sda2? (in the LVM primary def/boot partition. Bootdisk is saying RAID, but there is no hard or soft RAID setup on this box... but is JBOD on SAS6, so setup without RAID as an LVM.

When I setup the new primary as GPT in GDisk: I set the sda1 to type ef02, sda2 to type 8300 w/ a boot flag, sda3 to 8e00... Boot disk now reports both the BOS boot (sda1) and the LVM boot (sda2) as BIOS boot?... Figured I would get advice before making changes that I might regret.

---

### Post by oldfred on 2014-11-14
Did you originally partition drive with gdisk or with Windows?
And some vendors add proprietary bits to make a large drive work as MBR with XP. Then it is seen as 2TB but then has another partition it somehow uses. 
Sometimes they use 4K sectors.

Post these, if drive is sdb:
sudo parted -l
sudo gdisk /dev/sdb -l

With gpt the boot flag can only be on the efi partition or in gdisk ef00. If drive may in future be added to UEFI system I would waste 300MB and add the efi partition now as it should be at beginning of drive and that is difficult to reconfigure unless totally reformatting drive. If booting with BIOS you must have bios_grub partition 1 or 2MB unformatted with bios_grub flag  or ef02 setting in gdisk.

---

### Post by MAFoElffen on 2014-11-14
Fred-
I partitioned it with gdisk. I started with a low-level format on the drive with SeaTools (1-1/2 days worth) to make sure there was *nothing* on it, then with a fresh GPT partition table from gdisk. Went from there using gdisk (the info on how I laid that out is in my first post.) The 4TB is sda. The 1TB is sdb. (pastebin link is the report from boot repair app on the Secure Remix). 

In classes at the moment (3 tests today). Will get you the requested listing when I get back home to that box. Good idea on posting those listing as the boot repair report is misleading... but it was a good initial look at it. I'll try to run boot info on it and post that also. 

If I need to, I could do an extend the LV to add the original disk back in, pvmove back to the origial disk and start the prep over again on that new big disk...

Target is to move everything onto that 4TB, then load that server with ten 4TB+ disks.

---

### Post by oldfred on 2014-11-14
I really do not know LVM, but have seen many installs.

The default install with Ubuntu seems to be a /boot in an ext2 formatted partition and then the rest of the drive as one large physical partition for the LVM. If UEFI they also have the efi partition outside of the LVM. If not encrypted I believe grub will directly use a /boot that is inside / in the LVM, or a separate /boot outside LVM not required. But do not know details of configuring LVM.

It seems like you tried to set types ok. Not sure about boot flag as that should only be efi partition which using gdisk is ef00, so that may have confused things. Parted uses boot flag. Actual partitions are very long GUIDs, so different tools use different codes to set GUID. So gdisk ef00 is the same as parted's boot flag.

Your bios_grub should be unformatted partition with ef02 or from gparted add the bios_grub flag. And it only needs to be 1 or 2MB unless using some of the othe rformats that seem to need very large core.img. The bios_grub is just to store core.img as with gpt there is no space after MBR like MBR(msdos) partitioning has.

Your /boot partition should be ext2 or ext4, but since small you do not need the journal. I have seen suggestions that ext4 with journal off, is better than ext2, so do not know why Ubuntu uses ext2 as its default still.

I would think your drive has 4K physical sectors, so do not know why it is showing 512? That may be part of problem.
Usually you do not need to do low level formats of new drives.

Shows list of GUIDs.
[http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

---

### Post by MAFoElffen on 2014-11-14
Here goes... Attached reports. I put that drive into bay #2 and stuck the origianl boot drive back into bay #0. LVM goes off the GUID's so it does matter what order they are in... Booted off the orginal LVM boot partition to get these reports... so sda in the reports is the orinal boot drive. sdb is same. sdc is the new drive, that will be the new boot drive.

The original plan was to shrink the file system down to within 10% over used, then reduce the VG. I got it down to 2 disks--- the original 160GB LVM boot and the 1TB drive. Then I went to set up the new drive...

The original recipi for moving an LVM root was just for an MBR partitioned drive, not for GPT. I had partioned the LVM boot partition as 1GB, starting on the second sector, filesystem as ext2.... ext2 is what the ubuntu LiveCd uses for a defalt install of the LVM2 boot partion, so that is what I used...I used dump/restore to get the old boot image on the new drive... Then went to install grub and it was a no go. It just failed...

The box is a Dell 2900 Gen 3, so 2007, no EFI... But I thought well heck. I made a small EFI partition at type ef00. Still failed on Grub install, but then said it couldn't find a bios_boot partion, so I converted it to a bios_boot by changing the type to ef02. Grub installed fine... BUT--

Somewhere in the process, it looks like it swapped some of #1 for #2 and als set both #1 and #2 as type ef02!?! and partition one is now startign after partion #2.

I think I can delete the first 2 portions and realign them back to where they need to be. Then set the types back to where they need to. Backup/ restore the LVM boot partition back onto the new drive. Of course, if I moved the VG back onto the old root drive, I could just start over again... and not have to worry about damaging the partition with the VG...

Target is to get it all onto the new 4TB, then grwo with 4TB drives. On LVM and grub... Honestly, this is really my first time installing grub one aan LVM boot drive manually. I was a RAID fan years. Hardware, then software RAID. About a year ago, I set out to learn and force myself to use LVM. At first I was doing LVM on RAID... I liked LVm so much that I settled trusting LVM without doing RAID. Te only real challenge I've faced so far is trying to replace this It does have some challenges, such as tring to change out this root drive.

---

### Post by oldfred on 2014-11-14
Reports?

I thought you had to use RAID with LVM as if any one drive fails the entire LVM is lost? Or do you have good backups to another set of drives?

---

### Post by MAFoElffen on 2014-11-15
> **oldfred said:**
> Reports?

I thought you had to use RAID with LVM as if any one drive fails the entire LVM is lost? Or do you have good backups to another set of drives?
I used to think so. LVM seems fairly reliable and pretty forgiving.

For commercial use, for the iteration of what if's and uptime guarantee's, I would still recommend that. But my 13 servers are private... at my home. I started out forcing myself to use LVM on RAID 50. As you might remember I was sold on hardware RAID solutions until adadm came into it's maturity... Then I took over the mdadm GUI project... Then the job market stalled and I went back to college to document my skills. I had been told that I had plenty of skills, but didn't have any certs or degrees. Currently back in school, collecting degrees and certs... but money is tighter. I am slimming this server farm down to 4 enterprise class servers.

With money being tight, RAID 50 was overkill. That's giving up a lot of disk for redundancy. I went to RAID 5. Then I just came up with a different strategy. On 2 servers, I've been doing JOBD on LVM, taking snap shots, storing those snaphots (iterations of backups) on my SAN, then backing some of those off onto tape. I started thinking about playing with new software type clustering, but... This still seems like overkill for a home network, but I consider this as part of my resume. That, and I keep current with my skill set.

Edit-- Thanx. I just noticed that those attachments got uploaded to my uploads, but didn't attach to that post, did they? Re-attached them from my uploads to my previous post. Now there! 

Please note that when you tell someone to do "gdisk -l"... gdisk does not work like parted or fdisk with "--list". You have to do this format for each physical disk to get output for each device:
```

#sudo gdisk -l <device name> >> <ReportFileName>
sudo gdisk -l /dev/sda >> snoopyReport.txt

```
...and yes, when you partition GPT under Windows, it does strange things to the drive. This 4TB, was an openbox deal that had been originally formatted under windows. There were no partitions, but had GPT tables.Windows had said it was GPT, but gdisk said it was just a protected MBR. I tried to convert it in gdisk as GPT, but was still having diffulgallties. At first it didn't show up under Linux under /dev until I wiped it. Once it was clean, then it showed up fine to the system. That was frustrating, but since I didn't have anything of "mine" on it, that was okay. for some reason, gdisk is stil reporting this drive as 2TB instead of 4TB. Figure that one out... Hoping that is just the translation from logical to physical, on the drive itself. LOL

---

### Post by oldfred on 2014-11-15
I do not think this is the issue. But only one partition per drive should have ef02 bios_grub flag.

Number  Start (sector)    End (sector)  Size       Code  Name
   1          409600         2906111   1.2 GiB     EF02  bios_boot
   2            2048          409599   199.0 MiB   EF02  /boot

Does UEFI/BIOS see drive as 4TB? 

It almost has to have 4K physical sectors. But I do not think you can change that. Unless your low level format did something?
 Every other new large drive now has that. But logical are usually 512 and the one or two that were not were some proprietary thing.
But if 4K then size would be too large?

---

### Post by MAFoElffen on 2014-11-15
The Dell 2900's BIOS does not see any drives at all. Dell 6i SAS6 controller is HBA 0 (Host Bus 0) It see's it. This iron is not UIEF/EFI BIOS. My Win2012R2 box is UIEF BIOS and if I pop it in one of it's bay's, it see's that drive as 4TB... even without an EFI partition.

That is why I didn't think I needed an EFI partition for this with ef00... Though, I think if I did add one, it might just ignore it for this application right?

The two ef02's is **a problem**. I think it inherited that somehow in my grub install efforts. The LVM boot partition 'was" type 8300 before that.

I was unsure on the command structure of installing Grub2 manually to a raw LVM-boot partition on a large GPT disk. Lot's of experience on physical traditional methods and during fresh installs, but manually to raw LVM, that's still a learning issue for me. (then I remembered you...)

I can find references on doing LVM on regular MBR disks, then on doing large, over 2.2TB GPT disks... but not on trying to do both at the same time.

EDIT-- I'm wondering what would happen if I move the PV back off that 4TB... (then I wouldn't have anything on it that I cared about...) and install a fresh server sys on LVM on that drive and see how it lays it out as a default install(?) That would at least get the grub pointing to the correct LVM boot partition...

---

### Post by oldfred on 2014-11-15
I do not know how you mount your LVM but grub needs to see both / (root) which is in LVM and the /boot partition. 
Boot-Repair somehow does that.

Otherwise it is the standard mount partition(s) including separate /boot and install grub to MBR. With RAID you normally install to the root of the RAID which I gather is like the MBR when using RAID?

You can add an efi partition, I often recommend it as now many may move a large drive to a newer system with UEFI or have UEFI but only currently boot with BIOS. It can be difficult to add an efi partition at beginning of drive later when it is full of data. But in your case I doubt it is required. 
It used to be that some motherboards (Intel) required a boot flag on a drive to let you boot at all in BIOS mode, so even if BIOS boot on gpt drive we had to add an efi partition.

---

### Post by MAFoElffen on 2014-11-15
Moving the PV off it. That will take about an hour... 

Plan is then to lay it out as:
```

Number Size  Type  Name
=====  ====  ====  =====
1      1024k ef02  bios_boot
2      ???   ef00  GPT
No other to let the installer do it's defaults)

```
That seem good?

---

### Post by oldfred on 2014-11-15
Gpt is partitioning, the second partition is the efi partition. If not using efi 100MB is plenty as that is the Windows default, and grub does not use much when dual booting. 
In future you could add rEFInd, kernels, grub and lots of other code into efi partition so it is more like a boot partition, then it should be 300 or even 500MB. Mine is 300MB.

The other computer that correctly sees it as 4TB, I might use gdisk on it to make sure it sees total size in gpt partition table correctly?

---

### Post by MAFoElffen on 2014-11-15
> **oldfred said:**
> The other computer that correctly sees it as 4TB, I might use gdisk on it to make sure it sees total size in gpt partition table correctly?

GParted sees this drive as 2TB from that server also. So it seems this is not just related to gdisk and parted... but with this box itself. I just went out to the Dell Server forum and posted a question if other 2900 users are seeing that as a problem being BIOS or firmware related on this box...

---

### Post by oldfred on 2014-11-15
Some older hardware may not be updated enough to see the very large drives.

Several users have posted where the external drive caddy would not work and a new one did. Not sure about RAID, I would think that would have been more far sighted to see larger drives in future.

---

### Post by MAFoElffen on 2014-11-15
pv moved off that drive and the volume removed from the volume group. Will reboot it and play with it.

You may be right. I hear that servrer is popular for NAS now, but 25 views over on the Dell server forum and no replies on that yet.

Going to replace the GPT table and start fresh. Then remove all the other drives and play with it. If Ubuntu install reports the same on that, I'll try a Win2014R2 install disk from that box onto it and see what Win reports is as *"on that iron..."*

---

### Post by MAFoElffen on 2014-11-15
Here is the answer from Dell:
> 
[COLOR=#333333][FONT=Trebuchet MS]There is no issue. The maximum supported drive size on the SAS 6 is 2TB.[/FONT][/COLOR]

So now I'll pickup some red-label 2TB's for it and mount this one on my other newer box. So I guess that box will max out at 20TB.

---

### Post by oldfred on 2014-11-15
So older RAID hardware may not work with newer drives. 
Is that their way to get you to upgrade to new hardware?

---

### Post by MAFoElffen on 2014-11-15
Well-- There is two ways I could read that. One way I could read thier answer, is that the original 6i SAS 6 controller does not support drives over 2TB.... which then, A newer SAS 8 controller may... or that I need a newer iron to support larger drives.

I'm thinking since the controllers are HBA, that the first solution would work. I can live with staying limited at 2TB each drive for a long time. That will put me at 60TB between 3 and one of those has my SCSI RAID towers hanging off it. I'm not hurting for that much space. but it would have been nice to have known before I bought this 4TB drive.

---

### Post by MAFoElffen on 2014-11-16
Not really solved-- But dead-ended with a 4TB drive. Both the 6i PERC SAS6 RAID cards only support up to 2TB drives. Ordered another WD red 2TB drive. Also checking if the H700 RAID controllers will work on my boxes. The challenge on that will be if they will work with the 2900's 1x8 and 1x2 SAS6 backplanes...

---

### Post by MAFoElffen on 2014-11-30
Now completed and solved:
[http://ubuntuforums.org/showthread.php?t=2252290&p=13177777#post13177777](http://ubuntuforums.org/showthread.php?t=2252290&p=13177777#post13177777)

---

