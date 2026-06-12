---
title: "RAID1: Hang at &quot; Verifying DMI Pool Data&quot; / RAID1 suggestions"
date: 2007-09-18
forum: Installation &amp; Upgrades
---

### Post by takeawaydave on 2007-09-18
I recently acquired the following:

1 x startech 4 Port PCI SATA Raid 0.1 card
2x 500 GB SATA Disks

I'd done a little research and was under the impression that this RAID controller would work under Ubuntu. It sort of does but is more of a SATA controller marketed as a RAID controller since they chuck in some Windows drivers that provides RAIDing.

Sort of dissappointed (not that surprised though) that my disks were still being shown to Ubuntu as /dev/sda and /dev/sdb I thought I'd start working with software RAID under Ubuntu. 

I decided to use my existing Ubuntu server (installed only a month ago) on to a 80gB IDE drive and use the RAID to provide some redundancy for my data (website, films, music). 

I took guidance from the [HOWTO: Linux Software Raid using mdadm]("http://ubuntuforums.org/showthread.php?t=408461") and setup my first array. I did the following:

```
sudo apt-get install mdadm
```

then configured partitions on /dev/sda and /dev/sdb as identical linux partitions.

then for /dev/sda1 and /dev/sdb1 created two 1 gb swap partitions:

```
mkswap /dev/sda1
```

followed by 

```
swapon /dev/sda1
```

repeating for /dev/sdb1

These would not undergo software RAID.

I then created /dev/sda2, /dev/sdb2 as identical partitions. 

I created md0 using the following  command:

```
mdadm --create /dev/md0 --level=0 --raid-devices=2 /dev/sda2 /dev/sdb2
```

The example on [URL="http://ubuntuforums.org/showthread.php?t=408461"]HOWTO: Linux Software Raid using mdadm[/URL uses the additional --chunk option. I left this out since I reckoned default chunk size would suffice.

I then ran fdisk -l and could see my 80 gB IDE partitons (root is here amongst others) as well as /dev/sda2, dev/sdb2 and /dev/md0.

I tried to mount /dev/md0 but first needed to create a partiton (again) - not sure of things now I ran fdisk and created /dev/md0p1 as an identical partiton to /dev/sda2 and /dev/sdb2. I then tried to mount /dev/md0 and was told I should reboot.

On reboot I get the folllowing error at boot start (just after raid controller bios bit):

" Verifying DMI Pool Data" 

I have no RAID set on the controller and when I remove the controller card from the MB or the disks from the controller card I boot as per usual.

I am unable to find a way to boot in to Ubuntu with my new SATA disks attached since I have installed mdadm. Currenly run low level format on one of the SATA disks - not that I can see this helping much.

Any suggestions on how to proceed to get where I want to be?

---

### Post by takeawaydave on 2007-09-19
Please anyone with anything useful to contribute? Still stuck.

---

### Post by Pumalite on 2007-09-19
[http://forums.techguy.org/hardware/559281-problem-verifying-dmi-pool.html](http://forums.techguy.org/hardware/559281-problem-verifying-dmi-pool.html)

[http://www.tomshardware.com/forum/188279-30-boot-hangs-verifying-pool-raid-conundrum](http://www.tomshardware.com/forum/188279-30-boot-hangs-verifying-pool-raid-conundrum)

[http://www.soyousa.com/kb/kbdesc.php?id=133](http://www.soyousa.com/kb/kbdesc.php?id=133)

[http://www.msfn.org/board/lofiversion/index.php/t64589.html](http://www.msfn.org/board/lofiversion/index.php/t64589.html)

[http://www.pcguide.com/vb/showthread.php?t=36447](http://www.pcguide.com/vb/showthread.php?t=36447)

[http://icrontic.com/forum/archive/index.php/t-7887.html](http://icrontic.com/forum/archive/index.php/t-7887.html)

---

### Post by takeawaydave on 2007-09-19
Thanks Pumalite - so interesting bits but on the whole a some similar ambigous experiences. 

Turns out that if I unplug my 2nd IDE drive all works ok. I guess the advice of unplugging everything and trying things one step at  a time applies here....

---

### Post by Pumalite on 2007-09-19
There you go!

---

### Post by takeawaydave on 2007-09-19
Moving on how can I verify if RAID1 is working? I am using dmraid and get the following:

```
root@denali:~# dmraid -s
*** Active Set
name   : sil_ahajcfcefgcj
size   : 976771120
stride : 0
type   : mirror
status : ok
subsets: 0
devs   : 2
spares : 0
root@denali:~#

```

which looks good, but:
```


root@denali:~# dmraid -ay
RAID set "sil_ahajcfcefgcj" already active
ERROR: opening "/dev/.static/dev/mapper/sil_ahajcfcefgcj"
```

which don't looki too good.

Also how do I get UUID's of /dev/mapper/sil* devices?

---

### Post by takeawaydave on 2007-09-19
Also get the following when trying to do a speed test:

```

root@denali:/mnt/var2# hdparm -tT /dev/mapper/sil_ahajcfcefgcj1
/dev/mapper/sil_ahajcfcefgcj1:
 Timing cached reads:   580 MB in  2.01 seconds = 289.17 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
 Timing buffered disk reads:  176 MB in  3.01 seconds =  58.39 MB/sec
HDIO_DRIVE_CMD(null) (wait for flush complete) failed: Inappropriate ioctl for device
root@denali:/mnt/var2#

```

Am I barking mad? Trying to make this work?

Would I be wrong shelving this attempt and trying the other raid method? Not sure anymore.

---

### Post by Pumalite on 2007-09-19
Sorry. I'm not a Raid man. I actually think they are more trouble than good. Someone will chime in. Good luck.

---

### Post by takeawaydave on 2007-09-21
Come on! any RAID gurus out there? I know some of you have done this before!
```

root@denali:~# dmraid -ay
RAID set "sil_ahajcfcefgcj" already active
ERROR: opening "/dev/.static/dev/mapper/sil_ahajcfcefgcj"
root@denali:~# ls -l /dev/.static/dev/mapper/
total 0
```

What's the deal with this file /dev/.static/dev/mapper/sil_ahajcfcefgcj where's it meant to come from?

---

### Post by takeawaydave on 2007-09-21
Opened [new thread]("http://ubuntuforums.org/showthread.php?t=556284")

---

