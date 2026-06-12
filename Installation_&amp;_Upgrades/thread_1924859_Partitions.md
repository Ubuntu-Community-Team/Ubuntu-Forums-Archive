---
title: "Partitions"
date: 2012-02-13
forum: Installation &amp; Upgrades
---

### Post by Fightback on 2012-02-13
Hey Guys

I just bought a SSD. I also have a HD, and I'd like to install Windows 7 on the SSD, and partition the HD into two parts (200GB/300GB). On the 200GB part, I'd like to isntall Ubuntu.

I was wondering whether it'd be possible to make the third partition (the 300GB on the HD) available to both OS's?

Thanks!

---

### Post by TheFu on 2012-02-13
Yes, it is.  Just format any partition you want to share as NTFS.
Do not expect to install any Linux programs on this partition - it doesn't have the same file permissions that Linux uses.

Might I recommend a smaller Linux partition for the OS/App say 10 or 20GB (ext4), then a 10GB partition for your HOME (ext4), 1-2G for swap, and then a data-only partition (NTFS) with the rest of the storage?  You probably want to make all of these be **logical partitions**, not primary.  You'll thank me later.

Having your HOME partition separate will make OS upgrades easier since files your home won't be touched.

---

### Post by Fightback on 2012-02-13
Thank you for your help.

I understand why you separate the OS from the HOME, but why do you suggest an ext4 partition for my HOME and another one for data? In other words: would it be a very bad idea to make to HOME partition NTFS and big to use it for data storage, accesible by both OS's?

---

### Post by darkod on 2012-02-13
I am not sure linux would accept a ntfs /home partition.
Plus, you don't want windows touching your /home partition.

Go with separate ext4 /home, and ntfs data partition. Both ideas are great.

---

### Post by Fightback on 2012-02-13
Thanks to you too, Darkod.

Okay, so I understand that now. The next step will be the execution =)

I haven't yet recieved the SSD yet, but I'm guessing it is relatively straightforward to install it? [LIST=1]
[*]Install the SSD on it's 2.5' to 3.5' mount.
[*]Open PC, connect SATA, connect power.
[*]Close PC
[/LIST]
That's it?

Or is there anything else I need to consider?

Given I'm able to install the SSD and boot up my PC, will it just go into the Windows (7 64-bit) I have on the HD?
And if so, do I just install Win7 on the SSD and end up with 2 windows 7 versions?
And if so again, what would be the smart way to transfer the (quite big amount of) data on the HD that I want to my NAS, so that I can then format my HD and repartition it?
Furthermore, I have currently installed my Ubuntu under wubi, should I leave it as such and install wubi again on the win 7 of the SSD (I'd prefer any other way, since I don't really like the 32GB restriction...)? Or is there another way?

Now that's a lot of questions^^ I'm sorry if they seem very basic to you, but this is the first HD/SSD I install myself^^
I'm alright with software, but a true beginner in terms of hardware^^

---

### Post by darkod on 2012-02-13
The physical install of the SSD is how you described it. Nothing more to consider.

But for the win7 install, I would recommend to disconnect the hdd with win7 (one cable is enough, the sata or power cable).
If you try to install on the ssd and you have the hdd with win7 present, it will add the boot files to the first install. Then when you format the hdd your new win7 won't boot.

Disconnect it, and let it install like you only have the ssd.

After that, you can connect the hdd but in BIOS make the ssd first choice to boot, so it will boot your new win7. Copy what ever you want, where ever you want it.

After that you can reformat the hdd and do what ever you like with it.

About the ubuntu install. What we discussed about separate /home, and ntfs data partition, is usually used in proper dual boot install. Not with wubi. And wubi is not meant to be a long term install anyway. Updates can easily break it.

I recommend installing the dual boot, not wubi. For this, either plan to leave small part of the ssd for ubuntu, or after you finish copying the data from the hdd install ubuntu on it on a small partition, and use the rest as ntfs data partition.

---

### Post by haqking on 2012-02-13
+1 to everything above.

one more thing though, make sure AHCI is enabled in the BIOS if not already or done by default.

---

### Post by Fightback on 2012-02-13
Thanks guys.

@haqking I shall.

@darkod
Alright then, I think I have understood everything =).

