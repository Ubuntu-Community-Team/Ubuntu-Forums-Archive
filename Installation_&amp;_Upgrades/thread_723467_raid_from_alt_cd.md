---
title: "raid from alt cd"
date: 2008-03-13
forum: Installation &amp; Upgrades
---

### Post by Repus on 2008-03-13
I would greatly appreciate some help

I have 2 -  500gb hdds. I would like to setup RAID1 to simply mirror the two drives. Ive read I need to install using the alt cd. So I have the alt cd... and I imagine I need to use the custom partition setup but Im new to this and am not comprehending the instructions I have found in various threads.

Could someone point out what exactly needs to be done at this point? Is raid a two step process? One step at the partition and another after install?

fyi My motherboard does not provide raid. So this has to be a software raid setup.

Thanks in advance

---

### Post by Repus on 2008-03-13
Well I found a site that has a simply install step by step for raid1.  Not sure if it works just yet but it was easy enough to follow.

[http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/](http://advosys.ca/viewpoints/2007/04/setting-up-software-raid-in-ubuntu-server/)

---

### Post by diegosouza on 2008-03-13
Great article! Thanks, it goes to my delicious  :-)
After done the RAID, tell me if it works fine, I want to know.

---

### Post by Repus on 2008-03-14
In case anyone is curious the instructions on this link worked great and they were easy to follow.

[http://advosys.ca/viewpoints/2007/04...ubuntu-server/](http://advosys.ca/viewpoints/2007/04...ubuntu-server/)

Ive taken the liberty to re-post the text of Derrick Webber's instructions but I highly recommend visiting the link as it comes with pictures, tips, and other useful instructions, and its formatted for readability.

---clipped---
 To install a fresh Ubuntu System with RAID, boot from the CD-ROM as usual. Follow the prompts until you get at the “Partition Disks” dialog.

    * From the “Partitions Disks” dialog box, select “Manually edit the partition table”.
    * Select the first disk (”sda”)
    * Say yes to “Create a new empty partition table on this device?”
    * Use the dialog boxes to create one primary partition large enough to hold the root filesystem (4.1 GB in this example)
    * For “How to use this partition” select “physical volume for RAID“, not the default “Ext3 journaling file system”
    * Make the partition bootable.
    * Use the dialogs to create one other primary partition taking up the remaining disk space (197.4 MB in this example). Later this will be used for swap.
    * For “How to use this partition” select “physical volume for RAID“, not the default “Ext3 journaling file system” and not “swap area”
    * Repeat the above steps to create identical partitions on the second drive. Remember to mark partition one on both drives as “bootable”. The final result should look similar to the following:

see original article for pic

    * Once the partitions are configured, at the top of the “Partition Disks” main dialog select “Configure Software RAID”
    * When asked “Write the changes to the storage devices and configure RAID” select “Yes”.
    * For “Multidisk configuration actions” select “Create MD device”
    * For “Multidisk device type” select “RAID1&#8243;
    * For “Number of active devices for the RAID1 array” enter “2&#8243;
    * For Number of spare devices for the RAID1 array” enter “0&#8243; (zero)
    * When asked to select “Active devices for the RAID1 multidisk device” select both /dev/sda1 and /dev/sdb1
    * From the next dialog select “create MD device”
    * Repeat the above steps to create an MD device that contains /dev/sda2 and /dev/sdb2
    * Finally, from the dialog “Mulidisk configuration actions” select “Finish”

Next configure device md0 to be mounted as the “/” filesystem and device md1 to be mounted as swap:

    * From the “Partition Disks” dialog, move the cursor bar under “RAID device #0&#8243; and select “#1 4.1 GB”
    * Configure the device as an Ext3 filesystem mounted on /, as shown:

see original article for pic

    * From the Partition Disks dialog under “RAID device #1&#8243; select “#1 197.3 MB”
    * Configure the device as “swap area”, as shown:

see original article for pic

    * The final partitioning screen should resemble the following:

see original article for pic

    * Select “Finish partitioning and write changes to disk”.The RAID1 mirrors are created and made active, the the filesystem is formatted and installation of Ubuntu proceeds as usual.
    * Allow the installation to complete then reboot when requested.

---

