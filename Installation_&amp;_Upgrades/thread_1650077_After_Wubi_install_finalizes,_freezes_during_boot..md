---
title: "After Wubi install finalizes, freezes during boot."
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by jaythedogg on 2010-12-21
Hi all, semi-linux noob here, played with Red Hat 7.3 *a lil* back when it was fresh, have played with a working Wubi install of Ubuntu 10.10 & a dual-boot Ubuntu 10.10 Netbook Remix on an eeePC (Both installs done by me.)

So now I am playing with a computer that I literally found sitting on the side of the road. I mean, I drove by, double take happened, then went back & picked it up, along with one almost identical to it keeping it company.

Here are the basic specs:
WinXP Pro SP2 (Version 2002)
Pentium 4 CPU 1.80 GHz, 1.79 GHz (What?)
512MB of RAM (PC100 I believe, although could be 133)
GeForce2 MX 100/200 AGP 32MB DDR
Generic PS2 Mouse & Keyboard.
Standard CRT monitor.

Okay, for anyone that is willing to help this semi noob, I am frustrated beyond compare right now.
I used Wubi to install Ubuntu 10.10 (via the downloader) with a 10GB partition. Everything went according to plan, PC reboots, boot loader appears, select Ubuntu, it finalizes the install while I watch the slide show & then reboots again.
I select Ubuntu, the CD-Rom spins up & keeps spinning, computer is now unresponsive (no keyboard, mouse, black screen) right after the cursor blinking in the upper left goes from larger, to smaller (resolution change?).
I shut it down, reboot & remove the CD in the drive (Math Blaster install for my kids...). Great, now it gets to the Ubuntu Splash screen & freezes... Okay... Hard reboot time again (nothing works, keyboard is unresponsive, it sat for some time as well.)
I try again, freezes at the black screen just after the cursor transition, & before the Ubuntu Splash screen.
Okay, try rebooting & select the second option after selecting Ubuntu, Debug mode I believe? Anyway, I watch all of the text scroll by far too quickly to comprehend, which reminds me to watch Matrix again, & it gets to the same black screen following the cursor transition & it freezes after this phrase is on the screen:
skip stopping firewall: ufw (not enabled)
Still no keyboard response, no mouse, etc.
*Bang head on desk*
Moving on.
Searched the internet & the only thing I can think of is to try to ctrl+Alt+F1 & reboot X Server... Yeah, if the keyboard remained responsive long enough.
So I figure maybe I got a bad download, gonna try again & use the 10.04 version from the Ubuntu website.
I downloaded it & used a fresh download of Wubi (after uninstalling the previous install per the directions) to start the installation process.
Everything went as before, smoothly & then back to the freezing again & here I am.
I am going to bed & hoping that some kind guru can help me out, that would be great.(or someone that has shared the same experience, although finding the old PC on the side of the road isn't really necessary to have this experience I suppose... Did I mention how incredibly clean the PC was inside?)


Don't mind the apparent ADD & sleep deprivation induced ramblings, please, I am merely frustrated... And tired... And mildly ADD.

Also, what is up with the system properties listing the CPU like I have a dual core (2 logical processors) but the device manager saying I have only one, & AFAIK Pentium 4 only came in single core... How's that for a head scratcher?

Besides the point.

I figured, heck if this machine runs Windows XP pro just fine, it should do Ubuntu fine, seeing as this XP box won't play Hedgewars(.org) above 7 FPS with everything bottomed out & dumbed down... Maybe Ubuntu will breath new life in to it & allow the hardware to run a tad better, which was the initial reason for my wanting Ubuntu on this machine, to make it run with more vigor. :) Well, & so I can play Hedgewars on it.

Any help out there?

/zzzzz

Edit: One final thing, I tried chkdsk /r in the Run command from Windows, rebooted & it came back clean.
Edit #2: I am currently posting from said machine using Google Chrome, should anyone wonder... Why, I don't know, but maybe some reader out there is tired & has ADD as well.

---

### Post by theasprint on 2010-12-21
Hi,

Maybe a few problems.

1. Seeing that your PC is kinda old, maybe you want to try the Alternate version of Ubuntu?
The Alternate version of Ubuntu is not like the normal LiveCD version. The Alternate version has more support for low-end PCs because it does not have GUI.

2. Also you may want to try checking your MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. If you want better guidance, here's a nice guide: [http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

Good Luck.

---

### Post by jaythedogg on 2010-12-21
> **theasprint said:**
> Hi,

Maybe a few problems.

1. Seeing that your PC is kinda old, maybe you want to try the Alternate version of Ubuntu?
The Alternate version of Ubuntu is not like the normal LiveCD version. The Alternate version has more support for low-end PCs because it does not have GUI.

2. Also you may want to try checking your MD5SUM: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

3. If you want better guidance, here's a nice guide: [http://ubuntuforums.org/showthread.php?t=1649050](http://ubuntuforums.org/showthread.php?t=1649050)

Good Luck.

Thanks, I am going to try creating an install CD with the alternate version of 10.10, but is it possible/advisable to install that alternate version using Wubi?

For simplicity anyway?

---

### Post by theasprint on 2010-12-21
Hi,

Nope, not much recommended. I am also not sure if its possible to install Alternate Wubi version.

Just go and follow the guide I gave you earlier, with the Alternate .iso file.

And if there's no need to use WIN XP, then just remove it! Its an old OS.

* I managed to get Win 7 running on a Dell Inspiron 700M laptop. Quite an antique.

---

### Post by jaythedogg on 2010-12-21
> **theasprint said:**
> Hi,

Nope, not much recommended. I am also not sure if its possible to install Alternate Wubi version.

Just go and follow the guide I gave you earlier, with the Alternate .iso file.

And if there's no need to use WIN XP, then just remove it! Its an old OS.

* I managed to get Win 7 running on a Dell Inspiron 700M laptop. Quite an antique.

Will do, thank you. As far as getting rid of WinXP, yes, eventually. And for Win7 on that ancient Dell... Wow.

Now if you could get Windows 7 to run on an Amiga 500.... But we are only humans.

:)

