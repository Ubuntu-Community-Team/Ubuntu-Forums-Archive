---
title: "GRUB geom error"
date: 2010-02-16
forum: Installation &amp; Upgrades
---

### Post by stefano91 on 2010-02-16
Hello everyone! I've a netbook with XP pre installed and a 500GB usb hard disk.
my netbook disk was already partitioned with a 8GB partition of backup already made by acer when i bought it,and the rest was the Xp partition.then i wanted to intall ubuntu 9.1 on my usb disk so i partitioned it whit partition magic.then i run the ubuntu cd and installed it but it didn't recognized the new partition so i installed it in the old one,it was still enough.but when i restarted my pc at boot it says "GRUB geom error. system not found".and neither xp nor ubuntu start.i tryed the fixmbr,the fdisk/mbr and cotrolled the partition.now i can just acces to it with the ubuntu live cd i have put on an usb pen drive.can you help me?
thank you!and sorry if i made any mistake 'cause i'm not english!

---

### Post by oldfred on 2010-02-16
Just so we can see exactly what is where, run this script:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by stefano91 on 2010-02-16
thanks!I did what ypu asked me.
sda it's my netbook hard disk,whit the partition 1 of auto acer backup and the 2 ok xp.
sdb is my pendrive whit ubuntu.
sdc is my external usb disk whit the partition 1 of data storage,the 2 whit the ubuntu install (that doesen't works) and 3 is the one i made with partition magic that ubuntu install didn't recognized.
now what do you think i should do?

---

### Post by oldfred on 2010-02-16
When you installed grub you did not install it to sda but to sda2 - partition boot record (PBR). Grub is intended to install to the MBR as that is what a computer uses to boot. Windows boots from the MBR but has additional files in the PBR to continue booting. You need to reinstall those files to get windows to work.

There are several ways depending on what is booting:
How to fix XP when the boot files are missing & info on windows in logical partitions
[http://ubuntuforums.org/showthread.php?t=813628](http://ubuntuforums.org/showthread.php?t=813628)

Restore PBR boot secotr for windows from linux using testdisk
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Boot_Sector)

To run the Recovery Console from the Windows XP startup disks or the Windows XP CD-ROM, follow these steps:
1.    Insert the Windows XP startup disk into the floppy disk drive, or insert the Windows XP CD-ROM into the CD-ROM drive, and then restart the computer.

Click to select any options that are required to start the computer from the CD-ROM drive if you are prompted.
2.    When the "Welcome to Setup" screen appears, press R to start the Recovery Console.
3.    If you have a dual-boot or multiple-boot computer, select the installation that you must access from the Recovery Console.
4.    When you are prompted, type the Administrator password. If the administrator password is blank, just press ENTER.
5.    At the command prompt, type this commands one at a time.

FIXMBR  C:
FIXBOOT  C:
COPY [CDDRIVE]:\I386\NTLDR  C:\
COPY [CDDRIVE]:\I386\NTDETECT.COM  C:\
BOOTCFG  /rebuild

To repair windows with mounting issues from your Windows XP CD - Do not run fixMBR unless you want windows boot loader in the MBR.
fixboot C: 
chkdsk C: /R
Thread with this and other repair suggestions
[http://ubuntuforums.org/showthread.php?t=1393848](http://ubuntuforums.org/showthread.php?t=1393848)
Check disk from CD - WinXP recovery console - menu shown with example
[http://kb.wisc.edu/helpdesk/page.php?id=5097](http://kb.wisc.edu/helpdesk/page.php?id=5097)

---

### Post by stefano91 on 2010-02-21
Thank you!!!now windows works!i did the fixboot and fixmbr and i copied the files from the cd as you told me.i have another question now: what i have to do to make also ubuntu works?it is still installed on my external disk but from windows i can't see his partition.is it normal?and at the boot i can't choose anything,also if in the bios i put the external hard disk as first choice.can you help me?

---

### Post by oldfred on 2010-02-21
If you install grub to the external sdc then when you boot the external ubuntu will boot and when you boot the internal windows will boot. Grub in the external should also find the windows so if you make the external boot first in BIOS youcan choose which to boot. You should make the external first in BIOS as grub particularly with externals sometimes installs itself to the internal.

Windows will not see the Ubuntu partitions but linux can easily read NTFS partitions. I created a shared partition and put anything that I might want in either like firefox profile, thunderbird profile, docuements and photos in the shared partition. That way both could read common data.

Just make sure you put grub into sdc or the external drive. Sometimes externals numbering can change.
How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

### Post by stefano91 on 2010-02-22
I did as the link told but in the last passage where i run the command grub-install it tell me so:

> grub-probe: error: Cannot find a GRUB drive for /dev/sdc6.  Check your device.map.

Auto-detection of a filesystem module failed.
Please specify the module with the option `--modules' explicitly.


why?what i did wrong?thank you very much for your help!!!!

---

### Post by oldfred on 2010-02-22
Since you can boot still?

reinstall from working system - first find Ubuntu drive: 
sudo fdisk -l 
if it's "/dev/sdc"  then just run: 
sudo grub-install /dev/sdc 
If that returns any errors run: 
sudo grub-install --recheck /dev/sdc
Then: 
sudo update-grub

Do not install to sdc6, but to sdc the MBR.

---

### Post by stefano91 on 2010-02-22
I've done as you told me.it gives me another error.but I'm not so expert to understand.I took a picture of the page...where is the problem?thank you again!!!

---

### Post by oldfred on 2010-02-22
those commands you have to run after booting into a working system to install grub to a different drive. They do not work from the liveCD.
 If you have to install grub from a liveCD you can use the instructions in the link previously posted.

---

### Post by kansasnoob on 2010-02-22
From the Live CD you should be able to:

```
sudo mount /dev/sdc6 /mnt && sudo mount --bind /dev /mnt/dev &&sudo mount --bind /proc /mnt/proc && sudo chroot /mnt
```

```
grub-install /dev/sdc
```

If that shows any errors then:

```
grub-install --recheck /dev/sdc
```

Then exit, unmount, and reboot:

```
exit
```

```
sudo umount /mnt/dev && sudo umount /mnt/proc && sudo umount /mnt
```

```
sudo reboot
```

---

### Post by stefano91 on 2010-02-22
I do this but it gives always to me that error.look yourself...

---

### Post by kansasnoob on 2010-02-22
OK look here:

[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Cannot_Find_A_Device_For_boot/grub](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Cannot_Find_A_Device_For_boot/grub)

If that doesn't work I still have one more trick up my sleeve :D

---

### Post by stefano91 on 2010-02-22
I've done both.the first gives me an error, the second seems to load something but after 10 mins has not ended yet...uff i'm unable!!!any other suggestion?thanks!!!

---

### Post by kansasnoob on 2010-02-22
Just happened to think I wasn't very clear. Referring to that last link when it says:

> Install grub via

    ```
sudo mount dev/sdXY /mnt
sudo grub-install --recheck --root-directory=/mnt /dev/sdZ
```


"sdXY = sdc6"
"sdZ = sdc"

And you don't have a separate /boot partition or a a custom designed device.map.

So the next step is to revert your external drive to legacy grub, but I would like to have you run the Boot Info Script again and post the new results.

---

### Post by kansasnoob on 2010-02-22
> **stefano91 said:**
> I've done both.the first gives me an error, the second seems to load something but after 10 mins has not ended yet...uff i'm unable!!!any other suggestion?thanks!!!

Sorry I got distracted with a phone call. Refer to my last post.

---

### Post by stefano91 on 2010-02-23
ok here is the result...but i tried to boot from usb hard disk first.and i can chose between xp,ubuntu,ubuntu recovery and memory test.i selected ubuntu but during loading(and it is also quite slow,normal?)the loading bar stops and it crash.i also tried the recovery mode but after a lot of time it gives me an error but i don't remember exactly what because i did it yesterday eveneing...

---

### Post by stefano91 on 2010-02-25
Plese can some one help me?is there a command ti know where is rhe problem?or i have to do something else?thank you very much!

---

### Post by oldfred on 2010-02-25
You are past boot problems and into something on your system not working correctly. We need to know the last command it tried to run from the recovery boot.

Did your system boot ok from the liveCD? Sometimes added parameters are needed to get a video card to work.

Others with slow boots have solved them this way.

Slow boot change device.map
[http://ubuntuforums.org/showthread.php?t=1313207](http://ubuntuforums.org/showthread.php?t=1313207)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

Very long boot solved with experimental grub1.98 post8
[http://ubuntuforums.org/showthread.php?t=1367488](http://ubuntuforums.org/showthread.php?t=1367488)

---

### Post by stefano91 on 2010-02-25
yes from Cd it boot perfectly!and also from windows.it also find the grub and find the ubuntu installation.but when there is the loading with the bar under the writing "ubuntu" the lighting ball of loading bar stops after a few second.and nothing else happen.and i can't see the motivation...

---

### Post by stefano91 on 2010-02-25
ah i forgot to tell one thing!i didn't told it because i though it was normal but maybe it isn't. after i select ubuntu in the grub menu it load whit the underscore( _ ) for a while then appear the shivering ubuntu logo then the underscore again then some loading textes.they're quite logng, about a screen.i thought it was normal loading but maybe tell something important.have i to refer them to you?

---

