---
title: "Broken LVM array and I need the data off 2 disks"
date: 2010-02-28
forum: Installation &amp; Upgrades
---

### Post by themac on 2010-02-28
[FONT=Tahoma][FONT=Arial]Hi[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]I am new to ‘fiddling’ with Ubuntu (and definately no IT expert) having previously had a FC5 server setup to use Samba services to store photos and camcorder files. My problem is that a friend set up my FC5 system and all I had to do was set up the file shares in Samba.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]My machine had an 80GB HDD which contianed the base FC5 installation, with 2 nr 320GB HDD’s for photos and videos. The problem occurred when I decided to upgrade to Ubuntu server and being a novice I never realised that I would not be able to read the data from my two 320GB drives as they have previously been setup in an LVM. I thought that like windows disks I would be able to just plug them back in to a Linux system and ‘away we go’, sadly not to be.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]I have searched the forum for help on my subject and found a couple of useful threads ([http://ubuntuforums.org/archive/index.php/t-642329.html](http://ubuntuforums.org/archive/index.php/t-642329.html)) but none that has successfully helped me to recover the data on them. I am confident that the data is till there, it's just that I can't get at it.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]In my previous system I had have found out that I had one logical volume group - VolGroup00, with 3 physical volumes - PV0(80GB), PV1(320GB0, and PV2(320GB),  and three Logical Volumes, - LogVol00, LogVol01, and LogVol03.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]The new Ubuntu server is currently installed on the old PV0 and the problem is that I do not know how to link the two 320GB disks up to the new Ubuntu server to view and backup the data.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]When I use the pvscan –u PV3 is listed as an ‘unknown device’ and the UUId for PV0 is now not correct for the LVM as I have reformatted this drive as part of the Ubuntu setup.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]sudo dd if=/dev/sda2 bs=512 count=255 skip=1 of=/temp.txt yields the following text[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["RESIZEABLE", "READ", "WRITE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]extent_size = 65536[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]max_lv = 0[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]max_pv = 0[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]physical_volumes {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pv0 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "fufRff-6ldT-MB6t-FbrK-bAmF-0FtW-1CEEmB"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]device = "/dev/sda2"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["ALLOCATABLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_start = 384[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_count = 2380}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pv1 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "oh5gWw-0jK1-aXq1-A0Ev-bHFJ-QfRk-iJXG0Q"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]device = "/dev/sdb1"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["ALLOCATABLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_start = 384[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_count = 9538}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pv2 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "lKTd4H-mauQ-jvTv-tuNY-DH03-dO1E-4N0uf0"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]device = "/dev/sdc1"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["ALLOCATABLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_start = 384[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]pe_count = 9538}}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]logical_volumes {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]LogVol00 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "wUJ4IB-6i0W-6CxV-f7sv-BWof-yWoq-3zpENi"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["READ", "WRITE", "VISIBLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment_count = 1[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment1 {start_extent = 0[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]extent_count = 2363[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]type = "striped"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripe_count = 1 [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# linear[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripes = ["pv0", 0]}}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]LogVol01 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "U8tj9z-hI1M-mBzL-VoWw-onAB-3d3s-k0xsVD"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["READ", "WRITE", "VISIBLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment_count = 1[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment1 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]start_extent = 0[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]extent_count = 16[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]type = "striped"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripe_count = 1 [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# linear[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripes = ["pv0", 2363]}}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]LogVol03 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]id = "oYRtwo-H5wp-xL0X-LOfz-V3pR-FGrB-a8kHgR"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]status = ["READ", "WRITE", "VISIBLE"][/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment_count = 2[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment1 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]start_extent = 0[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]extent_count = 9538[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]type = "striped"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripe_count = 1 [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# linear[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripes = ["pv1", 0]}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]segment2 {[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]start_extent = 9538[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]extent_count = 1[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]type = "striped"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripe_count = 1 [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# linear[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]stripes = ["pv0", 2379]}}}}[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# Generated by LVM2: Sun Feb  8 13:48:48 2009[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]contents = "Text Format Volume Group"[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]version = 1[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]description = ""[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]creation_host = "mcinnesonline.com"              [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# Linux mcinnesonline.com 2.6.18-1.2200.fc5 [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]#1 Sat Oct 14 16:59:26 EDT 2006 i686[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]creation_time = 1234100928             [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]# Sun Feb  8 13:48:48 2009[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]Pvscan –u has the following output[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Arial][FONT=Tahoma]            [/FONT][/FONT][FONT=Arial][FONT=Tahoma][SIZE=2]Couldn’t find device with UUID ‘fufRff-6ldT-MB6t-FbrK-bAmF-0FtW-1CEEmB’.[/SIZE][/FONT][/FONT]
[FONT=Tahoma][SIZE=2][FONT=Arial]            Couldn’t find device with UUID ‘lKTd4H-mauQ-jvTv-tuNY-DH03-dO1E-4N0uf0’.[/FONT][/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][FONT=Arial]            Couldn’t find device with UUID ‘fufRff-6ldT-MB6t-FbrK-bAmF-0FtW-1CEEmB’.[/FONT][/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][FONT=Arial]            Couldn’t find device with UUID ‘lKTd4H-mauQ-jvTv-tuNY-DH03-dO1E-4N0uf0’.[/FONT][/SIZE][/FONT]
[FONT=Tahoma][/FONT][FONT=Tahoma][FONT=Arial][SIZE=2]            PV unknown device with device with UUID ‘fufRff-6ldT-MB6t-FbrK-bAmF-0FtW-[/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]           1CEEmB’ VG VolGroup00 lvm2 [74.38GB /0 free][/SIZE][/FONT][/FONT]
[SIZE=2][FONT=Arial][FONT=Tahoma]         [FONT=Arial][SIZE=2]  [/SIZE][/FONT][/FONT][/FONT][/SIZE][FONT=Tahoma][FONT=Arial][SIZE=2]PV /dev/sdb1 with device with UUID ‘oh5gWw-0jK1-aXq1-A0Ev-bHFJ-QfRK-  [/SIZE][/FONT][/FONT]
[FONT=Tahoma][FONT=Arial][SIZE=2]           iJXGC0Q’ VG [/SIZE][/FONT][/FONT][FONT=Arial][SIZE=2][FONT=Tahoma]VolGroup00 lvm2 [298.06GB /0 free][/FONT][/SIZE][/FONT]
[SIZE=2][FONT=Arial][FONT=Tahoma]      [FONT=Arial][SIZE=2]     [/SIZE][/FONT][/FONT][/FONT][/SIZE][FONT=Arial][SIZE=2][FONT=Tahoma]PV unknown device with device with UUID ‘lKTd4H-mauQ-jvTv-tuNY-DH03-dO1E-[/FONT][/SIZE][/FONT]
[FONT=Tahoma][SIZE=2][FONT=Arial]           4N0uf0’ VG VolGroup00 lvm2 [298.06GB /0 free][/FONT][/SIZE][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]As you can imagine my ‘other’ half is none too pleased and any help I can get to ‘connect’ the disk back into a useable array in Ubuntu where I can see the files again would help my marriage no end.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial] [/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]Thanks in advance for your help.[/FONT][/FONT]
[FONT=Tahoma][FONT=Arial]Chrs.[/FONT][/FONT]

---

### Post by stlsaint on 2010-02-28
Yes this sucks. You can try and plug the two drives back into the system and boot to the ubuntu livecd. Open the synapic repository (System>Admin>Synaptic)
and do a search for lvm, you will see lvm2 and kvpm...try those and a few other apps to try and recover the data.

---

### Post by darkod on 2010-02-28
Read here if this can help:
[http://www.linuxjournal.com/article/8874?page=0,0](http://www.linuxjournal.com/article/8874?page=0,0)

especially on page 3 they talk about restore of the LVM. Be careful, I haven't tried this myself, I don't know whether it can mess up the disks further. Just read for a start.

Sorry I can't help more. :(

Also, for you and anyone else reading this, if you had LVM you should have installed ubuntu using the alternate install cd which has RAID/LVM support. Not the standard desktop live cd.

The installation wasn't as you thought, the 80GB and then separately two 320GB disks. If all three disks were set as physical volumes for a single VolumeGroup, the data was spread all over the three disks, not just the two.

And since you overwrote the 80GB disk, not sure how far can you go in retrieving the data. I don't want to put you off, that's just my humble opinion and my understanding of things. Note that I am by no means LVM expert.

---

### Post by themac on 2010-03-01
> **darkod said:**
>  
The installation wasn't as you thought, the 80GB and then separately two 320GB disks. If all three disks were set as physical volumes for a single VolumeGroup, the data was spread all over the three disks, not just the two.
 
And since you overwrote the 80GB disk, not sure how far can you go in retrieving the data. I don't want to put you off, that's just my humble opinion and my understanding of things. Note that I am by no means LVM expert.
 
Thanks Guys
 
A Little nrevous about the thougts from Darkod, but will give things a go.
 
Thanks for the help.

---

