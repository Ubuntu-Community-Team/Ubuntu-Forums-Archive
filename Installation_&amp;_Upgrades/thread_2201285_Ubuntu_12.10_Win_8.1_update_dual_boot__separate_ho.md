---
title: "Ubuntu 12.10 Win 8.1 update dual boot  separate /home partition"
date: 2014-01-23
forum: Installation &amp; Upgrades
---

### Post by claven123 on 2014-01-23
I can't get a boot menu, grub that is when I updated my win 8 dual boot machine to 8.1.   I just ran the live ubuntu dvd and installed boot repair.  this i the output.

[http://paste.ubuntu.com/6804730/](http://paste.ubuntu.com/6804730/)

I have two options...

1. Try to work out the current install and get the dual boot to work....
2. Install/upgrade to 13.10 or the newest version of ubuntu

I don't really know which would be the best option?  I do have a separate /home partition with my files in there etc.... (not sure how to do the upgrade etc...)


BTW: Desktop 64b Dell XPS

Thanks

d

---

### Post by claven123 on 2014-01-23
Here is the screen shot of gparted...

d[ATTACH=CONFIG]249691[/ATTACH]

---

### Post by claven123 on 2014-01-23
Please write on a paper the following URL:
[http://paste.ubuntu.com/6804822/](http://paste.ubuntu.com/6804822/)


I ran boot repair and did the recomended option, I did not rename the windows boot files.

I am now going to reboot and see what happens.

BTW, It requested me to copy and past two sets of commands into terminal and I save the output of those terminal processes if needed.

Thanks,

d

---

### Post by claven123 on 2014-01-23
Ok, so I ran that and did a reboot.  I was greated with grub and chose ubuntu.  It loaded.... but 

I do not get unity, nor the top bar with all the options.  When certain windows open there is no top to them (even when I can see the whole dialog box).  I get a compiz error that states is shut down.  with a reference to bug 1100574 via the launchpad.

now, what do i do.....

d

---

### Post by claven123 on 2014-02-10
I did an additional reboot and was able to get a full ubuntu without issues.  Then after a few weeks of not really doing anything with the computer I went to restart and was only greeted with the standard windows boot menus.  I did not get grub.

I'm at a loss, should I rerun boot repair?

d

---

### Post by claven123 on 2014-02-10
So, I ran boot repair and chose to rename the files etc... and I was then greeting with grub on the reboot.


```

Boot successfully repaired.

Please write on a paper the following URL:
[http://paste.ubuntu.com/6909598/](http://paste.ubuntu.com/6909598/)

In case you still experience boot problem, indicate this URL to:
[EMAIL="boot.repair@gmail.com"]boot.repair@gmail.com[/EMAIL] or to your favorite support forum.

You can now reboot your computer.


You may want to retry after deactivating the [Backup and rename Windows EFI files] option.


```



Not sure how to make this change persist?


D

---

### Post by oldfred on 2014-02-10
I have not seen Dell's that need the backup & rename for buggy UEFI.
That is for those UEFI where vendor has modified it to only boot Windows. Or ubuntu entry in UEFI is not shown or does not work.
The rename then has the UEFI boot what it thinks is a Windows efi boot file that really is shim/grub and then from grub you boot Windows.
But if Windows does update to refresh its efi file it overwrites the renamed file. Best to not rename and set ubuntu as default entry.

       To undo & to rename files to their original names, you just need to tick the "Restore EFI backups" option of Boot-Repair.
    
Windows and particularly 8.1 seems to constantly refresh to make it the first in boot order. If that is occuring:
       UEFI NVRAM boot entries are cached in the BCD store
BCD has 1:1 mappings for some UEFI global variables
Any time {fwbootmgr} is manipulated, NVRAM is automatically updated

   Alternative to Boot-Repairs rename of shim.
Some systems work better to register grub/shim from inside Windows - for those that keep resetting Windows as default
[http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot](http://askubuntu.com/questions/371559/grub-not-showing-on-startup-for-windows-8-1-ubuntu-13-10-dual-boot)
bcdedit /set {bootmgr} path \EFI\ubuntu\grubx64.efi
[https://coderwall.com/p/vfyqkg](https://coderwall.com/p/vfyqkg)

You may also want to house clean out some old kernels. I normally keep 2, current and one older one. I prefer to use synaptic. If you do not have it:
sudo apt-get install synaptic
       Determine your current kernel:
uname -a
uname -r
In synaptic search for linux-image to choose to delete old ones
Also command line in post #8
[http://ubuntuforums.org/showthread.php?t=1283521](http://ubuntuforums.org/showthread.php?t=1283521)

---

### Post by claven123 on 2014-02-10
So, I should restore the efi backups?

I can't remember if just running boot repair worked in the past, it seems it did not.  Thus, I did the rename option this time.



I'm quite confused as to what to do..... it seems what I have is working.  I will attempt to reboot and see what happens? 

BTW, to get the dual boot a few years ago I used bcd type of program in windows.


I will work on the kernel thing as a side project....

thanks for all your help!

d

---

