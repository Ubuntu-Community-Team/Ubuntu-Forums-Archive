---
title: "Installed with wubi..get grub prompt"
date: 2012-01-24
forum: Installation &amp; Upgrades
---

### Post by kylec123 on 2012-01-24
I was trying to install Ubuntu with Wubi and with the first reboot i get grub prompt.  How do i boot from here?  I've read some similar threads and stuff from other places but nothing seems to be working.  I've restarted a few times already.  If i choose Ubuntu from the bootlist it automatically goes to the GRUB command line.  

I've been trying in and out for the past few days trying to get this to work but noting is working in my favor.  I've uninstalled(via provided uninstaller) a few times and re-downloaded.  I'm now turning to help.  

Thanks in advance for any suggestions.

---

### Post by kylec123 on 2012-01-25
Bumping this.

---

### Post by Wojtek918 on 2012-01-25
Got the same problem. I downloaded image of cd. Burned it and instaled ubuntu from running windows. It worked for me. Sory for my english, didn't used it for a while.

---

### Post by bcbc on 2012-01-25
> **kylec123 said:**
> I was trying to install Ubuntu with Wubi and with the first reboot i get grub prompt.  How do i boot from here?  I've read some similar threads and stuff from other places but nothing seems to be working.  I've restarted a few times already.  If i choose Ubuntu from the bootlist it automatically goes to the GRUB command line.  

I've been trying in and out for the past few days trying to get this to work but noting is working in my favor.  I've uninstalled(via provided uninstaller) a few times and re-downloaded.  I'm now turning to help.  

Thanks in advance for any suggestions.

What release are you installing? 
Did this happen the very first time after installing or was it something different? Please describe any other messages you get other than just the grub prompt.
Did you install with the standalone wubi.exe or from a CD?
Please post the wubi log file from the %temp% folder on Windows.

Also, it might help, to burn an Ubuntu CD or create an Ubuntu USB and boot from it, select "Try Ubuntu" (try without installing) and then post the results from the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). Sometimes this shows issues with the drives that give Ubuntu problems.

Thanks

---

### Post by kylec123 on 2012-01-25
Actually, the first time i tried to install Ubuntu(11.10 every time btw) i was able to actually use the OS.  After i messed around with it for a few minutes(didnt change anything) i decided to restart and try boting windows again.  It worked as it should have.  However, the next time i restarted i tried to go to ubuntu again.  This is where i started to get errors.  This error was something like  "error: cant read file"  or "error: cant find file"...something like that.  After this i decided to uninstall(ran the wubi uninstaller and finished it).  I did the same thing again and it gave me the error cant read file error immediately after first reboot at the end of wubi install.  I continued to uninstall again and i think after this time i started to get the Grub command prompt when i try to boot Ubuntu.  I always used the Wubi uninstaller to uninstall everything...so i figured i didnt go wrong there.  Also, if it matters....this laptop is BRAND NEW.  I just got it last week.  I literally have windows 7 + like 4 programs i downloaded.  So its basically "factory new" if you want to call it that.

---

### Post by kylec123 on 2012-01-25
[IMG]http://shakthydoss.files.wordpress.com/2011/09/grub.jpg[/IMG]

This is what i see when i try to boot Ubuntu.  If i remember right.

---

### Post by bcbc on 2012-01-26
> **kylec123 said:**
> Actually, the first time i tried to install Ubuntu(11.10 every time btw) i was able to actually use the OS.  After i messed around with it for a few minutes(didnt change anything) i decided to restart and try boting windows again.  It worked as it should have.  However, the next time i restarted i tried to go to ubuntu again.  This is where i started to get errors.  This error was something like  "error: cant read file"  or "error: cant find file"...something like that.  After this i decided to uninstall(ran the wubi uninstaller and finished it).  I did the same thing again and it gave me the error cant read file error immediately after first reboot at the end of wubi install.  I continued to uninstall again and i think after this time i started to get the Grub command prompt when i try to boot Ubuntu.  I always used the Wubi uninstaller to uninstall everything...so i figured i didnt go wrong there.  Also, if it matters....this laptop is BRAND NEW.  I just got it last week.  I literally have windows 7 + like 4 programs i downloaded.  So its basically "factory new" if you want to call it that.
It sounds like a file may have been corrupted. Wubi installs are sensitive to forced shutdowns, as this can introduce filesystem corruption. In some cases, users have reported corruption without forced shutdowns, which sounds possible in your case.

