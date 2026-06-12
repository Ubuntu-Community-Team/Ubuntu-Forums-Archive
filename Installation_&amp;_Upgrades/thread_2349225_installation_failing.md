---
title: "installation failing"
date: 2017-01-12
forum: Installation &amp; Upgrades
---

### Post by heatopher2 on 2017-01-12
Hello, I'm trying to install Ubuntu 16.04 alongside a Windows 7 partition, but no good so far. Ubuntu installs - can't see Windows. Windows installs - can't see Ubuntu. 

Sooooooo, I've tried the Boot Repair Disk off a USB, and the result is that I've only got Ubuntu now :~/ 

Oh dear. Please help me - redirecting if necessary to whatever is the correct place for this. Here is the URL of that pastebin thingy that the Boot Repair Disk produces:
[URL="http://paste.ubuntu.com/23786669/"]
http://paste.ubuntu.com/23786669/[/URL]

TIA,

Chris

---

### Post by yancek on 2017-01-12
Your boot repair output shows a windows partition on the first partition of the 240GB drive which also has your Ubuntu install.  You have the Grub code in the MBR pointing to the correct location of its files.  You also have the 3TB drive which has only windows partitions.  Is windows 7 on the first drive/partition?  Is the 3TB drive just data partitions?  The first partition on the first drive is the only windows partitions which shows boot files? The 3TB drive shows as using GPT.  Generally, when using GPT with windows, you need UEFI.  Not sure if that is necessary when the drive partitions are only for data.  Might be best to wait for someone with more experience with UEFI/GPT to reply.

---

### Post by heatopher2 on 2017-01-12
Hi, and thanks for replying. Yes, the 3TB partition is only for data. It's just an old-fashioned HDD, using GPT, as you said. 

Windows and Ubuntu are on the 240GB drive, which is an SSD. There's nothing wrong with the installation of either, as far as I can see, as they both work fine when I can actually get on to them! The problem is clearly about the boot sequence identifying the two loaders. I followed the instructions in this video, in order to try and get it right:

[https://www.youtube.com/watch?v=SOfnvbdWhrs](https://www.youtube.com/watch?v=SOfnvbdWhrs)

and then when that didn't work I followed one of the links on the discussion below the video which took me to the Boot Repair Disk download. I've tried to follow everything to the letter. Well confused now :~/

---

### Post by oldfred on 2017-01-12
You must have a newer UEFI system, but have both Windows & Ubuntu installed in the 35 year old BIOS/MBR configuration.

Better to boot Boot-Repair/Ubuntu installer in BIOS mode since Windows is BIOS.

Boot-Repair says you may have UEFI Secure boot on. Make sure in UEFI that is off as Windows 7 does not support UEFI Secure Boot.
Windows 7 can be installed in UEFI mode. But then that would be a total reinstall as Windows in UEFI must be on a gpt partitioned drive.

Boot-Repair's autofix will try to install grub to the MBR of every drive. But gpt drives have to have either a bios_grub partition for BIOS boot or an ESP - efi system partition for UEFI boot.

There may be an advantage to having grub on sdb and keep Windows boot loader on sda. Only slightly slower booting HDD as most of boot is still on SSD.
Then you can keep Windows boot loader on sda. Grub only boots working Windows, so when Windows typically breaks, you have to reinstall a Windows boot loader. Still better to have Windows repair flash drive however you are configurated. Boot-Repair really only fixed Linux systems and only can do a few minor repairs to Windows.

Turn off UEFI secure boot.
I would add a tiny 1 or 2MB unformatted partition on sdb and add bios_grub flag with gparted. And then see if booting from sdb works.
I would remove EasyBCD from Windows. That is just another boot menu and it uses the very old grub4dos to chain to grub. But it suggests installing grub2 to PBR or partition boot sector which is highly NOT recommended by grub.

---

### Post by heatopher2 on 2017-01-12
Oh, thanks for that very detailed reply! The truth is that I inherited this machine from a friend who is rather more tech-savvy than I am, and should understand your instructions better than I do right now. Because I'm finding all that quite hard to process right now!! :confused::lol::confused:

All this BIOS and GRUB stuff is "There Be Dragons" territory for me. Well, I know how to get into the BIOS, at least, and I know how to change the boot sequence, but that's about it. I'll have a look, however, and shall probably have to ask my friend to advise. But, really, thanks again :)

---

### Post by oldfred on 2017-01-12
Using gparted is similar to Windows own partitioning tool.

 Also links to more info
[http://gparted.org/documentation.php](http://gparted.org/documentation.php)
GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html) 

Usually better to use Windows partitioning tools to shrink NTFS, but use gparted to create the 1 or 2MB unformatted partition on sdb. And right click to see flags  and add bios_grub flag.

Then rerun Boot-Repair and it will install grub to sdb as well as sda. But in Boot-Repairs advanced mode you can select Windows and install a Windows type boot loader to sda.
Then in UEFI/BIOS set sdb as default boot drive.

