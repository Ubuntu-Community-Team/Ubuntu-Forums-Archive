---
title: "Adventures in Partitioning (Newby)"
date: 2020-01-15
forum: Installation &amp; Upgrades
---

### Post by davepool on 2020-01-15
Background: when I first moved to Linux last fall, it was with a low-spec laptop that was sitting in the back of the closet. Then I decided to add Linux to a slightly more capable laptop that I depended on for business in a dual-boot with Windows 10. But both of those installations were "full" (using the first option, Erase Disk and Install) and through online discussions I came to realize this was teaching me nothing about partitioning.  OTOH, these laptops were not anything I wanted to experiment with, since I depended on them.

So I picked up via ebay a used Lenovo ThinkPad X131e (with 8gb RAM...so I can try a distro with more of a demand on memory) and that's what I'm going to use as my laboratory (or playground, take your pick). It's on this device that I've installed Ubuntu Budgie.  With that installation, I went the "Something Else" route and, probably mostly due to the drives being configured this way (the previous owner had a Linux Mint install) -- though I *did* adjust the sizes of the partitions and formatted them -- I came out with this setup:

/dev/sda1 Filesystem Partition 1 using 20GB ext 4 to the / (320GB HDD)
                300GB free

/dev/sda2 Swap Partition 1 using 8.4GB as the Swap (20GB SATA SSD)
                Filesystem Partition 2 using 12GB ext4 to the /home 
                2.6 MB free

Now, let me add here that it wasn't until after I bought this laptop and even AFTER I made this installation that I realized the second drive was a SSD! And that leads to my question here: would there be any reason NOT to have done this installation by "flipping" everything...putting the OS on the SSD and the swap and /home on the HDD?  I realize that the current Filesystem partition on /sda1 is exactly the same size as the SSD...but I also know that size was arbitrary and simply based on some general guidelines I'd seen online. So how much smaller could that be? Would the speed of operation from the SSD be worth doing this? On the other side of the coin, are there good reasons NOT to use the SSD for the OS? 

