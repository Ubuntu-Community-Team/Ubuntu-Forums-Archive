---
title: "Getting Grub Screen after Installing Ubuntu on Second Hard Drive"
date: 2012-08-25
forum: Installation &amp; Upgrades
---

### Post by 777funk on 2012-08-25
I have windows xp on my H: drive and just installed Ubuntu on my C: drive (used entire drive from the Ubuntu Install Live CD). My H: is the primary boot device and upon booting it gives two options:
-Windows XP
-Ubuntu

If I boot into XP it works fine but doesn't show C: anymore
If I take the option to boot into Ubuntu it just gives a GNU Grub prompt

If I go into the BIOS and change the bootable hard drive to C: (Linux), Ubuntu boots perfectly. But I'd like to have the dual boot option, so H: needs to be my boot device. AND... it's not working. 

Not sure what I should do to fix this issue. 

If I go into the bios and put my C: drive as the first boot device, Ubuntu boots perfectly but doesn't show my H: drive. And in order to have the dual option boot at the beginning I need to have my Windows drive as the bootable one. And I'd like to be able to reference what I have on Windows when I'm in Linux. It doesn't show at all if I change the boot drive to C:.



Side note... I'd like to be able to reference what's in the Windows installation (My Documents etc) from Ubuntu.

The actual error I get is:
> GNU GRUB version 1.99-21ubuntu3

Minimal BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists possible device or File completions.This is a bummer because I was really looking forward to using Ubuntu!

---

### Post by dino99 on 2012-08-25
boot on ubuntu, then open a terminal, and run:

sudo blkid
(that will tell you on which partition ubuntu is installed: something like /dev/sda1 or /dev/sdb1)

sudo apt-get purge grub-pc
sudo apt-get install grub-pc
( choose to install grub on the ubuntu root partition : /dev/sda or /dev/sdb , as found by blkid above)

sudo update-grub

then logout & reboot.

more info with the link below :D

---

### Post by 777funk on 2012-08-25
> **dino99 said:**
> boot on ubuntu, then open a terminal, and run:
sudo apt-get install grub-pc


Ok great, just did this. In the Terminal it's sitting on  Configuring Grub-PC for a long time (been about 5-10 minutes so far) after typing the install line above into the terminal. I have a 500 kbps Internet connection if that makes a difference.

EDIT: the configuring for install seems to be hung. And my Grub is now gone so I'm guessing no more boot if I shut-down. Uh oh! Now what.

---

### Post by oldfred on 2012-08-25
Dino instructions are for a standard install. But you may have wubi which is an install inside a NTFS partition.

Post this first.

sudo fdisk -lu
sudo blkid -c /dev/null -o list

And if you want a gui to help with repairs you can download this into the Ubuntu liveCD or download a version that is a full liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

---

### Post by 777funk on 2012-08-25
> **oldfred said:**
> Dino instructions are for a standard install. But you may have wubi which is an install inside a NTFS partition.

Post this first.

sudo fdisk -lu
sudo blkid -c /dev/null -o list

And if you want a gui to help with repairs you can download this into the Ubuntu liveCD or download a version that is a full liveCD.

Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration an diagnose advanced problems.

Here's what I've got:
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000773c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048   618983423   309490688   83  Linux
/dev/sda2       618985470   625141759     3078145    5  Extended
/dev/sda5       618985472   625141759     3078144   82  Linux swap / Solaris

Disk /dev/sdf: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x06dd06dc

   Device Boot      Start         End      Blocks   Id  System
/dev/sdf1   *          63   976751999   488375968+   7  HPFS/NTFS/exFAT

and for the second command there:

> device     fs_type label    mount point    UUID
-------------------------------------------------------------------------------
/dev/sda1  ext4             /              ba47e66e-92c7-4eb0-9f29-3d3698e69fed
/dev/sda5  swap             <swap>         fc8c39ac-d7be-433f-8e6c-863d6d879fda
/dev/sdf1  ntfs             (not mounted)  E89CD1E79CD1AFF4

I uninstalled Grub (as in Dino99's instructions above) and it won't reinstall. I'm guessing when I restart the machine the boot will be gone.

---

### Post by 777funk on 2012-08-25
Ok, with a slow internet connection the Boot repair disk would take most of today to download. 

And no boot now with grub gone. 

So I'm reinstalling. I'm sure I'll have the same issue when it reloads with the Grub screen (I'd think since all will be the same). 

