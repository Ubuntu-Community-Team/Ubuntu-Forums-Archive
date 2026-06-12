---
title: "booting stalls during &quot;mounting root filesystem&quot;"
date: 2006-06-01
forum: Installation &amp; Upgrades
---

### Post by shoeshinecs on 2006-06-01
I cannot install Ubuntu 6.06 (Desktop). It loads the Linux kernel fine, but soon after it stalls when the "mounting root file system" statement apppears. I'm doubtful that the CD is corrupted because it works fine on my laptop. Also, I have two partions in my hard drive. They're both NTFS. I boot Windows off a different partition than the system partition. I know this is a problem, but could it also be a problem for Ubuntu?

Here are my specs: 

-Shuttle AN35N Ultra motherboard (nForce 2)
-Athlon XP Mobile 2500+ Processor
-Samsung SP1614N 160GB Hard Drive
-512 MB (Kingston?) Value Ram

If I wait long enough, the "mounting root file system" message clears and this appears:

[I]hdb:ide_intr: huh? expected NULL handler on exit
   hdb:ide_intr: huh? expected NULL handler on exit
   Buffer I/O error on device hdb, logical block 357298[/I]

---

### Post by denis.etienne on 2006-06-01
Same issue for me.
my /dev/hda is used for windows
my /dev/hdb is used for ubuntu 5.10
my /dev/hdc is dvd-rom

I have checked the checksum and it's ok.

Athlon XP 2200+
Samsung WriteMaster
512 MB

It displays:
[I]hdc:ide_intr: huh? expected NULL handler on exit
hdc:ide_intr: huh? expected NULL handler on exit[/I]

---

### Post by shoeshinecs on 2006-06-01
I did a search around the forums for "mounting root file system" and found an answer. Possibly, three.

First, when the "mounting root file system" error pops up, wait a few minutes until the shell loads. You'll know it loaded when the "hdb:ide_intr: huh? expected NULL handler on exit" error appears. Now, type *evms_activate*. Press CTRL-D. Wait about three minutes and see if things start getting okay'd. If not, type *mount-0 remount, rw // sbin / evms_activate *. Press ctrl-D. Wait a few minutes. This is what worked for me. If it doesn't for you, unplug all USB devices and restart the CD. Should work with no problems. Not sure.

Supposedly, the problem is that the USB devices are recognized in the wrong order causing it to stall. (I know someone can give a better answer. Please.)

Post to say how it goes. Good luck.

---

### Post by hsn on 2006-06-01
Same problem for me. CD-Rom drive and HD makes a strange noice. I'll try what shoeshinecs says.

---

### Post by rampus on 2006-06-01
I've a similar problem but "hdb:ide_intr: huh? expected NULL handler on exit" doesn't appear. After few minutes of installation start cd-rom and hdd stop working... and nothing happens. Ubuntu doesn't like samsung hdds?
My spec:
AMD64 3000+ Venice
MSI K8NGM2-FID GF6150
2x512MB Corsair VS
SAMSUNG SP1213N

---

### Post by tommy04 on 2006-06-01
This happened to me too. However, I got kind of angry and clicked a few times and hit a few keys in frustration, and it stopped hanging. This could be a coincidence, considering this never seems to work ever, but try either clicking the mouse a few times or hitting spacebar a few times. Who knows...

---

### Post by rampus on 2006-06-01
Unpluging all of the usb devices solved a problem:)

---

### Post by fkacct on 2006-06-01
I've also got the same problem.  I am trying to install 6.06 on a Sony Vaio Laptop with a Pentium 3 and PCMCIA CD drive.  The computer hangs for a minute or two at "mounting root file system" and then goes back to "Uncompressing Linux... Ok, booting the kernel." and hangs there infinitely.

---

### Post by gpw797 on 2006-06-01
Same thing here :( unplugged all USB devices and no help. Breezy installed fine on this machine... any alternative install methods?

---

### Post by rotten777 on 2006-06-01
I'm on the same boat. Samsung 300GB drives via SATA. The only USB device in use is my USB mouse. Very disappointing :(

I was wanting to get away from 5.10 today.

---

### Post by Freezepop on 2006-06-01
I'm encountering the same problem here, no USB devices connected. Trying to get Ubuntu onto a 15gb (TriGem) HDD.

---

### Post by rotten777 on 2006-06-01
wow. this seems to be a pretty common issue. 

now you see what happens when you rush releases.

---

### Post by tzutolin on 2006-06-01
I have exactly the same problem as well.

---

### Post by fkacct on 2006-06-01
I can't even reach the command prompt to type:  "evms_activate" and there are no devices connected to my Sony Vaio's USB port.  Has anyone found a solution to this?

---

### Post by Geekboy on 2006-06-01
I am having the same error.  It takes forever to get past Mounting Root filesystem.

It then starts to posting this error:

Buffer I/O error on device hdc, logical block 1. 

It lists logical blocks 0 through 15.  I did find [this]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667") []("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667")under bugs for dapper.

---

### Post by PirahnaBreaks on 2006-06-02
I've had the same error, with "mounting root file system" on the splash, and I/O errors on the verbose mode.  What conditions need to be present for the evms_activate command to work?  Do I need a shell proper, or can I just type it in in the midst of all the spam?  Unplugging all my USB devices really isn't a feasible workaround, as my keyboard is USB.

---

### Post by rcarring on 2006-06-02
This is not due to Dapper, this is due to the cd being popped out before Dapper had finished with it when completing the installation. Wait till you get the reboot message and reboot with the cd still in the drive, then pop the drive while the diag / splash of your pc is loading, not before.

---

### Post by lotos on 2006-06-02
I have exactly the same problem as well.

---

### Post by PirahnaBreaks on 2006-06-02
[QUOTE=rcarring]This is not due to Dapper, this is due to the cd being popped out before Dapper had finished with it when completing the installation. Wait till you get the reboot message and reboot with the cd still in the drive, then pop the drive while the diag / splash of your pc is loading, not before.[/QUOTE]

Uh...

Most of those who've posted here are unable to proceed to that point in the installation - at least in my case, the error is appearing during the CD boot process - no rebooting involved here, and no chance of the CD being unmounted.

---

### Post by fastb on 2006-06-02
Well I guess there are a lot of people with the same problem. I have the sam problem and it gets pass the "mounting root filesystem" if I disconnect the USB mouse but that is just not the option for me. I need my mouse ofcourse.
Nothing happens even if I wait for half an hour.

---

### Post by Odisej on 2006-06-02
I opened another thread being unaware that this was already discussed. Here is the link: [http://www.ubuntuforums.org/showthread.php?t=186608](http://www.ubuntuforums.org/showthread.php?t=186608)

Anyway, it is happening on my system too but it does seem to stop in about 10 minutes and the Ubuntu is loaded just find at the end. 

Try to wait a little bit, maybe it will work for you too. oh, and it is the same on both versions, 32 and 64 bit.

Odisej

---

### Post by Norm 2782 on 2006-06-02
Same here... it boots fine on my laptop where I have Ubuntu running since Hoary, but my mom's PC with a Win XP install refuses to boot the CD. No hd huh? errors or whatever... just hangs at Preparing Device Drivers and if I'm "lucky" at Mounting Filesystems or something...

---

### Post by Straker on 2006-06-02
As stated in another thread - I am also getting the huh? bug on hda.

I have a WD hard drive 160mb using SATA.  Surely this can't be a SATA bug.

I do have a Samsung CD/DVD drive, and as seen in a bug report and this thread so do others.  Could this be a major bug relating to Samsung drivers?

Also, this is a Breezy PC only, with no USB devices attached.

If you get this error, could you please verify if you have any Samsung devices?

---

### Post by gpw797 on 2006-06-02
No samsung here IBM HDs... that probably not the issue.

---

### Post by mkruse on 2006-06-02
Just wanted to chime in. I'm having this problem as well on my Toshiba satellite laptop. I don't see the "huh" part, but when trying to boot from the CD, it stalls at "Creating LiveCD user", then after a couple of minutes it clears to text screen and starts spitting out lines like "Buffer I/O error on device hdb, logical block NNNNN"

---

### Post by rotten777 on 2006-06-02
[QUOTE=mkruse]Just wanted to chime in. I'm having this problem as well on my Toshiba satellite laptop. I don't see the "huh" part, but when trying to boot from the CD, it stalls at "Creating LiveCD user", then after a couple of minutes it clears to text screen and starts spitting out lines like "Buffer I/O error on device hdb, logical block NNNNN"[/QUOTE]


that's not the same problem.

---

### Post by rotten777 on 2006-06-02
[QUOTE=rcarring]This is not due to Dapper, this is due to the cd being popped out before Dapper had finished with it when completing the installation. Wait till you get the reboot message and reboot with the cd still in the drive, then pop the drive while the diag / splash of your pc is loading, not before.[/QUOTE]

This is definitely due to Dapper.
I've downloaded 2 ISO files, burnt 4 CD's, and it won't even get to the first setup screen. Safe graphics mode does the same thing for me.

I'm really curious as to what testing was done before this was considered a final release.

---

### Post by rotten777 on 2006-06-02
[QUOTE=gpw797]No samsung here IBM HDs... that probably not the issue.[/QUOTE]


Does everyone have some other partition type on any of their drives?
I know I've got NTFS and FAT32 partitions on 2 different drives.

---

### Post by fastb on 2006-06-02
I wonder why doesn't anybody that had to do something with the final ubuntu says what is the solution to our problem, or why that problem accures?

---

### Post by Squibble on 2006-06-02
Same problem here installing Kubuntu on a Thinkpad T21 - the graphical installer just hangs and the DVD drive makes nasty grinding noises. The text mode installer seems to work, at least so far.

---

### Post by papernik on 2006-06-02
I had same problem, but this solve mine :

put 'irqpoll' in boot options

This was OK for me

try and make me know


bye

paper

---

### Post by rotten777 on 2006-06-02
[QUOTE=Squibble]Same problem here installing Kubuntu on a Thinkpad T21 - the graphical installer just hangs and the DVD drive makes nasty grinding noises. The text mode installer seems to work, at least so far.[/QUOTE]


this sounds like more of a bad media issue.

---

### Post by Squibble on 2006-06-02
[QUOTE=rotten777]this sounds like more of a bad media issue.[/QUOTE]
Unlikely, I verified the burn. Possibly the image was bad to begin with, this is what I've got:

415692829ebc4d5a54e5ce6a4f15f1a6  kubuntu-6.06-dvd-i386.iso

---

### Post by rotten777 on 2006-06-02
[QUOTE=Squibble]Unlikely, I verified the burn. Possibly the image was bad to begin with, this is what I've got:

415692829ebc4d5a54e5ce6a4f15f1a6  kubuntu-6.06-dvd-i386.iso[/QUOTE]


check the md5's on the ftp.

bad programming won't cause your DVD-ROM to grind and make weird noises though. it'll just crash/freeze/not work.

---

### Post by Squibble on 2006-06-02
[QUOTE=rotten777]check the md5's on the ftp.

bad programming won't cause your DVD-ROM to grind and make weird noises though. it'll just crash/freeze/not work.[/QUOTE]
The DVD md5sums aren't available anywhere (that I can access at least). If you read through the thread you'll notice I'm not the only one experiencing noise from their optical drive. If a bug somewhere causes the loader to read bad data it might well sit in a loop forever, trying to re-read it.

---

### Post by mrobbert on 2006-06-02
I experienced this problem on an IBM Thinkpad T42 after an upgrade from 5.10. I was able to get booted up by choosing the kernel from 5.10 (2.6.12something). That kernel works fine no matter what. I tried the 6.06 kernel with the irqpoll option and that did not help me at all. I then pulled my laptop out of the docking station that it was in the whole time and the problem is gone. Somebody had suggested problems with USB and my docking station has a number of USB devices plugged in so that may be it. I'll try adding some USB devices out of the docking station and try the docking station with no extra devices to see if I can find a problem device or combination, but this definitely looks like a kernel problem.

Thanks,
Mike Robbert

---

### Post by rotten777 on 2006-06-02
[QUOTE=Squibble]The DVD md5sums aren't available anywhere (that I can access at least). If you read through the thread you'll notice I'm not the only one experiencing noise from their optical drive. If a bug somewhere causes the loader to read bad data it might well sit in a loop forever, trying to re-read it.[/QUOTE]

well re-reading data constantly is not the same as "nasty grinding noises"

---

### Post by Taloen Loch on 2006-06-02
I'm hung at the "Uncompressing Linux... Ok, booting the kernel" too.  No ideas at all on how to solve this problem anyone?

---

### Post by mrobbert on 2006-06-02
OK, I'm back and my problem is definitely with the docking station. I can plug any combination of USB devices into the laptop while undocked, but the laptop in the docking station with nothing plugged into the docking station causes it to stall while mounting /.  I'm not real sure how to debug anything at this low of a level, but I'm willing to give it a shot if anybody can send some suggestions.

Thanks,
Mike Robbert

---

### Post by Squibble on 2006-06-02
[QUOTE=rotten777]well re-reading data constantly is not the same as "nasty grinding noises"[/QUOTE]
Yeah, because after receiving bad data a program would never try to reset/re-initialize the device. Anyway, the text-mode install completed successfully and the checksums of the installer files are correct.

---

### Post by Odisej on 2006-06-02
This is an update to my previous post:

I finally installed the latest Ubuntu even if I got that strange error at the beginning. As I said, with me the error is repeating  itself for about ten minutes and then the loading of the Live CD continues. 

After the system came up (it takes quite a while but I am not sure if this has anything to do with the initial errors) I finally installed it on the hard disk and all went smoothly.

Now, when booting from hdd there are no errors at all. 

I did not unplug any USB devices or did anything else to the computer. 

There was a question about Samsung DVD/CD Drives from somebody on this thread. Yes, I have one as well (SH-W162C).

Odisej

---

### Post by Taloen Loch on 2006-06-02
I've a couple of Samsung drives in my machine too.  Nothing in the USBs right now though.

---

### Post by NickeM on 2006-06-02
I have the same problem i can't boot from 2.6.15-23-686 which halts at "mounting root file system" but booting from 2.6.15-23-386 works fine! have tried removed all connected usb devices and running evms_activate but to no avail. 

My harddrives:
120GB Seagate Barracuda 7200.7 ST3120022A 7200 RPM IDE Ultra ATA100
160GB IDE Maxtor 6Y160PO HDD 8MB-Cache, Specifications; Maxtor DiamondMax 10 - hard drive - 160 GB - ATA-133

Does anyone have a solution, it would be nice to see dapper at its best =)

---

### Post by Straker on 2006-06-02
[QUOTE=Odisej]I finally installed the latest Ubuntu even if I got that strange error at the beginning. As I said, with me the error is repeating  itself for about ten minutes and then the loading of the Live CD continues.[/QUOTE]

Yes - This worked for me too.  About ten minutes of "huh?" errors then the CD boots.  I am posting from dapper right now.

So...be patient, and it might load.  Mind you, I am running an Athlon X2 4400+ and it still took 10 minutes, so be patient...

cheers.

---

### Post by PirahnaBreaks on 2006-06-02
I tried booting without USB devices plugged in - the LiveCD came up fine (woo!) and I was able to plug USB devices back in and proceed with the installation.

First boot from the hard drive worked flawlessly as far as USB is concerned - now I have to figure out how to get Ubuntu to speak VLAN tagging in order to get to the Internet.  ](*,)

---

### Post by denis.etienne on 2006-06-02
Solved :) 

DVD writer : TSSTCorpCD/DVDW TS-H552U (i.e. Samsung WriteMaster)
CD Writer: LITE-ON LTR-40125S

Install using DVD device: failure
Install using CD device: worked perfectly

It seems that was a device issue.

---

### Post by fkacct on 2006-06-02
Still havn't found a solution for my sony laptop.  I have tried all the tips but to no avail.  Unfortunately, I can't even try a different CD drive as the laptop doesn't boot via USB and it is currently using a PCMCIA CD Drive.  Don't want to go back to Breezy....

---

### Post by Straker on 2006-06-02
[QUOTE=denis.etienne]Solved :) 

DVD writer : TSSTCorpCD/DVDW TS-H552U (i.e. Samsung WriteMaster)
CD Writer: LITE-ON LTR-40125S

Install using DVD device: failure
Install using CD device: worked perfectly

It seems that was a device issue.[/QUOTE]

Yep - I have a TSSTcorpCD/DVDW SH-S162L (Samsung WriteMaster) - so maybe this is related to the Dapper CD not being able to read from itself in a Samsung drive?  Just maybe?

---

### Post by Freezepop on 2006-06-02
Hm, I'm also trying to install usoing a Samsung CD/DVD drive (SD-612).

---

### Post by jt_jam on 2006-06-02
Same problem here... I upgraded yesterday to DD and I can't boot with any USB device :(

I tried this :
[QUOTE=papernik]
put 'irqpoll' in boot options
[/QUOTE]
but the problem is still here.
I miss my mouse ](*,)

---