Also, if anyone has any guidance as to how big the partitions above (in the installation that's been performed...and that works!) could have/should have been, I'd appreciate the advice!

---

### Post by TheFu on 2020-01-15
People ask "how should I partition my install" all the time.  Please search these forums for lots of different answers.

Additionally, I wouldn't have 8G for the swap.  4.1G is my only answer for a desktop system swap size regardless of RAM in the system. There are caveats to this - also explained in detail in these forums already.

---

### Post by SeijiSensei on 2020-01-15
In general, most users have no need to partition their drives for Ubuntu installations these days unless it's for dual-boot or multiple operating systems.  I like to keep a couple different operating systems on my machines so I do partition my drives. In general I use
- a 512 MB partition with ext2 for /boot
- a 20 GB ext4 partition for each OS image that will be mounted as / when booted
- a swap partition larger than the actual memory size to enable hibernation
- the rest of the drive for /home so that it can be shared across the various operating systems

20GB for each OS is a bit of overkill; my Kubuntu 20.04 installation occupies about 7 GB. /boot and swap are separate primary partitions; the rest of the drive uses an extended partition. I believe current Ubuntu default installations no longer use a swap partition but a swap file instead.

If you want to learn more about storage options, I'd look into LVM as an alternative to fixed partitions: [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I have only single 512 GB SSDs in my laptops, and only HDDs in desktop towers.

---

### Post by davepool on 2020-01-15
> **TheFu said:**
> People ask "how should I partition my install" all the time.  Please search these forums for lots of different answers.

Additionally, I wouldn't have 8G for the swap.  4.1G is my only answer for a desktop system swap size regardless of RAM in the system. There are caveats to this - also explained in detail in these forums already.

@TheFu Thanks for the reply. The suggestion to "search" is not unexpected...that seems to be the reflexive response in most any forum for most any topic. And it's a valid point and I understand why active members get weary responding. However, those searches typically produce a lot of chaff surrounding the wheat, since they pull up all of the peripheral comment that every thread included. Perhaps that's why a lot of Linux distro forums have decided to compile a Wiki and make that available to users.

I'll see if I can find the explanation for why 4.1G is "the answer" for a swap...when having it the same size as the RAM was similarly offered as "the answer" somewhere else.

---

### Post by davepool on 2020-01-15
> **SeijiSensei said:**
> In general, most users have no need to partition their drives for Ubuntu installations these days unless it's for dual-boot or multiple operating systems.  I like to keep a couple different operating systems on my machines so I do partition my drives. In general I use
- a 512 MB partition with ext2 for /boot
- a 20 GB ext4 partition for each OS image that will be mounted as / when booted
- a swap partition larger than the actual memory size to enable hibernation
- the rest of the drive for /home so that it can be shared across the various operating systems

20GB for each OS is a bit of overkill; my Kubuntu 20.04 installation occupies about 7 GB. /boot and swap are separate primary partitions; the rest of the drive uses an extended partition. I believe current Ubuntu default installations no longer use a swap partition but a swap file instead.

If you want to learn more about storage options, I'd look into LVM as an alternative to fixed partitions: [https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)

I have only single 512 GB SSDs in my laptops, and only HDDs in desktop towers.

Thanks for the reply, @SeijiSensei. From what you've provided, I think I can take some comfort in the choice of 20 GB for the OS image (and even if it's overkill, as you say, it's at least commonplace). 

It's also good to know that "most users have no need to partition their drives for Ubuntu installations these days unless it's for dual-boot or multiple operating systems." As I explained, that *was*, in fact, the route I took with my first two installations on two other (less capable) laptops. But then I came upon a lot of users who were big believers in having a separate /home that they could use if/when they changed distros or chose a fresh install instead of an upgrade to their existing distro. And that's when I realized I couldn't "learn by doing" if I was using the complete installs.

So, if I've understood you, your laptops have *only* the SSDs and, therefore, that's why you've installed the Linux OS on them? Of the two replies I've received so far (you and The Fu) it appears neither one of you thinks my SSD is a better (or even good) choice for the OS over the larger HDD.

Boston, eh?  I lived there for 7 years ('80 through the end of '86...almost more years ago than I care to admit).  It was a great time to be there...though I tell people now (and not trying to be glib) that I liked everything about living in the Boston metro except affording it!

---

### Post by SeijiSensei on 2020-01-15
> **davepool said:**
> So, if I've understood you, your laptops have *only* the SSDs and, therefore, that's why you've installed the Linux OS on them? Of the two replies I've received so far (you and The Fu) it appears neither one of you thinks my SSD is a better (or even good) choice for the OS over the larger HDD.

I'd put the OS on the SSD for performance reasons, though with enough memory there isn't that much disk activity in normal operation. Linux loads needed programs and libraries into memory; once they are there the disk's performance doesn't matter. Putting the OS on the SSD considerably speeds up booting. 

> Boston, eh?  I lived there for 7 years ('80 through the end of '86...almost more years ago than I care to admit).  It was a great time to be there...though I tell people now (and not trying to be glib) that I liked everything about living in the Boston metro except affording it!

It hasn't gotten any better affordability-wise since then.

---

### Post by oldfred on 2020-01-15
That looks like a Haswell based system which would then have had Windows in UEFI boot mode.
Microsoft has required vendors to install Windows in UEFI boot mode with gpt partitioning since 2012.

For default installs of both Windows & Linux by users, it installs in the same boot mode as you boot install media. Systems with UEFI Secure boot off, will offer two ways to boot live installer, UEFI:flash or flash where flash is name or label of flash drive. My system says [noparse]UEFI:PMAP[/noparse] or PMAP. 

And then if you partition in advance and want UEFI, you really should use gpt and must have an ESP - efi system partition.

Lots more info on UEFI install, partitioning, definitions etc in link below in my signature.

---

### Post by davepool on 2020-01-15
@SeijiSensei Sounds pretty much like I'd be better off leaving well enough alone! Wasn't aware of the point about low disk activity with enough memory...do you think 8GB qualifies as "enough"?

---

### Post by davepool on 2020-01-15
> **oldfred said:**
> That looks like a Haswell based system which would then have had Windows in UEFI boot mode.
Microsoft has required vendors to install Windows in UEFI boot mode with gpt partitioning since 2012.

For default installs of both Windows & Linux by users, it installs in the same boot mode as you boot install media. Systems with UEFI Secure boot off, will offer two ways to boot live installer, UEFI:flash or flash where flash is name or label of flash drive. My system says [noparse]UEFI:PMAP[/noparse] or PMAP. 

And then if you partition in advance and want UEFI, you really should use gpt and must have an ESP - efi system partition.

Lots more info on UEFI install, partitioning, definitions etc in link below in my signature.

@oldfred I don't know about "Haswell-based system" but I think we can all assume that even if the guy I bought the ThinkPad from had Linux Mint on it, it certainly came from the factory with Windows.  But, as I said, about all I did was "follow the roadmap" of where things were laid out in his LM install.

I'll certainly check out the info at the end of your link....because most of that above about UEFI, PMAP, etc is a foreign language. But if it helps any, all of these installs of mine (including last night's of Ubuntu Budgie) were done with a USB on which the flashed installer was via Etcher from a download actually done on my Windows 10 desktop PC.

---

### Post by CelticWarrior on 2020-01-15
> **davepool said:**
> I'll certainly check out the info at the end of your link....because most of that above about UEFI, PMAP, etc is a foreign language. But if it helps any, all of these installs of mine (including last night's of Ubuntu Budgie) were done with a USB on which the flashed installer was via Etcher from a download actually done on my Windows 10 desktop PC.

