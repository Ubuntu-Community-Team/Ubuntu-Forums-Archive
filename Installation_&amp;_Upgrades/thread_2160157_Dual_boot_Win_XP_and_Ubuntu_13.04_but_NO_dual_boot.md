---
title: "Dual boot Win XP and Ubuntu 13.04 but NO dual boot option"
date: 2013-07-05
forum: Installation &amp; Upgrades
---

### Post by Nuuubie13 on 2013-07-05
[FONT=Arial][SIZE=2]Dear Forum:[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Yesterday I installed Ubuntu 13.04 alongside Windoze XP.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Installing Ubuntu was a snap and went without a hitch :). But for whatever reason there's no dual boot option there when I boot my machine :(.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]When I used Linux Mint a while ago and had a similar problem I reinstalled Linux only to find two Linux OS installed on the same partition.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Now I'm a bit worried that doing the same with Ubuntu will only get me the same result. [/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]So, I'm wondering if instead of formatting (or even low-level formatting) the Ubuntu partition before reinstalling Ubuntu again editing the boot.ini might be a bit faster. Btw, [/SIZE][/FONT][FONT=Arial][SIZE=2]Win XP is on Disk 2 and Ubuntu 13.04 on Disk 1, partition 2.[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Many thanks! :)[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Nuuubie13[/SIZE][/FONT]

---

### Post by fantab on 2013-07-06
Are you able to boot Ubuntu? Are you able to boot XP?

You say that XP is on Disk2 and Ubuntu on Disk1, right? Where did you install Grub? on disk2 or disk1? 
Look in the BIOS for HDD boot Priority and change it to boot Disk1 with Ubuntu as the first boot. Let us know.

---

