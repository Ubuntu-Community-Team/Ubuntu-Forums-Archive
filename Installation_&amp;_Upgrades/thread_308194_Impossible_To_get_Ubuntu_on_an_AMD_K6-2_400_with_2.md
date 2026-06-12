---
title: "Impossible? To get Ubuntu on an AMD K6-2 400 with 288Mb RAM??"
date: 2006-11-27
forum: Installation &amp; Upgrades
---

### Post by OzzyFrank on 2006-11-27
Hi all. This is my first post, but have been visiting here reading all your pearls of wisdom since taking the dive and installing Ubuntu a couple weeks back. OK, it got onto my P4 3Ghz PC quite easily, and runs a breeze... which led me to believe it would be the perfect OS for my other PC, running an AMD K6-2 400Mhz, with 288Mb of RAM. I mean, it runs Windows ME really well, and has even had XP on another drive (obviously ran slower than ME). So, with all this talk of Linux being able to run on ANY pc and BETTER than "Windoze", i gotta say I was mighty surprised (and somewhat disappointed) that I not only couldn't install Ubuntu, but the easier-on-resourses Xubuntu either. OK, have read about "alternate install" CDs so am downloading the one for Xubuntu now, but I doubt it will do anything, as the issue that halts both installs is an apparent lack of maths coprocessor. Now, i thought my chip had one built in, though never actually thought about this before, since Windows never complained. But apparently Ubuntu/Xubuntu needs one... or maths coprocessor emulation.

What I would like to know is if there is a workaround for this chip (or problem in general), or is there an emulator i can run before/during install so I can just get on with it. The install seems to suggest it would continue if it had emulation.

Please note I have indeed tried diffrent "boot options" I have found here and elsewhere via F6 at install menu, to no avail. I always get the "disabling IRQ#15" messages then "soft lockup" error at the end (except one time when I also used options like "noirqdebug=1" "acpi=noirq" & "pci=routeirq" and it did get further, but halted at a Xubuntu screen whre it let me press a key to reboot).

Any suggestions? Or is this PC simply too old for Linux, though it runs Windows ME and XP??

Many thanks in advance!

OzzyFrank

---

### Post by Randy R on 2006-11-27
Not impossible. I have 6.06 installed on mine and it works fine.

What motherboard do you have?

What chip set do you have?

Can you be more specific, what exactly is happening? Are there any error messages?

---

### Post by CyberX on 2006-11-28
Hi.
That's very odd because the K6-2 HAS a math coprocessor inside.
I'm using a K6-2/366 MHz in a Edgy (6.10) server with only 64 MB of memory.
I used the Alternate CD (command line only), so I'm pretty sure it will work with your K6 with 288 MB.

Perhaps you have a conflicting device. What's your motherboard and what devices do you have (both PCI/ISA cards and onboard devices enabled in the BIOS)?

---

### Post by OzzyFrank on 2006-11-28
Hiya

OK, I have a Gigabyte MB GA-5AA-T99 (ALADDIN5) running an AMD K6-2 400 with 288Mb RAM. I'll have to check what chipset, and what cards I have in (pretty much just a 2Mb Diamond Stealth graphics card, a parallel port card, and old Creative sound card (Vibra?)... oh and a USB card, as it didn't have USB).

