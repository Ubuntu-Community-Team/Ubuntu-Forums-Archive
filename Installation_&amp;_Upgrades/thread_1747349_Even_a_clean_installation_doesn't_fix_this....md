---
title: "Even a clean installation doesn't fix this..."
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by Dbzdude707 on 2011-05-02
Yeah, so I upgraded to 11.04 yesterday. Unity worked, but a bunch of other things seemed to be messing up. The interface was very new, so I wasn't sure whether certain things (like for example, the complete lack of the firefox button in firefox 4 no matter what I did) were supposed to happen. Then I tried to reorder the grub boot menu options and that only served to make things more glitchy, not to mention it didn't work.

I just decided to do a clean installation. Now, I have a few more problems.

First of all, when I'm booting up my computer, as it's loading Ubuntu I get some error like "the disk drive for _______ cryptswap is not available." I don't know exactly what goes in the blank, the error does not display long enough for me to get a good look at it.

Next, whenever I open GParted, what is supposed to be my swap partition has a red ! mark symbol next to it and says unknown.

Finally, Unity does not work despite the fact that my computer is perfectly capable of running it (it ran fine when I upgraded from 10.10 and again when I ran 11.04 from the installation CD). I'm thinking that it's likely that this is because of the first two problems.

It should be noted that I am trying to actually assign the proper partitions for Ubuntu manually. That is, when it gives me the 3 options like "install it alongside your other OS" "wipe everything and install it by itself" and "choose partitions manually"... I choose the last option. The reason is because I already have free space set apart that I want to install Ubuntu on. However, when I setup a ext4 partition and a swap partition, it will give me no errors and proceed on just fine. I only find out about these errors after I've already finished the installation.

I've done a clean installation twice now, and I just can't get rid of all of these problems. I know I'm too much of a newbie to handle this process, but please help.

---

### Post by weedwacker on 2011-05-02
What do you mean by "The reason is because I already have free space set apart that I want to install Ubuntu on."?

Are you wanting to run a dual-boot system?

If you are, there are some very good bits of information online that explain how best to set up dual-boot.

Google is great for: "Ubuntu - how to set up dual-boot."

---

### Post by wilee-nilee on 2011-05-02
Post a screen shot of gparted, use the paper clip in the reply panel to upload it and place it in a reply.

---

### Post by Dbzdude707 on 2011-05-02
> **weedwacker said:**
> What do you mean by "The reason is because I already have free space set apart that I want to install Ubuntu on."?

Are you wanting to run a dual-boot system?

If you are, there are some very good bits of information online that explain how best to set up dual-boot.

Google is great for: "Ubuntu - how to set up dual-boot."

What I meant is that I have an area on my HDD that is not partitioned, it's free space. I want to use that for Ubuntu. The rest is taken up by Windows, and I don't want to mess with that. So yes, I want to dual boot.