So still need to figure out why no dual boot function. In Windows as mentioned, C: is no longer showing up as a drive letter... but I do see the space in the device manager.

---

### Post by darkod on 2012-08-25
Did you have the windows disk disconnected during the ubuntu install? In that case, you never needed to uninstall grub, you only needed to run update-grub.

Anyway, can you try installing it again?

sudo apt-get install grub-pc

If it asks where to install, select /dev/sda. Sometimes when selecting in text menus you need to do it with the Space bar until a * sign shows, not by hitting Enter. If you hit Enter the process might continue without anything selected.

If you already have grub2 installed but never selected to install on /dev/sda, you can also try from within ubuntu:
sudo grub-install /dev/sda

---

### Post by darkod on 2012-08-25
> **777funk said:**
>  In Windows as mentioned, C: is no longer showing up as a drive letter... but I do see the space in the device manager.

Windows can't see linux partitions and assigns letters only to ntfs partitions. So it's perfectly normal that the ubuntu disk will not show up in My Computer any more.

And stop calling it C:, it's called like that in XP when it had ntfs partition, not any more.

But windows usually calls C: the main system partition, did you somehow change it with H:? How come you deleted the C: partition and XP still works?

---

### Post by 777funk on 2012-08-25
> **darkod said:**
> Windows can't see linux partitions and assigns letters only to ntfs partitions. So it's perfectly normal that the ubuntu disk will not show up in My Computer any more.

And stop calling it C:, it's called like that in XP when it had ntfs partition, not any more.

But windows usually calls C: the main system partition, did you somehow change it with H:? How come you deleted the C: partition and XP still works?

Thanks, and to further explain, I have 2 drives (formerly Windows labeled C: and Windows labeled H: ). I would like to keep my XP install on H: and would like Ubuntu on the other drive (aka C: ).

I just reinstalled Ubuntu on C:, We'll see if it worked. I'd like a dual boot machine (one system on each drive). And I'd like to be able to pull the material off of each from the other operating system. i.e. I'd like to be able to get to My Documents on the Windows installation from Linux.

EDIT: To update the thread, I re-installed Ubuntu and it's still giving me the:

 GNU Grub version 1.99-21ubuntu3
Minimal BASH-like line editing is supported. For the first word, TAB list possible command completions. Anywhere else TAB lists possible device or file completions.

It WILL boot if I select the booting HDD in the bios as the one that Linux is on. But if I have it on the Windows HDD as the first boot device it gives me the dual option and then goes to the GRUB prompt if I select Ubuntu.

---

### Post by 777funk on 2012-08-25
Also, I should add that I ran boot repair from the Terminal and it didn't fix anything. But here's what it said:

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/1166310/](http://paste.ubuntu.com/1166310/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.
Please do not forget to make your BIOS boot on the removable disk!


The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the  disk. Your BIOS may not detect them. You may want to retry after  creating a /boot partition (EXT4, >200MB, start of the disk). This  can be performed via tools such as gParted. Then select this partition  via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))

---

### Post by darkod on 2012-08-25
You seem to have a correct grub2 bootloader on the 320GB disk. That is the one that should be first option to boot from in BIOS.

Also XP is correctly detected and entry for it is created in the grub2 boot menu.

Are you sure no boot menu shows when you boot? Do you maybe see some message about the resolution on your monitor being wrong instead of seeing the boot menu?

Because if there is any such message, the menu is there but you are not seeing it and after 10 seconds it boot the default entry which is ubuntu. That's why it may seem that ubuntu is booting directly without asking you if you want to select XP.

---

### Post by 777funk on 2012-08-25
> **darkod said:**
> You seem to have a correct grub2 bootloader on the 320GB disk. That is the one that should be first option to boot from in BIOS.

Also XP is correctly detected and entry for it is created in the grub2 boot menu.

Are you sure no boot menu shows when you boot? Do you maybe see some message about the resolution on your monitor being wrong instead of seeing the boot menu?

Because if there is any such message, the menu is there but you are not seeing it and after 10 seconds it boot the default entry which is ubuntu. That's why it may seem that ubuntu is booting directly without asking you if you want to select XP.

Yes and it works great when I boot from the 320GB drive (C in Windows). But Windows is on the 500GB drive (H in Windows). So shouldn't I be booting from my original Windows drive? I don't get a dual boot option at start up with the 320GB Linux Install drive. Also, I don't see the original Windows installation or files on the 500GB Windows drive when I'm in Linux.