### Post by Nuuubie13 on 2013-07-06
[FONT=Georgia][SIZE=2]Hi Fantab:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Thanks a lot for your reply.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]I can boot Win XP but not Ubuntu 13.04. And changing the boot priority didn't change that :(.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Thinking I'd give it another go I deleted the Ubuntu partition, formatted it and reinstalled Ubuntu again. This time it installed itself on disk 0. And again there's no dual boot option for Ubuntu :(.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Not sure, if the following is of any importance. Once Ubuntu's been installed it says that a reboot is necessary. After clicking on "Reboot" Ubuntu ticks off a list of programs or processes that need to terminate and acknowledges each one with OK. After the last program closed and got OKed I think Ubuntu opened the DVD drive for the DVD to be removed. Idid that and after nothing happened for a while I manually closed the tray and pressed Enter which caused the machine to reboot but, as already mentioned, once again without the dual boot option. [/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]As for where Grub is installed, I don't know. Ubuntu did it. The Swap partition, though, is on the same disk as Ubuntu, i.e. now disk 0 (and XP on disk 2).  [/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]I didn't try changing the boot priority again because it seems that in a dual boot system both OS need to be entered into the boo.ini (which they still are not).[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT][FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Many thanks again.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Nuuubie13[/SIZE][/FONT]

---

### Post by fantab on 2013-07-06
Your BIOS is responible for making the HDD available for boot. If we have more than one HDD then the HDD Boot priority is necessary. If Xp is on Disk2, then it will have its boot loader on Disk2 and if Disk2 is set as first Boot Disk then XP will boot. If you change the HDD priority to Disk1 then XP will not boot.
Similarly, if Grub (Ubuntu bootloader) is on Disk1 and if the boot priority is set to boot Disk1 first then Grub will boot, if not then it wont. 
XP cannot boot Linux on its own while Grub can boot both Linux and Windows. So having the HDD with Grub as first HDD to boot in BIOS will enable Grub to load and give you a menu to choose either OS to boot. 
For Ubuntu boot.ini doesn't apply.

Grub install can be managed if you select 'Something Else' option during Ubuntu instalation. It needs to be installed on the HDD where Ubuntu is installed. This is recommended. However if Grub is installed on the other disk where XP is then it will overwrite XP boot loader files in MBR. So when Ubuntu is removed/uninstalled then XP will not boot and you have to fix the MBR with XP files. To avoid this, if you have different HDDs then a separted HDD for Ubuntu and Grub is recommended.

This is why it is important for you to know which HDD is booting first and on which HDD you have installed Ubuntu and Grub. So you can set it accordingly. 

Do you have any encryption on the HDDs?
Check in your BIOS for SATA Mode and tell us what option it is set to. IDE is ok, we need to see if its set to RAID.

Boot with Ubuntu DVD/USB and run the following:

```
sudo fdisk -l
sudo parted -l
```

and post the output here.

---

### Post by Nuuubie13 on 2013-07-07
[FONT=Arial][FONT=Georgia][SIZE=2]Hi Fantab:[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Thanks again for your reply :).[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Yes, Ubuntu and XP are on different disks. And no[/SIZE][/FONT][SIZE=2][FONT=Georgia], there's no encryption on the HDDs. [/FONT][/SIZE]
[SIZE=2][FONT=Georgia][/FONT][/SIZE] 
[SIZE=2][FONT=Georgia]The disk that Ubuntu is on and which I made the first boot disk says SATA4 (in BIOS). Not sure if that's what you're asking, though. Btw, how do I find out whether BIOS is set to RAID instead of IDE? In "Advanced BIOS Features" there was something about IDE but not RAID.[/FONT][/SIZE]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Anyway, things didn't work out quite as I'd hoped :(. After the Ubuntu install disk had booted and I'd selected "Something else" things got a bit murky. Googling for additional info that might help me better understand the intricacies of Ubuntu didn't get a lot of helpful info, though :(.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]When I tried to install Grub on the same HDD as Ubuntu (actually, I tried to install it in the Ubuntu partition) Ubuntu told me to first create (or set) a root folder. In my case Ubuntu is on the sdc5 ext4 folder (whatever that means) so I tried to install Grub into that folder as well as make it root. Actually, I did that twice and each time there was not dual boot option after the reboot.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]I probablydidn't pay enough attention but where in "Something else" can I enter: [/SIZE][/FONT]
[FONT=Georgia][SIZE=2]sudo fdisk -l
sudo parted -l
[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Also, should I delete and then format the Ubuntu partion before the next install? Ubuntu said something about corrupted (?) files and that I might have to manually install some programs myself.[/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]I'm sorry this seems to be getting more complicated by the day... :( [/SIZE][/FONT]
[FONT=Georgia][SIZE=2][/SIZE][/FONT] 
[FONT=Georgia][SIZE=2]Nuuubie13[/SIZE]
[/FONT]
[/FONT]

---

### Post by Penguenci on 2013-07-07
> **Nuuubie13 said:**
> [FONT=Arial][FONT=Georgia][SIZE=2]When I tried to install Grub on the same HDD as Ubuntu (actually, I tried to install it in the Ubuntu partition) Ubuntu told me to first create (or set) a root folder. In my case Ubuntu is on the sdc5 ext4 folder (whatever that means) so I tried to install Grub into that folder as well as make it root. [/SIZE][/FONT][/FONT]
[FONT=Arial][FONT=Georgia][SIZE=2]
You've told us the problem yourself! It is virtually impossible that the problem lies anywhere else but right here in what you just said.
[/SIZE][/FONT]
 
[/FONT]> **Nuuubie13 said:**
> [FONT=Arial][FONT=Georgia][SIZE=2]Also, should I delete and then format the Ubuntu partion before the next install? Ubuntu said something about corrupted (?) files and that I might have to manually install some programs myself.[/SIZE][/FONT][/FONT][FONT=Arial][FONT=Georgia]
[/FONT]
[/FONT]That's totally typical when you install Ubuntu on an existing Ubuntu partition. It's usually a *bad* idea to do that anyway, and has a 70% chance of making your mouse cursor permanently still even if you're able to boot into Ubuntu.


[B][SIZE=4]Solution:[/SIZE]
[/B]
- Reinstall Ubuntu, _****formatting****_ the partition. In other words, do a _***fresh install***_. You can leave the swap partition and its settings intact, but format the main Ubuntu partition(s) with home, root, and such.

- While installing, **[COLOR=#ff0000]select the HDD - not the partition - for the location of the MBR.[/COLOR]** In your case, this should be SDC, as opposed to SDC5. This time, as you reboot, you should get a GRUB menu with both your operating systems. And even if you don't, the fix is quite simple, but let's get to that if you actually need it, which you hopefully won't.

Incidentally, it's not a great idea to put Ubuntu on the 5th partition if you're planning to use GRUB. Your HDD may fail to boot even if you do everything else right, as your boot files will be too far from the beginning of the disk.

Good luck!

---

### Post by fantab on 2013-07-08
> **Nuuubie13 said:**
> [FONT=Arial]
[FONT=Georgia][SIZE=2]I probablydidn't pay enough attention but where in "Something else" can I enter: [/SIZE][/FONT]
[FONT=Georgia][SIZE=2]sudo fdisk -l
sudo parted -l [/SIZE][/FONT][/FONT][FONT=Arial][FONT=Georgia][SIZE=2]

[FONT=verdana]Boot with Ubuntu DVD/USB and choose option 'Try Ubuntu without installing'... wait till the desktop is ready. Open Terminal [Ctrl+Alt+T] and the run the commands and post its output here.[/FONT]
[/SIZE][/FONT]
 
[FONT=Georgia][SIZE=2]> Also, should I delete and then format the Ubuntu partion before the next install? Ubuntu said something about corrupted (?) files and that I might have to manually install some programs myself.[/SIZE][/FONT][/FONT]

Yes, re-installing Ubuntu after formatting the partition is a good idea. But first lets see the output I requested from the commands above.
Also post a Screen-Shot of HDD (on which you wish to install Ubuntu and its partitions) using Windows Disk Management.

> **Penguenci said:**
> [FONT=Arial][FONT=Georgia][SIZE=2]
[/SIZE][/FONT][/FONT]Incidentally, it's not a great idea to put Ubuntu on the 5th partition if you're planning to use GRUB. Your HDD may fail to boot even if you do everything else right, as your boot files will be too far from the beginning of the disk.

This is not true. I have Ubuntu booting from /dev/sdb8, Logical Partition without any issues.

---

### Post by Nuuubie13 on 2013-07-14
[FONT=Arial][SIZE=2]Thanks a lot everybody for replying **:**). And my apologies for this late answer :(.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]The day after I'd gotten your replies to my post and for whatever reason I suddenly couldn't enter text of any sort in XP **:**(. More to the point, I couldn't rename folders in the Explorer, couldn't enter text in Google and also couldn't enter or delete text in Word and OpenOffice. After unsuccessfully trying for several hours to figure out what was going on I low-level formatted the C (Windoze) partition, which took a whopping four days to finish!

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Anyways, a little earlier today I gave installing Ubuntu another shot (after installing Win XP first)... with the same annoying result. NO dual boot although I think I did everything right this time.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]a) Before installing Ubuntu I had it format the partition of the previous installation[/SIZE][/FONT]
[FONT=Arial][SIZE=2]b) Ubuntu is not on the same HDD as Windoze XP[/SIZE][/FONT]
[FONT=Arial][SIZE=2]c) The boot loader is on the same HDD as Ubuntu.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]This time Win XP is on sdb1, Ubuntu 13.04 on sdc3 (ext4 and \) with the boot loader on sdc and the swap partition on sdc1.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]I then opened the Terminal and first entered "[/SIZE][/FONT][FONT=Arial][SIZE=2]sudo fdisk -l" after the prompt and and then "sudo parted -l" after hitting Enter. After which I[/SIZE][/FONT][FONT=Arial][SIZE=2] got this: [/SIZE][/FONT]
[FONT=Arial][SIZE=2]parted: invalid option - - '1'[/SIZE][/FONT]
[FONT=Arial][SIZE=2]Usage: parted [ - hlsmv ] [ - a<align> ] [ Device [ Command [ Parameters ] ]... ]

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Any additional help to finally get a dual boot option is greatly appreciated **:**).

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Many thanks,

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Nuuubie13[/SIZE][/FONT]

