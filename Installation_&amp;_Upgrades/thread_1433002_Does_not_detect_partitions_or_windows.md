---
title: "Does not detect partitions or windows"
date: 2010-03-18
forum: Installation &amp; Upgrades
---

### Post by marouane87 on 2010-03-18
Hi :D

I've installed the last year ubuntu 8.10 on dual boot with winodows XP, but then I had to format the XP so I lost the dual boot and access to ubuntu and I used only XP...
Now, I downloaded Xubuntu 9.10, when I was trying to install it, when preparing the disks a message tell me that the PC has no operating system, then when I choose to manually partion the disk, xubuntu does not read the different partition I'm having and just display the hole disk as free space :o

Any help please?
Thank you in advance.

---

### Post by marouane87 on 2010-03-19
Sorry for the double post, but is there any thing that I can do to fix my problem please.

---

### Post by dandnsmith on 2010-03-19
I'd first try getting a gparted CD downloaded and burned to confirm the view of the HDD partitioning.

BTW does XP still run?

Next up, try a diagnostic CD on the hardware - especially RAM. If there is a problem, it could be in this or the motherboard.

---

### Post by marouane87 on 2010-03-19
Thanks for the answer.
Yes, I'm actually working on XP (so it is renning with nor problem).

I don't know Gparted but it seems to be "is the GNOME partition editor for creating, reorganizing, and deleting disk partitions" but I'm trying to install Xubuntu, is it compatible?
How to make a diagonostic for the RAM? (despite I think it is okey since XP is running with no problem)

I tried something, I booted on ubuntu 7.04, on the desktop, I choose workstation and it shows me all the partitions correctly, but when I try to install it, I have the same problem: having the hole disk to choose even in manually partitionning.

---

### Post by marouane87 on 2010-03-19
I've just tried Gparted, it show me also one entity /dev/hda as not allowed, it is size is about 114Gb (but not the different partition: the C, D and F partition I have)

(I think he did not detect the 5Gb of the old ubuntu installed)

---

### Post by marouane87 on 2010-03-20
I also tried sudo fdisk -l on terminal from the live mode and I think he detected the partitions, I don't inderstand where is the problem, here the result of fdisk:



Disque /dev/sda: 122.9Go , 122942324736 octets
255 têtes, 63 secteurs/piste, 14946 cylindres
Unités=cylindres de 16065*512=8225280 octets
identifiant du disque 0xe292e292

Périphérique Amorce Début Fin blocs ID Système
/dev/sda1 * 1 2550 20482843+ 7 HPFS/NTFS
/dev/sda2 2551 14945 9952837+ f W95 Etendu (LBA)
/dev/sda3 3266 6530 26226081 b W95 FAT32
/dev/sda5 6531 14945 67593456 7 HPFS/NTFS

---

### Post by dandnsmith on 2010-03-20
OK those show the HDD as partitioned with:
sda1  primary partition - likely to be the Windows system C:
sda2  extended partition occupying the rest of the HDD
   and serving as the container for:
sda3  a FAT logical partition for Windows D:
sda5  an NTFS logical partition for Windows F:

I'm not sure how best to suggest you proceed - personally, I'd backup anything desired, and repartition and format the HDD, aiming to get an uncommitted primary partition for Ubuntu (from which you could boot. This is because my personal experience (somewhat out-of-date now) suggests that you couldn't easily organise booting with you existing partition setup.

addition: I've just noticed, on reviewing your post, that there is a gap between before sda3, as if a logical partition had been removed. Either the partition tool you used or fdisk could use that space - but it may not help to solve the booting problem.

HTH

---

### Post by marouane87 on 2010-03-20
Thank you.

I'm a little bit confused, I don't have an F partiton: just C (20Gb), D (69Gb) and E (25Gb) :o

I haven't use any partition tool other than the CD of Windows XP

Is it possible to install Xubuntu on the F partition? (I could have done that but as I said in my first post, Xubuntu don't show me the partitions to choose from, juste the hole disk: 114Gb as free space(I don't know where the other 5Gb are gone, may be these are the F partition))


I'm gonna have a little trouble backing up since I have at least 100Gb of important files and no extern HD :frown:

I hope there is another solution :-|

---

### Post by dandnsmith on 2010-03-20
Sorry, since you said 
> I've just tried Gparted, it show me also one entity /dev/hda as not allowed, it is size is about 114Gb (but not the different partition: the C, D and F partition I have)

and then > I'm a little bit confused, I don't have an F partiton: just C (20Gb), D (69Gb) and E (25Gb)

I, too am a little confused.

There is a missing tranch from cylinder 2551 to cylinder 3265 according to your posting of the fdisk listing.

I'd revise my interpretation of the Windows disks to:

C: on sda1
D: on sda5
E: on sda3

assuming you quoted those sizes correctly.

I cannot imagine why the xubuntu tool wouldn't show all the partitions - what sort of HDD (IDE/SATA), and which xubuntu release are we talking about?

---

### Post by marouane87 on 2010-03-20
Ok, first let's make things a little clear ;)

In windows XP, in my workstation, I see 3 partitions: C 20Go, D 64.4 Go and E 24.9Go

