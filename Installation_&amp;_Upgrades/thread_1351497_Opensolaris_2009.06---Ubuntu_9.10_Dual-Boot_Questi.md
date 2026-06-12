---
title: "Opensolaris 2009.06---Ubuntu 9.10 Dual-Boot Question"
date: 2009-12-10
forum: Installation &amp; Upgrades
---

### Post by grubdude on 2009-12-10
[SIZE=3][FONT=Calibri]Hi,[/FONT][/SIZE]

[SIZE=3][FONT=Calibri]Does anyone have reliable experience working with the new Linux grub version 2, at all? I am trying to dual boot Opensolaris 2009.06 with Ubuntu 9.10 and it is more tricky to edit the new version Linux grub menu versus the old. I don't want to trash my install in the process....[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Unfortunately, I installed Opensolaris first and then Linux, so the grub menu is showing from Linux and boots into Linux only. It might have been better to install opensolaris second and modify its grub to see the Linux install. unfortunately ZFS and EXT4 file systems don't talk very well to each other....[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]I am fairly new to Linux/Unix so if you know a definite way to do this can you please put the exact lines etc. that need to be added to the grub2 menu to recognize opensolaris.[/FONT][/SIZE]
 
[SIZE=3][FONT=Calibri]Have 80gb hd on notebook split in half..First partition is opensolaris, second is Ubuntu 9.10 with included swap file. Thanks.[/FONT][/SIZE]

[SIZE=3][FONT=Calibri]Really don't want to hose either install with my lack of experience. Thanks in advance!;)[/FONT][/SIZE]

---

### Post by grubdude on 2009-12-11
Anyone have any feedback on this? Thanks;)

---

### Post by grubdude on 2009-12-12
I know that there must be someone on here that knows this.:)

---

### Post by grubdude on 2009-12-12
Will startup manager detect Opensolaris 2009.06?

---

### Post by grubdude on 2009-12-13
Anyone?;)

---

### Post by grubdude on 2009-12-13
Anyone know other forums where I might get some help with this. Seems like no one on here has any feedback.....Thanks;)

---

### Post by grubdude on 2009-12-14
Let me try again. Anyone?;):confused:

---

### Post by oldfred on 2009-12-14
Startup manager has not been updated to grub2 yet.

ranch hand has a variety of linked entries but I do not see a Open solaris. Entries for 40_custom.
[http://ubuntuforums.org/showthread.php?p=8191211#post8191211](http://ubuntuforums.org/showthread.php?p=8191211#post8191211)

menuentry "Mandriva-Gnome" {
        linux (hd0,12)/boot/vmlinuz
        initrd (hd0,12)/boot/initrd.img
}

IF you install open solaris' boot loader to its partition you can chainload to it.

menuentry "Chainload Other System on sda1" {
set root=(hd0,1)
chainloader +1

---

### Post by JorgeArturo on 2009-12-15
> **grubdude said:**
> Let me try again. Anyone?;):confused:
I have managed to install OpenSolaris 2009.06 and Ubuntu 9.10, and both work beautifully, but it took some effort.

I suggest you install Ubuntu first and then copy (in a flash drive) the grub.cfg file (/boot/grub/grub.cfg),
so that after you install OpenSolaris, you can edit the menu.lst file with the info supplied by Ubuntu.

Other than that, good luck!

I have now Vista, OpenSolaris and Ubuntu in my first harddrive and SuSE 11.2 in my second, but that is another issue that I have not resolved yet.

---

### Post by grubdude on 2009-12-15
Thanks to you both for your comments. I was hoping not to have to unistall and reinstall both OSs to accomplish this but probably easier to install Ubuntu first and follow your advice....
 
I have already customized my Ubuntu install and would rather not mess with it but on the other hand, I would like o be able to access Opensolaris which I cannot at this point from the Ubuntu loader....
 
Thanks.;)
 
**oldfred** can you please be a little more specific for a novice about how to configure the second option via chainloader? Thanks.

---

### Post by oldfred on 2009-12-15
Chainloading is just using one boot and linking to all the other operating systems. Grub2 & Ubuntu try to add direct boot to every system and in most cases that works.

To chainboot you have to have another bootloader installed. It can be on another hard drive or installed to the partition boot sector which is how windows boots, part in MBR which just links to the part in the PBR. That is how grub is able to chainboot windows since it just jumps to the windows PBR like the windows MBR boot would.