If you are installing OSes, Linux, Windows or others, that language cannot be foreign. You actually need to learn about and be aware of the basic differences between different hardware and be familiar with all the other hardware the machine has.  Not doing that is asking for trouble.

And the reason why you won't find the thing you're asking, some sort of "definitive guide for partitioning", is because that thing doesn't exist. That are different OS requirements regarding both the file system in the partition(s) and about the partitioning type as well - Windows requires MBR for BIOS/Legacy and GPT for UEFI - but besides those it all boils down to requirements of specific usage scenarios and personal preference. No one can give you the answer you're looking for, you need to learn first then find your answer by yourself. Like someone said here or AskUbuntu, not sure, not long ago, *if you want to understand Greek literature, you need to start by learning the Greek alphabet*.

---

### Post by davepool on 2020-01-15
> **CelticWarrior said:**
> If you are installing OSes, Linux, Windows or others, that language cannot be foreign. You actually need to learn about and be aware of the basic differences between different hardware and be familiar with all the other hardware the machine has.  Not doing that is asking for trouble.

And the reason why you won't find the thing you're asking, some sort of "definitive guide for partitioning", is because that thing doesn't exist. That are different OS requirements regarding both the file system in the partition(s) and about the partitioning type as well - Windows requires MBR for BIOS/Legacy and GPT for UEFI - but besides those it all boils down to requirements of specific usage scenarios and personal preference. No one can give you the answer you're looking for, you need to learn first then find your answer by yourself. Like someone said here or AskUbuntu, not sure, not long ago, *if you want to understand Greek literature, you need to start by learning the Greek alphabet*.

Fair enough, @CelticWarrior. Though, I really thought I might get a few measly points for even having tried (much the same way the French will generally take an English speaker off the hook once he or she has at least _*tried*_ to speak French), and actually performed a successful install via Something Else...and, net-net, was really asking about putting the OS on the SSD. I wasn't asking about Windows OS and file systems and partitioning there. I was asking only about Linux. 

I was totally prepared for "figure it out, buddy" from a Linux forum, as that reputation has been around a long time. So, I get it. But the downside to your "learn first and then find your answer by yourself" approach is that, quite possibly, the newbie does try to learn and tries to seek that answer...and then when additional info is solicited, the response (apparently) is "Ah, you didn't learn enough! Keep at it!" ](*,) :wink:

---

### Post by CelticWarrior on 2020-01-15
The point is there isn't a correct answer, it all depends on the intended usage. There are however minimal and recommended system requirement that you must keep in mind when manually partitioning.

One thing that now you don't need to worry about is the swap partition and that used to have some rules about size. Ubuntu since 17.04 uses a swapfile instead the swap partition by default. Whatever the installer sets as the maximum file size is usually fine.

For /root/ it, again, depends on the usage. If not having a separated /home partition then what makes sense is using the whole available space. With a separated /home partition then the size of /root/ will depend only on the amount of different softwares you intend to install.

And all of the precedent is independent of knowing whether your system has BIOS or UEFI as those require different installation processes and have different partitioning requirements, particularly if multi-booting.

---

### Post by TheFu on 2020-01-15
Everyone here was a noob at some point.  We asked similar questions.  Today, there is so much more information easily available between help.ubuntu.com and wiki.ubuntu.com and wikipedia.org and these forums.  Terms are defined. Examples are shown.  Real-world examples.

Searching for suggested disk layout ... 
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

in these forums ... 
[https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987](https://ubuntuforums.org/showthread.php?t=2426927&p=13888987#post13888987) - my layout; some others posted theirs too.
[https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277](https://ubuntuforums.org/showthread.php?t=2425709&p=13883277#post13883277) - my explanation - see why I wasn't willing to re-type that?  Don't worry too much about all the LVM stuff. You can think of an LV (Logical Volume) as a partition.

There are help.ubuntu.com guides for swap sizing as well.

Regardless, your situation is a little different, so you'll need to consider what you find, learn some terms, and make the best guess you can.  That's how we all learned this stuff.  I made some not-so-great choices when I was new and have learned from that.

---

### Post by SeijiSensei on 2020-01-16
> **davepool said:**
> @SeijiSensei Sounds pretty much like I'd be better off leaving well enough alone! Wasn't aware of the point about low disk activity with enough memory...do you think 8GB qualifies as "enough"?
More than enough. Currently my Kubuntu 20.04 machine is using about 2.6 GB of the 8 GB I have available. Most of the rest is being used as buffers and cache. Linux is quite aggressive about caching disk reads and writes so most of them are served from memory rather than physical storage.

---