---

### Post by darkod on 2012-08-25
No, you should boot from the disk where grub2 is, which in your case seems to be the 320GB disk. It doesn't matter which disk you had first or where windows is.

Ubuntu will not show you the windows partition by default but when you open the file browser on the left side you should see something like 465GB partition. If you click on it, it should mount it temporarily and show you the files.

There are ways to make it mount permanently but I usually don't mount permanently windows system partitions. You have to take into account that windows doesn't like very much for linux to touch its system partition.

I am not sure why you don't get a boot menu offering ubuntu and windows. It simply has to show up, the bootinfo results look correct.

---

### Post by 777funk on 2012-08-25
> **darkod said:**
> No, you should boot from the disk where grub2 is,  which in your case seems to be the 320GB disk. It doesn't matter which  disk you had first or where windows is.

Ubuntu will not show you the windows partition by default but when you  open the file browser on the left side you should see something like  465GB partition. If you click on it, it should mount it temporarily and  show you the files.

There are ways to make it mount permanently but I usually don't mount  permanently windows system partitions. You have to take into account  that windows doesn't like very much for linux to touch its system  partition.

I am not sure why you don't get a boot menu offering ubuntu and windows.  It simply has to show up, the bootinfo results look correct.

I'll try again and see if I get a boot menu on the other drive. I don't  think I did though. I believe it went straight to Ubuntu.
EDIT: Confirmed. It goes from the BIOS to a black screen and monitor goes to sleep (no input) then comes Ubuntu about 30 seconds later. No option for a dual boot if I use the C: drive (320GB). But if I boot from the H: (Home directory for Windows) I do get a dual boot option (but dead ending to the Grub).

I wonder if this could have something to do with the fact that my Windows root is NOT on C: Maybe Linux misplaced something during the install since most Windows systems are on C: as the home directory?




Also just tried this (But used the H: drive as the directory the file went into of course)

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Wubi_9.10)

but to no avail. Still not working. I'll try moving the partition to the beginning and seeing if that works.

---

### Post by oldfred on 2012-08-25
I thought you did away with wubi with the full install?

We have seen the boot issue with very large drives and grub not booting. If you can boot Ubuntu you do not have that issue. Boot-repair is just reporting that in case you do have that issue.

I do normally suggest smaller / (root) partitions and separate /home and/or data partition, somewhat for the same issue as the boot issue, but also to separate system from data. I suggest that for Windows also and like a smaller Windows system partition and most data in a shared NTFS data (only) partition. If putting most or all data in the shared you may not need a separate partition for /home.

The reports are a little strange that drive is sdf not sdb. Is this an external. But I thought Windows did not boot from externals.

Even your Windows boot.ini says it is on rdisk(0) or first drive. Grub does a drive mapping to make Windows think it is first but that does not always work.

---

### Post by 777funk on 2012-08-25
> **oldfred said:**
> I thought you did away with wubi with the full install?



The goal was to have Windows on the one drive and the Linux on the other and with a dual boot. I'm  not sure what happened though. Windows and Linux both work fine on the separate drives. Just the Dual Boot from my Windows Root (H: Drive) isn't quite right yet it (the 500GB drive and Drive H: in Windows) is the only one with the Dual boot option in the BIOS. Unfortunately it always lands in the Grub prompt.

One other interesting thing I noticed was that on the LiveCD the 320GB and the 500GB show in the Devices Menu. Only the 320GB shows when I actually boot from the 320GB drive containing Linux. I wonder why both show in Live but only the 320GB in the real deal.

Oh and EDIT: to answer the other question, the drives are both internal (SATA).

IF there's a way to start over, I have no personal data/files on Linux yet, I'd be happy to start over if there's an easy way to start from scratch.

---

### Post by darkod on 2012-08-25
> **777funk said:**
> 
EDIT: Confirmed. It goes from the BIOS to a black screen and monitor goes to sleep (no input) then comes Ubuntu about 30 seconds later. No option for a dual boot if I use the C: drive (320GB).

I already asked if you are seeing some message or anything strange with your monitor and this is the first time you mentioned it. :)

The boot menu is shown in those 30 seconds and since you are not seeing it and not selecting anything, the ubuntu boots by default. There is some issue either with resolution or something.

