---
title: "Installing Ubuntu over FC3 - dual boot"
date: 2005-06-22
forum: Installation &amp; Upgrades
---

### Post by oliwally on 2005-06-22
G'day folks, I need a bit of help 'coz I'm scared to stuff up my computer. :roll: 

Some background info:

I'm not completely new to linux, but I'm not very computer-techno minded either. I've tried RedHat 9, Mandrake10 and Fedora Core 3. All of these have been set up on my computer as a dual boot systems on two separate HDDs, where WinXP has been on one and Linux on the other. Worked well most of the time but found all the mentioned distros a bit complex to configure. Never really got it all running smoothly. Either sound wasn't working, network not working, video drivers not working etc. I know all this can be fixed, but for one such as I it's all just too much mucking around.

Then I tried Ubuntu live CD. The clouds blew away, birds started to sing, the scent of sweet flowers filled the room, everything worked well, the smile on my face was from ear to ear......until I started considering how to install Ubuntu for good ! I've had some trouble in the past with changing distros.  ](*,) 

Last time I tried to swap distros, just by simply installing over the top of an existing distro, I could no longer boot into either Linux or Windows. Somehow the MBR got messed up (if I comprehend correctly). Due to my limited computer knowledge I had to rescue all files and install everything from scratch - not the preferred option !

My current setup has XP on one drive, FC3 on the other, and grub managing the dual bootup stuff. At bootup I get the option to choose which OS to use. All works sweet (except for the fact that I'm having disagreements with FC3).

My question then (at long last). Will all be well if I simply stick in the Ubuntu installation CD and attempt to install over the top of FC3 ? Are you sure all will be well? Will Grub be ok? Will I have to configure Grub to give me the Ubuntu option? 

If this is not possible, then what are my best options? Should I uninstall FC3 and fix the MBR so that, at bootup, all will be as Mr Gates would want it to be?

If I need to reinstall the MBR, then what is a totally idiot-proof way of doing this ? Last time I tried the Windows XP installation CD  fixmbr  option etc, but it did not work for me - total disaster. I found that Mandrake had a neat little button on their installation CD to reinstall win MBR - that worked well, but FC3 doesn't have such a function. Isn't there a neat little utility that will magically reinstall the MBR as it should be ?

Please help. I want to go to Ubuntu but I'm just too scared to mess my computer up (again).

---

### Post by bunced on 2005-06-22
Yes, Ubuntu installs it's own GRUB, and configures it automatically for Windows. Just follow through the install procedure and choose to have it install on /dev/hda. 

Post if you need more help

Regards
David

---

### Post by mingus on 2005-06-22
You have a grub installed now in your MBR, by Fedora.  If you install Ubuntu you must either reinstall the MBR with the new grub *or* set up the system so that the BIOS bypasses this MBR.

Options:

1.  Install Ubuntu grub to first drive's MBR and use grub menu to go to Windows boot.  This is how you are set up now with Fedora.  Most straightforward, but occasionally does not work because of Windows conflicts, or has to be tweaked after install; a pain.  So, repeat this step in the install and install grub to a floppy, too.  That way you can be sure to get in if there is an MBR problem.  In fact, as a precaution, install grub to floppy no matter what.

2. Install grub on the Ubuntu drive only, with a menu choice to boot Windows,  This would look just like what you have now, but actually be doing it differently.  It avoids messing with the Windows drive's MBR altogether.  Two ways you can go with this.  You can just install grub to the second drive's MBR (/dev/hdb) and point the BIOS to boot from this drive instead of the first.  Or, you can install grub to whichever partition your /boot directory is on; this requires previously setting the boot flag on this partition during that step of the install.

---

### Post by oliwally on 2005-06-23
Thanks for the prompt help. 

I have a few more questions before taking the blue pill...

mingus - option 2 with Grub on ubuntu drive MBR only, so that windows drive MBR is not messed up, and then pointing Bios to boot from there sounds good. Would this not require me to reinstall the Windows MBR first? How will Grub know where to find the boot record to boot into window (if required) - or will it just find it from what Fedora has done?

 Should I just simply stick in the Ubuntu (actually Kubuntu for me) installation disk and proceed with the install? I'm just worried that I will loose my ability to boot into windows, since Grub has messed with the MBR on my windows drive. How will this be restored?  How will the new Grub installation know where to find the MBR to boot into windows. I'm still a little too worried to proceed at this stage.

Please keep helping me ! Thanks so much.

---

### Post by mingus on 2005-06-23
*option 2 with Grub on ubuntu drive MBR only, so that windows drive MBR is not messed up, and then pointing Bios to boot from there sounds good. Would this not require me to reinstall the Windows MBR first? How will Grub know where to find the boot record to boot into window (if required) - or will it just find it from what Fedora has done?*

Good questions.  I could give you just a yes/no answer, but seems a bit of theory might  be helpful; note that this is how Windows XP/2K works, which is a bit diff than earlier vsns and also much less flexible than Linux, but the general concepts are the same:  The last step of the BIOS is to look for a program in sector 0 of the device(s) defined in the BIOS as bootable.  If the device is a hard drive, the "record" (the program file is very small, only 1 record) placed in this sector is commonly called the Master Boot Record.  There is only one function of the MBR's code - to start the boot loader, which in Windows is c:\ntldr.  Ntldr needs 2 files to work, ntdetect.com and boot.ini.  These three files together make what MS calls the "system partition".  This is always the first primary partition, and ntldr always sits in the sector 1.

So, all that is required to boot Windows is a method to start ntldr.  The default is the MBR, but that function can be performed a number of other ways.  For example, if you place the system partition files on a floppy, you can boot from directly from it.  Or if you have grub (or lilo) installed in the MBR *or* anywhere else that the BIOS can find it, grub can start ntldr.  This is called "chain-loading".  Look in grub's menu.lst and you will see a short stanza that defines where the system partition is and where ntldr loader is on that partition (the +1 means the first sector).

Therefore, **assuming that your BIOS allows you to define the 2nd drive in the boot sequence**, if grub is properly installed on that drive, and you ask for Windows, grub will look for ntldr and run it.  The first drive's MBR is never looked at, which is where the Fedora MBR code is now.

Personally, if I were to use this setup, my first step would be to rewrite the first drive's MBR with the Windows version, and test booting Windows directly.  This way it's very clean, the OS's are on separate drives with each having its own MBR.  If for some reason the chain-loading from grub on HDD2's mbr to HDD1's ntldr doesn't work, you can get back into Windows by simply changing the boot sequence in the BIOS.  And you don't have to worry about one OS overwriting the other's MBR (as Windows sometimes does, likewise antivirus and drive overlays).  Furthermore, in a jam you could also just swap the drives or even put either drive in another system - both drives are independently bootable.

*Should I just simply stick in the Ubuntu (actually Kubuntu for me) installation disk and proceed with the install?*

Probably, but it depends.  In the Ubuntu install, I think by default it will create 3 partitions (/, /home, swap) with the ext3 filesystem.  Likely that is fine for you.  However, do you have anything on that drive you want to keep, like user data files in the Fedora /home directory?  If so, you'll want to think about how you want to organize the partitions, keeping this.  And you will certainly not want to wipe the drive, which the Ubuntu install will give you as an option (if you don't want anything that is on it now, then do this).