---

### Post by oldfred on 2013-07-14
That is an el not a one or capital I. You can just copy & paste commands as even spaces which may not show correctly are important.

May be best just to run this and post link. You can install to any working Ubuntu, to liveCD (each time you reboot) or download the full repairCD.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by Nuuubie13 on 2013-07-15
[FONT=Arial][SIZE=2]Thanks a lot, OldFred.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]I think I'll first try Linux-Secure. Right now Linux-Secure 13.0432bit is downloading.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]If for some reason I won't succeed I'll get in touch again.

[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Many thanks again.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Nuuubie13[/SIZE][/FONT]

---

### Post by Nuuubie13 on 2013-07-17
[FONT=Arial][SIZE=2]Hi OldFred, everybody:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]I think I'll need some more help **:**).[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]After downloading and burning both Boot-repair-disk-32bit.iso and Linux-secure-13.04-32bit.iso I[/SIZE][/FONT][FONT=Arial][SIZE=2] decided to try the Boot-repair-disk first but realized that I have NO I dea on how to use it **:**(. [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]More to the point, opening F1, F2, etc. is no problem. I just don't know how all of that info applies to my situation, i.e. the missing dual boot option.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]So, if I could get a few pointers that would be great **:**).[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]As for Linux-secure-13.04 and in case that turns out to be the more promising option, before installing it I probably need to format the Ubuntu partition again (sigh...)?![/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Many thanks,[/SIZE][/FONT]
 
[FONT=Arial][SIZE=2]Nuuubie13 [/SIZE][/FONT]

---

### Post by oldfred on 2013-07-17
Boot-Repair can just run auto repairs. But if issue is really just Windows needing a chkdsk or Windows repairs, you need your XP disk to run those repairs.

Best to post link to BootInfo report. See post #9.

---

### Post by Nuuubie13 on 2013-08-05
Quick note re. Boot Repair
[FONT=Arial][SIZE=2]Hi OldFred:[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Sorry about my long silence **:**(. [/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]It seems Boot-Repair doesn't start fixing the dual boot option on its own. At the very least you need to select either "32bit session" or "32bit session (failsafe)" in the middle of the screen to start boot repair. Adjusting additional parameters/settings with F1 trough F6 appears to be kind of optional (English seems to be the default language, i.e. F1 lets you select your language).[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Long story short, clicking on "32bit session (failsafe)" did start boot repair and actually fixed my boot problems.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]So, many thanks again for all the help.[/SIZE][/FONT]
[FONT=Arial][SIZE=2][/SIZE][/FONT] 
[FONT=Arial][SIZE=2]Nuuubie13[/SIZE][/FONT]

---