### Post by Patrick-Ruff on 2006-06-02
argh, same problem. Dell Inspiron 6000, no such USB devices whatsoever. I'de rather not wait for the discs to come.... this never happend with breezy.

---

### Post by Patrick-Ruff on 2006-06-02
adding root= to the boot options seems to help alot, its gotten much further then it ever has.

---

### Post by Patrick-Ruff on 2006-06-02
Yep!!! It Worked Perfectly!!!!!

---

### Post by fkacct on 2006-06-02
[QUOTE=Patrick-Ruff]adding root= to the boot options seems to help alot, its gotten much further then it ever has.[/QUOTE]

so I just press F6 for boot options and add "root=" ????????????  

Thanks

---

### Post by Patrick-Ruff on 2006-06-02
apparently so, but now after install, the boot fails to mount root... argh... well, consider it partially solved...

---

### Post by fkacct on 2006-06-02
my boot options already lists this: "root=/dev/ram rw quiet splash --"

---

### Post by Patrick-Ruff on 2006-06-02
I added root= at the end of that --. also, I was able to boot it in recovery mode, and then I got a consol and typed startx, still doesn't seem completely stable tho, I got an error at start.

---

### Post by fkacct on 2006-06-02
Ok, will try that right now and let you know how mine goes.....

---

### Post by Patrick-Ruff on 2006-06-03
ok.

---

### Post by Patrick-Ruff on 2006-06-03
any luck dude? I can get it to boot up with the safe-mode type thing, but I'de rather not boot up EVERY time like that... I reconfigured my xorg file, no luck whatsoever.

---

### Post by solstice on 2006-06-03
I'm having same issue as well. just figured i'd add myself to those having issues.

---

### Post by fkacct on 2006-06-03
I just put "boot=" at the end of boot options and I now go to a shell prompt a minute after seeing "mounting root file system."  I get this message at the prompt: "/bin/sh: can't access tty: job control turned off"  

This sucks....

---

### Post by Patrick-Ruff on 2006-06-03
I'm afraid I'm in the same situation. did you get through the installation? I did, but now I can't boot up without doing the recovery mode.

---

### Post by fkacct on 2006-06-03
couldn't even get through the installation on my laptop........this release is definately lacking....

---

### Post by mjziegle on 2006-06-03
I too had problems with the install.  I used the alternate CD.

I had problems getting a software raid setup.  It seemed to take forever.

You can start another session using <ctrl>+<alt>+f2 and then hitting enter.

Check what processes are going on using ps.  Take a look at dmesg and /var/log/messages.

For me it turned out my raid was rebuilding.

I've found that the partitioner doesn't works particularly well.  My recommendation would be to setup the partitions, reboot, then install.  I often got errors that the filesystems couldn't mount but the answer was always in dmesg.

FWIW I never had any trouble with any of the beta releases.  All this started up with the multiple CD concept in the RC and now LTS.

Another note, SATA seemed to give me more problems than IDE ones.

-matt

[QUOTE=fkacct]couldn't even get through the installation on my laptop........this release is definately lacking....[/QUOTE]

---

### Post by sfantu on 2006-06-03
Well I've installed on a 20 gig usb hdd, and after reboot hangs on mounting root file system, no error messages, no nothing even after 30 min.

---