I'm not sure yet whether I want to install Ubuntu on the SSD or on the HDD... What would you do?

---

### Post by darkod on 2012-02-13
I would install on the SSD. You never mentioned its capacity, and how much you need for win7 + programs. If you can spare at least 10GB on the SSD, you can install with a 10GB root partition on the SSD, 10-20GB /home partition on the HDD, and swap on the HDD too.

If you keep all your big files on the shared data partition, you don't need much for ubuntu, both the root and /home partitions can be small.

The final choice is up to you. Even if you decide to put ubuntu on the HDD it will work good.

---

### Post by Fightback on 2012-02-13
The SSD is 128 GB (that's definitively enough, right?)

I think Win7 + programs will be about 60GB (tops), so enough space for Ubuntu.

Probably going to install it on the SSD.

So the basic procedure will be as follows:
[LIST=1]
[*]Install the SSD (in terms of hardware)
[*]Partition the SSD (90GB Windows; 38GB Ubuntu (or so)). Which program would you recommend? GParted on the Ubuntu-Live-CD?
[*]Install Windows on the SSD Windows Partition
[*]Backup Windows files I want to the NAS
[*]Wipe HDD. What program is suitable? (On purpose not backing up Ubuntu, there really isn't much on there I still want) 
[*]Partition HDD (20GB /home, 2GB Swap, 478GB Storage) (There was something about LPARs, how would I achieve that?)
[*]Copy files back to HD
[*]Tweaking libraries etc (suggested [COLOR="SandyBrown"][here]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")[/COLOR])
[*]Install Ubuntu (via Live-CD)
[/LIST]
Done.

I've been skimming through that guide I linked above, when I stumbled across this quote, which made me wonder whether I need a separate Swap partition? I have 8GB of RAM and I'm not often running multiple VMs parallely, so I though I maybe could follow this advise: 
> [FONT="Arial Black"]**[SIZE="3"]Adding swap to Ubuntu[/SIZE]**[/FONT]

"Swap" memory is a section of the hard drive that your system's memory spills over into when it gets full and busy. Until recently, I'd been creating a whole separate partition for it. Recently, though, I've found that swap isn't always necessary on systems with a large amount of memory, and that swap can simply be a file tucked away on your hard drive somewhere.

Follow the Ubuntu help wiki's instructions for adding more swap, but consider changing the location they suggest putting the swap file&#8212;/mnt/swap/ for the place your Storage is held&#8212;/media/Storage, in my case.
Thanks for your help and fast replies =)

---

### Post by Fightback on 2012-02-14
That didn't really answer my question. =)
Here it is again^^

> **Fightback said:**
> The SSD is 128 GB (that's definitively enough, right?)

I think Win7 + programs will be about 60GB (tops), so enough space for Ubuntu.

Probably going to install it on the SSD.

So the basic procedure will be as follows:
[LIST=1]
[*]Install the SSD (in terms of hardware)
[*]Partition the SSD (90GB Windows; 38GB Ubuntu (or so)). Which program would you recommend? GParted on the Ubuntu-Live-CD?
[*]Install Windows on the SSD Windows Partition
[*]Backup Windows files I want to the NAS
[*]Wipe HDD. What program is suitable? (On purpose not backing up Ubuntu, there really isn't much on there I still want) 
[*]Partition HDD (20GB /home, 2GB Swap, 478GB Storage) (There was something about LPARs, how would I achieve that?)
[*]Copy files back to HD
[*]Tweaking libraries etc (suggested [COLOR="SandyBrown"][here]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony")[/COLOR])
[*]Install Ubuntu (via Live-CD)
[/LIST]
Done.

I've been skimming through that guide I linked above, when I stumbled across this quote, which made me wonder whether I need a separate Swap partition? I have 8GB of RAM and I'm not often running multiple VMs parallely, so I though I maybe could follow this advise: 

[INDENT]"[COLOR="Black"][SIZE="3"][FONT="Arial Black"]Adding swap to Ubuntu[/FONT][/SIZE][/COLOR]

"Swap" memory is a section of the hard drive that your system's memory spills over into when it gets full and busy. Until recently, I'd been creating a whole separate partition for it. Recently, though, I've found that swap isn't always necessary on systems with a large amount of memory, and that swap can simply be a file tucked away on your hard drive somewhere.

Follow the Ubuntu help wiki's instructions for adding more swap, but consider changing the location they suggest putting the swap file—/mnt/swap/ for the place your Storage is held—/media/Storage, in my case."[/INDENT]

Thanks for your help and fast replies =)

---

### Post by TheFu on 2012-02-14
Related to your SWAP question.

a) The old idea of having swap be 1-2x the amount of RAM is outdated.
b) Swap is meant to provide a little overflow for RAM, swapping too much makes a system slow and soon, unusable.

So, I never allocate more than 2GB for swap.  Swaping 2GB of RAM out is slow enough, thank you.  I can't imagine swapping 8GB out.  I do run some extremely well behaved VMs without any swap, but it is dangerous.  If there's no more RAM, your system could crash.  Most people prefer for their system to get slower and slower before a crash.

Whether a different partition is *required*, I don't know. It isn't a problem for me to create a 2GB logical partition - you won't run out of them - and enable the swap there.  I try to put the swap on a different physical disk than the OS to help performance.  Swap needs to be on locally attached, fast storage, not SAN storage.


Somewhere else you asked if 128GB of SSD was enough.
a) I don't use SSD - technology is too new for me.
b) Storage use will always expand to exceed available storage. ALWAYS.

