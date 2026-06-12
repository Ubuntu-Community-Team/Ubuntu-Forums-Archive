---
title: "Installing GRUB"
date: 2005-07-18
forum: Installation &amp; Upgrades
---

### Post by Irony on 2005-07-18
After I changed a drive name in XP my GRUB bootloader gave me an Error 17 message. I therefore used the XP installation disc to enter recovery mode and fixmbr to restore the windows installer.

The windows installer doesn't detect ubuntu so only boots into windows.

Can I install GRUB without having to re-install ubuntu.

I've followed the instructions at [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) and eventually got to a choice of mounting points;

[PHP]dev/disc/disc0/part1
dev/disc/disc0/part2[/PHP]

etc, and found that only

[PHP]dev/disc/disc0/part6[/PHP]

would do anything.

I then typed;

[PHP]# grub-install /dev/hda[/PHP]

but it gave an error.

My question is, is this the correct way to install GRUB. Or do I have to install ubuntu again.

---

### Post by ketiko on 2005-07-19
[QUOTE=Irony]After I changed a drive name in XP my GRUB bootloader gave me an Error 17 message. I therefore used the XP installation disc to enter recovery mode and fixmbr to restore the windows installer.

The windows installer doesn't detect ubuntu so only boots into windows.

Can I install GRUB without having to re-install ubuntu.

I've followed the instructions at [http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation](http://ubuntuguide.org/#restoregrubmenuafterwindowsinstallation) and eventually got to a choice of mounting points;

dev/disc/disc0/part1
dev/disc/disc0/part2

etc, and found that only

dev/disc/disc0/part6

would do anything.

I then typed;

# grub-install /dev/hda

but it gave an error.

My question is, is this the correct way to install GRUB. Or do I have to install ubuntu again.[/QUOTE]
 You don't need to install Ubuntu again.  I resized my partitions and got Error 17 in grub as well.  I did this and it worked.