Since error messages mention irq15, I looked up in the BIOS, but all it has was to choose either PnP/PCI or ISA/EISA (can't disable them in the bios by the looks of it). Looking in windows it seems to be the secondary ide (dual fifo or something?).

Error message I get when i just try to run the live cd for both Ubuntu and Xubuntu, and also the alternate install cd for Xubuntu (though not with command line, as I am a total newbie and have no idea what to input) is:

[  178.014501] irq 15: nobody cared (try booting with the "irqpoll" option)
[  178.015154] handlers:
[  178.015200] [<c02528e0>] (ide_intr+0x0/0x1f0)
[  178.015321] [<d28b7830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  178.015499] Disabling IRQ #15
[  238.637574] irq 15: nobody cared (try booting with the "irqpoll" option)
[  238.638194] handlers:
[  238.638240] [<c02528e0>] (ide_intr+0x0/0x1f0)
[  238.638362] [<d28b7830>] (usb_hcd_irq+0x0/0x60 [usbcore])
[  238.638537] Disabling IRQ #15
[  307.848210] BUG: soft lockup detected on CPU#0!


When i have tried different suggested boot options, I have gotten seemingly further as mentioned before, but end up with something like "Giving up. No maths co-processor or emulation found" (I'd have to try to recreate those instances to record the error messages in detail).

Anyway, as far as I know, my CPU is fine, and have seen quite a few people complain that similar PCs running Windows have had this error when trying to install Ubuntu (and other Linux distros).

For the record, I really like Ubuntu, but I'll have to stop trying to convert friends with slower PCs until I get this solved, hehe.

If there is any other specific info you think could help solve this, please let me know. Also, since i have the Xubuntu alternate CD, could anyone offer me tips on installing via command line (if you think that would help). I'm willing to give anything a try. Cheers

OzzyFrank

---

### Post by gjtoth on 2006-11-28
How is your BIOS setup?  Try running in the "failsafe" mode and see what happens.

---

### Post by CyberX on 2006-11-28
If this is your motherboard
[http://europe.giga-byte.com/FileList/Manual/motherboard_manual_5aa_3201_e.pdf]("http://europe.giga-byte.com/FileList/Manual/motherboard_manual_5aa_3201_e.pdf")
then you have an Aladdin ALI M1542 Chipset. But the manual says the maximum memory it supports is 256 MB, I don't know if that might be a problem or just an outdated manual.

It's just a guess, but you might try to boot without the Sound Card and the USB Card, and force the BIOS to clear the PNP/PCI configuration to see if it works.

---

### Post by RJARRRPCGP on 2006-11-28
> **OzzyFrank said:**
> AMD K6-2 400Mhz, with 288Mb of RAM. I mean, it runs Windows ME really well, and has even had XP on another drive (obviously ran slower than ME). So, with all this talk of Linux being able to run on ANY pc and BETTER than "Windoze", i gotta say I was mighty surprised (and somewhat disappointed) that I not only couldn't install Ubuntu, but the easier-on-resourses Xubuntu either. OK, have read about "alternate install" CDs so am downloading the one for Xubuntu now, but I doubt it will do anything, as the issue that halts both installs is an apparent lack of maths coprocessor. Now, i thought my chip had one built in, though never actually thought about this before, since Windows never complained. But apparently Ubuntu/Xubuntu needs one... or maths coprocessor emulation.


The K6-2 has a math coprocessor, thus that error message is bogus! 

The K6-2 is the equivalent of 686. It shall at least complete the installation and continue to run.

Math coprocessors have been integrated since 486DX! 

Unless you were trying to install it on a 486SX or earlier, you shall NEVER get that error message!

I NEVER saw any error message about the math coprocessor being missing for YEARS! 
That error message is SO old school.

---

### Post by Ruscit on 2006-11-28
I had the same problem, I couldnt install on two K-6-2, one 400mhz on a VIA chip, another 500 on a ALI chip. I used Xubuntu alternate. Kept giving errors like unable to mount root fs and stuff. Boot options didnt help.
So what I did was pull the HDs out and put them in a Celeron 333 machine installing there, then sticking them in the respective K6s

---

### Post by OzzyFrank on 2006-11-28
Hi. OK, yes, that error message is old school, but happening nonetheless. As for RAM, i had 256 in there when all this drama began, than found another 32Mb and stuck that in to see if it helped. As far as I can see, the MB supports 288 Mb RAM, and if i remember correctly it could support 512.

OK, the suggestion to use Failsafe in BIOS (or equivalent, which was load original defaults) did help. I now no longer get the "disbaling irq #15" or "no maths coprocessor found" messages in Ubuntu or Xubuntu (live install CDs with no F6 boot options)... the progress meter under the logo gets past bouncing back and foward, and crawls to the end... logo disappears and you get that small flashing cursor in the top left... then the monitor seems to go into hibernation/power saving mode, then switches off. The CD drive continues to be accessed for another minute or two, then everything ceases altogether, and the screen is dead till reboot. Have left it for many minutes, just in case, but no change.

Is this time to start using the CDs with boot options, and if so, which boot options? Or do I use the alternate CD, and if so, which install option? (If 'command line", I'd need to know what to input, as my head is still in DOS).

Also, any ideas what could have been preventing it getting this far in the BIOS? I never messed with chipset features, and there was certainly no "Disable Maths Coprocessor" option, hehe!

As for booting without the sound and USB card... I'd really like to leave that as a last option (unless you mean boot once without them, and go into BIOS to save the changes... but I think the bios reset fixed that IRQ issue).

Many thanks to all you guys for your help.

OzzyFrank

---

### Post by CyberX on 2006-11-28
Yes, BIOS failsafe seems to, somehow, reordered your IRQ's.

To be honest, I never used the Ubuntu "normal" CD with the K6-2, because I don't have enough memory in my server (I suspect that even 256 MB are not enough with anyhing older than a P3). I always used the Alternate CD, it needs only 48 MB and it's a lot more faster (and, although it's not a graphical installation, it's not dificult).

You could try adding these options with F6:
```
acpi=off noapic nolapic vga=771
```

(vga=771 is 800x600x256 colors, just in case you have a strange VGA/Display combination)

---

### Post by OzzyFrank on 2006-11-28
Hi all. OK, those last suggested boot options brought back the "no coprocessor or maths emulation" message, so tried the Xubuntu Alternate CD again, now that my BIOS settings have changed. I used the text install, worked around getting it to finally want to install into the ext2 partition i already had created, then set up some user options (and name + password etc).

However, during "Install the base system" it halts with this:

[!!] Install the base system
     Debootstrapwarning
Warning:
file:///cdrom/pool/main/o/openssl/libssl0.9.8_0.9.8b-2ubuntu2_i386.deb was corrupt.


I get this for every file it looks for, or at least a big whack of DEB files. It then ends with:

[!!] Install the base system
     Debootstrapwarning
Warning: Failure trying to run: chroot/target mount -t proc proc /proc

I try to install the base system, going over the previous attempt, and it is still the same thing. As far as i know, the CD is fine, or at least the ISO i downloaded burned to a CD without an error messages. Is this indeed a corrupt CD image, or am I doing something wrong? The CD drive is also fine, as I removed the fastest drive out of my main PC for this (and the install accesses the CD fine up till this point).

Any suggestions? I thought i was so close... hehe...

OzzyFrank

---

### Post by OzzyFrank on 2006-11-29
Hi once again

Boy, am I glad I didn't hit Submit on the lengthy SUCCESS! post I typed up during the install... as while i indeed look promising, and did in fact finish, I am at a black screen rather than a desktop! What I did since the last post are as follows.

First off, the Xubuntu "alternate" CD was indeed corrupt, as I burned a 2nd copy after getting an error message after burning the ISO initially, then promptly mixed them up (in my defence, besides the fact I was busy as hell with fruit jerky orders, RecordNow DX has given me a few "false" messages about CD failing while writing the lead out [they've all worked fine], which is why i kept the first one). The CD seems to work just fine, but obviously the DEBs are corrupt. This of course has nothing to do with the Live CDs of Ubuntu and Xubuntu not working, just why the Xubuntu alternate install halted after resetting the BIOS (it too didnt get futher than the others before that).

I started the install again, wiped the partition and started afresh, and the base install went in, then the software was all unpacked, installed and configured... and then the CD was ejected, we rebooted, and ended up at the GRUB menu.

So, to get to this point, the answer for me and I guess many similar PCs is to revert to original BIOS settings, then use the text-based install from an alternate CD (that isn't corrupt!).

But while the install ended without hiccup this time, upon loading Xubuntu (just the first option of generic Ubuntu kernel), it tells me it has activated the swap [ok], then checking root file system [ok], then checking file systems [ok], then after this the screen just goes black. I even unhooked my new 21" monitor and plugged that in, but no difference.

I then left that monitor in and tried to repair the broken install, but got to a stage i was out of my depth. So i did the lengthy install from scratch, and ended up with a hassle-free install, the swap, root and file systems being recognised, but then a black screen. So it wasn't the monitor, and the video card works fine till that point (Diamond Stealth 2Mb; the install correctly picks up the available resolutions of 640x480, 800x600 & 1024x768, so I have no idea what the problem can be!)

Any suggestions what could possibly be going wrong now?

OzzyFrank

---

### Post by OzzyFrank on 2006-11-29
Update: When the screen dies, there is some further disk activity for a few seconds, then nothing. I have of course waited to see if anything happens after a lengthy period. So i began to suspect I was at the login, just couldn't see it... so entered my username, then password, and got at least 20 seconds of disk activity. Would I be right in assuming I am in fact getting to the login and then to the desktop, but something has messed with the display? I have disabled power management in BIOS to no effect. And sometimes the monitor just goes into standby, other times totally off (the 21" goes into standby or stays lit but a weird brown). I have seen this in other posts, so know I am not the only one this is happening to (but no one else I saw tried to login and see if any disk activity resulted). Oh, the joy.

---

### Post by CyberX on 2006-11-29
Hi.

You can test it pressing Ctrl+Alt+F1 (or F2 or... F6). If you get a text-mode terminal, then indeed there's something wrong with your display setup.

---

### Post by Step on 2006-11-29
> **CyberX said:**
> Hi.

You can test it pressing Ctrl+Alt+F1 (or F2 or... F6). If you get a text-mode terminal, then indeed there's something wrong with your display setup.


Yeah CyberX is right F7 is your GUI, first see if the tty's are working properly. You will have to setup your display server manually if it's working. I had the same problem with Ubuntu 6.06 and 6.10 on a AGP Nvidia GeForce 6800GT with a Philips 170C monitor.:neutral: 

There are plenty of threads and HowTo's how to get your display server working. Good luck!

---

### Post by OzzyFrank on 2006-11-29
OK, first I should explain that not only am i a newbie to Ubuntu, but this is my first go at any Linux... so i have no idea about tty's and what to do with them, etc, hehe. So I just tried the function keys listed at intervals, and got nowhere. While it is checking the file system I assume i shouldnt be trying to do anything anyway, but tried the listed keys and just got stuff like [[[18~ and it didn't interrupt anything. Then of course the screen dies and I can't see anything anyway. Nothing turns the screen back on but a reboot.

Then it checks the drives, tells me I didn't unmount properly the last time (well, hard to do that while totally blind), says it will reboot, checks the drives when back again, all is ok with the system... goodnight display. If setting up the display server is something that can be done while I can still see the screen, I might look into it. Then again, I might not... it's sort of like going back to inputting data with punch cards.

I am just glad I haven't gone on about Ubuntu to too many people. And I'll keep those install CDs to myself, since I don't need people cursing me, hehe. Yeah, sure, it got on my P4 fine and it initially impressed me, but after this I have to admit I am staggered to realise just how good Windows is (at setting itself up with the available hardware; as i said earlier, Ubuntu picked the correct display setting during install - the same as what is available to me in Windows - but turns off the display as it gets to logon).

The purpose of all this is (besides getting Ubuntu on this old PC for my kids to use) is that basically I was ready to start installing this as a second option on as many friends' PCs as possible (I have no great love for the Windows® empire monopoly!). But many of my friends were Luddites till I got them online, and those P2s and K6-2s are still fine for their modest needs (email and Google search). And while Windows ME installs easily and runs wonderfully on these machines, I can't subject my friends to this. While it's a pain, for me it's also a challenge, but for them it would be an absolute nightmare, and they would become instant Linux-haters.

I'm still willing to give "the other half" of the computing world a shot. As for the AMD K6-2 machine, i might decide to waste some more of my time on it, or just give it back to Microsoft, hehe.

Thanks once again all. Any more suggestions always welcome (just remember I don't have a screen past a certain point in the boot sequence).

OzzyFrank

---

### Post by az on 2006-11-29
I would suggest you boot into memtest86 and see what happens.

---

### Post by OzzyFrank on 2006-12-01
Hi all

I've finally gotten to the Xubuntu desktop, so will recap some things in this summary that are mentioned below, for those who get here via a web search (I found many of my questions already answered in forums, but sometimes had to scroll through the tidbits [& chit-chat]).

OK, an AMD K-6 400Mhz could not run Ubuntu/Xubuntu live cds with 256 Mb RAM, so i put in a 32Mb chip to make the total 288Mb... still no go. I would be told quite emphatically that I had no maths coprocessor or emulation, which is of course rubbish. I tried every conceivable boot option via F6, and some would get me a little further, seemingly, then die at the same error (some of the boot options actually made it die instantly, not a few seconds later).

As per suggestions, I downloaded the "alternate" install CD of Xubuntu, and used the "text install". With this, I could indeed finish the installation, and the CD would eject, and I would reboot to the GRUB menu, then the drives and file systems would be checked and be listed as [ok]... then the screen would turn off, with no way to get it back than a reboot!

I had suggestions i needed to configure the display server, but realised this would be hard to do with a dead monitor, so thought I better keep looking for the answer.

So, as per the suggestion to run memtest86+, I tested my memory and one of my 128Mb chips had one small defect (which Windows could handle, but reading around it seems even one messed up memory address can totally kill Linux).

OK, down from 288 to 160Mb of RAM, but no faults... and still a dead screen. OK, reinstall #5... still a dead screen. But hey, since i removed the faulty ram, let's see if the Live CDs work... yes, with 160Mb of RAM i can run both the Ubuntu and Xubuntu live cds! Only one thing left, so I looked for a crappy old video card to replace the 2Mb Diamond Stealth, which funnily enough gives me a screen DURING the install.

After sticking in an S3 card, I rebooted and got further, but it was Xserver asking me for input about the changed display, so I just did another reinstall, then FINALLY ended up at a VISIBLE login screen (I figured I had been getting there anyway, just couldn't see it, after one time trying my username and password and getting a bunch of disk activity).

So, my suggestion is that if you are trying to run a live CD to no effect, and people reckon your PC and amount of RAM etc are surely enough, then do a memory test (and if one comes up faulty, isolate which one and remove it promptly, even if it never bothered you in Windows!). If you get through the install and then your screen disappears just before the login screen, exchange your graphics card for one that Linux likes better. Both cards I tried were based on S3, but seems Ubuntu likes the cheaper one (I would have thought the Diamond Stealth would be supported since it was an expensive and popular card in its day).

Many thanks to you all for your input; catch you again in the forums.

OzzyFrank

---

### Post by Tomachu on 2006-12-03
i would've suggested trying to boot/install with "irqpoll" as an option like your log suggested. i had that weird hd mounting and cd-rom reading problem too on my trusty p c433/ati rage pro turbo w/256mb. after irqpoll it ran perfectly :)

- tomi

---

### Post by RJARRRPCGP on 2006-12-03
Also, the math coprocessor is IRQ 13, AFAIK.

IRQ 15 is the secondary IDE port, AFAIK.

---

### Post by OzzyFrank on 2006-12-04
Hehe... the first thing I tried was the "irqpoll" option, since I'm new to Linux so figured their recommendation might fix things. Like I said previously, EVERY boot option I found in forums etc, and every combination of them, was given a go, to no avail. As you can see, I ended up finding the answer myself. Thanks to everyone for their help. OzzyFrank

---

