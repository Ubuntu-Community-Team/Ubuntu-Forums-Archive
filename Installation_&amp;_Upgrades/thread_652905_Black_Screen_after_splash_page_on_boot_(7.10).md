---
title: "Black Screen after splash page on boot (7.10)"
date: 2007-12-29
forum: Installation &amp; Upgrades
---

### Post by jordanit on 2007-12-29
Hi all,

I'm completely new to Linux/Ubuntu, and am hoping someone can give me some advice.  My housemate gave me his dad's old Toshiba Satellite (1800?) laptop to tinker around with, and I thought it'd be fun to try out Ubuntu on this thing as it's too old to run XP apparently.  I don't know much about it, but i know it's a Celeron 800Mhz, and I've got 384MB ram in it.  So far, I've downloaded the 7.10 desktop ISO, burned to a disk.  It boots up fine to the Ubuntu main screen (Start or Install, Start in safe graphics, etc..) but when I try either of those options, it takes me to a screen with the logo on it and a progress bar with an orange bit that zooms back and forth.  After that the screen goes black and I can't see anything.   I've tried normal start, and the safe mode-ish options, but same thing.  I even have a copy of Xubuntu, but it also does the same thing.  

I'm downloading a copy of the alternate CD, so hopefully that might get me farther.  If you have any ideas, they're very welcomed.

Thanks!
jordanit

---

### Post by Pumalite on 2007-12-29
I'd try Xubuntu Alternate CD (text based installer)

---

### Post by jordanit on 2007-12-29
I just tried the 7.10 alternate CD, and that seemed to work better, although not perfect.  The last screens I remember it getting to were the "configuring apt" "Scanning the mirror" screen at which it hung on until I unplugged the ethernet cable.  After that it went through a few more screens fairly quickly, and was installing a bunch of smaller files, and then the next time I looked at it, the screen was black with a white cursor in the top left corner.  no letters showed up when i typed, but the cursor did move over and once in a while it would leave an underscore where it was, but no letters.  I left it there for a while, them shut it down after it didn't do anything.  When i booted from the HD, it tells me "Missing Operating System" (which it definately didn't do before I tried installing Ubuntu).

Could it be something is corrupt? should i look into trying the Xubuntu alternate installer too incase the system's too old??

thanks,
jordanit

---

### Post by essexboyracer on 2007-12-29
I had the same on an old Tiny Laptop PIII 1ghz 256 MB ram. It seemed to hang on a black screen with the 7.10 ubuntu normal disk. Incidently the 7.10 ubuntu normal CD worked installing to my 1.2ghz Athlon 640MB Desktop

7.10 xbuntu (normal and alternate CD's both) worked for me on the laptop though. Perhaps just leave it alone for longer than you have when it seems to be stuck?

---

### Post by Pumalite on 2007-12-29
You cannot boot a Live CD with 340 MB of RAM. I suggest again you download and install with this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)

---

### Post by Pumalite on 2007-12-29
You could boot a Live CD is you make a 500 MB /swap partition ahead of time with Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn the image to a disk, boot from it and make your partition.

---

### Post by essexboyracer on 2007-12-29
pumalite may be correct, i dont know jordanit, im just along for the ride. 

My HD on the laptop did have a swap partition when booting the liveCD's, as I had previously had slackware and win2k on there (and re-partitioned the HD a gazillion times with the excellent gparted liveCD)

---

### Post by jordanit on 2008-01-01
sorry for the delay, New Year's Eve festivities have taken priority :guitar:.

I downloaded the Xubuntu alternate CD and used the text installer to try and install it.  Same thing happened:  it got to the "Install and Select" screen (about 5%) and then the screen went black with the white cursor/underscore in the top left corner.  I then downloaded Gparted and deleted all the partitions on the drive.  then tried re-installing with the "Guided - use entire disk" option when asked about partitioning disks.  I'm trying the "guided - resize IDE1 master, partition #1 (hda1) and use freed sp" option right now, but do you think it has something to do with the way my HD is setup or one of these options??  (it's looking for ext2 file system right now...??)


