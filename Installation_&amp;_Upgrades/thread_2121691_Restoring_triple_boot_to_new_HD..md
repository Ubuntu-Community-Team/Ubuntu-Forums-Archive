---
title: "Restoring triple boot to new HD."
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by Harp on 2013-03-02
Apologies for the inevitable redundancies of triple boot questions, but I felt my problem is specific enough that I haven't already found it covered in such terms. If anyone knows of a thread in which this specific problem is already covered, please point me to it without acting like an a-hole. Thanks.

Equipment:
MacBook Pro 7,1 (Triple Boot via rEFIt -- OS X Lion / Ubuntu 12.04 / Windows 8)
HDD --   Seagate Momentus 1TB (new)
             Hitachi 5K500 B-320 (old)

Background:
I had this triple-boot setup already configured on my old hard drive, but I just upgraded my laptop to a 1TB drive and so I'm currently re-installing (fresh installs) and then restoring my systems from backup. I re-installed/restored OS X fine (including a partition for Lion recovery, hfs+), then used the Ubuntu 12.04 livecd to make partitions for Ubuntu (ext4, plus Grub and Swap). I reinstalled/restored Ubuntu fine. Then I used gparted to create two more NTFS partitions: an 85GB for a Windows install, and a 100GB for a general sandbox to be shared between systems.

[[IMG]http://imageshack.us/a/img688/7673/screenshotfrom201303021.th.png[/IMG]](http://imageshack.us/photo/my-images/688/screenshotfrom201303021.png/)

Problem:
When I boot to the Windows 8 install cd, it does not recognize the separate NTFS partitions I made and lumps them together with the Linux and Linux Swap partitions as one big "Unallocated Space."

[[IMG]http://imageshack.us/a/img405/1024/20130302131753.th.jpg[/IMG]](http://imageshack.us/photo/my-images/405/20130302131753.jpg/)

I realize now that I probably should've installed Windows first, then Ubuntu. But I didn't. And I'd rather not have to go back and reformat everything this way and have to restore/reconfigure my Linux system again. I'd probably rather just ditch Windows if it came down to this, as I'm installing it "just in case," anyway.

Questions:
1) Is there a way to configure my Windows NTFS partition in Linux (or Mac) to be recognized by the Windows install cd?

or

2) Is there a way to, perhaps, install Windows through Linux (or Mac), as in using the terminal to copy files from the mounted Windows 8 install disc to the Windows partition? (huh?)

or

3) I still have the old drive, which I could mount via a SATA/USB cable, boot into the Ubuntu livecd, then dd the former Windows partition from my old drive to the proposed partition on my new drive. However, this is the method I originally intended to use to upgrade to the new 1TB drive but had all kinds of problems with the MBR (hence the fresh installs). Would dd'ing my old partition to my new one mess up my MBR?

I'm thinking #3 might be the best solution, just wanted to get some feedback first. Are there any better suggestions?

Thanks again.

---

### Post by darkod on 2013-03-02
It seems it doesn't like the partition table, so it's confused about the partitions on it. I don't know Macs, not sure how should you create partitions for windows. For example, it shows 4 partitions as primary, if it doesn't get the table as gpt, it might think 4 is the maximum since it is on msdos tables.

But this is just an assumption. As I said, I don't know Macs.

---

### Post by Harp on 2013-03-02
> **darkod said:**
> It seems it doesn't like the partition table, so it's confused about the partitions on it. I don't know Macs, not sure how should you create partitions for windows. For example, it shows 4 partitions as primary, if it doesn't get the table as gpt, it might think 4 is the maximum since it is on msdos tables.

But this is just an assumption. As I said, I don't know Macs.

Thanks for your quick reply. I see what you mean. In fact, if I click "Show Details" from the Windows installer, it tells me, "Windows cannot be installed to this hard disk space. The selected disk has the maximum number of partitions of this type."

This is what I get from running gptsync in the EFI shell: 
(the top portion is the GPT, though it scrolls off the screen and the -b pagination option doesn't seem to work for this command.):

[[IMG]http://imageshack.us/a/img546/4097/20130302153349.th.jpg[/IMG]](http://imageshack.us/photo/my-images/546/20130302153349.jpg/)

You can see the difference here. (side question, are these supposed to be listed as "Basic Data" rather than something more specific?)

Do you have any suggestions for a solution? I'm not too familiar with MBRs. Would the right thing to do be to change some partitions from primary to logical partitions? How would I even go about that? Or is there a way to replace the MBR with a GPT entirely?

Thanks for any help, this is definitely not my area of expertise.

---

### Post by darkod on 2013-03-02
Since you are on a Mac it's outside my area of expertise too. :) But at least now you know what's bothering it. I think the table has to be gpt since OSX won't work if it's not. Also, win7 works with UEFI boot, which I guess rEFIt uses, only on gpt.

But from what ever reason, it doesn't understand this gpt table.

Here is what you can try if you are happy starting from scratch. Sit down and calculate all partitions sizes and start/end points. Write them down so you have the layout. Then boot the ubuntu cd/usb in live mode and write a new blank gpt table. I suggest ubuntu because I'm sure windows can read such table. I hope OSX too.

Create the partitions with parted for example, parted doesn't create filesystem, only a partition. Then start installing, windows first if you think that's best. Can you install OSX after windows?

If you need help with parted, the basic is (assuming the disk is /dev/sda):
sudo parted /dev/sda #(to open the disk with parted from live mode)

Once inside the parted> prompt, the most common commands are:
unit MiB (or GiB) #(to switch the unit to MiB or GiB for exact partitioning)
mklabel gpt #(write new blank gpt table)
mkpart <label> <start> <end> #(make new partition with label, start and end point)
quit #(to quit when done)

The start and end point will be in the unit currently in use which you control with the 'unit' command.

Once the partitions are there, simply format each one during installation for each OS type.

You have more experience installing on Macs than I do, do you think that would work?

---

### Post by oldfred on 2013-03-03
It is my understanding with Macs that Windows has to be installed with MBR, but Macs use gpt. So they create a hybrid mbr/gpt system that you have to keep in sync. So Windows can boot from the MBR portion and the Mac & Linux can use the gpt partitions.

       [http://www.rodsbooks.com/gdisk/hybrid.html](http://www.rodsbooks.com/gdisk/hybrid.html)

---

### Post by Harp on 2013-03-03
I opted for the blunter solution. It appears that (as you implied, darkod) Windows 8 has no problem booting from a GPT via UEFI and rEFIt. The problem is that the Windows 8 installation disk installs based on the MBR, so I basically had too many partitions. 

As a solution, I deleted (begrudgingly) all my Linux and sandbox partitions, leaving only the EFI, Mac OS X and Mac Recovery partitions. Then I made a Fat32 partition of the size I wanted for Windows, and left the rest of the disk as empty space. This left only 4 actual partitions, sufficient for the Windows install disk to understand the MBR. So, I converted that Fat32 partition to NTFS with the install disk, installed Windows no problem and then continued to fill the rest of the drive with my Linux and sandbox partitions via the Ubuntu livecd. 

I have my triple-boot setup running fine now. As I said, rEFIt boots Windows using the GPT with no problem, it seems it was just an issue with the install disk.

The moral of this story... duct tape fixes anything.

---

