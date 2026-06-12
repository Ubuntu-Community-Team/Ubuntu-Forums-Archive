---
title: "Windows 7 now will not boot and Ubuntu failed"
date: 2013-09-19
forum: Installation &amp; Upgrades
---

### Post by ddubbz1979 on 2013-09-19
Some of you may have notice my other thread about have trouble with getting Ubuntu installed over the last 4 days due to EFI and manual partitioning confusion.  On the advice of a member, which I may not have followed correctly, I chose to partition 500 MB and set as a EFI bootloader and assign the grub to boot on that partition.  Still got the same crash as before and Ubuntu failed to install.  And now Windows 7 will not boot.  It looks like Ubuntu is no longer booting in EFI but legacy as I noticed a different screen and remember reading about the different screens between Ubuntu and EFI and Legacy modes.  My priority is to recover my Windows 7 cause it would be a disaster to lose it considering my work on it.  Then, I would like to run Ubuntu alongside.  I have backed up windows 7 on my flash but have no idea where to go.  Can someone help?  Thanks in advance.  If I sound desperate, that's because I am.  Thanks.

---

### Post by david98 on 2013-09-19
when you installed ubuntu did you click install alongside windows 7 or do something else like creating your own partition ?

---

### Post by ddubbz1979 on 2013-09-19
something else

---

### Post by david98 on 2013-09-19
if i was you i would delete ubuntu go back and reinstall it clicking install along side window's 7 should install grub 2.0. when you turn your computer on after that it will give you a choice to boot ubuntu' window's 7' or older versions of linux

---

### Post by ddubbz1979 on 2013-09-19
Error:  No boot disk has been detected or the disk has failed.

---

