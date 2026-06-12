---
title: "Windows XP drive letters changed"
date: 2007-04-19
forum: Installation &amp; Upgrades
---

### Post by mwaddoups on 2007-04-19
I finally installed Ubuntu 7.04 on my main box today, to dual boot with XP. Ubuntu is working well enough, but somehow during install it has switched round C: and D: on XP, so it no longer boots at all! Is there a way I can remedy this from ubuntu? I have tried a bootcfg /rebuild on recovery console, but as it is set to the wrong partition this fails to run. Any ideas?

---

### Post by louieb on 2007-04-19
Without more information I am clueless.  Is this the same PC you have Edgy on? Did you overlay Edgy or are you trying to triple boot? Which partition option did you use? Is this the first time Linux was install on this PC?  Are you sure GRUB was set up right? Can you see your windows data from Ubuntu? 
Please post the output from ```
**sudo fdisk -l**
``` (l as in little) this will list the partition table

---

### Post by mwaddoups on 2007-04-20
This is the first time I have installed Linux on this PC (as Feisty). Both windows partitions are mountable and available from Linux. GRUB seems to be set up right because the error is definitely windows related (something about a missing "hal.dll"). I used the partition option "Largest Continuous Free Space" - My partitions look something like this:

Extended >
[LIST]
[*]Windows Installation Partition  (bootable flag set)
[*]Linux Partition
[*]Swap
[/LIST]
Primary > Second Windows Partition

fdisk -l shows this exact data, so I'm pretty sure it's not the partitions themselves.

---

### Post by Herman on 2007-04-20
Hello mwaddoups,
One way to fix that is to edit your boot.ini file in Windows with the correct partition numbers. 
You probably can't do that directly from Ubuntu if you have the file security for boot.ini set at the default level, and  if you have the NTFS file system in Windows XP you probably shouldn't try to write to it from Linux unless you use special apps.
What you can do is arrange the use of another Wiindows XP computer somehow and make your self one of these special Windows XP boot floppy disks, [How to make your own Windows Xp boot floppy]("http://support.microsoft.com/kb/305595/EN-US/")
These Windows Xp boot floppies have their own copy of NTLDR, NTDetect.com, and boot.ini file. Because the floppy disk is FAT32, you will be able to mount it in Ubuntu and edit the boot.ini file in the floppy disk in any way you need to.

You will still need to know what the new partition number for Windows is now, from the sudo fdisk -l output that louieb asked you for. If you can post that here we may be able to help you more if you need specific help. If you can do it yourself then it doesn't matter. 

When you have Windows booted you can then edit your boot.ini file from within Windows itself quite easily and after that it'll all be fixed.
You are welcome to ask anytime if you would like more details on any part of this.

Another way to go about it is to get yourself a [GParted --LiveCD]("http://gparted.sourceforge.net/") and delete your Ubuntu partition if necessary to make a large enough area of free space to paste your Windows partition. You will need an area at least the size of your Windows partition to do so. If your Windows partition takes up more than half of your hard disk, you may have to remove data and store it somewhere else temporarily. You should have all your data backed up anyway. You may need to delete some data in order to be able to resize your Windows partition small enough to have room to copy and paste it. Then copy your Windows partition and paste it so it will get its original partition number back. Then re-install Ubuntu again.

I think making the boot floppy and editing boot.ini in Windows will probably be easier for you though.

Regards, Herman :)

---

### Post by mwaddoups on 2007-04-21
Herman - your first solution of manually editing the boot.ini worked great! Since my main windows partition is logical rather than primary, it confused me and led me to me trying a lot of other things first. Thanks for the help!

---

### Post by Herman on 2007-04-23
mwaddoups,
Great! I'm glad it worked for you. :)   Thanks for the feedback too.
I didn't know that it is possible to boot Windows in a logical partition unless there is a Windows primary 'boot' partition containing the boot loader files. 
Does your Windows XP boot through an old Windows98 installation in a primary partition that contains all the bootloader files from WindowsXP?
I would like to learn more about this type of arrangement.
Regards, Herman :)

