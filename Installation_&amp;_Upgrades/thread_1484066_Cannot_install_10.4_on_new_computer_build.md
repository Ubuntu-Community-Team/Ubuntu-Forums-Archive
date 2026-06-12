---
title: "Cannot install 10.4 on new computer build"
date: 2010-05-15
forum: Installation &amp; Upgrades
---

### Post by CinemaScope on 2010-05-15
I have built a new computer and bought an installation disc for it (64-bit version of Ubuntu **10.4**), but I can't install it (or even use it as a live CD). The usual process after the post you get is: "Reboot and select proper boot device or insert boot media in selected boot device and press a key." When I put in the **10.4** disc the usual warning expression is a screen full of figures (I can't screenshot it) with words like "Call trace...panic...write lock irq...oops end...no context...bad area nosemaphone...do page fault...audit watch init...child rip." I also had a 32-bit version disc of Ubuntu **10.4** but this has the same result. I've been using Ubuntu for a few years and also had a disc of an earlier version of Ubuntu (32-bit **8.10**): when I tried this it worked! I was able to use it as a live session (I did not want to install this older version on my new computer, though). However, I don't think there is a problem with the new installation discs because I was able to successfully install the 32-bit version of **10.4** on an older computer. So, I think my new computer is working ok (**8.10** works ok on it), the installation discs are ok (installed on another computer), but there must be something about Ubuntu **10.4** which doesn't like this new computer. Any ideas?



The spec of the new machine is as follows:



Mobo - Asus P7H55D-M Evo. Intel H55, socket 1156, ATX. 

CPU - Intel Core i5 661, 3.33 GHz. Socket LGA 1156, 32 nm.

RAM - 4x 2 GB DIMMS (total 8 GB). OCZ Gold DDR3 PC3 1066-1333 MHz dual channel.

HDD - Samsung Spin Point F3, SATA 2, 1 TB, 32 MB cache.

Graphics card - Asus ATI Radeon HD 4350, 1 GB DDR2.

DVD ROM drive - Asus 16x read (from an old computer).

Soundcard - None (using internal motherboard sound).

Monitor - Benq 24-inch LCD, 1920 x 1080, DVI-D.

Power supply - Antec 550W PSU.

Badly don't want to buy **Windows 7**, but can't leave this new machine lying around without an operating system. I built it specifically for Linux, and I've been so used to Ubuntu just installing on anything I try it on, I'm a bit mystified by this **10.4** problem. Any help greatly accepted.

---

### Post by hedgeberg on 2010-05-15
It could be that there is something wrong with the disk. If that's the case, find a blank or rewritable cd, and download the .iso file to it (just to be safe, use 32-bit). burn the iso (I reccomend roxio, otherwise find some freeware software, there are hundreds), and then try to boot from that. 
Another problem could be that you are trying to open a DVD using a CD drive. If that's the case, then make sure that whatever you download to is a CD, preferrably the most basic kind you can find, because there are many types of disks that old drives can't run. Since your "DVD" drive is from an old computer, its quite possible its not actually a DVD drive.

---

### Post by Bucky Ball on 2010-05-15
Hedgeberg, OP clearly states the install disk loaded and installed on an older machine so I don't think the disc is the issue but what's on it. ;)

---

