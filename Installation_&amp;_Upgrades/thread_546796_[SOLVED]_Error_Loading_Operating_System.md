---
title: "[SOLVED] Error Loading Operating System"
date: 2007-09-09
forum: Installation &amp; Upgrades
---

### Post by iheartubuntu on 2007-09-09
Please help guys! I have been really excited about getting Ubuntu working on my older laptop. Its a Pentium III, 900 mhtz with 500mb RAM, 20 GB HD.

My CDROM drive works, but is not readable to boot up into (i have no idea why). It did work fine in XP though. So, I could not use a Ubuntu install CD. My next step was to try a SD chip with Ubuntu install files in an SD chip reader plugged into the USB port. My bios says it can boot into external drives, so I thought this might work. It didnt. My next plan was to install Ubuntu using the netInstall option. I was excited. It was finally working and installing for me. Originally, when I tried the netIinstall or netboot, it didnt work because I was trying to do so wirelessly. Reading the message boards here, I then tried a direct connection to my laptop for the install. This worked. It appeared to be almost done, partitioned the drive, installed software, then the screen went unreadable and I could tell it was asking me some more questions. Since I couldnt read it, I (unfortunately) decided to reboot. It appeared OK on the reboot, trying to load ubuntu I guess, then rebooted itself, then when to the error code of "error loading operating system".

So this is where Im at. My CDROM doesnt work for booting. I cant read a USB device on boot and I get this error message every time. Is there ANYTHING I can do? My only idea now is to bring my computer to work tomorrow, try hopefully installing XP with an original XP disc (for some reason I think it can read original XP disc on boot up), install XP, then run the Ubuntu netboot again. 

Thats my only idea. Does anyone have any other options for me I can try? I do have a direct internet connection I can somehow make use of. Can I attempt to access the computer from another computer maybe?

Please help. Ive been reading and reading and finally got Ubuntu to install stage and now Im screwed.

---

### Post by Pumalite on 2007-09-09
(for some reason I think it can read original XP disc on boot up)

This sounds like a Micro%$& conspiracy.

Being this a brand new install; I think your best option is to re-install. ( netboot, direct connection, ideally through router providing you DHCP)

---

### Post by iheartubuntu on 2007-09-09
> **Pumalite said:**
> (for some reason I think it can read original XP disc on boot up)

This sounds like a Micro%$& conspiracy.

Being this a brand new install; I think your best option is to re-install. ( netboot, direct connection, ideally through router providing you DHCP)

So, the only way I can do netboot is to reinstall XP first?

And if it might help me in any way, I do have a 3.5" floppy removable drive I can put in place of the CDROM drive. Although, the netboot file is like 8mb? Dang.

---

