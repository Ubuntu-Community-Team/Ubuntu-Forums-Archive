---
title: "After 10.04 upgrade Win Vista does not boot"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by bogan on 2010-06-15
I have a similar problem to that described in the 'MBR questions (and: Windows 7 not booting with Grub2)' Thread, except that mine is with Vista and the bootinfoscript result is different. Also I am much less clued up on Linux than appears to be the author of that thread.
I have upgraded from Ubuntu 9.10 to 10.04 on my desktop PC, running Vista from sda1 with Linux on sda6 (actually the second partition of the 320 gig master drive, there is a similar external HD that causes the high number, but its presence or absence has no effect on my problem).
On booting, a cursor flashes top left on a blank screen ( no 'Grub Loading' text) and then the grub menu shows the new 32.22 Linux options and the Windows Vista booting from sda1.
If I press enter on the Linux option the cursor flashes for 20 seconds and then boots into Ubuntu with no problems.
If I press Enter on the Windows option the cursor flashes for 3 minutes without any change, completely unresponsive to any Keyboard input. ( I have not left it any longer, I have to hit the power button to shut down.)
If I press 'e' on the Windows option the screen shows: Gnu Grub v1.98 -1ubuntu6; Ctrl-x gives a terminal with a 'GRUB>' prompt, but it does not recognise any commands I tried. The boot option shows 'Disk Boot Failure,insert System Disk and Press Enter.' Pressing Enter reverts to the Grub Menu.
Booting from a Vista recover DVD and running Startup Repair shows no error, but it still does not boot. The dvd does not give me the option to repair the MBR, but does offer a Command Prompt. Can I repair the MBR from there ? if that is what I need to do.
If so what commands should I use ?
Bootinfoscript shows Grub2 in sda0 and both sda1 and sda5 (the Recover partition) pointing to different places in neither of which is core.img to be found:
```
=> Grub 2 is installed in the MBR of /dev/sda and looks on the same drive in 
    partition #6 for /boot/grub.
sda1:
    File system:       ntfs
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda1 and 
                       looks at sector 348606960 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. No errors found in the Boot Parameter Block.
    Operating System:  Windows Vista
    Boot files/dirs:   /bootmgr /Boot/BCD /Windows/System32/winload.exe

sda5: 
    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 348606664 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    Boot files/dirs:                                     
```Should I remove the Grub 2 from one or more of the partitions, as described by darkod ?

My system is : Medion MD 8822 with a 2.9GHz Dual Core Intel CPU, running Vista Home Premium 32 bit, 2Gb DDR2 Ram, 320 Gb Sata HD and externally similar HD( not plugged in when these tests were done, though it was during the upgrade installation).

---

### Post by Mark Phelps on 2010-06-15
> **bogan said:**
> ... Can I repair the MBR from there ? if that is what I need to do.If so what commands should I use ?
Command are "bootrec.exe /FixMbr" and "bootrec.exe /FixBoot"

See link below for more details:

[http://support.microsoft.com/kb/927392]("http://support.microsoft.com/kb/927392")

> Should I remove the Grub 2 from one or more of the partitions, as described by darkod ?
Wouldn't hurt, but fixing the Vista boot will correct that partition.  As long as you're not trying to boot from the FAT partition, it shouldn't really matter.

---

### Post by bogan on 2010-06-16
Thanks Mark, for your response.
I ran bootrec.exe /FixMbr and restarted from the repair disk but it went straight into the black screen and flashing cursor. A Power off reboot did the same thing, ie Grub did not run, or at least nothing showed.
I then ran bootrec.exe /FixBoot and restarted from the repair disk . It went direct into Vista. Similarly, a Power off reboot did the same thing, ie Grub did not run, or at least nothing showed.
 So I have got Vista back but lost Linux, so I cant rerun bootinfoscript.

What do I do now? Re instal Grub?  If so how? Can I boot from a 9.10 CD and do it from there? if so what commands? Would the Cd have Grub 2 or earlier?

Sorry for my ignorance, thanks for your help.

---

### Post by wilee-nilee on 2010-06-16
Just from the short list of the script it looks like a test disk fix to get rid of grub in Vista but before you do that post the whole script there could be other problems.

As far as I know which isn't much lol the fix/boot and fix/mbr only change the mbr not the grub in the windows partition. So post the script darkod will be on soon probably.

I misread the script I think it's time to crash.

---

### Post by darkod on 2010-06-16
You would have probably got away with just the /fixboot command. Since you also run /fixmbr, as the command itself says, it overwrote grub2 on the MBR with windows bootloader.

When you just want to repair the partition boot sector, don't run /fixmbr and it should still work.

Yes, just reinstall grub2 to the MBR with your 9.10 cd or even better with 10.04 cd. Depending what partition is your ubuntu root, and how many disks you have, the commands will differ.

It's best to boot live mode and post the results of

sudo fdisk -l

PS. I just noticed at the top of the code windows in your first post, it seems sda6 is your ubuntu partition. In that case the reinstall command would be:

sudo mount /dev/sda6 /mnt
sudo grub-install --root-directory=/mnt/ /dev/sda

But usually selecting wrong option where grub2 to be installed during the upgrade process breaks only windows boot, not ubuntu. So I'm confused whether there is another problem too.

---

### Post by bogan on 2010-06-16
Thanks Darko, for your suggestion, I ran grubinstall from a 9.10 DVD and I now get the old 'Grub Loading' Text, which is much more comforting than the Grub 2 flashing cursor.

```
ubuntu@ubuntu:~$ sudo mount /dev/sda6 /mnt
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt/ /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt//boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script 'grub-install'.
(hd0)    /dev/sda
ubuntu@ubuntu:~$
```Both Vista and Linux Ubuntu 10.04 now appear to run OK, whether there are other faults or not. The only thing I have found wrong is that the Recover Partition will not boot and run Recovery Mode when F8 is held down, as Microsoft say it should. Due to the extra copy of Grub 2 in sda5 ??

As you suggest it was Vista that was shut out; Linux was shut out by my using bootrec.exe/FixMbr as suggested to cure the Vista boot problem.
I have rerun bootinfoscript again and the full texts before and after are attached:

If you do not see  other faults in the Results2 text, I guess we can call that a Satisfactorily Solved One.):P

---

### Post by darkod on 2010-06-16
I don't know how it happened, but your recovery partition seems to be logical partition. Usually they are always primary. If you were moving around or creating partitions maybe you moved it as logical.

sda5: _________________________________________________________________________

    File system:       vfat
    Boot sector type:  Grub 2
    Boot sector info:  Grub 2 is installed in the boot sector of sda5 and 
                       looks at sector 348606664 of the same hard drive for 
                       core.img, but core.img can not be found at this 
                       location. According to the info in the boot sector, 
                       sda5 starts at sector 63.
    Operating System:  
    [COLOR=Red]Boot files/dirs:[/COLOR]

On another note, there are usually boot files included in it, to kick off the recovery process.

As it is, I don't know if you will ever be able to use it. And I'm not even sure how it worked, on different computers it works differently.

---