### Post by JohnFH on 2010-05-15
Interesting problem.  Do you get the same behaviour (error messages) every time you try to load the Ubuntu 10.04 CD?  Do you have any USB devices plugged in?  Try to eliminate the possibility of various hardware faults by using onboard graphics (if it's available), only use one RAM stick, unplug all USB devices, etc.  Also, boot up to 8.10 and run some diagnostics to test the system.  From 8.10 you could also try to create a boot USB stick of 10.04 and see if that works.

Let us know what you find.

---

### Post by darkod on 2010-05-15
Why would you have a warning after the POST to select proper boot device if you set in BIOS CD-ROM as first for example, and HDD second? It should start loading the cd right away.
From what I could understand, it doesn't even get to the ubuntu disc menu so you could try Safe Graphics right?
Another option is downloading the Alternate Install CD (image), burn it no faster than 8x, and see if you can install with that.
To avoid suspicion about your cd-rom you can try creating bootable usb stick if you have any laying around. Then boot from usb.

---

### Post by ronparent on 2010-05-15
If your lucky, and apparently most people are, the install goes with out problem. Otherwise you need to investigate several posible problems.

I've found through my own experience that because an install cd reads on one cd/dvd/reader/writer it may not on another. Sometimes I have had to resort to burning a bootable iso to a dvd disk.

Then there is the matter of needing special boot parameters. You might try hitting any key when the two icons appear on the bottom the live cd boot splash. This will bring up a language seletion screen and then the live cd manu (if you haven't already discovered it). At this menu hit f6 for boot parameter options - this action will also reveal an editable boot line. Any one of those options might be require to boot on that particular computer. The most common needed boot option is nomodeset (navigate to and hit space bar). I would also recommend hitting the <end> key which will move the cursor to the end of that line and back arruw to the end of quiet splash and backspacing to remove those two options. This will allow the boot process to scroll onto the screen. If it locks up where it stops gives some clue of what the boot process stopper might be. In general, it seems that the earlier the boot stops the more likely it may be one of the earlier option in the f6 list needed to boot that particular machine. The 1st three are unlikely unless you have an older computer - more than four years old. Otherwise than that it is strictly trial and error until you can find the one boot option or more that will free you computer to boot. 

Good luck. Let us know how you make out.

---

### Post by CinemaScope on 2010-05-15
Thanks everyone for your replies. I've been using Linux for several years now but when something unusual happens I'm a total newbie (I've been using Windows for over decade and when something out of the ordinary happens I'm a total newbie with that, too, so nothing against Ubuntu!).

"Same behaviour every time?" No, when I first tried the 10.4 CD in the new machine I saw the pink screen and animated dots below the name ubuntu. But that just went on for about 40 minutes and eventually I rebooted. Now, I never see that graphical screen, I just get the same warning (white letter against black) which fills the screen.

"Do you have any USB devices plugged in?" Only the USB mouse.

"Boot up in 8.10 and run some diagnostics". I can run 8.10 as a live CD, so what should I test? How do I do it?

"From 8.10 you should create a boot USB stick of 10.4." Can you tell me how to do that?

"A CD might install on one CD/DVD drive but not on another". I've swapped three different optical drives (16x DVD ROM, 52x CDRW, 8x DVDRW) and the results seem the same. These drives have successfully installed previous versions of Ubuntu on their computers, but not when used in this new machine with Ubuntu 10.4.

My own conclusions so far: Installation disc has no fault (installed ok on an older machine). New computer seems to have no obvious problem (Ubuntu 8.10 can be used as a live session). Therefore, Ubuntu 10.4 does not like a piece of hardware on this new machine or the way it's set up.

Thanks.

---

### Post by JohnFH on 2010-05-15
To run diagnostics, install checkbox (it may already be installed) and run it by calling checkbox-gtk.  It may already be under the menus somewhere called 'System Testing'.

To create a bootable USB stick is fairly straight-forward.  Download the 10.04 ISO and use the USB Creator tool included in 8.10 (under the System menu I think) to put the ISO onto a USB stick.  It will take a minute or two to complete.  Then reboot and press the key to bring up the BIOS boot menu to boot from USB.

I suspect the problem may be related to the graphics card - do you have a different one to try it with?

---

### Post by dino99 on 2010-05-15
> **CinemaScope said:**
> Thanks everyone for your replies. I've been using Linux for several years now but when something unusual happens I'm a total newbie (I've been using Windows for over decade and when something out of the ordinary happens I'm a total newbie with that, too, so nothing against Ubuntu!).

"Same behaviour every time?" No, when I first tried the 10.4 CD in the new machine I saw the pink screen and animated dots below the name ubuntu. But that just went on for about 40 minutes and eventually I rebooted. Now, I never see that graphical screen, I just get the same warning (white letter against black) which fills the screen.

"Do you have any USB devices plugged in?" Only the USB mouse.

"Boot up in 8.10 and run some diagnostics". I can run 8.10 as a live CD, so what should I test? How do I do it?

"From 8.10 you should create a boot USB stick of 10.4." Can you tell me how to do that?

"A CD might install on one CD/DVD drive but not on another". I've swapped three different optical drives (16x DVD ROM, 52x CDRW, 8x DVDRW) and the results seem the same. These drives have successfully installed previous versions of Ubuntu on their computers, but not when used in this new machine with Ubuntu 10.4.

My own conclusions so far: Installation disc has no fault (installed ok on an older machine). New computer seems to have no obvious problem (Ubuntu 8.10 can be used as a live session). Therefore, Ubuntu 10.4 does not like a piece of hardware on this new machine or the way it's set up.

Thanks.

[COLOR="Blue"][SIZE="4"]seem to be a video driver issue, boot with video=vesa on the boot line[/SIZE][/COLOR]

---

### Post by CinemaScope on 2010-05-15
I'm beginning to think it is a graphics card problem (that maybe the card is too new for Ubuntu compatibility -- all of my previous installations have been on older machines). I'll try another card taken from another machine to prove that point. Can you explain how I can boot with video=vesa and what exactly does that do?
Thanks again.

Edit: um, all my other cards are PCI and this new mobo has the PCIe slot for the graphics card.

Just thinking: since Ubuntu 8.10 works ok as a live CD on this new machine, that means I only have a graphics card problem with Ubuntu 10.4. Why does an old version of Ubuntu accept this new graphics card but the new version doesn't? That doesn't sound logical. What's different with the new Ubuntu which is tripping me up?

---

### Post by ronparent on 2010-05-15
I have a brand new ATI card installed on my signature machine. It works fine with the proprietary driver. Your concern at theis point is to get 10.04 installed so that you could activate the proprietary driver. To load, try appending **nomodeset** or **video=vesa** to the boot line on the live cd menu (bring the line up with f6 and just edit it). Your question just begs the quetion - most of us don't know, it just does. I'm sure once you get past this point everything will work fine.

---

### Post by Bucky Ball on 2010-05-16
When it asks 'Do you have any USB devices connected?' is there an option to answer 'yes' or 'y'?

---

### Post by CinemaScope on 2010-05-16
I don't remember seeing that option about USB (my mobo only has a PS2 socket for keyboard, not mouse, so I need to use one USB socket to have a mouse). I read some other posts in which people have been having trouble installing 10.4, and taking their advice I pressed the spacebar after I get the pink screen, which helped me get a bit further along the process, but ultimately there is no live session and I get a warning:

"(process:388 ): GLib-WARNING**: getpwuid_r(): failed due to unknown user id (0)". 

This same warning was seen by another poster. Any ideas? It's beyond me to understand this stuff...I'm just a Ubuntu user, not an Ubuntu scientist! Have spent all weekend getting nowhere; any help greatly accepted.:(

Many thanks.

---

