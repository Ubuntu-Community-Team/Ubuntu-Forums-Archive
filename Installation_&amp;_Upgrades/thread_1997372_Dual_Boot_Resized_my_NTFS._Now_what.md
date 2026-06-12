---
title: "Dual Boot: Resized my NTFS. Now what?"
date: 2012-06-05
forum: Installation &amp; Upgrades
---

### Post by SketchMan3 on 2012-06-05
Ok, I am at a total loss. My 200 gb harddrive is partitioned as so: 4gb Windows Recovery | 80gb Windows XP | 100gb unallocated free space.

Can somebody tell me what to do with this? I'm wanting to install Ubuntu 10.10 to the free space, but when I get to the "Manually Allocate Partitions" part, I have no idea what File Systems to use, what Mount Point to use, how big to make the Partitions, whether the system would run faster with a larger-than-suggested 2gb swap file, etc. etc. ad nauseam.

My old Windows partitions are purely for preservation purposes. i won't actually be accessing Windows it at all, but I want to leave it in case my external-hdd-backup of the files retrieved from that system goes bad (yes, I'm using the original as a backup to my backup).

I really wish the various guides on installing ubuntu and partitioning a hard drive manually and etc. went a bit more in-depth.


In hindsight, it would have been better to leave the NTFS system intact, and simply use the automatic resizing in the Live USB Installer, but since I already did the resizing of the system, I may as well just continue from there, right? 
Is there some way to tell it to "automatically" install to the free space? Should I set the unallocated space as just a temporary file system just so the installer can read it as a file system and overwrite it? 

Please help.

---

### Post by wilee-nilee on 2012-06-05
First 10.10 is end of life you will not have support for it do not install it. Download 10.04 if you want that desktop, is supported for another year or so, or download 12.04 the next long term supported for 5 years.

Resizing the windows first and making sure it runs the auto chkdsk and is in good order is the best and safest way to dual boot.

Boot the ubuntu live cd of what your going to install and take a screenshot of the gparted partitioner and post it using the paperclip in the reply panel, and we will get you set up.

The something option is really the one you're best getting acquainted with in the end, the custom install. It is not much different aesthetically than the custom install option in a windows install set up.

Post the gparted screenshot before you you start the install if you can.

---

### Post by SketchMan3 on 2012-06-05
Thanks for the response.

Yes, I resized Windows, and let it run the chkdsk.

So,  you say 10.04 is still being supported, while 10.10 is no longer supported? How interesting. I hope I don't lose anything worth keeping by using a downgraded system. I've been running off this 10.10 live usb for over a year, and I've forgotten exactly what the differences were (10.04 was my first ubuntu system on another computer). 

According to the live CDs I've used, my system can't handle anything higher than 10.10. Issues with performance, and the cursor not showing up...

Shoot... so I'm going to have to download and burn a live cd of 10.04? *goes to dig out the CD-Rs* I'll get that screenshot as soon as I've done that. It wouldn't do any good to post a shot of the 10.10 gparted from the live usb I'm on right now? Well, here it is anyway, until I get that 10.04 cd burned.

---

### Post by wilee-nilee on 2012-06-05
> **SketchMan3 said:**
> Thanks for the response.

Yes, I resized Windows, and let it run the chkdsk.

So,  you say 10.04 is still being supported, while 10.10 is no longer supported? How interesting. I hope I don't lose anything worth keeping by using a downgraded system. I've been running off this 10.10 live usb for over a year, and I've forgotten exactly what the differences were (10.04 was my first ubuntu system on another computer). 

According to the live CDs I've used, my system can't handle anything higher than 10.10. Issues with performance, and the cursor not showing up...

Shoot... so I'm going to have to download and burn a live cd of 10.04? *goes to dig out the CD-Rs* I'll get that screenshot as soon as I've done that. It wouldn't do any good to post a shot of the 10.10 gparted from the live usb I'm on right now? Well, here it is anyway, until I get that 10.04 cd burned.

You may be having a fail on any release above 10.10 due to a simple problem so lets keep the option of that open if needed. 10.04 is a longterm release, that is why it is still supported. Very little difference between 10.04 and 10.10 you should be fine, and can transfer some of it to the 10.04, maybe the whole home if the 10.10 is a full install, others will help with this.

Any gparted screenshot is good thanks.

You might give a hardware outline if you are interested in any releases above 10.10, basically the ram amount and chip speed, the command below will show the actual hardware itself.

```
lspci
```I will be gone for about 12 hours so if you're on line others will get you set up. ;)

---

### Post by darkod on 2012-06-05
Unfortunately we can hardly help you with partition sizes. It depends how you use your computer and your amount of data.

What I would do, is:
1. Create the root partition as logical, ext4, size 15GB, mount point /.
2. Create separate /home partition, logical, ext4, size (the rest - swap), mount point /home.
3. Create 2GB or 4GB swap partition, you will rarely use it anyway. But if you plan to hibernate swap needs to be around 1.5 x RAM size. Also create it as logical, filesystem type swap area. Swap doesn't use mount point.

That should be it.

EDIT PS. I agree it's better to look into the issue why you can't use anything above 10.10. Try in live mode first. It might be simply a video driver issue. It's much better to use the latest 12.04 LTS and if you want to older look interface instead of Unity you can always install Gnome Classic (package name gnome-panel).

---

### Post by SketchMan3 on 2012-06-05
It probably is a video driver issue. Can one install new video drivers when using a live CD? I recall not being able to find drivers for it from the "System>Administration>Additional Drivers" menu.

Here's my lspci:

