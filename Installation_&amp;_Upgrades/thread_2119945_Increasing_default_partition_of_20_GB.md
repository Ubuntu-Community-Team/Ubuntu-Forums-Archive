---
title: "Increasing default partition of 20 GB"
date: 2013-02-25
forum: Installation &amp; Upgrades
---

### Post by dat789 on 2013-02-25
Hi people!

I've got a brand new 128 GB SSD to which Windows 7 was installed. After that, I've installed Ubuntu 12.04 LTS (64-bit) alongside (NOT Wubi). During installation, it didn't give me the option to adjust the size of the partition for the Ubuntu so I ended up with its default size of 20 GB.

Of the 128 GB (c:\), I think (need to check):
~40 GB is occupied by Windows, NTFS
20 GB by Ubuntu
The remaining (as revealed by diskmgmt.msc) is NTFS.

After looking up the forums and the Internet, it seems that in order to increase the 20 GB I'd need to install Gparted. 
Is this right? I thought I'd run the check here first before doing it.

If not, how will it be done? I'm open for suggestions.
Look forward to receiving/reading your response.

---

### Post by darkod on 2013-02-25
Gparted is just one of the tools you can use to manipulate the partitions. It has GUI interface so it's quite easy to use.

But the main question is not what tool you will use, it's whether you have unallocated space to expand the partition or not.

Install Gparted and open the disk with it. If you have more than one disk you can select the disk in Gparted in the top right corner.

Look at the physical location of the existing partitions. For expanding the ubuntu partition you need unallocated space next to it. And you will have to do it from live mode since it can't xpand the root partition when you are running from it. Gparted is included in the live cd.

---

### Post by TheFu on 2013-02-25
Boot Windows to reduce those partition sizes as desired, leaving free space. The To increase space from this, the newly freed storage will need to be contiguous with the Linux partition.  The order of partitions matters to Windows, so be very careful not to change the order for the Windows Boot partition.

Boot off a liveCD Linux or flash drive Linux with gparted loaded. You cannot modify partitions while using them.  google "gparted iso" if your installation CD doesn't have it and doesn't let you install into the live virtual HDD while running.  I always keep a gparted ISO on my emergency flash drive with **Yumi**.  Yumi is a great tool to have many, many Linux ISOs on a single flash drive.

Use gparted to make the space you want - I'd suggest having 2 partitions - 1 for the OS and applications and another for /home. This is different from expanding the current storage, but has many good reasons.  OS upgrades will be less risky to your personal data if they are in a different partition.  Be certain to use Logical partitions for everything if you are on an MBR system.  If on a GPT system, it doesn't matter, since hundreds of primary partitions are allowed.

After you've extended the current partition, if you selected that method, gparted should extend the correct formatting for you.
If you created a new partition, you'll need to create a file system on it, mount it to a temporary location, move everything from /home over to the /mnt/home temporary area, setup the /etc/fstab to mount it  - I would used UUID-based mounts, then reboot.  Have a live-flash Linux ready to fix any issues with the mount.  Clear as mud?

---

### Post by dat789 on 2013-02-25
> **darkod said:**
> 
Look at the physical location of the existing partitions. For expanding the ubuntu partition you need unallocated space next to it. And you will have to do it from live mode since it can't xpand the root partition when you are running from it. Gparted is included in the live cd.

Thanks for your response.
Does this then mean to load in the Ubuntu installation CD and boot from there to make changes? If so, and as gparted is not part of the Live installation CD, what are my options?

---

### Post by darkod on 2013-02-25
> **dat789 said:**
> Thanks for your response.
Does this then mean to load in the Ubuntu installation CD and boot from there to make changes? If so, and as gparted is not part of the Live installation CD, what are my options?

If you still have your 12.04 desktop cd and boot it into live mode (Try Ubuntu), Gparted is included on it.

But first only look at the partitions layout and don't resize anything, especially if you need to shrink ntfs partitions first. Windows will not like it if you shrink the OS partition with linux tools. Use windows Disk Management instead.

First only use Gparted and look, you will make decisions depending on your current layout.

---