Well, on the Ubuntu help site, it describes the process in question like this:
> Create a swap partition of at least your amount of RAM (if you don't know, 2000 MB is a good value).
Create a partition for your Ubuntu installation.

My swap partition was already more than my amount of RAM. I have 4 GB of RAM. It doesn't tell me anything...

---

### Post by Dbzdude707 on 2011-05-02
> **wilee-nilee said:**
> Post a screen shot of gparted, use the paper clip in the reply panel to upload it and place it in a reply.

Sorry if this turns out to be a double post, but I did not see your reply until after I made the previous post.

---

### Post by wilee-nilee on 2011-05-02
> **Dbzdude707 said:**
> Sorry if this turns out to be a double post, but I did not see your reply until after I made the previous post.

So that is your main HD or one of them, I see the W7 boot and C partition sad1 and sda2, and a sda5 linux and the firmware sda3.

> Finally, Unity does not work despite the fact that my computer is perfectly capable of running it 

It is difficult to tell where you are at, can you actually boot into natty at this time?

The swap can just be deleted and a new one made with gparted. Can we confirm that the sda5 is the Natty, and that you are not trying to install on another HD, that I would need a picture of as well.

I also see no free space that is why I ask some of these questions.

Also note that you have 3 primary partitions, and one extended, the only option you have that will not brick your computer is install Linux inside the extended=sda4. 3 primaries and a extended is the HD limit.

---

### Post by Dutch70 on 2011-05-02
If you right click the swap partition in Gparted & select information, it may tell you what the problem with it is. 

If I understand you correctly, it's working but you have problems with unity or maybe your graphics card???

---

### Post by Dbzdude707 on 2011-05-02
> **wilee-nilee said:**
> So that is your main HD or one of them, I see the W7 boot and C partition sad1 and sda2, and a sda5 linux and the firmware sda3.



It is difficult to tell where you are at, can you actually boot into natty at this time?

The swap can just be deleted and a new one made with gparted. Can we confirm that the sda5 is the Natty, and that you are not trying to install on another HD, that I would need a picture of as well.

Yes, sda5 is Natty, and that is the only HD being used right now.

I can boot into Natty, but it gives me the errors I stated above and refuses to load Unity.

I tried to delete it and make a new swap earlier, that made grub have a fit. I don't remember exactly what it said anymore, but it wouldn't load a thing.

So yes, you can confirm everything you said there at the end of that post.

@Dutch70: You're correct, except that it does not tell me what the problem with it is. I already tried that.

---

### Post by Dutch70 on 2011-05-02
I don't know why deleting your swap partition would cause Grub2 any problems. Unless you're referring to the...
> "the disk drive for _______ [COLOR="Red"]cryptswap[/COLOR] is not available."
message that you got. To fix that, just need to edit your fstab after you recreate your swap partition.

[COLOR="Red"]It looks like you encrypted your swap partition.[/COLOR]

---

### Post by wilee-nilee on 2011-05-02
Dutch70 I have a college financial aid crisis I'm dealing with while doing this, so carry on with your always awesome help.;)

---

### Post by Dutch70 on 2011-05-02
> **wilee-nilee said:**
> Dutch70 I have a college financial aid crisis I'm dealing with while doing this, so carry on with your always awesome help.;)

Well thank you wilee-nilee, but I have one question if you get a chance. 

Could Grub malfunction when the OP deletes his swap partition due to it being encrypted? 
Possibly tied to / through the encryption or something?  
I can't think of any other reason.

---

### Post by wilee-nilee on 2011-05-02
> **Dutch70 said:**
> Well thank you wilee-nilee, but I have one question if you get a chance. 

Could Grub malfunction when the OP deletes his swap partition due to it being encrypted? 
Possibly tied to / through the encryption or something?  
I can't think of any other reason.

I have had a grub boot problem that was fixed by a delete and rebuild of swap, could not boot in or load grub to boot had to use a supergrub2 disc to get in. Anything encrypted though shouldn't block a partitioner from removing it as far as I know, which has its limitations lol.

I suspect that this is graphics driver for some problems, **which if we only actually new what they were would be quite helpful.**

The swap being a problem maybe just trying to delete a partition that is partially mounted although not showing the key=mounted in gparted. I would rm the partition I forget the commands though.

The op probably has left the swap in place with all of these installs, it may have been encrypted,as part of the original setup. While doing this they also may have built the sda5 to large and made the swap go unallocated, I don't know all the errors so it seems logical to assume the swap was encrypted, again here more info needed.

---

### Post by Dbzdude707 on 2011-05-02
> **Dutch70 said:**
> I don't know why deleting your swap partition would cause Grub2 any problems. Unless you're referring to the...

message that you got. To fix that, just need to edit your fstab after you recreate your swap partition.

[COLOR="Red"]It looks like you encrypted your swap partition.[/COLOR]

What I did with the swap partition that time was precisely this.
1. Tried to delete it from GParted, found out that was impossible because despite being somehow corrupted it was still mounted.
2. Used the Ubuntu installation CD to "Try Ubuntu" and use GParted from there.
3. Deleted the swap, made a new one.
4. The next time I tried to boot up my system, grub would not load a thing. Sorry, I've forgotten the error message. I could try to reproduce the error but that would mean I would be unable to load anything without using the ubuntu disk again.

Sorry though, I don't know what you refer to when you say "fstab." Also, it would not make sense for me to have encrypted my swap. Assuming that the encryption of that partition is the cause for the error, anyway. Because I have not personally done a thing to the swap partition. GParted made a standard swap partition and after that anything that happened to it was the work of the installer. It would not make sense for it to give me an error for something that it did to the partition automatically as part of the installation. This is a stable release as far as I'm aware, and this has happened all 3 times I've tried a clean installation now...

> **wilee-nilee said:**
> I have had a grub boot problem that was fixed by a delete and rebuild of swap, could not boot in or load grub to boot had to use a supergrub2 disc to get in. Anything encrypted though shouldn't block a partitioner from removing it as far as I know, which has its limitations lol.

I suspect that this is graphics driver for some problems, **which if we only actually new what they were would be quite helpful.**

The swap being a problem maybe just trying to delete a partition that is partially mounted although not showing the key=mounted in gparted. I would rm the partition I forget the commands though.

The op probably has left the swap in place with all of these installs, it may have been encrypted,as part of the original setup. While doing this they also may have built the sda5 to large and made the swap go unallocated, I don't know all the errors so it seems logical to assume the swap was encrypted, again here more info needed.

I will get the graphics driver information for you in a moment if I can find it. Usually however it does not enable the driver by default in a clean installation of Ubuntu, so I was not aware that would have been an issue here.

I can assure you however that I delete both the sda5 and swap partitions and make them anew each time I do a clean installation.

The third time I did the partitions for a clean installation, I followed the instructions on this page:
[https://help.ubuntu.com/8.04/switching/installing-partitioning.html](https://help.ubuntu.com/8.04/switching/installing-partitioning.html)
Granted, it's an old help file, but nevertheless I got the same errors upon finishing the installation.

---

### Post by Dbzdude707 on 2011-05-02
Update. This time, the graphics driver was automatically enabled from the start. For some reason, when I enabled it in 10.10, it made it so that Ubuntu would not even boot up the next time I started my computer. Grub would load and everything, but then I selected Ubuntu, and it would just freeze after it tried to load the login screen for a while.

Naturally, because of that experience I'm rather surprised they would enable this thing from the start.

I have the information for you, I think. It was hard to find it, but I think this is what you wanted.

nVidia Corporation GT218 [GeForce 310M]

---

### Post by Dutch70 on 2011-05-02
While we wait for wilee-nilee to get back, please post the output of...
```
sudo fdisk -lu
```
That's a lower case L before the u.

Also, please post the output of...
```
gksudo gedit /etc/fstab
```

Please paste the info between [CODE][ /CODE] tags by clicking the # symbol in the tool bar.

I hate to ask stupid questions, but I just want to clarify that you did click the dropdown box & format the swap partition to "swap" right? 
Where it says file system "unknown" it should say "linux-swap"

That guide you used is quite old. For example, the size of your swap doesn't really need to be twice the size of your RAM. That was recommended back when most people had less than 1GB of RAM. Now it just needs to be equal to your RAM & 1GB is the recommended minimum to even install Ubuntu.

---

### Post by Dbzdude707 on 2011-05-02
> **Dutch70 said:**
> While we wait for wilee-nilee to get back, please post the output of...
```
sudo fdisk -lu
```
That's a lower case L before the u.

Also, please post the output of...
```
gksudo gedit /etc/fstab
```

Please paste the info between ```
[ /CODE] tags by clicking the # symbol in the tool bar.

I hate to ask stupid questions, but I just want to clarify that you did click the dropdown box & format the swap partition to "swap" right? 
Where it says file system "unknown" it should say "linux-swap"

That guide you used is quite old. For example, the size of your swap doesn't really need to be twice the size of your RAM. That was recommended back when most people had less than 1GB of RAM. Now it just needs to be equal to your RAM & 1GB is the recommended minimum to even install Ubuntu.

Actually, this should be closer to what the error says:
> the device for /dev/mapper/cryptswap1 is not ready yet or present

Here's the output for the first one.

[code]Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xe56e3d6c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048     3074047     1536000   27  Unknown
/dev/sda2   *     3074048   784324047   390625000    7  HPFS/NTFS
/dev/sda3       954488832   976773119    11142144   17  Hidden HPFS/NTFS
/dev/sda4       784324606   954488831    85082113    5  Extended
/dev/sda5       938348544   954488831     8070144   82  Linux swap / Solaris
/dev/sda6       784324608   938346495    77010944   83  Linux

Partition table entries are not in disk order

Disk /dev/dm-0: 8263 MB, 8263827456 bytes
255 heads, 63 sectors/track, 1004 cylinders, total 16140288 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x522508ac

Disk /dev/dm-0 doesn't contain a valid partition table
```

Here is the output of the second one:

```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=5b324085-0038-4e91-bdfc-8e4a9d58baf0 /               ext3    errors=remount-ro 0       1
#/dev/sda5       none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0
```

As for your question, that's what I did the first time when it was giving me the mounted error. The second time, when I was doing it from the CD, I actually deleted the unknown partition and made a new linux-swap partition in its place.

...I can see how that gave me the error, now that I think about it.

---

### Post by wilee-nilee on 2011-05-02
So here is the command that will identify the video card in the terminal.
lspci | grep VGA

So it sounds like the swap situation is covered although, the stanza looks different then mine is your set up encrypted, anywhere. Super important info at least for me, I have to know when to stop helping, if it is beyond my knowledge, my general idea is do no harm here. The closet I come to understanding any encryption is being able to use truecrypt on a external media, that is it. 

Found this general info on this. 
[http://ubuntuforums.org/showthread.php?t=1365261](http://ubuntuforums.org/showthread.php?t=1365261)

So Op I'm assuming that you have just run a plain 
sudo update-grub 
from the Ubuntu install, after rebuilding the swap and have rebooted, to see if your regular boot in is good.

And now we are basically at the other problems hopefully ;) with natty, which if you can share with us what they actually are if graphics orientated like screen resolution etc or if you know you need a driver.

And whether you have looked at the additional drivers area in the menu.

To some extent at least for me I need a bit of a synopsis of where your at, what you have, and what you need still.

But I'm reading about a 100 pages of a book and getting ready to write a paper and waiting for a call on the financial aid, life could be more hectic I guess I'm not sure how though short of a death lol. I laugh because at this point that is all I can do.

---

### Post by Dutch70 on 2011-05-02
Edit: I don't think deleting & recreating his swap partition fixed it wilee-nilee.

I'm sorry to say...This just went over my head. I know nothing about encryption. I can tell you that if you encrypted your home directory on 10.04 and up. It will automatically encrypt your swap partition also. 

Look under caveats at the bottom.
[[COLOR="RoyalBlue"]https://help.ubuntu.com/community/EncryptedHome[/COLOR]]("https://help.ubuntu.com/community/EncryptedHome")
[[COLOR="RoyalBlue"]https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459985[/COLOR]]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/459985") Not that I think it's a bug, but maybe there is something useful there.

---

### Post by Dbzdude707 on 2011-05-02
Here's the output for the lspci command:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
```
I doubt the swap situation is covered, as it still only says that the partition is "unknown." I'll try the "format to" thing from the Ubuntu CD this time though, and do the sudo update-grub after that.

I honestly still don't know whether or not it's encrypted. I'm still reading the information from the link you gave though, so I'll see if that helps.

For the additional drivers area, that's where I looked to find out that the graphics driver in question is activated. It's not in use though, apparently.

Also I did in fact tell it to encrypt my home directory, I didn't think that would make it encrypt the swap partition as well but if that's the case then thanks for telling me.

---

### Post by wilee-nilee on 2011-05-02
> **Dbzdude707 said:**
> Here's the output for the lspci command:
```
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
```
I doubt the swap situation is covered, as it still only says that the partition is "unknown." I'll try the "format to" thing from the Ubuntu CD this time though, and do the sudo update-grub after that.

I honestly still don't know whether or not it's encrypted. I'm still reading the information from the link you gave though, so I'll see if that helps.

For the additional drivers area, that's where I looked to find out that the graphics driver in question is activated. It's not in use though, apparently.

Also I did in fact tell it to encrypt my home directory, I didn't think that would make it encrypt the swap partition as well but if that's the case then thanks for telling me.

Okay so I know nothing about encryption, heck it may be supposed to read that way for the swap I have know idea.

You might send a message to the mods, in that having a thread with a more specific header would help, bring in the people who know. Or even a new thread.

Do you really need encryption?

I ask this as help in this area I doubt will be fast or soon I hope so but from my time on the forums, and a whole lotta beans, history does not show a lot of users with expertise in this area. Or we all realize that it is a waste of time unless you really needed it.

Best of luck here I have to take care of my own business.

---

### Post by Dbzdude707 on 2011-05-02
The encryption error is fixed now, and the swap shows up correctly in GParted.

However, Unity still will not work on my computer... I'm not very good with hardware so I really don't know if it's capable of running it or not. However, it ran when I upgraded from 10.10 and it also ran when I booted Ubuntu from the install disk. That means it's capable of running it right?

Well, I ran lspci and here's the output, if that will help you guys tell whether or not it would be possible to run Unity:

```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
01:00.0 VGA compatible controller: nVidia Corporation GT218 [GeForce 310M] (rev a2)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
07:00.0 Network controller: Intel Corporation Centrino Advanced-N + WiMAX 6250 (rev 57)
16:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller (rev 20)
16:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (rev 20)
16:00.3 System peripheral: JMicron Technology Corp. MS Host Controller (rev 20)
16:00.4 System peripheral: JMicron Technology Corp. xD Host Controller (rev 20)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 05)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 05)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 05)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 05)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 05)
```

Thanks for all the help so far!

---

### Post by Blasphemist on 2011-05-02
This is supposed to test unity capability, run
```
/usr/lib/nux/unity_support_test -p
```

---

### Post by 3177 on 2011-05-02
I would seriously consider downloading a new copy of 11.04 and a new cd.
Or buy a copy from canonical.
Then re install WITH updates(need internet). 
After that it should be fine.

---

### Post by Dbzdude707 on 2011-05-02
> **3177 said:**
> I would seriously consider downloading a new copy of 11.04 and a new cd.
Or buy a copy from canonical.
Then re install WITH updates(need internet). 
After that it should be fine.

The errors in question are fixed already. And what you just said is exactly what I did, 3 times. It didn't work. The problem was that I had told it to encrypt my home folder. The problem now is that it doesn't want to run Unity and I'm not sure if it's even possible to.

> **Blasphemist said:**
> This is supposed to test unity capability, run
```
/usr/lib/nux/unity_support_test -p
```
Here is the output I got for that:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```

