---
title: "Clean install Ubuntu on a dual boot with windows"
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by ProcuratorIncendia on 2010-10-04
Hello those who read this,
A while ago I messed up my Ubuntu installation so I decided to boot the install from the disc again and overwrite it. It turns out the installation disc does not give you the option to replace a current Ubuntu installation so I was forced to take more space out of my windows [vista] installation.
This means I now have 1 ruined Lucid Ubuntu OS, 1 Working Lucid Ubuntu OS and a windows Vista OS system.
Is it safe to delete my ruined Ubuntu from inside vista?
Is it possible to overwrite my Ubuntu installations?
How can I delete them both and then install Lucid again?

I want to know this now as Maverick Meerkat will be released on Sunday and I want to install that in a clean installation without deleting my vista installation.

I do not have the Vista installation disc because Vista came pre-installed. I am not willing to buy anything.

If you help, thank-you...

---

### Post by Mark Phelps on 2010-10-04
> **ProcuratorIncendia said:**
> 
Is it safe to delete my ruined Ubuntu from inside vista?
IF you installed via Wubi, then use Vista to remove it like you would remove any other program.  But if you installed to separate partitions, do not use Vista; instead, suggest you download and burn a GParted LiveCD (which you can get from distrowatch.com), boot from that, and use it to remove the unwanted partitions.

> Is it possible to overwrite my Ubuntu installations?
Yes, but you have to use manual partitioning mode and select the partitions already there.  If you have removed them, just select the largest free space.
> How can I delete them both and then install Lucid again? Already covered this -- remove the partitions and select the largest free space.

> I do not have the Vista installation disc because Vista came pre-installed. I am not willing to buy anything.
There are links you can use to download a burn a Vista Repair CD, but it's not an installation disk, and can not be used to install or reinstall Vista.

> If you did the opposite of helping you get nothing... Threatening folks is not a good way of asking for help ...

---

### Post by ProcuratorIncendia on 2010-10-04
Thanks for the reply...[I]No I didn't you Wubi...It's not recommended for log term use.
I tried burning Gparted to a disk before but my system didn't boot from it.[/I]
Are you saying all I have to do is delete the Ubuntu partitions and then boot from the disk then select free space as the partition location?

---

### Post by oldfred on 2010-10-04
I like to use the separate gparted liveCD, but you can use the gparted in Ubuntu. You may have to swapoff as it usually mounts the swap partition. Click on the swap partition and swapoff.

You may not have had the free space option if you did not have any free space.

Besure to have good backups. If you want to reuse partitions then you have to use manual install.

If you are keeping Vista you should resize from Vista's MMC. Reboot Vista to make sure it is ok with its new size. It will run chkdsk to verify its changes.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by ProcuratorIncendia on 2010-10-04
@Oldfred: You didn't answer my questions and I don't understand your post.
[QUOTE=PI]
@Mark Phelps: Thanks for the reply...No I didn't use Wubi...It's not recommended for log term use.
I tried burning Gparted to a disk before but my system didn't boot from it.
Are you saying all I have to do is delete the Ubuntu partitions and then boot from the disk then select free space as the partition location?[/QUOTE]

---

### Post by oldfred on 2010-10-04
If you have nothing you want to save in the Ubuntu partitions, yes you can just delete them and install to the free space. It will automatically create / (root) and swap.

If you want a separate /home or NTFS partition as a shared data partition you need to use gparted first and then use the manual install to choose root & /home for the install.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
[http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html](http://www.ibm.com/developerworks/linux/library/l-resizing-partitions-1/index.html)

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

Full Disk install Lucid Graphical (Maverick is a little different in how the screens look, but same install)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by ProcuratorIncendia on 2010-10-05
So am I correct in thinking that all I must do is delete both my Ubuntu Partitions [After making a list of the programs I want to re-install] and then shutdown the computer, stick the disk in, and then install?

Or do I have to replace Grub2 with the windows OS bootloader thingy?

---

### Post by oldfred on 2010-10-05
When you install Ubuntu it will install grub, it usually defaults to installing grub on the first drive (sda) unless you tell it otherwise.

To list all your installed apps:


from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)

---

### Post by ProcuratorIncendia on 2010-10-05
That didn't answer my question...I know Ubuntu defaults grub2...But:
[QUOTE=PI]So am I correct in thinking that all I must do is delete both my Ubuntu Partitions [After making a list of the programs I want to re-install] and then shutdown the computer, stick the disk in, and then install?

Or do I have to replace Grub2 with the windows OS bootloader thingy?[/QUOTE]
Answer like:
1. Yes/No...
2. Yes/No...

---

### Post by oldfred on 2010-10-05
Yes you can delete the partitions and then install to the free space. The installer has several choices, full disk, side by side where it trys to shrink an existing partition and create new, install into free space, or manual where you create the partitions in advance (although now I think it lets you create during the install) and assign partitions to root and other if desired like /home.

You do not need grub to install, but the installed will install a new copy of grub2 so you can boot your new install.

---

### Post by ProcuratorIncendia on 2010-10-05
Thank-you, I think this is just about solved. Hopefully it works...:popcorn:

---

