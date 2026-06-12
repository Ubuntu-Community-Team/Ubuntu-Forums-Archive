---
title: "Setting up simple RAID1 with non RAID boot drive?"
date: 2011-10-16
forum: Installation &amp; Upgrades
---

### Post by Rebajas on 2011-10-16
Hiya,

I currently have a machine running 11.10 Ubuntu Server which has 6 HDDs that I'd like to mirror (3 storage disks and 3 mirrors), and 1 SSD for the system files and swap with no mirroring.

**What is the best way to go about this?**

I tried to set up a RAID 1 array on install but that screwed up several times - *I gave up as I just wanted to get to a stage where I had a working machine* :)

My blkid output looks like this:

```

sudo blkid
/dev/sda1: UUID="c90de38d-5c23-4fad-be5d-2f8cb464e1a4" TYPE="ext4" 
/dev/sdb1: UUID="e2457713-0d41-47af-a9a9-9f2cc5056a68" TYPE="ext4" 
/dev/sdc1: UUID="803d0e60-5857-4a26-918d-dc01ce4910fd" TYPE="ext4" 
/dev/sdd1: UUID="120053c9-3b45-42b3-8aff-09c3664bb947" TYPE="ext4" 
/dev/sde1: UUID="53662ab1-2d80-4695-b654-13875fdf59da" TYPE="ext4" 
/dev/sdf1: UUID="9947fc98-5c13-4596-bdea-288dd5fba54d" TYPE="ext4" 
/dev/sdg1: LABEL="Ubuntu System" UUID="249a1906-f92c-40a9-afa0-dd4e9b6ee886" TYPE="ext4" 
/dev/sdg5: UUID="6c46754e-ab04-431f-a575-5d86b8ea7ff4" TYPE="swap"

```

My fstab looks like this:

```

proc                                        /proc   proc   nodev,noexec,nosuid    0   0
UUID=249a1906-f92c-40a9-afa0-dd4e9b6ee886   /       ext4   errors=remount-ro      0   1
UUID=6c46754e-ab04-431f-a575-5d86b8ea7ff4   none    swap    sw                    0   0

```

Can someone advise on what I need to do? Either a good HOWTO that is still current and reflects a setup similar to mine, or by explaining in simple terms what I need to do.


Thanks in advance.


Tony.

---

### Post by Rebajas on 2011-10-19
Okay, so I'm sensing a certain reticence in answering the question above. Would you advise I RAID the whole shebang, boot drive included? Would that make life easier?




Is there anybody out there...?

---

