---
title: "Grub is mad, computer won't boot."
date: 2005-07-23
forum: Installation &amp; Upgrades
---

### Post by r2tincan on 2005-07-23
What Happened:

1. Installed Ubuntu
2. Didn't have any free space on my primary 80gb disk (~80gb NTFS, 8mb unassigned), so I opted to install to my external hard drive (~140gb NTFS, 20gb linux). I know now this was a bad idea. I opted to install the Grub Bootloader to switch between windows and linux.
3. Finished install, Rebooted. **GRUB ERROR 21**

Okay, so whoever designed GRUB decided to let it kill itself and not let my computer boot if it has a problem, and it has a problem.

Apparently Error 21 means that it can't find the hard drive specified.

So, I thought that my BIOS can't natively read my external hard drive, and I should probably upgrade to a version that could. I spent all night figuring out how to flash my bios using a CD (found out two of my burners are broken and it was my first time flashing BIOS) but alas the new version still doesn't see the damn thing.

Still getting Error 21. 

So I tried a number of other things...

1. Tried putting /root on an 8mb partition on the primary hard drive. This wouldn't work and it wouldn't really tell me why. It just said it failed.
2. Tried installing a different distro (Fedora) but that installation froze.

So basically I'm left with a computer that won't boot.


Does anyone know of a way to resize an NTFS partition without windows or linux running, (or maybe one I can use with knoppix if needed? but preferably something smaller) or maybe restore my old boot record, or edit the boot loader to ignore the missing hard drive and boot windows normally so I can do some partition resizing or  *something*?

I can't find my XP CD, either.

Will teach me for trying to install linux again.

Hardware:
a7n8x Deluxe mobo with BIOS revision 1008
the external HD is a 160gig maxtor connected via USB 2.0

Thanks in advance.

---

### Post by EchoBeach on 2005-07-23
Hi r2
At the moment I can only sympathise!  Sorry!
I have just installed Ubuntu (for the first time) on an external 8Gb drive connected by USB 2.0
My PC is a HP Pavilion Pentium 4 3GHz running XP MCE 2005 - with no CD, just a recovery partition!
Without thinking clearly, I opted for Grub.  Big mistake!  As the PC now won't boot unless the external drive is on and connected.
Since the HP has its own boot menu, I would like to remove Grub - in particular where it is influencing the MBR on the PC's main disk.
Then I will be able to choose to boot Linux without affecting anyone else's use of the PC.
I would like to end up with both the external and internal drives being independantly bootable (Ubuntu and XP respectively) without having to worry about each other.
Echo

---

### Post by varunus on 2005-07-23
Echo,

If you have your windows XP CD, you can boot from it, choose "recovery console," and use the "fixmbr" command to set up your master boot record to load windows.  (You can then use your built-in boot menu).

r2tincan,

Since you can't find your XP CD, There is one thing you can do for a temporary solution.  Ubuntu can resize NTFS partitions; so what you should do is boot the Ubuntu installer and reinstall Ubuntu to your main hard drive.  Follow the instructions here if you need help repartitioning, the installer can do it, and this link has pictures, so it'll be easy.  [http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

After you do this, it will reinstall grub for you, and this grub will work for both Ubuntu and Windows.  You can then at least boot, though it seems repartitioning is not what you want in the long run.  I would recommend keeping the setup with ubuntu and windows on the same drive if you have the room and using the external as storage in both of them; even if you don't want to do this, this procedure will at least make your computer bootable.

---

### Post by EchoBeach on 2005-07-23
Hi Varunus
Thanks for your reply.  Unfortunately my PC came 'preconfigured' with Windows XP MCE 2005, which means it didn't come with a CD.
Echo

---

### Post by codejunkie on 2005-07-23
[QUOTE=EchoBeach]Hi Varunus
Thanks for your reply.  Unfortunately my PC came 'preconfigured' with Windows XP MCE 2005, which means it didn't come with a CD.
Echo[/QUOTE]
i had the same problem with my hp/compaq recovery cds yeah right recovery ](*,)  but this is a great cd it might just be what your looking for it helped me fix mine [http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) it has all the tools to restore your mbr hope this helps.

---

### Post by EchoBeach on 2005-07-23
Thanks codejunkie.
I created my ubcd 3.3 and looked at the mbrtool program, but can't work out how to use it.