### Post by jt_jam on 2006-06-03
Here is the way i solved my problem : [http://www.ubuntuforums.org/showthread.php?p=1085962#post1085962](http://www.ubuntuforums.org/showthread.php?p=1085962#post1085962)

---

### Post by manicka on 2006-06-03
The easy way is to download the alternate iso image and do a good old fashioned  text based install.

The desktop live cd definitely leaves a lot to be desired

---

### Post by herby on 2006-06-03
I gotsthe same problem, upgrade from 5.10 via synaptic, hangup at "mounting  root file system" when booting kernel 2.6.15. After some time the system reboots, and there are no problems choosing kernel 2.6.12 from the grub-list!?!?

---

### Post by Patrick-Ruff on 2006-06-03
well, I managed to get past the initial install hang, install the system, but now it doesn't boot up. it always says unable to mount root. 
hence I'm on dialup, and it really isatn easy just to download a 700MB file. I'de rather get this solved without having dl a 'alternate' install cd....

---

### Post by Patrick-Ruff on 2006-06-03
[QUOTE=jt_jam]Here is the way i solved my problem : [http://www.ubuntuforums.org/showthread.php?p=1085962#post1085962](http://www.ubuntuforums.org/showthread.php?p=1085962#post1085962)[/QUOTE]
I think completely disabling USB devices is kinda out of the question... I'm definately not killing USB to get dapper running, when dapper should bloody run correctly in the first place.

---

### Post by Patrick-Ruff on 2006-06-03
Well, once again, I can get it to boot in recovery mode, but thats no way to run a bloody computer. what can be changed within recovery mode that could possibly fix this problem? on the boot screen, it does the exact following

(shows the whole ubuntu boot screen with the status bar and the details below)

Loading essential Drivers...                                                              ok
Mounting root file system...                                                                
Waiting for root file system...                                                                 



then after about 10 mins, it loads a BusyBox shell.  not the regular Linux shell, you cannot log on to root with this shell, startx does not work either. none of the sudo commands work.

---

### Post by XomboX on 2006-06-03
I have got a similar problem, it stucks for a while during "**Mounting root file system**". After 3 minutes it writes
[I]Uncompressig Linux... Ok, booting the Kernel.
[4294007.545000] hda: drive not ready for command[/I]

Nothing from this forum helped :-(

I have got an Hitachi [COLOR="Red"]SATA[/COLOR] 250GB harddisc. ](*,)

I have just tried to install Breezy and it worked perfectly. It must be a serious problem with Dapper and SATA discs!

---

### Post by Patrick-Ruff on 2006-06-03
this is kinda messed up, there has been FAR more people mentioning this issue, rather then people actually trying to help..this is not how problems are solved people...

---

### Post by Patrick-Ruff on 2006-06-03
appologies for the double post, internet lag.

---

### Post by ubuntu_demon on 2006-06-03
This is not a guide but a request to test. As it's quite cryptic. Apparantly it works for (some) people so I will write a guide later on. 

I have had a similar problem. Please **test** this solution. In my case I had to find out /dev/hda had become /dev/hde and I had to change that in my /boot/grub/menu.1st and in my /etc/fstab. I don't know the easiest way to find out what device it has become. You might start gparted from the desktop cd to find out. During reboot you can press esc to get into the grub menu and press e to alter the devicename. Then press b to boot. You will boot into the terminal if all goes well. Now change your /etc/fstab and /boot/grub/menu.1st.

Here are some links. I don't have time right now to really dive into this problem.

To avoid **this problem** prior to upgrading look here :
[http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2)

Having problems with installing or upgrading to Dapper? Here are some fixes
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

If someone has a good and understandable fix to this problem please post it here :
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

good luck all! :)

---

### Post by Patrick-Ruff on 2006-06-03
KICK ***!!! IT WORKED!!! it turns out those 2 files were set to a different hard drive that didn't even exist!!! either way, it works now, it DID take a min to mount root but I can deal with that. :)

---

### Post by XomboX on 2006-06-03
[QUOTE=ubuntu_demon]I have had a similar problem. Please **test** this solution. In my case I had to find out /dev/hda had become /dev/hde and I had to change that in my /boot/grub/menu.1st and in my /etc/fstab. I don't know the easiest way to find out what device it has become. You might start gparted from the desktop cd to find out. During reboot you can press esc to get into the grub menu and press e to alter the devicename. Then press b to boot. You will boot into the terminal if all goes well. Now change your /etc/fstab and /boot/grub/menu.1st.

Here are some links. I don't have time right now to really dive into this problem.

To avoid **this problem** prior to upgrading look here :
[http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2](http://www.ubuntuforums.org/showpost.php?p=1087008&postcount=2)

Having problems with installing or upgrading to Dapper? Here are some fixes
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

If someone has a good and understandable fix to this problem please post it here :
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

good luck all! :)[/QUOTE]

Sorry, I am a beginner and I don`t understand to your post :-(

---

### Post by adament on 2006-06-03
Not to sound disrespectful towards the forum staff but ubuntu_demon since you aren't specifying which subproblem you are referring to I believe you are trying to solve the common problem. However this problem is about not being able to boot from the desktop/live install cd, thus changing /boot/grub/menu.1st or /etc/fstab isn't really an option. However you might be referring to Patrick's problem which seems to have developed into something else. EDIT: This was apparently referring to Patrick's problem or at least it worked for him.

Besides I believe this might actually be several different problems giving the same symptom. I believe this because of the diversity of seemingly unrelated solutions. Besides there's also errors messages like this:
> hdb:ide_intr: huh? expected NULL handler on exit
hdb:ide_intr: huh? expected NULL handler on exit
Buffer I/O error on device hdb, logical block 357298
And without the huh? errors like this:
> Buffer I/O error on device hdb, logical block 357298
Xombox mentions a third set of errors:
> Uncompressig Linux... Ok, booting the Kernel.
[4294007.545000] hda: drive not ready for command

Patrick mentions that a lot of problem descriptions has been posted but no solutions and I thought I would just summarise what I had found of different solutions.

[LIST]
[*]Use evms_activate -- I couldn't get this to work but it only seems that this worked for shoeshinecs however to get his instructions look here: [http://www.ubuntuforums.org/showpost.php?p=1078025&postcount=3]("http://www.ubuntuforums.org/showpost.php?p=1078025&postcount=3")
[*]Remove all USB devices -- Didn't work for me
[*]Disable USB2 in the BIOS -- I didn't try this, but it should be related to the former solution
[*]Just wait -- This seemed to work for a number of people having to wait for 10 or more minutes with errors and the installer then suddenly continuing, this didn't work for me however
[*]Input irqpoll as a boot option -- This worked for some, personally I used both irqpoll noapic and nolapic and then I had to wait 10 minutes like in the solution above other boot options of use might be acpi=off pci=noacpi noacpi
[*]Patrick mentioned adding root= as a boot option had worked for him -- I haven't tried this but apparently it gave him problems when trying to boot the installed system. I believe the problems arising when trying to boot the installed system might be solved by changing the boot options in GRUB as explained by ubuntu_demon. EDIT: Due to the time it took for me to write the post, since then Patrick has confirmed that ubuntu_demon's tips worked solving his problems after the installation.
[*]Using a different CD drive -- I haven't tried this but it would sound logical since it arises from those Buffer I/O errors on the CD-rom drive.
[*]If all else fails the alternate install disc should work.
[*]Mjziegle mentioned something about a raid problem of his which had simmilar symptoms, [http://www.ubuntuforums.org/showpost.php?p=1085511&postcount=65](http://www.ubuntuforums.org/showpost.php?p=1085511&postcount=65)
[/LIST]

I hope I got all the different solutions in this post else I will try to edit it and update it with more info.

To Xombox:
Since your error refers to the hda drive and you are saying you use SATA disc for hdd, I believe this error is not related to the SATA disc, since it should have been called sda(at least as far as I know -- please correct me if I am wrong).

EDIT: I added the list of fixes to the dedicated fix thread, currently however the post doesn't include anything not included in this post.  [http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11")

---

### Post by Patrick-Ruff on 2006-06-03
it was *kinda* referring to my problem, however, somehow, I managed to get it to install, then I booted it up in recovery mode, edited the files that ubuntu_demon mentioned. and now it boots up and works perfectly... so, fiddle with the install options, thats how it worked for me.

---

### Post by adament on 2006-06-03
[QUOTE=Patrick-Ruff]it was *kinda* referring to my problem, however, somehow, I managed to get it to install, then I booted it up in recovery mode, edited the files that ubuntu_demon mentioned. and now it boots up and works perfectly... so, fiddle with the install options, thats how it worked for me.[/QUOTE]
Do you remember if you added/changed any install options beside adding root= as you mentioned in one of your prior posts. I would just like to assemble all information about fixs for this/these problem(s). :-) So the next people won't have to read 8 pages of posts like we had to.

---

### Post by XomboX on 2006-06-03
adament: you are doing a good job, man! Thx!
I do really use SATA disk and I wonder why it says "[COLOR="Red"]hda:[/COLOR] drive not ready for command".

Guys, tell me, why I can install breezy so easy and dapper always stucks?

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=Patrick-Ruff]it was *kinda* referring to my problem, however, somehow, I managed to get it to install, then I booted it up in recovery mode, edited the files that ubuntu_demon mentioned. and now it boots up and works perfectly... so, fiddle with the install options, thats how it worked for me.[/QUOTE]
I was referring to this problem of yours :

> 
I cannot install Ubuntu 6.06 (Desktop). It loads the Linux kernel fine, but soon after it stalls when the "mounting root file system"


It wasn't advice it was a request to **test** my solution. Because I don't know whether everyone who experiences the stalling during the "mounting root file system" is helped by my solution.

When I have more time(I'm just a volunteer) I will explain my solution in a more elaborate way.

I am requesting that everyone posts his fixes and tips in this thread :

[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

That will make it easier for us forum staff to make this list more understandable and complete :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=adament]Do you remember if you added/changed any install options beside adding root= as you mentioned in one of your prior posts. I would just like to assemble all information about fixs for this/these problem(s). :-) So the next people won't have to read 8 pages of posts like we had to.[/QUOTE]
Would you be so kind to post hem here ?
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

This might help a lot of people ! :)

---

### Post by XomboX on 2006-06-03
OK. Problem was with my ASUS DVD/CDROM E616. I tried different CDrom and it works. However I have got another problem: I can not part my disc, it says some errors :(

---

### Post by adament on 2006-06-03
[QUOTE=ubuntu_demon]Would you be so kind to post hem here ?
[http://www.ubuntuforums.org/showthread.php?p=1086319](http://www.ubuntuforums.org/showthread.php?p=1086319)

This might help a lot of people ! :)[/QUOTE]
I added the list of fixes to the thread, and I intend to try and keep the post up to date as new fixes/information emerge. [http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11")

---

### Post by ubuntu_demon on 2006-06-03
[QUOTE=adament]I added the list of fixes to the thread, and I intend to try and keep the post up to date as new fixes/information emerge. [http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11")[/QUOTE]
thank you very much!

I'll probably add the fix(es) after I've slept.

---

### Post by irusun on 2006-06-03
Same problem - stuck at "mounting root file system".

Same problem with both the desktop-386 CD and the server-386 CD.

I tried unplugging all USB peripherals, but that didn't help.

Breezy Badger worked fine.

System:
AMD Opteron 170 (dual core)
ASUS A8N SLI Premium motherboard
Seagate Barracuda IV 80GB PATA
(Windows on NTFS partition 1, data on NTFS partition 2, unformatted partitions on 3, 4 and 5).  All partitions created during Windows setup (just installed yesterday).

---

### Post by irusun on 2006-06-03
Okay, a bit of egg on my face :oops: 

It was a "hard drive" issue... I won't go through the whole story, but, in addition to my "new" hard drive, I (intentionally) had a "bad" additional hard drive hooked up via the PATA cable but with the power cable *unplugged* - I thought if it was unplugged, it would be ignored by the system.  By disconnecting the PATA cable, the desktop-i386 CD works now.  I discovered this was the problem by trying to re-install Breezy Badger and saw that it was hanging on trying to load the IDE drivers.

---

### Post by rotten777 on 2006-06-03
interesting. it seems we have a few issues mixed in the same thread.

i'm still without fix though. adding 'root=' did nothing.

i don't have another cd-rom to test but i've done this with 4 cd's and 2 iso sources. and it's the burning and reading works fine in breezy. so i know the drive isn't failing. i can even copy all the data from the install cd to my hard drive without errors.

is there anywhere i can look that would be more specific than "huh?"  ???????


setup:

sata drive 1: 300GB Samsung - 50% ubuntu 5.10, 50% ntfs xp pro x64
sata drive 2: 300GB Samsung - 100% fat32

AMD X2 4400, 2GB RAM, Geforce GTX 7800OC, Biostar motherboard.

---

### Post by bobt12 on 2006-06-03
I have been having the same problem as most of you have freezing at mounting root file system. I tried several of the boot options with no luck. I finally decided to try what I used on a few other Linux system installations that would hang like Mandrake and Mepis. I typed (ide=nodma) at the boot prompt. It has started installing. I cannot attest to how well it works out yet. I will post back at let everyone know how I make out.

---

### Post by loconet on 2006-06-03
I'm on a similar boat. In my case I upgraded from Breezy through the Update Manager. The installation went through successfully, it then proceeded to reboot my system. It stalls on "mounting root file system" then continues in "Waiting for root file system" and stalls there for 5 mins or so then kicks me to the shell saying /dev/hda4 is not found. So far I have experienced this using the 2.6.15-23-386 boot option as well as 2.6.12-9-386. I can boot fine on 2.6.12-10-386.

---

### Post by bobt12 on 2006-06-03
Looks like the installation was a success. I did a quick check of a few things inserted a cd it mounted and I was able to eject it, plugged in a thumb drive, it mounted and I was able to copy from it. Opened Firefox was able to go online. The only thing that did not go right was hibernate and suspend. Neither one worked. I choose shut down and that worked ok.

---

### Post by adament on 2006-06-04
[QUOTE=loconet]I'm on a similar boat. In my case I upgraded from Breezy through the Update Manager. The installation went through successfully, it then proceeded to reboot my system. It stalls on "mounting root file system" then continues in "Waiting for root file system" and stalls there for 5 mins or so then kicks me to the shell saying /dev/hda4 is not found. So far I have experienced this using the 2.6.15-23-386 boot option as well as 2.6.12-9-386. I can boot fine on 2.6.12-10-386.[/QUOTE]
Take a look at ubuntu_demon's guide to fixing menu.1st and /etc/fstab. Could sound like an issue with those. [http://www.ubuntuforums.org/showpost.php?p=1087417&postcount=76]("http://www.ubuntuforums.org/showpost.php?p=1087417&postcount=76")
EDIT: Sorry I had somehow managed to overlook that you had upgraded and wasn't doing a fresh install.

---

### Post by adament on 2006-06-04
[QUOTE=rotten777]interesting. it seems we have a few issues mixed in the same thread.

i'm still without fix though. adding 'root=' did nothing.
[/QUOTE]
Could you please list all the different of the proposed fixs you have tried and the result of trying each?[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11")

---

### Post by jt_jam on 2006-06-04
[QUOTE=Patrick-Ruff]I think completely disabling USB devices is kinda out of the question... I'm definately not killing USB to get dapper running, when dapper should bloody run correctly in the first place.[/QUOTE]

I disabled USB2 only, so that my USB2 hardware works as a USB1 device.

---

### Post by HighOrbiter on 2006-06-04
I'm having a similar problem installing Ubuntu 6.06 on my HP Compaq nx9005 (which happly runs the Breezy Live CD). 

The kernel loads up, but then the Live CD stalls once "mounting root file system" appears. Then, after about 10 mins, I end up at a shell with several errors on screen:

```
Buffer I/O error on device hdc. Logical block 357241.
Buffer I/O error on device hdc. Logical block 357249.
Buffer I/O error on device hdc. Logical block 357280.
```
I get about 10 of these errors, all with differing block numbers, and then something similar to whats below (sorry, typing this bit from memory):

```

SQUASHFS error. Sb-bread failed reading block 0x9b56c.
VFS. Trying to free free buffer.
VFS. Trying to free free buffer.

```
I don't think the CD is corrupted as I've checked the md5. 

I've tried the fixes give in [http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11]("http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11") but they don't seem to have any effect. The only one I can't try is to use a different CD drive, as i'm using a laptop.

Does anyone have any more ideas?

Thanks.

---

### Post by bobt12 on 2006-06-04
Check my previous post. I got it to work by typing ide=nodma at the boot prompt. To get the boot prompt go to OTHER OPTIONS, I think it is F6.

---

### Post by fastb on 2006-06-04
OK, I disabled USB 2.0 support in bios and I managed to install it successfully. It booted to my installed system and it worked ofcourse without USB2.0 support. My USB mouse worked. But after about 2 minutes my mouse stoped working and the only option for me was to reboot the computer. So, solving(kind of) one problem caused another one. 
I don't think Ubuntu people should release that kind of system.

---

### Post by therunnyman on 2006-06-04
It's a mismount problem, well documented, reported a thousand times, confirmed a thousand times, but the devs aren't responding.

Here's the long and short of it: various PCI, PCI-X, PCI-express, USB, etc. devices are being loaded before hard disks.  For instance, the problem I have here is I've got three SATA hard disks all told, two mobo, one hooked into a PCI Promise SATA controller.  Installation goes well, but when trying to reboot, it hangs where you guys are hanging.  This is beacuse somewhere between installation and reboot, the drive connected to the PCI controller is assigned the "sda" designation, when it should be sdc.  Dapper then cannot find a root fs, simply because the drives are misnamed, that is, Dapper is installed, but not where it thinks it is. 

There are workarounds, but they're sloppy as hell.  First one: figure out what's loading when, then physically rewire.  Second one: edit grub by either pressing E on the boot option you're having problems and directing grub to the disk Dapper thinks it's on.  Third one, edit menu.lst to direct Dapper to wherever it thinks it resides.  Fourth one: yank your ancillary SATA drives, your sound card, disable USB in the BIOS, and forget about using those (it's okay to leave your etherenet enabled, apparently).

therunnyman

---

### Post by Patrick-Ruff on 2006-06-04
I'm pretty sure this is merely a misconception of the system, it thinks the hard drive is named differently, so it trys to mount root to a hard drive that doesnt exist.  try the instlal options 'root=/dev/hda,sda,hda1,hda2,sda1,sda2' untill one or the other works.

---

### Post by rotten777 on 2006-06-04
I finally got it working. 

Quite a pain.

I used the instructions to upgrade via the alternate CD and apt-get dist-upgrade.

There were quite a few hiccups in the upgrade where I read the errors (basically apt refused to overwrite some files so I manually deleted them and restarted with the apt-get install -f command).

The second problem was it didn't install the AMD64-K8-SMP kernel.

The third problem was grub removed my entry for x64 Pro on /dev/sda1.

The fourth problem was that my nVIDIA graphics didn't work. X was complaining it couldn't load GLX (submodule wouldn't load) so I commented it out, re-ran the NVIDIA driver that I previously saved to disk, used dpkg-reconfigure to reconfigure X and chose the nvidia driver as opposed to the vesa or nv it recommended.

Finally it came up. I just need to restore my x64 boot menu entry, clean up some icon theme issues, and test everything. Unfortunately Rhythmbox forgot how to play mp3's again... so i'll hunt that down so I can have a soundtrack to fixing Ubuntu.


It's a wonder why average folks don't use linux....................... lol

---

### Post by gpw797 on 2006-06-04
I had same problem, ended up downloading the alternate disk and it got past that point but them hung up at seting up clock part... grrrr

I finally ended up reinstalling breezy, updating, then upgrade manager to dapper. Installation has taken a BIG step backwards since Breezy (which worked fine for me).

---

### Post by mpbretl on 2006-06-04
I reported this bug back in March:
[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.15/+bug/36667)

It got marked as a duplicate of bug #34172, which I didn't agree with, and then #34172 got rejected.

It's a pretty helpless feeling to report something 2+ months in advance of release, and see nothing done about it.  In fact, worse than nothing, since the bug report was rejected.

Not happy.  [-(

---

### Post by lbolla on 2006-06-05
I've spent most of the weekend reading all these posts and trying to install Dapper.
It came out that none of the suggestions worked A PART FROM ONE: use the ALTERNATE CD and the text-mode install.
It worked for me!

---

### Post by prince_sabin on 2006-06-05
My Old (PIII 450 mhz) computer had this problem with ubuntu desktop and text install would hang on the detecting CD-ROM part before the partitioner.  The (ide=nodma) fix worked for me in the live CD and I haven't tried the text based one.  This likely worked because I don't thnk that my old comp supports dma.  My plans are to install Xubuntu in the computer to have it be useful ... maybe.
If the live CD crashes on mounting using an older system this is a likely solution.  Worth a shot anyways. :)

---

### Post by mrobbert on 2006-06-05
I found that (at least in my case) the problem of getting stuck loading the root filesystem is due to a known [bug]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367") that didn't get fixed in dapper. Most people should be able to fix this by changing their drive designations once in menu.lst and /etc/fstab, but since my problem is caused by a docking station (Thinkpad T42 in a Dock II) I'm going to see this every time I pull my laptop out. 
Can anybody offer any suggestions on how I can possibly get dapper to a usable state given my situation? There are no drives in my docking station so I have no problem if the IDE bus gets disabled somehow.

Thanks,
Mike Robbert

---

### Post by Patrick-Ruff on 2006-06-06
if you can get it to boot in recovery mode, then you can edit the required files there, and change them to your hard drive name. and you shouldn't have any issues.

good day.

---

### Post by cam2009 on 2006-06-07
if someone who's gotten this to work could post a step-by-step, that'd be great. trying to follow along, but I'm just starting using linux and know nothing but windows until I finish this switchover that should've been done 2 days ago. i have no clue how or what to edit.

---

### Post by manicka on 2006-06-07
cam2009, I'd suggest downloading the alternate Cd image and using it to do a text-based install. It's a fairly simple process and doesn't create the same problems as the Desktop live cd.

---

### Post by cam2009 on 2006-06-07
[QUOTE=manicka]cam2009, I'd suggest downloading the alternate Cd image and using it to do a text-based install. It's a fairly simple process and doesn't create the same problems as the Desktop live cd.[/QUOTE]
thanks, but that just gives me the error

"Your installation CD-ROM couldn't be mounted. This probably means that the CD-ROM was not in the drive. If so you can insert it and try again."

Probably an unrelated error since no one else has mentioned it here. I've tried 5.10 Alternative, 6.06 Alternative, and 6.06 Desktop

---

### Post by MrShmoe on 2006-06-07
I've managed to install Ubuntu 6.06 on my computer. When I start my computer GRUB starts and gives me the option too boot windows or ubuntu. When I choose to boot Ubuntu it stalls on "Mounting root file system" And after about 2 min I get this message:
```
ALERT! /dev/hda1 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
```
I don't know why it says that it can't find the HDD since it could find it when I partitioned it and installed the OS on it.

My system is configured like this:

120GB S-ATA (Maxtor 6L120M0) - Windows
120GB IDE (Seagate Barracuda "ST3120026A") - Ubuntu

the IDE-drive is partitioned like this
/dev/hda1 - used as /
/dev/hda2 - swap
/dev/hda3 - used as /home

I have no idea what to do since I've never used Linux before, please help!

---

### Post by _jB on 2006-06-07
how come
[quote=menu.lst]title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot[/quote] works fine ?

I meen, they point at tha same root (hd0,1) and the same kernel (with different optons - **ro quiet splash** vs. **ro single**).

I also triede all the tips (nodma, irqpoll a.s.o), nothing worked. But when I boot recovery mode, and press ctrl-d twice, gnome/X works perfectly (without my sata drives though aka my /home :()

*btw; my older kernel loades oki (2.6.12-10-386) but I can't find headers for it (for nvidia.driver) so thats why I'm trying out the newer one)*

---

### Post by ol1v3r on 2006-06-08
This is a bit strange.. But I actually fixed my problem by burning it to DVD instead of CD.. Booted no problems at all ^-^

Give it a go on a DVD+RW? Just a suggestion anyways! :)

---

### Post by jeremytaylor on 2006-06-08
I have a very similar problem to MrShmoe. I'm using an asus w3v which has sata drives. When i boot in recovery mode I get warnings about the sata controller before MrShmoe's message comes up but with sda instead of hda. 

I too have tried all the suggestions on this list to no avail. I installed using the text installer and that didn't help. 

Jeremy

---

### Post by _jB on 2006-06-08
[QUOTE=ol1v3r]This is a bit strange.. But I actually fixed my problem by burning it to DVD instead of CD.. Booted no problems at all ^-^
Give it a go on a DVD+RW? Just a suggestion anyways! :)[/QUOTE]
Well I updated from 5.10 > 6.06 from [within the system](https://wiki.ubuntu.com/DapperUpgrades), but it's worth a shot for sure :)
The normal cd-version dosen't boot here either :(

---

### Post by janx on 2006-06-08
I experienced some of the problems described in this thread after an upgrade with update-manager. Could not solve even after a reinstall with the alternate CD.

Finally, I have been able to boot with the 2.6.12 kernel instead of the 2.6.15 (I use the 'k7' versions). I still have a few things to fix (no sound...).

---

### Post by HeSh on 2006-06-08
[QUOTE=MrShmoe]I've managed to install Ubuntu 6.06 on my computer. When I start my computer GRUB starts and gives me the option too boot windows or ubuntu. When I choose to boot Ubuntu it stalls on "Mounting root file system" And after about 2 min I get this message:
```
ALERT! /dev/hda1 does not exist. Dropping to a shell!


Busy Box v1.01 (Debian 1:1.01-4ubuntu3) Built-in shell (ash)
Enter 'help' for a list of commands.

/bin/sh: can't access tty; job control turned off
```
I don't know why it says that it can't find the HDD since it could find it when I partitioned it and installed the OS on it.

My system is configured like this:

120GB S-ATA (Maxtor 6L120M0) - Windows
120GB IDE (Seagate Barracuda "ST3120026A") - Ubuntu

the IDE-drive is partitioned like this
/dev/hda1 - used as /
/dev/hda2 - swap
/dev/hda3 - used as /home

I have no idea what to do since I've never used Linux before, please help![/QUOTE]

The same thing happened to me. It looks like dapper after instalation confuses hard disks. My primary hard disc (hda) became hde. I really don't know how it came up with e.

Anyways... you can see to wich letter your drive is assigned by choosing rescue option in GRUB. It will list hard drive mappings. Find there your hard and restart back to GRUB. Edit boot options and change hda2 into hdX2 (where X is your letter).

Boot dapper and change GRUB options from ubuntu and save them.

---

### Post by MrShmoe on 2006-06-08
[QUOTE=HeSh]The same thing happened to me. It looks like dapper after instalation confuses hard disks. My primary hard disc (hda) became hde. I really don't know how it came up with e.

Anyways... you can see to wich letter your drive is assigned by choosing rescue option in GRUB. It will list hard drive mappings. Find there your hard and restart back to GRUB. Edit boot options and change hda2 into hdX2 (where X is your letter).

Boot dapper and change GRUB options from ubuntu and save them.[/QUOTE]

yeah I thought something like that had happend, but when I checked out my harddrive using the live CD a second time it was still called hda.

btw, do you mean that I should start Ubuntu in rescue mode? I tried that but I don't know how I can see what my drives are called? And also when i do that having any USB-device plugged in, it stalls.

I also noticed another strange thing. if I start the text installer it can't find my harddrive when I come to the partitioning options.

---

### Post by HeSh on 2006-06-08
Here's the thing. With recovery (recovery option from GRUB) mode, you'll have output of all drivers that are beeing loaded. including list of drives. You can scroll up when it is done and check under what letter is your drive listed. And then go back to boot menu and replace that hda2.
Here is what mine wrote:
...
[some numbers here] hde: ST360015A, ATA DISK drive
...

Here is the strange stuff: during the boot my boot drive is recognized as hde2, but after Dapper boots and i log in, this is what mount returns as output:
/dev/**hda2** on / type ext3
WTF ???? so. i can't boot from hda2 'cause my root filesystem is hde2, but when boot is done hda2 is back and mounted as root / .


edit:
now i found out nothing is mounted as it shoud be.
My swap is originaly on hda3, and as such is written in fstab, but it isn't mounted. I changed it to hde3 and now it's mounted as hda3 to swap. It's also with other harddisks (i have 3 more partitions on 2 HDDs) and cdroms. Everything is messed up.

---

### Post by KenF on 2006-06-09
I had a similar problem. 
My problem:
  1.  After upgrading (from 5.10) the reboot stalls when trying to mount the filesystem.
  2.  It only happens when I have my USB drive plugged in.  Basically it seems reverse the order of the drives.  When I unplug the USB drive there are no problems.

I've tried adding "ide-reverse" (and "ide=reverse") to the boot prompt.  [At first I thought it had worked, but it turns out that the USB drive simply hadn't spun up.]. 

Ken

---

### Post by HeSh on 2006-06-09
Well, my problem is that i have 2 controllers. 1 main on the motherboard and second in PCI. Breezy had assinged a,b,c,d letters to motherboard controller (wich is logical), but Dapper assigns e,f,g,h to motherboard controller and a,b,c,d to the other one (e and a being primary master and h and d sec. slave, so that order is fine).

Anyway, i rewrote fstab and boot/grub/menu.lst and now everything works fine.

---

### Post by sumerags on 2006-06-09
Its a CD eror, I change CD ROM and have no prob with install

---

### Post by Pako on 2006-06-09
Similar issue using the "Live CD" 6.06 version for 64-bit.

Just noticed today, before it gets to the unbutu splash screen where it hangs it reads: **Timer not connected to IO-APIC**.

It just sits at "mounting root file system...".  I let it sit there as long as 2 hours while I watch a movie just to make sure I wasn't being too impatient.  I've tried a couple different burns with this last attempt burned at 2x speed.  

I also tried to boot with the various boot options fix with no luck as well.  

Hardware Spec:
[indent]
Motherboard: Asus A8R32-MVP Deluxe dual Channel Crossfire 3200 (Chipset RD580)
CPU: AMD 4800+ X2 (Dual Core)
Memory: TWINX2048-3500LLPRO, XMS3500, 2048MB, 2-3-2-6, 2x184 DIMM, Black XMS ProSeries
Hard Drive Array: WD Raptor 10,000 RPM 74gx2 Raid0
Hard Drive Storage: WD 400gb 16m (will be getting a second one for redundant data storage)
Optical Drive: Liteon SOWH1693s 16x DVD-RW
Graphics Card Master: ATI X1900XT 512MB Crossfire Edition
Graphics Card Slave: ATI X1900XTX 512MB
Monitor: Viewsonic VP2030b, 20.1 TFT LCD, 8ms response time, 1000:1 contrast, 1600x1200@60hz
Power Supply: Antec NEO 550w
Sound Card: SB Audigy 4
Speakers: Klisch Ultra Pro Media 5.1
[/indent]

For the test I was just running one X1900XTX card.  The Crossfire master card was pulled out of the system.

I also tried the x86 version with no luck as well.  Same exact issue.  The x86 version did work, however, on my 3.2 Ghz Intel machine.  No problem.

Any help would be appreciated.  Might have to just wait until 6.10?

[color=red]**Update June 10, 2006:**[/color]  I turned on APIC 2.0 support in my bios and I no longer get the "Timer Not connected to IO-APIC" any longer so it appears that I just needed to enable the APIC 2.0 support.  Now I get a new error after it can't mount "Buffer I/O error on device hda, logical block 357836".  My suspicions are my SATA Raid 0 so now I search for a new solution.  If I should post my experiences in a different thread please let me know...but my problems started with not connecting to IO-APIC and having it hang on "Mounting Root File System".

---

### Post by MrShmoe on 2006-06-09
[QUOTE=HeSh]Here's the thing. With recovery (recovery option from GRUB) mode, you'll have output of all drivers that are beeing loaded. including list of drives. You can scroll up when it is done and check under what letter is your drive listed. And then go back to boot menu and replace that hda2.
Here is what mine wrote:
...
[some numbers here] hde: ST360015A, ATA DISK drive
...[/QUOTE]

How do I scroll up after it stalls? I tried all keys on my keyboard but none of them made it scroll up, please help.

---

### Post by HeSh on 2006-06-09
Hold SHIFT and press Page-Up, and Page-Down to scroll

---

### Post by MrShmoe on 2006-06-09
It's seem like I have a little problem. When I read all the text in recovery mode it didn't a single time say anything about my harddrive nor was there any text like hd*1 in there. I don't get why it can't find my harddrive.

---

### Post by jeremytaylor on 2006-06-09
How about sda(b)(c)(etc) ?

Hmm. mine really is confusing me. I don't get any of these signs either and I'm a little concerned that my partition table might be broken.... but I can read it with parted, and the contents with a knoppix cd. blah. no idea.
jeremy

---

### Post by vgeneral on 2006-06-10
[QUOTE=bobt12]I have been having the same problem as most of you have freezing at mounting root file system. I tried several of the boot options with no luck. I finally decided to try what I used on a few other Linux system installations that would hang like Mandrake and Mepis. I typed (ide=nodma) at the boot prompt. It has started installing. I cannot attest to how well it works out yet. I will post back at let everyone know how I make out.[/QUOTE]


Bobt12's suggestion helped my installation move past the dreaded "... mounting root file system... " message.  I recommend giving it a try if your experiencing the same.:)

---

### Post by _jB on 2006-06-10
After trying all kinds *fixes* I finally got the install booting using **ide=nodma ide=reverse** and that worked out fine. Desktop up and running, install oki, reboot oki (after I added above to menu.lst)..

[COLOR="Red"]**But**[/COLOR]
[LIST]
[*]I have no **audio**
[*]I have no **internet**
[*]No **sata **drives (hda/hdb oki though)
[*]all worked fine with @ 5.x..
[/LIST]
The list above should work *out-of-the-box*, especially for us *[COLOR="Indigo"]not-to-1337-at-linux[/COLOR]* (how else can I tell my mom to download and use it ?? :P) :)

Think I'm falling back to 5.x for now, 6.06 looks sweet but I can't/won't recommend it to any of my friends yet.

Mayby I'm givin up on 6.06 to quick, but at the moment I don't have the time to mess around with system setup, I just want/need a working system..

---

### Post by siimo on 2006-06-10
I have this same problem and still haven't fixed it please enlighten me! the cds work on my other PC but on this system they won't:

athlon-xp 1700+
512MB DDR
80GB WD IDE p-ata
Samsung DVD-+RW writemaster
ATI Radeon 9250 128MB

---

### Post by skelooth on 2006-06-10
[QUOTE=siimo]I have this same problem and still haven't fixed it please enlighten me! the cds work on my other PC but on this system they won't:

athlon-xp 1700+
512MB DDR
80GB WD IDE p-ata
Samsung DVD-+RW writemaster
ATI Radeon 9250 128MB[/QUOTE]
I have a feeling it's your samsung drive siimo... i've installed on 2 other computers, but I'm trying to get it installed on a third and it absolutely refuses to play well with the samsung cd drive, the kernel complains that the driver is not valid, and the kernel will <0>panic

---

### Post by siimo on 2006-06-10
i gave up!

had a old hoary cd lying around, so instaled that then dist-upgraded to breezy then went to dapper from breezy and then apt-getted xubuntu-desktop.

](*,)

---

### Post by grandpa-geek on 2006-06-13
I posted this yesterday as a new thread, but I saw a note asking people to post in this thread on issues related to this one.

My problem doesn't relate to the install, but to booting after the install, and I encounter the same message.  I'm trying to boot Ubuntu from the boot partition set up by my primary Fedora Core 5 installation, where Ubuntu is installed (via the alternate install iso) on an LVM partition.

I had tried multiple things to get Ubuntu to boot on my system and finally arrived at copying the Ubuntu kernel and initrd to the same /boot set up by FC5. Ubuntu is installed on VolGroup00/LogVol03. My grub kernel root statement is root=/dev/mapper/VolGroup00-LogVol03/. The boot kept hanging at "Waiting for root file system". I followed the advice of the other threads and waited. I then got a message that /dev/mapper/VolGroup00-LogVol03/ does not exist, and the initrd brought up a shell with BusyBox.

I had seen a mesage that four partitions were now active in VolGroup00, so I figured something was working up to a point.

I looked at the /dev of the initrd, and there were /dev/mapper/VolGroup00-LogVol03 and /dev/VolGroup00/LogVol03. So the root filesystem is really there! I then created a mount point /mnt/ubuntu and tried to mount the filesystem. It kept telling me the filesystem didn't exist until I tried "mount -t ext3 /dev/mapper/VolGroup00-LogVol03 /mnt/ubuntu" and it mounted. So it isn't detecting the filesystem type, needs to be told what it is, and is giving a misleading message that the root filesystem simply doesn't exist.

Now the issue is how to tell the kernel that the filesystem is ext3, just like I did with the mount from the initrd.  I have tried to add rootfstype=ext3 to the kernel statement in grub, without success.  I tried it in various places on the line (e.g., before and after the root= statement) with no success.  I tried a statement rootflags="-t ext3" but that didn't work either.

The VolGroup00 was created by the LVM under FC5, and while the initrd was operating, I thought I saw a message fly by about SELinux.  I don't know if Ubuntu has any SELinux provisions in it.  I mounted the Ubuntu partition from FC5, picked a file, did an "ls -Z" on it, and got back an SELinux context, so I wonder if something related to SELinux on FC5 could be messing things up. 

My next step will be to try to see if messages are stored in /var/log on the Ubuntu initrd, so I can see what they were.

Meanwhile, I would appreciate any advice anyone has on how to tell grub or the Ubuntu kernel that the root filesystem is ext3.

---

### Post by Patrick-Ruff on 2006-06-15
this is beginning to be an irritating issue, I reinstalled Ubuntu, and this issue remains, but for some reason my menu.1st file is empty...not a good sign.... at all.

---

### Post by manicka on 2006-06-15
[QUOTE=Patrick-Ruff]this is beginning to be an irritating issue, I reinstalled Ubuntu, and this issue remains, but for some reason my menu.1st file is empty...not a good sign.... at all.[/QUOTE]

Reinstall using the alternate image and do a text-based install

---

### Post by warpdag on 2006-06-15
[QUOTE=manicka]Reinstall using the alternate image and do a text-based install[/QUOTE]

That won't work (or maybe with other minor issues but not with the one we are talking about here). The text installer will see sda (the one connected to your mobo ide controller) as the main install drive and will install itself on it, which is perfect, but at reboot, sda (or hda) becomes for most of us sde (or hde, might change with your config), i.e. obviously the kernel inits the mobo ide ports at last, i.e. a major flaw that will block most users that have more than one ide controller in their box. 

What amazes me even more is that if you have several ide controllers, the live install sees the install drive (the one connected to your mobo) as sde (for most cases), installs itself on sde, but still configures grub so that grub tries to boot from sda and not sde at reboot (even though to me this drive recognized as sde at boot is actually sda, but whatever...).

I guess the devs didn't really try to install dapper on a multi-disks box, or maybe they did but they may have been lucky (oblivious?) enough to decide that they would install it on a drive that is not connected to the mobo ide controller. I guess for the average joe with only 1 disk in his rig (or maybe more but all on the same ide controller) everything works perfectly, but again, please introduce me to an average joe that uses ubuntu, trust me, i want to meet him...

Going back to breezy, too bad, I really sincerely secretely love ubuntu (!), but this just sucks...

---

### Post by grandpa-geek on 2006-06-15
If you look over in the bug reports, there are bugs marked "critical" and "high" that seem related to this, and some are marked "confirmed".  Apparently there is something wrong with the initrd (a.k.a initramfs) and the boot process that has to be fixed.  My best guess is that it will only be fixed by releasing a new initrd.  

If I knew how to build one myself, I'd get my system fixed, since I was able to mount the root partition manually from the initrd shell that came up after the boot process root fs mounting failed.  (But I didn't know how to continue the boot process once I did that, how to create an initrd that would do what I was able to do manually, or how to pass a parameter to the kernel/initrd that would tell them what to do.)

---

### Post by scottrob12 on 2006-06-16
Hi All

2 weeks ago my Ubuntu cd's arrived. I have just put together a new base unit and made the decision to go over to Ubuntu. I installed the 5.10 CD and it booted fine. I was prompted to update software and did so. I was then prompted to upgrade to Dapper and completed the upgrade. I restarted and the system rebooted ok. The next morning, I switch on and, yes, the boot stops at '' mounting root file system''. I press the reset button and the system boots normally. This is as it has been since the start. I shut down the computer, on start up it stalls at the same place, on reset it boots normally. If I restart the computer, for instance after software install, the system boots normally.

I installed gparted.When I open it, I get the message

''The Kernel is unable to re-read the partition tables on the following devices:
-/dev/mapper/Ubuntu-root

Because of this, you will only have limited access to these devices. Unmount all mounted partitions on a deviceto get full access.''

I open gparted and there are 3 entries

/dev/hda1   ext3  243.14mb  51.70mb used  191.44mb unused   boot

/dev/hda2   extended  152.43gb

/dev/hda5   unknown   152.43gb   lvm

The system is working well, subject to the reboot and I am loath to mess about with these partitions as I am a bit of a novice. The hard drive is a Maxtor Diamond 9, 160gb. I have come to the conclusion that the boot problem is a software problem which will be sorted out by the powers that be via an update. However, I would appreciate any advice on the partition set up as when I installed 5.10, I chose the 2nd option to create lvm. Was I correct?

---

### Post by Brad A. Steffler on 2006-06-16
My boot/install problem:

Loading essential drivers ... ok  (this takes less than a scond to complete)
Mounting root file system ... ok  (this takes over 90 seconds to complete)
Moving mount points ... ok  (takes less than a second to complete)
Adding liveCD user ... ok (takes over 60 seconds to complete)

(now a series of messages follows for about 15 or so messages and then the screen goes black and the machine becomes unresponsive)

the messages are all variations on this theme:
[xxxxxxx.xxxxxx]  Buffer I/O error on device hda, logical block xxxxxx
(where "x" represents a numerical character between 0 and 9)
 

My hardware setup:
Asus A8V Deluxe motherboard with an Athlon FX-55 processor, 2.4 GHz
2 Gb RAM
2 WD 250 Gb Hard drives , one for windows and one intended for Ubuntu
Sony DVD ROM DDU1612, the CD/rw and DVD ROM  boot drive
Sony DVD RD DW-U18A, a DVD r+- RW drive
Floppy A: drive
nVidia 6800 GT video card

Bios is current as of 2 months ago and AMI version 17 for this mobo.

As suggested, I unplugged all USB devices. 
This was no help. 
While I am not a computer  novice, I am new to Ubuntu.
Any advice to help me would be appreciated.

---

### Post by m0bilitee on 2006-06-16
Well, this hit me now. I'm using 6.06 Server and the power went out at the house tonight due to thunderstorms.

If I do an ls on /dev/mapper, I see my second LVM group is showing up with lower dev numbers, and thus root is somehow ending up on my second LVM group instead of the first where /root actually exists.

For me right now, my second LVM volume group is on the second hard drive, so I'm going to pull the hard drive from the system and see if I can get the rest to boot. This bug seems to affect multi-drive systems.

My system:  Abit AN7 with Athlon XP 2500+. Boot drive is a Maxtor (don't remember the model exactly) ATA-133 drive, second drive is a WD ATA-100 drive. These drives worked great together otherwise.  This is not a dual boot system with any other OS.

---

### Post by Brad A. Steffler on 2006-06-17
A followup to my  install of Dapper Drake hanging at install:

I have the book, "Beginning Ubuntu Linux" by Keir Thomas. In the back is a Breezy install CD-ROM. I installed this first and then did an upgrade to Dapper Drake. No problems!

This would suggest that install problems are in the installer software itself.

6.06 is now in operation on my PC.

---

### Post by mpalla on 2006-06-17
I'm experiencing something similar, along with some other problems... all the details in this thread: [http://www.ubuntuforums.org/showthread.php?t=193506](http://www.ubuntuforums.org/showthread.php?t=193506)

---

### Post by scottrob12 on 2006-06-24
[QUOTE=scottrob12]Hi All

2 weeks ago my Ubuntu cd's arrived. I have just put together a new base unit and made the decision to go over to Ubuntu. I installed the 5.10 CD and it booted fine. I was prompted to update software and did so. I was then prompted to upgrade to Dapper and completed the upgrade. I restarted and the system rebooted ok. The next morning, I switch on and, yes, the boot stops at '' mounting root file system''. I press the reset button and the system boots normally. This is as it has been since the start. I shut down the computer, on start up it stalls at the same place, on reset it boots normally. If I restart the computer, for instance after software install, the system boots normally.

I installed gparted.When I open it, I get the message

''The Kernel is unable to re-read the partition tables on the following devices:
-/dev/mapper/Ubuntu-root

Because of this, you will only have limited access to these devices. Unmount all mounted partitions on a deviceto get full access.''

I open gparted and there are 3 entries

/dev/hda1   ext3  243.14mb  51.70mb used  191.44mb unused   boot

/dev/hda2   extended  152.43gb

/dev/hda5   unknown   152.43gb   lvm

The system is working well, subject to the reboot and I am loath to mess about with these partitions as I am a bit of a novice. The hard drive is a Maxtor Diamond 9, 160gb. I have come to the conclusion that the boot problem is a software problem which will be sorted out by the powers that be via an update. However, I would appreciate any advice on the partition set up as when I installed 5.10, I chose the 2nd option to create lvm. Was I correct?[/QUOTE]

Installed Boot up Manager. Still have to use reset to boot correctly but get following message when first boot fails:

/bin/sh : can't access tty; job control turned off

Appreciate it if anyone can shed a light on this.

---

### Post by branche_dude on 2006-06-24
I have been having same problem. All I did was add 'ide=nodma acpi=off' in boot options and it seems to be getting past the "mounting root file system" problem now. The same solution fixed hanging up of system during installion of Fedora Core 5. Now the setup started the GUI to start the installation but it seems to be hanging after displaying the Ubuntu logo. Hope that helps anyone and if anyone has solutions to my problem please let me know.

---

### Post by matt1988 on 2006-06-28
I was having the same problem witht he cd locking up at the splash screen. I was using a DVD-RW drive with a CD-R in the drive. I changed the DVD burner out with a CD drive, and violla it worked. No idea why.

---

### Post by Richard Roy on 2006-06-30
After updating kernel 2.6.15-23 to 2.6.15-25, when the computer boots, the system is stuck for several minuts on "mounting root filesystems". I have a laptop IBM thinkpad x60s. The problem did not exist before the last upgrade.

I posted a bug about that:
[https://launchpad.net/distros/ubuntu...eta/+bug/50313](https://launchpad.net/distros/ubuntu...eta/+bug/50313)

but it is not being taken care of for several weeks.
I heard other people have this bug.
This is a serious bug, and I want the community to help me. If it will not be fixed, I'll have to leave ubuntu on the next upgrade, and it's a pitty, since I really like this distro.
Please tell what should I do to pay the attention of the developers of ubuntu to fix this serious bug.

It seems that nobody really cares !

Many thanks.

---

### Post by wgscott on 2006-06-30
I share your frustration as well as this bug.  I reinstalled the kernel, and that seemed to help somewhat, but now it hangs when it is trying to talk to the video driver.  It is still pretty slow with disk arbitration.  Something is messed up with this kernel.  Everything works fine when I boot off the previous one.

This is really making me appreciate Mac OS X.

---

### Post by Richard Roy on 2006-07-02
someone please?

---

### Post by ubuntu_demon on 2006-07-03
I renamed this thread to : 
booting stalls during "mounting root filesystem"

I've posted about this bug on my blog :
[http://ubuntudemon.wordpress.com](http://ubuntudemon.wordpress.com)

This thread contains links to possible fixes :
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)

Currently it links to these possible fixes :
[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)

Please post your tips and/or fixes here :
[http://www.ubuntuforums.org/showthread.php?t=187659](http://www.ubuntuforums.org/showthread.php?t=187659)

What happened in my case :
For me my /dev/hda became /dev/hde after upgrading. On a fresh install I could produce exactly the same results. To solve it I had to edit my /etc/fstab and /boot/grub/menu.1st accordingly. Each time a new kernel gets installed I have to edit my /boot/grub/menu.1st again and change /dev/hda for /dev/hde.

See for example a part of my /boot/grub/menu.1st :
```

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,5)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hde6 ro vga=0×31a
quiet splash
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

