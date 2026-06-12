---
title: "Dapper 6.06 don't boot after update"
date: 2006-05-31
forum: Installation &amp; Upgrades
---

### Post by Han on 2006-05-31
Hello,

After updating dapper 6.06 LTS it won't boot and gives the following message:
mount; Mounting /dev/hda1 on root failed: No such device
mount; Mounting /root/dev on /dev/.static/dev failed : No such file or dir
mount; Mounting /sys on on /root/sys failed: No such file or dir
mount; Mounting /proc on /root/proc failed: No such file or dir
Target filesystem doesn't have /sbin/init

Has somebody a solution 

Kind regards

---

### Post by derek_i on 2006-06-01
[QUOTE=Han]Hello,

After updating dapper 6.06 LTS it won't boot and gives the following message:
mount; Mounting /dev/hda1 on root failed: No such device
mount; Mounting /root/dev on /dev/.static/dev failed : No such file or dir
mount; Mounting /sys on on /root/sys failed: No such file or dir
mount; Mounting /proc on /root/proc failed: No such file or dir
Target filesystem doesn't have /sbin/init

Has somebody a solution 

Kind regards[/QUOTE]
Same error here, right now trying to recover the filesystem (ext3) with an alternate superblock...

---

### Post by Smirre on 2006-06-02
After the update I only get a somewhat garbled screen saying it couldn't start the X server.   Been looking around, but still haven't got a clear idea on how to fix it.   I guess a clean install is the best solution, since I'm not at all familiar with using the console to recover from these kind of crashes/problems.  A bit annoying, seeing as I had gotten Ubuntu running and looking the way I wanted.

---

### Post by GQed76 on 2006-06-02
The X server is most likely failing due to a driver with your video card

Try editing your xorg.conf 

```
sudo gedit /etc/X11/xorg.conf
```

look for the area saying

Section "Device"
Identifier "ATI Technologies, Inc. Radeon 330M/340M/350M (RS200 IGP)"
Driver "ati"
BusID "PCI:1:5:0"

And in the Driver area, replace ATI  (or whatever driver it is) with VESA.  Save and try again

---

### Post by lolke on 2006-06-02
[QUOTE=Han]Hello,

After updating dapper 6.06 LTS it won't boot and gives the following message:
mount; Mounting /dev/hda1 on root failed: No such device
mount; Mounting /root/dev on /dev/.static/dev failed : No such file or dir
mount; Mounting /sys on on /root/sys failed: No such file or dir
mount; Mounting /proc on /root/proc failed: No such file or dir
Target filesystem doesn't have /sbin/init

Has somebody a solution 

Kind regards[/QUOTE]

See the same problem on a box that I upgraded from Breezy to Dapper. The problem that I see is the disks are recognized in a different order. When you see this error you will be at the busybox prompt. /dev/hda1 is mounted as /root, just take a look at /root and see what you see. In my case my old /dev/hde1 was mounted as /dev/hda1 so no wonder it can't find anything.
So somehow the disk order is different. Haven't been able to figure out how to change it.

I have an extra IDE controller card in my box so I can have a few extra disks.  So it see the extra controller card before the onboard IDE controller. The first drive on the onboard controller (the real /dev/hda) has the root system. But now it see that first disk on the extra card as the hda and therefore the root system can't be found.

Anybody see the same problem?

Lolke

---

### Post by ubuntu_demon on 2006-06-02
I had to edit my : /boot/grub/menu.1st and my /etc/fstab

Because what was /dev/hda in breezy had become /dev/hde for **me**.

$sudo apt-get install gparted
$sudo gparted will show you how your harddrive is recognized

You can also find out using fdisk or a livecd. (I tried some flight live cd a couple of weeks ago and it too recognized my harddrive as /dev/hde).

---

### Post by KeithO on 2006-06-02
i had this same issue last night.  I have 2 hd's on 1 ide cable (1 for file storage and 1 for the OS) and after upgrading, i got a busybox error stating it couldn't find hda1.  i'll try downloading a live cd and seeing whats up.

---

### Post by ezsit on 2006-06-02
This might be an "easy" fix for an old linux guru, even an novice may work his/her way through the instructions to fix this problem without too much trouble. However, this is a show stopper for a newbie. Couldn't this type of install problem be fixed before release? Confusing IDE device order seems like a pretty basic flaw. Doesn't it?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=ezsit]This might be an "easy" fix for an old linux guru, even an novice may work his/her way through the instructions to fix this problem without too much trouble. However, this is a show stopper for a newbie. Couldn't this type of install problem be fixed before release? Confusing IDE device order seems like a pretty basic flaw. Doesn't it?[/QUOTE]
AFAIK it only happens for a few people. 

