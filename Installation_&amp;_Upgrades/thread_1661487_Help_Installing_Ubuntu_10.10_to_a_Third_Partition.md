---
title: "Help Installing Ubuntu 10.10 to a Third Partition"
date: 2011-01-06
forum: Installation &amp; Upgrades
---

### Post by AVARiCE91 on 2011-01-06
Hi guys, this is my first post so please accept my apologies if I've put it in the wrong area. I've read the rules but you can never be too sure!
 
Basically, I've been using Ubuntu 10.10 on a LiveCD on and off (I'd say about twice a month) since it first came out. My laptop crashed (because of Vista) on Tuesday night and I decided that while Vista's still my main OS I need to start using Ubuntu more. Ideally, when I build my new PC later this year I want it to be solely Ubuntu.
 
Anyway, I digress.
 
My harddrive has 290GB of space and I've currently got two partitions on it. I've got the OS and programs installed on C:. Once I've started to repopulate (seeing as I've just reformatted), I want to put my user directory on D:. I've used Vista's partition manager to make C: 127.19GB and D: 117.19GB, with an unallocated space at the end of 53.71GB.
 
I want to install Ubuntu 10.10 on the currently unallocated partition. The questions I want to ask, really, are:
 
1) Is that too small a space?
2) As D: is empty, the automatic LiveCD installer chooses D: but I don't want it to install there, so how can I set it to install to the unallocated space?
3) I did a search and there were mentions to Ubuntu's inabitility to install to unallocated space, is this true? If so, should I just format the currently unallocated space to allow Ubuntu to install there?
 
Questions 2 and 3 can basically both be answered together but in essence, if I can't set Ubuntu to automatically detect and install to the unallocated space, how can I go about doing it manually? A search shows up lots of primary and logical spaces but I don't want to mess around.
 
I have no important information on C: right now seeing as it's just been reformatted so I'm more than happy to start from the very beginning or try things which will need a Windows reinstall.
 
Thanks in advance, I hope I've been relatively clear in what I need help with!

---

### Post by kansasnoob on 2011-01-06
Using the Ubuntu Live CD post the output of:

```
sudo parted -l
```

BTW that's a lower case L at the end.

---

### Post by Quackers on 2011-01-06
50GB plus, is plenty of space for Ubuntu, but obviously, it depends how much you want to put on there :-)
The 10.10 installer does not have the "install to largest free space" optionm, which is a shame. The "install alongside" option should be avoided AT ALL COSTS, as it has a propensity for over-writing existing operating systems.
Which leaves the "specify manually" option, which is the one for you :-)
I don't think it is likely to apply with Vista, but you should make sure that no more than 3 primary partitions are in use on the hard drive before you install Ubuntu.
Having made sure of the above, you can make your own partitions for Ubuntu (/root, swap, and /home (if required)) using the 10.10 installer partitioning screen. You need to double click on the unallocated space shown, then create your 2 or 3 partitions (probably within an extended partition).

---

### Post by AVARiCE91 on 2011-01-06
> **kansasnoob said:**
> Using the Ubuntu Live CD post the output of:
 
```
sudo parted -l
```
 
BTW that's a lower case L at the end.
 
I think I'm a bigger newb than you think. That's for the command-line, right? If so, I'll post it up in the morning.
 
> **Quackers said:**
> 50GB plus, is plenty of space for Ubuntu, but obviously, it depends how much you want to put on there :-) [1]
The 10.10 installer does not have the "install to largest free space" optionm, which is a shame. The "install alongside" option should be avoided AT ALL COSTS, as it has a propensity for over-writing existing operating systems.[2]
Which leaves the "specify manually" option, which is the one for you :-)[3]
I don't think it is likely to apply with Vista, but you should make sure that no more than 3 primary partitions are in use on the hard drive before you install Ubuntu.[4]
Having made sure of the above, you can make your own partitions for Ubuntu (/root, swap, and /home (if required)) using the 10.10 installer partitioning screen. You need to double click on the unallocated space shown, then create your 2 or 3 partitions (probably within an extended partition).[5]
 