### Post by dat789 on 2013-02-25
> **darkod said:**
> If you still have your 12.04 desktop cd and boot it into live mode (Try Ubuntu), Gparted is included on it.

But first only look at the partitions layout and don't resize anything, especially if you need to shrink ntfs partitions first. Windows will not like it if you shrink the OS partition with linux tools. Use windows Disk Management instead.

First only use Gparted and look, you will make decisions depending on your current layout.

Apparently the live CD I have does not include GpartEd.
Anyway, please take a look at the screenshot I've just generated. I installed gparted just right now.
[IMG]http://i.imgur.com/xG3u7xG.png[/IMG]

sda2 is where Windows 7 sits, with 49.43 GB of free space. No problems here for now.
sda5 is where Ubuntu 12.04 LTS currently sits and run. This was the default size of 20 GB.
sda6 is the space I would like to utilize. I'd really like the rest of its **15.53 GB absorb to sda5**, giving a total of 35.79 GB (total size; or 29.53 GB of remaining free disk space)

So, to begin this... do I get this -- [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php) ?

I do apologize if I sound fresh (only because I am). Your clear instructions and patience are very much appreciated. :p

---

### Post by TheFu on 2013-02-25
It looks to me like this will be easy if you want to merge sda5 and sda6.
* delete sda6 - use gparted - if you are running from a liveCD, you should be able to install gparted temporarily - this is fine.
* select sda5
* look in the menu - something like resize partition
* make sda5 larger - use as much or as little of the space that was under sda6 before.
* click apply
* wait a few minutes as all the operations are carried out.
That should be it.
Boot into the Linux installed on sda5 and see your extra disk. This command will prove that the extra storage has been added.
$ df -kh

---

### Post by darkod on 2013-02-26
> **TheFu said:**
> It looks to me like this will be easy if you want to merge sda5 and sda6.
* delete sda6 - use gparted - if you are running from a liveCD, you should be able to install gparted temporarily - this is fine.
* select sda5
* look in the menu - something like resize partition
* make sda5 larger - use as much or as little of the space that was under sda6 before.
* click apply
* wait a few minutes as all the operations are carried out.
That should be it.
Boot into the Linux installed on sda5 and see your extra disk. This command will prove that the extra storage has been added.
$ df -kh

+1. That should be it.

You can use the Gparted livecd or the ubuntu live cd, add Gparted in live mode if needed. I'm still confused you say it's not there since it should be if you have the default ubuntu cd. But you can always add it in live mode too, only it won't be there next time you use the cd. Live mode is temporary.

---

### Post by grahammechanical on 2013-02-26
It would be best to change the Ubuntu partition size from the live CD as I do not think we resize a Ubuntu partition while we are using it. Gparted is not installed into Ubuntu when Ubuntu is installed. And a good thing to as people can mess up their systems.

Gparted is on the standard Ubuntu live CD/DVD. It is what creates the Linux partitions in the first place. We need to run the Live Session and look for it in the Dash. I have used the live session in this way to re-size and create partitions several times.

Regards.

---

### Post by dat789 on 2013-02-26
@TheFu
Thank you for the clear instructions! As far as this thread is concern, I can now mark this as **SOLVED**!:KS

Booted the Live CD, choose Try Ubuntu instead of Install Ubuntu. Fire up gparted. And followed the instructions here. Apply. All done.
Screenshot here as proof.

[IMG]http://i.imgur.com/72ZZ8pw.png[/IMG]

:guitar:

---

### Post by dat789 on 2013-02-26
> **grahammechanical said:**
> It would be best to change the Ubuntu partition size from the live CD as I do not think we resize a Ubuntu partition while we are using it. Gparted is not installed into Ubuntu when Ubuntu is installed. And a good thing to as people can mess up their systems.

Gparted is on the standard Ubuntu live CD/DVD. It is what creates the Linux partitions in the first place. We need to run the Live Session and look for it in the Dash. I have used the live session in this way to re-size and create partitions several times.

Regards.

Yes, absolutely! Because of your second paragraph response, I was able to find it. This may sound silly but hey, it gave me the confidence kick to find it! And gparted was found! So, thank you! :P:popcorn:

---

