---
title: "Win-7 Boot problems post-Ubuntu installation"
date: 2012-01-05
forum: Installation &amp; Upgrades
---

### Post by MadMaxe on 2012-01-05
[SIZE=3]I have a Hp-pavilion dv6 with Win-7 and a 500GB Hd split into  3 drives -C:, a System tools and something else. I shrank 100Gb on the  C: and used that to install Ubuntu. Meaning i literally shrank by a  100Gb, formatted it and moved into the installation of Ubuntu - i didn't  restart a couple of times just so Windows could get used to the new  drive. During the installation, I had Ubuntu "Delete" the new drive,  format to ext4 and Install Ubuntu. Now I can boot Ubuntu but I simply  cannot boot into Windows. System-repair does not even find Win-7. fixmbr  works but fixboot throws up an error.

[/SIZE]  [SIZE=3]GParted shows this [/SIZE]
  [SIZE=3][http://i.stack.imgur.com/QwQv4.png](http://i.stack.imgur.com/QwQv4.png)[/SIZE]
[SIZE=3][URL="http://i.stack.imgur.com/QwQv4.png"]
[/URL][/SIZE]
  [SIZE=3]Boot-repair link is this [http://paste.ubuntu.com/794048/](http://paste.ubuntu.com/794048/)[/SIZE]
  [SIZE=3]
[/SIZE]
[SIZE=3]Please help![/SIZE]

---

### Post by tlcstat on 2012-01-05
Greetings,
Everytime I installed Win7 to dual boot with Ubuntu I would get a blue screen with the windows partition. Solution, I've been using Ubuntu for the last year. If I need Windows for anything I run it in a VM. I have a small 700meg version of Win7 that i use for the VM. I use it for updating my TomTom, Turbotax and a little bit of customer support from the old days. Sorry that I don't have a solution for your problem. 
tlcstat

---

### Post by ottosykora on 2012-01-06
Q: how did you shrink the windows partition?
with windows tool or gparted?

If done with gparted, there is some chance of partition being damaged.
I managed to manipulate even so called 'vista type' of partition (w7 uses that as well) with gparted without problem, but often it is reported that such operation ends up problem for windows itself.


Hmm, but from the bootscript output I personally do not see a problem at the right moment now, seems to poit all to the right direction.
What exactly do you observe when choosing windows from the boot menu?

However somehow I am not sure where your grub is searching for rest of its files, are you sure you still can boot to linux?



What errors do you get when trying to restore windows?




Q2 : Do you have any idea what is the small partition at beginning? Some bios extension?
Was it there always?

---

### Post by tlcstat on 2012-01-06
Greetings,
I started with a new primary partition on my 500Gb HD and installed a fully functional Windows 7, and rebooted successfully several times. I then installed my Ubuntu 11.10. putting grub in the primary Windows partition MBR. On reboot I got a Windows dreaded blue screen and the Ubuntu boots fine. This has happened to me using Win7 as well as XP. Since I was weary of Windows and its vulnerabilities anyway I just converted the Windows partition into a Truecrypt partition and run Ubuntu only. But since I do need a Windows installation for a few things such as my TomTom, I use Virtualbox for Windows and that does just fine. Since I'm kind of sold on Linux in general and Ubuntu/Unity specifically I don't intend to experiment any further with the Windows blue screen since that is typical of Windows under normal circumstances. I made a living from it!
tlcstat

---

### Post by darkod on 2012-01-06
```

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes Sector size (logical/physical): 512 bytes / 512 bytes
Partition  Boot  Start Sector    End Sector  # of Sectors  Id System
/dev/sda1                  63         2,047         1,985  42 SFS
/dev/sda2    *          2,048       409,599       407,552  42 SFS
/dev/sda3             409,600   726,452,223   726,042,624  42 SFS
/dev/sda4         726,452,224   976,771,071   250,318,848  83 Linux[FONT=Verdana]
[/FONT]
```[FONT=Verdana]

[/FONT]Your disk is dynamic, not basic. The SFS means dynamic. It was either dynamic all the time,
or you forced it creating more than 4 partitions and it switches into dynamic.

Ubuntu doesn't install on dynamic, that's your problem.
I'm not sure if you can convert it to basic without losing data, I don't work with dynamic disks.
That is a MS format, try googling around or some MS forums.

---

### Post by ottosykora on 2012-01-06
@darkod

hmmm, yes you are right again, missed that one..   ;-)

however, true is that the 1-3 are SFS, but the sda4 is 83 type and linux is installed in it.
Is the grub then trying to find the win loader and can not find it because it is sitting in the SFS?

note: yes it is possible to convert to 'basic' with windows tools without loosing data,  thought last time I did it, somehow it refused to do it from the gui, I had to use parted from the CLI in windows, no idea why.

somehow also not clear to me was what are those two question marks here:

>the same hard drive for core.img. core.img is at this location and looks 
    for ?? on this drive.<

---

### Post by Mark Phelps on 2012-01-07
I think you may already have had the maximum of 4 partitions in place when you shrank Win7 and created the new partition for Ubuntu.  That might force the conversion to Dynamic Disks.

Here's an MS article on the use of Diskpart to conver disks:

[http://support.microsoft.com/kb/300415]("http://support.microsoft.com/kb/300415")

---

### Post by darkod on 2012-01-07
> **Mark Phelps said:**
> I think you may already have had the maximum of 4 partitions in place when you shrank Win7 and created the new partition for Ubuntu.  That might force the conversion to Dynamic Disks.

Here's an MS article on the use of Diskpart to conver disks:

[http://support.microsoft.com/kb/300415](http://support.microsoft.com/kb/300415)

Yeah, but the basic problem is that you can't keep the data. Not as far as I know. That article says the same:
**convert basic [noerr]**

Use the **convert basic** command to change an empty dynamic disk to basic. 

The emphasis is on EMPTY. I believe if it's empty Disk Management allows you to do it too. But I might be mistaken about this.

The problem is if you have nowhere to move the data.

---

### Post by MadMaxe on 2012-01-08
Sorry for the late response folks I never got any notification that people have even responded to my query.

@ottosykora: I used Windows to create the extra partition. I only had 3 partitions before so I had no problem creating the 4th partition.

When choosing Windows, it starts to boot - the 4 windows color start to come together and then I get a fatal error after which it says I need to use the installation disk to repair and then re-start.

(see here [http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-7-ubuntu.html) while i followed a siimlar process and got a similar error at the "Boot Windows" time, the "Repair" does not pick "Win-7" as on OS that can be fixed and therefore does not fix anything)

Yep, I can boot into Linux no problems. It's how i'm posting here :)

@darkod - there are only 4 partitions on my drive. There were 3 before and I created a 4th for ubuntu. What you see in the snapshot is what I have. I knew about the 4-partition limitation so I didn't try to create any extra beyond what was needed.

---

### Post by darkod on 2012-01-09
> **MadMaxe said:**
> 
@darkod - there are only 4 partitions on my drive. There were 3 before and I created a 4th for ubuntu. What you see in the snapshot is what I have. I knew about the 4-partition limitation so I didn't try to create any extra beyond what was needed.

That still doesn't change the fact that the disk seem to be dynamic under windows. Regardless how it got that way. There had been even cases where manufacturers ship computers with windows preinstalled on dynamic disk.

Unfortunately I have no tutorial for converting to basic, although there was an exactly same case on this firum recently and the poster said he was able to convert back to basic without losing the data.

---

### Post by Mark Phelps on 2012-01-09
darkod:  Sorry, I missed that detail ...

MadMaxe: The link below is from the other post:

[http://www.petri.co.il/forums/showthread.php?t=3844]("http://www.petri.co.il/forums/showthread.php?t=3844")

Post #3 in the link has the details -- but the SW is from a Windows 2000 disk -- good luck in finding one of those today,  It was probably a lot easier when that post was originally written.

---

### Post by MadMaxe on 2012-01-09
> **Mark Phelps said:**
> darkod:  Sorry, I missed that detail ...

MadMaxe: The link below is from the other post:

[http://www.petri.co.il/forums/showthread.php?t=3844](http://www.petri.co.il/forums/showthread.php?t=3844)

Post #3 in the link has the details -- but the SW is from a Windows 2000 disk -- good luck in finding one of those today,  It was probably a lot easier when that post was originally written.

Thank you for the link Mark!

---

