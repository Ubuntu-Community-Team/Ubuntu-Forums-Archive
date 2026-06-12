---
title: "Installing Windows 8.1 after Ubuntu 14.04."
date: 2015-05-23
forum: Installation &amp; Upgrades
---

### Post by Thorgils on 2015-05-23
Hi guys!

I'm already used an Ubuntu 14.04. system paralel with a Windows 7. But after a few years my old Winows slowed down, and became totally unusable. So I decided to replace it with a WIndows 8.1, but I heared about the problems with installing Windows after Ubuntu.

I'm asking for a solution, to set up the Master Boot Record after the Windows installation, and allowing the Grub, to select the operating systems, which I want.
Thanks for it previously! 

I have found a solution in askubuntu.com for Win7 and Ubuntu 10.04 (I think), but it not works in 14.04, neither 12.04, as I tried. If someone has a solution for older systems, I welcome them too.
[http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu](http://askubuntu.com/questions/6317/how-can-i-install-windows-after-ive-installed-ubuntu)

Thank you!

---

### Post by grahammechanical on 2015-05-23
There is a complication that you should be aware of. Does the motherboard have a BIOS or UEFI boot system?

I have installed Windows 8 preview on my BIOS motherboard after installing Ubuntu. The installation will overwrite the Grub boot loader in all hard disks that are connected. But I think it gets complicated if the motherboard has UEFI. I think that Windows 8 will install in EFI mode and if Ubuntu is installed in legacy mode there will be problems. Note the panel at the bottom of this page.

[http://windows.microsoft.com/en-GB/windows-8/what-uefi](http://windows.microsoft.com/en-GB/windows-8/what-uefi)

On my BIOS motherboard after installing Windows 8 preview I ran the Ubuntu live session. I used the file manager to open the hard disk (it was sda) and that mounted the hard disk. Then I ran

```
sudo grub-install /dev/sda
sudo update-grub
```

Regards.

---

### Post by Thorgils on 2015-05-24
I have Bios luckily! And I have downloaded the 32 bit version of the Win8.1.

 Thank you for the answer :)  I have found another solution yesternday evening, and succeeded in virtual box. 
Today I will find out how it works in reality. I will return with the results

---

### Post by oldfred on 2015-05-24
Even with BIOS, you still have to make sure Windows 8 has it fast startup or always on hibernation turned off. And fully shutdown each time you switch.
The Linux NTFS driver will not mount a hibernated NTFS nor one needing chkdsk. Then grub2's os-prober cannot add it to grub menu, nor will it boot from grub menu.

Once Windows is working and reset so fast startup is off, then restore grub. Best to have both a Windows repair flash drive or know how to get to repair console from your Windows installer and an Ubuntu live installer, so you can reinstall grub after Windows overwrites it in the MBR.

       How to restore the Ubuntu/XP/Vista/7 bootloader  Or any BIOS Windows install.
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System

[/URL] Fast Startup off/hibernation
[http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html](http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html)
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by Thorgils on 2015-05-24
Thank you, they were usefull links, I have found the solution in one of them, which I was used. And that works now! Everything's OK :D :D :D

---

### Post by Thorgils on 2015-05-24
By the way, I'm actually newby in this forum. How can I change the [ubuntu] label to [solved] ?

---

### Post by oldos2er on 2015-05-24
At the top of the page, click the drop-down menu next to Thread Tools, then 'Mark this thread as solved.'

---

### Post by Thorgils on 2015-05-24
Thanks! :)again

---

### Post by Thorgils on 2015-05-25
So, to make it clear, I'm going to share how I've solved the problem - If someone has similar purpose

**Note that**: I istalled Windows 8.1 32bit beside an Ubuntu 14.04. (still 32bit) and my computer use BIOS firmware, not UEFI. 

First: Install the Windows to a separate partition, make sure, that it not confronts with your Ubuntu system or data partitions
After the installation you will able to start just the Windows, and your old Ubuntu can't reach. But that is still there (if you done well), just the Windows bootloader overwrote the grub.

To fix it you must start an Ubuntu Live CD (That sees your Linux and Windows partiton too). Boot from it, choose the "try Ubuntu" option.

**Note that**: When you use live CD you can easily become root, without password. If you typing pell-mell, it could cause catastrophic results. Don't type anything if you not understand what is it. If you might beginner, please read the whole explanation, before you do anything.

Then, mount your original Linux partiton:
```

$ sudo mount /dev/sdXY /mnt

```

To sdXY wrtie of course your attachment code, and partition number (In my case sda6), that you can find if you start GParted e.g. Search out your own.

Then you sould mount some directories which needed for the next operation.

```

$ sudo mount --bind /dev /mnt/dev
$ sudo mount --bind /dev/pts /mnt/dev/pts
$ sudo mount --bind /sys /mnt/sys
$ sudo mount --bind /proc /mnt/proc

```

After that use the next command:

```

$ sudo chroot /mnt

```

Whit this you've became root in your mounted system (also without password)

Now install grub:
```

$ grub-install dev/sdX # note that there is no number here, (you should type sda e.g.)

```

And if succeeded update it, it is important too, to detect all of your operating systems.

```

$ update-grub

```

If it detected the windows, you can exit now, and unmount everything.

```

$ exit
$ umount /mnt/proc
$ umount /mnt/sys
$ umount /mnt/dev/pts
$ umount /mnt/dev

```

Now you can restart the system, move out the live CD. and everything should work. All of your systems are reachable
The helpfull link was for me this:
[http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd)

---

