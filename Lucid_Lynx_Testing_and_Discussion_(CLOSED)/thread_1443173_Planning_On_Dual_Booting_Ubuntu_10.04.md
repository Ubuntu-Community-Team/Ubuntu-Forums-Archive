---
title: "Planning On Dual Booting Ubuntu 10.04"
date: 2010-03-30
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by techunit on 2010-03-30
I know how to partition install and use Ubuntu...

I am planning on doing a dual boot of Ubuntu 10.04 when it comes out. I understand how to partition my system but I do not understand the boot processes and would like to preserve the Windows Boot Loader. If I understand correctly Unless I make a change under the advanced button at the end of the installation the Windows Boot Loader will be overwritten by GRUB (please note I am not familiar with GRUB or dual booting)

Useful Info:

Dell Studio 1737
Intel Core 2 Duo 2.0 Ghz (64 bit compatible)
320GB HD
ATI Radeon HD 3650
4GB DDR2
Currently Installed OS: Windows Vista 32bit

Version Of Ubuntu Planned To Dual Boot Ubuntu 10.04 64bit

I would Like to preserve the windows boot loader.

A full guide would be helpful on dual booting.

I like video guides so youtube helps.

Thanks....

P.S. If the Graphical Boot Selector is bundled with Ubuntu 10.04 is this necessary?

---

### Post by Iowan on 2010-03-30
[Here]("https://help.ubuntu.com/community/WindowsDualBoot") is a Help page for dual-booting... but I don't know if it has specifics for 10.04 yet.

---

### Post by oldfred on 2010-03-30
It is not easy to use windows to boot Ubuntu. It usually entails writing the grub boot loader out and using the command line to copy the exact bytes required to boot and in windows linking to that file.
Another alternative third party boot loaders.

I find grub2 just fine for multibooting. It is very good at booting other systems particularly windows. If you decide you do not want grub2 it is very easy to reinstall the windows boot loader. The one issue that I have seen remaining is that some windows software writes hidden information into the MBR and corrupts grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

IF you have two drives it is easy to not change windows and totally install Ubuntu into the other drive.

---

### Post by Paqman on 2010-03-30
> **techunit said:**
> 
I would Like to preserve the windows boot loader.


Grub doesn't replace the Windows bootloader (NTLDR), it supplements it. If you select Linux in Grub, it boots Linux, but if you select Windows, it hands over to NTLDR, which boots Windows. So in a normal Grub-based dual boot setup, you still have the Windows bootloader.

---

### Post by oldfred on 2010-03-30
The way I do not recommend (I agree with stlsaint):

