---
title: "Grub hard disk error"
date: 2007-02-16
forum: Installation &amp; Upgrades
---

### Post by tomsturge on 2007-02-16
Ive formatted my hard drive to install kubuntu as the primary/only operating system. i ran the kubuntu live dvd and installed it as the main os with the default hard drive partitions.

Hda1 /
hda5 swap
with Grub installed on hdo

once installed i then rebooted without the live cd in and im greeted with a dos screen with the message,
'GRUB Hard Disk error'
no extra information given to the reason.

The only way ive found to boot the system is to use the 'boot from hard disk' option on the live dvd which works fine.

The only reason for this i can think of this is a cryption in the GRUB. if anyone can help with this problem or have a better idea as to the reason please help.

---

### Post by Herman on 2007-02-16
> GRUB Hard Disk error
I haven't seen that exact error before. Are you running 'Edgy Eft' or earlier? I think I read somewhere that 'Fiesty' has grub2. That might have new error messages we haven't seen yet.

I am collecting grub errors and other booting errors and possible solutions to them, the closest match I have is this one:                                [Hard disk boot sector invalid, press H to retry hard disk or any other key for floppy]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Hard_disk_boot_sector_invalid")

Another one that is vaguely close is this BIOS one:                                [Disk boot failure, insert system disk and press enter]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#DISK_BOOT_FAILURE_INSERT_SYSTEM_DISK")

Yours sounds like it might not be either of those, but you could check anyway, just to make sure.

Can you please enter 'sudo fdisk -lu' in a terminal and post the output here, I or someone else may be able to see what's wrong from reading that.

Regards, Herman :)

---

### Post by tomsturge on 2007-02-17
Here is the output from 'sudo fdisk -lu'

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes

Device.... Boot......Start.........End................Blocks.......Id...System
/dev/hda1...*..........63..........112390739....56195338+..83..Linux
/dev/hda2.......112390740...117210239.....2409750......5...Extended
/dev/hda5.......112390803...117210239.....2409718+...82..Linux swap / Solaris

---

### Post by tomsturge on 2007-02-17
grub> find /boot/grub/stage1
 (hd0,0)

This is the location of my grub. Could this be the problem? Should it be in hd0,1?

---

### Post by louieb on 2007-02-17
> **tomsturge said:**
> 
...with Grub installed on[COLOR=Red] hdo[/COLOR]
  Probably just a typeo error in your post did you mean [COLOR=Red]hd0 thats a zero?[/COLOR]
The fdisk output look normal. You may just need to reinstall GRUB.
Herman's site is one of my favorites. I usually go there first when I  have a Dual Boot or GRUB question.
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD) is the link to his reinstall GRUB page. or there is a forum how to link in my signature.

(hd0,0) is correct in GRUB speak thats the same as hda1.

---

### Post by tomsturge on 2007-02-17
sudo update-grub
Searching for GRUB installation directory ... found: /boot/grub
Testing for an existing GRUB menu.list file ... found: /boot/grub/menu.lst
Searching for splash image ... none found, skipping ...
Found kernel: /boot/vmlinuz-2.6.17-11-generic
Found kernel: /boot/vmlinuz-2.6.17-10-generic
Found kernel: /boot/memtest86+.bin
Updating /boot/grub/menu.lst ... done

After running setup in the grub shell i updated it in the main shell. Is anything out of the norm here?

---

### Post by tomsturge on 2007-02-17
Tried using Super Grub Disk to repair it but there is the same problem. 

Dont know what else i can do. Can someone give me some help on this?

---

### Post by louieb on 2007-02-17
Sorry but I don't see anything that you are doing anything wrong. fdisk looks fine.
The how to's usually work. 
Super Grub usually works.
Its just weird that you can boot  using the live CD but can't boot directly off the hard drive.
Somebody else may have something else to try.

---

### Post by tomsturge on 2007-02-17
Installed qtparted to check the partitions and received this message:

Critical Error during ped_disk_new!