### Post by david98 on 2013-09-19
Try running it through a live cd then go to gparted  and check [COLOR=#444444][FONT=UbuntuRegular] the 'boot' flag is already set on sda2.[/FONT][/COLOR]

---

### Post by ddubbz1979 on 2013-09-19
> **david98 said:**
> Try running it through a live cd then go to gparted  and check [COLOR=#444444][FONT=UbuntuRegular] the 'boot' flag is already set on sda2.[/FONT][/COLOR]
i'm not familiar with gparted so may have to look that up.  how do i delete ubuntu?  the ubuntu installation crashed.  i've tried to install it for 4 days now.  i can boot from my flash drive to ubuntu installation, but that's all i got.

ok found gparted and right clicked on sda2 and checked boot.  Do i restart?

---

### Post by david98 on 2013-09-19
Boot from live flash drive then run gparted to format partition ubuntu was on once done reinstall ubuntu click on install alongside windows 7 should work no problem that's what i have done on my laptop.

---

### Post by david98 on 2013-09-19
Here's a bit info on gparted [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)

---

### Post by david98 on 2013-09-19
Yes restart installation and install alongside windows

---

### Post by ddubbz1979 on 2013-09-19
why i chose something else is because i can't get alongside to work either.  it started giving me only about 6gb to install ubuntu on and i wanted to partition for more.  the slider in the installation only showed about 12 gb on my system.  i have windows back up now.  thank you so much for that.  that's why i want linux because it just works.  but i can't get installation to work.  thanks to you and gparted for getting me back up!  i'm trying 12.04.  i noticed 13.04 gave me more gb to work with on the slider during install.  should i try that?

---

### Post by Quackers on 2013-09-19
I would try to get Windows booting again before I did anything else.
Do you have a Windows repair/installation disc for the version you were running?
If so you should boot from that and select "repair my computer" and let that run. You may need to run that repair 3 times. See what it finds.
If you don't have a disc you should download a repair disc for your Windows version and architecture (ie 32 bit/64 bit) and burn that to a cd.

---

### Post by Quackers on 2013-09-19
Lol, ignore my last post if Windows is now booting normally.
If you want to shrink your Windows partition to give more room for Ubuntu you should use Windows Disk Management - nothing else!
Once that's done you should reboot Windows at least twice before doing anything else.

---

### Post by ddubbz1979 on 2013-09-19
windows is back.  gparted helped with the previous advice.  and as i mentioned in my other post, i keep getting this message [COLOR=#000000]The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot. while trying to install ubuntu in any way, shape or form.  [/COLOR]

---

### Post by Quackers on 2013-09-19
Do you have an (U)EFI system? Do you have a GUID partition table? 
I'm not sure whether gparted is completely GPT aware and if not can cause damage.

---

### Post by ddubbz1979 on 2013-09-19
i just cleared up new partitions in windows disk management and have 75 gb free space on a partition separate from windows.

---

### Post by Quackers on 2013-09-19
Did you see post 15?

---

### Post by ddubbz1979 on 2013-09-19
> **Quackers said:**
> Do you have an (U)EFI system? Do you have a GUID partition table? 
I'm not sure whether gparted is completely GPT aware and if not can cause damage.
its working now after gparted.  i'm not sure about the lingo you mentioned but can tell you i'm running windows 7 64 bit on a 1 year old computer.  i can give you any info you may need above that.  but windows booted this time after checking boot from the right click on sda2 in gparted.  before that, it was bad news.

---

### Post by ddubbz1979 on 2013-09-19
not sure, new here, how do i find it?

---

### Post by Quackers on 2013-09-19
So you moved the boot flag to sda2 in gparted, which is your Windows partition, presumably.
Sadly I'm not familiar with UEFI Windows systems.
How many partitions show in Windows disk management window?
I believe you said earlier that you created a 500MB EFI partition? Are there now 2 of those or just 1?

---

### Post by david98 on 2013-09-19
Go back in to gparted delete any partitions you are not using. ie (leave window's alone) format free space then install linux alongside window's and it should automatically use the free space on you'r hard drive:p

---

### Post by ddubbz1979 on 2013-09-19
> **david98 said:**
> Go back in to gparted delete any partitions you are not using. ie (leave window's alone) format free space then install linux alongside window's and it should automatically use the free space on you'r hard drive:p
do i format as a ntsf?

---

### Post by ddubbz1979 on 2013-09-19
> **Quackers said:**
> So you moved the boot flag to sda2 in gparted, which is your Windows partition, presumably.
Sadly I'm not familiar with UEFI Windows systems.
How many partitions show in Windows disk management window?
I believe you said earlier that you created a 500MB EFI partition? Are there now 2 of those or just 1?

i now have a pqservice, system reserved, acer, and my new unallocated free space

---

### Post by Quackers on 2013-09-19
And Windows, presumably :-)
What format is the system reserved partition? 
And where's the 500MB EFI partition you created?

---

### Post by ddubbz1979 on 2013-09-19
> **Quackers said:**
> And Windows, presumably :-)
What format is the system reserved partition? 
And where's the 500MB EFI partition you created?

I deleted the new partitions and started over after the efi.  i can't format the disk.  the option isn't lighting up when i mouse over.  it just says free space.  extended.  acer is the windows partition.

---

### Post by Quackers on 2013-09-19
If your system is a UEFI system the Ubuntu installer should pick that up and install accordingly (it should detect an EFI partition, if there is one).
If your system is not UEFI the installer should install Ubuntu in the normal (older) way using grub-pc rather than grub_efi.

I don't know which your system uses and I, personally, would stop and check that.

If you really want to go ahead and try to install Ubuntu you can run the installer and see what happens. I would recommend first though that you make Windows recovery discs and a Windows repair disc as if Ubuntu fails to install properly it may stop Windows booting, which will need to be repaired with a repair disc.

EDIT
Is your system showing an extended partition? It would seem so, which means it's not a UEFI system.
If the free space is named as free space then it's probably still within the extended partition and not usable by Ubuntu unless you create partitions manually.
Unallocated space would probably be preferable which would be achieved by shrinking the extended partition.

---

### Post by ddubbz1979 on 2013-09-19
According to what i've seen on screenshots ubuntu is installing as uefi.  not legacy.  i already have 3 partitions and to my understanding i can't have more than 4.  getting confused on how best to approach that.  i've tried installing alongside windows 7 and multiple manual options.  i have got to missing a detail somewhere.  however, and again, after 20 hours over 4 days and trying advice from 2 forum posts this is what i get when the installer crashes.  [COLOR=#000000]The 'grub-efi-amd64-signed' package failed to install into /target/. Without the GRUB boot loader, the installed system will not boot.[/COLOR]

---

### Post by Quackers on 2013-09-20
If you have an extended partition you have a MBR partitioned drive, which has a maximum of 4 primary partitions (or 3 plus one extended partition, which can hold multiple logical partitions).
As far as I'm aware (U)EFI booting systems use a GUID partition table (ie no extended partitions) under which as many as 128 partitions can be present (in theory).

Was that grub_efi message appearing whilst your self-created 500MB EFI partition was present? That would explain it.

Ubuntu will not install in "free space", as that is usually contained within an extended partition, unless appropriate partitions are created first.
Ubuntu will install into unallocated space, which is not contained within an extended partition. This would give the option of a "side by side" installation of Ubuntu.

It sounds like your free space is inside an extended partition and that extended partition can be shrunk which will then create unallocated space which Ubuntu can use.

---

### Post by ddubbz1979 on 2013-09-20
I only noticed it was extended in gparted.  just says free space in windows disk manager.  the 500mb efi partition was another attempt at something different.  i've gotten that message and install crash every time i try it.  if i don't do anything (including pre-partitioning) and just run alongside install, it won't let me use the slider to select enough space for my liking.  only about 6gb.  i'm shooting for 60 or more. sounds like from what you're saying.  i should go back to disk manager and shrink my windows volume to get the free space.  then shrink the free space to get the unallocated?  in gparted in shows an extended with an unallocated branched in under it in the table.  ???

and thank you for all your help this far.  i would love to make this work.  not one to give up, but really don't want to damage the disk or screw up the boot on this computer either.

---

### Post by Quackers on 2013-09-20
No problem.
You don't need to shrink the Windows partition, I suspect.
I suspect that viewed in Windows Disk Management window you will see a thin (green I think) outline around your free space. That is Windows' way of saying that it's inside an extended partition. Does that coloured outline encompass another partition preceding that free space?
You can shrink that outlined part (the "free space") down to the preceding partition, if there is one.
That will then give "unallocated space" rather than "free space", which Ubuntu can then use in a "side by side" installation.

---

### Post by Quackers on 2013-09-20
Actually that won't work if you've already got 4 partitions. Sorry, that's my fault - it's 5-35am here.
We need to see your current partition layout. Can you post a screenshot of either your Windows Disk Management screen or from gparted after booting from the Ubuntu live cd/usb and choosing "try Ubuntu"

---

### Post by ddubbz1979 on 2013-09-20
I restored it to the way it was and then shrank the windows drive again and now it says unallocated and with black bar instead of free space with green bar.  
[[img]http://s21.postimg.org/xtb68vmnr/20130920_012802.jpg[/img]](http://postimage.org/)
[img](http://postimage.org/)

---

### Post by Quackers on 2013-09-20
That's better :-)
Now the Ubuntu installer should offer you an "install alongside" option.
As it's your first Ubuntu installation I would just allow Ubuntu to do the partitioning and use that alongside option. It will create a swap partition (iirc) and a root (/) partition. Separate /boot and /home partitions are not necessary as such, though in a future installation maybe a separate /home partition could be tried as is preferred by some.

Actually it's probably easier to tell it to use the unallocated space and let it do its thing.

---

### Post by Quackers on 2013-09-20
8-10am here now, so it's bedtime for me.
Good luck with your installation. I'll look in later to see how things went.

---

### Post by ddubbz1979 on 2013-09-20
Grub2 did not install again and installation crashed.  Same message and problem as before.

---

### Post by Quackers on 2013-09-20
Ouch.
Did you see Oldfred's reply to your other thread?
We need to know what's happening with your system. How it boots and in what mode.
It may be a UEFI machine but booting in bios mode. Can you enter your bios and tell us what booting options are there please and what are currently set?
Also if you could boot into the Ubuntu cd/usb and select "try Ubuntu" then when the desktop loads open a terminal and run ```
sudo fdisk -l
```and post the output here please.

---

### Post by Quackers on 2013-09-20
It may be worth having a look at these pages (if you haven't already)
[https://help.ubuntu.com/community/UEFI]("https://help.ubuntu.com/community/UEFI")
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode")

---

### Post by oldfred on 2013-09-20
Closed your other thread as duplicate.

It looks like your system is in BIOS boot mode for Windows and then has to have MBR(msdos) partitioning. 
Post the fdisk suggested by Quackers. Only with confirmation of how Windows is installed can we best suggest what to do.
Also some BIOS have locked MBR with security settings which then prevents grub from installing to MBR. Have you checked UEFI/BIOS for MBR security or similar settings?

---

### Post by ddubbz1979 on 2013-09-20
> **Quackers said:**
> Ouch.
Did you see Oldfred's reply to your other thread?
We need to know what's happening with your system. How it boots and in what mode.
It may be a UEFI machine but booting in bios mode. Can you enter your bios and tell us what booting options are there please and what are currently set?
Also if you could boot into the Ubuntu cd/usb and select "try Ubuntu" then when the desktop loads open a terminal and run ```
sudo fdisk -l
```and post the output here please.


hard to tell from the font but is that sudo fdisk -1.  as in the #1?

---

### Post by Quackers on 2013-09-20
It's a lower case L but if you copy/paste it then it won't matter  ;)

---

### Post by ddubbz1979 on 2013-09-20
and sorry for the similar thread.  it started as a different problem but back to same thing again.  thanks for closing.

---

### Post by ddubbz1979 on 2013-09-20
> **Quackers said:**
> Ouch.
Did you see Oldfred's reply to your other thread?
We need to know what's happening with your system. How it boots and in what mode.
It may be a UEFI machine but booting in bios mode. Can you enter your bios and tell us what booting options are there please and what are currently set?
Also if you could boot into the Ubuntu cd/usb and select "try Ubuntu" then when the desktop loads open a terminal and run ```
sudo fdisk -l
```and post the output here please.

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x7b4d19a1

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048    35653631    17825792   27  Hidden NTFS WinRE
/dev/sda2   *    35653632    35858431      102400    7  HPFS/NTFS/exFAT
/dev/sda3        35858432   819482623   391812096    7  HPFS/NTFS/exFAT

Disk /dev/sdg: 1028 MB, 1028980224 bytes
4 heads, 8 sectors/track, 62803 cylinders, total 2009727 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sdg1   *           8     2009726     1004859+   c  W95 FAT32 (LBA)
ubuntu@ubuntu:~$

---

### Post by ddubbz1979 on 2013-09-20
my live usb now has 13.04 by the way in case it matters.  gave up on 12.04.  but feel free to let me know if that was a mistake.

---

### Post by Quackers on 2013-09-20
Thanks. When you boot the Ubuntu live usb I presume you get a black screen with a couple of lines of type at top left rather than the purple screen with the little man at the bottom?

---

### Post by oldfred on 2013-09-20
Version should not make any difference.
You have a BIOS boot Windows with the standard 100MB Windows hidden boot partition sda2 and main install in sda3.

Use Windows to shrink the main Windows install to make unallocated space for Ubuntu. Do not create partitions with Windows as it may want to convert to dynamic partitions from basic. Reboot into Windows so it can run chkdsk and make repairs for its new size.

I usually partition in advance with gparted but you can do it during install. You will have to create sda4 as an extended partition including all the unallocated space. Then inside the extended you can create an unlimited number of logical partitions. All your new partitions will be logical.

       For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:

for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)


Installer has not really changed, so you can install with 13.04 and screens will be almost the same in these examples.
 Install with separate /home from aysiu
[URL="http://www.psychocats.net/ubuntu/installseparatehome"]http://www.psychocats.net/ubuntu/installseparatehome
      [/URL]
 Install 12.04.1 with screenshots of Unity, gnome3, & gnome fallback - Not everything is necessary, but shows how to do many things
[http://*********************.com/](http://*********************.com/)

    [URL="http://www.psychocats.net/ubuntu/installseparatehome"]
[/URL]

[URL="https://help.ubuntu.com/community/DiskSpace"]
[/URL]

---

### Post by ddubbz1979 on 2013-09-20
> **Quackers said:**
> Thanks. When you boot the Ubuntu live usb I presume you get a black screen with a couple of lines of type at top left rather than the purple screen with the little man at the bottom?

first screen is black with try ubuntu, install, etc.  then ubunu logo on purple screen after selecting try.

---

### Post by Quackers on 2013-09-20
Thanks. See what Oldfred has to say but Ubuntu live usb is definitely booting in EFI mode. With your system it needs to boot in bios mode. To change that there will be a setting in your computer's bios. 
In this mode grub_efi cannot be installed. It should be installing grub-pc.

---

### Post by ddubbz1979 on 2013-09-20
And if dual booting with windows a shared NTFS partition is also  recommended. But you usually cannot create that as part of the install,  just leave some space. Or partition in advance (recommended).  This I do not understand completely and would mean I do need to partition in advance instead of during install.  ?  I don't understand how to just "leave some space."  Thanks for all the help. I'm not gonna give up just yet.

---

### Post by Quackers on 2013-09-20
Give up? Certainly not!
A shared partition is a matter of choice only.
Leaving space is accomplished in the "something else" option partitioning screen. You just don't use all of the available space - you make a swap partition and a root (/) partition but leave some space unallocated. Or create an NTFS partition in that unallocated space if you so desire.

Anyway, you need to get the Ubuntu live usb to boot in bios mode first or you won't be installing or partitioning anything.
Any news on your bios settings in that regard?

---

### Post by ddubbz1979 on 2013-09-20
yes sir!  got my bios up and it was priority as an efi boot.  i selected the other usb option and got the screen with the "little man" on the bottom now.  should i partition in advance in gparted?  or just try the alongside option?

---

### Post by Quackers on 2013-09-20
Excellent! :-)
I would choose the "something else" option and create the partitions you want from the 75GB unallocated space you created earlier.
I would suggest a swap partition, a root (/) partition and if you want a separate /home partition do that. If you want a NTFS data partition you can create that too but as you've only got 75GB that might be a squeeze.
With the live usb booting in bios mode it should now install grub normally (without grub_efi) and the installation should complete.

If you pre-partition with gparted you will still need to use the "something else" option in order to choose their mount points anyway.

---

### Post by ddubbz1979 on 2013-09-20
If the NTFS data partition isn't necessary, then I won't worry about it.  However, if you recommend I can allocate additional space as I've got more to work with.  Just wasn't sure what I needed but assumed 75 gb would be plenty for files.  I read the /home was a good practice so will do that.  I will allocate 20gb to the /  root.  4 gb to the swap.  and remaining to home.  I will make / as a primary.  and the rest logical.  and choose the / root to install to.  any issues there?  thanks again.

---

### Post by Quackers on 2013-09-20
Just one. 
As you already have 3 primary partitions any new new partitions will need to be logical partitions - all of them. This is not a problem as Ubuntu can boot from a logical partition.
You can always create a NTFS shared data partition if you want at a later date (though that too would need to be logical - i.e. inside the extended partition that Ubuntu will automatically create once logical partitions are created.

---

### Post by ddubbz1979 on 2013-09-20
Thank you so much and wish me luck.  Here we go.

---

### Post by Quackers on 2013-09-20
Good Luck :)

---

### Post by ddubbz1979 on 2013-09-20
one more thing.  what device do i choose for bootloader

---

### Post by Quackers on 2013-09-20
If your main hard drive is /dev/sda in Linux then the default position for grub will do (/dev/sda). I suspect it is /dev/sda (NOTE no partition number!) but you should check to make sure as sometimes the bios will make a usb drive /dev/sda

---

### Post by ddubbz1979 on 2013-09-20
stuck on retrieving file 40 of 102.  and looks like it killed my internet connection again.  i've had to reset my router after every attempt.

---

### Post by Quackers on 2013-09-20
Did you select to download updates and install 3rd party drivers  during the installation? Try without, if you did.

---

### Post by oldfred on 2013-09-20
Also are you using hard wired Ethernet connection? Best to use for install as sometimes it needs to download the wireless drivers and that causes issues.

---

### Post by ddubbz1979 on 2013-09-20
I think the hard wired internet was an issue as I was using wireless.  As well as going into BIOS to change from EFI boot to Legacy.  I now have Ubuntu 13.04.  Hope I shouldn't have got 12.04 instead.  But we shall see.  Thanks you guys for all the help and sticking with me.  I bypassed installing updates and 3rd party software during install.  Now I've got to figure that out to make sure I'm all up to date and ready to rock.  Thanks again.  One of the best forums I've been on for any subject matter.  Very impressive.  And 3 more computers to go that are still XP.  Hope its as easy now I know what's up.

---

### Post by Quackers on 2013-09-20
Excellent! :)
Glad to hear that. Did the grub menu include an entry for the Windows loader? If it does try to load Windows from it.
If it didn't try running ```
sudo update-grub
``` in a terminal and watch to see that it is picked up in the output, then try to boot it.

With regard to your different computers it's possible that older versions of Ubuntu may be advisable, but only trial and error will decide that.

Well done! Perseverence is good! :)

By the way I find it's better (read safer) to install synaptic package manager to run updates rather than using the software centre thingy.

---

### Post by ddubbz1979 on 2013-09-20
it will be my first install then.  i will search for synaptic now.  thanks again.  life saver today.  chalk up a successful support and keep up the good work.

---

### Post by Quackers on 2013-09-20
Nice one! Glad to help :-)

---

### Post by oldfred on 2013-09-20
Glad you got it working. :)

Run this to update everything after # is just my notes, do not copy
#resync package index 
sudo apt-get update 
#newest versions of all packages, update must be run first
sudo apt-get upgrade

To get the restricted extras:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by ddubbz1979 on 2013-09-20
Killer man.  Thanks.  Always open for tips. I'm a noob.  Is this all the updates I need?  Thanks again for all the persistance and help.

---

