---
title: "Xubuntu 10.04 Wubi install problem"
date: 2011-01-05
forum: Installation &amp; Upgrades
---

### Post by jaythedogg on 2011-01-05
After installing Xubuntu using Wubi (because Ubuntu never worked right on this PC) I got to Grub, selected Xubuntu & have tried Safe Graphics Mode, ACPI workarounds, etc. I have tried nosplash in the grub.cfg as well.

I get to the Xubuntu screen & it locks (no keyboard response, etc.) When I try it in Safe graphics mode or ACPI workarounds, I get the scrolling text, then some more text & finally it gets down to the line where it says:
* Setting sensors limits:                         [ OK ]
Then freezes. Any ideas guys?

My Ubuntu installs from Wubi, Live CD & alternate always failed, even when I wiped the hard disk clean & tried a full install. See my other thread problems here if interested:
[http://ubuntuforums.org/showthread.php?t=1652701]("http://ubuntuforums.org/showthread.php?t=1652701")
I was wrong on my previous system specs though.

Here they are:
WinXP Pro SP3
Pentium 4 CPU 1.80 GHz
512MB of PC800 RDRAM
GeForce 4 MX 4000 64MB DDR
Generic PS2 Mouse & Keyboard.
Standard CRT monitor.

Any help is greatly appreciated.

---

### Post by jaythedogg on 2011-01-05
I added "nomodeset" now after nosplash in my grub.cfg

Will post results, hopefully someone has insight on this problem with this PC.

---

### Post by jaythedogg on 2011-01-05
Booting normal settings, with grub.cfg modified with "nosplash" & "nomodeset" get me right to the "Xubuntu" "splash" screen (Black screen with Xubuntu in center) but this time in low res mode from nomodeset.

Still freezes & keyboard is unresponsive.

Anyone?

P.S. if anyone reads my prior thread, aside from the accidental boots I achieved previously with the 10.04 ubuntu alternate installs, this computer continually has the same problem.
Does Ubuntu have an issue with PC800 RDRAM?

I have no idea otherwise, I can't find any problems with my hardware & chkdsk doesn't find errors...

---

### Post by jaythedogg on 2011-01-05
Really? Nobody has any idea what can fix this? This has been an ongoing problem for me for nearly a month.

---

### Post by jaythedogg on 2011-01-05
Update: Banging my head on the screen repeatedly does nothing for the freezing, but certainly makes me feel like I need a reboot.

---

### Post by jaythedogg on 2011-01-06
Seriously guys, 9 hours & nothing? Really? Nobody has any idea what could be the problem?

I mean, I know this is a FREE OS, this is FREE support forums, but really?

Noone can even take a stab at this?

I am only frustrated because this is the response each & every time I have posted problems with this PC. Then someone will come along & (with good intentions) offer a tip, but didn't read my posts to determine if it had been tried yet.

I don't mean to rant but sheeesh!

---

### Post by Rubi1200 on 2011-01-06
It is quite likely that if you have been editing grub.cfg directly that the changes are not sticking.

The file grub.cfg in NOT to be edited directly.

Here is what I suggest:

Use a LiveCD to boot the computer (you may need to use the nomodeset option) and choose to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here and we will see what is going on with your current setup.

Thanks.

---

### Post by jaythedogg on 2011-01-06
> **Rubi1200 said:**
> It is quite likely that if you have been editing grub.cfg directly that the changes are not sticking.

The file grub.cfg in NOT to be edited directly.

Here is what I suggest:

Use a LiveCD to boot the computer (you may need to use the nomodeset option) and choose to try not install.

At the live desktop, download and run the boot info script linked at the bottom of my post (instructions included).

Post the results back here and we will see what is going on with your current setup.

Thanks.

Will do, but IIRC it wouldn't boot from the LiveCD before either.

---

### Post by Paddy Landau on 2011-01-06
You may not have compatible hardware.

Try Lubuntu, but I don't know that it would make any difference.

---

### Post by GrouchyGaijin on 2011-01-06
> **Paddy Landau said:**
> You may not have compatible hardware.

Try Lubuntu, but I don't know that it would make any difference.

Any luck with Lubuntu?

I'd try reformatting the hard drive again and try Lubuntu.

---

### Post by jaythedogg on 2011-01-06
I just got home with my LiveCD of Xubuntu, will post back when I see if it boots.

Not that I cannot go look, but what's with Lubuntu? I thought Xubuntu was for older systems?

Regardless. Back in a few with info on this attempt.

---

### Post by jaythedogg on 2011-01-06
Okay, got booted in to Xubuntu finally using LiveCD.  I hit F6, tried nomodeset, locked up as usual.

Then I hit F6 again on next attempt & hit:

apci=off
noapic
nolapic
nomodeset

Locked up again.

Then I selected all of them except free software only.

acpi=off
noapic
nolapic
edd=on
nomodeset

There was also one that said something about raid in the list, like dmraid or something, I ticked that too.

Here I am. Going to run that script that the first reply asked me to run, will post back in a min.

This is exciting. :)