### Post by KneadToKnow on 2011-11-23
I am trying to accomplish this, also. All the instructions I can find (like this thread: [http://ubuntuforums.org/showthread.php?t=803020](http://ubuntuforums.org/showthread.php?t=803020)) are doing one or two things I don't need to do: setting up the RAID as part of the initial installation (I really don't want to start from scratch) and/or booting from the RAID array. I have a drive that's already working fine _to which I am adding_ two drives I want to set up as RAID 1.

I don't get why this is such a hard thing to get recommendations on.

---

### Post by darkod on 2011-11-23
To the OP: What actually went wrong while doing it during the install?

The server is usually very good at installing raid. Most problems I have noticed are from people that try to install the desktop system with RAID but are doing it with the live cd (standard) instead of using the alternate cd as recommended.
But the server already has raid support and should work fine.
Were you trying fakeraid or software raid?

Otherwise, adding a raid array now should be fairly easy using mdadm. Let me google a bit. :)
One big question is are both of you expecting to configure a new raid array with keeping the data on the disks or not? Keeping the data could be a problem. Otherwise it should be fine.

---

### Post by KneadToKnow on 2011-11-23
> **darkod said:**
> One big question is are both of you expecting to configure a new raid array with keeping the data on the disks or not? Keeping the data could be a problem. Otherwise it should be fine.

My disks are blank, so I'm certainly not. :)

---

### Post by darkod on 2011-11-23
OK, first note that I have never tried this, but it goes something like:

Use your favorite partitioning program to create one or more partitions on the disks. Of course it's better to make the disks identical. The partition type should be raid autodetect.
For this example, lets assume you want to set up raid1 mirror of /dev/sda and /dev/sdb with only one single partition on the whole disk (create other partitions at will).

The mdadm command to create the array would be:
sudo mdadm --create /dev/md0 --chunk=4K --level=1 --raid-devices=/dev/sd[ab]1

You might want to use different chunk size, I believe 4K is the norm. The rest of the parameters are self explanatory I think. mdadm man page:
[http://linux.die.net/man/8/mdadm](http://linux.die.net/man/8/mdadm)

That should create the array for you. I'm not sure if it creates a /etc/fstab entry automatically of you will have to manually. Check if it's there.

Also note for future reference that you use --create only the first time. If you want to reassemble existing raid array with data later you use different commands.

After creating it you will probably need to create ext4 or what ever you want partition on /dev/md0.

---

### Post by darkod on 2011-11-23
PS. It seems I have a small error in the --raid-devices parameter.

Further reading material:
[http://en.wikipedia.org/wiki/Mdadm](http://en.wikipedia.org/wiki/Mdadm)
[http://www.cyberciti.biz/faq/linux-creating-software-raid-one-arrays/](http://www.cyberciti.biz/faq/linux-creating-software-raid-one-arrays/)

---

### Post by KneadToKnow on 2011-11-25
Thanks, **darkod**! That looks like it will be a big help!

---

### Post by KneadToKnow on 2011-11-25
Completely by coincidence, I found this today, which is also good info to have handy:

[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Configuring_Software_RAID](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch26_:_Linux_Software_RAID#Configuring_Software_RAID)

---

### Post by Rebajas on 2011-11-27
Hi Guys, thanks for taking an interest an offering help on this - had started to think RAID was something no-one had ever heard of :)

I think between the information you've offered and the links you've posted I may be making progress.

I followed a bunch of instructions, spread across multiple sites determined by the various errors, that have lead me to now having the output of **cat /proc/mdstat as**:

```
Personalities : [raid1] 
md2 : active raid1 sdf1[1] sde1[0]
      1953513382 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  2.1% (42681152/1953513382) finish=230.3min speed=138268K/sec
      
md1 : active raid1 sdd1[1] sdc1[0]
      1953513382 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  2.3% (46349888/1953513382) finish=231.2min speed=137459K/sec
      
md0 : active raid1 sdb1[1] sda1[0]
      1953513382 blocks super 1.2 [2/2] [UU]
      [>....................]  resync =  3.7% (73663680/1953513382) finish=355.6min speed=88086K/sec
```

I guess I will find out later what the hell this is! :) I'm hoping it is some kind of RAID initialisation that I will eventually be able to use - to be honest I'm just glad there are people out there who have heard of RAID :P



Cheers.

---

### Post by cbowman57 on 2011-11-27
I found this late but are there existing problems or did you guys all find solutions?

If you want to make a fresh installation to RAID as someone here already mentioned, used the alternate iso.

If you're trying to migrate an installation don't overlook gnome-disk-utility, if memory serves me correctly you can use that to construct arrays without having to go to the command line (for those that try to avoid such things).

---

### Post by KneadToKnow on 2011-11-28
I'm still getting mine set up, but so far all is well!

---

### Post by KneadToKnow on 2011-11-29
> **KneadToKnow said:**
> I'm still getting mine set up, but so far all is well!

HA! Well, what a difference overnight can make!

I checked on my array this morning to find that, while it appeared to be all set up correctly, it is now degraded, because one of my drives has bad sectors. :(

Well, at least I know about it now before I drop a bunch of data on it (it's going to be my network backup drive).

Thanks again to all the help this thread has been in helping me get the array set up. Once I get the bad drive replaced, I'll be able to repair my array and should be ready to go in no time.

---