Could this message give some information as to what the problem with GRUB? Is it my hard drive thats the problem?

---

### Post by rsambuca on 2007-02-17
Very strange indeed.  Do you have another IDE cable you can try?  I have seen weird errors disappear with a new cable.

---

### Post by tomsturge on 2007-02-17
Its running off a laptop so that idea cant be done quickly. How likely is that to help the situation? There isn't a boot problem with xp installed or suse, only seems to be a problem with Ubuntu and Kubuntu.

---

### Post by rsambuca on 2007-02-17
??? I thought you only had kubuntu?

---

### Post by tomsturge on 2007-02-17
I do but I tried ubuntu first and didnt like the gnome interface so i tired kubuntu for the KDE interface and prefer it but they both have the same problem with GRUB

---

### Post by louieb on 2007-02-17
Herman had asked earlier which version of Ubuntu are you trying to install. Now I am curious also. Because of bug reports and I don't need  the latest and greatest I am still running Dapper. Don't think it the hard drive.
Where did you install QTparted?

---

### Post by tomsturge on 2007-02-17
Sorry Im running edgy, thought about trying dapper but I wanted to get edgy working if possible.

I installed Qtparted using these commands:

sudo aptitude update
sudo aptitude install qtparted
kdesu qtparted

---

### Post by rsambuca on 2007-02-17
I would recommend using the gParted live CD as it is more up to date and has a few more features than what is found in the ubuntu repositories.  Also, it is easier to work on your drive(s) when nothing is mounted.

---

### Post by louieb on 2007-02-17
I'm out of stuff for you to try. The fact that you can boot using the Live CD.
That leads to one more question when you boot to hard drive using the live CD does grub display first then you select Ubuntu from the menu? 
I am wondering if grub is install in the MBR of the hard drive (hd0) or if it somehow got installed int the MBR of the first partition  (hd0,0).
When you installed Ubuntu, kUbuntu and when you use Super Grub did you tell it to install in the MBR of the hard drive (hd0) or the MBR of the first partition (hd0,0). If that what was done then that would explain what has happened.

---

### Post by rsambuca on 2007-02-17
If you can enter a terminal, enter ```
sudo grub
```
At the grub prompt, enter ```
setup (hd0)
```
type quit and try rebooting.

---

### Post by Herman on 2007-02-17
Hello tomsturge and everyone,
I found one or two links that might be helpful here,  ["**GRUB Hard Disk Error**" | MEPIS]("http://www.mepis.org/node/9363") and   [blarg?: **Grub Hard Disk Error**]("http://neon.polkaroo.net/%7Emhoye/blarg/archives/003382.php")

Well really I did a lot more reading than that, but those were the two I screened out that seemed to be the most promising.

I hope those will be of some help. There are one or two other threads running here in Ubuntu Web Forums at the moment with the same error. 

Regards, Herman

---

### Post by Even on 2007-03-27
New Ubuntu user (yay!) and I'm actually having this exact same error. When I try to boot from the hard disk, I get "Grub Hard Disk Error" and nothing else. When I boot from the Live CD and select "Boot from first hard drive" everything works perfectly. I even managed to install my ATI drivers and Beryl correctly! (Cube desktop is sooo cool!)

But I digress, I tried rsambuca's idea and I got this:

grub> setup (hd0)

Error 12: Invalid device requested

I was dual booting Win2K and Ubuntu Edgy at first, but then I just formatted everything and got rid of windows all together after I learned I can run World of Warcraft from Ubuntu. Somewhere along the line I'm almost sure I put GRUB in the MBR, but since I'm new, I'm not sure how to fix it.

Anyway, if this helps, here's my output of fdisk -lu:

Disk /dev/hda: 203.9 GB, 203928109056 bytes
255 heads, 63 sectors/track, 24792 cylinders, total 398297088 sectors
Units = sectors of 1 * 512 = 512 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1              63   278004824   139002381   83  Linux
/dev/hda2       278004825   398283479    60139327+  82  Linux swap / Solaris