Grub2 does not like to be installed to a partition but can be. Old grub works without complaint. I do not know about the boot loader Opensolaris uses. When installing Ubuntu you can select advanced and install grub to the PBR. You can also follow the grub install instructions but instead of installing to sda you install to sda3 for example or setup (hd0,3).

Grub2 with chainboot examples (search on chain)
[http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0](http://kubuntuforums.net/forums/index.php?action=printpage;topic=3106368.0)

These are examples using old grub but you can add a chainboot entry in new grub also.
chainboot 145 systems
[http://www.justlinux.com/forum/showthread.php?p=861282#post861282](http://www.justlinux.com/forum/showthread.php?p=861282#post861282)
[http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_](http://members.iinet.net.au/~herman546/p15.html#How_to_make_a_separate_Grub_Partition_)

---

### Post by grubdude on 2009-12-15
So, given my above install scenario, do you think that there is a way to make this work without a reinstall.
 
I believe that the Opensolaris grub is fairly similar to the old grub versus grub2.
 
As you can see, I am trying to avoid reinstall if possible.....;)
 
Unfortunately the grub2 does not recognize the Opensolaris ZFS file structure or else it would have automatically added it to the grub2 menu for booting.

---

### Post by oldfred on 2009-12-15
Did Opensolaris install its bootloader to the MBR and it was overwritten or is it in a partition? It should be possible to install the Opensolaris boot loader to a partition.

Old grub originally could not read ext4 and cannot read NTFS it just chainloads to the other boot loader that does work. 

The question is how to install the Opensolaris boot loader to a partition.

You can see where boot loaders are installed with the boot_info script.

Boot Info Script 0.41 courtesy of forum member meierfra 
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/) 
Instructions:  louieb's 
 [http://ubuntuforums.org/showthread.php?t=1291280](http://ubuntuforums.org/showthread.php?t=1291280)
 
or as example if on desktop or  downloads directory from liveCD download: 
sudo bash ~/Desktop/boot_info_script*.sh
sudo bash ~/Downloads/boot_info_script*.sh 
This will create a RESULTS.txt file in the same directory.(Ver41 put mine in my home dir). Paste the entire contents of that file back here, it can be big. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text, to make it easier to view.

---

### Post by grubdude on 2009-12-15
I am pretty sure Opensolaris installed bootloadfer in MBR since it was installed first and booted fine until I installed Ubuntu and it was most likely overwritten....The install is in 2 contiguous partitions on one hard drive....Thanks.

---

### Post by oldfred on 2009-12-15
I just read somewhere that Opensolaris has to be first and uses a modified old grub. I would try to install grub to the boot partition for opensolaris from opensolaris if possible.

You will see what you have with the script.

---

### Post by grubdude on 2009-12-16
I read that too somewhere, which is why I installed Opensolaris first but I think that was written when we were still using grub versus grub2. Not sure if it matters.....
 
Problem is, how do I access Opensolaris from my harddrive to even install or modify the Opensolaris grub?
 
Thanks

---

### Post by oldfred on 2009-12-16
I did a quick search and it does not look like opensolaris supports chainbooting into it but you can install Ubuntu's grub to a partition and chainboot to it from opensolaris.

If you need more help the opensolaris folks should be able to help you.

[http://www.linux.com/community/blogs/multi-boot-opensolaris-and-linux.html](http://www.linux.com/community/blogs/multi-boot-opensolaris-and-linux.html)
[http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and](http://blogs.sun.com/avinashjoshi/entry/mount_opensolaris_zfs_partition_and)
[http://www.corriganjc.net/weblog/archives/2009/01/dual_booting_op.html](http://www.corriganjc.net/weblog/archives/2009/01/dual_booting_op.html)

---

### Post by grubdude on 2009-12-16
Would that imply having to reinstall Ubuntu first and Opensolaris second?

---

### Post by oldfred on 2009-12-16
If you look at the links I gave you they show how to reinstall Opensolaris grub and add menu entries for other systems. It may be better to chainboot because I bet Opensolaris will not work with ext4 but you still can chainboot to Ubuntu if you put a copy of Ubuntu grub into its partition. Grub2 will complain (see below) but will work as I have done that.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_to_a_Partition)
grub-setup -v /dev/sda6
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force 

Then you can add a standard chainboot entry in opensolaris to boot ubuntu.

---

