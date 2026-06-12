---
title: "Dual boot problems, again"
date: 2010-01-10
forum: Installation &amp; Upgrades
---

### Post by RogerD on 2010-01-10
Hi

Having problems creating a Windows XP/9.10 dual boot system. Not sure if it's relevant, but here's the recent history of the operating system installations on the PC in question:

It was a dual boot XP/Hardy installation, but the XP got so slow, probably some sort of virus infection, that I decided to try and re-format the whole disk and start again. For some reason I couldn't re-format the disk from within XP, neither could I do a fresh XP installation. In the end I installed 9.10 on the whole disk, then re-installed XP on, what I assumed was the whole disk. So I've now I've got a functioning XP installation and I want to install 9.10 along side. I've got an 80GB hard disk, and I want to assign around 20GB to XP, which is only used as the 'OS of last resort', and the rest to 9.10.

Anyway, I start my 9.10 installation from the live CD, and get to the prepare disk space screen. On Youtube I found promising demonstration of a dual boot installation which said that at this stage I should have three options:

1 Erase and use the entire disk (which I obviously don't want)
2 Install Ubuntu alongside Windows (which is want I want to do)
3 Specify partitions manually (advanced) - I'm not 'advanced, so really I rather not go there.

For some reason, I don't have option 2, so I've no choice but to select option 3.

By the way, at the top of the 'Prepare disk space' screen I've a blue bar with a small green section on the right. The blue bit is assigned to XP (/dev/sda1) 74.2GB and the green bit is assigned to sway (/dev/sda5) 2.1GB.

So I click on Forward, and eventually get the 'Prepare partitions' screen. At the top there's a green bar with an orange bit on the right. The green bit is identified as 'sda1 (ntfs) 74.2GB and the orange bit as sda5 (linux-swap) 2.1GB.

The the window below there are three lines:

/dev/sda
 /dev/sda1 nfs 79653MB unknown
 /dev/sda5 swap 2303MB 0MB

Really I don't know what to do next, but I've found the 'Partitioning your disks' within the on-line Ubuntu documentation (s://help.ubuntu.com/9.10/switching/installing-partitioning.html), which tells me I must first resize the windows partition, and that I do this by right clicking on the Windows partition and selecting resize. I assume this is the line /dev/sda1 nfts, but when I do this, the options are 'change', 'delete' 'revert'. Maybe 'change' is equivalent to 'resize', but when I do that I open a 'Edit partition' window and I've no idea of how to go forward.

Can anyone help, or point me in the direction of some clear instructions on creating a dualboot system that matches what I see on my screen?

Roger D

---

### Post by montres on 2010-01-10
How come you couldn't make a clean XP installation first?

---

### Post by spiky001 on 2010-01-10
so have you got xp running now

---

### Post by RogerD on 2010-01-10
Yes, XP is running fine

---

### Post by spiky001 on 2010-01-10
I know this is abit late but i make the xp patin the size i want when loading xp in the 1st place then load on whats left dont know if you wanna do it that way.  Or when you get to load 9 10 i,m sure if you get to the pation part i 9 10 you can slide a slider to shrink xp partion not had to do that so if i,m wrong hope some1 can correct me. Otherwise you can reload xp make th partion the size you want then go from there

---

### Post by RogerD on 2010-01-10
Hmmm... I'm loathed to have to start all over again re-installing XP - a real pain. Also, can't see any sign of a slider

---

### Post by spiky001 on 2010-01-10
You could download Gparted live cd run that not used it myself but that can resize partions

---

### Post by spiky001 on 2010-01-10
[http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)

---

### Post by RogerD on 2010-01-10
Reluctant to do that - my point is that I'm pretty sure if I knew what to do, I'd be able to achieve a dual boot installation using the options available within the Ubuntu installation process

---

### Post by spiky001 on 2010-01-10
sorry cant help you any more lack of experience i,m sure some1 can help tho

---

### Post by RogerD on 2010-01-10
Thanks for your interest. I think I'm right about wanting to stick with the standard installation tool/process, I'm pretty sure it's based on gparted in some way.

---

### Post by darkod on 2010-01-10
First of all, Gparted is included in the ubuntu 9.10 live cd. If you boot with the cd with Try Ubuntu option, you can find it in System - Administration. You can always use it from there.
I know you probably don't want to reinstall XP again but because resizing XP can be problematic because of XP itself, here is my suggestion.
Boot with ubuntu cd, Try Ubuntu option. Open Gparted. Delete all partitions on the hdd (only if there is no dtaa you need on it). If any partition has like a keys symbol next to it, it's mounted and can't be deleted. Right click on that partition and use Unmount or Swapoff (for swap partitions). Keys will be gone and you work on it.
After all partitions are deleted, hit the big green tick mark button in Gparted toolbar to execute the commands (it only schedules them until you are sure you want to proceed).
After executing the commands you'll have a blank hdd. Create ntfs partition with the size you want for XP. DO NOT create any other partitions, definitely not for ubuntu. Hit the green button again to finish creating the ntfs partition.
Boot with XP install cd and install it on the partition you prepared. Check it's booting and working fine. If you want a second ntfs partition, create it with XP Disk Management. Be careful to leave enough unallocated space for ubuntu, at least 25-30GB. DO NOT prepare partitions for ubuntu from windows.
Boot with ubuntu cd, Install Ubuntu option and in step 4 tell it to use Largest Available Free space. It will use the free unallocated unpartitioned space you left for it and set itself there.
That should be it.

---

### Post by RogerD on 2010-01-10
Thanks for the detailed advice - it inspires confidence.
The weather in the UK is pretty terrible at the moment, it's too cold to do much else, so I'm going for the Gparted, re-install XP option.

Applied Gparted, to give hard disk with /dev/sda1 ntfs 20.45GiB, and unallocated 55.87GiB

Insterted XP disk and started installation. At first all seems to be going well, but then get message:

A problem has been detected and Windows has been shut down to prevent damage to your computer.

If this is the first time you've seen this stop error screen, restart your computer. If this screen appears again, follow these steps:

Check for Virsuses on your computer. Remove any newly installed hard drives or hard drive controllers. Check hour hard drive to make sure it is properly configured and terminated. Run CHKDSK /F to check for hard drive corruption, and then restart your computer.

Technical information:

*** STOP: 0X0000007b (0XF797E63C,0XC0000034,0X00000000,0X00000000)

Which is just the message I got when I originally tried to do a clean XP install, which is why I installed 9.10

Any ideas?

---

### Post by darkod on 2010-01-10
I have no clue about that error, but the first item in google when you google the error says:
[http://support.microsoft.com/kb/324103](http://support.microsoft.com/kb/324103)

Enter the error number in google and check other links too, if feeling like it.

What can I say, Windows. :)

---

### Post by RogerD on 2010-01-10
Thanks for your help. Looks like my best bet is just to abandon XP on this machine.

Roger D

---

### Post by qrazydutch on 2010-01-11
You could have a boot virus...recommend clean disk, start from scratch (I know, I know):D

Boot from the XP disk, get to DOS prompt and nuke your MBR..

Boot from the windows XP CD, press the "R" key in the setup in order to start the restoration console. Select your windows XP installation from the list, and enter the administrator password.
Enter the command: "FIXMBR" (without the quotes) at the input prompt and confirm the next question with a "Y" (without the quotes). Use exit to restore the computer.

I had to use this on a PC that I had corrupted the MBR with by using a boot manager.

Worked perfectly. This may have been posted before, and if so, forgive me. If not, now you know how to repair your MBR. By the way MBR stands for Master Boot Record. THis procedure kind of replaced Fdisk I think. 

just a thought. Then since XP still boots, run the LINUX boot again and see if the second prompt comes up, me thinketh LINUX smells a virus so it is not showing option 2...
(from "newbie" in LINUX)

---

### Post by qrazydutch on 2010-01-11
> **RogerD said:**
> Thanks for your interest. I think I'm right about wanting to stick with the standard installation tool/process, I'm pretty sure it's based on gparted in some way.

[http://www.techzonez.com/forums/showthread.php?t=3975](http://www.techzonez.com/forums/showthread.php?t=3975)

it a link that discussed hard drives etc

---