---

### Post by rsambuca on 2007-03-27
I think you might have made a typo since (hd0) is actually your hda1.  Perhaps try again and make sure it is a zero and not a capital O.

---

### Post by Even on 2007-04-03
Still having that "GRUB HARD DISK ERROR" message pop up without the Live CD.

grub> setup (hd0)

Error 12: Invalid device requested

And yes, that's a zero.

---

### Post by rsambuca on 2007-04-03
To get the grub prompt, did you enter "sudo grub", or just "grub"?

---

### Post by Even on 2007-04-03
Just grub.

---

### Post by rsambuca on 2007-04-03
Ahhh, that's the problem there.  You need to do "sudo grub".

---

### Post by Even on 2007-04-04
Hmm, I get the same result launching grub with the sudo command. Is that bad?

---

### Post by Even on 2007-04-04
Is there a MBR repair utility that I can run with Ubuntu and just reinstall grub?

---

### Post by rsambuca on 2007-04-04
```
sudo grub-install
```

---

### Post by davbslim on 2007-05-15
This site does provide some help
[http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php](http://neon.polkaroo.net/~mhoye/blarg/archives/003382.php)

This one has someone who updated their BIOS and got it working.
[http://www.mepis.org/node/9363](http://www.mepis.org/node/9363)

I cannot update my BIOS.  I already have the latest one.  It seems that I will have to stick with Dapper.  The ones who can update their BIOS may see this problem disappear.  My computer gives this message also. :(

---

### Post by mredding on 2007-08-03
I have a similar problem after a default install of Ubuntu Server 7.04 Feisty on an IBM Intellistation M Pro 6850-3M5 with 18.2 GB SCSI HD, 2.4 GHz Xeon P4, 1 GB RDRAM. I've flash updated the BIOS from DAE137A to DAE143A (Latest). No luck.

It seems this is a fairly common problem, even on other Linux flavors:
[http://www.howtoforge.com/forums/archive/index.php/t-10311.html](http://www.howtoforge.com/forums/archive/index.php/t-10311.html)
[http://lists4.opensuse.org/opensuse-autoinstall/2005-04/msg00037.html](http://lists4.opensuse.org/opensuse-autoinstall/2005-04/msg00037.html)
[http://forums.fedoraforum.org/showthread.php?t=81530](http://forums.fedoraforum.org/showthread.php?t=81530)
[http://www.linuxquestions.org/questions/showthread.php?t=363651](http://www.linuxquestions.org/questions/showthread.php?t=363651)
[http://www.webservertalk.com/message1230996.html](http://www.webservertalk.com/message1230996.html)
[http://forums.debian.net/viewtopic.php?p=13619&sid=ff189c1123266a70c62f8f3fc73be250](http://forums.debian.net/viewtopic.php?p=13619&sid=ff189c1123266a70c62f8f3fc73be250)

etc, etc.

Could it have something to do with RAID maybe? I don't have RAID enabled, but I believe this machine is capable of it. Also, a lot of these are IBMs. Maybe a common hardware thing?

EDIT: I tried Ubuntu Server 6.06 LTS Dapper Drake with the same result. :-(

EDIT x 2: Reinstalled Feisty Fawn, installed GRUB to the linux partition and GAG Graphical Boot Manager to the MBR (LILO install failed and gave an equally uninformative error). It's more of a workaround than a solution, but at least a successful one.

---

### Post by Jammy4041 on 2007-11-16
I am having trouble with the GRUB too. Does anybody know how to cure error 15?

Thanks James

---

### Post by Herman on 2007-11-16
Hello Jammy4041,
Probably you just need to check your spelling in your /boot/grub/menu.lst file's operating system entries, here, read this link, [     Grub error 15]("http://users.bigpond.net.au/hermanzone/p15.htm#15"). :)

If you still have trouble and you need more help, don't be shy to post here again and I or someone will help you.
If you can include a copy of the bottom part of your menu.lst file and the output from 'sudo fdsik -lu' it might also help.

Regards, Herman :)

---

### Post by Jammy4041 on 2007-11-24
Thankyou, Herman for your help.

I have managed to cue Error 15 by reinstalling Fiesty. Ubuntu is now my only OS.
 
If anybody experiences Error 15 it is probably due to a bad unistallation, so try reinstalling Ubuntu properly.

James

---

### Post by exphyl on 2008-02-02
I Have found a solution that works for me in reference to the Grub Hard Disk Error. You may want to go into your bios and check to see what hard drive is booting first, there is a good chance the wrong drive is booting first.

---

### Post by m.rambouillet on 2008-03-18
I have the same problem with grub : hard disk error.
The stage-1.5 is not found due to a bad geometry of the disk (i think's).
All versions of grub that i have tested (Mandrake, Gentoo) have the problem
(with or without the --lba option),
but the Fedora (with anaconda) install grub properly on the same machine,
and the boot is ok !

[B]I have just the solution for the problem after examining on the console number 5, the result of the Fedora installation
(just before rebooting).[/B]

To install grub manualy, the procedure is commonly :
    >root (hd0,0)
    >setup (hd0)
But this install the stage1.5 embedded by default and go in error when we reboot (on some hard disks).
[B]The good procedure is :
    >root  (hd0,0)
    >install  --stage2=/boot/grub/stage2  /grub/stage1  d  (hd0)  /grub/stage2  p  (hd0,0)/grub/menu.lst
[/B]
to install grub on the MBR of the first hard disk with the /boot/grub directory on the first partition of this disk.

---

### Post by surfed on 2008-03-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **m.rambouillet said:**
> 

To install grub manualy, the procedure is commonly :
    >root (hd0,0)
    >setup (hd0)
But this install the stage1.5 embedded by default and go in error when we reboot (on some hard disks).
[B]The good procedure is :
    >root  (hd0,0)
    >install  --stage2=/boot/grub/stage2  /grub/stage1  d  (hd0)  /grub/stage2  p  (hd0,0)/grub/menu.lst
[/B]
to install grub on the MBR of the first hard disk with the /boot/grub directory on the first partition of this disk.

Thank you, I have been fighting this problem on my IBM Intellistation for a long time and not even google helped me... i will file a bug report with solution.

---

### Post by jrogers360 on 2008-03-27
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have an IBM Intellistation with the same symptoms, and I'm trying to implement your solution.

I first ran 'sudo grub', then entered the commands you suggested:

```
root (hd0,0)
install --stage2=/boot/grub/stage2 /grub/stage1 d (hd0) /grub/stage2 p (hd0,0)/grub/menu.lst
```

But I recieve an error from the grub program when running the install command:

```
Error 15: File not found
```

What am I doing wrong here?  Which file is the error complaining about?

EDIT: I got it working...  The install command was missing /boot from each of the file names.  It worked with this:

```
root (hd0,0)
install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd0) /boot/grub/stage2 p (hd0,0)/boot/grub/menu.lst
```

---

### Post by surfed on 2008-03-27
> **jrogers360 said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314](https://bugs.launchpad.net/ubuntu/+source/grub-installer/+bug/206314) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I have an IBM Intellistation with the same symptoms, and I'm trying to implement your solution.

I first ran 'sudo grub', then entered the commands you suggested:

```
root (hd0,0)
install --stage2=/boot/grub/stage2 /grub/stage1 d (hd0) /grub/stage2 p (hd0,0)/grub/menu.lst
```

But I recieve an error from the grub program when running the install command:

```
Error 15: File not found
```

What am I doing wrong here?  Which file is the error complaining about?

EDIT: I got it working...  The install command was missing /boot from each of the file names.  It worked with this:

```
root (hd0,0)
install --stage2=/boot/grub/stage2 /boot/grub/stage1 d (hd0) /boot/grub/stage2 p (hd0,0)/boot/grub/menu.lst
```
Maybe the difference is that you dont have a dedicated boot partition?

---

