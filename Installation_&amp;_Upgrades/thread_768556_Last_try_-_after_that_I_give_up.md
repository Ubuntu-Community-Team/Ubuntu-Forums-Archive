---
title: "Last try - after that I give up"
date: 2008-04-26
forum: Installation &amp; Upgrades
---

### Post by mzbeg on 2008-04-26
Hi all

I have posted this in absolute bigners forum but have received no assistance. This is the last time I am posting my problems.  If I do not receive any assistance then I will totally give up and never ever think of going near any Linux programmes.

I installed 8.04 from Window XP rebooted into Ubuntu using the Verbose mode and got the following messages :

ata3.01=status {DRDY}
failed to read native max address (err-mask=0x4)
failed to reconnect some devices
revalidation failed (err0-5)

And many more.

The problem in Verbose mode is Pause/Break key does not work in order to write down all the messages.

I have Samsung 500GB partitioned as follows:

C:\Windows XP Primary
D:\Ubuntu; E:\ F:\ G:\ H:\ and all logical partitions.

I tried Safe Graphic Mode and got 3.01=status {DRDY}
ACPI workaround ata3.00=status {DRDY}

I do not know what it all means. Can any one help me please. Thanks.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - SATA Samsung SH-S203LJ DVD RW - ATA POINEER DVD-RW DVR-109 - EZCOOL Case - WINDOWS XP Service Pack 3.
mzbeg is online now Report Post   	Edit/Delete Message

---

### Post by overdrank on 2008-04-26
> **mzbeg said:**
> Hi all

I have posted this in absolute bigners forum but have received no assistance. This is the last time I am posting my problems.  If I do not receive any assistance then I will totally give up and never ever think of going near any Linux programmes.

I installed 8.04 from Window XP rebooted into Ubuntu using the Verbose mode and got the following messages :

ata3.01=status {DRDY}
failed to read native max address (err-mask=0x4)
failed to reconnect some devices
revalidation failed (err0-5)

And many more.

The problem in Verbose mode is Pause/Break key does not work in order to write down all the messages.

I have Samsung 500GB partitioned as follows:

C:\Windows XP Primary
D:\Ubuntu; E:\ F:\ G:\ H:\ and all logical partitions.

I tried Safe Graphic Mode and got 3.01=status {DRDY}
ACPI workaround ata3.00=status {DRDY}

I do not know what it all means. Can any one help me please. Thanks.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - SATA Samsung SH-S203LJ DVD RW - ATA POINEER DVD-RW DVR-109 - EZCOOL Case - WINDOWS XP Service Pack 3.
mzbeg is online now Report Post   	Edit/Delete Message

HI and welcome, I am assuming that you used Wubi when you state from within windows. I have not used Wubi for a installation and there is a forum located here
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)
As for your threat of never returning to linux that is your decision and has no affect on me helping or not. Good luck in whatever you choose.

---

### Post by Devi 710 on 2008-04-26
I don't know if many people here have done the install through windows, that is a new feature. So it may be difficult to get assistance.

I really wouldn't give up on Linux if I were you. It is sooo worth once you know your way around. I have a Mac and even it blows compared to linux.

I would install Ubuntu 7.10 or even 7.04 if I were you. 8.04 doesn't seem to be the best at this point. Make sure you defrag windows first, pop in the cd and follow the steps.

---

### Post by mzbeg on 2008-04-26
> **Devi 710 said:**
> I don't know if many people here have done the install through windows, that is a new feature. So it may be difficult to get assistance.

I really wouldn't give up on Linux if I were you. It is sooo worth once you know your way around. I have a Mac and even it blows compared to linux.

I would install Ubuntu 7.10 or even 7.04 if I were you. 8.04 doesn't seem to be the best at this point. Make sure you defrag windows first, pop in the cd and follow the steps.

Hi,
Thanks for your reply.  I tried 7.10 and I got this message :

ata3.00=failed to set xfermode (err-mask-0x40)

I even tried using irqpoll switch, it also hangs.

Thanks for your help.

---