---

### Post by jaythedogg on 2011-01-06
Problem...
Downloaded the boot_info_script055.sh & typed:

sudo bash ~/Desktop/boot_info_script055.sh 

In to terminal, (I DL'd it to the desktop btw) & I keep getting this error:
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: syntax error near unexpected token `newline'
/home/ubuntu/Desktop/boot_info_script055.sh: line 1: `<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Transitional//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-transitional.dtd">' 
Any ideas? Will google while I wait.

Edit:

Apparently, save as.... with Firefox grabbed the download page, my mistake, here is the code box with the pertinent info below:

```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================

 => Windows is installed in the MBR of /dev/sda

sda1: _________________________________________________________________________

    File system:       ntfs
    Boot sector type:  Windows XP
    Boot sector info:  No errors found in the Boot Parameter Block.
    Operating System:  Windows XP
    Boot files/dirs:   /boot.ini /ntldr /NTDETECT.COM

=========================== Drive/Partition Info: =============================

Drive: sda ___________________ _____________________________________________________

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes

Partition  Boot         Start           End          Size  Id System

/dev/sda1    *             63   268,414,019   268,413,957   7 HPFS/NTFS


blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 
/dev/ramzswap0                                          swap                                     
/dev/sda1        802CAD232CAD1566                       ntfs                                     
/dev/sda: PTTYPE="dos" 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (ro,noatime)
/dev/loop0       /rofs                    squashfs   (ro,noatime)


================================ sda1/boot.ini: ================================

[boot loader] 
timeout=30 
default=multi(0)disk(0)rdisk(0)partition(1)\WINDOWS 
[operating systems] 
multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect /NoExecute=OptIn 

```Waiting patiently for your instruction oh wise one. :P


Edit #1:

Just rebooted, this time with the "F6 other options" I only ticked EDD=On - Nodmraid -&- nomodeset

When I tried with just the two, not nomodeset, it locked. So nomodeset is a must, but it requires at least one more from prior attempts.

Going to try with one or the other plus nomodeset & post back.

---

### Post by jaythedogg on 2011-01-06
Okay, new problem...

Tried to reboot using the methods that work, now it just freezes at the black screen that has Xubuntu on it.

Tried other variations that worked... Same thing.

This happened before with Ubuntu (in other past threads) & using different hard drives & video cards...

Worked for a bit, by fluke or whatever, using certain methods... Like it discovers my tricks & builds immunity!

My computer is a BORG!

Is it the PC800 RDRam? Doubt it.

The SoundBlaster PCI sound card? Dunno.

Any ideas?

---

### Post by jaythedogg on 2011-01-07
I am just wondering why it works for a bit then goes Borg, this is really troubling me...

---

### Post by Rubi1200 on 2011-01-07
Hi,
the script results show that you only have Windows XP currently.

So, the root of the problem is the inability to boot the LiveCD to even get something installed.

I think it would be a good idea, since the regular CDs are not working for you, to try the Alternate CD.

This is a text-based installer, but fairly easy to use and I can walk you through the stages, especially the partitioning part.

You can find the download for the Alternate CD on the main download page (scroll down a bit to find it).

Then just burn it at the lowest speed to CD as you would do normally.

The other thing worth investigating, I think, are the settings in BIOS.

Look for, and try adjusting, things like AHCI compatibility, legacy keyboard settings and the like.

---

### Post by Paddy Landau on 2011-01-07
> **jaythedogg said:**
> ... what's with Lubuntu? I thought Xubuntu was for older systems?
Xubuntu is no longer as light as it used to be. In fact, on my old computer, I no longer find a significant difference between Ubuntu and Xubuntu.

[Lubuntu]("http://lubuntu.net/") is a new replacement that is very much lighter and faster. My old computer takes just one minute to boot into Lubuntu.

---

### Post by jaythedogg on 2011-01-07
> **Rubi1200 said:**
> Hi,
the script results show that you only have Windows XP currently.

So, the root of the problem is the inability to boot the LiveCD to even get something installed.

I think it would be a good idea, since the regular CDs are not working for you, to try the Alternate CD.

This is a text-based installer, but fairly easy to use and I can walk you through the stages, especially the partitioning part.

You can find the download for the Alternate CD on the main download page (scroll down a bit to find it).

Then just burn it at the lowest speed to CD as you would do normally.

The other thing worth investigating, I think, are the settings in BIOS.

Look for, and try adjusting, things like AHCI compatibility, legacy keyboard settings and the like.
What? I have booted from LiveCD, but then it fails after rebooting so many times. I had this PC wiped clean & tried to install Ubuntu & kept running in to the same problems, LiveCD or alternate text based!

Please check my previous post, as linked in my first post of this thread.

It isn't the installer, it is some kind of mystery conflict.

What didn't work would work, then stop working like it was a Borg or something adapting to new techniques & becoming immune!

I will check out Lubuntu, thank you to Paddy Landau, but I seriously think I may have to go to an older, more "current with my system's time frame" version of Linux. Any other user friendly distros that I can boot Live? I only ask because my CD burner is shot. I have to go use a friends & that is a PITA.
Please, let me know, thank you & I will post back with results from Lubuntu soon.

---

### Post by Paddy Landau on 2011-01-07
> **jaythedogg said:**
> What didn't work would work, then stop working like it was a Borg or something adapting to new techniques & becoming immune!
The only thing I can think of (as I said) is that there is a hardware incompatibility. I am presuming that you have a very old computer?

> **jaythedogg said:**
> I seriously think I may have to go to an older, more "current with my system's time frame" version of Linux.
Try [Puppy]("http://puppylinux.org/"). It is incredibly basic and very fast. Maybe, just maybe, it will work.

---

### Post by Rubi1200 on 2011-01-07
I looked at the post you linked to and this one; you ended up reinstalling Windows, so it is no surprise to find it there.

As far as the specifications are concerned, I see no reason why an install should fail in the way you describe it. 

Okay, so perhaps something like nomodeset and some other parameters were required. 

But, that should not have led to the situation you find yourself in.

There is one more possibility I can think of, but it is a wild guess and a shot in the dark.

Did you have any software installed in XP that uses FlexNet (a third-party software that writes to the MBR to protect software rights of other programs such as Adobe, Dell Data Safe and the like)?

Since you are in this position, and want to remove Windows completely as I understand, then take a look at this post:
[http://ubuntuforums.org/showthread.php?t=1661254](http://ubuntuforums.org/showthread.php?t=1661254)

In your case, I would try to just wipe the first 62 sectors as suggested, then try to install whichever version of Ubuntu and see what happens.

Extreme caution is required here and I recommend you make backups, but it might be worth a shot since it seems that something is preventing you from writing to the disk properly.

Maybe [dban]("http://www.dban.org/") is another option?

There are also plenty of other distros out there to try:
[http://distrowatch.com/](http://distrowatch.com/)

Some I can recommend include Puppy Linux, SliTaz, AntiX, Crunchbang, Linux Mint Debian Edition.

---

### Post by jaythedogg on 2011-01-07
Yeah, I cannot figure out what the compatibility issue is. Going to just learn & read until I figure it out. :)

---

### Post by Rubi1200 on 2011-01-07
Since you are experimenting with this anyway (to a certain extent), try a distro that is not Ubuntu-based. 

I have seen threads before where users tried everything to install one of the Ubuntu variants, failed, but were able to successfully boot and install something else (Debian, Slackware etc.). 

Might be worth trying.

---

### Post by jaythedogg on 2011-01-07
Okay, cool, will check it out after I try Lubuntu.

Question, what is most user friendly like Ubuntu? Maybe something that has an application center & built in wi-fi card support... If any come to mind.

Thanks :)

---

### Post by Rubi1200 on 2011-01-08
You could give Linux Mint Debian Edition a try; I found it to be pretty nice.

If you prefer something lighter, Crunchbang also comes to mind.

For more options:
[http://distrowatch.com/](http://distrowatch.com/)

---

### Post by jaythedogg on 2011-01-08
> **Rubi1200 said:**
> You could give Linux Mint Debian Edition a try; I found it to be pretty nice.

If you prefer something lighter, Crunchbang also comes to mind.

For more options:
[http://distrowatch.com/](http://distrowatch.com/)
Thank you, I will check it out. I tried a 10.10 Lubuntu LiveCD, wouldn't even boot from it... The computer sat at the black screen with a cursor for a while, then XP booted.

---