also,  whenever it gets to the "scanning mirror..." bit and hangs at 40%, i just pull the enet cable out and it eventually continues again.  think this has anything to do with it?  i read somewhere that problem is because the site it's looking for is out of commission?  Is there anyway to make it point to a working site??  just curious! :)

Thanks again for your help,
jordanit

---

### Post by Pumalite on 2008-01-01
Post your specs. You might need a lighter distro.

---

### Post by jordanit on 2008-01-01
Specs:

Toshiba Satellite 1800 (PS181C-00CET)
800 MHz Celeron, 125 KB L2
384 MB SDRAM
40 Gig HD <- i put this in
64 bit AGP Bus

if you need anything else it's on here:
[http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=4&part=4#spectop]("http://www.toshiba.ca/web/product.grp?lg=en&section=1&group=223&product=4&part=4#spectop")

---

### Post by Pumalite on 2008-01-01
Post # 5 should do it.

---

### Post by jordanit on 2008-01-02
well, i tried both the alternate AND desktop CDs, and still the same thing happens.  Ubuntu and Xubuntu progress bar shows, then the screen goes black and does nothng.

any other suggestions?

---

### Post by Partyboi2 on 2008-01-02
Try with some boot options.
When you are at the main menu screen press F6 to add options
At the end of the line add
```
noapic nolapic pci=noacpi acpi=off
```
And remove the "quiet" option
then press enter.
Removing the "quiet" option should show you where your system is hanging. (if those other boot options didn't work)

---

### Post by Pumalite on 2008-01-03
Here is a guide and a collection to try:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)
[https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html](https://help.ubuntu.com/7.04/installation-guide/hppa/boot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by thierman on 2008-01-03
Hi,

I have the exact (minus the harddrive) same hardware, and have had the same expierence. Taking off the quiet option from the boot I see it gets as far as Configuring X... at which point the screen blanks out and well, thats pretty much the end.

After waiting for n minutes/seconds, if I hit print screen, the CD starts doing stuff for about 30 seconds longer then nothing. I'm assuming this has something to do with X11, but without anymore info I can't really besure....

I've tried a number of options, 

vga=259/0xF07/..etc.../771 noapic nolapic pci=noacpi acpi=off etc...

and same result. So, I was wondering, did you ever have any success with this, or should I just decide that my old Toshiba Laptop will forever run Windows 2000? sigh.....


Thanks....

---

### Post by essexboyracer on 2008-01-03
Just an idea if none of the above work.... Does the machine already have something else on the hard rive, i.e. windows that takes up a lot of space? You didnt say that it was wiped clean of other offending OS's, if it is that try it

EDIT: just looked at your specs and the graphics controller is a trident cyberblade, the same as my tiny (FIC mobo). 
Try these: [http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=8ur&q=Toshiba+Satellite+1800+ubuntu&btnG=Search&meta=](http://www.google.co.uk/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-GB%3Aofficial&hs=8ur&q=Toshiba+Satellite+1800+ubuntu&btnG=Search&meta=)

[http://murga-linux.com/puppy/viewtopic.php?t=23050&sid=685029f65ea6e6806ae417fd51710a20](http://murga-linux.com/puppy/viewtopic.php?t=23050&sid=685029f65ea6e6806ae417fd51710a20)

[https://answers.launchpad.net/ubuntu/+question/1673](https://answers.launchpad.net/ubuntu/+question/1673)

[http://ubuntuforums.org/showthread.php?t=211767](http://ubuntuforums.org/showthread.php?t=211767)

the last link seems more appropiate and plausable, get a better brand of CD-R and burn at lower speeds

---

### Post by wilsonone on 2008-01-04
Hello all

I have been searching through the installation and upgrades forum for the past two weeks and have not found a solution to what I believe is the same problem described here.

When installing Ubuntu, Xubuntu, Dam Small Linux, ...  the install screen will go blank/black.  It sounds like  the monitor switches resolutions by itself because I hear the monitor click.  In order to reboot I have to pull the power plug and start over.

I have tried many of the options suggested in this thread and none of them seem to work.

Spent a lot of time on the Boot Options Documentation page.[https://help.ubuntu.com/community/BootOptions#head-07d4b7411f7da70e337287db9a86ea941038b8b3]("https://help.ubuntu.com/community/BootOptions#head-07d4b7411f7da70e337287db9a86ea941038b8b3")

But no dice.

Some Spec
PIII NetVista
System Mem 384 MB
Active Video Nvidia

I am open to all suggestions at this point.
Thanks:confused:

---

### Post by wilsonone on 2008-01-04
Having looked even further.  I suspect this is a video issue.  Another member made this remark in an adjacent forum.

Would the framebuffer have anything to do with my problem? To that end should I use the fb=false parameter during install?

---

### Post by Pumalite on 2008-01-04
You can do it also at the end of the installation, reconfiguring xserver amd choosing 'no framebuffer'

---

### Post by wilsonone on 2008-01-04
Just tried fb=false ... same result.
Progress bar appears up to 100% and then a blank/black screen.  The cdRom is still spinning but no response from the keyboard.  The only way to shut down is ... pull the plug.  Ouch.

---

### Post by jordanit on 2008-01-05
I haven't had much patience lately to play around with all the settings in here, but I've found a couple different distros that seem to work well.  One's Xfld (Xfce Live Demo CD), the installer runs smoothly without any headaches for me.  THe other one is DreamLinux, which is a bit heftier but works as well.  I had to tinker with some settings to get it to full size display, but nothing too crazy.  

I was looking at some of the above posts, and in one of them, the guy was talking about taking the Xorg.conf file from a working distro and doing a switcheroo with (in this case) Puppy Linux.  Is there a way to do this in Ubuntu or Xubuntu?  I've got the Xorg.conf file from Xfld (which works) on a USB key, but I just need to know when and how to do the switch.  In the other example, the guy mentioned hitting Cntrl+C to bring up a command line........I tried that all through the Ubuntu installation and had no such luck at getting a command prompt to do anything with.  do you think this approach will work with Ubuntu as well??  if so....how would I do the switch??!

thanks
jordanit

---

### Post by wilsonone on 2008-01-06
Thanks Jordanit.

I went and downloaded Xfld but encountered the same problem.

This can't be that tough.  The initial ubuntu install screen is displayed and then dies after the Linux kernel has been loaded.  This tells me that the install program must be selecting the wrong video driver and just needs to be bypassed.

I have been using xubuntu on an  older PII for the past 18 months and it has been very solid.

Is the link below the only web page that lists boot parameter options or is there another that is more extensive?
[https://help.ubuntu.com/community/BootOptions]("https://help.ubuntu.com/community/BootOptions")

Thanks

---

### Post by Pumalite on 2008-01-06
[http://grumpymole.blogspot.com/2007/...arameters.html](http://grumpymole.blogspot.com/2007/...arameters.html)
[https://help.ubuntu.com/7.04/install...oot-parms.html](https://help.ubuntu.com/7.04/install...oot-parms.html)
noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317

---

### Post by wilsonone on 2008-01-06
Thanks Pumalite.

I noticed you had mentioned these sites earlier,... I will address them with more vigor.  Will let you know when I hit on something.

Thanks

So ... several days later .. I have been playing with some of the boot parameters and have a screen full of text.
noapic nolapic acpi=off pci=noacpi pnpbios=off

  The install appears to have locked up at...
[   65.961638] Checking  'hlt' instruction...

I think my monitor is being shut off by the install disc for some reason.  Is that possible?

---

### Post by Pumalite on 2008-01-06
You are welcome. Good luck.

---

### Post by thierman on 2008-01-06
OK, some good new and Some bad news....

While doing a lot of work on this. I finally got a text only Ubuntu system to come up, and from there installed ssh, so I could login from another computer.

Just so you know, I got the text only up using the Alternate CD version of 7.10 ubuntu. 

Now, once I got to the same point of my install, with myself logged into the machine via ssh, I was able to see that Xorg was consuming 99% of the CPU. 

I did some searching on the net and found the following in the Debian bugs site:

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454304](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=454304)

Which identifies a bug in the xserver-org-core package. I downgraded this package to xserver-xorg-core_1.2.0-4, well, to the debian version, and now, at least Xorg is no longer in a CPU loop and I get something on my screen. Albite, the greeter trying and then failing. However, given that brute forced this in, this is no surprise....


The quesiton is, given what I've found, I'm wondering what the best solution is, force a downgrade for just the xserver-org-core back to a previous ubuntu version that predates the bug, or will there be an ubuntu version of this patch available soon? I'm writing this in haste to post what I've found. I admit, I'm not posting the solution yet. But at least I'm many steps closer, and letting people know there is hope, and this will be solved.

I guess  I could always try and install 6.0.6 LTS version and see if that works. 

If anyone has any suggestions I'm open before I start to put more time into this tomorrow.

            -C

---

### Post by aonegodman on 2008-01-07
WoW, I woke up this morning to the same problem after doing the Ubuntu upgrades yesterday.  Boots through usplash screen then blank black screen with a flashing cursor in upper left corner. Just sits there - no further progress. :confused:

Been looking over above posts and reading through them. I even tried copying the xorg.conf and menu.lst files off of my LiveCD Ubuntu 7.10 disk to my Ubuntu drive.

I mean since that boots up fine and I'm using it now to get on line and make this post and search solutions, right? Made sense to me anyway.

But it didn't work.   This isn't a boot problem per say is it? I mean grub is booting the system, it just crashes or halts when it gets past the Ubuntu splash screen.

So I mean it looks more like the XORG thing you guys are talking about. How do you do a restore(as in Windows) to last good system config? This brings up another question, what about System Emergency Disk for Ubuntu and how to make one?  Thanks.

Now I'm really a noob to the Ubuntu scene here and I'm really impressed with the forum and community support I find available. I know someone is going to figure this out. It's just frustrating since I depend so much on my computer and internet access for work.

Thanks to all for helping out.  =D>

---

### Post by halln on 2008-01-07
That thing happen to me as well what I did is I installed feisty 7.04 first, then update it with the latest kernel then after that I upgrade it using 7.10 alternate cd It works for me, give it a try

---

### Post by aonegodman on 2008-01-08
Listen up people!!   Regarding my above post on black screen, I have progressed since yesterday.

Now what I had done was reboot on a crash/lockup screen. I had a program hang and couldn't shut it down so I just hit the restart button on my computer.

What I didn't know was this - when an improper shut down occurs Ubuntu will run a chkdsk routine on restart to examine and fix disk errors. This is what the black screen was about. The phone or something happen to cause me to just walk away from my computer. When I came back about 10 minutes later my desktop was back and all was well.  :D

It would be nice if Ubuntu had some type of notification when it did this so us poor noobs knew what was going on behind the black screen.  :lolflag:

Perhaps there is a way to start and run Ubuntu in a command line visual mode?

---

### Post by thierman on 2008-01-09
Well, there is and there isn't....

You can always edit the boot options with F6 and strip off silent. 

PRoblem with this bug is, the moment xserver-xorg tries to start up it blanks the screen. And since it's in a inifiniteloop, you can't do anything. 

What I did, is install a command line only system from the Ubuntu Alternate CD, then using apt-get I installed the various packages I needed to bring X up. But before that, I made sure I had installed openssh, so I could login to the box. 

If you are having a fsck (checkdisk) issue, then simply stripping off the quiet flag from the boot options should allow you to see that, since I'm pretty sure fsck run's before the system tries to bring up X.

I also tried with the live CD to just add single to the options on the boot parameters, expecting that it would boot to single user mode (text only) without starting X. I was wrong. Only on the alternate CD.

---

### Post by jordanit on 2008-01-09
so, i still have not found an option that worked.   Although one thing that has worked for me Ubuntu-wise is installing the 7.04 desktop CD!  7.04 works for me, and that's enough to make me happy.  I haven't tried upgrading or anything yet, but I will in the future.  I had to burn it twice...it only worked the second time at a burn speed of 1x (hooray!).  I'll continue to keep my eye on this forum to see if anyone can come up with a fix for this issue!

Thanks for your help,
Jordan

---

### Post by wilsonone on 2008-01-10
Success :) -- No more Black Screen when installing Ubuntu.

The problem I was having turned out to be a boot parameter issue and not video.

I eventually hit on this pdf

[http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf]("http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf")

About two nights ago I was attempting an install of Xubuntu using the Alternate text only version.  Having pressed f6 and adding a nosplash parameter I noticed that the computer had stalled. The very last line of code on the monitor was a bunch of numbers  and 'hlt'.  Looking through the pdf (above) I found a reference to a boot parameter 'no-halt'.  According to the documentation .... 

**The 'no-hlt' parameter is available for use because the 'hlt' instruction does not work correctly for some x86 processors.  This option tells the kernel not to use the instruction.**

:smile:



As a result I went back to the original distro of Ubuntu 7.10, pressed f6 and added the boot parameter 'no-hlt' and everything went just fine.

One little six letter string made all the difference in the world.

[COLOR="Blue"][SIZE="4"]I would like to thank all of you for your input.  If it had not been for Pumalite and Jordanit pointing me in the direction of the boot parameters I would never have stumbled on a solution.  I'm still not totally clear on boot parameters but I've certainly learned a lot.[/SIZE][/COLOR]

---

### Post by thierman on 2008-01-12
Good news for those still battling the Xorg infinate loop problem. (Shows up a blank screen with cursor at boot) The problem I described above.

It's an Xorg bug, and the workaround has been posted in the following thread. It works for me... 

[http://ubuntuforums.org/showthread.php?p=4123324#post4123324](http://ubuntuforums.org/showthread.php?p=4123324#post4123324)

---

### Post by Pumalite on 2008-01-12
> **wilsonone said:**
> Success :) -- No more Black Screen when installing Ubuntu.

The problem I was having turned out to be a boot parameter issue and not video.

I eventually hit on this pdf

[http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf]("http://www.kernel.org/pub/linux/kernel/people/gregkh/lkn/lkn_pdf/ch09.pdf")

About two nights ago I was attempting an install of Xubuntu using the Alternate text only version.  Having pressed f6 and adding a nosplash parameter I noticed that the computer had stalled. The very last line of code on the monitor was a bunch of numbers  and 'hlt'.  Looking through the pdf (above) I found a reference to a boot parameter 'no-halt'.  According to the documentation .... 

**The 'no-hlt' parameter is available for use because the 'hlt' instruction does not work correctly for some x86 processors.  This option tells the kernel not to use the instruction.**

:smile:



As a result I went back to the original distro of Ubuntu 7.10, pressed f6 and added the boot parameter 'no-hlt' and everything went just fine.

One little six letter string made all the difference in the world.

[COLOR="Blue"][SIZE="4"]I would like to thank all of you for your input.  If it had not been for Pumalite and Jordanit pointing me in the direction of the boot parameters I would never have stumbled on a solution.  I'm still not totally clear on boot parameters but I've certainly learned a lot.[/SIZE][/COLOR]

I'm glad you got it to work for you. Happy Ubuntuing!

---

### Post by RunJun on 2008-01-12
I'm getting a similar problem but with a difference. I can boot the live cd, install, and start ubuntu 7.1 in recovery mode fine(except I can't do anything with users in recovery mode). But the normal boot it displays "Starting up..." but there's no activity at all until ab...

it just started.:confused: I took about 5 min but it started. It didn't display anything even though I took quiet out of the boot.

I added Pumalite's suggestion but I'm not sure that's what did it.
(noapic nolapic acpi=off pci=noacpi pnpbios=off vga=0x317)

I'm going to try restarting after updating see if i need to permanently add that boot parameter.

---

### Post by Pumalite on 2008-01-12
The boot parameters should be tried one at a time.

---