### Post by tofuconfetti on 2008-04-26
You may have the same problem that keeps the Live CD from booting on some systems.  It took me about a day to figure it out for myself and I've been using many versions of linux for about 10 years.  

There were several posts on [this thread]("http://ubuntuforums.org/showthread.php?t=765195&page=5") about the Live CD freezing on boot up.  What happens is that some bios' with some motherboards apparently don't assign IRQ's correctly when you use SATA drives in IDE mode.  That is why you're seeing funny responses for some setting this in 'raid mode' versus 'ACHI' mode.  I found the solution at [this link]("https://wiki.ubuntu.com/WubiGuide#head-9fe000fa2e31a632fdcf384438b2aee35076c623") after searching the bug reports.

It sounds like your error message is telling you that the kernel can't find your "ata 3.00" drive.  That is why I think it's the same bug.

The article tells you to enter "irqpoll" at the end of the kernel boot command.  The method described did not work for me and I was applying it to the Live CD graphical boot environment.  See my solution in the thread I posted at the first link.  It sounds like you are past and need for the actual computer boot sequence.  What you might need to do is boot from the Live CD, and you may have to follow my instructions on the first link I provided in how to get into the live CD, and once there mount your system partition, and edit the /boot/grub/menu.lst file.  

In the line that describes the options for the kernel boot, add 'irqpoll' (no quotes) at the end of that line and it should have the same effect.  Hopefully that will work.  Since you are installing it from a Windows environment, you'll have to edit that file.  It will require you to be root, so use the "sudo" option.

I hope you're at least a little familiar with the command line as it's easiest to do from there.

---

### Post by rickycodie on 2008-04-26
another thing that you could try that has worked for me in the past is to boot into bios and set the hard drive to compatability or similar setting. if you don't have that setting, then sorry i couldn't help.

---

### Post by Caligatio on 2008-04-26
I'm getting the EXACT error message.... I think it's widespread.