---

### Post by 3177 on 2011-05-02
First off, please don't get snippy with me, Im trying to help you.
Secondly,I would recomend going back to 10.10 or even better 10.04.3.
Judging by your specs unity is not going to work for you.

---

### Post by Dbzdude707 on 2011-05-02
> **3177 said:**
> First off, please don't get snippy with me, Im trying to help you.
Secondly,I would recomend going back to 10.10 or even better 10.04.3.
Judging by your specs unity is not going to work for you.

Sorry, I wasn't intending to be snippy. I do appreciate the help.

Well, the classic interface works fine, I just wanted to know if it was possible to get the new one to work. If not though, I can deal with that.

---

### Post by 3177 on 2011-05-02
> **Dbzdude707 said:**
> 
Well, the classic interface works fine, I just wanted to know if it was possible to get the new one to work. If not though, I can deal with that.
  
I would personally install 10.04.3 if I were you.
Advantages:Everything works that you want
Disadvantages: No unity(not a bad thing)

---

### Post by Blasphemist on 2011-05-02
> **Dbzdude707 said:**
> The errors in question are fixed already. And what you just said is exactly what I did, 3 times. It didn't work. The problem was that I had told it to encrypt my home folder. The problem now is that it doesn't want to run Unity and I'm not sure if it's even possible to.


