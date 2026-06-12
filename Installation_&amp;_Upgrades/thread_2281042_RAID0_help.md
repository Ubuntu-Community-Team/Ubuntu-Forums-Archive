---
title: "RAID0 help"
date: 2015-06-04
forum: Installation &amp; Upgrades
---

### Post by jvanleuven on 2015-06-04
I bought a Aorus X3 and put in two samsung 850 m.2 drives (500gb each). 

I was in a hurry to get my computer set up (replacing dropped laptop), so I did a default Ubuntu 14.04 install.

The two drives are mounted separately, so I didn't set up the RAID correctly? The RAID is enabled in the BIOS.

Now, I've spent a couple of weeks getting everything set up, is there a way to enable the RAID w/o reinstalling the OS? One drive is just ext4. The other has EFI boot, ext4, swap, and free space partitions. 

Thanks, I really appreciate the help.

---

### Post by TheFu on 2015-06-04
No. But you can backup your settings and a list of installed programs, then put those back when you are done with the fresh install.

BTW, using "FakeRAID" is almost never a good idea. I really mean NEVER.  It has all the problems that HW-RAID has and the performance of SW-RAID, but without the same flexibility of SW-RAID.  Why bother? I'd use SW-RAID (and I do).

BTW, RAID0?  Don't like your data much, I take it.  OTOH, it is your system and if you have perfect, automatic, versioned, daily backups, then go for it.

I'm confused. Why do you want RAID0? Are you a 4K format video editor?

---

### Post by jvanleuven on 2015-06-04
Thanks. I'll contemplate the effort/reward tradeoff. Getting the nvidia drivers working with prime-select was kind of a pain.  

No, not a video editor. I work with a lot of DNA sequence data (big txt files ~5-20Gb each). I think the increased read/write speed may help.

In BIOS, RAID is selected. Should I disable this, then use a software RAID controller?

---

### Post by TheFu on 2015-06-04
FakeRAID (in the BIOS) is worthless, IMHO. I cannot see any good reason to use it - EVER. Without the fakeRAID drivers, enabled or not, it doesn't matter (probably). I would disable it, if only to save power.

Well - for large data like DNA sequences, I could be convinced to setup a 50G RAID0 stripe, provided it is only used for temporary working storage, not left overnight AND backups are 100% working first. RAID0 with 2 disks doubles the likelihood that a disk failure will screw you.  On a laptop, don't think the performance will justify RAID0 (disk controllers just aren't that good).

Hopefully other people will chime in with their opinions too.

---

### Post by jvanleuven on 2015-06-04
Thanks. I really appreciate the input. The EVO850 m.2 drives are already fast. It is pretty amazing, ran some perl scripts last night, but the laptop still ran seamlessly with 4 threads pinned out and 16Gb ram full (using swap).

Still, it would be nice to have one big drive (instead keeping stuff in two locations). I'm not too worried about the 2X likelihood of failure. I backup frequently. My understanding is that the speed increase is substantial and do ssd's fail that often anyway?

Does the RAID increase disk errors or something?

---

### Post by tgalati4 on 2015-06-04
If you are setting up RAID0 for SSD's then it's possible that you won't get 2X the speed up you get from slow, spinning hard drives.  So I would do some testing with your workload.  That takes time.  I agree with TheFu, fakeRAID is generally poor, but it is easier to manage and may give some hardware benefits that are not available to software RAID, so only testing with your workload will determine that.

Handling big text files implies large data paths.  You might be better off getting server hardware and lots of RAM, because that will blow the doors off of a gaming laptop for this type workload.

---

### Post by TheFu on 2015-06-04
A quality RAID card - like from LSI - can do amazing things with data throughput, especially when connected to a server backplane.

My goal in life is to never experience a HDD failure.  I want to swap in new disks 1 day before any HDD fails. Alas, I cannot predict when any specific drive will fail. Nobody can.  If they are in use at the time of failure, the specified MTBF means absolutely squat.  If you have solid backups, go for it.  **mdadm** is the tool  for SW-RAID on Linux. Or if you just want to merge the storage into a single logical directory/partition, you don't need RAID for that - **lvm** can do it (at the cost of complexity), as can a few file systems like unionfs (which I've never used). Definitely read up on the PROs/CONs for any of these solutions.  You could just use symbolic links too.  There are lots of answers that don't use RAID. Whether you need to reload the OS or not depends on how you layout the OS vs the data.

I've heard that SSDs don't fail as quickly as spinning disks. Don't know. All disks fail. They usually wait until a critical moment to do so.

Only you can select which option makes the most sense for your needs.

---

### Post by jvanleuven on 2015-06-04
Alright. Thanks everyone, I think that I'll give it a try.

 Is there any way to clone my current Ubuntu install and put in onto the raid after I set it up? I can easily transfer all the data files. It's all the software, libraries, passwords, etc. that take me time to set up.

-James

---

### Post by TheFu on 2015-06-04
Use normal backup and restore methods, just be certain you don't override any of the new settings for storage.  Moving between systems (which is really what you are doing), is pretty easy.
[http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview](http://blog.jdpfu.com/2013/12/11/how-to-migrate-debian-ubuntu-systems-and-data-overview) explains some options. I think there is an easier method now, assuming you aren't running any servers with data. I'm old and set in my ways, so having a list of installed packages, all the system and personal settings and the data  is how I do it.

---

### Post by jvanleuven on 2015-06-05
I'll need to do a fresh OS install to get the RAID0 set up correct. So, I cannot use something like CloneZilla, right? 

Should probably just copy ~/.* folders and data files to the new install?

---

### Post by jvanleuven on 2015-06-10
Took me a few days to get it all sorted out. After trying a few things, here is what worked;

1. set drives to ahci in bios (not using Intel fake raid)
2. boot into linux with live usb (i was using uefi-biolinux)
3. format both hard drives the same with gparted (gpt table)
          200 mb fat32 boot flag
          10 gb raid
          ~450 gb raid
4. boot to ubuntu server 14.04 (also must have ubuntu server iso file on another usb. I had to mount the iso to /cdrom)
5. manually set up partitions 
6. build raid 0 with the 10gb and 450gb partitions
7. format one of the 200mb partitions to EFI boot
8. format the newly created raids for swap (20gb) and ext4 (~900gb mounted to /)
9. install ubuntu server
10. install ubuntu desktop

This worked for me. Aorus x3 plus with 2x samsung evo850 m.2 drives.
Can verify ~1gb/s data transfer speed on the raid.
Only mistake seems to be a leftover and useless 200mb fat32 partition. I can live with that.

Thanks for the help.

---

### Post by tgalati4 on 2015-06-11
You can put freedos on the fat32 partition and use that for firmware updates in the future.  What was the published, single-drive transfer speed?  Are you getting 2X transfer speed with your configuration?

---

### Post by jvanleuven on 2015-06-15
Huh, thanks for that suggestion. Looks like it might be a good idea.

Published speed for Samsung evo850 is ~500Mb/s. I've been processing data on the drive and see ~1Gb/s copy speed (large uncompressed text files). 

So yes. Looks like about double the published speeds.

---

