---
title: "Installing Ubuntu on External USB HD"
date: 2011-09-09
forum: Installation &amp; Upgrades
---

### Post by dbkats on 2011-09-09
Hi!

I'm very new to Linux, but I liked it so much I wanted to install it on my external USB HD. 

I followed some instructions that I found [here]("http://www.ubuntugeek.com/a-much-easier-way-to-install-ubuntu-on-a-usb-device-stick-or-hd.html"). I got stuck, though, after deleting all partitions on my HD.

My HD now consists of about 1.36 TB of free space. I am running Ubuntu  from a live CD and see this through GParted partition editor. I see the  same thing under "install Ubuntu". The disk is recognized under  /dev/sdb. 

What I wanted to do was to create one (or several) partitions for Linux  to live on, and another partition for my data. That way, if I want to  NOT boot from Linux, I can access all my files (like movies). However, I  am not sure how to partition my disk in order to do so.

When I select "/dev/sdb" and click on "Install Now", I get an error message:
"no root file system is defined. Please correct this from the partitioning menu". 
I guess this means I have to partition it prior to install. Can you guys help?

---

### Post by YesWeCan on 2011-09-09
Hi and welcome.

It is quite easy to do. A little hard to explain in text like this.

This data partition...do you want to access it with Windows? If so, it needs to be formatted as NTFS and not the usual linux format called ext4.

I just booted the 11.04 live CD and found it doesn't offer me the option to make an NTFS primary partition, which is garbage! So you'll need to use GParted instead. Which is a better tool anyway.

Easy tutorial here: [http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)

Using GParted first make a **primary** partition for your shared data and make it NTFS format.
Second make an **extended** partition to contain your Ubuntu **logical** partitions. This is for maximum flexibility. You only need root (/) and swap but some like to have a separate /home. So ideally make 10GB root formatted ext4, whatever size you like for /home formatted ext4 and a swap. There is no right answer for swap size but most just make it the same size as their RAM.

Then fire up the Ubuntu installer and in the partitioning section choose "Something else". This will give you an "Allocated Space" table and you click on each of the root and home partitions in turn, on each clicking "change" and then choosing their mount points. You do not have to do anything about swap...it will take care of itself.

**BY FAR THE MOST IMPORTANT THING **is to set the boot-loader location. The installer is insane and always chooses sda. You must not let it do this or it will trash the MBR on your internal hard drive. Lots and lots of people screw their systems up by mistake. It also gives you the choice to install to a partition which is crazy. So make sure you choose /dev/sdb (or whatever it has named your external HD).

Have a go. :)

---

### Post by recluce on 2011-09-09
Good instructions by YesWeCan. I would do a few things differently on the partitioning, though:

sdb1: Primary EXT4 Partition, at least 15 GB for Ubuntu Root ("/")
sdb4: Extended Partition (balance of the drive space)
sdb5: Logical EXT3 Partition, your Ubuntu home ("/home"), at least 75 GB
sdb6: Logical NTFS partition, balance of the Extended minus swap
sdb7: SWAP space, at least the size of your physical memory

Explanations: 

sdb1: I put the root partition at the beginning of the drive for best performance, putting it in a primary partition is more traditional than actually required. 10 GB is rather small for an Ubuntu root - and since there is plenty of room, better make it somewhat bigger. EXT4 is choosen for performance 

sdb5: having a seperate home partition means that you can reinstall Ubuntu without loosing your data. Very good idea. I chose EXT3 for unmatched stability, you want your data to be safe. Size of 75 GB should be sufficient for most people, even with some video conversion or editing. 

sdb6: whatever is left at this point (minus swap) becomes the NTFS partition, which can be used to share data between Ubuntu and Windows. 

sdb5 and sdb6 are put side by side in an extended partition to facilitate resizing. The OP is new to Ubuntu, should he find out that his home partition is too small or too big, this makes resizing with GParted easier.