Here is the output I got for that:

```
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: unable to create the OpenGL context
```

Have you got an embedded gpu and a nvidia? One of your previous posts makes me think maybe you do. Does your bios allow you to turn off the embedded? Or are you running dual head?

Your nvidia may have a bug but I haven't followed it all the way. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/775459](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/775459)

In additional drivers does nvidia show up? At least I think you can get to that.

---

### Post by Blasphemist on 2011-05-02
Just found this.

> Re: Laptop COMPATABILITY List.
UBUNTU 11.04 & KUBUNTU 11.04

Laptop TOSHIBA SATELLITE M645-S4050
PROCESSOR: Intel Core I5-450M 2.40 GHz, 3MB Cache
MEMORY: 4 GB DDR3
HARD DISK: 500 GB SATA (internal), 40 GB (external USB)
CHIPSET: Mobile Intel® HM55 Express Chipset
GRAPHICS: NVIDIA® GeForce® 310M with NVIDIA® Optimus™ Technology
and Intel Integrated Graphics
DISPLAY: 14.0" @ 1366x768 px
NETWORKING: 10/100 Ethernet & Intel® Centrino® Advanced-N +
WiMax 6250
BATTERY: 12 cell/98Wh Lithium Ion battery pack

Almost everything worked out of the box from a new installation. Both systems were tried from an USB external hard disk install.