Take a look at: [http://ubuntuforums.org/showthread.php?t=765195](http://ubuntuforums.org/showthread.php?t=765195)

Looks like some SATA controllers just aren't working.

---

### Post by Flopmouth_Fish on 2008-04-26
I'm having a similar problem to the OP (I think):

I have Windows XP installed on a 250GB SATA drive. I originally thought that I'd install both XP and Ubuntu on this drive, so I created a 200GB partition for Windows and was going to use the remaining space for Ubuntu.

However, last time I tried to do this using the guided partitioning (which was a bad idea), it resized my Windows partition and toasted my XP install.

Since I can't afford to lose any of my Windows data, I decided to install Ubuntu on a second hard drive, an 80GB Western Digital IDE drive.

I installed 8.04 on the 80GB drive this morning. The installation was successful, and after it finished installing, I clicked "restart computer". Sure enough, it restarted, but I was never given an option to boot Ubuntu; it automatically began loading Windows.

I've tried resetting all the BIOS settings to default, and it still defaults to Windows without even giving me the option to boot Ubuntu.

I've tried to manually boot off the 80GB drive; it starts the nVidia Boot Agent, but gives me a "PXE-E61 boot disk failure", and says to check the drive connection. I know that the drive is properly connected; it shows up in Windows.

Here's my system setup:

DFI nF4-DAGF (nForce 4 chipset) socket 939
AMD Athlon 64 3700+
1GB RAM
250GB Western Digital SATA
80GB Western Digital ATA

I'm at wit's end, but I'm not going to give up, as I'm happily running 7.04 on an old Dell, and my XP install still works (thank God).

Thanks in advance

---

### Post by Flopmouth_Fish on 2008-04-26
Oops; double post.....

---

### Post by tofuconfetti on 2008-04-26
Try switching the SATA chains that the drives are on.  Put the 80 Gb drive on the first SATA connection.  Then if Ubuntu boots, modify the /boot/grub/menu.lst file to include the option to boot windows.

Whenever I do a dual boot setup I put Linux on the first drive in the chain and windows on the second.  With Ubuntu, the installer automatically recongizes a Windows installs and modifies grub for you.

---

### Post by HDave on 2008-04-26
About 6 months ago, I was in the EXACT same boat as you.  Trying to get Gutsy up and running on my laptop was very hard for me -- especially being brand new to Linux.

Some very kind poster told me to stick it out, find a way to make it work, and that I would be grateful later on.  Though it took me a MONTH of effort to stabilize my system, I can tell you it was one of the most technically rewarding experiences I have had.

It has come a long way, but using Ubuntu will (unfortunately) still force you to learn a lot more about your computer than you ever wanted to know, but you will be better off for it.  The community support here is also second to none...although there are a million new users all trying to get newbie help here right now, so there will be some delays.

Just hang on, you'll be swimming in Hardy goodness before you know it.

---

### Post by Flopmouth_Fish on 2008-04-26
> **tofuconfetti said:**
> Try switching the SATA chains that the drives are on.  Put the 80 Gb drive on the first SATA connection.  Then if Ubuntu boots, modify the /boot/grub/menu.lst file to include the option to boot windows.

Whenever I do a dual boot setup I put Linux on the first drive in the chain and windows on the second.  With Ubuntu, the installer automatically recongizes a Windows installs and modifies grub for you.
SATA chain?

The 250GB drive is SATA; the 80GB drive is an IDE drive.

For some reason, the 250GB SATA drive is listed as an IDE drive in the BIOS.

In the BIOS, the 80GB IDE drive is listed as "IDE Channel 1 Master" (My two DVD drives are the IDE channel 0), and the 250GB SATA drive is listed as "IDE Channel 2 Master".

I tried setting the 80GB drive as the first HDD to boot from, and it still went straight into Windows.

I'm going to try disconnecting the SATA drive.

---

### Post by Flopmouth_Fish on 2008-04-26
I tried disconnecting the SATA drive, and it booted into the nVidia Boot Agent, and gave me the same message as before.

So I switched the 80GB drive to IDE Channel 0 (I switched it with the DVD drives), and it gave me a GRUB Loading Stage 1.5 Read Error.

What should I do?

Perhaps the hard drive is dying?

---

### Post by Flopmouth_Fish on 2008-04-26
Bumpity-bump-bump!

---

### Post by Flopmouth_Fish on 2008-04-26
I'm reinstalling Heron right now with only the IDE drive connected.

My fingers are crossed...

---

### Post by tofuconfetti on 2008-04-27
SATA chain.  Maybe a bad usage of the word.  But the SATA connectors have an order.  Look on the actual motherboard, they will be SATA 1, SATA 2, etc.  Then to make matters worse, you'll sometimes have a second group that are connected to a "raid controller", which isn't really a hardware raid controller, it's just another series of SATA connectors on another hardware SATA interface sometimes from a different company that offers software drivers for Windows.  

In times past, those had VERY spotty linux support.  I distinctly remember a couple of Promise IDE "raid" controllers I never got to even recognize a drive connected to them.  

So as a matter of practice, when I am installing Linux on a computer with Windows installed AND I am sure that I want Windows to dual boot (almost never nowadays, since I only use Linux and Mac now) I put a fresh drive in the first "drive spot", either IDE 1 if it's and IDE setup, or SATA 1 if it's an SATA system.  I put the Windows drive second on the device chain.

That may be nothing more than superstition to some, but when I do it this way I ALWAYS know which drive I am looking at by device name.  In other words if I am working from the command line on a SATA system, the SATA 1 drive is /dev/sda and the second is /dev/sdb.  It just keeps me from making mistakes when I do it the same every time.

I have also found that Ubuntu tends to put the grub boot loader on the FIRST drive in the chain.  If you put Windows first, you can get rid of it, but if you decide you don't like the Linux you just installed, you have a grub boot loader you don't need.  If you put the drive first, just remove the drive, put the Windows drive there, and Viola! you're back where you started.  It keeps thing clean.  

This is off topic, but it may help you someday.

---

### Post by mzbeg on 2008-04-27
> **rickycodie said:**
> another thing that you could try that has worked for me in the past is to boot into bios and set the hard drive to compatibility or similar setting. if you don't have that setting, then sorry i couldn't help.

Thanks for your reply. No I do not have any compatability option in  the BIOS.

Last night I was trying to load 7.10 version, about after 7 or 8 attempts always with "irqpoll", it reached up to the desk top. I started installing and when I reached the spot where you have to create swap partition, it said it would take a long time. I left my computer on whole night. This morning when I checked, it was still busy creating the swap partition. I canceled it and went straight to installing without swap file. It started installing and hanged after loading 15%. 

It did create dual boot option for me, but when I tried to boot it, I got the same message. In XP envoirement it gave me the option to uninstall, which I did.

Most of the time I get same error "ata3.00=failed to set xfermode (err-mask-0x40)"

Is there an explanation of the contents of "Help" you get when you type help at the command prompt.

Thanks for your help.

Abit IP35 Pro - Intel Core 2 Duo E8200 - Corsair 2GB DDR2 800MHz/PC2-6400 XMS2 Memory - NVIDIA GeForce 8600 GT - Cooler Master Hyper TX 2 Processor cooler - Corsair HX Series 520W Modular PSU - Samsung SpinPoint HD501LJ 500GB SATAII Hard Drive - Poineer 109 DVD RW - SATA Samsung SH-S203LJ DVD RW - ATA POINEER DVD-RW DVR-109 - EZCOOL Case - WINDOWS XP Service Pack 3.

---

### Post by mzbeg on 2008-04-27
AT LAST SUCCESS !!!!

Hi all

I tried two things. First instead of booting from my SATA DVD Drive, I booted from IDE DVD Poineer Drive.

Second reading from various threads I used the following switch which 
worked for me :

all_generic_ide floppy=off irqpoll

Now I have to configure my internet connection.  Thanks all for all your help. Cheers

---

### Post by Flopmouth_Fish on 2008-04-27
When i tried to install it with only the IDE drive in the system, it gave me an error about halfway through the install...

Something about not being able to read the files off of the DVD drive, I think.

I'm getting kinda frustrated...

I might just install 8.04 on the 40GB partition on my SATA drive, unless anyone has any suggestions?

Thanks

---

### Post by tofuconfetti on 2008-04-30
I posted this on another thread, but I'll put it here so you guys can see it also.  I had forgotten this had worked before.  From [this thread]("http://http://ubuntuforums.org/showthread.php?t=765195&page=10") ...

> After all this, I decided on that particular computer to revert back to 7.10. It did the same thing. I hadn't remembered that, but it finally dawned on me that previously I had disabled the "USB legacy support" in the BIOS of that motherboard. I did that again and had absolutely no problems booting up. Then I remembered that was required of another Intel based ASUS motherboard.

So I closed down the 7.10 Live CD and tried the 8.04 CD with the legacy USB disabled. It worked like a charm with no parameters passed to the kernel line.

The only downside to this is that you can't select the options in the boot menu IF you are using a USB keyboard. You can, of course, solve this with a PS2 connected keyboard just for the setup (I always keep one around).

Add that as another one to try on your list of possible solutions.

The hardware I had success on was:

Intel D975XBX2 motherboard
e6600 quadcore chip
4 Gb of RAM
Nvidia 8800 GTX video
WD 500 Gb SATA drive on SATA1
SATA DVD+/-RW on SATA5
No floppy as registered as such in the BIOS
USB keyboard/mouse


---

### Post by oldsoundguy on 2008-04-30
something similar on trying to upgrade to hardy from gutsy on one machine.

Sata drive errors.  Only I don't HAVE SATA drives, IDE only.
BUT it is old PIII 733 using the Via chipset and have noticed that there are bug reports filed on that chipset. (oldest and slowest box in the joint!)

Went back to 7.10 till the issue gets solved for that unit. (and that may not be until 8.10 comes out in October!)

If it works, doan be messin' wid it!!!!  It IS nice to have the fall back to a working system on that machine!

---

