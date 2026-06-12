---
title: "Dual boot 13.04 and Win7 - boots only to Windows"
date: 2013-06-22
forum: Installation &amp; Upgrades
---

### Post by gilch on 2013-06-22
(I am not an advanced user)
I used to have a dual boot system - Win7 and Ubuntu 12.04 - Everything was working fine.
My motherboard blew up. I had to replace it, and they installed Win7.

I tried to install Ubuntu 13.04.
The install apparently recognized that my disk had Ubuntu 12.04, because it accepted to UPGRADE to 13.04.
Continued install until the end.

After that, I tried to boot the system, but ONLY Win7 will boot.

I am really stuck now. (Win7 works fine, but I miss Ubuntu)

Should I try to install Ubuntu 1304 from scratch?

Thanks in advance.
Gilles

---

### Post by oldfred on 2013-06-22
If you have no data to save, a reinstall is often a quick solution. But you may be able to repair with this or we can review the BootInfo report.

 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by gilch on 2013-06-22
Thanks for your reply.
I installed and ran Boot-Repair.
It gave the following URL:
[http://paste.ubuntu.com/5790760/](http://paste.ubuntu.com/5790760/)

I hope this means something to you...
Gilles

---

### Post by oldfred on 2013-06-22
I would not run the auto repair that installs to all disks. You could reinstall just to sdb. Some BIOS need a boot flag on a drive to let you boot. If you have issues add a boot flag to any primary partition on sdb as grub does not use it.

If you are booting Windows directly, you have BIOS set to boot the drive that is sda. Change BIOS to boot from the drive that is sdb or the other 320GB drive. I have two 160GB drives and sometimes had to experiment before I understood how BIOS enumerated them.

---

### Post by gilch on 2013-06-22
I'm afraid this is getting beyond my capabilities.
I tried to modify the boot drive, but the bios doesn't say "sda" or "sdb". Just a bunch of numbers and letters. I tried the five and when it ONLY boots in Windows, it gives me this: (I had made a typo originally, saying that it did not boot in Windows).

error: file not found
grub rescue

Now I am lost.
Gilles

---

### Post by oldfred on 2013-06-22
Yes, BIOS shows drive by model & serial number. Model often has size inside it somewhere. So you should have two that start similarly but then have different serial numbers.

Then grub does have an error and you should use Boot-Repair to reinstall to sdb. But change default of all drives to just sdb. I believe that is an option you have to change. You want to keep the Windows boot loader in sda.

---

### Post by gilch on 2013-06-22
Ran into difficulties.
1 ---- boot-repair was not found, so I reinstalled it.
2 ---- then I made a selection for grub to use sdb
3 ---- then boot-repair asked me to run three chroot commands.
        the first one was
        sudo chroot "/mnt/boot-sav/sdb2" dpkg -configure -a
4 ---- when I ran that, it said
        Options marked [*] produce a lot of output - pipe it through 'less' or 'more' !

????So I was lost again (sorry)
Gilles

---

### Post by oldfred on 2013-06-22
Are you sure it is one line? I am not specifically familar with that set of command from boot repair, but you usually chroot press enter, then run other commands one at a time.
Also quotes may not be correct. Boot-Repair must have created mount point.

sudo chroot /mnt/boot-sav/sdb2
dpkg -configure -a

spaces are also important, often best to copy & paste.

If running Boot-Repair from an Ubuntu live installer, you have to reinstall each time you reboot. You can download a versions with it installed as a repair tool.

       LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by gilch on 2013-06-22
I got the three chroot to run this time.
When I rebooted, it booted still in Windows.

I have to leave now, I hope I can get some more of your help tomorrow perhaps?
Thanks for trying real hard to help.
Gilles

---

### Post by oldfred on 2013-06-22
Golfing early, but will be around later in day.
I regularly run an Advanced search on all my posts and it shows those with new info.

---

### Post by gilch on 2013-06-23
I don't have any new info. But, I guess I have to say something so that your Advanced search finds me !

---

### Post by oldfred on 2013-06-23
Run a new copy of the BootInfo report.

Did you still get errors on the updates?

---

### Post by gilch on 2013-06-23
New Bootinfo report:

[http://paste.ubuntu.com/5794039/](http://paste.ubuntu.com/5794039/)

---

### Post by oldfred on 2013-06-23
I am not seeing anything with BootInfo report.

This should not be related, but may cause other issues.

>  /dev/sdb3      ext4       246G  229G  4.9G  98% /mnt/boot-sav/sdb3



When a drive gets that full you often have issues. I believe that is your /home.

---

### Post by gilch on 2013-06-24
Would it mean that the only solution would be to re-install Ubuntu 13.04 from scratch? Or should I install 12.04?

---

### Post by oldfred on 2013-06-24
Sometimes a reinstall is the quickest solution. But we like to try to fix things. :)

But if your /home is 98% full a reinstall does not change that. 

I have both 12.04 as my main install and 12.10, 13.04 , & 13.10 installed in 25GB / (root) partitions just to see the changes, so when we get to 14.04 and install that I have a better idea of what has changed along the way.
Very new hardware need the newest version as the kernel & drivers have changes for the new hardware.

---

### Post by gilch on 2013-06-24
So, how do I erase that non-functioning 98% full drive?
I cannot see it in Windows. If I knew how to identify it, could I reformat it while installing a fresh copy of 13.04? Here is what Windows shows (3 or 4 drives?):
- ST3320620AS ATA Device
- ST3320620AS ATA Device (Is this an extended partition? - it shows as empty. There are no files in it)
- WDC WD10EACS-00D6B0 ATA Device
- WDC WD10EACS-00ZJB0 ATA Device

Should I open the box and look at the physical drives to identify it? Would that help?
I don't want to risk erasing anything in those 4 (3?) drives.

---

### Post by oldfred on 2013-06-24
Windows does not show Linux formatted partitions. Only use Windows to resize the Windows partition, not for any Linux partitions or creating new partitons.

But that shows you have 229GB of your data in your /home, are you sure you want to erase it?
Understand /home is not a drive but a partition. As sdb3 it is the third partition on sdb drive which is the Linux formated 320GB drive where the other 320GB drive is your Windows install.

---

### Post by gilch on 2013-06-24
Is it a case where the drive is too full (98%) making it impossible to change the grub, and therefore there is no way of doing anything? (catch 22) I cannot see the drive to empty some of its content.
I am looking for a solution that does not seem to exist.

What if I installed 13.04 into the Windows partition that is empty? I don't have any idea how I would be able to identify that partition to install 13.04 in it.

Sorry if I cannot come up with "intelligent" ideas.

---

### Post by oldfred on 2013-06-24
What is all that data. You should have backups anyway, but can you remove some of it?

You have multiple drives and it looks like the others have some space. It just you never should let a partition get full. With Windows you generally want 30% free, and at only 10% free it just about stops working. 
Linux trys to hide 5% so that you do not crash system when you run out of room.
Your /home only has some user settings and data for applications, so an install should not have to write much into /home but with 2% free, you do not have any space.

Without knowing how you want to organize data which is very personal anyway, I cannot really suggest.
I normally keep a 25GB / (root) including my /home which is only about 2GB of the total use of 9GB in the 25GB. But I have lots of data in other data partitions, one NTFS and the others ext3 or ext4.

 RecoverLostDiskSpace
[https://help.ubuntu.com/community/RecoverLostDiskSpace](https://help.ubuntu.com/community/RecoverLostDiskSpace)
HOWTO: Recover Lost Disk Space - drs305
[http://ubuntuforums.org/showthread.php?t=1122670](http://ubuntuforums.org/showthread.php?t=1122670)
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)
HOWTO: Cleaning up all those unnecessary junk files...
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)
    Caution deborphan will delete anything you manually installed. See comment:
Better to use Synaptic to select the ones you no longer want. Also you get notified about dependencies to be removed and can reconsider, if need be.
[http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc](http://lifehacker.com/5817282/what-kind-of-maintenance-do-i-need-to-do-on-my-linux-pc)

---

### Post by gilch on 2013-06-24
I think I have been able to look at the files in my "sdb3".   I could delete or transfer most of that. BUt when I try to do that it tells me I don't have the permission to change anything. How do I give myself permission?

---

### Post by oldfred on 2013-06-25
From a liveCD you should have permission as there is no owner. Perhaps it sees the ownership does not match.

you can try this, but understand that in this mode you can damage system, so you want to not modify system partitions or any of the normally hidden files & folders. Not for normal use.

gksu nautilus

From a working install that loads a graphical file manager with root permissions. Since liveCD has no passwork, if it asks just click thru.

---

### Post by gilch on 2013-06-25
It's me again. I am not able to change, move or cut or delete any file with this CD Ubuntu.
If I look at Permissions, it says "You are not the owner, so you cannot change these permissions."
I tried gksu nautilus...it does not show the sdb files.

---

### Post by oldfred on 2013-06-25
nautilus shows the files and gksu nautilus does not?

---

### Post by gilch on 2013-06-25
CORRECTION:::::::::::::::::

IGNORE THIS MESSAGE:
When I use the Files icon on the desktop, I see Places and two other sections called Devices and Network.
In Devices, I see all the drives, including the Windows one. When I click on the device called "268 GB..." I see my files.

gksu nautilus only shows me the "Places" section, so I don;t see 268 files/ Is my system screwed up or not !!!

READ THIS ONE INSTEAD:

This time I used "sudo gksu nautilus" and it showed me all the files that I could see before. IN here I am allowed to cut or transfer files. WHich is what I am going to do next.

(Perhaps I had entered the nautilus command wrongly before). Thanks for your patience.  I will tell you when the drive is a sensible size.

---

### Post by oldfred on 2013-06-25
With gui apps you are supposed to use the gui version of sudo - gksu or gksudo.  
I am surprised that sudo gksu nautilus would work as you have sudo twice, once command line & once gui?

---

### Post by gilch on 2013-06-25
However I got to where I am, I did delete and transfer a lot of files, so that we should be around 60-70% full.
Now, what is the next step?
I ran another boor-repair summary: [http://paste.ubuntu.com/5800096/](http://paste.ubuntu.com/5800096/)

---

### Post by oldfred on 2013-06-25
If you boot with one time boot key (f12 on my system) the drive that is sda (one of the two 320GB drives) , does Windows boot without issue?

And if you boot from the drive that is sdb (the other 320GB drive) that has grub in the MBR, does it boot?

If you run this it shows your drives, and then if you run it without the -short you will see more detail including serial number. Usually in BIOS model & serial number are combined.

sudo lshw -C Disk -short

---

### Post by gilch on 2013-06-26
The first 320GB boots Windows,
the second one gives this:

error: file not found
grub rescue>

---

### Post by oldfred on 2013-06-26
From Boot-Repair reinstall grub to just sdb not the Windows drive. It likes to default to reinstall to all drives, but choose just sdb.

---

### Post by gilch on 2013-06-27
Followed your instructions, Boor-repair put Grub only on sdb.
IT WORKS.
Booting options appears, and will boot either in WIndows or in Ubuntu.

How do I thank you for taking so much time helping me out? Thank you thank you thank you.
THe world is a better place with you around.

---

### Post by oldfred on 2013-06-27
Glad I could help.

Next time I am in town you can buy me a cup of coffee or a beer. :)
I like this site as we get users from all over the world.

---

### Post by gilch on 2013-06-28
You will be always welcome. Would be pleased to offer you a Tim Horton.   I am in Ottawa, Canada.

---