Swap: if you want to use hibernation from Ubuntu, the minimum size is the same as your physical memory. Also, this has proven to be a safe amount of swap space in almost any szenario.

About GRUB: if you can boot from an USB drive, just follow YesWeCan's instructions. If your BIOS does not allow you to boot directly from an USB storage device, please check back before installing!

---

### Post by YesWeCan on 2011-09-09
> **recluce said:**
> 
sdb1: Primary EXT4 Partition, at least 15 GB for Ubuntu Root ("/")
sdb2: Extended Partition (balance of the drive space)
[COLOR="red"]sdb3[/COLOR]: Logical EXT3 Partition, your Ubuntu home ("/home"), at least 75 GB
[COLOR="Red"]sdb4[/COLOR]: Logical NTFS partition, balance of the Extended minus swap
sdb5: SWAP space, at least the size of your physical memory

Explanations: 

sdb1: I put the root partition at the beginning of the drive for best performance, putting it in a primary partition is more traditional than actually required. 10 GB is rather small for an Ubuntu root - and since there is plenty of room, better make it somewhat bigger. EXT4 is choosen for performance 

sdb3: having a seperate home partition means that you can reinstall Ubuntu without loosing your data. Very good idea. I chose EXT3 for unmatched stability, you want your data to be safe. Size of 75 GB should be sufficient for most people, even with some video conversion or editing. 

sdb4: whatever is left at this point (minus swap) becomes the NTFS partition, which can be used to share data between Ubuntu and Windows. 

sdb3 and sdb4 are put side by side in an extended partition to facilitate resizing. The OP is new to Ubuntu, should he find out that his home partition is too small or too big, this makes resizing with GParted easier.

Swap: if you want to use hibernation from Ubuntu, the minimum size is the same as your physical memory. Also, this has proven to be a safe amount of swap space in almost any szenario.

About GRUB: if you can boot from an USB drive, just follow YesWeCan's instructions. If your BIOS does not allow you to boot directly from an USB storage device, please check back before installing!
I think your sdb3 & 4 want to be sdb5 & 6 as they are logical. I would not use anything other than ext4 because of its superior search and journalling (I am not aware of any stability problems...what have you experienced?). My root contains 6GB and I have quite a lot of stuff installed. As this is an external USB disk I am putting simplicity above ultimate performance. I think Windows accessible partitions sit better in primaries, including Windows OSs, and linux in logical. Some subjective preference involved here.
Good point to check the PC can boot from a USB.

---

### Post by recluce on 2011-09-09
> **YesWeCan said:**
> I think your sdb3 & 4 want to be sdb5 & 6 as they are logical. I would not use anything other than ext4 because of its superior search and journalling (I am not aware of any stability problems...what have you experienced?). My root contains 6GB and I have quite a lot of stuff installed. As this is an external USB disk I am putting simplicity above ultimate performance. I think Windows accessible partitions sit better in primaries, including Windows OSs, and linux in logical. Some subjective preference involved here.
Good point to check the PC can boot from a USB.

You are right on the drive numbering (I edited my post), I should get another cup of coffee!

EXT3 vs. EXT4: I tried to avoid that discussion, but there are still some anecdotal reports of data corruption on large file writes with EXT4. I am super-conservative with data integrity and since the performance difference is small anyway, I prefer EXT3 for data storage.

Windows and primary/logical: I don't like Windows much, but Windows can handle logical partitions just fine. Hence putting both /home and the NTFS side by side inside the extended, to facilitate resizing.

Ubuntu root sizing: I am sitting at 9.2 GB right now - and I don't think that I installed an unreasonable amount of applications. Hence the recommendation to have at least 15 GB, since there is plenty of storage space available.

And yes, some personal preferences seem to be involved on both sides. :biggrin:

---

### Post by YesWeCan on 2011-09-09
I need more applications! :P

I would be disinclined to use anything but ext4 on rumours only. It's been out for several years now and has superior performance features and safer journalling.

As for partition locations, there are many ways to skin a cat. ;)

---

