---
title: "Install Ubuntu 12.04 into a specific existing partition?"
date: 2012-07-08
forum: Installation &amp; Upgrades
---

### Post by dewdrop_world on 2012-07-08
This should be a fairly simple question. Probably already asked and answered, but I couldn't find a clear answer in Ubuntu community documentation, I didn't see anything like it in the first three pages of topics under "Installation and Upgrades" and also, the Ubuntu forums search returned the surprising result of "no matches" for the search terms

upgrade "12.04"

... so, I did try to find an existing answer but the search seems to be not all that hot.

Anyway... I have these partitions:

/dev/sda1
/dev/sda2
/dev/sda3 -- win7
/dev/sda4 -- fat32 (data)
/dev/sda5 -- ext4 (Ubuntu 10.04)
/dev/sda6 -- swap
/dev/sda7

Ubuntu is not allowing me to perform an upgrade installation from 10.04 to 12.04 (even though some information online suggested that Ubuntu should support upgrades from one LTS to the next). So, I want to do a fresh installation of Ubuntu 12.04 into /dev/sda5 and restore my files from backup later.

Which options in the liveCD installer should I use? If I remember right, the first question is:

- Install alongside existing operating systems (not exactly -- I do want to blow away 10.04)
- Format and use the whole hard disk (definitely not!)
- Other (maybe...)

I had a look at "Other," but there isn't much text to explain what's going on. The upper panel lists the available partitions and there are some buttons to modify the partitions, but it isn't clear whether this is the place to choose the partition into which you want to install the new version.

There's also a pop-up menu for the device where you want to install the bootloader. This is also unclear. Should this be the hard drive overall (/dev/sda) or the target partition for installation (/dev/sda5)?

Sorry if this "should" be obvious, but it isn't.  Understandably, I really don't want to click the wrong thing and fubar my hard drive.

Thanks for advice.
James

---

### Post by darkod on 2012-07-08
Yes, you need to use the Something Else, in the list of all partitions select the one you want to use as root, and click the Change button below.

Select mount point /, change the Use As to ext4 (or another filesystem if you prefer to use different one), tick the format box. NOTE: That will DELETE all data on the partition. Make sure you save what you want to keep.
If you have a separate /home, do the same, only select mount point /home, DO NOT format it, and select always the same filesystem as the one currently on the partition.
It should use the swap automatically, but it doesn't hurt selecting the swap partition to be used as swap area too (no mount point for swap).

The bootloader goes to the MBR of the disk, /dev/sda (without any number).

Having said all this, if you prefer to do the upgrade, the LTS to LTS upgrade becomes available only after the first .1 release is made, in other words when 12.04.1 comes out (scheduled around August 23rd).
You can also try the upgrade now by opening terminal and starting the update manager with the -d option:
```
sudo update-manager -d
```

---

### Post by Karlchen on 2012-07-08
Hello, dewdrop_world.

The option to select in your case seems to be **(3) Other ...**
Options (1) and (2) do not match your situation, therefore the right choice is (3).
(3) allows you to select any action that is not covered by (1) and (2).

You will be allowed / forced to tell gparted which device to format for your Ubuntu 12.04 installation. As you are going to replace the existing 10.04 installation, you will choose /dev/sda5. As your swap device you will choose /dev/sda6.

About the location of Grub:
Well it depends where it is now. I would simply choose the same location.

Where has the Grub that came with Ubuntu 10.04 been installed to?
+ to /dev/sda5?
+ to /dev/sda (i.e. the Master Boot Record)?

Let me ask the other way round:
When you boot your machine up, you will be presented a boot menu.
What kind of boot menu is it?
In case it the the Windows boot menu (bootmgr), then Grub must have been installed to /dev/sda5.
In case the first boot menu which you see is a Grub menu, then Grub must have been installed to /dev/sda.

Factor of uncertainty:
We have not learnt whether there is another Linux system on your machine, installed in /dev/sda1 or /dev/sda2, which might have installed yet another Grub. Is there?

Kind regards,
Karl

---

### Post by dewdrop_world on 2012-07-08
> **darkod said:**
> Yes, you need to use the Something Else, in the list of all partitions select the one you want to use as root, and click the Change button below.

Select mount point /, change the Use As to ext4 (or another filesystem if you prefer to use different one), tick the format box. NOTE: That will DELETE all data on the partition. Make sure you save what you want to keep.

The bootloader goes to the MBR of the disk, /dev/sda (without any number).

Thanks. That was my guess -- but when it comes to the risk of messing up the partitions, an educated guess is not good enough.

I'm now writing this in a fresh Ubuntu 12.04 installation, with a lot of files restored from backup and software reinstalled. No significant problems so far! (Other than really disliking the unity desktop and switching back to gnome.)

Thanks again! Big help --
James

---