---

### Post by jaythedogg on 2010-12-25
Okay, update!

I finally got around to burning a copy of 10.10 alternate i386. I started installing last night about 11pm Central. I just now got back on the computer.

No, not because of sleep, because it wouldn't boot Windows or Ubuntu, it wouldn't even load Grub at first.

Here is the chain of events in list form:

1- Put in the disc, rebooted PC from XP Pro sp3.
2- Installed Ubuntu 10.10 Alt using recommended settings/partition
3- Reboot, starts with: No device found (or something) & grub recovery:
4- Reboot a few times, same effect, reinstall Ubuntu
5- Try it with a new partition next to other install.
6- Reboot PC, now grub works, one XP & two Ubuntu options.
7- Ubuntu gets to splash (loading screen, says Ubuntu & has dots to indicate load progress) then freezes.
8- Reboot into recovery mode. Freezes after saying something about hard disk with some path/file not ready hit M for something or wait... Then freezes.
9- Put Ubuntu disc back in, attempt repair, no help.
10- Use disc again, check integrity, disc is fine, do rescue, no avail.
11- Completely format drives (two in RAID, first is 40 GB then a 20.5 GB) Reinstall using FULL 40GB Windows went bye bye.
(Note, couldn't load Windows through grub at any point either)
12- Changed out AGP Geforce2 MX 100/200 32MB for PCI Geforce2 128MB & changed BIOS accordingly. (In case it was a bad AGP driver?)
13- Same problem, would freeze at cursor (single cursor in upper left, black screen), recovery mode produced same results as #8 in this list.
14- Wipe & reinstall, this time to 20.5 GB drive in hopes that it was 40 GB that went bad.
15-Reboot PC, no grub, just "Hard Disk Error" in upper left, black screen
16- Yanked both drives, the master connector on my ribbon cable was coming off, reattached & used slave connector on my other spare drive, 160 GB Maxtor IDE. (Slave is master if no second drive present) - Note that the previous drives were set to primary & slave via jumper, so I set my 160 GB as master from cable select via jumper.
17- Reinstalled Ubuntu after clean wipe using the partition tool on the disc. Basic settings, use entire disk for partitions.
18- Reboot & fail. It got to the cursor going from large to small (assuming graphics software loaded & resolution changes?) & freeze.
Tried again, same problem.
19- Reboot in to recovery mode via grub & I got a menu... YAY! First time I have seen it so I almost dropped my Amp (energy) on my keyboard! (Okay, not really...)
20- Didn't know what to do so I figured it could only be (out of the list) a graphics issue, going from text based to GUI, chose the low graphics option this one time & it got me here....

Okay, now it seems as though it is a graphics issue... What do I do to fix it & thus possibly allow me to reboot (because I am afraid to reboot & not have a working computer again!) & get on with my new life as an Ubuntu user / linux student?

Any help is greatly appreciated, thanks in advance!

---

### Post by jaythedogg on 2010-12-25
Okay, oddly enough, Ubuntu updated, like 210MB, so it required restart. I said goodbye to my GUI desktop & on a whim, hit restart.
Here is the expected outcome. Nothing. Back to freezing at boot, black screen with a cursor after resolution change.
Here is the odd part, I took the GeForce 4 MX 4000 64MB PCI card out & put in this large, no heat sink, wide, looks like Win98 compatible "Multimedia diamond 64MB DRAM" card... On a whim & powered the computer up... Guess what? It runs just fine, but in 800x600.
Note: Grub2 (update to grub, I think it is grub) doesn't show up, I don't have a boot loader now, just straight to the black screen with a cursor for loading.
I am going to attempt to go download the linux drivers for the GeForce 4 MX 4000 card I have, figure out how to install them & shut down, switch back & see if it will boot with that card.
If not, I will replace it with this ancient, yet wonderfully working, booger I have in here now & see if it *chooses* to boot.

Hopefully someone out there will benefit from my problem here, it is a learning opportunity I am in the midst of, without a teacher, or even a tutor for that matter. Must be too early in the AM.

---

### Post by jaythedogg on 2010-12-25
Okay, I don't think it is the graphics drivers. I tried rebooting without installing a driver & the old card I had in it wouldn't boot, it would hang like my failed attempts above.
So I tried going back to my GeForce 4 MX 4000, fail. Back to old school card, fail & got as far in recovery as to get some message about nouveau not recognising the CHIP. I am baffled here, as it worked last time the system booted.
So I switched it back to the GeForce 4 MX 4000, tried booting recovery, fail. Tried regular boot, fail. Tried recovery again & it went through & allowed me to use the recovery options list....

I don't think I need to select "use failsafe graphics" to get it to finish booting from there, as from that point I am pretty much in to GUI, I click continue & use it this time only, then it goes straight to login...

Please, I implore you, oh Ubuntu gurus, ease my screaming chipsets & tell me what to do!

I honestly can't figure it out.

Thanks.

---

