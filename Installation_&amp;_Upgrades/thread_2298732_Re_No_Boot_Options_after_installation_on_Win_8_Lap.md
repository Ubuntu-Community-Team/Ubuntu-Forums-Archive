---
title: "Re: No Boot Options after installation on Win 8 Laptop (EFI)"
date: 2015-10-13
forum: Installation &amp; Upgrades
---

### Post by Ifaistos on 2015-10-13
Hello everyone :-)

I received an ASUS F554L Laptop with Win 8.
I want to have only Ubuntu Linux.

I managed to partition as I normally do and deleted the partitions of Win 8.

After successful installation I removed the USB Stick, and rebooted.

However I am back at the Bios, with no boot options.
It seems that I didn't do smt right with the partitions.

There ware a couple of warnings during partitioning about EFI but I chose to go on.
It seems that I was wrong in hoping that everything would work out.

Does anyone know what I need to do?
Can anyone point me to a page explaining the procedure?

Thank you all in advance!

I just tried to redo the procedure by booting from my USB stick, and it ended with the following error :
---[ end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I think I "broke" it!

Please help...

Update : I created a live DVD, and it works.

I am trying to install again.

Any suggestions for installation?  I get the following warning :

Force UEFI Installation?
This amchine's firmware has started the installer in UEFI mode but it looks like there amy be existing opersting systems already installed using "BIOS compatibility mode".  If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems late.

If you wich to install in UEFI mode and don't care about keeping the ability to boot one fo the existing systems, you have the option to force that here.  If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here.

and then the options were : "Go Back" and "Continue in UEFI mode".

in the previous time I tried my installation in tried option 2.

Any suggestions?

---

### Post by grahammechanical on 2015-10-13
Now that you have a working live session you can go further and you need to read this

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> Having a PC with UEFI firmware does not mean that you need to install Ubuntu in UEFI mode. What is important is below:  


[LIST]
[*]if  the other systems (Windows Vista/7/8, GNU/Linux...) of your computer  are installed in UEFI mode, then you must install Ubuntu in UEFI mode  too. 
[*]if  the other systems (Windows, GNU/Linux...) of your computer are  installed in Legacy (not-UEFI) mode, then you must install Ubuntu in  Legacy mode too. Eg if your computer is old (<2010), is 32bits, or  was sold with a pre-installed Windows XP. 
[*]if  Ubuntu is the only operating system on your computer, then it does not  matter whether you install Ubuntu in UEFI mode or not. 
[/LIST]


Machines that come with Windows 8 pre-installed have Windows 8 installed in EFI mode. it is possible that your first Ubuntu install was in BIOS compatibility mode and that was causing the problem you had with the restart. It may also be the reason you are now getting this warning about the possibility of the existence of an OS that was installed in BIOS compatibility mode.

For you the matter has been simplified by not needing to dual boot with Windows 8. Are you installing by using the Erase disk and install Ubuntu option? That will make things very simple for you.

Regards.

---

### Post by Ifaistos on 2015-10-13
Thank you for your answer!

Actually it should make things simpler by wanting to have a single boot ubuntu system.

However I want to be able to create partitions.
Like one for "/"
another one for "/home"
and another one for the rest of the disk...

So how do I do that?

I tried the boot-repair program.

I got the error GPT detected.  Please create a BIOS-Boot partition (>1MB, unformatted filesystem, bios-grub flag).  This can be performed via tools such as Gparted.  Then try again.

I reinstalled and created the BIOS-Boot partition.
It still couldn't boot.
I rerun the boot-repair.
It prompted that my computer has started in EFI mode, and that I should create a new partition Fat32 for EFI.
However it allowed me to continue.
I finished with not errors and produced the following url address: 
paste.ubuntu.com/12775723

I tried to reboot but is STILL doesn't work :(

It just accesses the BIOS, where in the BOOT section it just doesn't have ANY Boot Option Priorities.

I am guessing that the laptop doesn't detect anything with bootable sectors.

Can anyone help?

I followed a different Strategy.
I rebooted with the live DVD.
I asked to delete and reinstall Ubuntu.

It WORKED!

However it created a partition for EFI automatically.
And it mounted only one partition from the ones I had created the "/".

The other two partitions which were "/home" and the rest of the disk which is supposed to be mounted under "/home/username/Data"  have not been mounted.

I tried to do it with GParted, but it does not allow me to mount them.

Does anyone know how to do what I ask?
Thanks!

---

### Post by oldfred on 2015-10-13
You have to copy data to /home and unmount existing & mount the new one. If you already have data or no data to worry about, you may just need the entry in fstab for separate partition that is /home.
 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

If you have data partitions to mount also:

 [http://ubuntuforums.org/showthread.php?t=1983336](http://ubuntuforums.org/showthread.php?t=1983336)
Mount & edit fstab from user Morbius1 in Post # 6 - suggest using templates instead.
Good example of manually mounting, except I prefer /mnt/xxx as location to mount to.

      
 Understanding fstab
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[URL="https://wiki.archlinux.org/index.php/Fstab"]https://wiki.archlinux.org/index.php/Fstab
[/URL]
 [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

[URL="https://wiki.archlinux.org/index.php/Fstab"]
[/URL]

---

### Post by Ifaistos on 2015-10-14
Here is a small guide to the solution for someone who has the same problem with me:
[http://ubuntuforums.org/showthread.php?t=2298860](http://ubuntuforums.org/showthread.php?t=2298860)

Many thanks to the community for all their help!
Viva Ubuntu!!

---

