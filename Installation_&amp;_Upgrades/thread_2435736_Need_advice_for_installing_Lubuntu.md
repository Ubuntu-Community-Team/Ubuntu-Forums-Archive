---
title: "Need advice for installing Lubuntu"
date: 2020-01-24
forum: Installation &amp; Upgrades
---

### Post by AbleTassie on 2020-01-24
I am trying to help a friend who is disabled and has PC problems. I ran into some problems installing Lubuntu on his PC and so need some advice.[B] 

Background:[/B] First my friend's PC, a Samsung ([specs]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/")) running on Windows 8.1 Pro was slow and poorly responsive, then it basically started freezing for hours on end, essentially useless. I figured he had viruses. I tried to scan the HDD by using ESET Rescue System (a Linux-based antivirus program, [link]("https://www.eset.com/int/support/sysrescue/")) by booting off a thumb drive and then scanning for viruses. Unfortunately it appears that there was a hibernated (Windows) NTFS partition the linux-based ESET Rescue System could not mount and so it appears the ESET System could not scan the HDD.

So, I decided to show him a trial Live boot with Lubuntu 16.04 LTS on a thumb drive. This trial live boot went well, we were able to access his email and he could play solitaire online. These two activities are apparently pretty much all of what he does with his PC. So I decided to try starting the permanent install of Lubuntu on his hard drive. But I got this message (I've learned, people on the forum are familiar with):
[I]This machine's firmware has started the installer in UEFI  mode but it looks like there may be existing operating systems already  installed using "BIOS compatibility mode". If you continue to install  Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later. If you wish to install in UEFI mode and  don't care about keeping the ability to boot one of the existing  systems, you have the option to force that here. If you wish to keep the  option to boot an existing operating system, you should choose NOT to  force UEFI installation here.

[/I]So I stopped and removed the USB drive per the Lubuntu protocol on the screen (shutdown > remove USB> press Enter). I do not necessarily want to preclude the possibility of him not using Windows 8.1 Pro in the future. It's not my PC. On the other hand he has no one else here to help him. And  Windows as presently on his machine is useless.

 He got the PC years ago and apparently no longer has any documentation or disks, etc.  I have read some of the Ubuntu UEFI info page [here]("https://help.ubuntu.com/community/UEFI") and realize that I may have to do some work in order to install Lubuntu more safely alongside Windows.But, as I said, Windows as presently on his machine is useless.In fact, something else has now also apparently changed with the booting of Windows: I tried to get back into Windows after removing the Lubuntu live boot USB, but got this boot message:*** All boot options are tried. Press <F4> key to recover with factory image using Recovery or any other keys for the next boot loop iteration**, *see attached screenshot.[SIZE=2][FONT=arial]I tried pressing the F4 key and other keys and the PC remains on this screen, so I cannot even boot into a useless frozen Windows anymore.

QUESTION(S): If I go back and force the Lubuntu install, do I run the risk of losing Windows 8 completely? Or could it be reinstalled later if it will not boot? I do not have a license key or disks, but perhaps there are free licenses around that could be used? 

Is there some other approach (as described, perhaps, on the Ubuntu UEFI info page [here]("https://help.ubuntu.com/community/UEFI")) to installing Lubuntu that might help maintain the original Windows installation and perhaps allow an antivirus scan that would make Windows functional again?

Thanks,

A.

[ATTACH=CONFIG]284894[/ATTACH]
[/FONT][/SIZE]

---

### Post by Skaperen on 2020-01-24
is there anything of value to your friend on this PC?  if not, then i recommend a full-disk clean-wipe and just install Windows all over, again.  does he have the CDs and original license code to do this?  if not then install Lubuntu on the clean disk.  be sure he's OK with losing everything.

if there are files to keep, get a partition map and show it in your next post.

---

### Post by guiverc on 2020-01-24
To virus scan the system, you'd need to boot into windows, turn off any 'fast boot' & cleanly shutdown (so the file system is in a safe/complete state, instead of parts of it stored in cache written in the hibernate/boot file instead of the file system correctly).

Ubuntu releases have a year.month format, so Lubuntu 16.04 LTS means it was the 2016-April release of Lubuntu, which only had three years of supported life, so is no longer supported, no longer gets security updates - as do all flavors of 16.04 LTS except for Kylin.  If you want to use 16.04, I'd recommend Ubuntu Server 16.04 LTS (no desktop so won't be suitable), or Ubuntu 16.04 LTS (desktop using Unity 7 desktop), or Ubuntu-Kylin 16.04 LTS - all of which have 5 years of supported life, all other 16.04 flavors are EOL & unsupported.  [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

I don't know your device, but 16.04 is rather old (being developed late 2015 & early 2016) so I'd expect better results with a newer OS (eg. Lubuntu 18.04 LTS which is supported until 2021-April (ie. 18.04 + 3 years) let alone having access to newer software, and security updates.  Yes a full-disk install (erasing windows) is far easier, but I can appreciate your desire to keep the older-OS door open (it's a lot more work though).

Also ensure you 
(a) validated your ISO was flawless - [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
(b) your write to install media was perfect - [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) (where CD refers to CD/DVD/hdd/ssd/thumb-drive/etc)

The Lubuntu manual installation reference is [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html) but note it refers to the current stable release (19.10)
[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
[https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)
which will of course differ for older releases.

---

### Post by AbleTassie on 2020-01-24
> **Skaperen said:**
> is there anything of value to your friend on this PC?  if not, then i recommend a full-disk clean-wipe and just install Windows all over, again.  does he have the CDs and original license code to do this?  if not then install Lubuntu on the clean disk.  be sure he's OK with losing everything.

if there are files to keep, get a partition map and show it in your next post.

Thanks for your replies Skaperen and Guiverc,

I don't think there is anything of value on the PC HDD. He does not communicate super well, he has something like cerebral palsy. But he still communicates well enough. I was able to poke around in the Windows 8 some before it really started freezing up. I suppose I might have been able to access the license key/code before it froze up, but I did not think it would freeze up as it eventually did.

He has no CDs or original license code. Somebody on another post in this forum said there are free Windows 10 licenses available. If that is true for Windows 10, I figure that maybe there are also free, legal, Windows 8 licenses or free, low cost CD/DVDs available if they should ever be needed. There is a version of his PC that is now on sale on Ebay for $199. I am surprised they are asking that much for it, but maybe a selling point is its large touch screen. I don't think he uses the touch screen though; I was showing him how to use it and he seemed not to realize he had a touch screen. I did not realize it either, but discovered it by chance.

What is a partition map and how do I get it? I am afraid I may be limited due to the hibernated Windows NTFS partition. I tried to look at Windows on his hard drive during the live boot Ubuntu session and I could not mount the files. I got this message: 
 &#8230;[SIZE=4][SIZE=2]..* the disk contains an unclean file system (0,0). Metadata kept in Windows cache, refused to mount. *[/SIZE]*[SIZE=2]Failed to mount &#8216;/dev/sda5&#8217; : Operation not permitted The NTFS partition is in an unsafe state. Please resume and shutdown Windows fully (no hibernation or fast restarting), or mount the volume read-only with the &#8216;ro&#8217; mount option.[/SIZE]*[/SIZE]

Thanks,

A.

---

### Post by AbleTassie on 2020-01-25
> **guiverc said:**
> To virus scan the system, you'd need to boot into windows, turn off any 'fast boot' & cleanly shutdown (so the file system is in a safe/complete state, instead of parts of it stored in cache written in the hibernate/boot file instead of the file system correctly).

Ubuntu releases have a year.month format, so Lubuntu 16.04 LTS means it was the 2016-April release of Lubuntu, which only had three years of supported life, so is no longer supported, no longer gets security updates - as do all flavors of 16.04 LTS except for Kylin.  If you want to use 16.04, I'd recommend Ubuntu Server 16.04 LTS (no desktop so won't be suitable), or Ubuntu 16.04 LTS (desktop using Unity 7 desktop), or Ubuntu-Kylin 16.04 LTS - all of which have 5 years of supported life, all other 16.04 flavors are EOL & unsupported.  [http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/](http://fridge.ubuntu.com/2019/03/01/ubuntu-16-04-6-lts-released/)

I don't know your device, but 16.04 is rather old (being developed late 2015 & early 2016) so I'd expect better results with a newer OS (eg. Lubuntu 18.04 LTS which is supported until 2021-April (ie. 18.04 + 3 years) let alone having access to newer software, and security updates.  Yes a full-disk install (erasing windows) is far easier, but I can appreciate your desire to keep the older-OS door open (it's a lot more work though).

Also ensure you 
(a) validated your ISO was flawless - [https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0](https://tutorials.ubuntu.com/tutorial/tutorial-how-to-verify-ubuntu#0)
(b) your write to install media was perfect - [https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck) (where CD refers to CD/DVD/hdd/ssd/thumb-drive/etc)

The Lubuntu manual installation reference is [https://manual.lubuntu.me/stable/1/Installing_lubuntu.html](https://manual.lubuntu.me/stable/1/Installing_lubuntu.html) but note it refers to the current stable release (19.10)
[https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html](https://manual.lubuntu.me/stable/1/1.1/retrieving_the_image.html)
[https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html](https://manual.lubuntu.me/stable/1/1.2/booting_the_image.html)
[https://manual.lubuntu.me/stable/1/1.3/installation.html](https://manual.lubuntu.me/stable/1/1.3/installation.html)
which will of course differ for older releases.


Thanks Guiverc,

I figured that I could not scan for viruses unless I got back into Windows and modified it as you have said. BUT, I could not and cannot get into Windows to do this. Your advice about getting a more current version of Ubuntu is good. I will certainly try that. I have done some Ubuntu/Lubuntu installations on my own machines, so I think I am aware of some of the things you are pointing out, but it is good to go over the points again. The specs for the device are [here ]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/") ; my guess is that the device will accomodate a newer version of Lubuntu fine. Any other comments from you or others will be appreciated.

Thanks,

A.[URL="https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/"]

[/URL]

---

### Post by CatKiller on 2020-01-25
> **AbleTassie said:**
> First my friend's PC, a Samsung ([specs]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/")) running on Windows 8.1 Pro was slow and poorly responsive, then it basically started freezing for hours on end, essentially useless. I figured he had viruses.

It could just as easily be a hardware problem with the drive. Given that it spontaneously became less functional after you started using it, that seems more likely.

According to the specs you linked to, that machine has a particularly slow spinning rust drive. Replacing that with an SSD would give it a new lease of life even if the old drive was working properly.

---

### Post by guiverc on 2020-01-25
My desktop is over a decade old (*c2q-9400, or before processors went i series*), and runs Lubuntu 20.04 fine (*or the development release that will be released in a few months*). The oldest laptop I have used today was a 2005 dell latitude d61 (*single core pentium M with 1gb ram*) which was running Lubuntu 18.04 LTS  (*used today for support purposes; thankfully I don't need it as it needs more ram, but I used it in testing Lubuntu 18.10 & 19.04 too*) so I'm convinced you won't have issues with later releases.

On initial reading of your first post, I blamed your issues on malware... after reading Catkiller's response I'm thinking I'd suggest validating the hardware too. ie.

   - a RAM test ('Test Memory' is how it appears on my d61 using Lubuntu 18.04 LTS; [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)); full test will take awhile but I think of it as good insurance

   - check your disk health (ie. it's SMART or self-monitoring  analysis and reporting technology built into most drives; [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools))  On Lubuntu 19.10 you can use *KDE Partition Manager* to view this info, on 18.04 LTS use `gnome-disk-utility` which appears as "*Disks*" in the menu), or `smartctl` via command if so inclined and love the raw data).  SMART keeps loads of stats, meaning it's not real easy to understand, but maybe worthwhile being good insurance.

For Lubuntu the pro's & con's of your release choices are as I see it

Lubuntu 18.04 LTS - a long term support release with 3 years of life, so until 2021-April, meaning you can set it and it should be okay for some time.  The negatives are it's a very old desktop (like old w2k  or early xp maybe) but that's also why some people love it; it's familiar. It's big weakness though it's the last LXDE for Ubuntu or Lubuntu.

*Lubuntu switched to the LXQt desktop in 18.10 which is where future work is now performed (upstream LXDE is pretty much on life-support with most devs having moved to LXQt; there are technical reasons for this; LXDE used old GTK2 technology which is dead) The significance of this history follows...*

Lubuntu 19.10 or the 2019-October release has a short 9 months release, so installing it means you'll have to move to Lubuntu 20.04 LTS within by 2020-July. This is the hassle with using 19.10. The benefit is it has an upgrade cycle; 20.04 will have 3 years of life after you've made that jump.  It is a more modern desktop, is very light, our Lubuntu manual assumes you're using LXQt now.

(*I knew touch screen works on 19.10; so I booted 18.04.4 on a sony thingy and it works there too. I can't say how well on either as I don't use touch*)

If you use Lubuntu 18.04 LTS you'll need to re-install to switch to LXQt, so that's the hidden hurdle with using Lubuntu 18.04 LTS to my thinking.  The main alternative to me would be using Xubuntu 18.04 LTS (which will easily upgrade to Xubuntu 20.04 LTS), though a number of other Ubuntu flavors can be used too.  As for which will be best for you; it's mostly a personal choice on what type of interface you like along the lines of which is the best cake (chocolate, banana, carrot etc)  Ubuntu Flavors can be downloaded for trial via [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours).  It's my opinion your box will run any Ubuntu flavor.  Some are less fancy when booted up, having less *flare*, but they stay out of your way which actually is good; but how much frosting do you like? or really your friend likes?

---

### Post by oldfred on 2020-01-25
That system is Haswell based, so should be UEFI/gpt.
Microsoft required vendors to install in UEFI boot mode starting with Windows 8 in 2012. Only systems that were upgrades from Windows 7 may be BIOS/MBR configuration.

Post this:
sudo parted -l

Not sure if this works or not to remove hibernation flag on the NTFS partition(s).
[https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

Best to boot Windows and shutdown without hibernation - all similar instructions:
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

---

### Post by AbleTassie on 2020-01-25
> **CatKiller said:**
> It could just as easily be a hardware problem with the drive. Given that it spontaneously became less functional after you started using it, that seems more likely.

According to the specs you linked to, that machine has a particularly slow spinning rust drive. Replacing that with an SSD would give it a new lease of life even if the old drive was working properly.

Thanks for your input CatKiller. Regarding SSDs, how much do they go for these days, $US/GB? His current drive is 500 GB, but given the fact that he really does not do much with his PC, a large SSD would not be necessary. I have replaced a couple HDD drives on a laptop and it's not particularly tough.

A.

---

### Post by CatKiller on 2020-01-25
> **AbleTassie said:**
> Regarding SSDs, how much do they go for these days, $US/GB? 

I had a quick look at laptop form factor (which is probably what's in there already, since it's 5400 rpm, although you should check) 500 GB SSDs on Amazon and they were £50-60, which Google tells me is around $65-75.

---

### Post by AbleTassie on 2020-01-25
> **guiverc said:**
> My desktop is over a decade old (*c2q-9400, or before processors went i series*), and runs Lubuntu 20.04 fine (*or the development release that will be released in a few months*). The oldest laptop I have used today was a 2005 dell latitude d61 (*single core pentium M with 1gb ram*) which was running Lubuntu 18.04 LTS  (*used today for support purposes; thankfully I don't need it as it needs more ram, but I used it in testing Lubuntu 18.10 & 19.04 too*) so I'm convinced you won't have issues with later releases.

On initial reading of your first post, I blamed your issues on malware... after reading Catkiller's response I'm thinking I'd suggest validating the hardware too. ie.

   - a RAM test ('Test Memory' is how it appears on my d61 using Lubuntu 18.04 LTS; [https://help.ubuntu.com/community/MemoryTest](https://help.ubuntu.com/community/MemoryTest)); full test will take awhile but I think of it as good insurance

   - check your disk health (ie. it's SMART or self-monitoring  analysis and reporting technology built into most drives; [https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools))  On Lubuntu 19.10 you can use *KDE Partition Manager* to view this info, on 18.04 LTS use `gnome-disk-utility` which appears as "*Disks*" in the menu), or `smartctl` via command if so inclined and love the raw data).  SMART keeps loads of stats, meaning it's not real easy to understand, but maybe worthwhile being good insurance.

For Lubuntu the pro's & con's of your release choices are as I see it

Lubuntu 18.04 LTS - a long term support release with 3 years of life, so until 2021-April, meaning you can set it and it should be okay for some time.  The negatives are it's a very old desktop (like old w2k  or early xp maybe) but that's also why some people love it; it's familiar. It's big weakness though it's the last LXDE for Ubuntu or Lubuntu.

*Lubuntu switched to the LXQt desktop in 18.10 which is where future work is now performed (upstream LXDE is pretty much on life-support with most devs having moved to LXQt; there are technical reasons for this; LXDE used old GTK2 technology which is dead) The significance of this history follows...*

Lubuntu 19.10 or the 2019-October release has a short 9 months release, so installing it means you'll have to move to Lubuntu 20.04 LTS within by 2020-July. This is the hassle with using 19.10. The benefit is it has an upgrade cycle; 20.04 will have 3 years of life after you've made that jump.  It is a more modern desktop, is very light, our Lubuntu manual assumes you're using LXQt now.

(*I knew touch screen works on 19.10; so I booted 18.04.4 on a sony thingy and it works there too. I can't say how well on either as I don't use touch*)

If you use Lubuntu 18.04 LTS you'll need to re-install to switch to LXQt, so that's the hidden hurdle with using Lubuntu 18.04 LTS to my thinking.  The main alternative to me would be using Xubuntu 18.04 LTS (which will easily upgrade to Xubuntu 20.04 LTS), though a number of other Ubuntu flavors can be used too.  As for which will be best for you; it's mostly a personal choice on what type of interface you like along the lines of which is the best cake (chocolate, banana, carrot etc)  Ubuntu Flavors can be downloaded for trial via [https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours).  It's my opinion your box will run any Ubuntu flavor.  Some are less fancy when booted up, having less *flare*, but they stay out of your way which actually is good; but how much frosting do you like? or really your friend likes?


Thanks guiverc,

I am interested in keeping this as simple as possible, so maybe Xubuntu 18.04 LTS would be the best choice, since it could be easily upgraded. I've never used Xubuntu, but I just looked at the Desktop environment on Wikipedia and, like Lubuntu, it is spare, which I like. If I were to live boot Xubuntu 18.04 LTS, what would I use to test the hardware? 

I did use such a utility once, in an Ubuntu based OS and it returned results indicating bad sectors on a hard drive. This led me to replace the HDD myself, as I mentioned in my last post. 

Would I have been able to have had such a successful trial live boot session using a thumb drive in a USB with Lubuntu if the HDD had major problems? If the HDD does indeed have major problems, would a temporary solution be live boot sessions off a USB or DVD/CD until the HDD is replaced? 

Regarding tests of the hardware, the ESET Rescue System also has a Memory Test program, Memtest 86+, so that could be used to test RAM. But the ESET Rescue System has no utility to test the HDD.

Thanks,

A.

---

### Post by guiverc on 2020-01-25
Everything I said except for the discussion of LXDE/LXQt applies to Xubuntu too.

Xubuntu uses the XFCE desktop. XFCE like LXDE used to be based on GTK2; however the XFCE team ported their desktop to GTK3 unlike the LXDE team which switched to Qt (Q toolkit). The switch from GTK2 to GTK3 has been ~invisible to end-users of the system.  Whilst testing Lubuntu on hardware, I use the same hardware to test Xubuntu as well (they were the other flavor to support x86 until mid-19.04 cycle), and it worked on my old pentium M laptops (the move from GTK2 to GTK3 did cause a slight drop in speed on Xubuntu which was noticeable, but on faster c2d (core 2 duo) type processors it was negligible or not noticeable at all). 

The memtest works the same with Xubuntu; I would use `gnome-disk-utility` to view SMART data in Xubuntu, or `smartctl` from command line  (I won't look for xubuntu media; but a quick scan of [https://packages.ubuntu.com/bionic/xubuntu-desktop](https://packages.ubuntu.com/bionic/xubuntu-desktop) makes it look like you may need to install it first, [https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gnome-disk-utility](https://packages.ubuntu.com/search?suite=all&searchon=names&keywords=gnome-disk-utility) so `sudo apt install gnome-disk-utility`).

As Xubuntu is using the toolkit (GTK+) as standard Ubuntu, you can almost use any standard Ubuntu program without wasting resources (that and you have 6GB means you don't need to worry either; 1-2GB it's a worry; 3-4 it's a consideration, 4+ considering it will waste more time than you'll likely lose)

Booting and running a 'live' system on a box with dead/dying hard drive will work normally. The 'live' system boots from your media & runs completely from RAM so it isn't impacted, the "/" file system it creates is in the machines RAM (not disk), so the only time it may look at the disk is in booting looking for any available swap space it can use; so a sick drive may slow that process a little (a dead drive even less) before it decides it's unavailable (ie. possibly a slower boot could be the only 'tell'). On boxes with no hard drive, or dead drives; 'live' media is how I'd use them.  

A live system is slower (the media comes from a squashfs or compressed; so it needs to decompress before it can use anything from the media - the decompression won't occur on an installed image, that and slightly slower performance in reading is the difference).

SMART is built into the drive itself; a number of programs will read the data off the drive, some of them can cause the drive to kick off it's own testing, but I would first just read the stats off the drive to see if it considers itself healthy.  Testing the drive is optional.

---

### Post by AbleTassie on 2020-01-26
> **oldfred said:**
> That system is Haswell based, so should be UEFI/gpt.
Microsoft required vendors to install in UEFI boot mode starting with Windows 8 in 2012. Only systems that were upgrades from Windows 7 may be BIOS/MBR configuration.

Post this:
sudo parted -l

Not sure if this works or not to remove hibernation flag on the NTFS partition(s).
[https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation](https://askubuntu.com/questions/145902/unable-to-mount-windows-ntfs-filesystem-due-to-hibernation)

Best to boot Windows and shutdown without hibernation - all similar instructions:
Fast Start up off (always on hibernation), note that Windows turns this back on with updates, SHIFT + Shut down button
[http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472](http://ubuntuforums.org/showthread.php?t=2324331&p=13488472#post13488472)
[http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html](http://www.tenforums.com/tutorials/4189-fast-startup-turn-off-windows-10-a.html)
[http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html](http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html)
[https://www.windowscentral.com/how-disable-windows-10-fast-startup](https://www.windowscentral.com/how-disable-windows-10-fast-startup)

Fred,

Thanks,

AbleTassie

**Here is the output you requested for sudo parted -l: **Sorry, I could not take screenshot as this is a live session**. **I also tried to straighten up table and could not.[U][B]

(ALSO SEE LATER EDIT BELOW WITH DISKS TESTS, THERE APPEARS TO BE A DISK PROBLEM.)[/B][/U]

To run a command as administrator (user "root"), use "sudo <command>".
See "man sudo_root" for details.

```
lubuntu@lubuntu:~$ sudo parted-l
sudo: parted-l: command not found
lubuntu@lubuntu:~$ sudo parted -l
Model: ATA ST500LM012 HN-M5 (scsi)
Disk /dev/sda: 500GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start        End          Size         File system       Name                                     Flags
 1          1049kB    525MB     524MB           ntfs             Basic data partition                  hidden, diag
 2          525MB     840MB     315MB          ntfs             Basic data partition                   hidden, diag
 3          840MB     945MB     105MB                             EFI  system partition                 boot, esp
 4          945MB    1079MB    134MB                             Microsoft reserved partition        msftres
 5          1079MB    500GB     499GB          ntfs          Basic data partition                        msftdata
 6          500GB      500GB     473MB          ntfs                                                              hidden, diag


Warning: The driver descriptor says the physical block size is 2048 bytes, but
Linux says it is 512 bytes.
Ignore/Cancel?
```[B]
LATER EDIT:[/B] I took some pictures of the output of the DISKS utility and the associated SMART data & self tests and a picture of the screen of the output of the sudo parted -l command that Old Fred recommended the photos are attached. [B]It looks like there is a HDD problem, as Disk Failure is predicted.
[/B]
[ATTACH=CONFIG]284902[/ATTACH][ATTACH=CONFIG]284903[/ATTACH][ATTACH=CONFIG]284904[/ATTACH][ATTACH=CONFIG]284905[/ATTACH]

---

### Post by oldfred on 2020-01-26
You can copy & paste terminal output directly here from a live installer's Firefox.
You use code tags to preserve formatting. # icon in forum's advanced editor.
Added tags & tried to clean up a bit, but if copied from terminal it just works.

Best to make sure you have good backups and get a new drive.

---

### Post by AbleTassie on 2020-01-27
Thanks to everybody for their responses, especially OldFred, guiverc, CatKiller, but also Skaperen,

I have taken into account everything that each of you has said. I have a few remaining questions before marking this thread as SOLVED.

 I plan to tell my friend he needs a new HDD. I'll have to remember to do a memtest86+ to check his RAM as well. 

In the meantime, while waiting for the disk and installation, I will make a bootable USB of Xubuntu 18.04 LTS that allows changes so that we can enter his wifi router password. His hand eye coordination is poor enough that it is a hardship to enter even a minimal length password, especially repeatedly. And I will try to change the boot order in his BIOS to boot off the USB drive first.

I downloaded via torrent an Xubuntu 18.04 LTS and I checked the SHA256SUM and it matched the downloaded iso file.

 **Questions:** (1) Is it really necessary to do the GPG key verification? It is pretty laborious as I remember, and I would need to relearn it.

 (2) If he uses the thumb drive for many live boot sessions, or continuously, is the thumb drive liable to wear out quickly? One of my concerns is that he is going to say, *"Why can't I just keep doing this with this thing (the thumb drive), and not order a new hard drive?"* He doesn't even know what a thumb drive is. I had thought of using a DVD disk, but I believe I would not be able to allow changes so his wifi router password to be recorded.

(3) Since it is not my PC, I was interested in trying to allow him the option in the future to use the Windows 8.1 Pro that came with the PC new, **_IF_** he should want to. (I am going to use Xubuntu in the meantime.) I think given the fact that his hard drive appears essentially dead (and I can't really mount it, at least easily, with Lubuntu), and he has no original disks or documentation for the Windows 8.1 Pro, it appears that there is no way to find his original Windows license on the hard drive, short of some costly sophisticated procedure. Is this correct? Are there cheap legal Windows 8.1 Pro licenses that can be obtained at this point?

Thank you,

Able

---

### Post by guiverc on 2020-01-27
(1) If the SHA256SUM was correct; I'd not worry about the GPG check myself.

(2) thumb-drives last pretty well when being READ, it's the WRITE that really causes the wear. Sandisk thumb-drives tend to give me 3-6 months of reliable use before they start becoming a hassle (ie. compares of saved data no longer match what I wrote to the media), but that is how I use them. I have other thumb-drives where I wrote data on it 6-8 years ago and I'd expect to be perfect (ie. little writing was done to that media).  Note: I'm no expert with thumb-drives, this is observational from my use (I've used about 9 today so far, writing 2 ISOs).  (I mainly use them for writing ISO's on them, ie. overwriting most of the media; not just little writes)

Sorry can't help with (3)

---

### Post by CatKiller on 2020-01-27
1: If you mean checking the files, it's not difficult; when you boot the install image there's a "check for defects" option that checks every file against its hash. It's more useful for optical media than a thumb drive, since you might have had a bad burn, but it's pretty easy.

2: All flash media has a finite lifetime. SSDs overprovision and have robust controllers and power circuitry, so their expected lifetime is the same or longer than that of hard drives. Thumb drives have some reasonable protective casing, and their own controllers, so a good thumb drive can last quite a while - I still use a 32 MB thumb drive, that I got free when The Bourne Ultimatum came out, when I'm doing BIOS upgrades. SD cards have no controllers and essentially no casing: they are optimised for being tiny and being cheap. They don't last very long at all.

3: I understand that if you're using UEFI Windows licence keys can be stored there in some fashion. The last version of Windows I used was win2k, so I couldn't tell you how to use that information to reinstall Windows.

---

### Post by CelticWarrior on 2020-01-27
(3) The Windows key(s) is indeed store in the EPROM, not in any storage device. So, you can at any time reinstall Windows just by downloading the ISO from MIcrosoft and burning it to a USB stick and it will activate just fine. Also don't forget downloading the heaps of drivers for that model.

---

### Post by AbleTassie on 2020-01-29
Thanks to everybody again,

I made a boot-able thumb drive with Xubuntu 18.04 LTS on it for live sessions. (I made it with the mkusb version dus.) I want to allow my disabled friend to use his PC for playing solitaire and email until I can obtain and install a new hard drive. I think a fully installed version of Xubuntu 18.04 LTS would work well for the interim.

 For that reason I hope to make a fully installed version of Xubuntu 18.04 LTS on another thumb drive using the procedure described at this article, [Run Ubuntu 18.04 from USB stick]("https://linuxhint.com/run-ubuntu-18-04-from-usb-stick/") , unless anybody here cautions me otherwise. My friend would use this full install version of Xubuntu with the thumb drive in place essentially all the time until I obtain and get the new hard drive.

Thanks,

A.

---

### Post by sudodus on 2020-01-29
It will probably work well enough until you install a new hard disk drive (or SSD if you want to be modern) with an installed system according to that link.

But on the other hand, it might also work to replace the cloned live-only Xubuntu system with a persistent live system in the USB thumb drive. mkusb can do it for you. And that system should also work well enough to install and run solitaire and an email client, and due to the way it manages the memory it will not wear the drive as much as an installed system.

Whichever method you use, I think it will work. Good luck :-)

---

### Post by AbleTassie on 2020-01-30
> **sudodus said:**
> It will probably work well enough until you install a new hard disk drive (or SSD if you want to be modern) with an installed system according to that link.

But on the other hand, it might also work to replace the cloned live-only Xubuntu system with a persistent live system in the USB thumb drive. mkusb can do it for you. And that system should also work well enough to install and run solitaire and an email client, and due to the way it manages the memory it will not wear the drive as much as an installed system.

Whichever method you use, I think it will work. Good luck :-)

Thank you sudodus,

I made a persistent live system on a USB thumb drive using the mkusb version dus, but the USB thumb drive does not appear in the boot menu for his PC. His PC is a Samsung ([specs]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/")) running on Windows 8.1 Pro. The USB thumb drive also failed to boot on my Acer E5-575 ( [specs]("https://www.cnet.com/products/acer-aspire-e-15-e5-575-5157-15-6-core-i5-7200u-6-gb-ram-1-tb-hdd-us-international/") ), which is just a couple of years old, see the attached photos (Acer Boot Failures 1 &2) of the boot menu screen in sequence for the booting of the Acer E5-575.

On the other hand, the USB thumb drive booted and worked in my Lenovo Y510 ( [specs]("https://www.cnet.com/products/lenovo-ideapad-y510/specs/") ) and my Qosmio (Toshiba) G55-Q804 ( [specs]("https://support.dynabook.com/support/staticContentDetail?contentId=2165304") ). See the attached boot photos (LenovoY510 Boot Successes 1 & 2), the second of these photos shows the 5 different Xubuntu live with persistence choices I was given to boot into (sorry about the shakiness of the photo). 

I suspect the difference between failures and successes has something to do with Classical Boot vs UEFI booting procedures.

QUESTION: Is there anything I can do to remedy the problem of the thumb drive not booting up (or even showing on the boot menu) for my friend's PC, Samsung ([specs]("https://www.cnet.com/products/samsung-series-5-500a2d-core-i3-3220t-2-8-ghz-monitor-led-21-5-series/")) ? 

As an aside, after the failure described above, I started to try to make a USB thumbdrive with a fully installed Xubuntu on it as described in the article[SIZE=3] [SIZE=2][Run Ubuntu 18.04 From USB Stick]("https://linuxhint.com/run-ubuntu-18-04-from-usb-stick/") using the [/SIZE][/SIZE][SIZE=3][SIZE=2]Qosmio (Toshiba) G55-Q804 ( [specs]("https://support.dynabook.com/support/staticContentDetail?contentId=2165304") ),  but when I got the part of creating a **"/dev/sdc2** EFI System Partition of 512MB," there was no "EFI System Partition" choice on the drop down menu for "Use As" in the "Create Partition" box. I am thinking that the lack of a choice may have to do with BIOS vs UEFI (or EFI) in the Qosmio (Toshiba) G55-Q804 ( [specs]("https://support.dynabook.com/support/staticContentDetail?contentId=2165304") ).

Thanks,

Able

[ATTACH=CONFIG]284939[/ATTACH][ATTACH=CONFIG]284940[/ATTACH][ATTACH=CONFIG]284941[/ATTACH][ATTACH=CONFIG]284942[/ATTACH]


[/SIZE][/SIZE]

---

### Post by sudodus on 2020-01-30
It seems to me that you have to **turn off secure boot** in an UEFI/BIOS menu in order to make the Samsung computer boot into the persistent live USB boot drive. (The UEFI/BIOS vary a lot, some allow booting Ubuntu based USB drives with secure boot, some don't).

Acer computers are also difficult to boot from USB. You may have to add a password for the UEFI/BIOS menu system in order to be allowed to turn off secure boot. And you had better remember that password. Otherwise the computer might be locked down for you.

---

### Post by AbleTassie on 2020-01-30
> **sudodus said:**
> It seems to me that you have to **turn off secure boot** in an UEFI/BIOS menu in order to make the Samsung computer boot into the persistent live USB boot drive. (The UEFI/BIOS vary a lot, some allow booting Ubuntu based USB drives with secure boot, some don't).

Acer computers are also difficult to boot from USB. You may have to add a password for the UEFI/BIOS menu system in order to be allowed to turn off secure boot. And you had better remember that password. Otherwise the computer might be locked down for you.

thank you sudodos,

I went into the BIOS and tuned off secure boot and that worked. I am writing this post from my friend's PC with an Xububtu Live system with persistence made with mkusb.

Thanks to everybody. I will  mark this thread SOLVED.

Able

---