AFAIK there are bug reports about this type of problem. 

IMHO a release such as Dapper has to be released eventually .. it's impossible to fix all bugs otherwise releases would get postponed indefinitely and Ubuntu would resemble Debian (which also rocks) very much. Ubuntu chooses for predicatable releases. 

I hope a bug fix will become available through updates though.

---

### Post by ezsit on 2006-06-02
> AFAIK it only happens for a few people. 

AFAIK there are bug reports about this type of problem. 

IMHO a release such as Dapper has to be released eventually .. it's impossible to fix all bugs otherwise releases would get postponed indefinitely and Ubuntu would resemble Debian (which also rocks) very much. Ubuntu chooses for predicatable releases.

I'm not talking about fixing all bugs, but bugs that cause impropper IDE device mappings seems important for the pre-release phase. I've been using Ubuntu since 5.04 and have witnessed a steady decline in the quality of releases. Breezy had several issues and Dapper seems even worse. I've been looking at the live version and don't see much of anything to tempt me away from my patched and stable Breezy system.

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=ezsit]I'm not talking about fixing all bugs, but bugs that cause impropper IDE device mappings seems important for the pre-release phase. I've been using Ubuntu since 5.04 and have witnessed a steady decline in the quality of releases. Breezy had several issues and Dapper seems even worse. I've been looking at the live version and don't see much of anything to tempt me away from my patched and stable Breezy system.[/QUOTE]
That's a bit personal as everyone has different hardware and different needs.

On average most people agree that Dapper is an improvement over Breezy. But if you want to use Breezy go ahead. Ubuntu is also about choice.

---

### Post by lolke on 2006-06-02
[QUOTE=ezsit]This might be an "easy" fix for an old linux guru, even an novice may work his/her way through the instructions to fix this problem without too much trouble. However, this is a show stopper for a newbie. Couldn't this type of install problem be fixed before release? Confusing IDE device order seems like a pretty basic flaw. Doesn't it?[/QUOTE]

Agree. Got my system up and running again by editting the grub boot command, changing hda to hde1. Now it boots fine but still had to edit the fstab to make sure other partitions are mounted correctly.

By the way in my opinion this is a major BUG. The order of disks should be:
- first IDE port on mobo
- second IDE port on mobo
- additional IDE ports on additional cards

But somehow dapper thinks that the first disk is on the additional card. I've seen reports on the same problem with SATA cards. So this looks like a common problem. Looks like a udev problem but I'm not 100% sure.
If you only have one disk in your system you won't see this issue but none of my boxes have one disk.

I think this should be raised as a very high issue. I'll have to check the bug reports and see whether something like this has the right attention. This will give Ubuntu a bad name because it has the name of that it "simply works". Well for me it doesn't. I had to do some stuff to make it work. No problem for me but a lot of other folks will have problems.

Just me 2 cents,
Lolke

---

### Post by ubuntu_demon on 2006-06-02
Ofcourse it's very frustrating and unfortunate if it happens to you. And I really hope there will be a bugfix for it through the updates.

---

### Post by KeithO on 2006-06-02
I agree that this kind of thing should not happen.  The install was seemless until the reboot.  when i burned a live cd and loaded that way, the only real option i could see was to start fresh.  luckily this is just an experimental box so it didn't kill me to do.

---

### Post by ezsit on 2006-06-02
> That's a bit personal as everyone has different hardware and different needs.

On average most people agree that Dapper is an improvement over Breezy. But if you want to use Breezy go ahead. Ubuntu is also about choice.

IDE drive detection and partition mapping is personal? I would assume most epeople have IDE drives. Sure, some people have SCSI and some have SATA, but most users have IDE drives. I have two IDE drives in my system, some people have only one, and others have more. This particular bug might only show on certain motherboards, or on certain drive configurations - that's what makes less than endemic, but it certainly isn't personal. Don't getr me wrong, I'm not making fun of your phrasing to be nasty. I merely see this issue as larger than you might think.

As for using Breezy, if it works, why fix it?

---

### Post by ubuntu_demon on 2006-06-02
[QUOTE=ezsit]IDE drive detection and partition mapping is personal? I would assume most epeople have IDE drives. Sure, some people have SCSI and some have SATA, but most users have IDE drives. I have two IDE drives in my system, some people have only one, and others have more. This particular bug might only show on certain motherboards, or on certain drive configurations - that's what makes less than endemic, but it certainly isn't personal. Don't getr me wrong, I'm not making fun of your phrasing to be nasty. I merely see this issue as larger than you might think.
[/QUOTE]
AFAIK it only happens with certain hardware. Not with all hardware.