When I used Gparted, it shows me just the hole disk: /dev/sda (wich is the same result given by xubuntu 9.10 installer and ubuntu 7.04)

Then, I used Xubuntu 9.10 (wich I want to install) in live mode, and I used fdisk command (on terminal) and it gave me the table above (with all partitions: sda1, sda2 ect...) 

I agree that (refering to size given): 
C: on sda1
D: on sda5
E: on sda3


My HDD is Maxtor 6Y120L0 (I think it is IDE and not sata since it is too old, since 2004 and even above :roll: )
I'm trying to install Xubuntu 9.10 O:)

---

### Post by srs5694 on 2010-03-20
I've been seeing a lot of posts lately with similar reports: GParted doesn't show partitions that are shown by fdisk and other tools. This sounds to me like a bug in libparted (the partitioning library upon which GParted and many other Linux partitioning tools rely). It's been a while since I used the Ubuntu installer, so I don't know how easy it is to work around such problems; however, if you can use fdisk or some other tool to create your partitions, and then format them with mkfs, you may be able to install without using a libparted-based partitioning tool.

---

### Post by marouane87 on 2010-03-20
Thank you for the answer.

Well I think it is impossible for me to do such a thing cause I'm still a noob, but it may be a good idea to use fdisk to create the ext4 and swap partition using the missing tranch from cylinder 2551 to cylinder 3265 without risking to lose may data or other partitions and then install wubuntu into those new partitions.

But I can't do it, as I said I'm a noob ;)

---

### Post by lemming465 on 2010-03-20
Ubuntu variants from the 9.10 series seem to have more trouble than usual with legacy BIOS/software/fake RAID, for one thing.  If you boot a live CD, does opening a terminal window and trying *sudo aptitude remove dmraid* before launching the installer ("ubiquity") help the partitioning step see stuff?

---

### Post by marouane87 on 2010-03-21
When I write "sudo aptitude remove dmraid" and then launch the installer, after choosing the time zone, it shows me a message of error unexpected and then the installer freeze, I close and I launched a second time, all goes OK but the problem of partitions still remains :|

---

### Post by lemming465 on 2010-03-21
Is there any chance you could try an Xubuntu Lucid 10.04 beta 1 live CD?  It would be interesting to know if that did any better.

---

### Post by marouane87 on 2010-03-23
Ok, thank you, I'm downloading it and I hope it is going to work, I'll let you know ;)

---

### Post by marouane87 on 2010-03-25
The same problem with 10.04 beta...
I start to doubt that there is something wrong with my HDD despite that windows if fonctionnal and all partitions are fine under windows...
Is there any software that can scan the HDD and correct the errors if they exist please?
Thank you.

---

### Post by Cowpoke on 2010-04-02
I am having the same problem.  I cloned my *old* xubuntu drive to a new hard disk -- successfully; as part of the exercise, I am supposed to extend the partitioning to use up the whole of the new hard drive.  Interestingly, neither the old nor the new drive are being propertly detected, though they do show up correctly when the ***fdisk -l*** command is issued.

Using gparted, I tried to *create partition* on the new drive after I duplicated the old drive.  Predictably, I had to re-dup the old onto the new again.

Are there other partition managers that we might try?  Is anyone else experiencing this same phenomenon?

Thanks in advance.

Ride on...
Cowpoke

---

### Post by srs5694 on 2010-04-02
> **Cowpoke said:**
> I am having the same problem.  I cloned my *old* xubuntu drive to a new hard disk -- successfully; as part of the exercise, I am supposed to extend the partitioning to use up the whole of the new hard drive.  Interestingly, neither the old nor the new drive are being propertly detected, though they do show up correctly when the ***fdisk -l*** command is issued.

Using gparted, I tried to *create partition* on the new drive after I duplicated the old drive.  Predictably, I had to re-dup the old onto the new again.

Are there other partition managers that we might try?  Is anyone else experiencing this same phenomenon?

AFAIK, there are only three families of partitioning tools in Linux, at least for the partition types that are common on x86 and x86-64 systems:


[list]
[*]libparted tools -- the libparted library powers the text-based GNU Parted, the GUI GParted, and a few others. libparted supports Master Boot Record (MBR), GUID Partition Table (GPT), and a few other partition types. It also supports creating or modifying filesystems as part of partition creation/modification, which makes it convenient, especially for new users who aren't familiar with tools such as mkfs. It's the only family that includes GUI programs.
[*]The fdisk family -- fdisk, cfdisk, and sfdisk are text-mode tools for MBR and a few other exotic partition table types, but they don't support GPT. These tools also don't support filesystem manipulation, so you must use separate programs (mkfs, resize2fs, etc.) to create or resize filesystems after you create or modify partitions.
[*]GPT fdisk -- This package includes the gdisk and sgdisk programs, which are designed to fill the role of the fdisk family but for GPT disks. Like fdisk, GPT fdisk doesn't support filesystem modifications and has no GUI mode.
[/list]