**edit :**

udev enumeration should use /sys/bus not /sys/devices
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367)

**The devs know about this bug and we might see a dapper-update someday.** See this thread :
[http://www.ubuntuforums.org/showthread.php?t=208207](http://www.ubuntuforums.org/showthread.php?t=208207)

---

### Post by Richard Roy on 2006-07-04
All the suggested solutions don't work for me.

my fstab is:
/dev/sda3       /               ext3    defaults,errors=remount-ro 0       1
/dev/sda4       none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

and I dont have /dev/hde.

So what should I do ???

---

### Post by justinflavin on 2006-07-06
i'll just throw my 2 cents in here - i have exactly the same problem, when booting off a Ubuntu 6.06 CD i downloaded a few weeks ago.


However, it boots up ok from a Kubuntu 6.06 CD that I received in the post.

Xubuntu / Edubuntu (downloaded) also have the same problem. Maybe there's some sort of fix in the Kubuntu CD that i received?

---

### Post by tiripon on 2006-07-07
I have this problem also "Hangs at :Mounting Root File System..." after a while it tells: "MP-BIOS Bug: 8254 Timer Not Connected To IO-APIC"

The IRQPOLL in boot options fixed that, but now I am stuck at " * Saving VESA state..."

It wont go pass this step.

> **papernik said:**
> I had same problem, but this solve mine :

put 'irqpoll' in boot options

This was OK for me

try and make me know


bye

paper

---

### Post by tiripon on 2006-07-07
> **tiripon said:**
> I have this problem also "Hangs at :Mounting Root File System..." after a while it tells: "MP-BIOS Bug: 8254 Timer Not Connected To IO-APIC"

The IRQPOLL in boot options fixed that, but now I am stuck at " * Saving VESA state..."

It wont go pass this step.
This is an update of my previus post:

I have this problem with all the I386 Ubuntu 6.06 cds or dvds on my laptop only. It works great on my destop or even with Virtual PC 4. My laptop is a Mobile AMD Athlon XP-M 2400+ (512 MB of RAM). Bios version: A1004SMS V2.20. It is manufatured by Averatec. Disabling the USB in the bios does not fix it.

---

### Post by dtragcoen on 2006-07-10
Not to rehash what Ubuntu_Demon and Adamant have both suggested, but it appears we have a number of seemingly different issues. However, based on the list of results compiled by them and runnyman's post here [http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41) it would appear these are are symptoms of an issue with udev identifying devices in a consistent manner. However, if we can get some sane sense of what hardware is tied with what solutions, it might make things easier on everyone until udev is fixed.

I also have a request to Ubuntu_Demon or another mod at the bottom of this post relating specifically to this thread in order to further reduce the amount of reading new people have to go through. (It's getting long and I read the whole thing.)

In future responses and requests, I would suggest the following:
If you are having trouble installing from cd - First, go read this thorough post by Adament if you've missed anything this far:
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
Otherwise - or if that does not solve your problem then refer to Ubuntu_demons list of Issues and potential fixes here:
[http://www.ubuntuforums.org/showthread.php?t=187656](http://www.ubuntuforums.org/showthread.php?t=187656)
particularly under the section titled 'booting stalls during "mounting root filesystem"?'

If you fix it please go here: [http://www.ubuntuforums.org/showthread.php?t=212839](http://www.ubuntuforums.org/showthread.php?t=212839)
and respond with as much of the information requested there as possible.

Good Luck!

------------------------------------------

Note to Mods. Due to the length of this thread and the prevalence of the issue I am creating a similar post beginning a new thread for solution responses solely to this post. Because all of the solutions to this will be gathered from different sources, it should make updates to Adament's post simpler. However, it would be impractical to try placing this all in multiple posts in the installation solutions thread. It's already becoming disjointed with bits and pieces relating to similar issues. I intend the results of this to be compiled as one post from time to time, rather than thrown together haphazardly.

I also suggest the creation of a thread for questions only linked from this thread and possibly locking this thread with all relevent solutions links in the final post. Of course, by placing the relevent solutions links as the start of the new thread, it should reduce the amount of questions asked and speed the process of isolating new issues similar to this along.

Thanks

---

### Post by ubuntu_demon on 2006-07-14
**Everyone please test this general workaround :**

[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/69)

[quote=Paul Sladen]
For those still wondering; The workaround for this issue involves specifying the partition to boot from by ID, rather than the transient location:

  1. Boot a desktop/LiveCD.
  2. Run sudo /sbin/dumpe2fs /dev/sdX | grep UUID
  3. tell 'grub' or 'lilo' to boot with that ID:

     linux ... root=UUID=d4c51a2a-d93f-4dc1-8717-9c3cdb4d41ce

and also adjust this in:

  /boot/grub/menu.lst
[/quote]

Replace sdX for sda, sdb, sdc, sdd, hda,hdb,hdc,hdd or whatever gparted on the livecd tells you it is.

You can post results either on launchpad here :
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/)
Or in this thread :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)

---

### Post by ronly on 2006-07-16
Unfortunately I have to report that that general workaround doesn't work :( If there is an update to dapper coming, how soon can we expect it? I'm not trying to push the developers since it's a volunteer effort that I appreciate greatly but if I can get any estimate on how long it will take I'll know whether I should spend a lot of time on a temporary solution or if I should just wait.

---

### Post by ronly on 2006-07-16
This is getting very, very strange but now I, finally, have something positive to report and a question to ask. I thought I had already tried everything but in the bug report on launchpad someone with precisely the same motherboard as I have, had gotten it to work by disabling pnp in the bios (which I had too) and booting with "acpi=off irqpoll" (which I had tried previously too but I now have a different cdrom drive). Doing so finally let me boot my system but my usb mouse didn't work and just to test usb devices I tested my bluetooth dongle, but then my ps/2 keyboard stopped working too. My system hadn't, however, crashed completely since I could login from my mobile phone (thank you midpssh developers!) and reboot. Then I disabled legacy usb support and everything seems to work. Since I still have some dependency issues due to all the experimenting I've done and such I think it's best if I install dapper from scratch and then modify grub to always boot with those options but before doing so I'd like to know what those options do? Is it (reasonably) likely that I won't get a hosed harddrive or such? I have done previous installs by moving everything into one directory on the partition I intend to have as root and then just installed the new system without formatting that partition so unless I had this concern about my sata harddrive I would to that now but since I saw a few hundred lines of
[   39.577262] nv_sata: Secondary device added
[   39.577293] nv_sata: Secondary device removed
whilst booting I hesitate to do much before I know more. Have others that have solved it through similar means gotten a working system despite the sata_nv messages?

---

### Post by 0xDEADBEEF on 2006-07-17
Problem with: sh-s162l
solved. Have a look at [http://wiki.network-crawler.de/index.php/Bug_workaround_Samsung_sh-s162l](http://wiki.network-crawler.de/index.php/Bug_workaround_Samsung_sh-s162l)
greez

---

### Post by batista on 2006-07-18
Im too lazy to read everything so i dont know if this has been posted already. I was having the same issue at mounting root... so when it takes you back to the bufer error just leave the pc alone, it will actually boot into the live cd where you can install ubuntu, well thats what worked for me oh and also i disabled the usbs. Hope it helps. BTW it takes about 15-25minutes.
 
Intel P4 1.8Ghz
Asus crappy mobo
512MB PC2100
Samsung dvd toster w/ lightsc.
160GB segate, 80GB WD.

---

### Post by Fubie on 2006-07-18
Just curious,  Did anyone use a download manager to get the iso's?

Then I used leechget on the CD & DVD iso's I had all kinds of issues and this was one of them.

I then took the slow road and let the DVD iso download properly and I no longer get any of these errors.

Just thought I'd post my experience.

---

### Post by Argium on 2006-07-19
I'm having the stalling problems as well, but I haven't previously installed Ubuntu before (because I had the same problem with Ubuntu 5).

How can I fix this without a linux shell?  I dont have lilo/grub installed atm, and I dont have any linux partitions (I'm going to create them during the install).

---

### Post by ubuntu_demon on 2006-07-19
> **ronly said:**
> Unfortunately I have to report that that general workaround doesn't work :( If there is an update to dapper coming, how soon can we expect it? I'm not trying to push the developers since it's a volunteer effort that I appreciate greatly but if I can get any estimate on how long it will take I'll know whether I should spend a lot of time on a temporary solution or if I should just wait.
from [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/57](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/57) :
[quote=Scott James Remnat]
I've also iterated that the fix has been around for some time now, and that it would go into edgy when it opened (it's already partially there, awaiting builds) -- and that if we have no adverse effects in edgy, it could be backported to either dapper-updates or at least dapper-proposed or dapper-backports.
[/quote]

I personally hope it will make the Point Release. See : [https://wiki.ubuntu.com/DapperPointReleaseProcess](https://wiki.ubuntu.com/DapperPointReleaseProcess)

IMHO this is the worst case scenario : "needing to update to Edgy when it releases to solve it"

---

### Post by niboraus on 2006-07-21
well i have read post after post and its a revelation to see so many problems with a OS.

truley the BSOD is now renamed "The Brown Screen Of Death"

I am just trying to move from XP and I took on board the Ubuntu PR of an easy install but this is absurd, the distros should be removed from the net until it is fixed.

The number of "fixes" for this problem are many and appears their is some randomness here as what works for one does not for another.

Does anyone really now how to solve this??

Or is it back to Bill for Me?

---

### Post by Seb71 on 2006-07-23
I have the same problem (booting stalls during "mounting root filesystem") since updating to 2.6.15-26 kernel (with both 386 and k7 kernel versions).

With 2.6.15-25 kernel or with 2.6.15-23 kernel, my Ubuntu PC is booting.

Configuration:

Ubuntu 6.06 LTS - clean install from Ubuntu LiveCD.

Motherboard: MSI KT6 Delta LSR (VIA KT600 Chipset).

CPU: AMD Athlon 2500+ (Barton Core).

hda (Primary IDE Master) - Seagate 120GB IDE HDD with several partitions.
hdb (Primary IDE Slave)- empty.

hdc (Secondary IDE Master)- ASUS DVD +/- R/RW Writer (ASUS DRW 1608P2).
hdd (Secondary IDE Slave)- Sony DVD-ROM (Sony DDU1211).

sda - Seagate 160GB S-ATA HDD (with sda2 -linux swap partition and sda3 - root partition).

sdb - empty.

---

### Post by Greg T. on 2006-07-23
I think we're at a point in this thread where the "me too" messages can stop. I check this thread regularly looking for a fix, and it's always disappointing to see the most recent post is nothing more than another story of someone hitting the wall. Welcome to the club... maybe there will be a fix before Edgy is final. Sigh.

---

### Post by Seb71 on 2006-07-24
If you are referring to my post, let me tell you that I did not post in this thread. My post was moved here from a different thread, a thread initiated by ubuntu_demon with a solution to this problem.

In that thread, the last post before mine post was from someone reporting that his Ubuntu 6.06 was stalling at the point of "Mounting root file system" **only when using certain kernel versions**. There was the first place were I seen such a report.

Previously, the people that reported this problem never indicated that the boot stall happens only with certain kernel versions.

---

### Post by Abel Nightroad on 2006-07-24
Disabling USB 2.0 on the BIOS worked fine for me.

Before that I was able to install Ubuntu, just disconnecting USB devices. But, when connecting them inside Ubuntu, the system hang up.

Now with USB 2.0 disabled, all works fine (I really don't need USB 2.0, since I just use a USB pendrive and a Wacom tablet)

---

### Post by YaleHadderity on 2006-07-26
Just writing in to say that I had this same problem, but removing the USB hard drive fixed it.  The install would hang at "mounting root filesystem".  I tried switching BIOS settings and burning different CD's all to no avail.  It turned out the problem was a USB connected hard drive.  Once I unplugged that, I was able to install without problems.  Note that I was able to leave my USB mouse, keyboard and headphones plugged in during the install without problems. 

Hope that helps.

---

### Post by big_gie on 2006-07-26
Hi all,

I do have the same problem. Maybe not the same cause though.

Pentium 4 64-bit & 160 HD (PATA, what is pata anyway?)

This is a clean install using the ShipIp 64-bits CD. The installation works (I still need to put "noapic nolapic" for the live cd to shutdown correctly). But on reboot, I get the stalls during "mounting root filesystem", and then a shell prompt after the error "ALERT! : /dev/hde3 does not exist".

I tryed many many many different kernel parameters, without success. I always get the same error.

I'm pretty sure it is related to initrd not having the sufficient modules to load the HD drivers.

When the livecd is booted, I have:
/dev/hda (cdrom)
/dev/hde1 (ntfs)
/dev/hde2 (swap)
/dev/hde3 (/)
So grub gets the right combination.

But when in the BusyBox shell, I get :
> ls /dev/h*
/dev/hda
and nothing else. As if somthing was missing for the kernel.

Anyone having a clue? On this thread ([http://forum.framasoft.org/viewtopic.php?t=18850](http://forum.framasoft.org/viewtopic.php?t=18850)) it seems to show a way to reconfigure the linux-image packages that way (Note: has not been adapted to my system):
[quote="http://forum.framasoft.org/viewtopic.php?t=18850&p=152773#bot"]
mount /media/hda5
mount -o bind /dev/ /media/hda5/dev/
mount -t sys none  /media/hda5/sys/
mount -t procfs none  /media/hda5/proc/
chroot /media/hda5 /bin/bash
mount -a
dpkg-reconfigure linux-image-`uname -r`
[/quote]
The part "mount -t sys" and "mount -t procfs" didn't work with error unknown fs sys and procfs.

Saddly it didn't worked.

Anyone?!?!?! :-k :confused:

---

### Post by BorgHunter on 2006-07-30
I'll toss my hat in the ring too. "Me too." Mine is unique in that after a hang, I hit the power switch, kill my machine, and start it up, and it will boot absolutely fine, no problems. But it has to hang once for this to occur. It doesn't do this on my laptop, and it doesn't do this on one kernel only: 2.6.15-23-386, which is what I use now. All newer 386 kernels and, near as I can tell, all 686 kernels (including 2.6.15-23-686) cause the hang. As I can boot without dying, it does not concern me greatly, though one would think that a problem this large would be fixed by now by The Ubuntu Gods.

---

### Post by Brian Kendig on 2006-07-31
"Me too!" I am having similar problems on a Gateway Astro All-In-One PC with both Ubuntu 6.06 and Xubuntu 6.06 CDs.

The computer is a Celeron 400, 66MHz bus, 128MB RAM (upgraded from 64MB). Circa the year 2000. Small and underpowered, but I hoped to get Xubuntu onto it. The *only* ports on it are USB and modem; it comes with a USB keyboard and mouse.

Booting either the Ubuntu 6.06 or Xubuntu 6.06 CD has the same effect:

- the boot menu appears; I select the first (default) option

- it says "Loading essential drivers... ok"
- it says "Mounting root file system..."

- A minute or two later it drops back to a text screen and begins printing an error message every few seconds, each preceded by a timestamp:

Buffer I/O error on device hdb, logical block 14
Buffer I/O error on device hdb, logical block 15
Buffer I/O error on device hdb, logical block 0
Buffer I/O error on device hdb, logical block 1
Buffer I/O error on device hdb, logical block 2
Buffer I/O error on device hdb, logical block 3
Buffer I/O error on device hdb, logical block 4
Buffer I/O error on device hdb, logical block 5
Buffer I/O error on device hdb, logical block 6
Buffer I/O error on device hdb, logical block 7
Buffer I/O error on device hdb, logical block 8
Buffer I/O error on device hdb, logical block 9
Buffer I/O error on device hdb, logical block 10
Buffer I/O error on device hdb, logical block 11
Buffer I/O error on device hdb, logical block 12
Buffer I/O error on device hdb, logical block 13
Buffer I/O error on device hdb, logical block 14
Buffer I/O error on device hdb, logical block 15
Buffer I/O error on device hdb, logical block 0
Buffer I/O error on device hdb, logical block 1

etc. This has continued for an hour until I turned off the PC.

I've tried leaving the keyboard and mouse unplugged (so that the only thing connected to the computer is the power cord). Same result.

The only two devices in this system are the hard drive and the CD-ROM, so I assume hdb is the CD drive.

The computer will boot from a Windows CD without problems.


EDIT: Solved the problem! I pulled the Samsung SC-140 CD-ROM drive from the computer and used another brand of drive. Now the installation is proceeding without any problems at all. So it appears that the Ubuntu and Xubuntu 6.06 Live CDs don't like Samsung CD drives?

---

### Post by _jB on 2006-07-31
I gave up on 6.06 a while ago, I've tried it on my 3 setups and all had the same problem.
Yesterday I downloaded [Ubuntu 6.10 Knot-1]("http://cdimage.ubuntu.com/releases/edgy/knot-1/") and it seem to work oki. I have only installed it on 1 machine sofare (htpc) but there's no problem with it yet. I'll try my laptop (just to test) later on, and if that works, then my workstation is up next :)

[SIZE="1"][FONT="verdana"][I]**workstation**
[LIST]
[*]AMD 3400+
[*]ASUS K8N4-Deluxe
[*]1.5GB pc3200
[*]ide/sata/dvdwriter
[*]Nvidia 7900 GT
[/LIST]
**htpc**
[LIST]
[*]Amd- Mobile 2400+
[*]512 ddr pc2100
[*]Dvd
[*]Nvidia Geforce 5900xt
[/LIST]
**laptop**
[LIST]
[*]600 Mhz
[*]6 Gb hdd
[*]64mb ram
[/LIST][/i][/FONT][/SIZE]

---

### Post by filterpunk on 2006-07-31
I recently had this issue but was able to find a solution.  In my setup, I have a drive set for Windows and a drive set for Ubuntu.  Ordinarily, Ubuntu is attached as the first drive to boot, both physically and in BIOS.  Windows had recently taken a crap due to problems with a USB dongle, so I went about reinstalling everything.  Afterwards, when I tried to head into Ubuntu, the system got hung up during "mounting root filesystem."

Either I had physically changed a cable around, changed the boot order of the two drives in BIOS, or Windows install had swapped the two somehow, but the reversal of Ubuntu to second place and Windows in first turned out to be the issue.  In other words, all the fstab and grub info says it's drive one, but it's now drive two, where Windows used to be, so it borks and Windows takes the top spot.

---

### Post by mod187 on 2006-07-31
I HAD this problem. This is my story:
[http://www.ubuntuforums.org/showthread.php?t=212907](http://www.ubuntuforums.org/showthread.php?t=212907)

Maybe it will help someone.

---

### Post by lnostdal on 2006-07-31
Adding irqpoll and acpi=off to the kernel boot-options worked here (sorry if this has been mentioned/tried before; this thread is way big).

---

### Post by Brian Kendig on 2006-08-01
> **lnostdal said:**
> Adding irqpoll and acpi=off to the kernel boot-options worked here (sorry if this has been mentioned/tried before; this thread is way big).

That got me a little bit further - now the boot process passes "Mounting root file system" and gets two lines further to "Adding live CD user", at which point it stops; a few minutes later it goes to the text screen which says only "Uncompressing Linux... Ok, booting the kernel.", and then there's no further activity.

---

### Post by possumjc on 2006-08-01
I had the same problem only after installing the 686 kernel for dual core support. I have a Pentium D machine with an Intel board (it has an ATI chipset though..). The default install from the live-cd worked great except for not supporting SMP. I installed the SMP kernel and that kernel exhibited the same problem that many of the posters in this thread have had. I was able to solve it by adding irqpoll to my menu.lst file. I hope that this might help.

Regards,
Joel

---

### Post by firenewt on 2006-08-01
I lugged through this huge thread of me-toos, picked out the offered solutions. Followed them carefully. None of them changed a thing. Oh well, time to play frisbee with a cd.

---

### Post by deleta on 2006-08-03
> **mrobbert said:**
> I experienced this problem on an IBM Thinkpad T42 after an upgrade from 5.10. I was able to get booted up by choosing the kernel from 5.10 (2.6.12something). That kernel works fine no matter what. I tried the 6.06 kernel with the irqpoll option and that did not help me at all. I then pulled my laptop out of the docking station that it was in the whole time and the problem is gone. Somebody had suggested problems with USB and my docking station has a number of USB devices plugged in so that may be it. I'll try adding some USB devices out of the docking station and try the docking station with no extra devices to see if I can find a problem device or combination, but this definitely looks like a kernel problem.

Thanks,
Mike Robbert

[HTML]
I have the exact same problem with my T42 and docking station.  Everything works just fine out of the docking station, but the computer freezes when I try booting when the laptop is in its docking station.  I tried removing all the USB devices and even the floppy on the docking station to no avail.  Have you had any luck?
Thanks,
Diego Eleta[/HTML]

---

### Post by DaCheetah on 2006-08-03
> **BorgHunter said:**
> I'll toss my hat in the ring too. "Me too." Mine is unique in that after a hang, I hit the power switch, kill my machine, and start it up, and it will boot absolutely fine, no problems. But it has to hang once for this to occur. It doesn't do this on my laptop, and it doesn't do this on one kernel only: 2.6.15-23-386, which is what I use now. All newer 386 kernels and, near as I can tell, all 686 kernels (including 2.6.15-23-686) cause the hang. As I can boot without dying, it does not concern me greatly, though one would think that a problem this large would be fixed by now by The Ubuntu Gods.

My problem is almost identical.
I had no problems at all with the LiveCD booting, at least on the computer in question, there were some minor issues on my laptop, probably something to do with the widescreen LCD, but that's another story. The installation went fine and booted ok, and all was well, but EVERY time I boot cold (the computer has been off for a while) it will stop on "Mounting Root File System..." and sit there, I think for about 10 minutes before booting, but I'm impatient, and hit reset (or Ctrl-Alt-Del) and when the computer reboots, it works fine, completing that step almost instantly.

Incase it helps:
Ubunutu 6.06 (Dapper Drake) Desktop i386 Live CD
AMD Athlon 2700+
1GB of DDRAM IIRC
All drives are IDE:
- 60GB Maxor HDD (Primary Master/hda)
- 80GB Seagate HDD (Primary Slave/hdb (NTFS))
- 20GB um, another Seagate I think. (Secondary Slave, hdd, also NTFS)
- Pioneer DVR107D DVD+/-RW as Seondary Master (hdc)
PS/2 Keyboard, USB mouse
USB Canon MPC270 (With a CF reader, which is mounted as an external USB drive)

---

### Post by nodma on 2006-08-03
This helped me boot up Dapper:

**_ide=nodma_**


I acquired an old IBM NetVista A40 (6840-K7G), which includes:
- i815 motherboard, 
- a 20GB IBM hard-disk (?),
- Matrox G450 video card,
- LiteOn LTN486s CD drive,
- the newest official BIOS, with pretty much default settings (yeah, I know...)

I also tried:
- AOpen CD-924E/AKO instead of LiteOn cd drive

I always got the huh? messages before using ide=nodma boot parameter. Managed even to destroy one of the shippit CDs trying to boot :-k Anyhoo, hope this helps :p

---

### Post by molex on 2006-08-03
I found typing ACPI=OFF in the boot options helps

---

### Post by jojacob on 2006-08-04
today i started having the Buffer I/O error on device hda, logical block xxxxxx error trying to boot the live cd. funny thing is, it worked two days ago just fine. all i've really done between now and then is defrag my harddrive. what's going on here?

---

### Post by sronan on 2006-08-16
Had the same problem (stall at mounting root filesystem) while trying to install 6.06 Dapper on a Gateway Pentium II with Mitsumi CD. Had worked fine with 5.10.

Solution for us: Install test version of 6.10 Edgy Eft Knot 1. 
[http://www.ubuntu.com/testing?highlight=%28edgy%29](http://www.ubuntu.com/testing?highlight=%28edgy%29)

Seems to be working fine.

  - Stephen

---

### Post by snyper82 on 2006-08-16
I have the same problem with Xubuntu, Kubuntu, and Ubuntu on a AMD K& 233Mhz system with 256MB ram and Fujtizu HD (10.2GB).

---

### Post by snyper82 on 2006-08-16
> **papernik said:**
> I had same problem, but this solve mine :

put 'irqpoll' in boot options

This was OK for me

try and make me know


bye

paper

That seemed to work for me!

---

### Post by Marvil on 2006-08-16
This is a very annoying problem we have(had) in common.  
I don't know exactly what it is doing when it is mounting the root , but here is my solution to the problem. 

I didn't change anything in the software.  I had another aproach 
Changed setting in the BIOS , changed the harddisk to be the first bootdevice 
and everything worked fine. I had this problem in Windows couple years ago.

Have been testing the last week and no hangs.

---

### Post by Eykonic on 2006-08-16
I have the same installation problem with 6.06 on an older machine. No solutions are appearing on this forum!

---

### Post by Lord Erik on 2006-08-17
I've read though all these posts and tried a few of the suggestions.  Interestingly knoppix gives similar errors.

My hardware

pentium core2duo 2.13GB process
MSI 975X Platinum mainboard
2x512mb ram
Inno3D 7900GT graphics card
250gb seagate SATA2 hdd
pioneer ide dvd burner

trying to install using the dapper desktop cd I get to mounting root file system and it hangs, I dont get any error messages.

I have also tried Knoppix 3.9 and 5.1 they both start up and then stop at "cant find Knoppix filesystem".  Similar to the ubuntu halting at mounting root filesystem maybe?

I've also tried using a different CD drive and get the same results.

I have tried using ubuntu 5.04 and 5.10 but both of those say they cant find a cd drive module so I cant continue the installation.  

I'm downloading the alternate cd now and will try that.  I'm running out of ideas though.

It's a brand new machine that I put together last night I can't get an OS installed.

---

### Post by Senshi on 2006-08-17
I was also having problems installing Ubuntu from the cd.  It would stop at "Mounting Root firesystem".  At first I though it was the cds.  Several cds later and I still had the same problem.  I eventually installed Ubuntu with the DVD.  Had no problems there.

---

### Post by Lord Erik on 2006-08-17
Using the alternate CD with a text menu installation has got me past the "mounting root filesystem" then hanging error.

Using the alternate cd
I select a language (English) and a location (Australia), select keyboard (only gives me one option), then it detects hardware.

at this point "Detect and mount CD ROM", it says that "No common CD-ROM drive was detected" and ask me to either use a floppy with drivers or select a driver and device location.

I've never seen this before and not sure what to do.  I'm currently using a pioneer DVD burner so I put in an old 32x cd reader thinking that might work but I got the same errors.

any ideas?

---

### Post by Fr@nKy on 2006-08-17
I still have this problem! Pressin Alt+F1 during the Ubuntu LiveCD boot tells me that there's an I/O error on hdc. How do I change the hdc to something else because i believe that Ubuntu is chosing he wrong disk. And also, how do I discover the right disk?

---

### Post by ubuntu_demon on 2006-08-17
From [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/) :

[quote=Scott James Remnant]
Officially marking as Rejected for dapper.

Here is the reasoning:

- We applied the &#8220;fix&#8221;, as planned, to the udev in Edgy Eft.

- While the fix corrected the problem described here, it caused new problems. Because it was a fundamental change to device ordering, it changed the order of other devices where more than one existed in the system &#8212; including other disks

- For Edgy this was not a problem, as the upgrade makes other changes that make device order non-important anyway

- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it

- That workaround is preferable to causing far more working systems to cease functioning.
[/quote]

---

### Post by Eykonic on 2006-08-18
I am in the same boat. Try installing over the net from:
[https://help.ubuntu.com/community/DapperUpgrades#head-792e320b3976df97f0d8b47047e1bcc955fd2569](https://help.ubuntu.com/community/DapperUpgrades#head-792e320b3976df97f0d8b47047e1bcc955fd2569)

---

### Post by kicktheken on 2006-08-18
> **bobt12 said:**
> I have been having the same problem as most of you have freezing at mounting root file system. I tried several of the boot options with no luck. I finally decided to try what I used on a few other Linux system installations that would hang like Mandrake and Mepis. I typed (ide=nodma) at the boot prompt. It has started installing. I cannot attest to how well it works out yet. I will post back at let everyone know how I make out.

This fixed my problem when my ubuntu installation hung at "mounting root file system". I'm using an Acer Ferrari 4005WLMi laptop trying out the latest (6.06.1 LTS Destop amd64) distro.

---

### Post by sdebo on 2006-08-19
Reading the thread I know that I must get the UUID and update fstab and menu.lst.

I got the UUID alright.  However I do not know what commands to place in which files and in what format.

Placing what was suggested here in menu.lst resulted in incorrect parsing of the file.

Can anyone spell out how to carry out the fix please?

EDIT -->

Ok I reread some other threads from KenF and sorted out fstab(partially) and menu.lst.  


I do not know how to get the UUID of SWAP partition.  Tyring to get the UUID mentions some 'magic number'.  Who wrote GREP knows how to tease.  
How do I get this magic number. Magic word...please.

As it is, Ubuntu Dapper still will not boot but freeze when mounting root file system.

EDIT -->

I reformatted the drive and reinstalled using the graphical installer.  It booted correctly.  I attribute the issue to the GUI installer not mounting the drive where my Win98 installation was.  The text installer would recognise it and set up GRUB to offer it as a boot option.  

Now I have Dapper running but will have to modify menu.lst manually to boot in Win98.

Hope this info is of help to others stuck with a faulty Dapper boot sequence.

---

### Post by WiseSalesman on 2006-08-19
I have this issue with my setup, and I am an absolute Linux newbie. 

System is:
P4 1.7ghz
384 MB ram

On system board:
120GB hdd - Linux Install - primary master
60GB hdd - WinXP Install - primary slave
DVD-RW - Secondary Master
DVD-ROM - Secondary Slave

On a PCI IDE card:
250GB hdd - Data

Ubuntu Dapper boots fine (like now) as long as the IDE adapter (and, consequently, the 250GB hdd) are removed. If they are plugged in and enabled, Ubuntu reads the PCI controller as /hda/, and what should be read as /hda/ (the 120GB hdd) as /hde/. So the dillema is that I can only make the OS work if I slightly cripple my system.

Messing around with the coding and UUIDs seems to be a little beyond me (although i'm willing to give it a shot, eventually), so I was heartened to see that the following was posted in the initial [bug report]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index"):

> 

Another obvious workaround, for anyone affected ... install the following packages:

[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/libvolumeid0_093-0ubuntu3_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/volumeid_093-0ubuntu9_i386.deb)
[http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/u/udev/udev_093-0ubuntu9_i386.deb)

(replace i386 with your architecture if different)


I decided to try this workaround, as it seemed more straight-forward and easy to understand (install a couple packages and you're done?). My problem is that when I download and attempt to install these, the package installer gives me "Error: Dependency not satisfiable: libc6". 

Attempting to install the package manually returns:
> dpkg: dependency problems prevent configuration of libvolumeid0:
 libvolumeid0 depends on libc6 (>= 2.4-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.
dpkg: error processing libvolumeid0 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 libvolumeid0


So I downloaded libc6_2.4-1ubuntu9_i386.deb from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.4-1ubuntu9_i386.deb&md5sum=a2d6aa17d6307d0af295a504edff06a2&arch=i386&type=main") and installed it manually, but that just caused Synaptic to tell me my packages were broken, and didn't REALLY fix anything.

Even though Synaptic says my system is completely up-to-date, I've tried reinstalling libc6 and anything with a name similar to libc6. If I can't get support for my PCI card working, I can't use Ubuntu, and am stuck with WinXP.

Uh.... help, please? 

Also - is this the right place for this question? Should I have just created a new thread?

---

### Post by mpgarate on 2006-08-20
Ive gotten this error:
Buffer I/O error on device hds, logical block 312045

I think this is what youre talking about? Several other i/o errors appeared before it, and then it stopped. I will try letting it go for awhile longer and edit the post with results. Is that the fix?

---

### Post by Omnisuite on 2006-08-20
I think I have a related problem but with different error messages. I'm trying to get *buntu on an old comp (400 mHz and win98). I've tried ubuntu and edubuntu, but they seem to behave similarrly. I've gotten the I/O buffer error messages before and I've tried doing stuff like adding 'root=' or getting rid of usb stuff. Now I get messages like
'SQUASHFS error: unable to read fragment cache block'
'crc error' 
'-- system halted'
'invalid compressed format (err=1)'
'Kernal Panic - not syncing: VFS: unable to mount root fs on unknown-block(1,0)'
Often I'll get combos of these message. They usually occur after it says uncompressing linux or the kernal. Occasionally I get a checksum error before the menu even loads. These seem related to what other people have had because I've also had the I/O buffer errors and some of the errors have to do with mounting root fs. Has anyone had some of the errors I've described or am I in my own boat with this?

---

### Post by ubuntu_demon on 2006-08-22
Here are workarounds (which need testing) :
[http://ubuntuforums.org/showthread.php?p=1257154](http://ubuntuforums.org/showthread.php?p=1257154)
[https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/comments/83)

---

### Post by ubuntu_demon on 2006-08-22
> **WiseSalesman said:**
> I have this issue with my setup, and I am an absolute Linux newbie. 

System is:
P4 1.7ghz
384 MB ram

On system board:
120GB hdd - Linux Install - primary master
60GB hdd - WinXP Install - primary slave
DVD-RW - Secondary Master
DVD-ROM - Secondary Slave

On a PCI IDE card:
250GB hdd - Data

Ubuntu Dapper boots fine (like now) as long as the IDE adapter (and, consequently, the 250GB hdd) are removed. If they are plugged in and enabled, Ubuntu reads the PCI controller as /hda/, and what should be read as /hda/ (the 120GB hdd) as /hde/. So the dillema is that I can only make the OS work if I slightly cripple my system.

Messing around with the coding and UUIDs seems to be a little beyond me (although i'm willing to give it a shot, eventually), so I was heartened to see that the following was posted in the initial [bug report]("https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/+index"):



I decided to try this workaround, as it seemed more straight-forward and easy to understand (install a couple packages and you're done?). My problem is that when I download and attempt to install these, the package installer gives me "Error: Dependency not satisfiable: libc6". 

Attempting to install the package manually returns:


So I downloaded libc6_2.4-1ubuntu9_i386.deb from [here]("http://packages.ubuntu.com/cgi-bin/download.pl?arch=i386&file=pool%2Fmain%2Fg%2Fglibc%2Flibc6_2.4-1ubuntu9_i386.deb&md5sum=a2d6aa17d6307d0af295a504edff06a2&arch=i386&type=main") and installed it manually, but that just caused Synaptic to tell me my packages were broken, and didn't REALLY fix anything.

Even though Synaptic says my system is completely up-to-date, I've tried reinstalling libc6 and anything with a name similar to libc6. If I can't get support for my PCI card working, I can't use Ubuntu, and am stuck with WinXP.

Uh.... help, please? 

Also - is this the right place for this question? Should I have just created a new thread?
I copied your post to this existing "mounting root filesystem" thread.

Try this :

[http://www.ubuntuforums.org/showthread.php?t=197956](http://www.ubuntuforums.org/showthread.php?t=197956)
[http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11](http://www.ubuntuforums.org/showpost.php?p=1088366&postcount=11)
[http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41](http://www.ubuntuforums.org/showpost.php?p=1098541&postcount=41)
[http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62](http://www.ubuntuforums.org/showpost.php?p=1231460&postcount=62)
[http://ubuntuforums.org/showthread.php?t=212839](http://ubuntuforums.org/showthread.php?t=212839)
[http://www.ubuntuforums.org/showthread.php?t=186115](http://www.ubuntuforums.org/showthread.php?t=186115)

I don't have time to test the newest UDEV workaround myself because I don't have acces to my machine (I'm staying at my girlfriends place for a while).

good luck!

---

### Post by KarlOng on 2006-08-22
I had the same problem during install.  The system would either hang at "loading kernel" or "mounting root file system"

It was really annoying and I couldn't find the source of the problem.  I found that if I just kept pressing the reset button, eventually it would kick in and load properly.

Drove me crazy.  5.10, 6.06, 32 and 64 bit editions all had the same problem for me, but they would all load eventually after I reboot a zillion times.

I was finally able to install my system, but I could't boot because the installer didn't install Grub!  I followed instructions elsewhere on how to install Grub manually.

[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

After doing that, it would boot off my HDD, but stall at "mounting file system" again.  This is off my HD, not the Live CD.

I unplugged my usb mouse and used a PS/2 adapter for the keyboard.  I replugged in the mouse after Ubuntu loaded up.  Finally up and running.  Just need to solve the USB problem permanently.

---

### Post by Argium on 2006-08-23
Hi,

I'm still having this problem with the 6.06.1 release.  

My install hangs at "mounting root filesystem".

I've tried a few of the options (such as noacpi) and eventually got to the desktop, but the installation corrupted my windows partition so I had to reinstall everything.  The format of the HD hasn't inadvertedly solved the problem either.

I'm running 2 120GB HDs in SATA (no raid).

Any advice would be grand.

Thanks.

---

### Post by chakra_dude on 2006-08-23
@KarLong: what reset button are you talking about? you mean the hard restart button on the PC? thanks

---

### Post by KarlOng on 2006-08-23
Yes, I was pushing the hard reset button on my case to restart my machine over and over again.  Eventually, for no ryme or reason it would kick in and boot into Live desktop.

Kind of flaky if you ask me...  I thought Windoze was supposed to be the crappy OS to install.

---

### Post by Fr@nKy on 2006-08-24
This issue is driving me crazy! I wanted so badly ubuntu but i can't. Do you want a EVEREST Report of my system detailded?

---

### Post by Fr@nKy on 2006-08-24
Guys I did it! I'm in! I'm writing from ubuntu Live CD. I disabled USB 2.0 and used my DVD-RW instead of my DVD Player and it worked. however I couldn't use 800x600, 1024x768, 1280x1024 Resolutions. I needed to boot into safe graphic mode because if not the system would look all jerky on my LCD, In the same way that a CRT monitor shows up when you put a higher resolution than it supports. Why does this happen?

---

### Post by akurashy on 2006-08-26
So I ran into this phenomenon of an error, I today moved my computer to a new case because the other one was pretty old

Noticing,

IDE Cables, like some of other people mentioned in some other posts, if you were playing with the computer with IDE cable master plug (sometimes blue ) and you moved it to the other ide slot then that going  to screw it up badly and changes the numbering of the HD#

That's just what i noticed, doesn't mean its the solution to the problem. but it did work for me, i just reversed the cables to like they looked in my old case (more like IDE1 slot to HD and ide2 to cdrom etc etc)

hope this helps to some people here D:

---

### Post by mxreader on 2006-09-04
Me too.

Environment: IDE XP, SATA 6.06 LTS, DVDRW

I tried dualboot install using a liveCD, everything installed fine. Dualbooting appear to work fine. Upon complete shutdown and rebooting, Ubuntu tries to load, then did not find the right partition I think because it says:

Mount: Mounting /dev/sda1 on /root failed: Invalid argument
etc...

So far I dont know what to do.  Can anyone shed some light for a newbie?

---

### Post by richo132 on 2006-09-08
I encountered this problem while trying to install Dapper on an IBM Netvista A40.
A number of solutions have been suggested in this post, but have given variable results. I therefore hypothesised that boot stall message was a generic symptom of several possible underlying problems. To test this idea, I loaded a working image of Dapper onto /dev/hda of my Netvista and booted in recovery mode. This gives very detailed diagnostic info to monitor the boot process. I was then able to see that, in my case, the boot process stalled with the message "Checking instruction 'hlt'". Research into this indicates that this is a hardware level test designed to trap some unusual condition(s). However it seems that the test itself can be troublesome. With more research, I discovered that the test can be blocked with the boot option "linux no-hlt". This fixed my problem. 
To try this solution, 
[LIST]
[*]boot from the Dapper live/install CD
[*]select menu option "Start or Install Ubuntu"
[*]press "F6 Other Options"
[*]on "Boot Options" line, 
       delete 2 hyphens at the end of the line
       append "linux no-hlt"
[*]press enter
[/LIST]
Good luck.

---

### Post by city-17 on 2006-09-10
I have the same problem when i start ubuntu with 2 keyboards connected, one is usb and the other is ps2. I know that sounds weird but happens to me. I have to start ubuntu with only one keyobard no matter wich.

---

### Post by obleak on 2006-09-11
I also had this problem.

I 'fixed' it by disconnecting my cd rom... weird as there is nothing wrong with the CD rom... 

I suspect the ide,dma,irq probing

---

### Post by richo132 on 2006-09-11
> **city-17 said:**
> I have the same problem when i start ubuntu with 2 keyboards connected, one is usb and the other is ps2. I know that sounds weird but happens to me. I have to start ubuntu with only one keyobard no matter wich.
I'd be interested to know whether boot works ok for you with 2 keyboards if you use the "linux no-hlt" boot option.

---

### Post by loconet on 2006-09-12
And this my friends is why Linux will never be a realistic alternative OS for the desktop for the majority of users. 

Months later there isn't a single solid solution to this problem? Wow.

---

### Post by scoultas on 2006-09-13
I've been getting this problem since I installed some updates using Update Manager.  I tried changing menu.lst to use UUID, but that didn't work.  I've tried unplugging both my cd-rom and dvd-rom drives, to no affect.  I've unplugged all usb devices in case that was the cause - no improvement.  I also tried adding 'no-hlt' to menu.lst, still nothing.  I can boot up if I wait for 3 to 5 minutes, but half the time it fails and drops to a shell instead.  It does scare me that I've had three occasions now where allowing recommended updates causes problems with the machine which take hours to fix (the other two were kernel panics).  I'll try installing the recommended debian patches next...  Does anyone have any further recommendations?

---

### Post by Marksman Ken on 2006-09-14
I resolved this problem by allowing USB 1.1 only on my motherboard. It seems that USB 2.0 is the problem for me but whats worse is I need it for my wifi to get the internet :(

---

### Post by Dillius on 2006-09-14
I read about 19 pages of this before I realized just how confusing it is to deal with multiple seperate problems in one thread.

Does anyone have a fix who knows FOR SURE that their problem is related to their USB devices aside from disabling USB 2.0 in BIOS? I know that mine is related to that problem because If i unplug every USB device I have aside from my keyboard, it boots fine. It only has a problem when I try to have my external hard drive and my monitor's built in USB hub plugged in.

EDIT: By the way, I have installed successfully, this is occuring on booting.

---

### Post by supafraud on 2006-09-14
i am trying to install ubuntu on a usb hard drive and it hangs for several minutes on waiting for root filesystem, and then i get this:

[IMG]http://img172.imageshack.us/img172/151/untitled1lk7.jpg[/IMG]

---

### Post by dustsmoke on 2006-09-15
> **loconet said:**
> And this my friends is why Linux will never be a realistic alternative OS for the desktop for the majority of users. 

Months later there isn't a single solid solution to this problem? Wow.

No, this is an ubuntu problem that ubuntu maintainers can't seem to fix. In fact, I've yet to see ubunutu actually boot without me messing with it on anything. I've never seen anything like this happen in the past to anything else 'linux'.

I just wanted to chime in with a this problem happens to me to on both x86 and amd64 builds on entirely different systems.

---

### Post by aethernaut on 2006-09-15
I tried the Server Install CD on an old AMD 750mhz I have sitting here collecting dust and had the same problem alot of you are having: the install just stopped after looking for the CD drive.
    
  After that failed I went back to a Kubuntu Live cd that I had just used in another comp (I'd also run a checksum on both after downlaod and a CD check after iso burn); AND I went as far as to DL the Alternate Install iso ...nothing would install and I was getting a tad bit frazzled until I tried this:

> **bobt12 said:**
>  I typed (ide=nodma) at the boot prompt. It has started installing. I cannot attest to how well it works out yet. I will post back at let everyone know how I make out.

  ::w00t!!:: This works for me =D> 

  Thanks to bobt12 for posting =D>

---

### Post by moentkaey on 2006-09-15
I have a dell dimension server and It has a SATA drive and a CD-rom.  Nothin fancy, just a simple set up.  I do not have any USB connections, just a simple computer.  I had it on Ubuntu for a while and one day after a simple reboot, it stalls on Mounting root file system.  It says ok next to it, but doesn't proceed.  I tried relabeling the /boot file from sta1 to ste1, but that just went to shell.  Can you help me on this?

---

### Post by Lord Illidan on 2006-09-15
I too have this problem.

Live CD worked fine, yet it wouldn't boot from grub.

About to try Fedora...hope it works!

---

### Post by Marksman Ken on 2006-09-19
I have managed Ubuntu to work with USB 2.0 enabled, but I had to change the USB setting in my BIOS from High speed (480Mbps) to Full speed (12Mbps)

---

### Post by loconet on 2006-09-19
> **dustsmoke said:**
> No, this is an ubuntu problem that ubuntu maintainers can't seem to fix. In fact, I've yet to see ubunutu actually boot without me messing with it on anything. I've never seen anything like this happen in the past to anything else 'linux'.


I know this is a Ubuntu problems. But it seems like Ubuntu now a days is the flag carrier for desktop Linux. Many people consider it the ideal Linux desktop distribution (I'm one of those people) and it's a bit frustrating that something like this, which is affecting a great number of people, cannot be addressed after several months of being known. :-({|=

---

### Post by petrus4 on 2006-09-19
Hey everyone,

First, a couple of disclaimers...I found this thread from Slashdot, and am admittedly not a regular Ubuntu user, my own distribution of choice (if it can be called that) being Linux From Scratch.

That being said, there is at least one suggestion I wanted to offer. This is a workaround, and is intended for people for whom the setup has completed, but who simply can't boot into their new Ubuntu system after that. For people who can't complete the setup, I can't really suggest anything, since I don't know anything about the internal workings of the setup.

Another thing is that this solution may require an additional person's help for some users. I wouldn't find doing it difficult myself, but I'm aware that some users might.

Anyway, the first thing you'll need is a LiveCD (I'm recommending Knoppix here) which allows access to the console. You'll also need to know which hard drive Ubuntu is on (in terms of /dev/hd<whatever>) but with Knoppix this probably won't be a problem as it tends to set up named hard drive shortcuts on the desktop, so you'll be able to figure it out from one of these.

The file we're interested in on the Ubuntu drive is called /etc/fstab, (which possibly stands for File System TABle) and for those of you who don't know, it's basically a text file which specifies which hard drives and other storage devices get mounted automatically when the system boots. (I will admit that I don't know for sure that this file even exists on Ubuntu, but given that it is standard for every other Linux system I've heard of, I certainly hope it does)

What we want to do is edit this file (the command to do so will most likely be "nano /etc/fstab" - Nano being the name of a console text editor) and disable every other drive from being automatically mounted on startup, other than the root drive, at least for the time being. That way we might possibly be able to mount them manually when we want them without problems, or we can leave them off until we're able to get more help for figuring out what is wrong.

The first line in this file (/etc/fstab) is likely to look like this, and you want to leave this line alone, as it is the one which tells the system to mount the root drive:-

/dev/hda1  /  reiserfs  defaults  1 1

There will also be some lines there possibly talking about things like devpts, sysfs, tmpfs, proc, and swap...you won't want to touch those. However, for lines beginning with /dev/hd, it's safe to disable those, and a very easy and safe way to do so is to simply put a # sign at the beginning of the lines, so they would end up looking like:-

# /dev/hdc  /mnt/cdrom  iso-9660  ro  0 0

If you reboot from Knoppix now and try again to start your Ubuntu system, assuming the problem was being caused by an issue with the hardware detection, it should now be able to start up and go into KDE or whatever. (since I'm assuming that Ubuntu goes into a GUI automatically at startup)

If you want to try and manually mount one of your other drives for copying some files over to Ubuntu later, go into Konsole (for KDE) and you can type something like this to try and get it working:-

mkdir -p /mnt/cdrom; mount -t iso-9660 /dev/hdc /mnt/cdrom.

The first command creates a directory in the Ubuntu file system that you can access the CD-ROM drive from, and the second command will try to mount the CD-ROM drive, assuming it's the third storage device (/dev/hdc) in the system. Those of you who are interested and sufficiently brave (again, I don't find this scary, but apparently some do) can use the command

man mount

to find out more about how to use the "mount" command.

I hope this helps someone. The main reason why I hadn't actually installed Ubuntu yet is because I have a particular piece of hardware (a D-link DSL-200b USB ADSL modem) which I haven't been able to get working in Linux at all yet...but this has renewed my curiousity to try it.

I also strongly recommend that if they are able to, people with USB keyboards try to get a ps2 one if they are able to...I suspect doing so will also eliminate a large number of potential problems.

---

### Post by Elisei on 2006-09-20
Might be too late but just in case : i have acer E500 (ASE500-UP801M);
To bypass the problem had to go to bios and disable all usb;
USB 2.0 support is off by default unless bios is overwritten;

---

### Post by cabe on 2006-09-20
I signed up just to say how appalled I am by this glaring problem.  I have spent the past twelve hours trying to set up ubuntu.  The install runs fine, then apt-get breaks.  I fix apt-get, now my wireless card doesn't work right.  I go back to lsmod on the live CD to find the right module, and then when I try to boot back into the installation I see *this* bullshit.

**1 problem, 23 pages, 227 posts, 14 weeks, ZERO solutions.**

At this point, if there were Windows apps that would do what I want (linux has the software I need) then I would install Win2k3 server in a *f^(&ing heartbeat*.

There's some basic functionality that I'm looking for -- I'd like ubuntu to *turn on*.

---

### Post by greenhat on 2006-09-20
> **ubuntu_demon said:**
> From [https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/](https://launchpad.net/distros/ubuntu/+source/udev/+bug/6367/) :

> 
Quote:
Originally Posted by Scott James Remnant 
Officially marking as Rejected for dapper.

Here is the reasoning:

- We applied the “fix”, as planned, to the udev in Edgy Eft.

- While the fix corrected the problem described here, it caused new problems. Because it was a fundamental change to device ordering, it changed the order of other devices where more than one existed in the system — including other disks

- For Edgy this was not a problem, as the upgrade makes other changes that make device order non-important anyway

- These changes are too invasive for backporting to dapper

- This bug has a known workaround, which can be applied by the minority of users affected by it

- That workaround is preferable to causing far more working systems to cease functioning. :

FYI - I've been patiently waiting for this to be fixed in Edgy,  and as of Knot 3, it still isn't fixed!  Makes me think it's not going to make it, again :sad:

---

### Post by Jodokos on 2006-09-21
I have the same problem (I've made some "screenshots" of the boot without the "splash" option, if anyone is interested in it for debugging or so, I could send them).

After trying around for a few hours (unplugged usb devices, tried another cdrom-drive, etc...), I was able to boot into the live-cd desktop by unplugging all of my sata-drives.

This is not a very practical solution, but at least i'm able to try out the live-cd.

I think I will give ubuntu another "chance" as my windows-replacement, but not too soon...

[FONT="Courier New"][INDENT]System:
CPU: Mobile AMD Athlon XP, 1800 MHz
MoBo: ASRock K7VT4A Pro (Chipset: VIA VT8377A Apollo KT400A)
RAM: 1024 MB  (PC3200 DDR SDRAM)
BIOS: AMI (08/07/06)

Drives:
HD SAMSUNG SP2504C, SATA-II (unplugged for booting the livecd)
TSSTcorp CD/DVDW SH-W163A  (unplugged for booting the livecd)
TOSHIBA DVD-ROM SD-M1712 (thank god I still have an IDE device, or I wont be able to start ubuntu livecd at all)
[/INDENT][/FONT]

Looks like ubuntu will be the first "real" windows replacement for me, after I have tried a few distros the last years (suse 6, gentoo, knoppix6, suse 10) if it gets this problem fixed.

Greets
J.

---

### Post by rsambuca on 2006-09-21
I tried the live CD a few times, but it always froze at the "mounting root filesystem" stage (right near the beginning).

I tried adding "ide=nodma" to the boot options and it now works.

---

### Post by David Thomas on 2006-09-21
I also have this problem.  I have USB turned off in BIOS and am using PS/2 mouse & keyboard.  I don't even have a hard drive in the machine. 

I was really excited about 6.06.  But, looking through this thread, I see lots of people with problems and not real solution, just a hotdge-podge of suggestions.  This needs a FIX.

I was hoping to migrate the 7 machines I manage to Ubuntu,  but I guess its not ready for prime time.  ....its still too deep into geek teritory :(

---

### Post by neepster on 2006-09-21
Well, everyone has been raving about this distro for a while, so I decided to try it, and low and behold, there is a GIANT bug that makes it impossible to install without a giant amount of pain and the developers have decided not to fix it.  Frankly I find this hard to believe.  This certainly doesn't match what I heard about Ubuntu being a "quality" distro.

When's the next big distro update out?  Will THAT one be fixed?

---

### Post by Boztech on 2006-09-23
FYI, I had this problem with my AMD X2 / Asus A8R-MVP / WD SATAII system and solved it by disconnecting my internal USB card reader and using a PS/2 keyboard and mouse.

So far so good..

---

### Post by bubbafrye on 2006-10-01
well.. I read the first couple of pages of this thread when I too had this hang at "mounting root filesystem".
I confess that I did not read the whole (12 page) thread, but I did have success when I... 
1) ran the disk self-check (it hung for about 15 minutes at the  "mounting root filesystem", but then took off) 

and 
2) unplugged my USB mouse and printer.  Install hung at usual spot, but after I came back (~20 minutes later) I was greeted by a nice brown desktop.  I plugged in my USB mouse and it came to life right away.

I am now updating my video drivers.  we'll see how things are after a reboot.

good luck!

---

### Post by bubbafrye on 2006-10-01
Oh.. my system specs:

AMD Athlon X2 4600 (not AM2)
ASUS A8N - E
GeForce 6600 GT
2 gigs Corsair RAM
120 gig Maxtor IDE Diamondmax 10

---

### Post by rakesh343 on 2006-10-02
Slightly different problem, but can one help? When I started the installation initially from a CD, it booted successfully. But while installation, it gets stuck at the midway stage, displaying the message "No Root files" in a small dialog box. What to do?

](*,) ](*,)

---

### Post by bubbafrye on 2006-10-02
rakesh343:
did you try checking the install disk with it's self-check?  How about re-downloading and burning?



.. for the record my install didn't 'stick'.  I think it was a faulty Hard Drive (it used to be in an external shell that was *ahem* dropped a few times).  I will let you know more when I try it on a more reliable drive.

---

### Post by stolsvik on 2006-10-03
I just wanted to chime in here, and tell you my experience (I have it working now!):

After trying the Desktop CD a number of times, trying out the "disconnect USB stash" and various option w/o luck, I downloaded both the alternate CD and Knoppix.

Both of these, in particular Knoppix, pointed out much better what was the underlying real problem: it really **couldn't** mount the root filesystem (which at this point is on the CD) - and the reason is that it apparently can't read the CD.

I have a brand new system with a P5B Deluxe board, and it suddenly occurred to me what was the problem, so I searched and came up with [this]("http://www.csie.nctu.edu.tw/~cdsheen/enews/read.php?server=netnews.csie.nctu.edu.tw&group=comp.os.linux.hardware&artnum=333198")  suggestion: "The problem may be the PATA chip which doesn't have a Linux driver yet". Which seems correct - the board is apparently **too** brand new! The point is that the BIOS can boot the first stage from the CD, but when Linux have to take over the reading, it has no driver to do this, and the "error-message" the Desktop CD comes up with is **utterly useless** - it just stalls. (I've come across this exact same thing with a Windows 2000 install some years ago, but also here it did at least tell me what the problem was: No driver to read from CDROM - do you have one on a disk?)

I would at this point have loved if Unbuntu had the option of doing a network install from the CD, which would have solved my problem. But it doesnt, you have to go all the way and do a PXE-style booting: [wiki/Netboot]("https://help.ubuntu.com/community/Installation/Netboot"), [wiki/QuickNetboot]("https://help.ubuntu.com/community/Installation/QuickNetboot"). (This is very .. non-optimal .. , as the netinstall-stuff does actually reside on the Desktop CD - you have to load it using PXE, with all the hassle it involves. Why is that?!)

So, that was nearly it, BUT the Ubuntu kernel had one more surprise in hand: it didn't have a driver for the primary Gbps network port either! So I were just as stuck, but at least this problem was pointed out clearly. 
  However, on at least the P5B Deluxe version, there is a second port, and remembering that this was of an inferior type from some review of the board, I realized that it might be another type. After going into the BIOS for the millionth time, disabling the primary port, enabling only the secondary (and "enable ROM boot" or whatever it says, which gives two netboot choices, one which is PXE), I was finally in luck, and my new system is now up. Hopefully, some new version of the kernel will give me PATA CDROM and primary Gbps network access.

There is a number of things the Desktop CD could have done to help me not use around 8 hours on this:
[LIST]
[*]First and foremost point out that it couldn't read from the CD at all
[*]Secondly give the option of doing a networked install directly from the CD
[/LIST]

---

### Post by CallsignBaron on 2006-10-10
Don't mean to sound like a broken record her but I am having this problem as well and I am trying to install Edgy 6.10 knot 3. If this is a problem since Dapper and is still a problem in Edgy, does anyone know if the developers have acknowledged this and plan to fix?? Not much of a distro if you can't even install it. I'll be damned if I'll start unplugging my hardware to install.
BTW-Xubuntu installed just fine, whats up with that??

---

### Post by underbug on 2006-10-14
> **ol1v3r said:**
> This is a bit strange.. But I actually fixed my problem by burning it to DVD instead of CD.. Booted no problems at all ^-^
Give it a go on a DVD+RW? Just a suggestion anyways! :)

Yes!  I just tried this and it worked no problem.

Now if I can just get Ubuntu to recognise my
Cirque Glidepoint touchpad.....

---

### Post by treble101 on 2006-10-15
I had the booting stalls problem.  So I tried Breezy instead, which worken, then Xubuntu Dapper which worked as well.  Then I finally used the Alternate install CD instead and it worked flawlessly.  These were all clean installs.  The Desktop CD still doesn't work... 

I have a Sony Vaio PCG-SR33, an oldie.  Maybe it was a memory shortage...?

---

### Post by benblout on 2006-10-16
I have a simple question, which I have been unable to find an answer to by extensive reading and searching.

Is there any way to know if I am going to be hit by this bug before I upgrade?  I have working Breezy systems, and don't want to lose them if my systems are going to be hit by this bug.

Thanks,

Ben Blout

---

### Post by ubuntu_demon on 2006-10-17
> **benblout said:**
> I have a simple question, which I have been unable to find an answer to by extensive reading and searching.

Is there any way to know if I am going to be hit by this bug before I upgrade?  I have working Breezy systems, and don't want to lose them if my systems are going to be hit by this bug.

Thanks,

Ben Blout
I'm assuming all your systems are equal.

IMHO you should try and install Dapper one of your systems. (make sure to backup your important data of that system first ofcourse)

If you don't encounter the bug on this first system then you won't encounter the bug at all.

If you don't need LTS then Edgy might be an option because it doesn't suffer from this bug.

good luck!

---

### Post by benblout on 2006-10-17
> **ubuntu_demon said:**
> I'm assuming all your systems are equal.
<snip>
good luck!

Thank you for the suggestions, unfortunately, my systems are most definitely not equal.  I support a couple boxes for myself, and additional units for friends and family.  All of them are single-boot machines (ubuntu only, no other OS installed), but other than that the hardware varies all over the board, from PII to PIV machines, from one machine with just two IDE drives to one machine with IDE, SATA, and SCSI drives.

Again, sorry I did not make it clearer in my original question how disparate my systems are.

-Ben

---

### Post by greenhat on 2006-10-17
> **ubuntu_demon said:**
> ...
If you don't need LTS then Edgy might be an option because it doesn't suffer from this bug.

good luck!

I'm not sure which version of Edgy you're referring to, but I tried Knot 3 and it still has the problem.

---

### Post by Zeikcied on 2006-10-24
I have to admit I didn't read this whole thread, but I've had problems with this, too.

I downloaded the DVD iso for Dapper (Kubuntu) a couple days ago and have been using it in LiveCD mode to get my system ready.  It has worked fine the whole time.  I installed Kubuntu to hda (or rather hda2), and rebooted.

It gets to Mounting Root Filesystem, and then it kicks me out to a command line.  Some kind of built in shell.  (I'm still very new to Linux, so I have no idea what it is.)  The last few lines above mention that it tries to mount /dev/hda2, but can't because of "invalid arguments."  Then it tries to mount other things, and it says the file does not exist.  Probably because the root partition didn't mount.

I'm not sure if it is the same exact problem that others have had, but it's still a problem for me.  And it's a disapointing reintroduction to Linux for me.  (After unsuccessful attempts years ago with other distros.)

---

### Post by whiffy badger on 2006-10-27
Does anyone know if the "booting stalls during mounting root filesystem" issue has been resolved with edgy.  I first encountered this problem with Dapper using the installation CD, then after many attempts, inexplicably the CD started working. I installed Dapper successfully, thinking that the problem was over but as soon as I rebooted after installation I again encountered the very same problem, but now after a dozen or so attempts I have given up attempting to boot dapper.  I have decided to wipe out Dapper because of this.

I have downloaded edgy but this time all it does is freeze without achieving anything.  

I am very much a Linux noob but after all the praise, attention and hype lavished on ubuntu and the claims that "it just worked". I feel very disappointed that it can't even be predictably installed on a wide range of hardware.  

If this issue is still there with Edgy then I think I will give Ubuntu a miss.  Although much maligned, Windows does at least install itself reliably which is by any way of looking at it a fundamental if Ubuntu is ever going to be primetime.  

AMD 64 3200+
Asus A8N-VM
160 GB HD
1 GB memory
Nvidia fx6600-le graphics

---

### Post by greenhat on 2006-10-28
> **whiffy badger said:**
> Does anyone know if the "booting stalls during mounting root filesystem" issue has been resolved with edgy...

I have downloaded edgy but this time all it does is freeze without achieving anything...


I have the same problem with Edgy when booting from the live CD, it simply hangs at various points.  Once I got it to start the install process and partition the drive, then it hung copying files at 99%, a couple other times it hung after a successful boot, but I couldn't click the install icon.  Then once it hung partway through the install when trying to bring up the partition menu.  

The machine runs fine with Dapper but only using a dedicated drive.  If I try using a a dual boot drive, I get the dreaded boot stalls during "mounting root filesystem" problem, which is why I started posting on this thread 6 months ago.  Win XP works fine from the dual boot drive.

I'm disappointed as well, because I really want to continue migrating to Ubuntu, but this is holding me back. I've tried almost everything suggested in this thread over the past several months and still no joy. ](*,) 

System:
Asus P4-S533-MX
P4 2.4 CPU
512 MB RAM
ATI AIW 7500 Video
SB Audigy 2

---

### Post by rpradeep on 2006-11-28
I am using a HP visualize X Class 1GHz workstation and Samsung SH-D162C DVDROM.

Firstly My computer halt at mounting root filesystem and refused to go further. Then I changed the Firmware of DVDROM from TS04 to TS01 then it worked after several Buffer I/O error (ie only delayed the booting)

This also make delays in openning the DVD drive when new CD is inserted on Ubuntu desktop (after installation).

Recently I changed back my Firmware and changed the BIOS settings as follows.

In that i changed the IDE for my cdrom setting from AUTO to CDROM
and disabled UDMA.

Now it's working fine for me.

---

### Post by rpradeep on 2006-11-28
I am using a HP visualize X Class 1GHz workstation and Samsung SH-D162C DVDROM.

Firstly My computer halt at mounting root filesystem and refused to go further. Then I changed the Firmware of DVDROM from TS04 to TS01 then it worked after several Buffer I/O error (ie only delayed the booting)

This also make delays in openning the DVD drive when new CD is inserted on Ubuntu desktop (after installation).

Recently I changed back my Firmware and changed the BIOS settings as follows.

In that i changed the IDE for my cdrom setting from AUTO to CDROM
and disabled UDMA.

Now it's working fine for me.

---

### Post by devcaka on 2007-02-06
I had the same problem.. I thought I should post what fixed it..

replacing my secondary HDD.. I guess it was faulty although I couldnt find anything with scandisk..

goodluck to the rest of you guys..

devcaka

---

### Post by KenF on 2007-03-18
I give up with Ubuntu.
Breezy was great.  However the dist-upgrade to dapper has partially broken on my main machine (AMD 3200) due to the above USB drive/ordering issues.  Interestingly, Feisty (any Herd) doesn't install at all on my two other machines for other reasons (doesn't seem to support loading from a SCSI cdrom?).

My first install was slackware (1995).  My second distro was Redhat(5.2).  I played with Knoppix.  My third was Debian (a few of those).   I think I'm heading back to Debian, but if you have any recommendations, let me know.

Thanks,

KenF

---

### Post by mxreader on 2007-04-13
over 6 months later.... still no solution,

---

### Post by 8rdx on 2007-04-22
<mackie>**M'KAY!**</mackie>

So I read the original post, which is what my problem was, the cd hanging at "mounting root file system." I wanted to install ubuntu to an old Gateway (PII-450, 3.2G) and it had a Mitsui hard drive (which may or may not have been the problem).

I read through the whole thread, ignoring things that did not pertain to the original problem, and compiled this list of things to try to resolve it:

PHYSICALLY:
unplug USB devices
swap CD drive

IN THE BIOS:
change hard disk to be first boot device
changed the IDE for cd-rom setting from AUTO to CDROM
disabled UDM
disable USB2.0 support

ADDING TO BOOT OPTIONS: (F6 in the startup screen)
ide=nodma
acpi=off
irqpoll
linux no-hlt

CD:
try the alternate cd
try edgy cd (although now I guess it'd be feisty)
try breezy cd
try another debian cd (maybe freespire?)

This list is not in the order that I tried these options, but I will say that I tried three of them and one of them worked, so now ubuntu is installed on the Gateway POS. I will not say which one worked, because that will take away the fun for you.

:)

---

### Post by Josecuervo69 on 2007-08-18
I was able to fix this problem by disabling the "USB legacy support" option in the BIOS. Now I am able to boot Ubuntu with all USB devices attached. :) Hope this helps someone with this issues.

;o)

~Cuervo~

---