[How to Install Grub](http://forums.fedoraforum.org/showthread.php?t=975)

---

### Post by Irony on 2005-07-19
Thanks for reply ketiko. How did you use Fedora instructions to fix ubuntu. I've got the ubuntu CDs.

I've also tried;

[PHP]Once you have chosen your keyboard and all the hard drive and cdrom drivers hae been loaded hit CTRL-ALT-F2 and then

mount /dev/hda5 /mnt

ls /mnt
(to see if you have it right)

chroot /mnt
grub-install /dev/hda

reboot[/PHP]

but this simply says command not recognised, or something to that effect.

I've looked at a lot of the forum answers regarding installing grub over windows boot loaders but it seems that this is a deficiency in ubuntu, e.g. the rescue mode doesn't work and the other answers require quite a degree of linux knowledge to make work (which I don't have yet).

Re-installing ubuntu on my system would probably be easiest as it quite fast on my system, however I want to be able to resolve the issue just in case it happens again because then I might have a lot of stuff on ubuntu which I can't access (there's not much at the moment).

---

### Post by mingus on 2005-07-19
Umm . . . actually, rescue mode does work.  But it does require the same level of knowledge as XP's recovery mode . . . 

Can you clarify your post where you said:

[I]dev/disc/disc0/part1
dev/disc/disc0/part2

etc, and found that only

dev/disc/disc0/part6

would do anything.[/I]

and then you tried again, but mounted hda5???

It sounds like both times you did not mount the root (/) partition.   

We need to know what your disk partitions are.  The command:
#fdisk -l
will give this info.  Rescue mode requires knowing the root partition.  Do you have a Live-CD by chance, either Ubuntu or Knoppix or SimplyMEPIS or . . .?

---

### Post by Irony on 2005-07-19
Hi Mingus, I have the LiveCD (this proved useful with my laptop when resolving the installed ubuntu screen resolution).

I take it you mean to boot up with the LiveCD and then open a terminal and type;

*#fdisk -l*

Where it said;

[I]dev/disc/disc0/part1
dev/disc/disc0/part2
etc,[/I]

in rescue mode, I tried dev/disc/disc0/part1 first but each time a red screen came up and continue only brought me back to;

[I]dev/disc/disc0/part1
dev/disc/disc0/part2
etc,[/I]

Here's a picture of my partitions as viewed from windows;

[http://ironclub.net/log/partitions.png](http://ironclub.net/log/partitions.png)

XP is installed in the 56.98 GB drive whilst ubuntu is installed in the 52.23 GB partition

---

### Post by Irony on 2005-07-19
I've just replicated the conditions on my old laptop and got it to work to install GRUB on the laptop!

Basically I booted from the install ubuntu CD and at the prompt typed;

*boot: rescue*

Then I got to a section where it said mount points;

[I]dev/disc/disc0/part1 
dev/disc/disc0/part2
dev/disc/disc0/part3 
dev/disc/disc0/part5[/I]

I tried *dev/disc/disc0/part1* first but it got to a red screen, so I tried *dev/disc/disc0/part2* and got to a *sh-3.00#* prompt. My laptop has 2 main partitions one for XP and one for ubuntu.

So I typed;

*grub-install /dev/hda * 

This then said device contents in;

*map/boot/grub/device.map*

in;

*(hd0) /dev/hda*

It then came up with *sh-3.00#* again. I didn't know what to do at this point so ejected the CD with a pin and pushed Ctrl+Alt+Del which switched it off and rebooted. It kept accessing the CD drive at first so I restarted it again by pushing the on button and GRUB booted up fine and showed ubuntu and XP.

I have 3 questions when it comes to doing the same on the big Desktop machine;

How do I know whether to mount dev/disc/disc0/part1, 2, etc; how do I exit properly at the sh-3.00# prompt; when do I eject the install ubuntu disc?

---

### Post by mingus on 2005-07-19
You are close . . .

According to the XP screen, Ubuntu is on the 3rd partition.  Assuming the partitions were created sequentially from front-to-end of the drive, that would be /dev/hda3 (partitions are numbered as they are created, and hence it is possible to have numbering that is different from the physical position on the disk).

You got the red screen because partition 1 is NTFS, and the Ubuntu CD knew this could not have the root partition.

So on your desktop system you should be able to boot :rescue like you did on the laptop.  Mount partition 3.  You should then be able to do #grub-install /dev/hda.

After being returned to the prompt, do:
#umount /dev/hda3
#reboot
or Ctrl-Alt-Delete will also probably reboot.  At this point, how you open the CD drive depends on the machine.  Usually if you hit the open button on the drive as the system has just begun to boot (when you see the BIOS name, CPU, and RAM), it will open.  If you can't seem to get it open naturally, enter the BIOS setup and change the boot sequence to bypass the CD, boot normally, login, and eject the CD.  Try not to use the pin or hard-reset.

---

### Post by Irony on 2005-07-20
Hey that's great, I'll give it a go.

I did create the partitions sequentially.

I'll report back later. Thanks!

---

### Post by Irony on 2005-07-20
Nope, didn't work  [-X . Same result as in my very first post. In other words the rescue option worked on the laptop but not (as yet) my big desktop machine.

This is what happened;

*boot: rescue*

Then I got to a section where it said mount points;

[I]dev/disc/disc0/part1 
dev/disc/disc0/part2
dev/disc/disc0/part5 
dev/disc/disc0/part6
dev/disc/disc1/part7[/I]

I tried dev/disc/disc0/part1 first but it got to a red screen, the same with 2 and 5, I got to part6 and got to a sh-3.00# prompt, so I typed;

*grub-install /dev/hda*

But got the message;

*The file /boot/grub/stage1 not read correctly*

So I went;

*umount dev/hda6*

It said;

*not mounted*

So I typed;

*reboot*

And XP booted up as normal. Note I didn't try the dev/disc/disc1/part7 option.

---

### Post by mingus on 2005-07-20
The error messages you got suggest that the grub master program was not found because the root partition was not mounted.  The list:

dev/disc/disc0/part1
dev/disc/disc0/part2
dev/disc/disc0/part5
dev/disc/disc0/part6
dev/disc/disc1/part7

is strange because of the last line showing "disc1"; that's not a typo, is it???  

If what you meant was disc0, then your table is: 
#1 XPa
#2 Extended
#5 XPb
#6 Ubuntu
#7 Ubb
and hence partition 6 was correct, and should have been mounted.

Try booting rescue again, choosing partition 6 again.  When you drop in the shell, do:
#cd /home
#ls
if you see your user name, then you've mounted the root.  If so, then do:
#ls /sbin/grub
and it should display back:
/sbin/grub
so now that you've verified that your root is mounted and the grub master program is there, again try:
#grub-install /dev/hda

if you get an error again - or you find that partition 6 was not mounted - then there is something we are missing.  Do #reboot and boot back in with the live-CD.  Open a terminal and do:
$sudo fdisk -l
and post back the result here.  Once we've confirmed the partition layout, I'll reply back with 2 different sets of instructions for reinstalling grub - one will surely work.

Again, sorry about the hda3 mistake - I missed the green border in the XP screen cap, which indicates an extended partition.

---

### Post by Irony on 2005-07-21
First off, I'd just like to say thanks for all the help mingus.

[I]dev/disc/disc0/part1
dev/disc/disc0/part2
dev/disc/disc0/part5
dev/disc/disc0/part6
dev/disc/disc1/part7[/I]

These are correct, i.e. where it says *disc1* it is *disc1* not *disc0*. I just assumed that *disc1* meant my smaller physical 2nd hard drive.

However I've been into the LiveCD and got the following;

[PHP]sudo fdisk -l

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7438    59745703+   7  HPFS/NTFS
/dev/hda2            7439       24791   139387972+   f  W95 Ext'd (LBA)
/dev/hda5            7439       13016    44805253+   7  HPFS/NTFS
/dev/hda6           13017       19834    54765553+  83  Linux
/dev/hda7           19835       24791    39817071    7  HPFS/NTFS

Disk /dev/hdb: 11.5 GB, 11525455872 bytes
255 heads, 63 sectors/track, 1401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdb1               1        1401    11253501    c  W95 FAT32 (LBA)[/PHP]

Is this any help?

---

### Post by mingus on 2005-07-21
[I]dev/disc/disc0/part1
dev/disc/disc0/part2
dev/disc/disc0/part5
dev/disc/disc0/part6
dev/disc/disc1/part7

These are correct, i.e. where it says disc1 it is disc1 not disc0. I just assumed that disc1 meant my smaller physical 2nd hard drive.[/I]

That was a fair, and as far as I can see, accurate assumption.  It is confirmed by your fdisk report and agrees with the XP partition screen.  Let's hope this is a trivial bug in the installer and not indicative of a larger partition table glitch.

Did you try the instructions from my last post using :rescue mode?  What happened?

Try this method after booting with the Live-CD and opening a terminal:
$ls
(you should see nothing except "Desktop")
$df
(you should not see any of the HDD partitions mounted)
$sudo mkdir /drive
$sudo mount /dev/hda6 /drive
$sudo chroot /drive
#df
(you should now see hda6 mounted as /)
#ls /home
(you should see your username - this confirms you have mounted *your* partition)
#cd /sbin
#ls g*
(you should see "grub" the installation program)
#cd /
#grub-install /dev/hda
(look for the line "Installation finished. No error reported."  Now, if your system can boot from floppy, insert a clean formatted diskette and do)
#grub-install /dev/fd0
(again, a message indicating no errors)
#umount /dev/hda6
close the terminal and reboot.  First reboot from the floppy.  That should work.  Then pull the floppy and reboot from the hard disk.  Keep your fingers crossed.

---

### Post by Irony on 2005-07-21
Thanks mingus. I'm going to try both methods.

With the floppy method should I set the BIOS to first boot with floppy?

---

### Post by mingus on 2005-07-21
[QUOTE=Irony]
With the floppy method should I set the BIOS to first boot with floppy?[/QUOTE]

Sure.  It is actually harmless to leave it this way, the only effect being an extra couple of seconds in the boot process.  When the BIOS sees there is no bootable media in the floppy drive, it simply goes to the next device setup in the boot sequence list.

---

### Post by Irony on 2005-07-21
Well I've reset it so I've got floppy first, dvd drive second and hard disk last in the boot sequence. Not quite sure why I didn't have it like that in the first place - probably trying to get an even faster boot-up!

Anyway here is what I've done.... unfortunately still without success ](*,) ;

First I followed the instruction;

[PHP]Try booting rescue again, choosing partition 6 again. When you drop in the shell, do:
#cd /home
#ls
if you see your user name, then you've mounted the root. If so, then do:
#ls /sbin/grub
and it should display back:
/sbin/grub
so now that you've verified that your root is mounted and the grub master program is there, again try:
#grub-install /dev/hda[/PHP]

But at *cd /home* it said *no such file or directory*.

I then typed *ls* which then gave *bin cdrom etc initrid lib* (I wrote down everything if it is important) and so on.

So I then tried the floppy instructions but got this;

[PHP]ubuntu@ubuntu:~$ ls
Desktop
ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/mapper/casper-snapshot
                       2062739   1307206    650727  67% /
tmpfs                   453328         4    453324   1% /dev/shm
tmpfs                   453328        12    453316   1% /tmp
/dev                   2062739   1307206    650727  67% /.dev
none                      5120      2896      2224  57% /dev
ubuntu@ubuntu:~$ sudo mkdir /drive
ubuntu@ubuntu:~$ sudo mount /dev/hda6 /drive
ubuntu@ubuntu:~$ sudo chroot /drive
root@ubuntu:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7             53905884   1649824  49517784   4% /
proc                  53905884   1649824  49517784   4% /proc
sysfs                 53905884   1649824  49517784   4% /sys
devpts                53905884   1649824  49517784   4% /dev/pts
none                  53905884   1649824  49517784   4% /dev
df: `/proc/bus/usb': No such file or directory
root@ubuntu:/# ls /home
irony
root@ubuntu:/# cd /sbin
root@ubuntu:/sbin# ls g*
getty    grub         grub-install    grub-reboot
grepmap  grub-floppy  grub-md5-crypt  grub-terminfo
root@ubuntu:/sbin# cd /
root@ubuntu:/# grub-install /dev/hda
The file /boot/grub/stage1 not read correctly.
root@ubuntu:/# grub-install /dev/fd0
/dev/fd0 does not have any corresponding BIOS drive.
root@ubuntu:/#[/PHP]

It seems it recognises my irony username but won't install grub. Also I don't know what the floppy BIOS message means.

Actually it occurs to me that the floppy doesn't work in the LiveCD anyway. My USB Zip Drive does. Could I transfer the GRUB program to it then in Windows copy it to the floppy?

If its hopeless, I could just delete all the partitions using XP device manager and set them up again and install ubuntu. However I'd prefer to see if I can fix it and I also just want to learn how linux works.

---

### Post by mingus on 2005-07-21
Well, you've certainly been patient, but I gotta say it doesn't look good.

I could give you commands to resolve the grub floppy error returned, but I doubt it will make a difference.  You will get then get the same error immidiately preceding.  

Let's recap.  Take a close look at the following:

[I]ubuntu@ubuntu:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
                      2062739   1307206    650727  67% /

ubuntu@ubuntu:~$ sudo mkdir /drive
ubuntu@ubuntu:~$ sudo mount /dev/hda6 /drive
ubuntu@ubuntu:~$ sudo chroot /drive
root@ubuntu:/# df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda7             53905884   1649824  49517784   4% /[/I]

The Live-CD does not mount the drive, it creates a temporary filesystem in memory.  Hence the first df showed nothing mounted as /.  Then you mounted hda6.  Now look at what is shown mounted as / - it is hda7, not hda6.  Not possible.  Now look at:

[I]dev/disc/disc0/part1
dev/disc/disc0/part2
dev/disc/disc0/part5
dev/disc/disc0/part6
dev/disc/disc1/part7[/I]

You verified "disk1".  If this is what the table is actually reporting, I replied:
*Let's hope this is not indicative of a larger partition table glitch.*

There is a table problem.  This whole journey began when:
*"After I changed a drive name in XP . . ."*
Here is more than you probably ever wanted to know:  You changed a drive label, and that seemed to break the grub boot code in the MBR.  But the code is in the first 466 bytes of the 512 MBR and should not have been touched by changing the label.  The next 44 bytes is where the table is.  The last 2 bytes is the "disk signature" which XP uniquely uses as an index cross-referenced to entries in the Registry - and that is where XP stores the its label (no one else does this).  I good theory would be that when the label was changed the table was over-written.  Grub ran, so the code was still OK, and it found its partition in the table  but as Error 17 indicates - it was not the partition it was supposed to be:  It was an NTFS partition.  The table had been changed, not just a label.  Which is exactly what you are seeing now above, with hda6 being confused with hda7, and hda7 reported as being on the other disk.  

I appreciate this is a real pisser:  Write a letter to Gates.

Now there are partition editors and a MS tool that enables you to modify these tables (everything in hex btw), but you don't wanna go there.

You could try to just reinstall Ubuntu, which would rewrite the table entry for hda6.  Given that XP will ignore that partition, this might work.  But be very sure you have a good backup of the other partitions first.

If all that resides on D and F is data, no programs, then the cleanest solution is to backup that data, delete the entire extended partition, create 2 new primaries and restore D and F to those, create a new extended with 2 new logicals, 1 for Ubuntu and the other for swap.

Feel free to get a second opinion.

Oh, and btw, where is your swap partition????

---

### Post by Irony on 2005-07-22
I think one of the problems is that ubuntu isn't installed into a primary partition. When I set up the partitions I just did it by installing XP and using that to create the partitions. It set up the partitions as extended and logical as per [http://www.ironclub.net/log/partitions.png](http://www.ironclub.net/log/partitions.png) . At the time I didn't realise that I could have set up a partition with the ubuntu disc which has a manual editing bit that can shrink partitions thus leaving free space. 

Originally when I had ubuntu installed onto my 2nd hard drive it showed a primary and extended logical partition (presumably for the swap). Whereas now you can see that ubuntu is installed into a logical drive.

I've been reading a bit on partitions and it says that a max of 4 primary partitions can be created on one disc. I don't actually know if this can be done from Windows Device Manager. If not how do I create a primary partition or will it be created by the ubuntu install if I just delete a partition from Windows Device Manager first so that it is unallocated. That is what happened on my old laptop it created another primary partition and added a logical partition (presumably this is the swap partition).

Anyway I've had quite a bit of practice installing ubuntu in several ways and it looks like I'm going to get more practice.

---

### Post by Irony on 2005-07-22
Well I've reinstalled and it looks like this;

[http://www.ironclub.net/log/part2.png](http://www.ironclub.net/log/part2.png)

Is ubuntu supposed to be 2 logicals, on my laptop ubuntu XP and ubuntu are primaries, whilst the swap is a logical.

---

### Post by mingus on 2005-07-22
> **Irony]Well I've reinstalled and it looks like this said:**
> http://www.ironclub.net/log/part2.png[/url]

Is ubuntu supposed to be 2 logicals, on my laptop ubuntu XP and ubuntu are primaries, whilst the swap is a logical.

I'm a bit brain fried at the moment . . . hmm. . . . I have a 5 diff Linux distros on logicals in the same extended, but they are all being chain-loaded from another distro on a primary. 

With Windows the boot sector must definitely be on a primary.  But sorry, I just don't remember right now if Linux has the same constraint . . . what I can say is that if Linux does, you still have at least two other fairly easy options . . .

You can install grub to the boot sector of your Ubuntu partition, which from the diagram looks like it should be hda5.  Find the Windows dual-boot HowTo in the wiki for details:  Just make a copy of the Ubuntu boot sector to a DOS formatted floppy.  Get into W$, copy that file to C:, and then add a line to the end of C:\boot.ini.  This will chain load Ubuntu from Windows ntldr.  This method is very reliable.

Your other option - which I don't remember the exact detail of how, but you would find it quickly googling - is to delete the Ubuntu and swap partitions, and replace that extended with a 4th primary.  Reinstall Ubuntu on that primary.  Then you create a swap **file** on the Ubuntu partition.  Linux doesn't really care if swap is a file or a partition, it just wants a block of reserved space.  W$ just uses a file (pagefile.sys).  A partition is used with Linux mostly because it's just easier.  The only gotcha with doing this is if during the Ubuntu installation you needed swap space due to a RAM limitation, but that doesn't appear to be an issue for you.  (Of course, you may be spittin' bullets at me now for not having in my last post mentioned this in lieu of creating the swap partition  :-# )

---

### Post by Irony on 2005-07-23
Thanks mingus. I'm saving this thread for future reference. I'm gonna play around with ubuntu now and familiarise myself with it. This is the first linux distro I've ever used and I like how fast it is to install (only about 20 mins, versus an hour for XP) and the way it immediately detects my network connection, I don't have to pay a licence fee, its got openoffice, gimp, blender, a LiveCD...

---