---

### Post by Fightback on 2012-02-14
Hmm. I think I'll just allocate a 2GB Swap partition on the HDD.

You talk about Logical partitions. I must confess that I still don't really understand the difference between a logical partition and a primary partition.

Also, most probably because I don't understand this difference, I don't quite understand how I will have to set up the partitions.

What I want to achieve is the following:

[LIST=1]
[*]SSD (capacity 128GB)
[LIST]
[*]A 80 GB Windows partition for Windows 7 OS and programs.
[*]A 48 GB Ubuntu partition for Ubuntu OS and programs.
[/LIST]
[*]HDD (capacity 500 GB)
[LIST]
[*]A 2 GB (Ubuntu-)SWAP partition
[*]A 30 GB /home partition
[*]A 468 GB storage partition accessible by both OS's (-> NTFS)
[/LIST]
[/LIST]

I intended to first partition the SSD, then install Windows on it. Now, given that I have mounted it onto my system, how would you recommend to partition it? Should I partition it with GParted on the Ubuntu-Live-CD?
And if so, those two partitions would need to be primary partitions, right? Or do I only create the Ubuntu partition and let windows find it's place itself?

Thank you for your help.

---

### Post by haqking on 2012-02-14
I would put your Swap on the SSD as it is faster than the HDD but thats my opinion.

Also swap is not used only if a application runs out of memory.

It is also used when processes in memory are sleeping, they will often be swapped out for current processes.

You also dont have to use a swap partition, you could use a swap file also.

there is lots of debate on it.

On my laptops i use 2x ram +1 for hibernation.

On my desktop i have 16Gb ram and so only use .5x the ram.

I have windows 7 on first SSD with a swap for my Linux

I have linux (slackware and debian) on my second SSD

and a shared 2TB data HDD as my 3rd physical drive

Swap should be close to the first sector on a HDD but i dont think it really matters on a SSD so my swap on my first SSD is towards the end after the Windows C:

My machine runs like its on rocket fuel no matter what i do, what application i run or what OS i am in ;-)

Peace

---

### Post by Fightback on 2012-02-14
Thanks haqking - Awesome blog btw, I'd love to see that guide progressing =)

I read something about not putting Swap on a SSD, because it wears it out?

I still don't really get the partitioning. When I just create a new partition with GParted, will it be a logical partition or a primary one?

---

### Post by haqking on 2012-02-14
> **Fightback said:**
> Thanks haqking - Awesome blog btw, I'd love to see that guide progressing =)

I read something about not putting Swap on a SSD, because it wears it out?

I still don't really get the partitioning. When I just create a new partition with GParted, will it be a logical partition or a primary one?

it only wears it out if it is used constantly which if you have a large amount of ram as it wont be.

besides if the read/written to argument about wearing out a SSD was a big deal we wouldnt put anything on them.

