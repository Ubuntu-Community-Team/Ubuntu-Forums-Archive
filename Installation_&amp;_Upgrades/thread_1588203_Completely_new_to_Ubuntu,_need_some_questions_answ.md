---
title: "Completely new to Ubuntu, need some questions answered."
date: 2010-10-04
forum: Installation &amp; Upgrades
---

### Post by GoDong-DK on 2010-10-04
Ok, I'm completely new to Ubuntu, and haven't actually installed it yet, so my questions aren't concerned about how I use it, but rather the problems of installment and more importantly how to get started.

The first thing I got a little question for is how to split my HDD into two partitions in order to install Ubuntu, as I will be dual-booting it with Windows 7. The second thing I want to ask about is how big the risk of corrupting my HDD is when installing Ubuntu, and whether I can take some precautions in order to reduce the risk of said thing. The third thing I'm gonna ask about is how to get drivers for my graphics and that alike. And fourth and last: Is it going to make a difference that I'm running it on a laptop?

---

### Post by Sylos on 2010-10-04
Hello there and welcome to the party.

1/2. Ubuntus installation process will offer you some options for installation. The easiest and most straightforward for the newer user is to allow the installer to move windows to one end of the disk and use he remaining free space. As with all partitioning this is not without risk so backing up is always a good plan. Tha being said I have done 5 or 6 installations o different ubuntu versions and variants and never had an issue.

3. This depends on your graphics card and the things you wish to do. The default installation will work without 3d accelaration and other extras from your first boot (in most cases). If you want to access the good stuff from your card you will need to install the drivers. There is a programe for this in the "System" menu which will do most cards (works in ubuntu 10.04 on my system). This should be fairly easy but could be difficult depending on your card. If you need more info post your card details.

4. Using a laptop shouldnt be a issue per se other than the whole issue of individual hardware having individual issues. If it helps ease your mind, Im typing on a laptop running ubuntu that installed ok first time.

Best of luck.

---

### Post by GoDong-DK on 2010-10-04
> **Sylos said:**
> Hello there and welcome to the party.

1/2. Ubuntus installation process will offer you some options for installation. The easiest and most straightforward for the newer user is to allow the installer to move windows to one end of the disk and use he remaining free space. As with all partitioning this is not without risk so backing up is always a good plan. Tha being said I have done 5 or 6 installations o different ubuntu versions and variants and never had an issue.

3. This depends on your graphics card and the things you wish to do. The default installation will work without 3d accelaration and other extras from your first boot (in most cases). If you want to access the good stuff from your card you will need to install the drivers. There is a programe for this in the "System" menu which will do most cards (works in ubuntu 10.04 on my system). This should be fairly easy but could be difficult depending on your card. If you need more info post your card details.

4. Using a laptop shouldnt be a issue per se other than the whole issue of individual hardware having individual issues. If it helps ease your mind, Im typing on a laptop running ubuntu that installed ok first time.

Best of luck.

Thanks, that cleared some things up, and the thing tht you've done it on a lappy reassures me in that it wouldn't be a problem. So, thanks!

---

### Post by Sylos on 2010-10-04
No problem. I hope all goes well.

If you hit issues then post on the forum here. I think the best attribute of ubuntu is the community - always somebody who knows to lend a hand.

---

### Post by GoDong-DK on 2010-10-04
> **Sylos said:**
> No problem. I hope all goes well.

If you hit issues then post on the forum here. I think the best attribute of ubuntu is the community - always somebody who knows to lend a hand.

That's what I've been told ;-)

---

### Post by Zimmer on 2010-10-04
Do a bit of serious reading first...

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
For alternative to dual booting read about WUBI (not used  it personally)

