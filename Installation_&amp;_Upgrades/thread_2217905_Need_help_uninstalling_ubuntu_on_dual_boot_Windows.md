---
title: "Need help uninstalling ubuntu on dual boot Windows XP"
date: 2014-04-18
forum: Installation &amp; Upgrades
---

### Post by Babak on 2014-04-18
Hi, I would appreciate some help in uninstalling ubuntu. 

I've already searched and found the typical method to do this but I'm here because the installation of ubuntu as a dual boot OS with Windows XP had a wrinkle and I want to make sure that this won't complicate matters if I proceed with the usual advised method of uninstalling ubuntu (as per this: [http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/) or this [http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422](http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422))

Before installing ubuntu, the Windows XP system had 2 hard drives: long story short, this is an older windows computer that had a BSD failure a few years ago and I bought a new drive (500GB) and installed Windows XP (again) on this drive rather than attempt to fix the older drive (80GB) which the original Win XP OS was installed on.

When I booted and attempted to install ubuntu 14 from a USB, the installation process defaulted to the non-system, smaller and older drive (80GB). I could have installed it on the larger and newer drive but the process for that was more complicated - ubuntu's installation screen required from me the creation of a partition, etc. and although I tried, it gave me an error message. So I went back to the default installation location of the older drive since it was easier with just a single radio button!

I selected a 20GB size partition for ubuntu on the smaller and older 80GB drive.

Now I would like to **uninstall ubuntu**.

I know that the first step is to go to Windows XP's disk management window and delete the partition for ubuntu/linux. Here's a screenshot of disk management showing the drives and the partitions:

[http://i.imgur.com/N2FYg6R.png](http://i.imgur.com/N2FYg6R.png)

But I don't see one partition but two! together they add up to 20GB so I'm pretty sure they are where ubuntu resides. 

So my first set of questions are: is this correct? do I erase both? and why are there two?

My second set of questions:

Since ubuntu seems to have been installed on the non-system drive (Disk 0 or E: -- the older, smaller 80GB drive) does this mean that I do not have to boot into recovery console and then fixmbr to remove grub and re-install the windows bootloader?

Where is grub located? is there a way for me to find out via windows?

Or does it not matter and I have to do this step anyway? that is, part B of this:
[http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/](http://bobmorris.wordpress.com/2008/02/09/how-to-uninstall-ubuntu-on-dual-boot-windows-xp-using-windows-only/)

Thank you.

---

### Post by gdesilva on 2014-04-18
> **Babak said:**
> 

But I don't see one partition but two! together they add up to 20GB so I'm pretty sure they are where ubuntu resides. 

So my first set of questions are: is this correct? do I erase both? and why are there two?


> **Babak said:**
> 

Since ubuntu seems to have been installed on the non-system drive (Disk 0 or E: -- the older, smaller 80GB drive) does this mean that I do not have to boot into recovery console and then fixmbr to remove grub and re-install the windows bootloader?



Depends. If you get the Grub menu when you boot the machine and if you want to get rid of it then you would need to run fixmbr from Windows which will replace grub with Windows boot loader, ntldr. If you do not get the Grub Menu and can boot into Windows directly then there is nothing more to do.



EDIT: Sorry, something got screwed up....see below.

---

### Post by gdesilva on 2014-04-18
> **Babak said:**
> 

But I don't see one partition but two! together they add up to 20GB so I'm pretty sure they are where ubuntu resides. 

So my first set of questions are: is this correct? do I erase both? and why are there two?


First one is Ubuntu the second invariably is the Swap partition created when you installed Ubuntu.

> **Babak said:**
> 

Since ubuntu seems to have been installed on the non-system drive (Disk 0 or E: -- the older, smaller 80GB drive) does this mean that I do not have to boot into recovery console and then fixmbr to remove grub and re-install the windows bootloader?



Depends. If you get the Grub menu when you boot the machine and if you want to get rid of it then you would need to run fixmbr from Windows which will replace grub with Windows boot loader, ntldr. If you do not get the Grub Menu and can boot into Windows directly then there is nothing more to do.

---

### Post by Babak on 2014-04-19
Hi gdesilva,

thank you for responding. To answer your question, yes, I do see the 'purple' grub menu screen which shows ubuntu at the top and the two previous installs of windows xp at the bottom of the list of options on the menu.

My questions were not answered though, do I erase both partitions? where is grub located? how can I find grub from within windows?

I guess I should have mentioned that the reason I want to uninstall ubuntu is because something is wrong with it because it won't boot up. The first part of the screen comes up showing that ubuntu is about to load and then the screen goes dark (after a text warning is shown about something about a cpu temperature thing not working...?). I've waited and waited but for some reason the screen just remains dark (sort of bluish black) and nothing happens at which point I have to manually shut down or restart the system.

---

### Post by fr33z0n3r on 2014-04-19
Babak,   I'm no expert,  but if you are correctly describing the boot experience, then you might not want to delete the ubuntu partitions before correcting the MBR (which tells the BIOS how to boot what is on the HDD).  You would use fixmbr to do that.  That runs in the XP Recovery Console (which hopefully you have installed).  Once you do that, Windows might automatically boot.

If you want to retain the ability to dual boot, then doing this is not helpful.  Using the current Ubuntu Live DVD would probably give you visibility on the 2 partitions (since it know the format they use), and could be used to over-install the new ubuntu over the old ubuntu.  But MAKE SURE you have a full disk backup of windows, etc.   As you could accidentally wipe it.

But don't forget - I AM NOT AN EXPERT.

---

### Post by Babak on 2014-04-19
I guess what I'm unsure about is this sort of thing:

"If you set up your dual-booting differently, your instructions may vary slightly&#8212;like if you put Linux on a separate hard drive, or if you have other operating systems on the drive. But for most people, these instructions should suffice."
[http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422](http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422) from the section to "Keep Windows and Remove Linux"

I'm concerned that because of the 2 drives and because of the distinction among them: one is the system drive and the other the data drive as well as the fact that ubuntu was installed on the data drive (80 GB) **not** on the system drive (Win XP) that the instructions are different!

This is why I asked all those questions like how do I find out which drive grub was installed on?!?

---

### Post by oldfred on 2014-04-19
This will show all the details
 Post the link to the Create BootInfo report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

I do not think this removes partitions, but should reinstall the correct boot loader for you.

 An easy way [OS-Uninstaller] Safely remove Windows, Ubuntu... in 1 clic ! 
[http://ubuntuforums.org/showthread.php?t=1769489](http://ubuntuforums.org/showthread.php?t=1769489)
[https://help.ubuntu.com/community/OS-Uninstaller](https://help.ubuntu.com/community/OS-Uninstaller)

Boot-Repair is not yet available for trusty 14.04 yet, but can be installed with several work arounds. If you have older installs the above instructions should work.

---

### Post by Babak on 2014-04-19
Thank you oldfred - I can't use BootInfo because I am unable to enter ubuntu session - this is why I asked how I can find out where GRUB is from within windows

If I understand you correctly, you're saying that Boot-Repair is not yet available for 14.04 but that OS-Uninstaller will do the job (but technically, OS-Uninstaller is part of LinuxSecureRemix [https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)) Is that right?

How do I create a live or boot USB which has LinuxSecureRemix? The instructions are: "Download Linux-Secure-Remix, and burn the image on a DVD, or create a live-USB. Boot on it, then launch OS-Uninstaller from the bottom-left menu."

Do I use [http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/) to create the bootable USB and instead of a linux distro ISO choose the LinuxSecureRemix file I download from [http://sourceforge.net/projects/linux-secure/files/](http://sourceforge.net/projects/linux-secure/files/) ?? or something else?


In any case, I do have the Win XP recovery CD so I don't think I really need all these tools. What I need is ** to make sure that I remove grub and re-install windows boot on the CORRECT HD - and since I have two, as mentioned repeatedly above, I want to make sure that I'm doing this to the correct one!!!**




.

---

### Post by oldfred on 2014-04-19
You just need to install the XP boot loader to the drive's MBR with your Windows install. Make sure BIOS is set to boot from the windows drive before making the repair and that boot flag is on the Windows partition.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

You create bootable CD, DVD, or flash drives from ISO all the same way. There are many different tools but they both format device, extract ISO and make it bootable. Slightly different internally whether flash drive or DVD.

      
 How to create a bootable Ubuntu USB Flash Drive - unetbootin
[http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/](http://www.linux-geek.co.nz/2011/04/11/how-to-create-a-bootable-ubuntu-usb-flash-drive/)
[https://help.ubuntu.com/community/USB%20Installation%20Media](https://help.ubuntu.com/community/USB%20Installation%20Media)


 Most find this works best
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
If that does not work
[http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/](http://www.pendrivelinux.com/universal-usb-installer-easy-as-1-2-3/)
Pendrive also has page on booting ISOs
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/)

      
 [URL="https://help.ubuntu.com/community/BurningIsoHowto"]https://help.ubuntu.com/community/BurningIsoHowto
[/URL]
 [http://www.ubuntu.com/download/help/burn-a-cd-on-windows](http://www.ubuntu.com/download/help/burn-a-cd-on-windows)

[URL="https://help.ubuntu.com/community/BurningIsoHowto"]
[/URL]

---

### Post by gdesilva on 2014-04-19
@babak, have you considered re-installing Ubuntu on the existing partition to see whether you still have the problems with booting? It appears thatt you do not mind having the Grub boot loader and this would be a quick way isolate problem with your first install. If you still have problems then following the advise given by Oldfred is the way to go. Just a suggestion.

With regards to your second question, grub is located in the Master Boot Record (MBR) and the third question, you cannot access MBR or Grub from Windows but any OS can write/modify a bootloader, like NTLDR (Windows) or Grub (Linux) in MBR. Hope this clarifies the issue.

---

### Post by Babak on 2014-04-19
Thank you oldfred and gdesilva. I bit the bullet and just followed the typical uninstall process (delete partitions from within XP via disk management screen) and then use XP recovery CD to fixmbr. It worked!!

It removed the grub purple menu and went straight to win xp.

But with one wrinkle... isn't there always a wrinkle? 

After deleting the two partitions, there is no right click menu option to "extend partition" as in step 4 of the lifehacker tutorial:

"4. Right-click on your Windows partition and choose "Extend Volume." Extend it to fill the free space your Linux partition left behind."
[http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422](http://lifehacker.com/how-to-uninstall-windows-or-linux-after-dual-booting-508710422)

I don't know why. Nor how to go about fixing that. But I suppose that is a windows issue and outside the realm of an ubuntu help forum!

Maybe I can use this?
[http://www.disk-partition.com/free-partition-manager.html](http://www.disk-partition.com/free-partition-manager.html)

---

### Post by Babak on 2014-04-20
how do you mark a thread as resolved?

---

### Post by jhay2 on 2014-04-21
try this but i not guaranteed that this is the perfect method for your problem 




to restore windows bootloader 

Boot your windows xp cd installer


then install it without reformating drives
to achieve it 

when you see the choices of format usually these are the following

format into NTFS quick
format into NTFS
format into FAT quick
format into FAT
Leave system intact (no change)


choose the last option so it will just reinstall windows xp without formating the whole system ..it will just replace your old windows files and install bootloader without touching the user folder like Documents Program Files , 

and that would replace the grub bootloader into a windows bootloader .. 

to Remove ubuntu 

format those partition with "unknown partition" labeled at disk management into an NTFS 

or you can use mini partition tool for more disk management features like resizing /merging /moving

---

### Post by oldfred on 2014-04-21
I do not use Windows anymore, but others suggest these. They have free versions that do basic things and paid versions that do a lot more.
 EASEUS Partition Master 
[http://www.partition-tool.com/personal.htm](http://www.partition-tool.com/personal.htm)
Partition Wizard
[http://www.partitionwizard.com/free-partition-manager.html](http://www.partitionwizard.com/free-partition-manager.html)
[http://www.partitionwizard.com/partitionmanager/partition-fix.html](http://www.partitionwizard.com/partitionmanager/partition-fix.html)

To close a thread see my signature.
Or see post #9
[http://ubuntuforums.org/showthread.php?t=2054969](http://ubuntuforums.org/showthread.php?t=2054969)

---