Shows Boot-Repair's advanced screens:

 [https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by heatopher2 on 2017-01-12
Hi, and thanks again. I'm really only half-following, so like I said I'll have to ask my friend to help out here, because I'm not feeling too confident. However, I don't like to give up too easily, and so I have been rummaging around the BIOS a little bit, and found the advanced boot options. Here they are:

[ATTACH=CONFIG]273161[/ATTACH]

So I was wondering if changing this setting selected here (below) would conform to what you wrote earlier about turning UEFI off?

[ATTACH=CONFIG]273160[/ATTACH]

Or is there anything else there which would help?

---

### Post by oldfred on 2017-01-12
My Asus motherboard has similar settings.
And the UEFI or BIOS setting never let me boot in UEFI mode, only booted in BIOS.
So I changed everything to UEFI only.
It also looks like you have specific settings for USB and those are currently Legacy/CSM/BIOS.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

You can tell which way your are booting just by the first screen.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by heatopher2 on 2017-01-13
Hi, once again, thanks for the advice. I've been playing with gparted, and have some observations and questions. Apologies in advance if any of this is a bit stupid/basic. But like I said, I'm not very confident about any of this.

Firstly, here's the current state of sda, the SSD that the two OS's are on (plus the little swap partition in the middle):

[ATTACH=CONFIG]273188[/ATTACH]

Confused..... Why isn't there any sign of some kind of GRUB partition? I mean, I did use the [COLOR=#000000]Boot-Repair, and followed the instructions as best I could. And for that matter, why doesn't the Ubuntu install put that on, when I've told it that I want to be dual booting?

Anyway, whatever the answer is to all that...... Can I make a small space at the front of sda for a GRUB partition, like you (oldfred) advised me to do on sdb, the HDD? Or is that dangerous somehow?

[/COLOR]Next, here is sdb, the 3TB hard disk:

[ATTACH=CONFIG]273187[/ATTACH]

OK, so the first small partition on there is a Microsoft-only thing that I shouldn't touch, right?

In which case, I'm telling gparted to shrink the first of the data partitions, to make space for the GRUB partition, like you told me (I haven't actually executed on any of this, of course, as I'm a coward :-|):

[ATTACH=CONFIG]273186[/ATTACH]

.... and now creating the unformatted partition in the free space, as you (oldfred) told me, here:

[ATTACH=CONFIG]273185[/ATTACH]

Just tell me if I'm doing anything wrong, otherwise I'll assume that I'm OK here.

And then you said to right click on the new drive and put a [COLOR=#000000]bios_grub flag, but I can't do that:[/COLOR]

[ATTACH=CONFIG]273184[/ATTACH]

Is that because that's something that I do after installing the GRUB partition with [COLOR=#000000]Boot-Repair?

I think that's it for now. TIA [/COLOR]:D

---

### Post by oldfred on 2017-01-13
Always best to shrink from end of partition as that goes quickly, if you shrink or move beginning of a partition, it has to copy all data and depending on size & amount of data can take a very long time, never interupt gparted when it is doing something. And a power failure or shutdown in the middle corrupts data.
Not sure why you cannot add bios_grub flag.
I might run the updates by clicking on the check in gparted's top panel. Then see if you can add flag.

You did use Windows to partition & format your sdb, as it always adds the unformatted system reserved partition for its use. Windows always wants that before any NTFS partition on a gpt drive.
Somewhat like grub's bios_grub partition, but Windows uses it for enryption or serial numbers and other things it does not want users to see.

---

### Post by heatopher2 on 2017-01-13
[COLOR=#000000]OK, I understand that. So can I put that little partition right at the very very end of the disk, i.e. after the really big partition? Just because I suppose it's possible that I'll have to resize drives at some time or other.

And secondly, you didn't actually answer these questions at the beginning, about the SSD, quoted here (I'm not really worried about the safety of the Windows partition, as I've got it backed up fine):

[/COLOR][INDENT][COLOR=#000000]Confused..... Why isn't there any sign of some kind of GRUB partition? I mean, I did use the [/COLOR][COLOR=#000000][COLOR=#000000]Boot-Repair, and followed the instructions as best I could. And for that matter, why doesn't the Ubuntu install put that on, when I've told it that I want to be dual booting?

Anyway, whatever the answer is to all that...... Can I make a small space at the front of sda for a GRUB partition, like you (oldfred) advised me to do on sdb, the HDD? Or is that dangerous somehow?[/COLOR][/COLOR][/INDENT]

---

### Post by oldfred on 2017-01-13
Boot-Repair does not create partitions, only reinstall or repair grub. You are supposed to have correct partitions on drive.

Normally best to add both ESP & bios_grub at beginning of drive when first partitioning it.
UEFI suggests ESP should be at beginning of drive, but Windows typically makes it second or third partition. And a few users have put it at the end of smaller drives. Not sure if ESP would work with new multi-TB drives.
But grub says it will find a bios_grub anywhere on drive, so you can just shrink anyone of your NTFS partitions by 1 or 2MB and add the bios_grub there.
Then use Boot-Repair to reinstall all of grub.

---

### Post by heatopher2 on 2017-01-13
OK, I think I'm understanding a bit now..... and how big should an ESP partition be?

---

### Post by oldfred on 2017-01-13
The ESP is for the .efi boot files. 
Windows makes it 100MB which even works for most dual boot installs.
But if you later want to add other installs or use some other UEFI features it is better to make it larger as increasing size of first partition after drive has lots of data can be difficult.
I typically use/suggest 300 to 500MB. But on my 32GB or 64GB flash drives use the 100MB. If drive is larger then using an extra 100 or 200MB does not waste much space on a TB sized drive.

---

### Post by heatopher2 on 2017-01-14
Hello. I'm not done here yet, I'm afraid :( Getting a bit tired, and annoyed that it's not made at least a *little* bit easier for the layman, but really, I am quite determined to get this working.

So, I made that grub partition on sdb. As you suggested, once that was done I was able to mark it with the grub-bios flag. And then I went back to the Boot-Repair. Here's what I put on the main options:

[ATTACH=CONFIG]273205[/ATTACH]

Anything wrong there?

Next, the grub location tab. GRUB on sdb, and having Windows as the default OS (obviously, I'm used to Windows, but I dooooo really want to get used to LInux too):

[ATTACH=CONFIG]273204[/ATTACH]

Anything wrong with that?

OK, and then there are a load of extra options, which I of course don't have any idea about, so I've left them blank. Anything I should change there?

[ATTACH=CONFIG]273208[/ATTACH]

OK, so then I ran the install, and when it came to asking where I wanted to put the grub files, I did this:

[ATTACH=CONFIG]273206[/ATTACH]

Correct?

And that was that............ And then when I restarted, booting off sdb, I got a purple screen (BIOS?), with only Ubuntu options (I took a picture of that, but the site won't let me upload it for some reason). No sign of Windows :icon_frown: 

What was worse was that when I reverted to sda for booting, I got *this*, and had to reinstall Windows: 

[ATTACH=CONFIG]273207[/ATTACH]

... which is only annoying and time-consuming, rather than utterly devastating, as I do have it all backed up. Buuuuut, really, shouldn't it all be a little bit easier than this????

I can't even tell if this has anything to do with the UEFI stuff. I've looked in the BIOS for this UEFI Secure boot, but can't find that, and not sure that it's even relevant to what's going on with grub. Please enlighten me. I'm starting to get a bit frustrated! #-o

TIA

Oh, here's the log file, or whatever you call it. Is it any different from the previous one? I wouldn't have a clue where to look!

[http://paste.ubuntu.com/23795438/](http://paste.ubuntu.com/23795438/)

---

### Post by oldfred on 2017-01-14
I do not understand why you had to reinstall Windows?
If booting from sda it should work, or if issues use f8 for repair console, and if that does not work use your Windows repair flash drive or installer's repair console.

Install on sdb looks ok, now.
But it said network error, so did it really reinstall grub or error out.
When doing total reinstall of grub, you have to have Internet working as it down loads new copy of grub. Best to use hardwired, not wifi for installs & major updates.

You did boot installer in UEFI mode. Since both installs are BIOS, best to use BIOS mode.

If you boot sdb from UEFI/BIOS what happens?

---

### Post by heatopher2 on 2017-01-14
Hi , thanks for replying, as ever. I thought you might be off for the weekend! I can't tell you what happened with Windows. That was weird. I promise that I didn't do *anything* to sda! (unless the boot repair did something, but there was nothing in the settings that I put, was there?) I just switched the boot option back to sda after getting only Ubuntu off sdb, and got that screen of death :eek:

Not sure about the network error. If it was producing the online report I obviously must have had the PC hardwire-plugged into the router (the wifi is off a usb dongle, so obviously no good in such a bare-bones mode). 

Well, as you know by now, all this is quite a long way outside my comfort zone, so I'm going to take a time-out just now, and come back to your suggestions later tonight or tomorrow. I do like problem-solving, though, so I'm NOT giving up :D

---

### Post by heatopher2 on 2017-01-15
Hi, I just wanted to let you know that this is sorted now, and thank you for your help.  After a lot of messing around, it was all about the UEFI vs Legacy issue. Once I'd got everything set on BIOS it was OK. One weird thing is that despite telling the wizard that I wanted Windows to be the default system from grub, but having double-checked on that several times, it definitely doesn't work. Ubuntu clings jealously to its default status. But that's fine. In fact, this kind of works out nicely, because if I set sda as the boot drive I get Windows, and if I set sdb I get Ubuntu (or Windows). Not too bad.

Now I've got another question, of course, but maybe it doesn't belong on this forum, and anyway I'm OK to leave it for a day or two! Thanks very much again, and all the best :D

---

