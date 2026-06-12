---
title: "Problem installing xubuntu. Warning, I'm a newbie"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by seanandjael on 2006-12-15
Okay so here's the deal. Very interested in running a linux based OS for the first time. I heard that ubuntu was very easy to use, even for beginners and that it could run on older hardware. Started with Ubuntu Live CD and found out my hardware was too old (according to some old forum posts) so I switched to xubuntu alternate CD

I'm running AMD Duron 697 MHz, 64M memory, 30 GB hard drive. Running the alt CD in text only mode because of my low memory (says it should work w/ 64 on this site).

Now for the problem: I install all the way to the "Install apps and programs" portion of the install but after 6% completion it stops and CD spins for a while then errors and says that this portion of the install failed. It lets me try to install something else. The only thing left to install is the boot files but when I try to install them they fail as well.

I've checked the integrity of the CD from the boot menu and it says it's fine, so apparently the CD is okay. Memory test went fine if that matters. Also I don't know if it matter but I previously had Windows 98 on the computer but don't care about it or any of the data, just told the installer to format the drive and partition however it wants to. Lastly there's also a 1GB hard drive installed that I wasn't going to do anything with. again I don't know if it matters but it's in the system and I was planning on leaving it there. Basically I'm trying to give all the info I have so that the problem can be diagnosed.

One last thing. I'm aware that a similar post is up on the unofficial xubuntu forums, it seems to be the same thing. However that never really got resolved, so I'm hoping for better luck here.

Please Help!

Thanks

---

### Post by kerry_s on 2006-12-15
Perhaps, try installing the base(command-line) & if that works you can apt-get/aptitude xubuntu-desktop or better yet go custom.

---

### Post by mrunion on 2006-12-15
OK, I *know* this sounds dumb -- but it happened to me (not on Ubuntu).  A long time ago I was installing Linux on an OLD laptop -- OLD!  Everything would go fine, but when the files started copying over from the CD the install would eventually lock up.

Turns out what was happening was the computer was somehow thinking that since nothing was going on with the SCREEN (as in no mouse moving around, no keys being touched) that it needed to start saving power.  It would "spin down" or somehow "disable" the CD ROM drive.  That hung the install.

What I ended up having to do was MOVE THE MOUSE around in little circles once every five or so minutes during the "copying from CD" portion of the install.  That worked.  Don't ask me why this stupid laptop did that.

It might be worth a shot in your case.

---

### Post by seanandjael on 2006-12-15
Okay, hey thanks for the quick response. I have to say these ubuntu forums are great! I'm trying to boot into a command line system now....

I'll also try the mouse moving thing (although it's a usb mouse, don't if it will detect it yet) maybe i'll try to tap a useless key here an there too

---

### Post by seanandjael on 2006-12-15
Here's what happened when i tried to install the command line system. It got through "Select and install software" which was where it stoped before. But immediately errored on the GRUB boot loader.  It said that it's an essential part of the OS and couldn't complete w/o it. Then went on to say that it didn't detect any other OS's on my system and could possible install GRUB to the Master Boot and that might fix it. I said okay and again immediately failed. This and the LILO boot files are the only things left in the install according to the list. Any idea what I should do?:confused:

---

### Post by seanandjael on 2006-12-15
Okay so I'm still having problems. ](*,)  Does anyone know why the whole install process would work but the last steps, installing the booting system would fail??:confused: 

I wanna run xubuntu so bad but I must have tried it a million times by now and it always fails somewhere. Mostly at the point where it installs the booting portion

---

### Post by steveandarchie on 2006-12-19
Probably not much help to you but I have an Athlon 600MHz running Ubuntu and it works fine. I had some stability problems with ME on the old box and I thought it was dying so I tried an Ubuntu dual boot and it's steady as a rock and runs pretty well. I should point out that I dropped 256Mb Ram in one of the slots a while back so that would help - why not try the same, the RAM was cheap as chips.

That said I will start a separate post on my xubuntu problem because I would like to see if it makes a difference. If not it's no big deal as Unbuntu works fine.

---

### Post by Juan Largo on 2006-12-19
seanandgael -

Have you considered using MEPIS instead of Xubuntu?  I've had real good success with MEPIS on some really old motherboards.  I'm using it now on a Compaq Presario 7478 that was built in the year 2000.  Of course I did upgrade the RAM from 64M to 512M and added a hard drive, but I'm stuck with the original sound card and video card and a really ancient BIOS, since the Compaq motherboard isn't upgradable.  MEPIS had no trouble recognizing any of this antique hardware, as well as configuring a really old IJ750 printer. MEPIS comes on a Live CD with an installer.  You can force it to operate at whatever screen resolution your PC can handle by hitting F3 at the boot menu screen and scrolling down to the desired resolution.  I forced it to use 1024x768 for my installation, which provides a really nice display.

I also think the MEPIS installation is easier than Ubuntu (I've tried both), and it gives you flexibility to configure it a lot of different ways.  If you want a dual-boot setup and have a floppy drive (what old computer doesn't?), you have the option of booting into MEPIS from the floppy without touching your master boot record.  Then if you want to delete MEPIS, all you need to do is delete the partitions without screwing around with de-installing GRUB.

---

### Post by seanandjael on 2006-12-20
I'm afraid I would rather not upgrade the hardware. This is a really old machine that I was gunna trash anyway, but I was really interested in trying out Linux for the first time. I guess I could try to upgrade the memory but I can't imagine that the memory is a problem on a text-only based install. As far as MEPIS goes, I'd like to try that but from reading it's really based off of Ubuntu anyway, and I'm having problems with Ubuntu. Plus MEPISLite (which is for older systems as I understand it) you have to pay for. I can't justify paying for something when I'm not even remotely sure that it's going to work.

Like I said before, the text based install is moving along super fast, it takes maybe 10 min to get through everything but just immediately errors when I get to the last part of the install which is the boot stuff. You guys really think it's the memory?

---