They are a glorified USB key if you like, i still have a 8Mb USB key from like 10 years ago (yes i said 8mb) which has been used a gazillion times and works fine (been in washing machine twice...LOL)

anyways its all down to your personal use really.

By the time your SSD wears out they will be so cheap to replace anyways ;-)

I got my 128GB crucial M4's for like £120 each or something like that, in a years time you will get a 512Gb or 1Tb at that price i suspect.

As for primary or logical that is upto you and what you choose to create.

With MBR then you are limited to 4 primarys per disk or 3 and one extended in which you can have as many logical as you like (give or take)

With GPT the limit is 128

for linux other than the /boot there is no real requirement for a primary over an extended/logical

and /boot doesnt technically need to be a primary but 9/10 often is

edit: here is a link to a explanation i just found for you [http://ubuntuforums.org/showthread.php?t=282018](http://ubuntuforums.org/showthread.php?t=282018) i havent read it all way through but Bodhi knows his stuff so will likely be accurate

edit 2: oh yeah depending on what SSD you have, check to see if there are any firmware updates for them, it can be done after the OS install, but you might want to do them first, if you do them after then make sure you have backups/clones

---

### Post by Fightback on 2012-02-14
That's true. So it will be 3 partitions on the SSD, one for ubuntu, one for windows and one for Ubuntu-swap.

Right, I shall read through that guide and then get to work =)
I shall post (hopefully) how it went^^

---

### Post by haqking on 2012-02-14
> **Fightback said:**
> That's true. So it will be 3 partitions on the SSD, one for ubuntu, one for windows and one for Ubuntu-swap.

Right, I shall read through that guide and then get to work =)
I shall post (hopefully) how it went^^

after each install make a backup/clone then you can restore easily.

Then play around as much as you like until your find a suitable setup that works for you.

I can wipe all my drives in about 2 minutes and reinstall to about 20 different image points from a base windows 7 install to a triple boot and various partitions.

Proper Planning and Preparation Prevents Poor Performance ;-) There is a P missing from that but the language filter would pick it up LOL

Peace

---

### Post by Fightback on 2012-02-14
I will

That's kinda impressing^_^ nice =)

LOL

---

### Post by Fightback on 2012-02-14
I'm sorry for double posting, but I have an important question:
I'm formatting my SSD and was wondering whether I have to make the 2GB Swap partition a primary or an extended partition?
Or do I want to make one big (extended) partition and make logical partitions within?

EDIT: Nevermind, got all excited because of the SSD and forgot what TheFu wrote in the beginning. Sorry.

---

### Post by haqking on 2012-02-14
> **Fightback said:**
> I'm sorry for double posting, but I have an important question:
I'm formatting my SSD and was wondering whether I have to make the 2GB Swap partition a primary or an extended partition?
Or do I want to make one big (extended) partition and make logical partitions within?

EDIT: Nevermind, got all excited because of the SSD and forgot what TheFu wrote in the beginning. Sorry.

Linux doesnt care about primary, extended and logical etc, it can go on anything.

if on a HDD then best to be near beginning of disk to improve read/write times depending on type of disk.

on a SSD probably dont matter too much, with enough ram then it wont hardly matter ever anyways ;-)

---

### Post by Fightback on 2012-02-14
Okay so I formatted the SSD to be one big extended partition, and divided that extended partition into a 2Gb swap partition, a 20GB ext4 partition designated for /, and left the rest unallocated. Rebooted with disconnected HDD, tried to install win7; didn't work.
Back to Gparted, allocated the unallocated part with NTFS, now I'll try again :)

Btw, hardware install went without a hitch :)

EDIT: That didn't help^^
back to GParted, now trying something different: an extended for both / and swap and a primary for windows

---

### Post by darkod on 2012-02-14
> **Fightback said:**
> Okay so I formatted the SSD to be one big extended partition, and divided that extended partition into a 2Gb swap partition, a 20GB ext4 partition designated for /, and left the rest unallocated. Rebooted with disconnected HDD, tried to install win7; didn't work.
Back to Gparted, allocated the unallocated part with NTFS, now I'll try again :)

Btw, hardware install went without a hitch :)