And forget booting about the 500GB disk, you have windows bootloader on it which can't boot ubuntu. The option for ubuntu you are seeing there is an old leftover from wubi installation you had, that's why it's not leading you anywhere when you select it.

Back to the topic, you can try and set a standard low resolution for grub2 and see if that helps.

Boot ubuntu and open terminal, execute:
gksu gedit /etc/default/grub

Find the line that looks like #GFX_MODE=640x480 or similar and delete the # symbol at the front. Only that.
Save and close the file.

In the terminal run:
sudo update-grub

Restart and see if that shows the menu. Again, for the final time, boot from the 320GB and only that.

---

### Post by 777funk on 2012-08-25
Ok so there's something showing there but I'm just not seeing it. Being new to Ubuntu, I didn't know what to look for. My monitor turns off at times when booting from Windows as well so I figured that was normal.

Anyways, I guess that's probably the dual boot I should have seen (the black out period). Thanks. 

I'll see if I can fix it. But... now it won't boot at all. Not sure what's happening but.., not giving up yet. I already have around 12 hours into this can't quit now. 

Thanks to all for the help given and suggestions. I'll see if I can get the dual boot to display. I suppose even if it doesn't display, I should be able to press down arrow and hit enter to get Windows assuming there is a dual boot option. Right?

---

### Post by 777funk on 2012-08-25
> **darkod said:**
> 

Boot ubuntu and open terminal, execute:
gksu gedit /etc/default/grub

Find the line that looks like #GFX_MODE=640x480 or similar and delete the # symbol at the front. Only that.
Save and close the file.

In the terminal run:
sudo update-grub

Restart and see if that shows the menu. Again, for the final time, boot from the 320GB and only that.

Tried this and still not showing anything for about a minute. I also tried hitting the down arrow and enter to see if XP would boot and it didn't work. But that did bring up a long chain of text before Ubuntu loaded (which I didn't see earlier).

Here's what I got in the terminal after changing the file (double checked and confirmed that the "#" was gone):

> nick@nick-Inspiron-531:~$ sudo update-grub
Generating grub.cfg ...
cat: /boot/grub/video.lst: No such file or directory
Found Microsoft Windows XP Home Edition on /dev/sdf1
done


---

### Post by 777funk on 2012-08-25
Now when I hit down arrow and Enter on the screen I can't see, a blue/purple box pops up with options to start normal, start recovery mode, update grub, etc. I'm assuming this is like Safe Mode in a PC. Not sure what I have going on here.

---

### Post by 777funk on 2012-08-26
Just found [this article]("http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/2/") dealing with a Dual Boot and Dual Drives. Could it have to do with the fact that my primary OS (Windows) is on SDF and Linux is on SDB now (I reinstalled)?

The article says that the boot loader looks for SDA.

---

### Post by oldfred on 2012-08-26
Your system is a bit strange as most have Windows as sda or first drive and the second drive is sdb. Sometimes external devices skip drives to sdf or sdg but nor normally internal drives.

It seems like you still have some video issue. One down arrow got you to the recovery mode, which removes the quiet & splash boot parameters so you see all the details of the boot process. Windows is last on the list so it is several down arrows depending on how many kernels you have installed.

Windows in your sdf drive still thinks it is in the first drive as boot.ini says rdisk(0) or first drive.

What system is this?

---

### Post by 777funk on 2012-08-26
Just found this:


[http://askubuntu.com/questions/161297/why-does-my-screen-blank-out-for-the-duration-of-the-grub-boot-menu](http://askubuntu.com/questions/161297/why-does-my-screen-blank-out-for-the-duration-of-the-grub-boot-menu)

and it seemed to cure the missing text for 30 seconds between bios and startup. And I can now see all the boot options!

Here's the article:

     [COLOR=Magenta]**[Why does my screen blank out for the duration of the Grub boot menu?]("http://askubuntu.com/questions/161297/why-does-my-screen-blank-out-for-the-duration-of-the-grub-boot-menu")**


                                     Upon booting, when I should see the GRUB menu, my monitor  simply says: "No optimum mode. Recommended mode: 1600*1200". If I wait  for a short while, Ubuntu starts to boot and it reaches the desktop. [/COLOR]   [COLOR=Magenta]
  So I guess there is no video signal during that time, there's the  grub menu but I cant see it and after the wait time everything is fine. I  have the same problem when I log out for a short moment, before the log  in screen is reached. and this also happens when i shut down ubuntu.
  The VGA is an onboard NVIDIA GeForce 7025.


**1 Answer**[/COLOR]                                                                      [COLOR=Magenta]
[]("http://askubuntu.com/questions/161297/why-does-my-screen-blank-out-for-the-duration-of-the-grub-boot-menu?answertab=active#tab-top")

                           The graphical Grub menu does not appear to be compatible with your video card. So let's switch to a text menu instead.[/COLOR]           [COLOR=Magenta]
[/COLOR]   
[LIST=1]
[*][COLOR=Magenta]Open the terminal with Ctrl+Alt+T[/COLOR]
[*][COLOR=Magenta]Paste the below, and enter your password when asked:
  sudo sed -i -e 's/#GRUB_TERMINAL/GRUB_TERMINAL/g' /etc/default/grub[/COLOR]
[*][COLOR=Magenta]Then type sudo update-grub[/COLOR]
[*][COLOR=Magenta]Reboot and hopefully you get a text menu instead of the screen just blanking out.[/COLOR]
[/LIST]
[INDENT]   [COLOR=Magenta]*Explanation:* Here, *sed* simply uncomments the GRUB_TERMINAL=console line, forcing  text mode[/COLOR]
 [/INDENT]

---

### Post by oldfred on 2012-08-26
The askUbuntu maintains the command line complexity of Ubuntu. It works but there are other ways also.

Resetting an out&#8208;of&#8208;range resolution (does not include grub's set gfxmode=640x480)
[https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution](https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution)

Repair grub's video mode and other settings with a gui.
[https://launchpad.net/grub-customizer](https://launchpad.net/grub-customizer)
HOWTO: Grub Customizer Updated for grub 1.99
[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)


IF the default is not working you may be able to set it to your size not just the 640x480. If the correct setting is 1024x768 you just edit it to that value.
Use this with your monitor size in /etc/default/grub:
GRUB_GFXMODE=1024x768

Or use command line editor:
sudo nano /etc/default/grub
or 
gksu gedit /etc/default/grub
and just remove the #  as that makes that line a comment.

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

---

### Post by 777funk on 2012-08-26
Thanks to all who've helped. Loving Ubuntu so far! Not planning to boot the XP session much in the future.

---

### Post by 777funk on 2012-09-15
I uncommented the graphical interface command in GRUB and it has been working but now I'm trying to fix this properly and having trouble. My monitor goes to sleep during grub if I have it uncommented. I changed the resolution to 1024x768 as oldfred recommended. But that didn't seem to do it. Any tips?

Edit: I just noticed my NEC LCD1765 native resolution is 1280x1024

so I'll try adding this line.
#GRUB_GFXMODE=1280x1024

EDIT EDIT: Just tried this and the monitor is still going to sleep during GRUB. It says Analog RGB out of range going to sleep or something to that effect.

---

### Post by oldfred on 2012-09-16
Did you remove the # as that makes a line a comment or not really used.

And did you run this after the update ( I always forget to do this and wonder why my changes have not been done):

sudo update-grub

---

### Post by 777funk on 2012-09-17
> **darkod said:**
> I already asked if you are seeing some message or anything strange with your monitor and this is the first time you mentioned it. :)

The boot menu is shown in those 30 seconds and since you are not seeing it and not selecting anything, the ubuntu boots by default. There is some issue either with resolution or something.

And forget booting about the 500GB disk, you have windows bootloader on it which can't boot ubuntu. The option for ubuntu you are seeing there is an old leftover from wubi installation you had, that's why it's not leading you anywhere when you select it.

Back to the topic, you can try and set a standard low resolution for grub2 and see if that helps.

Boot ubuntu and open terminal, execute:
gksu gedit /etc/default/grub

Find the line that looks like #GFX_MODE=640x480 or similar and delete the # symbol at the front. Only that.
Save and close the file.

In the terminal run:
sudo update-grub

Restart and see if that shows the menu. Again, for the final time, boot from the 320GB and only that.

Here's what I've got now and it's working (No # symbol). But it's low res mode right? or am I ok here?

EDIT: I updated it to the native res of the monitor and I have now a box with simple options to choose between which OS to load and how (maybe 5 lines of options), then it goes to a dark purple blank screen, then says UBUNTU, then goes to the login screen. I'm assuming this is normal now. No screen timeouts.

---