---

### Post by mwaddoups on 2007-04-23
That was what confused me as well - it had just been set up that way by Windows. My boot.ini/ntldr files were stored on a separate partition in Windows - my old D:\ partition, and since Ubuntu was installed it changed the boot.ini partition numbers, and therefore lead windows to believe that D:\ was C:\. I guess that when Windows was installed, since I already had the other primary partition it automatically installed in a logical partition (although why is another matter!).
Hope this clarifies things.

---

### Post by Herman on 2007-04-23
I have an interesting link on the subject here, [http://www.goodells.net/multiboot/index.htm](http://www.goodells.net/multiboot/index.htm). 
That is only for people who have some spare time and who are really interested in this subject as it is quite a lot of reading. 

What I really want to find out is if the Windows logical partition is able to be recovered (made bootable again), if the primary partition is deleted to install Ubuntu in. A few people have reported doing that but so far no-one has reported any success with booting their subsequent Window (in the logical partition). I think they would need to re-install Windows if that was the situation. I have tried it myself and I was unable to boot Windows in a logical partition at all. I'm only interested so I can use the information to possibly help people in those circumstances.
There is no need to reply again though, I don't mean to bother you if you are busy. I will experiment with it more sometime myself when I get time. I'm just happy yours is booting allright. :)
Thanks for replying again.

Regards, Herman :)

---

### Post by hbherman on 2008-03-14
When I installed Ubuntu Hardy (alpha 6) as a dual boot (Vista was already there), the drive letters changed (c: became d: and vice versa). I then couldn't run either Vista (no ntldr) or Ubuntu (no partition).
I tried everything I could think of, but nothing worked. What finally worked, was a reinstall of Ubuntu Hardy whereupon  the drive letters reverted to the correct pair.
That is my interpretation which may or may not be correct. I believe I made no errors in the first install and did exactly the same on the second.
Harvey

---

### Post by Herman on 2008-03-14
:) Hello hbherman,
Hmmm, I don't know what might have been going on there. :-k

Windows uses the drive letter A: for the floppy disc drive and B for one of those bigger old fashioned floppy disc drives that no-one has anymore.
'C' represents the hard drive, I understand, and D would be the CD-ROM drive normally, but if another partition is made in the disk, it gets assigned the 'drive letter', (or should we say 'partition' letter?), 'D', bumping the CD-ROM drive to something else.
If you have more than one installation of Windows in a computer, and they can 'see' each other, one Windows will think it's 'Drive C', and the other will be 'Drive D', and the boot loader files from the new 'Drive D' installation will be copied to 'Drive C', making the 'Drive D' Windows dependant on the 'Drvie C' Windows for booting.
If GRUB's 'hide' and 'unhide' commands are used to hide the first Windows installation from the other during installation, they will both think they are on 'Drive C', meaning 'the hard drive'.

In Linux when we say 'disk' or 'drive', we mean a hard disk drive, and if there are more than one hard disk drive in a computer, the hard disks are numbered from one to whatever number, according to how they are plugged in a jumpered, and how they are set up in the BIOS.
When we get used to the way Linux numbers partitions, it has real meaning. Partition numbers 1, 2, 3 and 4 can all be primary partition numbers, and one of those can be for a extended partition.
Numbers 5,6,7 and so on, are logical partitions.
Linux drive numbers and partition numbers make a lot more sense to me.

To say your Windows drive letter changed from 'C' to 'D' really doesn't tell me anything useful, but if you had said your partition number was changed accidentally, and then changed back again, I would guess that maybe there was a bug in your partition table.
Otherwise, it might have been a bug in Windows.
Either way, it is likely to have been a bug in Windows. Windows is quite buggy, especially their partitioning program, and has been reported to have caused a number of partition table problems already.
It could be that Windows left a buggy code in your partition table and Linux choked on it the first time you used a Linux partitioner to install with, but the second time the Linux partitioner was able to successfully repair the problem.
Normally, the Ubuntu installer would have failed on the safe side and refused to look at a hard disk with a glitch in the partition table, and you would not be able to proceed with the installation at all.