Windows needs to install on primary. Delete all partitions. Make one primary ntfs of 80GB, leave the rest as unallocated. For ubuntu it's best not to create partitions in advance, do it during the install.
When you start the ubuntu install, use the manual method and create the / and swap with the sizes you decided. You can create them as logical partitions.
That's it.

---

### Post by Fightback on 2012-02-14
Okdioke, thanks darkod :)

Going to do that now.

One question though, when/how do I create the seperate /home on the HDD?

---

### Post by darkod on 2012-02-14
> **Fightback said:**
> Okdioke, thanks darkod :)

Going to do that now.

One question though, when/how do I create the seperate /home on the HDD?

You have to do it at the same time when installing. So, if the HDD is not ready for overwriting, you need to wait with the ubuntu installation. It's much more difficult to separate it later on an existing install.

I was referring only to the SSD, that's why I mentioned only / and swap. Sorry if I confused you.

The correct term is: Start the manual method when installing ubuntu and create logical / and swap on the SSD, and primary (or logical) /home on the HDD. If you only have two partitions on the HDD, /home and the ntfs data partition, they can be both primary. No need to use logical.

---

### Post by TheFu on 2012-02-14
Having a plan for the partitions is great, but don't forget that HDD makers don't count the same way everyone else does and there are formating losses. 1000 != 1024, so you won't get 80GB+48GB=128GB 

With that said, I think your numbers are reasonable.  If you are a java developer, you'll probably want more HOME.  I do perl, so I've been able to work easily in 10GB the last 3 yrs.

You do not need to allocate the HDD completely now.  You can move and expand later if you plan smartly now.

Primary partitions are limited to 4 per physical HDD.  To have logical partitions, you need 1 primary that is marked as "Extended." Every "logical partition" resides inside the extended partition.  In the old days, a primary partition was required for booting Windows and MS-Dos.  MS-Windows may still have this requirement - I don't know.  I do know that Linux does not have this requirement for any partitions.  Also, I've heard there isn't any artificial limit on the number of logical partitions that a HDD can hold - over 50 are possible at least.  Basically, I see it this way - primary partitions are scarce - don't use them unless you must.  Logical partitions are plentiful and can be used by all OSes as data partitions and Linux for booting.  Prefer logical partitions.

I've seen laptops from a vendor come with Windows already using all 4 primary partitions.
a) Windows recover
b) hardware support tools
c) Windows OS/Apps Boot
d) Windows Data
In this configuration, we can not create an extended partition to hold any logical partitions. Bad planning.

Don't forget that you need a place to backup all this data.  Backing up the SSD partitions to the HDD is easy enough, but you'll probably find it easier to get another HDD and backup both the SSD and HDD to that instead.

There are 2 types of people in the world those who backup and thos ....

---

### Post by haqking on 2012-02-14
sorry yeah i may of confused things when i said linux doesnt care about primary/logical etc/

Windows does of course ;-)

Peace

---

### Post by Fightback on 2012-02-14
@TheFu
I was thinking something like one extended partition; within two logical partitions, one 20GB /home and the other one the rest of the HDD; Storage.

Hehe, what a nice saying. I am using Duplicity on Ubuntu and Duplicati on Windows for Backup. I might change from Duplicity to Duplicati on Ubuntu aswell, though.
The saying reminded me of a quote I have read somewhere:

> There are 10 types of people in the world, those who understand binary, and those who don't.

Love it =)

---

### Post by haqking on 2012-02-14
> **Fightback said:**
> 
The saying reminded me of a quote I have read somewhere:



Love it =)

I prefer 

> There are only 10 types of people in the world - those who understand ternary, those who don't, and those who mistake it for binary

;-)

---

### Post by Fightback on 2012-02-14
Haha, pretty awesome as well xD

Everything went well. Enjoying fast boot times =)

Do you think the community would be interested in a guide for a set-up like mine?

---

### Post by TheFu on 2012-02-20
I really like **Duplicati** and **Duplicity**, but prefer **rdiff-backup** myself.  In rdiff-backup, the most recent backup appears like a mirror, so getting the most recent version of a file back is just 'cp' . That is very handy.  With the other tools, you must have them installed to restore a file. That can be a hassle sometimes.

Regardless, you are probably doing the best practices for backups using any of these tools. 
**You are to be congratulated.**

---

