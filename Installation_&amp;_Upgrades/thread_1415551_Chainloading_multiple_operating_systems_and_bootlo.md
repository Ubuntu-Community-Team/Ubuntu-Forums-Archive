---
title: "Chainloading multiple operating systems and bootloaders"
date: 2010-02-24
forum: Installation &amp; Upgrades
---

### Post by Cyber Akuma on 2010-02-24
Currently my System has Vista(NTFS), Ubuntu(ext4), and OpenSUSE(ext3) installed.

The problem with this setup is that when I created it, OpenSUSE could not do ext4, meaning it could not update the menu.lst every time there was a kernel update, manually updating it got old FAST.

OpenSUSE now supports ext4..... but still runs on grub1, and I really don't want to go back to grub1 when Ubuntu uses grub2.

I am about to delete the Vista partition to install Windows 7 and the OpenSUSE partition to re-create it in ext4, and I figured I might as well make a 100mb or so boot partition at the start of the drive as I delete my Vista partition. I want to try to keep the Ubuntu partition if possible, but if I need to I can delete that too. If I keep it though, I will need to update it's existing grub1 install to grub2.

Problem is, I am not sure how to keep my menu.lst file updated automatically. If OpenSUSE supported grub2 I could just point them both to the boot partition and be done with it.

I was wondering if there was a way I could install a sort of "master" version of grub with no kernels, that merely points to either the config(menu.lst) files or grub installs of other operating systems (these being Ubuntu and Opensuse) so they can just update their own version of Grub and not mess with the master. That way I won't need to manually edit menu.lst every time OpenSUSE has a kernel update.

---

### Post by oldfred on 2010-02-25
This is one way:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)


In old grub I created a grub partition and created my own menu.lst that just chainbooted to all the operating systems. New grub can do this but grub2 does not want to be installed in a partition (PBR) to allow chainbooting to it.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Grub legacy:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by recluce on 2010-02-25
> **oldfred said:**
> This is one way:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)


In old grub I created a grub partition and created my own menu.lst that just chainbooted to all the operating systems. New grub can do this but grub2 does not want to be installed in a partition (PBR) to allow chainbooting to it.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Grub legacy:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

Excellent advice in the above post. I am in a multiboot situation on my machine, too. For testing purposes, I need CentOS and FreeBSD, I have Ubuntu 9.04 and 10.04 on the machine, as well as Windows XP. The only way I found to keep my sanity was a dedicated legacy GRUB partition as per the instructions under "GRUB legacy" above. 

If you want, you can chainload into Ubuntu's GRUB2 this way (thus you would not have to edit the menu.lst for Ubuntu entries). If you install legacy GRUB to a dedicated partition, I would recommend taking the GRUB files from a Jaunty live CD - or other distribution that has GRUB 1 and EXT4. Using GRUB files from a distribution that does not have EXT4 (like Intrepid) will cause GRUB to be unable to boot from EXT4.

---

### Post by darkod on 2010-02-25
I'm relatively new to linux so it might be the reason I'm confused.
You don't mind using grub2 and at the same time are loking for a way to keep menu.lst updated automatically?

Isn't just putting grub2 on the MBR doing that job for you? It updates automatically after ubuntu kernel update, and after doing suse kernel update it should see it also with update-grub.
Isn't that what you are after?
So, you would install grub2 from karmic and tell suse not to install a bootloader when doing the install. That will keep your grub2.

---

### Post by oldfred on 2010-02-25
Some of it is just a personal preference. And the new grub2 is very good at finding other operating systems where old grub was not as good. 

But if you have a lot of systems the grub2 menu can get very large as it will show every version of every operating system & yes you can code in some restrictions. You also have to reboot into Ubuntu to update the grub2 menu where a chainboot entry never has to be updated and the operating system you are using is updated automatically. So even to reboot after a kernel update, you do not have to go into Ubuntu to update grub2 to see the newer version.

---

### Post by Cyber Akuma on 2010-02-26
> **oldfred said:**
> This is one way:
total custom menu/config file - meierfra 
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Custom_Menu)


In old grub I created a grub partition and created my own menu.lst that just chainbooted to all the operating systems. New grub can do this but grub2 does not want to be installed in a partition (PBR) to allow chainbooting to it.
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#Dedicated_GRUB_Partition)
Grub legacy:
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

I'm confused, I thought the new grub was grub2?

So you're saying that I can make the master bootloader grub2 but I would need to make all the others grub1?