[QUOTE=ezsit]
As for using Breezy, if it works, why fix it?[/QUOTE]

I don't have anything against running breezy.

---

### Post by lolke on 2006-06-02
[QUOTE=ubuntu_demon]
I don't have anything against running breezy.[/QUOTE]

Neither have I so I won't upgrade my other boxes for now. But still one box has the problem and there is no way back. disk ordering (IDE, SATA or SCSI) is a standard almost, especially for IDE (PATA). So for years (I started in 1997 with Debian hamm using 2.0.32 kernel) the ordering was the same but somehow for dapper it is different. Not good and it should be a high priority bug.

Lolke

---

### Post by govedarov on 2006-06-03
I have same problem . I decided to upgrade to dapper with lean install . The Cd`s I downloaded didnt work at all - neither live or the install CD ( no idea why , they stopped responding when I tried to run the partitioner.)
Then I decided to install breezy, and then to upgrade it clean - installed , updated to dapper - reboot : voila! 
It started to mount the /root, then waited and then - appeared a black screen . I wrote the messages down :

/dev/sda6 does not exist. Dropping to a shell

Then came some sort of BusyBox ( whatever it is ) , and there was :

/bin/sh : can't access tty; job control turned off


OK - u explain to change fstab , and other things - but can u give me a more simple explanation bout it ( I am not that expirienced with it). What exactly should it be done ? ( step by step if possible).
Thanx in advance !

---

### Post by Al_maverick on 2006-06-04
Also, how can I find the new name for the drive? I upgraded using adept, I didnt download the livecd or the alternate cd. Now I am downloading it, but if there is a quick way to find how dapper is detecting my drive, I could change the grub boot command and the fstab now.
In breezy it was sda3. Ive tried sda1 to sda7, and sdb3, but no luck. I am downloading both CDs now, but it will take 2 days with my slow broadband access. Im back to XP for the moment :(

---

### Post by ubuntu_demon on 2006-06-04
**booting stalls during "mounting root filesystem"? See adament's post here** :
[http://www.ubuntuforums.org/showpost...6&postcount=11](http://www.ubuntuforums.org/showpost...6&postcount=11)

---

### Post by therunnyman on 2006-06-04
Ayuh, same problem here.  Here's what I know for certain: for whatever reason (probably udev), the SATA drives connected to a card (PCI Promise controller here) are mounted first, becoming sda and sdb.  The ones plugged in to your SATA mobo are then mounted as sdc and sdd.  Very sad, pitiful bug that should've been fixed ages ago, but isn't.  Anyone with more than two SATA disks encounters this problem; for my part, I reported it, confirmed it for the thousands of others who encountered this bug, and nothing's happening.

A solution, if you really want Dapper, is to physically rewire your disks according to the scheme above.  First, unplug your third (and fourth, if you have it) SATA drives.  The Dapper installer will properly recognize your mobo drives as sda and sdb.  Install dapper on the drive of your choice (let's say sda for example).  When you're done, connect port 1 from your card to the disk you installed Dapper on , in this case, the disk that was sda, or SATA 0 on your mobo.

My opinion: screw Dapper.  Breezy dealt with this stuff perfectly; why bother with a prematurely released distro upgrade?

therunnyman

---

### Post by lolke on 2006-06-04
[QUOTE=Al_maverick]Also, how can I find the new name for the drive? I upgraded using adept, I didnt download the livecd or the alternate cd. Now I am downloading it, but if there is a quick way to find how dapper is detecting my drive, I could change the grub boot command and the fstab now.
In breezy it was sda3. Ive tried sda1 to sda7, and sdb3, but no luck. I am downloading both CDs now, but it will take 2 days with my slow broadband access. Im back to XP for the moment :([/QUOTE]

In my case I got the busybox prompt when the mount failed. Then I ran "mount" and it showed that /dev/hda1 was mounted as /root. When I did an "ls /root" I recognized the layout of the disk as my old /dev/hde1.

I was able to boot into dapper with changing hda1 to hde1 in the grub boot menu. You can do this by hitting 'e' for edit on the kernel you want to boot. Then you see the line with "root=/dev/hda1" (or what ever your root device is) and then change it to the correct root device.

Lolke

---

### Post by lolke on 2006-06-04
[QUOTE=therunnyman]Ayuh, same problem here.  Here's what I know for certain: for whatever reason (probably udev), the SATA drives connected to a card (PCI Promise controller here) are mounted first, becoming sda and sdb.  

My opinion: screw Dapper.  Breezy dealt with this stuff perfectly; why bother with a prematurely released distro upgrade?
[/QUOTE]

Correct. It loads the external card first. This is a major issue. I was looking in the dapper bug reports and I've seen this particular being reported in April. Unbelievable that it has been fixed since.

I wish there was a quick way to go back to Breezy. But it looks like I'm stuck on Dapper for now. Won't upgrade my other boxes for sure.

Lolke

---

### Post by web250 on 2006-06-06
I can confirm this bug too. And someone before me filed a bug #46189
[https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/46189/+index](https://launchpad.net/distros/ubuntu/+source/linux-meta/+bug/46189/+index)

---

### Post by therunnyman on 2006-06-06
This is my personal favorite bug report..Confirmed!  Major!  And yet...

[https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/33649](https://launchpad.net/distros/ubuntu/+source/debian-installer/+bug/33649)

---

### Post by ubuntu_demon on 2006-06-07
from [http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656) :
**booting stalls during "mounting root filesystem"?**
[http://www.ubuntuforums.org/showpost...6&postcount=11](http://www.ubuntuforums.org/showpost...6&postcount=11)
[http://www.ubuntuforums.org/showpost...1&postcount=41](http://www.ubuntuforums.org/showpost...1&postcount=41)
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

---

### Post by derek_i on 2006-06-07
I chimed in on the second post experiencing the same problem so here is an update. In my case, Breezy was running fine but after the update to Dapper the machine wouldn't load with the error mentioned earlier. Booting from a tools CD, I checked the partition with badblocks and it was fried. I think all the disk activity from upgrading aggrevated a drive that was on the way out already.

I upgraded a VAIO that was setup the same way (this time just changed the sources list) and everything was flawless.

Very impressed by all the work that gone into Ubuntu...

-D

---

### Post by KenF on 2006-06-09
My problem:
[INDENT]The order of my drives gets reversed ... and ends up unable to "mount root filesystem".[/INDENT]

My solution: 
[INDENT]Add the string:  ide-reverse[/INDENT]
[INDENT]to the boot prompt.[/INDENT]

[One can add this interactively in GRUB (type e to edit.  Add  ide-reverse to the kernel line.  One can add it more permanently by editing /etc/boot/menu.lst]

Let me know if this helps!

Ken

---

### Post by KenF on 2006-06-09
I thought my solution had worked.  It turns out that it didn't  (I've tried adding "ide-reverse" and "ide=reverse".  I thought it worked, but it turns out that I probably just got lucky and my USB drive hadn't fully spun up).

Ken

---

### Post by MeneM on 2006-07-31
Hello All,

I almost have the same problem, it won't boot from /dev/hda2 (/dev/hda1 has windows on it, this is a dual boot).

During boot time, it will stop booting with the error message:
mount: Mounting /dev/hda2 on /root failed: No such device

But when I boot using the Livecd, the drive is most certainly recognised as being /dev/hda2 ???

Fun part: I reinstalled using my ordered live cd from shipit. Everything went ok, I reinstalled ubuntu, then upgrade wanted to do it's thing. I restarted (there was a new kernel update) anb boom! Same thing?!

So it's definitly in the upgrading where things go awry.

Thanks,
Mark

---

### Post by Davidp on 2007-02-16
I've been seeing this particular problem in many many Ubuntu forums.

People get this message on boot

mount; Mounting /dev/hda1 on root failed: No such device
mount; Mounting /root/dev on /dev/.static/dev failed : No such file or dir
mount; Mounting /sys on on /root/sys failed: No such file or dir
mount; Mounting /proc on /root/proc failed: No such file or dir
Target filesystem doesn't have /sbin/init

It happened to me and I solved it, not saying it will work for everyone.

Also I find that a lot of people replying to these problems seem to enjoy showing off their own ability and make it far too technical for us mere mortals to understand so I'm going to put how I solved this problem in 'laymans' terms for all those non techies, like me, out there

First boot using your live CD.

Then you need to mount your hd, so open a terminal and put in the following.

sudo mkdir /mnt/ubuntu
sudo mount /dev/hda1 /mnt/ubuntu. (in this case hda1 is whatever your hd is called)

Your hd should now be mounted.

Open Konqueror and look in 'storage media' click on the mounted hd.

click on  the 'boot' directory and here you will find a list of all the kernels you have  on your computer since you first  installed Ubuntu, they have titles such as config-2.6.15-23-386.

If you have lots of these say something like the following config-2.6.15-23-386.
config-2.6.15-24-386, config-2.6.15-25-386..config-2.6.15-26-386.config-2.6.15-27 -386. 2.6.15-28-386

It means that you have upgraded the Kernal more than once and the problem for me was that too many upgrades had caused a conflict the answer is to remove all of them except the first one, in this case config-2.6.15-23-386. and then to reinstall just the last one, in this case config-2.6.15-28-386. 

To remove all of the unwanted ones do this.

In the consul type the following

sudo chroot /mnt/ubuntu.

then this

 apt-get update (I'm assuming you have an internet connection)

Wait for the packages list to download and  then do this

apt-get uninstall linux-image-2.6.15-28-386.  Here you need to select the most recent version of the kernel,in this example its version 28.

Repeat this with each of the installed kernels

apt-get uninstall linux-image-2.6.15-27-386.  then 26 then 25. then 24

DO NOT, REPEAT, DO NOT UNINSTALL THE FIRST VERSION YOU HAVE, IN THIS EXAMPLE 2.6.15-23-386

Finally, were nearly there!  put in this.

apt-get install linux-image-2.6.15-28-386.  where the image is the latest version of the kernel, at the time of writing its 2.6.15-28-386.

You should now have a clean install of the latest version of the Kernel, it should solve your problem but if it doesn't don't loose heart, mess around with some of the above your computer may be different to mine.  For example after deleting all of them  try installing one of the older versions or even just leaving the first one in place

Good Luck, it took me two days to work this out!

---

### Post by momeara on 2007-03-26
I had the same problem and your solution worked perfectly for me.

Thanks!

m

---

### Post by Exothermicus on 2007-04-04
I found this thread, because I have the same IDE device order problem.  In my case I have the wrong device order, even for my live-CD's. I have tried several flavors.  One thread I found seemed to think it was an issue with the  PCI device numbers being lower for the add-on card than what was assigned to the on-board controllers.  I'll have to check my lspci when I get home to verify this is the case on my system or not.

I'm building this as a new system, so I can reasonably work around the device order.  All of the 2.6.x live CD's I have tried seem to load the devices in the wrong order, but some distro&#8217;s have problems mapping the DMA and interrupts properly because of this strange order.

My configuration is an ECS K8M800 V2.0 MoBo, with two SIL0680 PCI raid cards.  I have 9 hard drives: five 250 GB and four 500 GB, one of the 250's is attached as the MoBo primary (secondary?) master, the other four are on the first card, and the 500's are on the second.  The drive attached to the MoBo controller is recognized last as /dev/hdk (looks like    I have the drive on the secondary instead of the primary controller).  The other four 250's are hda-hdd, and the 500's are hde-hdh.

I had previously used the 4 250's in different system where I was running Gentoo 2006.0, attempting to boot it results in the: "unable to find root error".  Editing the grub command line from root=/dev/hde2 to /dev/hda2, seems to allow it to get farther into the boot, but since I custom built the kernel for the older MoBo, it fails a little farther up the food chain.

I have verified that non-Linux disk utilities properly assign the drives in the natural expected order, but Linux is doing its own thing.  If I find that my PCI device addresses are not out of whack, then it is likely an issue with the order the generic-IDE driver loads the chipset specific drivers (Via comes after SIL etc,...).  I can probably solve the issue by building a custom kernel and leaving the SIL0680 module for later loading, but that will not fix the live-CD's.

I had the SIL0680 cards in the system on first boot; I have tried clearing the BIOS ESCD data, but have not removed the cards when doing this.  I can try that once the system finishes the burn-in tests it is currently running on the 500GB drives.

<Edit>
Additional Information:

I have another system using a similar configuration, but with an ECS 755-A2 that uses the SIS 755 northbridge instead of the VIA chipset.  This system has 4 additional hard drives attached using one of the SIL0680 cards; this system does not have any problems with the IDE channels loading in the wrong order.   Only the chipsets are different.

One thought I had, is that the 755-A2 MoBo did not have integrated graphics, where the K8M800 does.  I wonder if the setting to force a PCI video card to take precedence over the on-board video would have any bearing on the precedence of the IDE devices, but as I said Dos and windows based drive utility tools show the devices in the expected order.   My burn-in testing will take another day or so before I can try anything on the problem system.  I have all pseudo tty's tied up until then.
</edit>

Exo

---