Anyway, all's well that ends well, and I'm glad you ended up with a successful dual boot. 
If anything like that happens again, it would be interesting to see the output from 'sudo fdisk -lu', from a Live CD. That might show up a problem if the problem is inside the partition table. If it's a problem inside Windows Vista then who knows?  :lolflag:

Regards, Herman :)

---

### Post by ptaeck on 2008-04-09
Hello Herman,
I luckily found the exact thread I have been looking for;)
Got the same problem as hbherman. Here is the story:

Before 3 days I got my vista installation working beside with xp and my newly installed and "tuned" ubuntu hardy heron (upgraded from gutsy). Got grub menu for Ubuntu and vista boot loader but I decided to use only the vistas boot loader even for the linux. 
(now I know it was BAD choice)

Everything was working OK with 2 bootloaders - Grub et vista boot loader: 
xp booted with drive C:/ (hd0,0), vista drive booted also as C:/ with drive letters reasigned, so I was able to browse the xp directly from disk D:/, and the ubuntu from partition(hd0,6). 

Finally I got interrested in playing with MBR, luckily I have made MBR backup and also installed the current bootloader to floppy. Inspired by this  [[COLOR="#004080"]topic[/COLOR]]("http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/") I somehow got it working as you can see in the last [[COLOR="#004080"]screenshot[/COLOR]]("http://duggmirror.com/software/How_to_Build_Triple_Boot_XP_Vista_Ubuntu_with_single_Boot_Screen_wpics/ebfa93091c617b43b9509c9c40b71d3e_061113-vista-winload.png") - of course I have not reinstalled my whole disk.

But here comes the problem(s): first time booting vista the welcome screen is there a bit longer, then suddenly appears "Preparing Desktop" - at this moment I know there is something wrong - after apx. 4 min watching the prepairing screen and poking into my nose was loaded default user. My shiny vista desktop was gone, suddenly appeared a lot of infos about APPCRASH (schvost.exe) and I was not able even run a web browser... then I found it - Vista drive is now E:/ and not C:/ like before - and crashes are propably caused by using the "old" XP system files from C:/. Simply to say - the drive letters in vista did not get reassigned. (Forgot to say - In xp/vista was next partition for media, see the list below please:))

BEFORE
xp booted    : system drive C:/ media drive D:/  VISTA E:/
vista booted: system drive C:/ media drive E:/   XP D:/
AFTER
xp booted    : system drive C:/ media drive D:/  VISTA E:/
vista booted : system drive E:/ media drive D:/  XP C:/

Solution? First I grabbed the vista dvd and tryied to repair the system - well it was pretty - vista still bootig as E:/ after several repair attempts, then I plugged the floppy trying to boot Hardy - device was not found :mad: - from grub command line I found out the linux is now (hd0,5) - and I booted linux fine:)
 BUT: the partition table have been changed.
So I said :confused: and restored the MBR from the backup.

From xp then I reset the vistas BCD storage via EasyBCD and reinstalled the vista boot loader.
Everythings almost fine :-k :

Able to smoothly boot xp (first primary partition)
Able to boot Hardy from floppy - from hard disk I get stucked with GRUB _ (see the attachedd image) (first extended partition)
and the vista is still screwed up....(last extended partition)

For detailed info see the screenshot from LiveCD please:

[IMG]http://egyptian.mysteria.cz/download/screenLiveCD.jpg[/IMG]

I am posting this as a last call before I reinstall my vista system.
But I am asking: DO I NEED IT AGAIN? Cause Hardy is much valuable for me now:)