The best thing to do in this case is to run chkdsk /f from windows. That will make sure there is no NTFS corruption. (If you installed wubi on the C: drive you need to reboot to complete the chkdsk). If the corruption is within the root.disk (the virtual disk Wubi uses is a file that sits on NTFS, but within it is an ext4 file system) then you need to run fsck, but you can't do this from windows. You'll need to download an Ubuntu CD ISO and create a bootable CD or USB which you can run in 'live mode' (try without installing) and then fsck the disk.

It's strange that you should see the same problem after reinstalling.

I guess I'd advise creating a CD/USB (get it from here: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download) ) and then run the [bootinfoscript]("http://bootinfoscript.sourceforge.net/"). That should provide some decent information, and then you have a CD you can install from (wubi or normal) and use as a repair CD later.

---

### Post by mastablasta on 2012-01-26
did you install updates? some updates can break grub (sicne this is not a pporpper side by side install). check the wubi megathread for troubleshooting & solutions: [http://ubuntuforums.org/showthread.php?t=1639198](http://ubuntuforums.org/showthread.php?t=1639198)

---

### Post by bcbc on 2012-01-26
The wubi/grub issues have been fixed for a while now. Used to be common, but since 11.04 was released it was fixed (and the fix was also added to 10.04 and 10.10).

---

### Post by kylec123 on 2012-01-26
Thanks alot for the suggestions.  I will get around to trying this later today an I'll update this after.

---

### Post by kylec123 on 2012-01-26
What exact fsck should i do?  When i type just fsck in the terminal i get "fsck from util-linux 2.19.1"  Thats it.

Sorry my linux knowledge goes about as far as using cygwin on windows to compile with the gcc.

---

### Post by bcbc on 2012-01-26
The [wubi guide]("https://wiki.ubuntu.com/WubiGuide#How_can_I_access_my_Wubi_install_and_repair_my_install_if_it_won.27t_boot.3F") has a write up on this.

Basically, you need to identify which partition holds the root.disk, mount it and then fsck it.
e.g. if it's /dev/sda2
```
sudo mkdir /media/win
sudo mount /dev/sda2 /media/win
sudo fsck /media/win/ubuntu/disks/root.disk
```

You can give fsck some options: -f (force even if it appears clean), -v (be verbose), -y (automatically attempt to fix - doesn't prompt for you to enter Y each time if finds a problem).

---

### Post by kylec123 on 2012-01-26
When i try the fsck it says both(only two i have) partitions are mounted.  And trying the fsck it says both directories specified do not exist.  

I think i'll try and install via usb stick.  However i have a question about this also.  

"The installer has detected that the following disks have mounted partitions.  

/dev/sda

Do you want the installer to try and unmount the partitions on these disks before continuing? If you leave them mounted, you will not be able to create, delete, or resize partitions on these disks, but you may be able to install to existing partitions there."  

Wasn't really sure what to do here.  So i backed out of the installation.  Any knowledge on what this means?

---

### Post by bcbc on 2012-01-26
first unmount it:
```
sudo umount /dev/sda1
```

If you're on the live CD it shouldn't mount the partitions, unless you click on the Nautilus (house) icon and then click on the partitions to view them.

Since you seem to want to install now, you can either unmount the drives (click on nautilus and look for the 'eject' icon next to the partition label/size). Or you can reboot and go straight into the installation. 
The reason it's warning you is that it might need to shrink the existing partition to make room for the Ubuntu partition and it can't do that if it's mounted.

---