[1] Thanks for that. :)
[2] I've already used that and it simply installed Linux to D:. Vista was fine on C: so it hasn't caused any trouble but it wasn't what I wanted. To be honest, I don't mind if Vista's overwritten because it's a fresh install anyway. Thank you for the warning though!
[3] Yup, I've seen it but it baffles me, it's an advanced option and I'm a bit of a newb when it comes to Linux in general, let alone Ubuntu.
[4] There aren't. I'm also in the midst of formatting the unallocated space, leaving me with C:, D: and the 53GB which I'm listing as A:.
[5] Thanks for that and apologies for using up more of your time but how do I go about doing that? From what I understand, I need to use the space (which I'll now refer to as A:) to create a Primary partition for /root, a logical partition for swap and another primary for home, right? Do I need to do it in any particular order? How much space should I give each one? How will I know it /home's required? So many questions! Thank you very much for your time though, I appreciate it.
 
Thanks again guys.

---

### Post by Quackers on 2011-01-06
I personally leave the space as unallocated, then create partitions in the installer using that free space. It is confusing to use terms like A:, C: etc as Linux refers to partitions as sda1 or sda2 (sda being the first hard drive, and sda1 being the first partition on that hard drive). 
How much ram is in your machine?
Do you intend using hibernate?
Do you want a separate /home partition or just a standard /root partition containing all Ubuntu files and settings?
Some say that a separate /home partition is beneficial when it comes time to upgrade or re-install (leaving your configuration settings and personal files untouched). Although it's not quite as clear-cut as that in that some configs and settings may not suit the newer system.

---

### Post by AVARiCE91 on 2011-01-06
> **Quackers said:**
> I personally leave the space as unallocated, then create partitions in the installer using that free space. It is confusing to use terms like A:, C: etc as Linux refers to partitions as sda1 or sda2 (sda being the first hard drive, and sda1 being the first partition on that hard drive). [1]
How much ram is in your machine?[2]
Do you intend using hibernate?[3]
Do you want a separate /home partition or just a standard /root partition containing all Ubuntu files and settings?[4]
Some say that a separate /home partition is beneficial when it comes time to upgrade or re-install (leaving your configuration settings and personal files untouched). Although it's not quite as clear-cut as that in that some configs and settings may not suit the newer system.[5]
 
[1] Ah, once again, thank you for the expertise. I'll start using that system then. sda1 holds my Windows OS files, sda2 is currently empty but will hold my user documents for Windows and I'm about to turn sda3 back into unallocated space.
 
Having read around a little bit, I believe I need at least 4GB for root but what would you recommend?
 
[2] I have 3GB RAM. Again, I've read around and I see that it's recommended that I have a 6GB swap partition.
 
[3] For Windows? Yes. For Linux, not really but I'd rather learn about it. Feel free to send me links to places where I can learn if you don't want to type something out yourself! :)
 
[4] Once again, as I've been reading I get the feeling that separating /home is what I'm doing with Windows on sda2, so yes, I would much prefer that to be honest. I've always been a fan of separating my personal data from the OS.
 
[5] ..And now I get the feeling that it's not quite as I've pictured it! :P
 
I'm going to turn sda3 back into unallocated space. Depending on how much space you recommend I use for Ubuntu/Linux (from there I'll calculate how much space I envisage myself using for my own personal data) I'll add the appropriate amount on to the end of sda2.
 
To clarify what I've read and understood thus far, though:
 
Given that sda1 and sda2 are both Primary Partitions, I only have two Primary Partitions left. One of these I should use on my root (/) and the other I should split into two logical partitions for my 6GB swap and X large /home.
 
I fear I've got my wires crossed.
 
As always, thank you very much for your time.

---

### Post by oldfred on 2011-01-06
At best swap needs to be just over 3GB with 3GB of RAM. You could get by with 2GB if you do not hibernate. The old 2X rule was when you only had 256MB or 512MB of RAM.

I would leave D: as a shared NTFS drive for data you might want in windows & Ubuntu. I do not like writing into a windows partition, but reading is ok. And windows will not even see the Linux partitions. You can have all of Ubuntu in logical partitions in the extended partition you create.

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space.
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by Quackers on 2011-01-06
Which Windows version are you using? If Win 7, it is worth checking your disk management screen in Windows to check the number of primary partitions currently in use by Windows - including any recovery partition. 

With 3GB of ram, and intending to use hibernate, your swap should be about 3.2GB
With a separate /home partition your /root partition could be 8GB.
The rest of the space could be your /home partiton.
Linux doesn't bother about being in a primary partition (like Windows does) so it can be installed within an extended partition. If you create an extended partition the full size of your free space, you can then create /root, /home and swap within that extended partition.