Omg I have written a bit longer post - sorry. Hope you have understood it.And thanks for reading if smb found a little time for me. Have a nice night!

---

### Post by Herman on 2008-04-10
[NTFS and FAT32 file system repair and maintenance]("http://users.bigpond.net.au/hermanzone/p10.htm#NTFS_File_Fystem_Repair_and_Maintenance") - Windows CHDSK - Linux ntldrfix

:) Hello ptaeck, 
Sorry for the delayed reply. 
I can see a yellow triangle there in your GParted screencap.
That is a sign that your Vista partition needs a file system check.
I think you need ro run 'CHKDSK E: /R' from a WIndows Recovery Console.

Try that first, you can read more about it from the link I included at the top of this post if you need more info.

See if that helps, it won't hurt, but I'm not guaranteeing it will solve the problem. It is worth a try though, and if that doesn't work Then we can think some more and try something else.

Regards, Herman :)

---

### Post by ptaeck on 2008-04-10
Vista drive is checked and repaired - but still boots with a wrong letter:(
Thanks so much for your help!:KS

---

### Post by Herman on 2008-04-11
:) Do you mean your Vista boots?
Or, do you mean it still doesn't boot, and has a wrong drive letter?

---

### Post by ptaeck on 2008-04-12
Well vista boots as I described in my first post (5. paragraph), only thing needs to be changed is the letter of the system drive as it used to be.

---

### Post by LaRoza on 2008-04-12
> **ptaeck said:**
> Well vista boots as I described in my first post (5. paragraph), only thing needs to be changed is the letter of the system drive as it used to be.

Drive letters don't mean anything.

Windows assigns them using an outdated method.

If Vista needs to see itself as C:, then when in Vista, go to Computer Management->Disk Managment and assign the letter to it.

Drive letters are assigned as it boots, but can be made static.

Driver letters are a pre MS-DOS novelty. MS-DOS used them to be compatible with the system it was copying (it was new then). Windows uses it because DOS did. 

Drive letters mean nothing to Linux, so you will have to assign them from Windows.

---

### Post by ptaeck on 2008-04-12
Of course I have tryied to change the letter in vista but it is not possible to change the letter of system drive while is vista running.
Even when I am not able to run :arrow:ANY application - I get only message I dont have permission for it and that the app have not been found. When I copied an exe file on desktop I got the same popup. And run it from C:/ did not helped too.:confused:

---

### Post by ptaeck on 2008-04-12
:grin: Hey, pssst, I got what you need - I have solved it! :grin:

So if you get in troubles with changes of system drive letter like me just do this (works for Vista):

You should still be able to boot your "limited desktop", where I thought you can not run ANY app.
But you got luck today as I, because the only thing you need to run is [COLOR="RoyalBlue"]regedit[/COLOR] - and even on "limited desktop" it runs! So - you can just find it in Windows/system32/ folder and once you run it - you have won this fight! Just remember which letter got now your screwed system drive - you will need it.

In regedit find this key:  [COLOR="Red"]HKEY_LOCAL_MACHINE\SYSTEM\MountedDevices[/COLOR]

and RENAME the needed entries [COLOR="Red"]\DosDevices\[drive letter]:[/COLOR] to what you need.

for exapmle:

vista system drive is E:/ and it needs to be C:/

1.FIND the following entry: "\DosDevices\E:" & RENAME it to "\DosDevices\X:"
2.FIND "\DosDevices\C:" &  RENAME it to "\DosDevices\E:"
3.RENAME again the edited entry "\DosDevices\X:" to "\DosDevices\C:"

this easy 3-steps FIND-RENAME method swapped the drive letters C:/ & E:/ :lolflag:


If you somehow dont know which drive letter is assigned to your current system drive - simply delete all entries except the first (Default) one. On next boot it shoud be rebuilded again by default as it happens when you runs your newly (re)installed system and the system drive will be C:/ again.

:guitar:

---