[http://ubuntuforums.org/showpost.php?p=9016207&postcount=6](http://ubuntuforums.org/showpost.php?p=9016207&postcount=6)

---

### Post by techunit on 2010-03-30
Ok well one question. I have a restore Partition on my computer. Will using Grub2 affect my ability to use this partition should I need it. Also is the grub2 boot menu the same as seen in the Wubi install? To clarify is installing ubuntu through Wubi also use grub? The reason I ask is because I have installed through wubi before and If it is the same situation then I think I will be fine.
Thanks

Tech-unit

---

### Post by oldfred on 2010-03-30
The wubi uses windows boot loader to chainload into the grub menu. With normal grub install it is reversed. Grub is in the MBR and brings up the grub menu that will also list windows with settings to chainload to windows.

---

### Post by Paqman on 2010-03-31
> **techunit said:**
> I have a restore Partition on my computer. Will using Grub2 affect my ability to use this partition should I need it.

Nope, that won't be a problem at all.

---

### Post by techunit on 2010-03-31
Ok Can someone point me to some examples so I know what to expect. Thank you for the help a set of pictures or a video would be helpful.

---

### Post by Slim Odds on 2010-03-31
> **oldfred said:**
> The way I do not recommend (I agree with stlsaint):

[http://ubuntuforums.org/showpost.php?p=9016207&postcount=6](http://ubuntuforums.org/showpost.php?p=9016207&postcount=6)

What, exactly, is it that you don't like about this method?

---

### Post by oldfred on 2010-03-31
re: Using windows booting to ubuntu

See stlsaint issues. I have used grub and find it very easy to install and update. It becomes a non-standard way to boot that if the user understands can use, but then we can not help with boot problems.

---

### Post by kansasnoob on 2010-03-31
Since you obviously know nothing about dual or multi booting why start with a Beta version of Ubuntu?

I'm honestly not being rude but the odds of a successful experience are minimized with a development distro. You've mentioned both dual-booting and Wubi.

Well read the release notes about Wubi in Lucid Beta1:

> Wubi as included on the ISO images is unable to enter its second stage of installation, so you will not be able to install inside Windows using just an ISO image in this beta release. As a workaround, users who are installing the Ubuntu Desktop Edition can download the stand-alone version of wubi from [http://releases.ubuntu.com/10.04/wubi.exe](http://releases.ubuntu.com/10.04/wubi.exe)  which includes the fix for this bug. This bug will be fully addressed for 10.04 LTS Beta 2. (541607) 

[http://www.ubuntu.com/testing/lucid/beta1#Known%20issues](http://www.ubuntu.com/testing/lucid/beta1#Known%20issues)

These are the simplest guides for dual booting (but they're outdated due to grub2):

[http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm](http://apcmag.com/the_definitive_dualbooting_guide_linux_vista_and_xp_stepbystep.htm)

But if this is your first experience with Linux you should not be starting with a Beta!

---

### Post by VMC on 2010-03-31
> **oldfred said:**
> re: Using windows booting to ubuntu

See stlsaint issues. I have used grub and find it very easy to install and update. It becomes a non-standard way to boot that if the user understands can use, but then we can not help with boot problems.

I agree with this and the link you provided. I guess its mainly for Windows users that want Windows to still control everything. 

Grub and now Grub2 have never failed me, or if I ran into trouble help is just a forum away. We can be more helpful to those using Grub than trying to circumvent the booting process.

As Kansas implied, I'm not sure what the OP here wants, since he mentioned both  installs. We need to know either or - Wubi or partition install.

---

### Post by Slim Odds on 2010-03-31
> **oldfred said:**
> re: Using windows booting to ubuntu

See stlsaint issues. I have used grub and find it very easy to install and update. It becomes a non-standard way to boot that if the user understands can use, but then we can not help with boot problems.

Yes we can, and we will.

I responded to stlsaint. Do you think that I didn't read the post that I replied to?

Some of the things that stlsaint wrote were just plain ridiculous, like this:> You MAY for some weird config be able to see the ubuntu install momentarily but pretty soon it will fail and crash your system.Like some magic little pixies just come and mess with your 'puter. That is some nonsensical scare tactics if I've even seen them.

There are a number of ways to multi-boot and they all work swell.

I've used GRUB, LILO, NTLDR, and the new Win7 bootloader and they all worked, some better than others. None used magic and none just stopped working for no reason.

---

### Post by techunit on 2010-04-03
I don't plan to install the beta... I am preparing myself with the required knowledge based on the help I receive from those who have better knowledge than I.

---

### Post by techunit on 2010-04-03
Ok how do I access grub menu. Does it just come up or do I hit escape? I have change Grub settings in the past but I have never dual booted. I have heard somewhere that ubuntu 10.04 final will have a Graphical Bootloader... I hope you could understand this.

Also should I change my mind and use the Windows Bootloader how do I determine which sda or sdb or sdb2 this has me a little confused. I will end up with four partitions. 

My current partitions are as follows.
1. 141MB ESIA Configuration
2. 10GB RECOVERY
3. 287.95 Windows ( I plan to shrink this partition by 60GBs for ubuntu)

From What I understand the SDx info is set by the location of the  partition on the disk.

* so if this is the order in windows disk management then (from left to right)
(1. will be sda1) 
(2. will be sda2) 
(3. will be sda3) 
and when #3. has been shrunken and ubuntu installed on the free space
I should set the GRUB setting to sda4?

Then I load from the live-cd and in a terminal type 

>  sudo dd bs=512 count=1 if=/dev/sda4 of=linux.bin And When I reboot it will use the windows bootloader? Could you explain a little what is being done with each command (besides sudo) (explain "dd" "bs=512" "count=512" "if=/dev/sda4" "of=linux.bin").

I can translate some parts of this I think. "if=/dev/sda4" converts to if this variable is met "of=linux.bin" then exicute linux.bin (I have some experience with coding...)

My Reason for doing this is because I am unsure about how long I will continue to use ubuntu and would like the ease of going back with out to many change. Change is good just isn't a montra that fits me.

Please check this....!

---

### Post by jppr on 2010-04-03
I don´t have any problem, I have 2 HD. /dev/sda1 is 10.04 and /dev/sdb1 is windows 7.
I even thought of preparing it in windows 7 and ubuntu on the same HD, it was easier to buy a new hard drive for ubuntu

---

### Post by techunit on 2010-04-03
hm.... not to be rude but you must not have understood that I have a laptop... besides the fact that I can actually install two hard drives...


P.s. Partition install is the way I plan to go...

---

### Post by techunit on 2010-04-03
I have installed Debian , Ubuntu, LinuxMint, Xubuntu.... countless times I know what I am doing beyond the bootloader...

---

### Post by oldfred on 2010-04-03
I generally know what dd does but have not used it. I ran this to understand myself and it expains the detail better than I can:
```
man dd
```

Grub2 designers do not want you installing grub2 to a partition. I did it with the beta of Karmic and got the warning message on every update. The designers say blocklists can evenually cause problems that will make you reinstall grub as a file can be moved and then grub cannot find it. I lost my links to all the discussion (as well as losing the argument since I liked chainbooting).

Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by techunit on 2010-04-03
I think that I will go with GRUB (The Relative Ease in which you can restore the Windows Boot Menu) Will the GRUB bootloader comeup as part of the boot sequence or is it accessed through the  Grub menu (hitting "esc" during boot sequence)?

---

### Post by junior aspirin on 2010-04-03
GRUB just shows up as a text list before any OS starts. It shows straight after the BIOS stuff and allows you to select with the keyboard arrow keys which OS to boot into, Ubuntu is the default (although this can be changed) after 10seconds of no action, or hitting enter the chosen OS will boot automatically. If you don't have another OS installed the list is not shown. 

I think that sums up what you are after.

---

### Post by techunit on 2010-04-03
Thank you... I will go with GRUB... Going back to Windows MBR looks fairly easy and I am not worried about the stability of GRUB2... Just curious but will I be given all the recovery options at the boot screen or will it only show the bootable Operating Systems. It doesn't matter but I would like to know what I should expect. Thanks

---

### Post by ranch hand on 2010-04-03
You may want to take a look at the link in my sig.  It will give you a working idea about grub.  The first 2 links in that post are the very best in depth info you are going to get.  The second one is the one I recommend because of the way it is laid out and it is more Ubuntu oriented.

I would shrink your partition as you said but use an extended partition for the unused space.  That way you can have a swap partition (primary partitions are limited to 4) and you could install with a separate /home.  Just easier on your box and your installation.  Somewhat easier recovery too.

---

### Post by techunit on 2010-04-03
I won't need any swap space becuase I have 4GBs of RAM. Could you clarify what you mean by this. Use an extented partition?

Just noticed that you know more about ubuntu and I have been using it for longer!

---

### Post by ranch hand on 2010-04-03
> **techunit said:**
> I won't need any swap space becuase I have 4GBs of RAM. Could you clarify what you mean by this. Use an extented partition?

Just noticed that you know more about ubuntu and I have been using it for longer!
There are 2 types of primary partitions.  One is called a primary the other is called extended.

An extended partition is one in which you can install many "logical" partitions.  As an example I have a 320Gb external enclosure that I am redoing right now.  I use it to loan to people that may want to try Ubuntu (it is a lot faster than the CD).  It has 14 partitions on it counting the swap partition.  This is not possible with just "primary" partitions as they are limited to a maximum of four (old DOS configuration rules).  With an extended partition the number of logicals is, theoretically, infinite.

You can do without swap unless you push the box a lot.  If I open a bunch, 20 or so, images in Gimp I start using some swap.  Sleep also depends on there being an equal amount of swap to ram.

As for knowing more about Linux than you do, I doubt it.  I have gathered some knowledge on some things.  Partitioning an Grub are a couple of them because I enjoy multi-booting.

It does help that I do not use any OS' that are not Linux (except for the Dreaded Mother in Laws box that I try to keep up to date which run Win JerryLewis Pro or something like that).

---

### Post by techunit on 2010-04-03
Well I only plan to have Ubuntu And Windows On my system... If what you are saying is that you can only have 4 primary partitions on a harddrive then I will be fine because currently I only have 2 primary partitions currently and when I install ubuntu I will have 3. So long as swap doesn't act as a primary partition I will be fine. Also I believe that when you use the wizard to install ubuntu you are given the option to install to free-space as part of this a swap partition will be created. Thus I will have a swap partition I don't believe that swap is a primary partition.

I do not think I am going to over complicate this procedure.

---

### Post by ranch hand on 2010-04-03
Yup, swap counts as a primary.

I really like to have a separate /home partition but I suspect that most installs are just a single partition plus the swap.

While I always use both the swap and the /home, if I could only have one of them I would go with the /home.

It is your box, though, so I guess (grudgingly) that you can do what you want with it.

I know that I haven't had any real trouble with my Hardy installation that was installed on one partition.  What a nice OS.

This new LTS, I think, is going to be another similar work horse of an OS.

---

### Post by techunit on 2010-04-03
Ok your right. But a an expanded partition what file system is it? Or will it even matter?

---

### Post by techunit on 2010-04-03
Ok I understand what your talking about. I have been one of those lucky few who doesn't have many problems with there installs. Thanks to people like you. Ok so I shrink my windows partition and then in Gparted make a 60GB expanded partition and then put in a ext4 file system logical partition inside then when installing I should: 

1. select to manualy partition and make a swap partition and install partition Or 2. it I do not make a logical partition inside of the expanded partition and the wizard will recognize it as free space and I don't have to to do more work. 

Which is correct 1. or 2.

Thanks again.

One more question: This won't affect the boot sequence in GRUB correct... I trust it won't because you use it to multiboot using grub.

---

### Post by ranch hand on 2010-04-03
The answer to your question is yes.  Either way you do it.

If you just make the partition (extended) and do nothing to it the installer will see it as unused space.

If you create a small swap partition and then a !0Gb partition for / and leave the rest for /home you will need to use the manual partitioning option in the installer.  This is not tough.  Scared the crap out of me the first time and then I felt pretty silly.

You can actually create the extended partition, the logical partitions within it (/ ,/home, swap) all in the installer partitioner.  I just do it with gparted first for some reason.  I guess because it is a good idea to get gparted up and really look at the drive and plan what  you are doing if you are multi-booting so you may as well just get the partitions made ahead of time.

Seeing that you just have the unused space after resizing with the MS partitioning tool, the installer partitioner would be just fine.  You just right click on the unused space and select "change" or "edit" (they keep changing the names of the options) and add the partitions.  There is a place to define the buggers for format (ext2,3 or 4 and swap and a couple others) and mount point (/, /home, swap and some others).  Pretty simple really and you have it set up the way you want.

You ought to try it out with 9.04 or 9.10 and see how tough it is.

I wouldn't put a testing OS on my main drive at all.  I use 10.04 all day, right now.  My main drive (both internals actually) are turned off in bios.  I want no development contamination on my stable installs.

---

### Post by techunit on 2010-04-03
New Game Plan Please Comment...

1. back-up my data
2. In windows Disk Management Shrink my windows partition by 64GBs
3. Reboot and make sure everything is working
4. Boot into Ubuntu 10.04 64bit Live CD
5. Create a Expanded Volume of 64GBs
6. Double click install and install ubuntu to largest contiguous free space (inside of expanded volume) **This should create a ubuntu partition and a swap partition inside the expanded partition correct?**
7. Reboot

I will use GRUB2 Bootloader thanks to the advice of the forum members.

Thank you.

---

### Post by techunit on 2010-04-03
To installing a development release I agree I am waiting but I wanted to make sure that I knew what I was getting into with a dual boot and get some better knowledge on the subject.

I have used the manual partitioner for a long time since the eeepc netbook I have has a SSD it isn't good to have swap on it, because of the limited number of read and writes you can have. 

I was a senior member on the forum.eeeuser.com forum for the original eee pc netbook and I started with ubuntu from there. Now that I am using ubuntu on almost every machine I wanted to move to this forum to ensure that I get better answers.

Thank you so much for the help you really made this easy for me to get my plans set.

---

### Post by rondackcpu on 2010-04-03
Here is a link to a discussion on how to launch the Restore Partition if the MBR links become corrupted.  It sounds like the real thing.

    <http://www.goodells.net/dellrestore/recover.htm>

Hope it helps.

CRS

---

### Post by ranch hand on 2010-04-03
Sounds like it should work just fine.

I can see the appeal of the SSDs but I think I am going to wait a bit before fooling with them.  In an unbelievably short time they will have a lot more capacity and be a lot cheaper.

---

### Post by techunit on 2010-04-03
Rondackcpu this is not an official dell resource thus I cannot trust it. would you please remove the link so that someone looking at this thread doesn't screw up there machine doing something that is unnecessary and incorrect.... The Recovery partition just holds the image to be burn to a cd. There is another kind of restore that accesses the restore image from the restore partition, but that is embedded in the bios ( I don't believe it to be affected by the GRUB bootloader).

Also, if I understand correctly I can just restore the MBR ( I have a restore DVD) should something go wrong and have access to the restore partition if needed.

I am sure that you were just trying to help but. . . and I mean nothing mean by this but it seems that you didn't completely read over the thread. I don't blame you because we are all guilty of this.

The correct way to go about this is. . . if I am not mistaken. . . is to restore the MBR should I need the restore partition. The Restore image to restore the entire harddisk is launched at the bios.

I don't mean to be rude but the imformation that you provided is not official and doesn't apply to a new machine norton ghost isn't used anymore if I remember correctly) My brothers laptop had this form of restore image and the imformation applies only to that kind of image.

---

### Post by techunit on 2010-04-03
Yes wait one more year and you could have a wonderful 320GB SSD for only $100

estimate based on past market on memory.

---

### Post by techunit on 2010-04-03
The major reasons for focusing on making sure that I am completely sure what I am doing is based on that the laptop I am planning to install ubuntu on is my primary computer and is something goes awry I will have to depend on secondary computers.

P.S. I have a Wifi finder button built into the side of my computer. I am wondering of it will bring up any applications or if I need to install one. I know that it will work when it is shutdown, hibernated or suspended.

---

### Post by ranch hand on 2010-04-03
Judging by the performance of my wifes Sys76 Pangolin I would say that the thing should have no trouble connecting.

We had, or I should say I had, some trouble getting the bugger hooked up but that had to do with not knowing anything about wifi connections.  Up until a year ago we had never connected with anything but dialup.  It really helps if you know how to activate the wifi.

---

### Post by techunit on 2010-04-03
OK well I tried this procedure but you must manually partition and ensure you select to use the logical partition option otherwise it won't work. I need to know what I should set the mount point. On a single installation I usually choose the root directory, but I am not sure about what I should set for a dual boot. Oh and how much swap space do you think I need.

---

### Post by ranch hand on 2010-04-03
Well, I haven't used the auto install for several releases.  Sorry.

If you just want one partition for your install use the / (root) mount point that will  install every thing right there.

For sleep to work you need the same swap as your ram (that is what they say, I never use it so I don't know) and that is what you will get with auto installation.  I usually go about 1Gb because it is easy to hit.  I have five 320Gb HDDs so if I use a bunch it really doesn't matter.  I would use at least a half a gig so that you have enough if you get into something demanding.

With the amount of ram in most boxes now it really takes some doing to need it or to notice that it is faster with it than without it so if you do not do things that have a lot of demand I would keep it small.

When we bought the Pangolin it came installed on a 10Gb / and then 3Gb swap (same as ram) and then the rest of that 320Gb HDD as /home.  I removed the swap and shrank the /home a bit and then enlarged the / and put the swap back in (it came out a little bigger, 3.5Gb I think.  Sleep works great on it, wife uses it.

---

### Post by seeker5528 on 2010-04-03
> **techunit said:**
> Also should I change my mind and use the Windows Bootloader how do I determine which sda or sdb or sdb2 this has me a little confused. I will end up with four partitions.

<snip>

> and when #3. has been shrunken and ubuntu installed on the free space I should set the GRUB setting to sda4?

Then I load from the live-cd and in a terminal type 

And When I reboot it will use the windows bootloader? Could you explain a little what is being done with each command (besides sudo) (explain "dd" "bs=512" "count=512" "if=/dev/sda4" "of=linux.bin").

You don't want to copy the entire MBR, just the code area so the block size should be 446 (bs=446) and you only want to do it once or else you will be outside of the area you want (count=1), if you did more when creating an image you would just end up with extra stuff, if you are writing back to the MBR you want to make sure it doesn't overwrite important information....

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you copy the MBR before installing Ubuntu, the existing paritions should get mounted at ,/media/something-or-other' so if you do:

```
dd if=/dev/sda of=/media/something-or-other/windows-mbr.img bs=446 count=1
```

Then if you later decide you want the windows boot loader in the MBR for whatever reason you can do:

```
dd if=/path/to/windows-mbr.img of=/dev/sda1 bs=446 count=1
```

If you write more than 446 then you start getting into the partition table information, which could be bad if the partition tables have changed in between the time you made the image and the time you wrote the image back the the MBR.

Later, Seeker

---

### Post by techunit on 2010-04-03
> **seeker5528 said:**
> <snip>



You don't want to copy the entire MBR, just the code area so the block size should be 446 (bs=446) and you only want to do it once or else you will be outside of the area you want (count=1), if you did more when creating an image you would just end up with extra stuff, if you are writing back to the MBR you want to make sure it doesn't overwrite important information....

[http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

If you copy the MBR before installing Ubuntu, the existing paritions should get mounted at ,/media/something-or-other' so if you do:

```
dd if=/dev/sda of=/media/something-or-other/windows-mbr.img bs=446 count=1
```Then if you later decide you want the windows boot loader in the MBR for whatever reason you can do:

```
dd if=/path/to/windows-mbr.img of=/dev/sda1 bs=446 count=1
```If you write more than 446 then you start getting into the partition table information, which could be bad if the partition tables have changed in between the time you made the image and the time you wrote the image back the the MBR.

Later, Seeker

Um sorry for making it so unclear. I am now going with GRUB bootloader because of the relative ease in which I can move back to Windows Bootloader.

---

### Post by techunit on 2010-04-03
ranch hand. Thankyou I found somemore information on this and have all the information I need for now.

---

### Post by seeker5528 on 2010-04-05
> **techunit said:**
> Um sorry for making it so unclear. I am now going with GRUB bootloader because of the relative ease in which I can move back to Windows Bootloader.

If you are dual boot from a single hard drive with Windows Vista or 7, then some updates will fail if they include things that relate to hard disk/directory encryption. The logic being if they don't control the entire boot process, they can't verify the integrity. 

Not such a big deal if it was just an update for those things. If you can't install the service packs, that's a bit more significant.

If you have Vista basic this shouldn't be an issue you have to worry about, it doesn't give the option to use the encryption, can't swear 100% about premium, but I think basic is the only one that doesn't provide the option to use disk encryption.

The way I set up my system is with multiple hard drives, Linux on the first, Windows on the second. When the odd occasion comes along where Windows thinks it needs control of the MBR for an update, or the rare occasion when I re-install/upgrade Windows, I just unplug the first HDD and make sure the Windows drive is first in the HDD boot priority.

Later, Seeker

---

### Post by techunit on 2010-04-06
No encryption in home premium. I haven't received any updates regarding the Harddisk. I have firmware updates that have been used to fix issues with the integrity of the HD but those don't require the windows MBR. Also if there were so many problems with this then Dual booting wouldn't be so popular.

---

### Post by ranch hand on 2010-04-06
A better way to say that would be "if it was hard ranch hand wouldn't have 12 OS' on his test platform".

---

### Post by techunit on 2010-04-06
That is correct! Ranch Hand Wouldn't be running OSes so easily and if he had a problem then we would know.

---