See oldfred's info above :-)

---

### Post by AVARiCE91 on 2011-01-06
> **oldfred said:**
> At best swap needs to be just over 3GB with 3GB of RAM. You could get by with 2GB if you do not hibernate. The old 2X rule was when you only had 256MB or 512MB of RAM. [1]
 
I would leave D: as a shared NTFS drive for data you might want in windows & Ubuntu. I do not like writing into a windows partition, but reading is ok. And windows will not even see the Linux partitions.[2] You can have all of Ubuntu in logical partitions in the extended partition you create. [3]
 
For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-20 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext3(or ext4)
3. 2 GB Mountpoint swap logical[4]
 
Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. [5]
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip. [6]
 
[1] Ok, thanks. :)
 
[2] When I previously installed Linux into sda2, I could read files from sda1. Same as when I used the Live-CD, so I think I've somehow accidentally got that shared system working! Again, when I had it previously installed, I could see the partitions when I went to Vista's Disk Management screen. Do you mean that Windows won't see the Linux partitions when I click on "My Computer", for example?
 
[3] Oh, nice. So I'll leave sda3 as unallocated space, use Linux's partition manager to turn it into an extended partition and everything will install in there?
 
[4] (See after Quacker's Post - [2])
 
[5] I think I've already got this working, I can access files while in Ubuntu, like I previously mentioned. To be honest, that's as far as I need things to go. If Windows dies on me again I want to be able to copy my files using Ubuntu but that's all the inter-operability I'm going to need.
 
[6] I always plot these sorts of things in advance. I'm a proper newb when it comes to the wonderful world of Linux but I've been using Windows for years and I favour the phrase "measure twice, cut once"!
 
Thank you very much for your help, too.
 
> **Quackers said:**
> Which Windows version are you using? If Win 7, it is worth checking your disk management screen in Windows to check the number of primary partitions currently in use by Windows - including any recovery partition. [1]
 
With 3GB of ram, and intending to use hibernate, your swap should be about 3.2GB
With a separate /home partition your /root partition could be 8GB.
The rest of the space could be your /home partiton. [2]
Linux doesn't bother about being in a primary partition (like Windows does) so it can be installed within an extended partition. If you create an extended partition the full size of your free space, you can then create /root, /home and swap within that extended partition.
 
See oldfred's info above :-)
 
[1] Vista and I've used it throughout this process. I have the partitions I mentioned previously. sda1 has Vista OS on it. sda2 is empty but I'll be moving my Windows User Directory there. sda3 is currently over 50GB of space which I'm about to make unallocated before my installation of Ubuntu.
 
[2] I'll add the extra swap space so that hibernating is an option, you never know! Given oldfred's advice, I'm going to go for a 10GB root. That means I'm only using <14GB. I'll use 30GB on the entire thing and add the extra 20GB back onto sda2.
 
So here's my final course of action really guys, I'll just run it by you:
 
- Turn sda3 into unallocated space, expand sda2 by another 20GB.
- Use the Live-CD to turn the unallocated space into an extended partition.
- Create a 3277MB swap file as a logical partition (1024 * 3.2, rounded up, if you're wondering how I turned out that number) within the extended partition.
- Create a 10GB root (/) as a logical partition within the extended partition.
- Create a 15GB /home as a logical partition within the extended partition.
 
Sounds good? One final thing, do I have to do anything for the /boot? I've seen it pop up a couple of times.
 
Thank you very much both of you for your time, especially Quackers who appears to have the patience of a saint! :D

---

### Post by oldfred on 2011-01-06
/boot is for old systems with limits on BIOS not able to boot beyond 137GB, servers with RAID or LVM - logical volume manager systems. For standard desktops you do not need any other system partitions separate.

If your long term plan is more to Ubuntu I would not expand your shared NTFS partition, but let Ubuntu have it. But it is not critical one way or the other.

---

### Post by AVARiCE91 on 2011-01-06
Brilliant, thanks. I'll give it a go tomorrow morning and if it works I'll edit OP to say solved.
 
Thanks to Quackers, kansasnoob and yourself. If any of you are in West London feel free to send me an email (it's in my profile somewhere) and I'll buy you a pint or something. Thanks again.

---