### Post by Pumalite on 2007-09-09
[http://www.linuxquestions.org/questions/showthread.php?t=341981](http://www.linuxquestions.org/questions/showthread.php?t=341981)

[http://www.linuxquestions.org/questions/showthread.php?t=513193](http://www.linuxquestions.org/questions/showthread.php?t=513193)

[http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html](http://www.ubuntugeek.com/install-ubuntukubuntuedubuntuxubuntu-without-cdrom-drive.html)

Don't forget to use Alternate CD

---

### Post by iheartubuntu on 2007-09-09
Thanks for the tips Puma. I'll see what I can make of them today and then tomorrow when I get into work.

---

### Post by Pumalite on 2007-09-09
You are welcome. Good luck.

---

### Post by iheartubuntu on 2007-09-10
Just got into work, tried the XP disc in my laptop, and my cdrom drive will not read it.

What can I do now? It appears the easiest way is to do a floppy install?

---

### Post by iheartubuntu on 2007-09-10
My floppy drive is at home, but I'd like to get my floppy disks ready in the meantime.

Puma, the links for creating a ubuntu floppy disk are confusing to me. I guess im not as technically gifted as you :) One link had someone recommending  making debian boot floppies and installing debian. Does Ubuntu have any files or links for creating Ubuntu floppies?

Otherwise, I'll have to somehow get my floppy drive to work, fdisk the drive, format it, and try getting my cdrom to work.

I think im screwed.

---

### Post by logos34 on 2007-09-10
> **shirteesdotnet said:**
> My floppy drive is at home, but I'd like to get my floppy disks ready in the meantime.

Puma, the links for creating a ubuntu floppy disk are confusing to me. I guess im not as technically gifted as you :) One link had someone recommending  making debian boot floppies and installing debian. Does Ubuntu have any files or links for creating Ubuntu floppies?

Otherwise, I'll have to somehow get my floppy drive to work, fdisk the drive, format it, and try getting my cdrom to work.

I think im screwed.

this is admittedly a long shot--

Is there any way you could possibly connect the floppy drive AND cdrom at same time--for instance, unscrew the bottom panel and pull the floppy ribbon cable and power cord out just enough to plug into the floppy drive (they're probably way to short).  Because if so you could try Smart Boot Manager (floppy) to boot the cdrom.  

The only other way besides some kind of netboot/network install is to take the hard drive out and hook it to another machine/lappy and do the install.  Then put it back and hope it works.
> 
Does Ubuntu have any files or links for creating Ubuntu floppies?

You could try these (whether they work as advertised is another matter):

[https://help.ubuntu.com/community/Installation/WithFloppies?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/WithFloppies?highlight=%28installation%29)
[https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies?highlight=%28installation%29](https://help.ubuntu.com/community/Installation/FromHardDriveWithFloppies?highlight=%28installation%29)

---

### Post by Pumalite on 2007-09-10
logos34 is the last word here.

---

### Post by iheartubuntu on 2007-09-10
Thanks for the help guys.

Heres my plan for now... if it doesnt work, I will spend more time with your links...

-boot up the system using a DOS boot disk.

-format & partition the HD

-hopefully, hopefully I can then read the CDROM drive once im at least in my floppy. If so, hopefully, i can run windowsXP and install it, then proceed to do the netboot of Ubuntu, which I did have working.

If this idea doesnt work, I'll check out logos34 links. Thanks.

---

### Post by Pumalite on 2007-09-10
Good luck!

---

### Post by iheartubuntu on 2007-09-11
Ive had a bit of success tonite.

When I got home with my boot floppy, I found in my stash of old computer stuff, a workable CDROM drive. I removed the obviously faulty CD/DVD drive, in place of the CDROM drive and presto, I can boot from Ubuntu disc now.

Ive begun to do the install, and when I got to the point to select which version to install, I picked Ubuntu since I figured it would be fine with 500mb RAM on an older P3 system.

On the "select and install software" page, it says "Please wait..." with 6% done. Its been at 6% for a good 50 minutes now.

I dont know whats going on at this point. Does it usually take a while?? The HD gets read about every other second... It doesnt feel like its writing much, but what do I know.

Should I just let it go overnight?

Thx!

I have another old laptop to fix after this one :)

---

### Post by merlinus on 2007-09-11
DId you check the cd for errors at the startup menu?  Did you burn at no more than 4x?  Did you do a checksum on your download?

---

### Post by Pumalite on 2007-09-11
Are you using the Alternate CD as I suggested some posts back?

---

### Post by iheartubuntu on 2007-09-11
I noticed my discs might have been giving me problems... a 4x burnt disc wouldnt work, yet a 16x disc would. I have 3 discs...

-Ubuntu Mini
-Ubuntu
-Ubuntu ALT

The only one that worked last night was the mini install. And thats where I was at the 6% mark. Anyhow, I checked in on the computer and the night ended with a dreaded "unable to install GRUB" message.

I brought all my drives, discs and computer to work with me today so I can solve this prob. Turns out my regular Ubuntu disc and my ALT Ubuntu discs were both trash and unreadable.

I reburned the ALT disc and ran an integrity test. Alls OK so far. Im now installing Ubuntu ALT and will continue to update this thread for future reference.

Thanks again for the help!

---

### Post by iheartubuntu on 2007-09-11
The install crashed again. I think my problem is burning a workable disc.

Ive tried burning the ISO file (alt) from 4 different computers now. Only two of those computers can burn as slow as 4x. All discs I do a check on, fail.

Any advice?

I guess I can go back to trying a netboot.

Does anyone here offer Ubuntu disc burning? :(

---

### Post by merlinus on 2007-09-11
Are you using good quality cds, or el-cheapos?

Also, you might try InfraRecorder, an open source burning program.

---

### Post by Pumalite on 2007-09-11
You can also try ImgBurn:(ex DVD Decrypter): [http://www.imgburn.com/](http://www.imgburn.com/)

---

### Post by iheartubuntu on 2007-09-11
Im using Memorex cd's. 

Just burned a 4x using ImgBurn, verified the disc to be good, now attempting an install.

Several of the discs Ive thrown out today that dont load up on the laptop, work fine on other computers. Pointing to the drive as the prob.

I'll give it a few more attempts tomorrow with a different CD drive I have here that I can swap in... if not I think I will try netboot.

Yah, Im getting an error here again trying to install. Im thinking its the drive more than anything.

Uggh. And this disc loaded up great on the computer I just burned it from.

---

### Post by merlinus on 2007-09-11
At this point, I also suspect your cd drive.  But it is not unusual for disks burned on one computer and/or drive to not work in another.

---

### Post by Pumalite on 2007-09-11
If you want to netboot:

[https://help.ubuntu.com/community/Installation/Netboot](https://help.ubuntu.com/community/Installation/Netboot)

---

### Post by iheartubuntu on 2007-09-13
A bit of an update.

I finally gave up on installing to that particular laptop. 

I reinstalled WinXP on that system without a problem. I'll leave that system alone now.

I do however have an exact identical laptop, but with only 256 RAM, not 512. So, I proceeded to install the Ubuntu ALT disc. No problems. I went through the complete installation, it told me about the admin privileges using "sudo" then it popped my cd out so I could reboot. Man, this was getting exciting!

Upon reboot... I get "Operating System Not Found".

Any more tips for this out of luck, yet excited, future Ubuntu user?

Should I try installing the newest version of Ubuntu?

---

### Post by iheartubuntu on 2007-09-13
The new Ubuntu didnt work. :|

---

### Post by Pumalite on 2007-09-13
In that 256 MB RAM laptop, try: Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by iheartubuntu on 2007-09-13
> **Pumalite said:**
> In that 256 MB RAM laptop, try: Xubuntu Alternate CD: [http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

Thanks yet again Puma! I'll try it out tonite.

---

### Post by Pumalite on 2007-09-13
You are welcome. Good luck!!

---

### Post by iheartubuntu on 2007-09-14
So I just installed **Xubuntu **right now. It worked just fine. I ejected the CD, rebooted and the computer once again says "operating system not found".

Anyone know why it might be doing this?

The only thing I can think of is its a partitioning prob? When it asks me to partition the drive, I usually pick "erase entire drive" or erase all, whatever it asks me. So, it should just partition my only drive, a 20GB drive, right? I mean, it installs all, so it must be partitioned correctly.

---

### Post by confused57 on 2007-09-14
> **shirteesdotnet said:**
> So I just installed **Xubuntu **right now. It worked just fine. I ejected the CD, rebooted and the computer once again says "operating system not found".

Anyone know why it might be doing this?

The only thing I can think of is its a partitioning prob? When it asks me to partition the drive, I usually pick "erase entire drive" or erase all, whatever it asks me. So, it should just partition my only drive, a 20GB drive, right? I mean, it installs all, so it must be partitioned correctly.
You might want to post the laptop's manufacturer & model.  Also, there might be some kind of mbr protection(or antivirus setting) in the bios that is preventing grub's IPL from installing to the mbr...

---

### Post by iheartubuntu on 2007-09-14
Its a GATEWAY 5300 Solo Laptop. 256mb RAM, 900mhtz. 20GB hd.

---

### Post by confused57 on 2007-09-14
Try booting the Xubuntu install cd...then select "Boot from first Hard Disk".  If Xubuntu boots to the hard drive, then I suspect it's a mbr/bios problem(boot order?) that's causing the OS not found error.

---

### Post by iheartubuntu on 2007-09-14
> **confused57 said:**
> Try booting the Xubuntu install cd...then select "Boot from first Hard Disk".  If Xubuntu boots to the hard drive, then I suspect it's a mbr/bios problem(boot order?) that's causing the OS not found error.

OK. I did that and here is the answer I get....
[B]

isolinux: Disk Error 01, AX = 0201, drive 80

Boot Failed: press a key to retry

[/B]

---

### Post by iheartubuntu on 2007-09-14
I think i figured out my prob!

[http://ubuntuforums.org/showthread.php?t=194438](http://ubuntuforums.org/showthread.php?t=194438)

my bios somehow switched itself to boot from cd, not auto HD mode. i put it on auto to find the hd, and xubuntu is loading!

---

### Post by confused57 on 2007-09-14
> **shirteesdotnet said:**
> OK. I did that and here is the answer I get....
[B]

isolinux: Disk Error 01, AX = 0201, drive 80

Boot Failed: press a key to retry

[/B]

You might want to try booting your system with the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
It's a very small download(5-7 Mb) & it "may" be able to boot into Ubuntu, or you could try installing grub to the mbr, using SGD.

Added:  Great, just read your last reply...I sort of thought there was a bios "glitch".  Glad you found the solution.

---

### Post by iheartubuntu on 2007-09-14
I think im going to re-install Ubuntu ALT since that installed fine but gave me the same error message also.

---

### Post by iheartubuntu on 2007-09-14
I would like to humbly thank everyone who guided me to getting this thing up and running! Thanks Puma and Confused57!!!

---

### Post by iheartubuntu on 2007-09-14
Greetings! I am posting now with my new Ubuntu ALT version on a PIII-900mhtz with 256 ram and it works GREAT! 

Installing some favorites now like picasa, sopcast, and stellarium.

Thanks guys!!!

PS... got my netgear wireless card to work too, no probs.

---