[http://members.iinet.net/~herman546/index.html](http://members.iinet.net/~herman546/index.html)
Lots of detailed info here and sound advice regarding backing up data (and your MBR) and what you are going to prepare for if things go wrong...

There are lots of guides out there and some can get outdated quite quickly as Ubuntu moves on in its 6 month cycle and Windows goes its own way,too.

Ask yourself  'What do I want to do, and why..?'
My own tip FWIW..
Resizing a Windows partition ? Let Windows handle that at first, then use Ubuntu to work on the freed space...

Does Ubuntu 'have' to go on the laptop HDD? or do you have an external portable drive handy?
(This is from someone who has Vista and 8.04 on a laptop and 3 different Linux  installs on an external USB drive ).
I will get you a link on how to make space using Windows ...

---

### Post by Zimmer on 2010-10-04
This page shows how to get free space using Windows tools.
[http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2](http://apcmag.com/how_to_dualboot_vista_with_linux_vista_installed_first.htm?page=2)

This is the guide I used to get my first dual boot with Vista and 8.04 (using EasyBCD as the boot loader).

When I installed Ubuntu 10.04 to my external disk recently I allowed it to write GRUB2 to the MBR of the external disk. Now GRUB2 on the external recognises ALL the installs and I can boot to Vista or 8.04 from there.

HOWEVER.. I am not sure what the consequences are of allowing GRUB2 to write itself to the MBR of my Vista disk, should , for some reason, I have a problem booting.. without a Vista install disk I have (at the moment) no way of restoring the MBR as Vista wants it other than doing a restore from the hidden Windows partition , which would likely attempt (and probably succeed in) erasing the 8.04 install and my data partition in the process.
(The data is backed up, in case you were wondering..)

Having used Ubuntu for the past 6 years Vista would be no great loss.. EXCEPT for the Line6 software I need to talk to my PodXT live and Variax guitar from time to time. If push came to shove I guess I would be able to dig out an old Win98 or Win95 disk to get by with..
What about you? How would you recover Win7 ? It is a question I believe  you should ask yourself now.

---

### Post by florus on 2010-10-04
General advice: 
1) delete windows restore points and defrag disk before shrinking windows partition
2) always use windows to shrink a windows partition
3) when installing Ubuntu, use gparted to create separate root(system) and home(data) partitions - it will make your life much easier in the future.
4) I use a laptop to dual boot Ubuntu development releases with Windows without any problems, so you should be very safe with a stable release.

---

### Post by oldfred on 2010-10-04
I like to have several repair disks available so I can boot in an emergency. I used to write 3 or 5 CDs with system rescue, gparted, supergrub, Ubuntu install and maybe others. Now I have them all on one USB and just update. I keep one CD updated just incase the USB fails.

You also should have windows repair CDs.

If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

And always know how to reinstall the MBR with which ever operating system you have on that drive.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

---

### Post by GoDong-DK on 2010-10-05
I do not have an external HDD, so I can't install it somewhere else than  the laptop's HDD, sadly. My backup will be put on my uncle's external, but, obviously, I can't really install Linux on that. I'm going to read up a bit more, but I understand that GRUB is a boot manager, and I'm pretty certain that I will be able to get some help from my uncle, and possibly another person I know who runs various Linux distros. I've heard some bad things about "WUBI" so I would be happy if someone experienced with this program could help me out at that point.

I'll download that Windows 7 repair disk aswell.

---

### Post by Mark Phelps on 2010-10-05
Whenever installing Ubuntu onto a Win7 preloaded PC, the safest approach is to shrink the Win7 OS partition using Win7 Disk Management utility first, leaving the new unallocated space as is, and then letting the Ubuntu installer format the unallocated space.

Simply allowing the Ubuntu installer to shrink the Win7 OS partition is risking filesystem corruption that could render Win7 then unbootable.  If you make the Win7 Repair CD, you will then have the means to repair that corruption.  But why take that chance when it is completely avoidable?

---

### Post by Sylos on 2010-10-05
Can anybody explain the reason why it is more risky to let ubuntu resize the partition rather than get windows to do it. Do they both not carry the same risks in moving data and risking corruption?

Not trying to start an argument - just curious

---

### Post by oldfred on 2010-10-05
Herman claims it is not with the installer, but gparted would move the start of the windows partition to 63 when windows was at 2048, if checkbox not unchecked. That change messed with windows and caused issues. Now the Ubuntu installer has changed from the sector 63 start to sector 2048 as the default and the issue may be moot, but we still suggest using the windows tools. Any change to windows can cause issues and it is better to change it in two steps ( with windows reboot) so windows can run its chkdsk after the resize before installing Ubuntu.

starting with Vista - MSoft made some changes to the way it installs itself in a partition. Gparted can deal with it but should have the round to cylinder unchecked.
Herman on checkbox
[http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17](http://www.uluga.ubuntuforums.org/showpost.php?p=7816261&postcount=17)
Vista and Partitioning - details
[http://www.multibooters.co.uk/partitions.html](http://www.multibooters.co.uk/partitions.html)

---

### Post by matt_symes on 2010-10-05
Hi, 
 
I you are really worried about you existing configuration, use something like clonezilla a back up and clone your entire harddrive first. That way you can rollback if there are any issues.
I would also suggest running ubuntu as a live CD first. That way you will see if all you hardware is supported.
 
Kind regards

---