```

00:00.0 Host bridge: VIA Technologies, Inc. VT8378 [KM400/A] Chipset Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237/VX700 PCI Bridge
00:0a.0 Communication controller: Agere Systems V.92 56K WinModem (rev 03)
00:0b.0 FireWire (IEEE 1394): VIA Technologies, Inc. VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller (rev 80)
00:0f.0 IDE interface: VIA Technologies, Inc. VIA VT6420 SATA RAID Controller (rev 80)
00:0f.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:11.6 Communication controller: VIA Technologies, Inc. AC'97 Modem Controller (rev 80)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)
01:00.0 VGA compatible controller: VIA Technologies, Inc. KM400/KN400/P4M800 [S3 UniChrome] (rev 01)

```

My computer is an old HP Pavilion a735w with 1g of RAM and AMD Athlon XP 3000+. Anyway, I'll just deal with upgrading in 2013 when 10.04 hits end-of-life. 

Also, thanks, darkod, for giving me a starting point. That's VERY helpful, and exactly what I needed. 

I basically just want to use it for the typical net surfing and media consumption, simple video editing, music creation, drawing, and playing games like Supertuxkart and Open Arena, and have lot's of storage space.

Question: in the drop-down menu, are all of the non-faded-out filesystems able to run Ubuntu? Even fat32? Not that I want to use fat32...

10.04 live disc burned...

---

### Post by darkod on 2012-06-05
If you are talking about Gparted, in the drop down menu it lists all filesystems it can create. You will need a linux filesystem for the ubuntu root and /home partitions, like ext4.

So, no, it will not run on all FSs that Gparted has to offer. They are there so you can also create additional ntfs partitions, etc. But you will need extX for ubuntu.

---

### Post by SketchMan3 on 2012-06-05
I was actually talking about the section of the Ubuntu Installer that let's you manually setup partitions for your install. But you answered my question anyway.

Edit:
> **darkod said:**
> Unfortunately we can hardly help you with  partition sizes. It depends how you use your computer and your amount of  data.

What I would do, is:
1. Create the root partition as logical, ext4, size 15GB, mount point /.
2. Create separate /home partition, logical, ext4, size (the rest - swap), mount point /home.
3. Create 2GB or 4GB swap partition, you will rarely use it anyway. But  if you plan to hibernate swap needs to be around 1.5 x RAM size. Also  create it as logical, filesystem type swap area. Swap doesn't use mount  point.

That should be it.

Do I create them in that order? with root partition at the left-most, and the 2-4 GB swap at the right-most, home in the middle? [s]The root partition is where installed packages go, right?[/s]
Edit: Nevermind that last part, =\

---

### Post by darkod on 2012-06-05
Yeah, I would suggest that order. In future if you ever need to shrink /home and use that space to expand / to give it more space, it's better they are next to each other.

---

### Post by SketchMan3 on 2012-06-06
Oh, goody! The 10.04 installer does have the option to "Install to Largest Continuous Space", so I don't have to manually partition the drive.

Will the automatic install do the same thing you advised me to do manually?

Edit: Also If I have 1gb of RAM, would making the swap 4gb be a problem? I'd prefer to have a good-sized swap, considering I have such a small amount of RAM. Edit 4: And, I may upgrade to 2gb in the future.

Edit 2: Also, I'm using the Ubuntu Installer to create the partitions instead of using Gparted. I hope that's not a problem. And, what is the advantage of having separate root and home partitions?

---

### Post by darkod on 2012-06-06
With the Install to largest continuous free space will install on only two partitions, root and swap, and select their sizes according to the free space size. So, you will not have control on the exact size of swap for example.

With the manual install, you can make swap any size you choose to, so yes, you can make it 4GB.

The advantage of having separate /home is that in future you an do a clean install formatting root but you will still have all data in your /home available because during the install you will tell the installer to use that partition as /home and NOT TO format it.

Yes, you can create the partitions with the installer, no harm done.

---

### Post by SketchMan3 on 2012-06-06
Thanks, to you all! I think I'm ready, now. Hopefully this thread will be of use to someone in the future. Oh, wait, one more question. Lol. 

I'm on the "Ready to Install Step" and happened to click the "Advanced..." button. Do I have to install bootloader? Do I do anything with that?

---

### Post by darkod on 2012-06-06
The bootloader goes to the MBR, in other words /dev/sda (without any number in it). That should be the default anyway.

---

### Post by SketchMan3 on 2012-06-07
Welp, everything worked out. Thanks for all your help. Now if I can just get FLASH working (Not even Flash-aid is getting it... but that's a topic for another thread).

---

### Post by wilee-nilee on 2012-06-07
> **SketchMan3 said:**
> Welp, everything worked out. Thanks for all your help. Now if I can just get FLASH working (Not even Flash-aid is getting it... but that's a topic for another thread).

To install flash, codecs and ms fonts run in the terminal
```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by SketchMan3 on 2012-06-08
Does that work better than using the Software Center? Installing restricted from the software center was one of the first changes I made to my system. Before that I had opened rhythmbox and they told me to install mp3 support or something.

Anyway, I made a thread about my flash problems.
[http://ubuntuforums.org/showthread.php?t=1999334](http://ubuntuforums.org/showthread.php?t=1999334)

---

### Post by wilee-nilee on 2012-06-08
> **SketchMan3 said:**
> Does that work better than using the Software Center? Installing restricted from the software center was one of the first changes I made to my system. Before that I had opened rhythmbox and they told me to install mp3 support or something.

Anyway, I made a thread about my flash problems.
[http://ubuntuforums.org/showthread.php?t=1999334](http://ubuntuforums.org/showthread.php?t=1999334)

Same app from the software center, the terminal, or synaptic.

---