Make sense?  Don't hesitate to ask.  We appreciate the criticality.

---

### Post by ah.heng on 2005-06-23
[QUOTE=mingus]Personally, if I were to use this setup, my first step would be to rewrite the first drive's MBR with the Windows version, and test booting Windows directly.  This way it's very clean, the OS's are on separate drives with each having its own MBR.  If for some reason the chain-loading from grub on HDD2's mbr to HDD1's ntldr doesn't work, you can get back into Windows by simply changing the boot sequence in the BIOS.  And you don't have to worry about one OS overwriting the other's MBR (as Windows sometimes does, likewise antivirus and drive overlays).  Furthermore, in a jam you could also just swap the drives or even put either drive in another system - both drives are independently bootable.[/QUOTE]

how would you restore the windows MBR exactly?

me and several other fedora users have problems reading the winxp cd after installing fedora. it would load, but the blue installation screen doesn't load, you're just stuck looking at a blank page with a flashing dash.

the general consensus is that it's a grub problem. i'm not sure whether or not FC4 has solved this problem though.

---

### Post by mingus on 2005-06-23
[QUOTE=ah.heng]how would you restore the windows MBR exactly?

me and several other fedora users have problems reading the winxp cd after installing fedora. it would load, but the blue installation screen doesn't load, you're just stuck looking at a blank page with a flashing dash.

the general consensus is that it's a grub problem. i'm not sure whether or not FC4 has solved this problem though.[/QUOTE]

Can you elaborate a bit on the CD problem?  When you boot from it, you should see a line of text about "Windows is inspecting your hardware . . ." and then there is a blue screen titled "Windows Setup."

If you are not seeing *any* of this, then it sounds as though the CD is not being boot from.  That is controlled in the BIOS.  Offhand I can't think of anything on the hard disk that would affect this.

