---
title: "Kubuntu 12.04 x64 will not boot after install"
date: 2013-03-02
forum: Installation &amp; Upgrades
---

### Post by SpectrumDT on 2013-03-02
Kubuntu 12.04 x64 will not boot after install

Hi, all.

I have the following situation: 

I am on a 64-bit system.
I have a brand new hard drive.
I have installed Windows 7 on the first partition on this hard drive.
Now I am trying to install Kubuntu 12.04 next to my Windows. 
The Kubuntu installer seems to install fine, but when I boot I get this:

error: no such partition
grub rescue>

This means I can boot neither Kubuntu nor Windows. I've googled a bit. I've found out (url=http://ubuntuforums.org/showthread.php?t=1359802]here[/url]) that I can restore the Windows boot loader by booting with the Kubuntu Live CD and doing this:

```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```

The above allows me to boot Windows, which is nice and all, but it doesn't help me get into my Linux. 

I've tried to restore GRUB by booting with the Kubuntu Live CD and using the GUI tool "Boot-Repair" (and doing a "recommended repair"). That didn't help. It just brought back the error message "error: no such partition". 

I have a (presumably) functioning Kubuntu installation, but I cannot boot it. Can anyone help me set up GRUB so I can get into my Linux? 

Thanks in advance!

---

### Post by oldfred on 2013-03-02
How large is new hard drive? And how did you partition. Some have had issues with very large / (root) partitions. I normally suggest 25GB for / and use the remainder for /home or preferred just as data partition(s). Especially if dual booting with Windows another NTFS shared data partition is good to have. Best not to write into Windows system partition, just shared data. And then set Windows system partition as read only.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by SpectrumDT on 2013-03-02
Thanks for the reply.

My Boot-Repair URL is this: [http://paste.ubuntu.com/5580271/](http://paste.ubuntu.com/5580271/)

My hard drive is 3 TB. The first partition, containing Windows, is one terabyte. The second partition, containing Kubuntu (ext4), is 100 GB in all.

**EDIT:** I've messed around a bit, so I decided to run boot-repair again (with default settings). Here is my newest boot-repair URL: [http://paste.ubuntu.com/5580448/](http://paste.ubuntu.com/5580448/)

---

### Post by oldfred on 2013-03-02
There was a bug where grub/Ubuntu would not boot from partitions over 500GB location on drive. Supposedly that bug was fixed but we still see issues with some BIOS and grub versions. I would add a /boot partition near the beginning of some drive.

You do know with MBR partitioning your 3TB drive is only 2TiB or about 2.2TB as that is the largest MBR is. Some drive manufacturers have a 4K drive and make MBR use that which may be a work around. Yours shows the 512/4K mapping.

With Multiple drives it usually is best to have Windows on one drive (sda) and Ubuntu on another drive. And I like to have an operating system on every drive as a backup boot.

---

### Post by SpectrumDT on 2013-03-03
> **oldfred said:**
> There was a bug where grub/Ubuntu would not boot from partitions over 500GB location on drive. Supposedly that bug was fixed but we still see issues with some BIOS and grub versions. I would add a /boot partition near the beginning of some drive.

You do know with MBR partitioning your 3TB drive is only 2TiB or about 2.2TB as that is the largest MBR is. Some drive manufacturers have a 4K drive and make MBR use that which may be a work around. Yours shows the 512/4K mapping.

With Multiple drives it usually is best to have Windows on one drive (sda) and Ubuntu on another drive. And I like to have an operating system on every drive as a backup boot.
Thanks for the reply. I installed Kubuntu on another hard drive instead, and now it works fine. :)

---