> **darkod said:**
> Isn't just putting grub2 on the MBR doing that job for you? It updates automatically after ubuntu kernel update, and after doing suse kernel update it should see it also with update-grub.
Isn't that what you are after?
So, you would install grub2 from karmic and tell suse not to install a bootloader when doing the install. That will keep your grub2.

The problem is since OpenSUSE uses Grub1, it won't be able to understand grub2's menu.lst file. So if I were to for example Update OpenSUSE, and the update required a reboot, I would not be able to reboot back into OpenSUSE without first going into Ubuntu and running the grub2 update command.

----------------------------

All I am trying to do it make it so my bootloader(s) won't require any manual intervention when there is an update to any of my operating systems, I don't really mind if there is an easier method than chianloading, i'll do it if there is, I just don't want to manually keep updating the kernel filenames in the menu.lst file.

---

### Post by recluce on 2010-02-26
> **Cyber Akuma said:**
> I'm confused, I thought the new grub was grub2?

So you're saying that I can make the master bootloader grub2 but I would need to make all the others grub1?



The new GRUB is GRUB 1.97, also called GRUB2. GRUB2 uses grub.cfg instead of menu.lst. grub.cfg is usually auto-generated, not really meant to be hand-edited and thus quite complex (dare I say "cryptic"). 

The old GRUB is GRUB 0.97, also called "Legacy GRUB" or GRUB 1. Legacy GRUB uses the menu.lst file, which can be auto-generated in some cases, but is perfectly fine to edit by hand - it is heavily commented, which makes that task easy. 

> 
The problem is since OpenSUSE uses Grub1, it won't be able to understand grub2's menu.lst file. So if I were to for example Update OpenSUSE, and the update required a reboot, I would not be able to reboot back into OpenSUSE without first going into Ubuntu and running the grub2 update command.


GRUB2 does not use menu.lst

oldfreds and my idea goes as follows:

Make a small GRUB partition (as per the instructions linked by oldfred), 100 MB is plenty of room. This partition would probably be best suited for reiserfs, but ext2/3 is fine as well. As per the guide, copy the relevant legacy GRUB files to this partition (from a distribution that uses GRUB 0.97 and knows about EXT4, like Ubuntu Jaunty) and setup this instance of Legacy GRUB to use the MBR.

For one time only, you will have to edit the menu.lst file on your GRUB boot partition. Set all your OS partitions to chainload. As an example:

title        Ubuntu
root        (hd0,3)
chainloader    +1

title        OpenSuse
root         (hd0,4)
chainloader   +1

Now, in OpenSuse install and setup legacy GRUB to use the boot sector of OpenSuse's partition (not the MBR!). See the Legacy GRUB guide for details on how to do this.

In Ubuntu, install and setup GRUB2 to use the boot sector of Ubuntu's partition (again, not the MBR!).

When you turn on your computer, the MBR will be loaded and direct the system to load Legacy GRUB from the dedicated GRUB partition.

From the menu, you select the OS you want to boot - you will not see kernel versions here, just what you manually entered after "title". The chainload will cause GRUB to load the bootloader in the selected partition, whatever that bootloader may be - GRUB could not care less. So besides X different flavours of Linux, you could also boot FreeBSD, Windows or MAC OS or even MS-DOS this way.

The chainloading will load GRUB 1 for your OpenSUSE and display the kernel list generated by SUSE. Chainloading into the Ubuntu partition will bring up GRUB2 and the kernel list generated by Ubuntu. 

All kernel updates should automatically be added to the appropriate GRUB files of the distribution being updated. Note that you might see some Ubuntu kernels while in Suse's grub and vice versa. Just ignore them at this stage.

If you usually use the most recent kernel only, the secondary GRUB installations could be set not to display the menu ("Hit ESC to display the menu") and use a short timeout (3 sec or so).


> 
All I am trying to do it make it so my bootloader(s) won't require any manual intervention when there is an update to any of my operating systems, I don't really mind if there is an easier method than chianloading, i'll do it if there is, I just don't want to manually keep updating the kernel filenames in the menu.lst file.

You really should read the guides linked by oldfred, this would answer your questions better than I can answer them. But in a nutshell: using the approach described will exactly do what you want. Also, it will make GRUB (the one in the dedicated partition) independent from a specific Linux installation - so you don't loose the bootability of your system just by installing a new distribution to the wrong partition. You could even boot a system that way that contains no linux installations at all!

---

### Post by oldfred on 2010-02-26
recluce gave a good explanation of chainboot process. grub2 does not like to be installed in a partition but has to be forced. I installed it to a partition and every update did list the warning message again. But it worked fine. There may be cases where you have to reinstall the grub2 in the partition if a grub file gets moved.


[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