Since you say "fdisk -l" produced a display that shows your correct partitions, it's apparent that fdisk (or one of its variants) is the best tool to use on your disk. (If you were to use gdisk on it, the disk would be converted to GPT form, which might be OK for a Linux-only system but is definitely not good if you multi-boot with Windows. It's conceivable that libparted would work better on the converted disk, but you'd need to reinstall your boot loader.) As I posted earlier, I've seen a number of posts recently from people who are having problems with libparted-based tools. I suspect there's a bug in some versions that's causing problems, but I don't know this for a fact, nor do I have specifics. You could try a more recent version of GNU Parted, but you'll need to either track down a Debian package or install from source. GNU Parted (including libparted) is hosted [here,](http://www.gnu.org/software/parted/index.shtml) and GParted's home page is [here.](http://gparted.sourceforge.net/)

---

### Post by Cowpoke on 2010-04-02
Thank you very much for your response.  Impatient as I am, I poked around to see what I might be missing.  Your suggestion is precisely right.

Issuing the following command
```
sudo fdisk -l
```shows the correct partitions -- and something else.

The very first line shows a warning condition:

> Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)

...and shortly thereafter:
>    Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14569   117025461   83  Linux
/dev/sda2           14570       14946     3028252+   5  Extended

From start to finish now, resolve the problem as follows.
Issue the fdisk command with the device you need to fix:
```
sudo fdisk /dev/sda
```

Now change the partition's System ID -- use the same ID type displayed (albeit compressed) above, namely 83.

```
Command (m for help): t
Partition number (1-5): 1
Hex code (type L to list codes): 83
Command (m for help): w
```

...that's it!!  :D

---

### Post by srs5694 on 2010-04-02
> **Cowpoke said:**
> Issuing the following command
```
sudo fdisk -l
```shows the correct partitions -- and something else.

The very first line shows a warning condition:

```
Warning: invalid flag 0x0000 of partition table 5 will be corrected by w(rite)
```

A-ha! It actually wasn't necessary for you to re-enter the partition type code, but doing so did no harm. The problem is that a value that's supposed to be present to identify logical partitions was damaged. This is something you can't change manually; fdisk corrected the problem automatically when you saved the partition table. No doubt GParted was getting confused by its absence. Perhaps this is what's happening to other people, too.

---

### Post by souptafied on 2010-04-10
[COLOR=Red][B][SIZE=5]WARNING!
[/SIZE][/B][SIZE=5]**[SIZE=3][COLOR=Black]Be[/COLOR][/SIZE]** [B][SIZE=3][COLOR=Black]careful if following this thread!
I followed it and rendered both my linux and windows partitions useless.
[/COLOR][/SIZE][/B][SIZE=3][COLOR=Black]Luckily it was on an older box and I am only using xubu on it anyway! It might be nice if marouane87 could edit the beggining to warn people.[/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][B][SIZE=5]
[/SIZE][/B][/COLOR]

---

### Post by marouane87 on 2010-04-24
> **souptafied said:**
> [COLOR=Red][B][SIZE=5]WARNING!
[/SIZE][/B][SIZE=5]**[SIZE=3][COLOR=Black]Be[/COLOR][/SIZE]** [B][SIZE=3][COLOR=Black]careful if following this thread!
I followed it and rendered both my linux and windows partitions useless.
[/COLOR][/SIZE][/B][SIZE=3][COLOR=Black]Luckily it was on an older box and I am only using xubu on it anyway! It might be nice if marouane87 could edit the beggining to warn people.[/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][B][SIZE=5]
[/SIZE][/B][/COLOR]

I could not fix my problem, on the other hand, I have not encounter any data loss, please tell me wish tutoriel caused the damage to make the warning on the first message, thank you.

---

### Post by Cowpoke on 2010-04-24
> **souptafied said:**
> [COLOR=Red][B][SIZE=5]WARNING!
[/SIZE][/B][SIZE=5]**[SIZE=3][COLOR=Black]Be[/COLOR][/SIZE]** [B][SIZE=3][COLOR=Black]careful if following this thread!
I followed it and rendered both my linux and windows partitions useless.
[/COLOR][/SIZE][/B][SIZE=3][COLOR=Black]Luckily it was on an older box and I am only using xubu on it anyway! It might be nice if marouane87 could edit the beggining to warn people.[/COLOR][/SIZE][/SIZE][/COLOR][COLOR=Red][B][SIZE=5]
[/SIZE][/B][/COLOR]

...most unfortunate.

It was mentioned that the method is of high risk when not running in a purely Unix environment.

srs5694 mentioned:
> Since you say "fdisk -l" produced a display that shows your correct partitions, it's apparent that fdisk (or one of its variants) is the best tool to use on **_your_** disk. (If you were to use gdisk on it, the disk would be converted to GPT form, *which might be OK for a Linux-only system but [COLOR=Red]_is definitely not good if you multi-boot with Windows[/COLOR]_*. It's conceivable...

My emphasis added.

The "*your*" which I bolded and underlined was specifically directed at me; thank you for your assistance srs5694, worked like a charm.

Still, my apologies for any role I may have played in bricking your computer; remember this is unpaid advice which you follow at your own risk. ...your mileage may vary...

...ride on...

---