What didn't work: NVIDIA OPTIMUS switching (can't use the nvidia video card), but so far the performance of the Intel video card has been good.

From, [http://ubuntuforums.org/showthread.php?p=10754894](http://ubuntuforums.org/showthread.php?p=10754894) Laptop compatibility list. Just saying, I'll keep looking.

---

### Post by Dbzdude707 on 2011-05-02
> **Blasphemist said:**
> Have you got an embedded gpu and a nvidia? One of your previous posts makes me think maybe you do. Does your bios allow you to turn off the embedded? Or are you running dual head?

Your nvidia may have a bug but I haven't followed it all the way. [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/775459](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers/+bug/775459)

In additional drivers does nvidia show up? At least I think you can get to that.

That certainly appears to be the case, though I do not know how to turn off the embedded one.

Nvidia does show up under Additional Drivers and the driver in question there is activated, however it says it's not in use.

It may be worthy of note that if I select this:
System -> Administration -> NVIDIA X Server Settings
It will give me the following error:
> You do not appear to be using the NVIDIA X driver. Please edit your X configuration file (just run 'nvidia-xconfig' as root), and restart the X server.

I do as it tells me, running that command as root, and it gives me this:
> Using X configuration file: "/etc/X11/xorg.conf".
Backed up file '/etc/X11/xorg.conf' as '/etc/X11/xorg.conf.backup'
New X configuration file written to '/etc/X11/xorg.conf'

So far so good, but then I select the Server Settings thing again and it gives me the same error.

---

### Post by Blasphemist on 2011-05-02
I think it is a good thing you're not using the nvidia from what I can tell. See my previous post from the compatibility list.

I'd say why go back to 10.4 as was recommended? Stay here, use classic if needed and work on getting unity going. I think you need to kill nvidia in whatever is the appropriate way. I'll look into that over dinner. You should too. I'm using this for searches, keeps the results focused.

[http://www.googlubuntu.com/](http://www.googlubuntu.com/)

---

### Post by Dbzdude707 on 2011-05-02
...Well, I don't know about downgrading. It's just, I'd like to stick with the latest stable release at all times, if possible. I have OCD like that.

There's a new error now. All I've done since the most recent clean installation of Ubuntu 11.04 (this time telling it not to encrypt the home folder, so the errors regarding encryption and swap are gone) is...
-Ran the nvidia command I mentioned a moment ago.
-installed a few things: Pidgin, Chromium, VLC, Wine, GParted. I did not add any new repositories. These are from sources that came with Ubuntu.
-customized firefox by installing several add-ons

I think that's about it. None of this should cause it to fail to properly log off or start up Ubuntu. It will take me to a black screen where it starts going through all these commands and a [OK] will pop up at the right of each one. Ok, that's normal, but it seems to have a problem with something called System V: That was the last command it showed before refusing to proceed to the login screen when I tried to log out earlier. There was an [OK] after it, but it wouldn't do anything else, so... And, it said it was trying to send a crash report when I started it up next and it gave a [fail] for that if I remember right. When I try to start Ubuntu up, the last thing it will do on the black screen is something about battery settings and it will give an [OK] on that too but from there on it won't do anything else again. It should be noted that my computer doesn't freeze when I do this, as I can move to another line with the enter key and more commands will pop up when I press the power button to shut the computer down. It appears to shut down properly. It just can't handle the login screen.

This is not the same error I got when enabling my graphics driver in 10.10. When I did that, it would just stay at the 4 animating dots for a while upon trying to load Ubuntu and then finally freeze. I no longer have this issue because I'm not using 10.10 anymore and I never activated my graphics driver again after that when I was, but I just thought this was relevant information.

---

### Post by Blasphemist on 2011-05-02
It would be helpful if we knew how to disable the nvidia drivers. 

[http://ubuntuforums.org/showthread.php?p=10755617](http://ubuntuforums.org/showthread.php?p=10755617)

I'm looking for that.

---

### Post by 3177 on 2011-05-02
> **Dbzdude707 said:**
> ...Well, I don't know about downgrading. It's just, I'd like to stick with the latest stable release at all times, if possible. I have OCD like that.


well.... 10.04 IS the stable release.

---

### Post by Blasphemist on 2011-05-02
I found this, it may help.

> Install Latest Nvidia/ATI drivers
Ubuntu uses a GUI frontend to Jockey for the installation of the proprietary nVidia drivers (and other proprietary drivers).
Menu -> System -> Hardware Drivers
Sometimes after a kernel upgrade a proprietary driver may stop working. In such a case, try installing the new linux-headers that match the newly upgraded kernel:
sudo apt-get install linux-headers-$(uname -r)
If dkms and build-essential have never been installed on your system, these can also be worthwhile:
sudo apt-get install dkms build-essential


It came from this.

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Natty#Installation_of_ATI_and_nVidia_Graphics_drivers)

---

### Post by Blasphemist on 2011-05-02
Here is what I started looking for, right or not.

> What if I already installed the Restricted Driver, and now my computer is not booting X?
1. Boot into Recovery mode (GRUB). Start failsafe-X.
2. When you're in, go to System > Administration > Additional Drivers to deactivate the nVidia driver.
3. Move Xorg:
Code:
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
4. Reboot. Intel card should kick in.
-------

And look at this.

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

---

### Post by wilee-nilee on 2011-05-02
> **3177 said:**
> well.... 10.04 IS the stable release.

So is arch linux let it go.

---

### Post by Dbzdude707 on 2011-05-03
> **3177 said:**
> well.... 10.04 IS the stable release.

...I didn't tell it to install beta releases though. 11.04 is considered stable, isn't it? They even have it recommended for download on the ubuntu downloads page. I'm pretty sure they don't put beta releases there... Though I guess I don't know much about this.

> **Blasphemist said:**
> Here is what I started looking for, right or not.

And look at this.

[http://ubuntuforums.org/showthread.php?t=1657660](http://ubuntuforums.org/showthread.php?t=1657660)

Whoa, not only does it boot up correctly now but unity works. It was all the cause of a faulty driver, I guess. I wonder why it would be put in and enabled by default if it tends to fail like this (since it failed last time too...).

> **Blasphemist said:**
> I found this, it may help.

It came from this.

[http://ubuntuguide.org/wiki/Ubuntu:Natty#Installation_of_ATI_and_nVidia_Graphics_drivers](http://ubuntuguide.org/wiki/Ubuntu:Natty#Installation_of_ATI_and_nVidia_Graphics_drivers)

Do you still want me to try looking into this? I don't know that there would be a need for that now that it all seems to be working.

---

### Post by Blasphemist on 2011-05-03
> **Dbzdude707 said:**
> ...I didn't tell it to install beta releases though. 11.04 is considered stable, isn't it? They even have it recommended for download on the ubuntu downloads page. I'm pretty sure they don't put beta releases there... Though I guess I don't know much about this.



Whoa, not only does it boot up correctly now but unity works. It was all the cause of a faulty driver, I guess. I wonder why it would be put in and enabled by default if it tends to fail like this (since it failed last time too...).



Do you still want me to try looking into this? I don't know that there would be a need for that now that it all seems to be working.

This thread is a good example. Even a couple of bad issues can be solved by sticking with it and getting help. For what I helped with, neither of us really knew enough to start with but we got there. We didn't back off and think this is to tough for us. We didn't see a related bug and give up.

As to your last question, no, don't break it right now while it's working. Do watch for any solutions that you think can improve things but research first. And update the bugs with your success and the reason. Not everyone has the intel to fall back on.

---