I have now managed to successfully boot up Ubuntu on my USB drive: with the help of information in [this thread](http://ubuntuforums.org/showthread.php?t=50590) 

I think I just need to be able to restore my MBR.

---

### Post by EchoBeach on 2005-07-24
My USB drive has Grub installed OK.  The problem, now, is that the MBR on the PC's primary partition needs to access Grub on the USB drive in order to boot.
If I want to start XP, I have to have the USB drive online, so that Grub can direct the boot process back to the primary partition.
I want to be able to have the PC boot straight into XP when the USB drive is not online - at the moment I'm the only one (of four) exploring Linux!
Echo

---

### Post by mingus on 2005-07-24
The Windows MBR can be restored from a bootable W98/ME/DOS floppy.  This is an undocumented command.  After booting make sure you are a the A:\> promt, and do:
fdisk /mbr

If you want to boot from the IDE hard drive with Windows and from there boot into Ubuntu, there is a dual-booting from Windows HowTo in the wiki.  Assuming you have a floppy drive, you (a) install grub to the external drive partition, (b) make a copy of that grub to a FAT formatted floppy, (c) copy that file from the floppy to Windows C:\, and (d) add a line at the end of c:\boot.ini.  Windows ntldr will show a menu choice for Ubuntu, run grub from C:\, and chain load to the Ubunut partition.

---

### Post by EchoBeach on 2005-07-24
Thanks Mingus.
I have Grub installed on the USB drive.  
It is defined such that when I use the PC's own boot menu Grub boots from the first hard drive and partition (hd0,0), when I select the USB drive, but it boots from the second partition of the first hard drive (hd0,1), if I choose the PC's internal HDD (the first partition is the FAT32 supplier's recovery partition with XP MCE 2005 on the main NTFS partition).

When I first attempted to install Ubuntu, I made the mistake of allowing it to update the MBR.

I have tried to 'fixmbr /device/harddisk0' from the Recovery Console, but that hasn't (apparently) changed anything.

All I want to do, now, is restore the normal boot process, whereby the internal HDD boots straight to Windows when the USB drive isn't there.

Thanks for your time.
Echo

---

### Post by mingus on 2005-07-25
[I]. . . it boots from the second partition of the first hard drive (hd0,1), if I choose the PC's internal HDD (the first partition is the FAT32 supplier's recovery partition with XP MCE 2005 on the main NTFS partition).

I have tried to 'fixmbr /device/harddisk0' from the Recovery Console, but that hasn't (apparently) changed anything.

All I want to do, now, is restore the normal boot process, whereby the internal HDD boots straight to Windows when the USB drive isn't there.[/I]

Assuming you mean from a W2K or XP install CD, then the command is just:  fixmbr
I don't recall if the command allows an explicit drive statement; in any event, the default location is the mbr of the first drive defined in the boot sequence.

Also remember that the W$ MBR code will look for the loader on the "active" primary, so be sure that the partition you wish to boot from is marked so in the table and is the partition with the boot sector (also called the "system partition"; XP can reside on more than one partition, as long as the system partition is active).

---

### Post by EchoBeach on 2005-07-25
Thanks Mingus.  All sorted now. :-D
I logged into my XP drive from within the Recovery Console and was heartened to see warning messages when I typed 'fixmbr' (without any parameters).
Rebooted and, sure enough, no mention of Grub.
Tested it again.  Still OK! :-D 
Now I powered up my USB drive and rebooted the PC.  Pressed <Esc> to access the PC's boot menu and selected the USB drive.  Up popped Grub.  And into Ubuntu.
All I need to do now, is to amend Grub's menu.lst to remove references to XP - as irrelevant in this context.
What would the root password be if I wasn't asked to supply it at install time (non-expert)? :| (So that I can 'nano' the file.)

---

### Post by Juergen on 2005-07-25
In Ubuntu you have root disabled by default, but your user is a sudoer.
So do
```
sudo nano /boot/grub/menu.lst
```and the password you're asked for is your **user**-password

---

### Post by mingus on 2005-07-26
[QUOTE=EchoBeach]Thanks Mingus.  All sorted now. :-D

All I need to do now, is to amend Grub's menu.lst to remove references to XP - as irrelevant in this context.
What would the root password be if I wasn't asked to supply it at install time (non-expert)? :| (So that I can 'nano' the file.)[/QUOTE]

Glad all is finally OK.  Juergen nailed the last step, remove the XP stanza (it will be obvious), and you are home free.

---

### Post by EchoBeach on 2005-07-27
Mingus
I've just last night re-installed 5.04 in 'Expert' mode.
I was asked to specify the root password (twice) and then set up an additional user.
Once I'd rebooted and the configuration finished, I logged in with my 'normal' user.
Attempting to run 'Root Terminal' (to edit Grub's menu.lst), I am challenged for the root password; 'wrong password'.
If I try 'sudo nano ...menu.lst', I am informed that my 'normal' account is not in the group 'sudoers'.
I also tried this while started in the 'Recovery' version - the one that had the parameter '/single', but no difference.
What have I missed?
I can see light at the end of the tunnel!
Echo

---

### Post by EchoBeach on 2005-07-27
Juergen
> In Ubuntu you have root disabled by default, but your user is a sudoer.
So do
```
sudo nano /boot/grub/menu.lst
```
and the password you're asked for is your user-password
When I tried that, and put my password in, I got the following response:
```
...  is not in the sudoers file.  This incident will be reported.
```
How do I add the user to that group - without the root password?
Echo

My Grub menu.lst looks like this - in case it's relevant:```
title           Ubuntu, kernel 2.6.10-5-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 ro quiet splash
initrd          /boot/usbinitrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 ro single
initrd          /boot/usbinitrd.img-2.6.10-5-386
savedefault
boot

title           Ubuntu, kernel memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
savedefault
boot
```

---

### Post by pauljwells on 2005-07-27
[QUOTE=mingus][I]. . . it boots from the second partition of the first hard drive (hd0,1), if I choose the PC's internal HDD (the first partition is the FAT32 supplier's recovery partition with XP MCE 2005 on the main NTFS partition).

I have tried to 'fixmbr /device/harddisk0' from the Recovery Console, but that hasn't (apparently) changed anything.

All I want to do, now, is restore the normal boot process, whereby the internal HDD boots straight to Windows when the USB drive isn't there.[/I]

Assuming you mean from a W2K or XP install CD, then the command is just:  fixmbr
I don't recall if the command allows an explicit drive statement; in any event, the default location is the mbr of the first drive defined in the boot sequence.

Also remember that the W$ MBR code will look for the loader on the "active" primary, so be sure that the partition you wish to boot from is marked so in the table and is the partition with the boot sector (also called the "system partition"; XP can reside on more than one partition, as long as the system partition is active).[/QUOTE]
 For partitioning and OS selection I've been using Acronis Disk Director. OK so it's against linux principals to use comercial software, but it seems to be rock-solid. It lets you resize your NTFS partition to give unallocated space, onto which you can install linux. Let the istaller load grub in the mbr but then reinstall Acronis OS selector (a part of disk director) and it writes a neat GUI OS selector that sees all your OSs.

---

### Post by mingus on 2005-07-27
[QUOTE=EchoBeach]Mingus
I've just last night re-installed 5.04 in 'Expert' mode.
I was asked to specify the root password (twice) and then set up an additional user.
Once I'd rebooted and the configuration finished, I logged in with my 'normal' user.
Attempting to run 'Root Terminal' (to edit Grub's menu.lst), I am challenged for the root password; 'wrong password'.
If I try 'sudo nano ...menu.lst', I am informed that my 'normal' account is not in the group 'sudoers'.
I also tried this while started in the 'Recovery' version - the one that had the parameter '/single', but no difference.
What have I missed?
I can see light at the end of the tunnel!
Echo[/QUOTE]

Log in as your normal user.  Open a terminal (not the Root Terminal) and do:
$su
you will be prompted for the *root* password you gave at the install (the 2nd entry was for verification), and the prompt will turn to a # sign.  Now you can do:
#nano -w /boot/grub/menu.lst
or for that matter,
#gedit /boot/grub/menu.lst

Re changing menu.lst - your post does not show a stanza for XP.

If you went in via booting Recovery, you are taken to a prompt where you can drop into a shell as root.  From there you have full access to the system.

---