Replacing the Windows MBR with this CD is done after setup runs.  There is a choice ("R") to enter the Recovery mode.  When you get to the command prompt, it's >fixmbr.

Alternatively, you can use a W98/ME/DOS bootable diskette.  You can get one at [www.bootdisk.com](www.bootdisk.com) and elsewhere.  Boot to the A:\> prompt and do:  fdisk /mbr

Yet another method which takes a bit longer is a very good idea for other reasons (like no matter what you do, you cannot get back the MBR).  Create an XP boot floppy, which is simply copying the 3 files of the system partition, as I referred to before.   Additionally, the Recovery mode you use off the CD can be copied to the Windows hard drive, and run from there.  With these two tools, you can always boot Windows, bypassing the MBR.  And you can get to the Recovery console even if you don't have a bootable CD.

[http://support.microsoft.com/default.aspx?scid=kb;en-us;305595](http://support.microsoft.com/default.aspx?scid=kb;en-us;305595)
[http://support.microsoft.com/default.aspx?scid=kb;en-us;307654](http://support.microsoft.com/default.aspx?scid=kb;en-us;307654)

---

### Post by oliwally on 2005-06-24
mingus - thank you so much for your excellent advice. I have a much clearer (and less fearful) understanding of how the boot thingo works. It doesn't seem so scary after all. I can handle 3 little files.

I have created a boot floppy as you suggested, just in case everything goes pear-shaped. It worked like a charm in booting straigt into XP. So therefore, all my fears were blown away, knowing that I could get back into XP.

I then gave the XP CD recovery / fixmbr another go - and that sweet scent of flowers came back to my room. What an absolute rip-snorter !  Although it didn't work for me on previous attempts, this time all was well (that was on a Maxtor HD wich, as I read on other forums, sometimes has a problem with this function for unknown reasons)

So now, thanks to you, I have my normal bootup straight into Windows and I can wipe everything on my second HD (I don't need any of it)  to install Kubuntu there. 

I'll give it a go but may need some more help in making sure that Grub resides on the Kubuntu MBR.  I suppose I will also have to convince Grub to give me the dual boot option and to find the ntldr if I want to boot XP.

I'll write again and let you know how it goes. 

Thanks again - your help is magic !  \\:D/

---

### Post by mingus on 2005-06-24
[QUOTE=oliwally]mingus - thank you so much for your excellent advice. 

I'll give it a go but may need some more help in making sure that Grub resides on the Kubuntu MBR.  I suppose I will also have to convince Grub to give me the dual boot option and to find the ntldr if I want to boot XP.

Thanks again - your help is magic !  \\:D/[/QUOTE]

You are most welcome.

When you install and come to the bootloader step, just be sure that you tell the installer *explicitly* where you want grub installed:  /dev/hdb - don't let it assume /dev/hda!  In this step, behind the scenes the program update-grub will try to set up Windows to be chain-loaded from Ubuntu.  This is controlled from and described in the file /boot/menu.lst.

Good luck!

---

### Post by oliwally on 2005-06-24
Moderate success with a bit of rocky-road thrown in.

I have gone through the installation steps and at the bootloader step have told it to install Grub to dev/hdb. So far so good. When restarting the computer (without changing the bios boot sequence) I was straight back into XP just as expected.

I then changed the Bios boot sequence to go to my Ubuntu drive. All sweet - Grub comes up and gives me several options, including Windows XP.

This is where things did not go as planned. When choosing the Ubuntu option the following message came up:

Booting 'Ubuntu' Kernel 2.6.10-5-386
root (hd1,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz - 2.6.10-5-386 root = /dev/hdb1 ro quiet splash
Error 17 : Cannot mount selected partition

On pressing ENTER the Grub menu came up again. I tried the Win XP option and got the following reply:

Booting 'Microsoft Win XP Pro'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
save default +1
Error 13 :  Invalid or unsupported executable format.


I have no idea how to fix any of that. I'm assuming that Grub is just not finding what it is expecting to find.

What would I need to do to fix this problem ?

---

### Post by ah.heng on 2005-06-24
[QUOTE=mingus]Can you elaborate a bit on the CD problem?  When you boot from it, you should see a line of text about "Windows is inspecting your hardware . . ." and then there is a blue screen titled "Windows Setup."

If you are not seeing *any* of this, then it sounds as though the CD is not being boot from.  That is controlled in the BIOS.  Offhand I can't think of anything on the hard disk that would affect this.[/QUOTE]


it does boot from the CD, it goes into the blue screen and immediately after goes black and stays there.

here's more.
[http://www.fedoraforum.org/forum/showthread.php?t=58553](http://www.fedoraforum.org/forum/showthread.php?t=58553)

---

### Post by mingus on 2005-06-24
[QUOTE=oliwally]
Booting 'Ubuntu' Kernel 2.6.10-5-386
root (hd1,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz - 2.6.10-5-386 root = /dev/hdb1 ro quiet splash
Error 17 : Cannot mount selected partition

On pressing ENTER the Grub menu came up again. I tried the Win XP option and got the following reply:

Booting 'Microsoft Win XP Pro'
root (hd0,0)
Filesystem type is ext2fs, partition type 0x83
save default +1
Error 13 :  Invalid or unsupported executable format.
[/QUOTE]

I'm on the road just now with clients, will only be doing intermittent checking for a while . . .

When you boot the second drive, if you ask for Windows *first*, do you get the same message?
What filesystem did you use to install Ubuntu?
What happens when you use the Recovery Mode menu entry?
Will need you to post back if you can your /boot/grub/menu.lst file and do a "fdisk -l" to post back the partition table and the /etc/fstab to show your mount points and filesystems.

sorry, gotta run . . .

---

### Post by mingus on 2005-06-24
[QUOTE=ah.heng]it does boot from the CD, it goes into the blue screen and immediately after goes black and stays there.

here's more.
[http://www.fedoraforum.org/forum/showthread.php?t=58553](http://www.fedoraforum.org/forum/showthread.php?t=58553)[/QUOTE]

Read this thread and it makes perfect sense . . . problem is not in the boot sequence or even the MBR, but the partition table (which actually occupies the last 50 bytes or so of sector 0; together they comprise what is called the "master boot block").  Windows is very limited and strict in what it can do with LVM, and by design expects to be installed single-user no other OS (incl other W$); this is why touching the partition table is always dicey if W$ is there, too.

---

### Post by oliwally on 2005-06-25
> When you boot the second drive, if you ask for Windows *first*, do you get the same message?

Yes, I get the same message: Booting ' MS Win XP Pro' yadda, yadda.....

> What filesystem did you use to install Ubuntu?

I'm not perfectly sure but I do believe it's ext3 - I used the automated process which set everything up by itself. How would I find out, other than installing again and having a close look?  Should I use the manual partitioning option during installation and specify what type of filesystem to use?

> What happens when you use the Recovery Mode menu entry?

Same error message: Erro 17: Cannot mount selected partition

> Will need you to post back if you can your /boot/grub/menu.lst file 

I know what you're talking about there, but I don't know how to get to it from the grub menu. Please give me instructions on how to get that file.

> and do a "fdisk -l" to post back the partition table and the /etc/fstab to show your mount points and filesystems.

Do I throw in a windows boot floppy (I've got one) and type "fdisk -l" at the command prompt?

I know how to get those files once in linux, but I don't know how to get them with what I've got at the moment.

---

### Post by mingus on 2005-06-25
Rather than having you try to get in with the installation CD or a live CD, how do you feel about reinstalling?  That may be the easiest - especially because one possible source of the grub problem may be in the partitioning setup vis-a-vis the HDD and the BIOS.

I've always used "expert" mode, which is very granular.  I'm not sure, but I think you can use the standard mode and when you get to the step for partitioning and installing the boot loader, you can take manual control.  The partitioner is not very intuitive, but once you get the feel of it, works well; essentially you highlight a line, hit enter to go to a submenu, highlight a line and toggle thru choices, etc.

Since you took the guided suggestions, I take it that you don't have strong feelings on the partitioning scheme.  Some users split the / directory across 3-5 partitions for administration and extra-security reasons, but that means you need to learn how to manage that.  Others separate /home because it is sorta equiv to W$ MyDocuments, and this can be easier for backups and filesystem integrity if you have a lot of user files.  And if you want a partition that shares files between W$ and Ubuntu, that can be a separate FAT32 partition.  This is all up to you.

What you do want is a separate partition for /boot.  Use 100MB, hdb1, ext2.  Make hdb2 swap, 2x your RAM.  Put the rest of the drive on hdb3 mounted as / with ext3, unless you want to separate / from /home, in which case take about 10GB for / and use the rest of the disk for /home on hdb5 (hdb4 will need to be an extended partition, with hdb5 a logical inside it).

Now when you get to the boot loader step, do not take the automatic default.  It allows you to tell it where you want the loader installed.  You want it on /dev/hdb (the "b" without a number means this drive's MBR).  Let me suggest that you repeat this step, but the second time install grub to /dev/hdb1 (the first sector of the /boot partition).  Then if we have a problem later getting grub to run from the MBR, we can alternatively tell the BIOS to use the grub installed on /boot instead.

Wanna give this a try?

PS.  fdisk in DOS is not the same program as fdisk in Unix.  *Never* mix the use of the two on the same partition; that will corrupt the table.

---

### Post by oliwally on 2005-06-25
That doesn't sound too difficult.

Just to make sure I've got it right:

I need 

boot partition - does it have a name, size  and extension or is this hdb1?
hdb1 partition - name?, 100 MB of ext2 type
hdb2 partition- swap, twice RAM, of swap type
hdb3 partition - simply " / ", rest of drive, ext3 type

I don't need home partitions etc, as you described.

All the extensions and names will probably be more obvious once I look at the options available when I'm doing it.

Now, just as  a forethought - I know how to tell BIOS to boot from a particular HD, but how do I tell it to boot from a certain partition on the HD?

Thanks again for your efforts - I feel I'm slowly getting there and learning lots on the way. I'll try all this out later today, so I won't post for about 12 hours.

---

### Post by mingus on 2005-06-25
[QUOTE=oliwally]
boot partition - does it have a name, size  and extension or is this hdb1?
hdb1 partition - name?, 100 MB of ext2 type
hdb2 partition- swap, twice RAM, of swap type
hdb3 partition - simply " / ", rest of drive, ext3 type

Now, just as  a forethought - I know how to tell BIOS to boot from a particular HD, but how do I tell it to boot from a certain partition on the HD?
[/QUOTE]

the hdb1 partition should be mounted as /boot, take 100MB and format as ext2

re 2nd question - The HDD has a reserved sector 0 for the MBR, the default.  Each partition also has a reserved first sector.  If you install the loader to partition where /boot is located, and you set the bootable flag on that partition, the BIOS will go to the first sector on that partition rather than the MBR.  E.g., on one of my systems I have XP and SuSE on the same drive.  W$ is MBR hostile, so I leave the MBR alone.  Grub is installed in SuSE's /boot and that partition is flagged for boot.  The BIOS boots from the SuSE partition, bypassing the MBR, and then I chain-load back to XP.

---

### Post by oliwally on 2005-06-26
So, is a particular partition 'flagged' as boot simply by calling it /boot? If not, then how do I flag a partition to be bootable?

---

### Post by oliwally on 2005-06-26
> So, is a particular partition 'flagged' as boot simply by calling it /boot? If not, then how do I flag a partition to be bootable?
Never mind - I found the option to flag while creating the partitions.

I have done as you said (as above) to partition hdb. All not too difficult.

I installed grub on hdb1. I set Bios to boot from hdb (hd1 in bios) and let the computer boot up - no cigar !

The following message came up:

Grub loading stage 1.5
Grub loading please wait.....
Error 15

Error 15 is 'file not found' from what I could find out on the net.

---

### Post by mohaham on 2005-06-26
looks like the disks get swapped when you change the bios options..
can u try this..

Booting 'Ubuntu' Kernel 2.6.10-5-386
root (hd0,0)
kernel /boot/vmlinuz - 2.6.10-5-386 root = /dev/hda1 ro quiet splash


and for Xp...

change this to root (hd1,0)

---

### Post by oliwally on 2005-06-26
hi there mohaham -  thanks for helping out

I tried your suggestion. It didn't work either. Here's the output:

uncompressing linux...Ok. booting the kernel.
audit (11119825457.190:0); initialized
starting ubuntu
VFS: Can't find ext3 filesystem on dev hda1
modprobe : FATAL: Could not open /liv/modules/2.6.0-5-386/kernel/fs/nls/nls_cp4
37. ko' : no such file or directory
pivot_root : no such file or directory
/sbin/init:428. Cannot open dev/console ; no such file 
Kernel panic - not syncing: Attempt to kill init!

---

### Post by mingus on 2005-06-26
[QUOTE=oliwally]I installed grub on hdb1. I set Bios to boot from hdb (hd1 in bios) and let the computer boot up - no cigar !

The following message came up:

Grub loading stage 1.5
Grub loading please wait.....
Error 15

Error 15 is 'file not found' from what I could find out on the net.[/QUOTE]

The errors you got the first time and then after you reinstalled are entirely different.  With the former, grub could not find where it was being pointed to for boot.  In the latter, the loader program (stage2) itself was not found.  I suggest  concentrating first on getting the loader to run, and then dealing with the pointers issue, which is what mohoham was addressing - and btw, how/where did you make the changes he suggested?  This change is not in your menu.lst file now, is it????

There are a half-dozen ways to do this.  My pref is to use the install CD to get in and then create a floppy which should (a) boot the system and (b) provide a grub shell in which commands can be entered interactively and tested for validity.  This is more granular than other methods, so just go slow and be precise.  It's advantage is that every step is controlled and if there is a problem, feedback.

* boot from install CD doing :rescue at the prompt
* go thru the screens, you will get to one which asks you to specify which partition the root (/) is on.  Yours is /dev/hdb3.
* you will be dropped in to a shell
* do a ctrl-alt-F2 to move into a console - your / partition has already been mounted under the /target directory
* temporarily change the root directory from / to /target with this command:
#chroot /target
and now do the following . . .
because you have /boot on a separate partition, you first need to mount that . . .
#mount /dev/hdb1 /boot
now insert a clean floppy and create a filesystem on it
# mke2fs /dev/fd0
now mount the floppy, create directories, copy grub and boot files . . .
#mount /dev/fd0 /media/floppy
#mkdir /media/floppy/boot
#mkdir /media/floppy/boot/grub
#cd /boot/grub
#cp stage1 stage2 menu.lst device.map /media/floppy/boot/grub
now enter the grub utility and install the loader in the floppy's boot sector
#grub
>device (fd0) /dev/fd0
>root (fd0)
>setup (fd0)
>quit
now reboot the system, making sure that the BIOS is set to boot from floppy
#reboot

when you see "grub stage 2 . . . " press ESC to see the menu (otherwise it will quickly run the default).  First try booting into Ubuntu.  Then reboot using the floppy, and try to Windows menu selection.

Let us know what happens.

---

### Post by oliwally on 2005-06-26
> the pointers issue, which is what mohoham was addressing - and btw, how/where did you make the changes he suggested? 
To do this I reinstalled Ubuntu using the automated process. So I was back to getting the Grub menu. I then chose to edit the commands to reflect what mohaham suggested. I realized that this was going back a step from what you (mingus) instructed, but it was worth a go - it seemed simple and logical. 

> This change is not in your menu.lst file now, is it????
No, I have now installed again using the manual partition setup we talked about earlier, so I'm back to where we left off before mohaham made suggestions (which are very much appreciated !).

Ok, I'll give your latest advice a go and post back. 

Hey, thanks again for sticking with me.....I'd never ever get linux going if it wasn't for forum help.

---

### Post by mingus on 2005-06-26
note that an alternative to my post above is to just reinstall (again!) and then at the boot loader step choose /dev/fd0 . . . the main reason I do it this way is I want to explicitly control the grub install, rather than depending on the grub-install script, esp when there have been problems.

Hang in, you are close.  It's well worth the extra effort.

---

### Post by oliwally on 2005-06-26
Dude ! I'm in !  :) Writing to you from within Kubuntu

I'm only half sure of what it is you got me to do - kind of lost me at the 
#grub
 >device (fd0) /dev/fd0
 >root (fd0)
 >setup (fd0)
step (what do the brackets mean?)
The rest of the stuff i sort-of understood - thanks for the detailed instructions. Simply magic !

Only prob I had that the 'reboot' command didn't work. Tried 'shutdown' but to no avail. Ended up resetting the computer - I'm sure that's not entirely healthy option.

> note that an alternative to my post above is to just reinstall (again!) and then at the boot loader step choose /dev/fd0 . . . the main reason I do it this way is I want to explicitly control the grub install, rather than depending on the grub-install script, esp when there have been problems.
I totally agree. I DON'T want grub back on the windows mbr - that's where all my fear and troubles started !

I guess the next step is to convince the computer that it doesn't have to boot into grub / ubuntu from the floppy, but instead make it automatic, booting from the ubuntu drive. How do we do that ?

---

### Post by mingus on 2005-06-26
Fantastic!

Gonna have to wait till tomorrow to post back next steps, really late here and I've got an early call.  In short, we now need to get grub installed to the 2nd HDD.  That is going to be a lot easier now that you're in Kubuntu and you have that floppy as an interim/backup solution.

The grub commands:  device says where to install stage1, root says where to find the boot files now to install and later when boot, setup actually does the installation.  The brackets are just std grub device syntax.

The #reboot glitch is my fault.  I forgot to have you chroot back to / and umount the two partitions.

What happened when you tried to boot Windows from the grub menu?  (If you didn't see the grub menu, it's because the timeout is too fast - pressing ESC when you see "Grub stage2 . . . " will pause you at the menu.)

---

### Post by oliwally on 2005-06-27
> What happened when you tried to boot Windows from the grub menu?
All is good so far. I can boot into windows and all.

Looking forward to getting the changes done permanetly.

---

### Post by mingus on 2005-06-27
First, an important detail:  There is one distinct diff between how grub works on your bootable floppy vs hard disk.  The floppy holds (because it's big enough) stage1, stage2, and menu.lst - it is self-contained and so as long as the pointers in menu.lst are correct, it works.  This is also why it is not affected by whatever the BIOS boot sequence is for the HDD's.

When you install to the HDD, the grub pgms are in diff locns pointing one to the next.  There are a nbr of variables.  So installing to HDD can be a bit tricky.

But as long as you have that floppy, and you don't touch hda, you are safe.  Try it this way first:

* set your BIOS to boot from the 2nd drive and reboot with floppy into Ubuntu
* open the root terminal and do:
#grub
grub> device (hd1) /dev/hdb
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

* remove the floppy, cross your fingers, and reboot . . .

if it works, I'll take a pint of Foster's if you pls . . . if not, boot from floppy and post back error

---

### Post by oliwally on 2005-06-27
Unfortunately the Fosters will have to wait just a little.

> grub> device (hd1) /dev/hdb
returned: 'file not found' 

Why is it not possible to just copy the contents of the floppy into hdb1? Why would this not work? But if the explanation for this is too technical or would take you too long to write - just give a 'it just doesn't work that way'. I'll be happy with that.

---

### Post by mingus on 2005-06-28
*returned: 'file not found' *

would you pls try that again making sure you are running as *root*.  You will get this error as a regular user because without root permission you cannot "find" hdb.

*Why is it not possible to just copy the contents of the floppy into hdb1?*

Nope.  The answer lies in my prev posts.  Installation puts them where they need to be, which simple copying cannot do.  And when the files are installed, they are modified with unique pointers to work together.  Stage1 on that floppy will be physically diff than stage1 in the hdb1 boot sector.

---

### Post by oliwally on 2005-06-28
aha !

This time I've used the sudo command and my user password to get in (sudo grub).

Still, some abnormalities:

At the line 

```
grub> root (hd1,0)
```

there was this return:

```
Filesystem type is ext2fs, partition type 0x83
```

I rebooted to ubuntu drive (without floppy), and Bingo.....straight into the Grub menu. Half a Fosters coming your way.

However, when selecting to boot Ubuntu, the following was returned:
```

Booting ubuntu.... yadda, yadda
root (hd1,0)
Filesystem type unknown, partition type 0x7
Kernel /vmlinuz -2.6.10-5-386 root: /dev/hdb3 ro quiet splash
Error 17: Cannot mount selected partition
Press any key to continue.....
```

I also tried booting in to WinXP - similar message flashes up for about half a second, then I'm returned to the Grub menu.

---

### Post by mingus on 2005-06-28
[I]Still, some abnormalities:

At the line 

```
grub> root (hd1,0)
```

there was this return:

```
Filesystem type is ext2fs, partition type 0x83
```[/I]

Nope, that is what it's supposed to do.  It's just telling you what it found on hd1,0.  Did the same when you created the floppy.

Pls repeat the procedure the whole way.

---

### Post by oliwally on 2005-06-28
No, still not woring. I've done the 
```
grub> device (hd1) /dev/hdb
grub> root (hd1,0)
grub> setup (hd1)
grub> quit

```
two more times and then rebooted without floppy. Same result as before.

I received the following return during the setup stage - don't know if that helps:
```

grub> setup (hd1)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd1)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd1) (hd1)1+16 p (hd1,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.

```

---

### Post by mingus on 2005-06-28
drats!

The strength of grub is its flexibility, but that is also its weakness - you have to use *exactly* the syntax grub wants for it to work right - and its not at all intuitive.

So let me suggest this:  Post back here the files menu.lst and device.map.  I will put together several different install stanzas.  Hopefully one will work; that way we won't have to keep looping this around one step a day.  OK?  Give me a day or two to put that together.

---

### Post by oliwally on 2005-06-29
Sounds great. Once again - thanks for all the time you're taking to help me out. 

Ok, here's the menu.lst and the device.map.

The menu.lst:

```
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.           
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hdb3 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro quiet splash
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd1,0)
kernel		/vmlinuz-2.6.10-5-386 root=/dev/hdb3 ro single
initrd		/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd1,0)
kernel		/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
chainloader	+1
```


And the device.map:

```
(hd0)	/dev/hda
(hd1)	/dev/hdb

```

---

### Post by mingus on 2005-06-30
I think this may do the trick . . .

Figured it would be easier to just modify your menu.lst and device.map files, so they are attached to this post with a .txt extension.  Save them to your home directory.  

Now get in a terminal and do:
$su
#cd /boot/grub
#mv menu.lst menu.lst.old
#mv device.map device.map.old
#cp /home/<user>/menu.lst.txt menu.lst
#cp /home/<user>/device.map.txt device.map
#ls
and you see the new devicemap and menu.lst files

now do:
#grub
grub> device (hd0) /dev/hdb
grub> root (hd0,0)
grub> setup (hd0)
grub> quit

after the root command you'll get a msg re the filesystem it found; that's OK.  after setup you should see several lines about stage1, stage1.5, stage2, etc. - all should be "yes".

now reboot.  I tested this on one of my boxes set up with your disk config, and it worked.  If the chain-load to Windows hiccups, then open menu.lst with a text editor, find the Windows stanza, and change "root (1,0)" to "rootnoverify (1,0)".

---

### Post by oliwally on 2005-06-30
Mingus, you're a total legend !

Bonza rip-snortin'-beauty, she's a ripper mate !  It all works perfectly !

So, where do I send that bolltle of Foster's ? 

One thing I noticed was that the output of grub> setup (hd0) did not have all lines as "yes". I'm assuming it doesn't matter ?

Here's the output:

```
grub> device (hd0) /dev/hdb

grub> root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83

grub> setup (hd0)
 Checking if "/boot/grub/stage1" exists... no
 Checking if "/grub/stage1" exists... yes
 Checking if "/grub/stage2" exists... yes
 Checking if "/grub/e2fs_stage1_5" exists... yes
 Running "embed /grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /grub/stage1 (hd0) (hd0)1+16 p (hd0,0)/grub/stage2 /grub/menu
.lst"... succeeded
Done.
```

Many, many thanks to you. I wish I could return the favour in some small way. I totally admire your knowledge about linux and know for certain that I will have to rely on people like you to help me out. I don't think there is a realistic chance that I will ever attain such detailed knowledge (not without the family suffering from dad-depravation !) You have demonstrated true Ubuntu spirit:
> "A person with ubuntu is open and available to others, affirming of others, does not feel threatened that others are able and good, for he or she has a proper self-assurance that comes from knowing that he or she belongs in a greater whole and is diminished when others are humiliated or diminished, when others are tortured or oppressed." -- Archbishop Desmond Tutu.Not that I was actually tortured or oppressed - except by the desire to get the distro working on my 'puter.

Well, it's been a total pleasure. I'm sure I'll bump into you again on the Ubuntu forums as the next problem arises. Btw - love the cat avatar. We used to have one just like him, and yup, he looked exactly like that when he was washed. So we washed him a lot - just for the laugh !

---

### Post by mingus on 2005-06-30
Thanks again for the very kind words.  It will prob be some time before I get back to Australia (yep, been there nbr of times; in my wild SE Asia days used to hang w/Aussie buds).  So save that Foster's . . .

This Ubuntu thing is real, although it will take another yr or two to see whether Linux on the desktop is sustainable.  In the next few months I plan to deliver several hundred Ubuntu systems to disadvantaged families; if this program flies, it will be thousands.

*I wish I could return the favour in some small way.*

You already have.  It's a pleasure to be of some assistance to folks who are cooperative and appreciative.      

*I don't think there is a realistic chance that I will ever attain such detailed knowledge*

To be fair, I've had a bit of a head start:  Been a systems engineer for 25 yrs.  You will do just fine.

Take care!

---

### Post by oliwally on 2005-07-01
No, I don't think I can catch up on 25 years of experience.

*This Ubuntu thing is real, although it will take another yr or two to see whether Linux on the desktop is sustainable. In the next few months I plan to deliver several hundred Ubuntu systems to disadvantaged families; if this program flies, it will be thousands.*

Yes, I've tried a few linux distros now, and none have been as easy as Ubuntu. For me, it's definately a possible substitute for WinXP. I suppose once they work our installation tricks like you've shown me (ie when you don't have to use the command line any longer and it's all gui driven and easy) if will take off at lightning speed.

Well, until next time. God bless you cobber. Enjoy Oz when you venture over here again. Got some friends at present doing the US thing - they're loving it. One day it'll be my turn !

'til then ...

---

