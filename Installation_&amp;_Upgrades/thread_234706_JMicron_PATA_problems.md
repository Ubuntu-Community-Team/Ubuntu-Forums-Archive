---
title: "JMicron PATA problems"
date: 2006-08-11
forum: Installation &amp; Upgrades
---

### Post by Encryptor on 2006-08-11
OK, so I bought a new computer yesterday.
A Core 2 Duo E6600 on an ASUS P5B Wi-Fi motherboard with 2 GB or RAM. RAID(0)-ed 3 Seagate SATA drives and left one SATA WD Raptor to be the boot drive. Also, there is 1 PATA connector which has 2 DVD drives connected into it: 1 Asus DVD-ROM and 1 LG DVD-Writer. As far as I understood, the ICH8R (with the Intel Storage Matrix for RAID) is responsible for the SATA hard-drives, and the JMicron JMB363 controller is responsible for the 1 external SATA port or the 1 internal PATA. ICH8R can be set into AHCI/RAID/IDE mode and JMicron into RAID/AHCI/IDE mode. So, I set the ICH8R into RAID mode (for the 3 Seagates) and JMicron in IDE mode (for the DVD-ROMs which are connected to the PATA port). Looking at the boot screen, I can see that everything was detected correctly. I get a notification (that everything is fine) about the RAID that I created  and,afterwards, I see that my 2 DVD-drives have been detected. Cool! So then I put the Ubuntu 6.06 (Kubuntu) DVD in the DVD drive and booted the system. I thought it would be nice to check the memory, so thats what I tried to do. I got a blank screen. The system was not responding even after I waited for 5 minutes. I restarted. Booted from the DVDrom again, and chose: Install Kubuntu. It loaded the kernel, I see the blue Kubuntu icon, and then the process stopped at : Mounting root filesystem. "Great" I said, when the system went back into the terminal and left me with a blinking cursor. 
"Ok.. lets try a text installation". The text-based installation seemed to start well.. I chose the language, I chose the keyboard layout.. but then I see "it" : Failed to detect the CD-ROM. "So where exactly did you boot from?" I asked the computer (boy am I glad I was alone in the office when talking to a computer). Afterwards, Ubuntu asked me whether I have a floppy with a driver, and I said No (where the hell should I go to find a driver for my dvdrom anyways?). And then I tried using the "cdrom" module along with /dev/cdrom. I didnt expect it to work - and it didnt, so that was pretty useless, but worth trying. And now, I press Alt+F2, go into the shell, and run: "ls -al /dev | more" . The output was beautiful: amongst other devices, I found these devices: sda, sda1, sdb, sdc, sdd. No hd*. (Now that I think about it, sda is probably the WDC Raptor, and sda1 is the windows partition on it [forgot to tell you that I created a partition on the WDC prior to booting the Ubuntu CD] ). Then I tried to mount /dev/sda1 to /mnt/sda1. "mkdir /mnt/sda1; mount /dev/sda1 /mnt/sda1" -> the error (it would be too easy if it worked) was "mount: Mounting /dev/sda1 to /mnt/sda1 failed: Illegal argument". Same thing happened when I tried variations of the command (I thought maybe this version of "mount" has a different way of taking parameters, but I couldnt get it to work anyways),I tried variations of the devices hoping that I will be able to find the device for the dvdrom (like sdb, sdc).. In the end I gave up on mount. The next thing I did was: read the system messages, or whatever they are called. so I run: "dmesg | more" and I start reading in hope that I will find something related to my DVD-drives. I remember seeing some lines about "sd module needs an update", some SATA drives being linked to "sdd", so I figured sdd must be my RAID0. Some warnings/messages (perhaps errors, don't remember) about sdb and sdc (and the message that the "sd" module should be updated). Logically, sdb and sdc should be the DVD Roms connected to the JMicron controller (which is in IDE mode). Now I am confused. PATA shouldn't be detected as SATA or SCSI. So I start searching the Ubuntu forums. It appears others have the same problem. One user happened to have the same chipset (P965) and the same LG DVD writer as I do. No solution in his thread except "load the ide-generic" module and some speculations about the SATA module (dont know which one) interfering with the detection of PATA drives if ata_piix is loaded after the sata module. And then somebody said something about booting in "expert" mode and choosing first the ide-generic module, and the load all the other ones. I tried: didnt work. So then I searched the internet. I found some hope here: [http://pcburn.com/article.php?sid=1590](http://pcburn.com/article.php?sid=1590) . 
I see that there are some patches to the kernel being applied to a release candidate of 2.6.18 (rc1). After checking kernel.org, I noticed there is a rc4 already, so the jmicron support should already be included in this release candidate. 
Great, now what? Is there a way to patch the driver on the DVD (assuming that I can edit the ISO with UltraISO on a Windows machine)? should I wait till they release 2.6.18? If so, when will the Ubuntu installation CD/DVD will actually include a kernel version with support for JMicron? 
I am pretty stuck right now, I hope somebody can advise me on how to get Ubuntu to work on my new machine.
Thanks in advance! and sorry for the long post, I had no time to make it shorter ;)

---

### Post by Encryptor on 2006-08-11
I accidentally replied to my own post :)

---

### Post by mtang on 2006-08-12
Hey, just wanted to pop in and say that I've been having exactly the same problem too with an Asus P5B Deluxe.  Any solutions would be great.

---

### Post by Encryptor on 2006-08-12
Is there another way of installing ubuntu?
I really liked the network installation of FreeBSD.. Load from a floppy, select a mirror and leave it over night.. anyways, if I could get ubuntu on the drive, then I could probably boot without the DVDroms and patch the kernel myself (assuming that the patch will solve my problem[CENTER][/CENTER]). what do you guys think?

---

### Post by mtang on 2006-08-12
I tried using instlux, which runs in Windows and puts a small Ubuntu installer on your boot partition.  You'd want the network version, not the CD-ROM one.  I tried the network, but couldn't get it to connect to the repository.  Maybe you'll have better luck?

---

### Post by kzt on 2006-08-13
I also have a P5B motherboard, and I am experiencing the same issues (Kubuntu 6.06 Desktop).  I don't understand why there is an issue with linux and the JMicron controller, since other OS' can use it without additional drivers.  As for the instlux net install, this fails because it doesn't support the Realtek ethernet controller.

---

### Post by mtang on 2006-08-13
I salvaged an old Ethernet NIC from an unused machine, and ran the net install of instlux using that, and I now have a happy Dapper install running :).  Still don't have access to the optical drives, but I'll live with that until I can figure it out.

---

### Post by Encryptor on 2006-08-13
For some reason, instlux refused to boot, so I downloaded a mini image from the main ubuntu server (i'll post the link later, its in the netboot folder). I managed to get it up and running with a bit of hassle. Indeed, there were problems with the Ethernet controller, but the funny thing is that 1 of the built-in LAN ports worked, when the other one didnt (it was detected, but no DHCP..)! :) I don't know why, but even in windows, 1 LAN port worked immediately, the other one needed a driver (i suspect they have 2 different controllers, one of them being unsupported). Anyways, Ubuntu is installing now,I am waiting for all the packages to be installed, and, hopefully, I'll have a running system in the next few hours. I plan to patch the kernel afterwards and I'll post the results. Pray for me, as this is the only hope left :) 
In the worst case, even if the patch doesnt work, I wont be able to use the DVD-ROMs until this gets fixed by the gods above :). Meanwhile, I'll try to understand why the RAID wasn't detected properly, but thats another story :) and another post :D
Am I wrong, or all these problems are because JMicron entered the market recently and nobody cared enough to support their products? And now that ASUS is using their controller(s), developers found out about them and are/will be working on supporting it?

---

### Post by Encryptor on 2006-08-14
I installed the 2.6.17.8 kernel. Didnt fix my problems.
Then I tried to install the 2.6.18-rc4-mm patch (which contains some fixes for JMicron), but it wouldnt patch: it complains about reverting some files and that it cant find several files. So I am stuck. Again. Any ideas on what to do further (except for waiting for Ubuntu 6.10), or any suggestions on how to get the 2.6.18-rc4-mm patch to work with the 2.6.17.8 kernel headers?

---

### Post by ihcnet on 2006-08-15
I have the exact same problem with the exact same motherboard. I found a forum post yesterday on some Fedora forum from Alan Cox, a kernel developer. 
He said that he had actually caused the probelm, and that a fix should be included in the kernel by the final version of 2.6.18. Here's a link: 

[http://fcp.homelinux.org/modules/newbb/viewtopic.php?topic_id=24885&forum=12&post_id=105517](http://fcp.homelinux.org/modules/newbb/viewtopic.php?topic_id=24885&forum=12&post_id=105517)

---

### Post by Encryptor on 2006-08-16
Thanks for the reply! I should thank Alan Cox for the time I spent on installing Ubuntu :) But, in the end, its a good thing that its going to be fixed ;)

---

### Post by moritz1 on 2006-08-20
I have exactly the same problem. PATA not detected, so my optical drive is useless. I was looking around for a driver on floppy disk but no success so far :(

---

### Post by thotz on 2006-08-22
> **moritz1 said:**
> I have exactly the same problem. PATA not detected, so my optical drive is useless. I was looking around for a driver on floppy disk but no success so far :(

Please, could you file a bug on bugs.ubuntu.com ? As far as I know this driver will be added in kernel 2.6.18 and Edgy will have 2.6.17, so please write a bug report, that the developers should add this driver to the Edgy kernel. Otherwise we won't be able to install Ubuntu on this (and a few other) motherboards. I think the driver is available in Fedora Core already...

---

### Post by Encryptor on 2006-08-24
I confirmed the bug. I will try to install kernel 2.6.17.11 today, maybe it will "magically" work with my drives :) although I haven't noticed anything interesting in the Changelog,since 2.6.17.9, the kernel i am running now.

---

### Post by thotz on 2006-08-28
> **Encryptor said:**
> I confirmed the bug. I will try to install kernel 2.6.17.11 today, maybe it will "magically" work with my drives :) although I haven't noticed anything interesting in the Changelog,since 2.6.17.9, the kernel i am running now.

Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.

---

### Post by Encryptor on 2006-08-29
> **thotz said:**
> Could you have a look at Ubuntu Bug [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

It will be fixed in Ubuntu Edgy soon.

Hurray!
Now, all I have to do is wait until October? ](*,) :)
I think the 2.6.18 kernel will be released in the following week or 2, so I'll compile it and use it :D and then I'll update to Edgy. I wonder if that will work?

But I am glad to see that the developers are doing there best to support us. Good job! :KS

---

### Post by amonsul on 2006-09-01
Ok! I have the same Problem with the same hardware....


But i cannot wait! Could i install Ubuntu with an external USB-DVD drive??????? Yoo know if it works?

---

### Post by amonsul on 2006-09-01
or maybe with SATA-DVDrecorder ???

---

### Post by lolikapuxa on 2006-09-01
Same Problem here. Hardware:
Intel core 2 duo E6400 
P965 board chipset
lg dvd drive

New machine, just bought today. 
This has to be the problem. 
With Gparted it doesn't detect the dvd-rom drive. With other distro's or live cds it complains always about the lg drive.

I hope the patch will fix the problem. Hurry dev's, i really need my ubuntu :D

---

### Post by playerX on 2006-09-02
It's possible to boot gentoo passing a parameter to the kernel on-boot, I'm installing that.
You can also boot from a sata dvd recorder/player or from an external usb device and you'll be fine.

---

### Post by Encryptor on 2006-09-02
> **playerX said:**
> It's possible to boot gentoo passing a parameter to the kernel on-boot, I'm installing that.
You can also boot from a sata dvd recorder/player or from an external usb device and you'll be fine.

Do you mind sharing the misterious parameter with the rest of us?
Is it "all-generic-ide"?

---

### Post by fireboxtester on 2006-09-02
I made a wiki page to put all of the information about this issue in one place:
[https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

As you can see it's a pretty major issue.  There are already 3 bugs and at least 9 forum threads regarding this.  Hopefully we can get this fixed for Edgy.  (I'm going to test Knot 2 later tonight)

---

### Post by spartas on 2006-09-02
> **Encryptor said:**
> Do you mind sharing the misterious parameter with the rest of us?
Is it "all-generic-ide"?

Yes, that is the boot paramater, but I couldn't get it to work under Ubuntu.  I had a bit of better luck with Fedora, still no install.

---

### Post by lolikapuxa on 2006-09-03
Has anyone tried the Ubuntu 6.10 (Edgy Eft) Knot 2 ? 
I saw the changelog, and it still uses 2.16.17 . I wonder if it is already patched.

---

### Post by fireboxtester on 2006-09-03
> **lolikapuxa said:**
> Has anyone tried the Ubuntu 6.10 (Edgy Eft) Knot 2 ? 
I saw the changelog, and it still uses 2.16.17 . I wonder if it is already patched.

I tested Edgy (Kubuntu Knot 2) last night and I just hit a blank screen.  Details on Wiki page( [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support) ). I'm meaning to test the Alternative Install so I can get a more detailed error.  

I'd like to hear what others find though just to be sure.

Is there any way to tell if it's supposed to be in Edgy yet?

---

### Post by Xfacter on 2006-09-04
> **fireboxtester said:**
> I tested Edgy (Kubuntu Knot 2) last night and I just hit a blank screen.  Details on Wiki page( [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support) ). I'm meaning to test the Alternative Install so I can get a more detailed error.  

I'd like to hear what others find though just to be sure.

Is there any way to tell if it's supposed to be in Edgy yet?

I get the same thing. I really hope they can get this fixed soon, as it's not very fun having to use an old computer for Ubuntu when I have a Core 2 Duo computer right here. ](*,)

---

### Post by Encryptor on 2006-09-06
I'm just waiting for the 2.6.18 kernel to be out.. then i will compile it and use it, and i'll finally have CD/DVD drives!! :)
ANd when edgy comes out, i'll perform an upgrade which will hopefully fix this annoying problem :/

---

### Post by spartas on 2006-09-06
Just a tip:
If you have another machine, you can load ubuntu on the drive from that system, put the drive in the new system and it will boot properly.

One caveat: You must attach the drive to the SATA ports connected to the intel chipset, and not the ones on the JMicron one.  You can tell because the intel chipset has more ports connected to it (usually 4 or 6) and they'll be a different color.

---

### Post by lolikapuxa on 2006-09-07
I read [this]("http://distrowatch.com/?newsid=03682#0") in distrowatch. It says OpenSuse Factory uses kernel 2.6.18rc5.
 Has anyone already tried this? I just can't download it since i've passed my ISP trafic.

---

### Post by zoto on 2006-09-08
I also have this same problem, Core 2 duo e6400, gigabyte 965p-ds3, pioneer dvd burner.  I've tried all of the newest edgy iso's to no avail.  I'm going to try a PIX installation, or perhaps install to the hard drive on another computer, then move it to the core2.  

For those getting a black screen, try hitting alt+f2 then back to alt+f1 and see if you can see an error. For some reason switching terms seems to make things show up on my computer...

---

### Post by Encryptor on 2006-09-08
Or you can use a network install CD of ubuntu.. it's called a "mini-image" i think.

---

### Post by taliosfalcon on 2006-09-08
the problem is even after installing from the network its not going to pick up your optical drives on pata..its really annoying how ubuntu doesnt like the all-generic-ide command..i like ubuntu better but fedora c5 installed and runs flawlessly on my ds3 mobo w/ the all-generic-ide entered during install ](*,)

---

### Post by Encryptor on 2006-09-09
> **taliosfalcon said:**
> the problem is even after installing from the network its not going to pick up your optical drives on pata..its really annoying how ubuntu doesnt like the all-generic-ide command..i like ubuntu better but fedora c5 installed and runs flawlessly on my ds3 mobo w/ the all-generic-ide entered during install ](*,)

Of course it won't, but the point is that you'll have Ubuntu running on your machine (assuming that you have SATA hard drives). How often users need the optical drives varies from one user to another, but I, for example, am not using the drives that often. The internet compensates a bit. Now, burning a CD/DVD is a different story :D

---

### Post by amorangi on 2006-09-09
I finally get my E6600 tomorrow, but I will have the same problem as everyone here with the P5B mobo.

My plan is to install from a USB flash drive, then upgrade to kernel 2.6.18 as soon as it is released, which should be quite soon (they're up to rc6 and talk is it'll be the last).

Is this idiot talk? (I've never done a flash install, nor upgraded the kernel).

---

### Post by bsodmike on 2006-09-11
I'm gonna wait for Edgy to come out and 'survive' on my slooooow P4 for the moment hehe...

---

### Post by willnapier on 2006-09-12
Several posts have mentioned waiting for Edgy. Hate to be a misery-guts, but if Edgy is going to be based in the 2.6.17 kernel, it's not going to help, is it? Isn't this important enough for the patch to be in whatever kernel Edgy uses? Who needs to know or decide this? I refuse to buy xp - I have not used windows for 3 years. My only way of using my new intel core 2 duo is by installing FreeBSD, which is a great learning experience but it doesn't even have things as basic as sound configured by default and is not good with java or flash. So I need K/ubuntu back!

If someone can assure me (or even give me crumbs from the Table of Hope) that Edgy WILL be installable, I don't mind waiting the few weeks and forgoing java flash sound etc.

Someone (actually a linux enthusiast at the company who built my box) said that it is pretty trivial to patch a kernel and make up a custom install cd. Do I take from the fact that nobody has done this yet, that it isn't so trivial? Or could one learn to do this without being an expert?

With thanks for any comfort.

Will

---

### Post by SFAOK on 2006-09-13
> **willnapier said:**
> Several posts have mentioned waiting for Edgy. Hate to be a misery-guts, but if Edgy is going to be based in the 2.6.17 kernel, it's not going to help, is it?

(I think) the bug page says the patch was back-ported which I think means the fix for the problem was put into the 2.6.17 kernel Edgy will use. But I could be wrong here.

> **willnapier said:**
> If someone can assure me (or even give me crumbs from the Table of Hope) that Edgy WILL be installable, I don't mind waiting the few weeks and forgoing java flash sound etc.

Yeah, would be nice. Saying that, Knot 3 will hopefully be released tomorrow and I'm hoping it'll provide some more information.

> **willnapier said:**
> Someone (actually a linux enthusiast at the company who built my box) said that it is pretty trivial to patch a kernel and make up a custom install cd. Do I take from the fact that nobody has done this yet, that it isn't so trivial? Or could one learn to do this without being an expert?

Yeah, I was wondering this as well. It'd be nice to have Dapper as an alternative to Edgy in case Edgy installs OK but is unstable for whatever reason.

---

### Post by willnapier on 2006-09-15
Hi everyone. Well, in the end, after two weeks trying to use FreeBSD and finding how unfriendly it is to the soho/private user, I have bought my way out of not being able to use K/ubuntu... it occurred to me that if there were such a thing as a SATA DVD Writer, then you could just by-pass the JMicron controller completely. And there is. Two actually - one by Plextor costing around GBP 70, and one by Samsung, the 'Writemaster' SH-W163A DVD writer, which you can pick up online for GBP 25-30. I dashed down to Tottenham Court Road and bought one there and then. You will probably need a sata cable, and a molex to sata converter so you can use the power supply in your case (together costing another GBP 6 or so). I set it up in 30 minutes and .. well, it works!! I cannot tell you how relieved I am. The install process recognized all my new equipment (apart from the optical drives that are ide/pata) and installed fine. Everything just works. The contrast with FreeBSD is incredible (although to be fair, there are PCBSD and DesktopBSD that claim to be more user friendly but neither of their install cds would start up on my new system). What a relief! I can now get on with my life!

For the record though, some other options that I didn't try were:

1) compiling a new kernel with the patch in it (or is there a ready-made kernel with the patch now?) - on my old pc - then moving the old hard disk into the new pc (having to use the pata connection used by the two optical drives), then copying (using 'dd' - look it up under 'man dd') the whole thing onto the new hard disk, then removing the old hard disk and reconnecting the two optical drives.

2) using Tom's Root Boot (TBR) to get a minimal linux booting from floppy, then using an iso of the install cd on a usb key to install. This is different from making up a bootable usb key, which I tried but was over my head.

Perhaps you can see why I preferred to my the writer. Anyway, I'm a very happy bunny now and hope you can be too.

Will

---

### Post by amorangi on 2006-09-15
I did try the "[Installing Ubuntu from a Flash Drive]("https://help.ubuntu.com/community/Installation/FromUSBStick")"  to no avail (just kept getting No Operating System Found. 

I too would be interested in knowing how to make an install CD with an upgraded kernel. Can anybody point me in the right direction on how I would do this?

---

### Post by Cynical on 2006-09-16
Btw the patch was backported so there will be no problem with edgy when its released. I'm just hoping it'll show up in one of the daily builds sometime soon

---

### Post by bsodmike on 2006-09-18
Thanks for the heads up Cynical.  I really don't want to spend 30+ quid on another optical drive (when I have a perfectly decent one already) just to install Unbuntu.

That said, it's nice to hear that there is away around this issue for anyone in a serious hurry (and cash to spare!).  Please keep us updated if you see this patch in one of the daily builds :D

---

### Post by amorangi on 2006-09-18
Apparently it should be in the daily build today (18th). Here's hoping!

---

### Post by bsodmike on 2006-09-18
Where did you hear this amorangi?  

The latest I can see is 15th.  Please provide a link when possible :)

---

### Post by ph8 on 2006-09-18
It was in today's *kernel* build, which should make it into a CDImage tomorrow (19th) I hope it works after all this hoo-hah or i'll have to start using fedora (#-o)

---

### Post by sleeperknight on 2006-09-18
the 18th daily builds are not out yet

---

### Post by CodeMonkeyX on 2006-09-18
I am downloading a new kernel system update for Dapper right now, it includes a patch that adds support for the JMicron chip.

[http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17-7.20/changelog](http://changelogs.ubuntu.com/changelogs/pool/main/l/linux-source-2.6.17/linux-source-2.6.17_2.6.17-7.20/changelog)

So if you already have Ubuntu running on your P965 motherboard then hopefully the PATA drives should now work when connected to the JMicron connector. 

Can anyone confirm this is working?

If this new Kernel works, then another option would be to make a [custom Ubuntu install CD](https://help.ubuntu.com/community/InstallCDCustomization?action=show&redirect=InstallCDCustomizationHowTo) with the new kernel package, and the using the new Kernel. Then maybe you will have an installable CD with Dapper on it?

---

### Post by amorangi on 2006-09-19
There's a daily build dated 19th out now - dare I hope that this will solve everything?

---

### Post by bsodmike on 2006-09-19
[st]Got a link for the rest of us m8?[/st]  Found it nm :)

---

### Post by amorangi on 2006-09-19
Daily builds are [here]("http://cdimage.ubuntulinux.org/daily/current/").

---

### Post by sgifan67 on 2006-09-19
Hello,

I also own a P5B motherboard and tested the build from the 19 (today). 

No success, no change...

I checked Mandriva 2007.0 RC2 released yesterday and it works. they also use a 2.6.17 kernel

Remark to all P5B users, when testing do not forget to set the JMicron controller to AHCI mode and not IDE. It won't work in IDE mode.

---

### Post by kerneloftruth on 2006-09-19
Hi,

I don't know, how experienced you guys are, but you could give the kernels in my [kernel roundup on forums.gentoo.org]("http://forums.gentoo.org/viewtopic-t-498160.html") a try: they work without any problems for me (p5w dh deluxe with 2 IDE-harddrives connected to JMicron)

follow this [guide]("http://ubuntuforums.org/showthread.php?t=56835") if you have problems with configuring a kernel on your own; the most important settings should already be discussed in my kernel roundup

my Bios settings are:
- JMicron Boot-ROM enabled
- Controller set to Basic mode

For those, who really need a running Linux, try my livecd:
[ Gentoo livecd with JMicron support]("http://forums.gentoo.org/viewtopic-t-494931-start-0-postdays-0-postorder-asc-highlight-.html")

I'm really hoping that this issue will be solved in the final Edgy release ...

Good luck guys

---

### Post by ShaneG on 2006-09-19
> **amorangi said:**
> Daily builds are [here]("http://cdimage.ubuntulinux.org/daily/current/").

Has anyone tried this disc yet? I'd rather not download it without knowing first. 

Thanks!

---

### Post by amorangi on 2006-09-19
Yes, I've tried it, and unless I missed something it doesn't work. I'll try again with the next daily, but otherwise I think I'll have to switch to another distro.

---

### Post by sleeperknight on 2006-09-19
> **ph8 said:**
> 
In other news, the kernel failed to build for the build today (19th) so hopefully it will be sorted tomorrow! (20th) Here's too hoping!

I just hope, but dont expect

---

### Post by sargosis on 2006-09-21
Apparently, Ben collins is working on making a fix to the kernel now, he says he should have it out and done by tomorrow. Here's the link where i'm getting all my info:

[https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502)

However, i'm still really new to all of ths and i was hoping to simply ask:

Since it looks like he's just fixing the kernel, how do i use the updated kernel to fix the problem with the install CD? or is there someone out there that can take the kernel and update the CD? It seems that although a fix is within our grasp, those of us new to linux may be forced to wait ntil Edgy Eft comes out.

---

### Post by nuggien on 2006-09-21
Just download one of the isos from here tomorrow (9/22):  [http://cdimage.ubuntulinux.org/daily/current/](http://cdimage.ubuntulinux.org/daily/current/)

Those will incorporate Ben's fixes.

---

### Post by sargosis on 2006-09-21
Thanks. Appreciate the help.

---

### Post by amorangi on 2006-09-22
I have Ubuntu 6.05 running on my Asus P5B Deluxe, but it wasn't really the solution I wanted, nor does it appear to have solved all the issues.

First I had to install Windows XP <shudder> on a small (4GB) partition. With an E6600 this only took about 20minutes. Unfortunately I used a "home edition" version which needs activation rather than a corp version, but I'll probably just delete it again anyway, and 30 days was long enough for the task at hand ;) 

Then I used instlux to do an install from the intenet for Ubuntu6.06 (instlux doesn't really "run from windows" as claimed, so I was unable to install from CD as I'd hoped). All went well, it took about 90 minutes.

I then followed the thread on upgrading to kernel 2.6.17, except that I did it for kernel 2.6.18. That too was pretty straightforward. I'm not sure how long it took to compile the kernel, but probably an hour or so. And it worked first go.

The only problem is - still no CD-ROM! What did I miss?

---

### Post by bsodmike on 2006-09-22
Could someone pls confirm that the 22nd's daily works?

---

### Post by StefanSteinheimer on 2006-09-22
22nd's daily doesn't work for me. :-(
Edit: The fixed kernel (version 2.6.17-9.23) is not on the CD. The version on the CD is 2.6.17-7.20 from Sept. 18th.

---

### Post by wkulecz on 2006-09-22
I've an Asus P5Bdeluxe running Windows 2000 and when I changed the JMicron BIOS setting from IDE to RAID (to enable the external SATA port as I understood the docs) I lost the CDROM on the IDE drive!

The Windows 2000 JMicron drivers are installed and show no errors in Device Manager, just the CDROM and if I remember correctly its IDE ports are gone.

This may not be Linux's problem to solve!

--wally.

---

### Post by SFAOK on 2006-09-22
> **wkulecz said:**
> I've an Asus P5Bdeluxe running Windows 2000 and when I changed the JMicron BIOS setting from IDE to RAID (to enable the external SATA port as I understood the docs) I lost the CDROM on the IDE drive!

Something similar happened to me when I changed it from IDE to ACHI (I have a P5B). I had a copy of Open Suse 10.2 Alpha 4 and I was able to install with those settings. With it set to IDE, IIRC Suse complained there was no CD drive.

Booting into Windows with the setting on AHCI, Windows loads drivers for the JMicron Controller. In Device Manager, there are two JMicron Controllers listed, one with the little warning sign suggesting something's not right... I'm wondering what would happen if I removed the controller from Device Manager with the setting on IDE, rebooting, changing the setting to AHCI and seeing what Windows does...

---

### Post by sgifan67 on 2006-09-23
build of 23-09 that contains ben's latest kernel
does'nt solve the probleml on a P5B

The CD rom on JM363 IDE port is not detected...
With the bios set either in AHCI mode or in IDE mode.

So for now i'm stuck with mandriva, that I really dislike.

my main desktop was on ubuntu since warty 4.10 so almost 
two years.

I think I really did a mistake upgrading to code 2 duo 
so early...

---

### Post by bsodmike on 2006-09-23
Today I booted off the 22nd cdimage and it no longer gets stuck at 'decompressing kernel'...so \o/.

However, it can not find the CDROM drive lol.  I'm downloading the 23rd's DVD image, and am hoping to give this a shot.

---

### Post by SFAOK on 2006-09-23
> **bsodmike said:**
> Today I booted off the 22nd cdimage and it no longer gets stuck at 'decompressing kernel'...so \o/.

However, it can not find the CDROM drive lol.  I'm downloading the 23rd's DVD image, and am hoping to give this a shot.

According to the latest comment on the page in [launchpad]("https://launchpad.net/distros/ubuntu/+bug/57502"), the installer is still using a broken kernel, so it won't work...

---

### Post by wwuster on 2006-09-23
I tried the cd from the 23rd. Still doesn't work.

William

---

### Post by SFAOK on 2006-09-23
> **SFAOK said:**
> Something similar happened to me when I changed it from IDE to ACHI (I have a P5B). I had a copy of Open Suse 10.2 Alpha 4 and I was able to install with those settings. With it set to IDE, IIRC Suse complained there was no CD drive.

Booting into Windows with the setting on AHCI, Windows loads drivers for the JMicron Controller. In Device Manager, there are two JMicron Controllers listed, one with the little warning sign suggesting something's not right... I'm wondering what would happen if I removed the controller from Device Manager with the setting on IDE, rebooting, changing the setting to AHCI and seeing what Windows does...

So I've been looking into this today and I'm a little :(

Apparently, if you want to leave the settings as AHCI in the bios, you have to install Windows with that option and use a floppy disk to load drivers, otherwise it won't work when you turn it onto AHCI later. So as it is, I'll have to switch bios settings when I want to boot into the other OS on my drive...

If anybody can help me clear this mess up, I'd be grateful!

---

### Post by bsodmike on 2006-09-23
/me gives up, gonna wait for Edgy final.

---

### Post by sargosis on 2006-09-23
Even if the kernel was fixed and those of us with P5B mobos managed to install Ubuntu, the drivers for the board (sound, ethernet, Jmicron, etc) are not available for the linux community and wont be for quite some time. I really hate to have to do this, but i'm switching back to windows. 

Personally, i can't stand windows, but what's the point in linux if my computer ca't even support its own hardware?

---

### Post by SFAOK on 2006-09-23
> **sargosis said:**
> the drivers for the board (sound, ethernet, Jmicron, etc) are not available for the linux community and wont be for quite some time.

Well, I've installed Fedora Core 5 and Suse 10.2 alpha 4 and the sound worked on both installs (I've got a P5B). JMicron is the issue here and support should be added in the kernel any day now. The ethernet is the other problem, there are drivers available but they take a bit of work to install...

---

### Post by penguins! on 2006-09-24
I struggled with this problem for hours on a freshly built Conroe E6600 system with a GIGABYTE GA-965P-DS4 P965 mobo.

Eventually I settled for a temporary fix and connected my optical drive to my   external USB ide enclosure. Install CD paused for a few seconds on "Mounting root filesystem.." but then proceded to boot. Happy days.

Or not. Ubuntu won't detect my SATA disk. Tried the alternate install cd too. The partition manager can't see any devices at all. The drive is connected to the Intel controller in AHCI mode. I even tried completely disabling the JMicron controller. 

I think I might have to wait fro Edgy final too ](*,)

---

### Post by jaredvolkl on 2006-09-25
I'm posting this from Ubuntu. I don't know how I didn't get this before, but apparently I figured out the right combination of settings in my BIOS to boot from my IDE CD-ROM with a USB adapter. Install went fine, SATA disk works great, but I still have no IDE.

I read a ton about how to compile custom kernels while trying to get a custom livecd going with 2.6.18 on it, but I was never able to do it. Still, I think it'll help me try to compile that kernel in so I can have IDE support.

BTW, I didn't have to change to AHCI in my BIOS, I left it at IDE and I was OK. Not sure if I'll have to change that once I get the new kernel compiled in though.

---

### Post by SFAOK on 2006-09-25
Anyone tried todays daily (25th)?

---

### Post by sgifan67 on 2006-09-25
> **SFAOK said:**
> Anyone tried todays daily (25th)?


wait for tommorow (26th) at least. The edgy-change 
shows that a new debian-installer with the updated 
kernel was submitted at nount the 25th.

---

### Post by SFAOK on 2006-09-25
Sounds promising, plus the Beta is due on the 28th. Fingers crossed :)

---

### Post by wwuster on 2006-09-26
I did get my system mostly running. I have a core 2 duo with a new intel
DP965LT motherboard. Everything is now running except access to the cdrom drive. Sound works. I did  disable the onboard ethernet controller and just
used a pci one that I had because I wasn't sure the internal one would yet work.

I used the mini.iso from here:
[http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/)

This then installed edgy from the internet and it's been working fine for a few days. After edgy is released I'll enable the internal ethernet controller and try that. The updates have worked fine so I'm hoping that there will be a new kernel update in the next few days that will get the cdrom/dvdrom drive running.

Oh yes, I had to change the bios setting for the sata drive to ahci. It was set to IDE.

William

---

### Post by SFAOK on 2006-09-26
From the bug page:

> This is properly fixed (i'm told) in the -10 kernel which will take a few days (at least) to make its way into the debian-installer package and, from there, to a daily image.

How can I tell which kernel the installer is using?

---

### Post by wkulecz on 2006-09-26
> Personally, i can't stand windows, but what's the point in linux if my computer ca't even support its own hardware?

You have to choose hardware for the software you plan to run.  I got my P5Bdeluxe specifically to run Windows 2000 (Photoshop and video editing), I otherwise got off the windows boat at XP.  I knew it would be a problem for Linux right now, so I'm not even trying,  but your P5B would be even worse off if Windows98 was what you wanted to run.  

I spent a fair bit of effort making sure W2K drivers were available for all the hardware on board and the video card I bought, before I bought them.

To follow up, I did get the JMicron SATA internal port to work along with both DVD burners on the IDE ports by leaving the BIOS setting at IDE.   Rextest (from Canopus to see if your hardware is OK for their software) showed more than good enough read/write speeds on the JMicron SATA drive, both burners burn, so I'm happy.

So I see now Linux support for the JMicron controller in whatever mode is lacking in Ubuntu.

--wally.

---

### Post by websurrfr on 2006-09-26
I too have a P5b motherboard (vanilla, not deluxe) with the Jmicron controller issue.  Am I correct in understanding that if I download an install ISO, the Desktop version for example, in the next few days that it should work properly?

---

### Post by SFAOK on 2006-09-26
> **websurrfr said:**
> I too have a P5b motherboard (vanilla, not deluxe) with the Jmicron controller issue.  Am I correct in understanding that if I download an install ISO, the Desktop version for example, in the next few days that it should work properly?

Check out the [bug page]("https://launchpad.net/distros/ubuntu/+bug/57502"). Apparently a daily incorporating the fix should soon be available - hopefully for the beta (due on the 28th), maybe sooner, maybe a little later. Not long to go either way (touch wood! :))

---

### Post by websurrfr on 2006-09-26
Thanks.

---

### Post by jaredvolkl on 2006-09-27
> **SFAOK said:**
> So I've been looking into this today and I'm a little :(

Apparently, if you want to leave the settings as AHCI in the bios, you have to install Windows with that option and use a floppy disk to load drivers, otherwise it won't work when you turn it onto AHCI later. So as it is, I'll have to switch bios settings when I want to boot into the other OS on my drive...

If anybody can help me clear this mess up, I'd be grateful!I'm in the same boat my friend. Let me know if you ever get this fixed. I'm sure I'll reinstall Windows eventually, so I'll get it working sometime, but if I can get it in the meantime, that's even better.

---

### Post by sgifan67 on 2006-09-27
todays build is updated with correct kernel 2.6.17-10

I have CD AND Harddrive connected on JM363 

Install works fine, partitionned my HD, copied the whole files

but then at reboot GRUB gives an error 21 and won't boot

So I think now the next thing to correct is GRUB...

I suppose if i had used an SATA hd the reboot would have been ok.

So the correction is ready for those of you using a SATA HD

---

### Post by hetauma on 2006-09-27
Is there an way to check the changelog for each daily cd?
And also does anyone know if the 2.6.17-10 kernel works also with other mobo's with Jmicron controller? mine is gigabyte ga-965p-ds3

---

### Post by websurrfr on 2006-09-27
How do you get the "Daily build"?  Are the normal downloads from Ubuntu.com/download updated daily on all the mirror sites?

---

### Post by hetauma on 2006-09-27
You can find daily images at
[http://cdimage.ubuntulinux.org/](http://cdimage.ubuntulinux.org/)

---

### Post by bstock on 2006-09-27
Ok, so I downloaded the daily build located here: [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/)

Got the 'PC alternate install CD'. Says it was last modified on 09-27-2006 at 15:32.

Tried to boot it up and still got errors saying could not detect cdrom, with or without all-generic-ide passed to boot options. Dropped to console and did 'ls /dev/sd*' and showed nothing. Nothing for /dev/hd* either, though I'm running 2 SATA hard drives and an IDE cdrom on an Intel BOXDG965RYCK (found [here]("http://www.newegg.com/Product/Product.asp?Item=N82E16813121048")).

If I change BIOS to AHCI, I can then see my hard drives in /dev, but no cdroms. I'd really like to avoid installing in AHCI mode as Windows will not boot in that mode, and I'd like to dual boot without re-installing windows or changing the BIOS each time I want to switch OS's.

Shouldn't the new 2.6.17-10 kernel be able to detect everything, or will I have to wait until 2.6.18?

Thanks for everyone's help, I'll keep watching to see if anyone has any success.

---

### Post by hetauma on 2006-09-27
Downloaded the 27/09 daily cd and tried to install on a system with Gigabyte ga-965p-ds3 motherboard with IDE cdrom and SATA HDD.

From bios settings I tried both IDE and AHCI mode and in both cases I tried with and without all-generic-ide flag.

On all four combinations the installation started nicely and found the cdrom.

Strange thing tho is that in none of the cases it could find my sata hdd. :( 

Isn't that a bit strange since even 6.06 could find my hdd but not the cdrom?

Any ideas if there is any other issue that is preventing the installer from finding my SATA hdd?

---

### Post by pallekuling on 2006-09-27
Have been following this thread for a while, as I was unable to install Ubuntu 6.04.

I just installed the 09/27 Edge build, and the installation finally went fine on my Asus P5B :)

All my harddrives are SATA, and i had to enable AHCI mode in the BIOS.

---

### Post by penguins! on 2006-09-28
> **hetauma said:**
> Downloaded the 27/09 daily cd and tried to install on a system with Gigabyte ga-965p-ds3 motherboard with IDE cdrom and SATA HDD.

From bios settings I tried both IDE and AHCI mode and in both cases I tried with and without all-generic-ide flag.

On all four combinations the installation started nicely and found the cdrom.

Strange thing tho is that in none of the cases it could find my sata hdd. :( 

Isn't that a bit strange since even 6.06 could find my hdd but not the cdrom?

Any ideas if there is any other issue that is preventing the installer from finding my SATA hdd?

I have the DS4 and it can't find my SATA disk either. Are you using the Intel controller?

---

### Post by hetauma on 2006-09-28
> **penguins! said:**
> I have the DS4 and it can't find my SATA disk either. Are you using the Intel controller?

yeap I had the sata hdd connected on the intel controller.

Then I connected the sata hdd on the purple slots (same controller for the ide cdrom) and it worked fine. I have now a working ubuntu edgy. 

So this might imply to users with other motherboards who have sata hdd and ide cdrom. Try and connect them all in the same controller (Jmicron one)

Note: I installed ubuntu with the 28/9 daily cd. Not sure if 27/9 works since when I tried it I had the hdd connected on the intel controller

---

### Post by LlamaAgenten on 2006-09-28
I have the same problems, with a Gigabyte DS4. I downloaded the 28/9 release, and tried to install, some of it went fine without problems. But when the installation came to the package selection, packet 813, it just couldn't get any further, but the machine didn't crash, it just didn't work. For 30 minutes it didn't get any further. 

Now i don't know what to do, else than wait for at newer, and better release.

---

### Post by pallekuling on 2006-09-28
> **LlamaAgenten said:**
> I have the same problems, with a Gigabyte DS4. I downloaded the 28/9 release, and tried to install, some of it went fine without problems. But when the installation came to the package selection, packet 813, it just couldn't get any further, but the machine didn't crash, it just didn't work. For 30 minutes it didn't get any further. 

Now i don't know what to do, else than wait for at newer, and better release.

This happened under my install of the 27/9 release. I switched to console Alt+Ctrl+F2 (?) and killed the apt process. Then I returned to the install, it reported an error and tried once more - this time sucessfully.

I don't know if this is a safe thing to do, but as far as I know it sure workes for me.

---

### Post by shawncorn on 2006-09-28
I got the system installed with the 9/28 cd, but grub is halting with an error 21.  Is anyone else getting this?  Does anyone know the solution?  I installed ubuntu on a PATA drive with no problems up to that point.

---

### Post by sgifan67 on 2006-09-29
> I got the system installed with the 9/28 cd, but grub is halting with an error 21. Is anyone else getting this? Does anyone know the solution? I installed ubuntu on a PATA drive with no problems up to that point.


I can second that, i'm exactly in the same situation. Since 27/8 the daily builds installs (if we forgot that half of the time i'm also stuck in package installation 813 of 813).

I'm using a PATA Harddrive also.. and the infamous error 21 appear at boot.

I also tried to use LILO. (click on <back> at partitionning stage and choose LILO in the menu) . The result was that it boots, but it seem the install was not correct as the system don't finish correctly the boot arguing missing things in /sbin

I suspect LILO boot is not really supported. but technically it boots...
but maybe it is a solution to try to use LILO.

---

### Post by SFAOK on 2006-09-29
Anyone had any joy with the beta? Despite trying different combinations, the splash screen appears, doesn't do anything then I get a complaint from Busy Box that it can't access tty because job control is turned off.

I have a P5B motherboard with a SATA hard drive and IDE DVD drive. Cheers!

---

### Post by sgifan67 on 2006-09-29
I wrote
> I can second that, i'm exactly in the same situation. Since 27/8 the daily builds installs ...

I meant 27/9, before this date nothing was working at all (no jmicron support in debian installer)

---

### Post by apple2_91 on 2006-09-30
My hardware is:
MB: Gigabyte DS3
CPU: Core 2 Duo E6300
SATA HDD 
IDE DVD
and I experience the same problems. The 09/28 release detects the dvd but doesnt detect the sata harddisc. I haven't tried other sata slots as my case cant be opened so I think older releases should do the work. My idea is to put an installation iso file somewhere on the hdd and when the setup says that cdrom is not found we can mount the hard drive (I suppose) and create the /dev/cdrom file so that it represents the iso file (using mknod maybe) I dont know how exactly to do it but I suppose its possible.
I'm running windows now and I suppose itll be very temporary. Any ideas will be highly appreciated.

---

### Post by sleeperknight on 2006-09-30
Has anyone tryed the 30/9 daily build? :-k [http://cdimage.ubuntu.com/daily/20060930/](http://cdimage.ubuntu.com/daily/20060930/)

---

### Post by sargosis on 2006-09-30
the 9/28 build for the alternate CD worked for me. I have to switch my BIOs to AHCI, but it worked. my system has a DVD-RW in the IDE and 2 SATA HDDs connected internally to channels 1 and 2. I haven't tried the desktop CD, but i know the Alternate one worked for me.

---

### Post by lolikapuxa on 2006-10-01
i tried the 28/9 and it happens the same thing. 
 It installs ok, 
but then it gives error 21 (grub). And now i just can't access my windows partition

---

### Post by lolikapuxa on 2006-10-02
I changed the sata port in my pc from 1 to 3, and now grub detects my partitions. 
But then it says something abou dualfunction and crashes...

---

### Post by sleeperknight on 2006-10-02
has anyone tryed it with the october 2 daily build, has a new kernel in it 2.6.17-10.25, or is the ICH8 [https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63516](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/63516) bug still in it?

---

### Post by StefanSteinheimer on 2006-10-02
The daily build from October 2 is the first that finishes the installation on my machine (Asus P5B), but only on a PATA HDD connected to the JMicron controller. It doesn't see my SATA disk connected via ich8. Now I'm getting the infamous grub error 21 when trying to boot from the PATA disk :( . I'll try to fix that tomorrow. If I can make it boot I'll post an update here.

---

### Post by Zoolonly on 2006-10-04
I bought a SATA DVD drive and installed the dapper !
Works fine !
At least i've got my ubuntu back !! ;-)

---

### Post by lazerradial2003 on 2006-10-05
Any progress here? Is such a shame having this lovely dual core box and then running xp on it :(. How do i make sure i'm downloading the most recent build? (The one people are having most luck with) Thanks.

---

### Post by Cynical on 2006-10-06
Actually I'm installing from the 10/05 desktop daily iso right now. ICH8 is still broken so just make sure your sata device is managed by the jmicron controller and you shouldnt have a problem.

---

### Post by lazerradial2003 on 2006-10-06
thanks for the reply, does this build allow IDE devices on the jmicron controller to be used? Where abouts can i download the daily iso from? Cheers.

---

### Post by wwuster on 2006-10-06
I keep updating edgy with update manager and have seen a new 2.6.17-10-generic kernel every couple of days, but my cdrom drive still doesn't work. Is the fix supposed to be in these kernel updates? If not, when?

thanks,
William

---

### Post by wellmt on 2006-10-06
So I'm supposed to convert my SATA drives to IDE and plug them into the J-Micron controller?

Less than Ideal not having not using the ICH8 controller though isn't it? 

I understood that ICH8 support was in kernel 2.6.18. I *hope* the developers manage to get both the ICH8 **and** J-Micron support into the Ubuntu even if the drivers are backported to kernel 2.6.17). 

How are people with this new hardware supposed to install 6.06LTS? Would an updated ISO be released (like Debian do?)

---

### Post by kzt on 2006-10-06
Well, I have an Asus P5B motherboard, and I run a PATA CD and HD for Linux, and let me tell you how I am happily typing this message in Konqueror right now.  This solution is intended for people who have the GRUB Error 21.  It requires that you have a running copy of Windows on the machine.  I have tested this solution in Windows XP, with my bios set for IDE mode.  This is a quick draft.  I'll expand on it later.

Step 0: Download and Install k/ubuntu from the Daily Builds [Tested kubuntu daily-live 2006/10/05; /boot should be either ext2 or ext3]
Step 1: Download explore2fs [Link]("http://www.chrysocome.net/explore2fs")
Step 2: Download and Install WinGrub [Link]("http://grub4dos.sourceforge.net/")
For the base setup, I used drive C and checked the Copy Stage Files box.  To actually install GRUB, select Tools -> Install Grub.  In that dialog, I had it add an entry to my boot.ini file.
Step 3: With exploree2fs, copy the kernel and initrd from your installation onto your Windows disk.
Step 4: Modify C:\Grub\menu.lst to reflect the contents of /boot/grub/menu.lst
Here's my entry - modify as needed.
```
title	Kubuntu Edgy Eft
root	(hd0,0)
kernel	/Grub/vmlinuz-2.6.17-10-generic root=/dev/hda3 ro quiet splash
initrd	/Grub/initrd.img-2.6.17-10-generic
boot
```
Step 5: Reboot

Remaining Issues: Cannot detect drives connected to ICH8.

Note that WinGrub may incorrectly report which disk is hd0 and hd1.  If you get an error after you reboot, check that first.

Edit 0: I am using the i386 build.  The AMD64/EM64T disc does not appear to be fixed at all.
Edit 1: Added my entry for WinGrub, and clarified WinGrub instructions.

---

### Post by SweVoyager on 2006-10-07
> **wellmt said:**
> So I'm supposed to convert my SATA drives to IDE and plug them into the J-Micron controller?

Your motherboard should have at least one SATA interface connected to the JMicron controller, so no need to convert your HD interface (just move the cable to one slot connected to the JMicron controller). Check in the manual to see which SATA plugs belongs to which controller.

---

### Post by Zillion on 2006-10-07
I have 2 ide drives on the JMicron Ide port on my Asus P5W board. Pisses me off I can't use them at all. I hope a fix comes soon!!

---

### Post by wellmt on 2006-10-07
> **SweVoyager said:**
> Your motherboard should have at least one SATA interface connected to the JMicron controller, so no need to convert your HD interface (just move the cable to one slot connected to the JMicron controller). Check in the manual to see which SATA plugs belongs to which controller.

OK thanks for that I'll take a look. The Foxconn 'manual' is actually just a poster so I'll just have to experiment.

Still hope ICH8 support will get sorted though. I mean this is an Intel Southbridge not some minor chip!

---

### Post by ColDebug on 2006-10-08
I have dapper installed on a ga965-ds3 with everything (sort of) working. Either i cannot use the tv card, or i cannot use the dvd drive, but its definitely workable until a real solution comes available. It's not too hard to do:

network install (instructions earlier in thread and elsewhere on site). I had an old machine with windows installed so it was a quick matter of copying the tftpd package and the netboot tar.gz package for dapper 64, booting form the network and letting it isntall from the repositories.

It works jsut fine with the sata drives connected to the intel chip. after that, download kernel 2.6.18 from kernel.org, remove the link to evms from /etc/init.d, import the config from 2.6.15 and recompile. When you reboot into 2.6.18 everything SHOULD work - for me the only thing that doesnt is my tv card (which is par for the course, since it also doens't work in edgy).

You don't have to switch the hard drives from the ich8 controller, it works fine and will detect a pata drive on the jmicron controller (at least it does for me).

Definitely not a simple install, but it only takes about two hours if you have a fast internet connection.

---

### Post by fortywosquared on 2006-10-08
Well, after following this thread and trying the various suggestions (I'm glad it's working for some; alas I am still in the dark), I started dragging the linux.kernel newsgroups for whatever I could find.  After a few modifications to the search terms, this gem appeared:

[http://groups.google.ca/group/linux.kernel/browse_thread/thread/269177f336ae050a/f1480da005544652?lnk=st&q=linux+2.6.19+duo&rnum=2#f1480da005544652]("http://groups.google.ca/group/linux.kernel/browse_thread/thread/269177f336ae050a/f1480da005544652?lnk=st&q=linux+2.6.19+duo&rnum=2#f1480da005544652")

Promising in deed.  However, it is very (OK, entirely) dependant on a bleeding edge kernel (2.6.19rc1).  All of this brings me to my point.  Is there a way to modify the installer on the Ubunto CD to use this newer kernel?  If anyone has a link on where one could begin such a task, I'd love to take a crack at it.

---

### Post by teletubby on 2006-10-09
I have a ASUS p5b deluxe/wifi..

Installed using a usb-drive with grub and a network-install image. After the install I compiled a new kernel manually ( 2.6.18 ), at first it didn't find any IDE-drives on the pata-controller so I started looking around in the kernel-source and found some references to AHCI and Jmicron. Found the AHCI option (for the JMicron) in BIOS, turned it on... rebooted.. and it worked..

So basically:
* JMicron is working
* ICH8 is working
* One of the gbit NICs is working, the other one not..
* Haven't played around with Wifi yet, but i bet that doesn't work.
* Sound (intel HD) is working, can also be turned into standard AC97 if you got problems..

Here's the kernel images i compiled if anyone wants to use them:
[kernel-image-2.6.18-banan1]("http://www.student.uib.no/~sei081/kernel-image-2.6.18-banan1_10.00.Custom_i386.deb")
[kernel-headers-2.6.18-banan1]("http://www.student.uib.no/~sei081/kernel-headers-2.6.18-banan1_10.00.Custom_i386.deb")
(right-click, save as)

---

### Post by SFAOK on 2006-10-09
The patch to fix ICH8 has been committed but not released yet. Anyone know what causes a fix to move from being commited to being released?

---

### Post by sluzbenik on 2006-10-09
Hi...I'm new to Ubuntu but thought I'd give it a try. With the latest Edgy DVD image I can successfully boot with my DVD-RW attached to the Jmicron controller but Gparted doesn't seem to want to work on a PATA hard drive attached to the Jmicron controller, though it sees them. The first time I tried to let it resize the Windows partition that was there, but it just hung. So I created an EXT3 partition with Acronis but it did the same thing when trying to resize that partition (I didn't know I needed a separate partition for a swap file so again I tried to parition with Gparted during installation.) 

Can I just create a couple more partitions in Acronis and somehow get the Installer to skip the partitioning stage and just mount these partitions and install stuff there? No matter what it seems like it's unavoidable to make new partitions with the installer...

Not sure what to do now...I don't want to install on anything but this particular drive and preferably while keeping my existing NTFS partition.

---

### Post by wilsonywx on 2006-10-09
I just want to know if there are any guarantees of fixing this problem in the Edgy release. I think it is unacceptable for users to scramble the net for alternative installation methods.

---

### Post by SFAOK on 2006-10-09
The JMicron problem is compounded by the fact that Grub can not recognise drives attached to some JMicron controllers. The Live CD can see and even install to my SATA HDD but Grub doesn't even know it's there leaving me with an unbootable system.

Tomorrow's kernel should include ICH8 support and I don't think Grub has any problems with ICH8 so hopefully I should get Ubuntu up an running with tomorrow's daily build. AFAIK, both the JMicron and ICH8 problem should be fixed in tomorrow's daily. If you download it and you still can't get it to work and you're sure it's the distro (i.e. it's not bios settings or anything), you should add comments to the relevant bug pages.

Hope people have some success :)

---

### Post by pooslinger on 2006-10-09
Has anyone tried this to get a live cd to work?  You can do all this from the Ubuntu LiveCD if you save the original .iso to the hard drive.

1. [http://reconstructor.aperantis.com/index.php](http://reconstructor.aperantis.com/index.php)
2. Copy kernel image, headers, etc to:

> yes, you can use custom packages.  (i need to update the manual)  if you
copy all of your custom .deb files to
[WORKING_DIRECTORY]/root/var/cache/apt/archives/

and then launch reconstructor with the -m  switch, it will manually install
all .deb files in the cache when you click "Apply" on customization.  
([http://groups.google.com/group/reconstructor/browse_thread/thread/52667347054e16aa/f13c328a66eb1af2#f13c328a66eb1af2](http://groups.google.com/group/reconstructor/browse_thread/thread/52667347054e16aa/f13c328a66eb1af2#f13c328a66eb1af2))
3. sudo python reconstructor.py -m
4. Click Apply to load new .debs to live image, updates image automatically.
5. Boot new live CD with new kernel?

I'm assuming that it can't be this easy to load a new kernel.  What else would need to be changed?

---

### Post by sluzbenik on 2006-10-09
Ah well, I installed Ubuntu using a IDE Controller card with an extra 40-ribbin cable (lol). That worked. Then I tried to put that drive back on the Jmicron and I got the GRUB error 21. So much for Linux.

Not that I wouldn't run ito ff the old IDE controller card, but I'd have to basically redo all my wiring and if you have an Antec P180 you know how much that is.

Plus once I was in and started looking for drivers for my 1900xt I realized I was waaaaaaaaaaaaay in over my head.

Thanx for the fun...

---

### Post by lazerradial2003 on 2006-10-10
Does anyone have any more information about the problem with GRUB and the Jmicron sata interface, My install went without a hitch but I just get the grub error 21 if i try to boot to it. Does anyone know how to find out which drive is hd1, hd2 etc from the shell? That way i can at least check my grub config file using a rescue CD and make sure it isnt just that the installer is messing up the config file and referencing to the wrong disk. Thanks.

---

### Post by DidYouReadGuyDebord on 2006-10-10
Hi Ubuntuers!
I am a Debianist. I upgraded my kernel to 2.6.18 before changing my motherboard and CPU. I got my jmicron interfaces to totally work on a P5b-VM thanks to someone on [http://lists.debian.org/debian-user/2006/10/thrd2.html](http://lists.debian.org/debian-user/2006/10/thrd2.html)
Here is the exact post:
[http://lists.debian.org/debian-user/2006/10/msg00744.html](http://lists.debian.org/debian-user/2006/10/msg00744.html)

This line was the key to my success and the only parameter I had to change in /grub/menu.lst:
# kopt=root=/dev/hde3 ro
When it was set to hda3 debian could not find the / partition on my master PATA harddisk connected to the jmicron interface.
Then "update-grub" for this modification to spread through /boot/grub/menu.lst

My /etc/fstab:
proc            /proc           proc    defaults        0       0
/dev/hde3       /               ext3    defaults,errors=remount-ro 0       1
/dev/hde1       /boot           ext3    defaults        0       2
/dev/hde6       /home           ext3    defaults        0       2
/dev/hde7       /opt            ext3    defaults        0       2
/dev/hde8       /usr            ext3    defaults        0       2
/dev/hde9       /usr/local      ext3    defaults        0       2
/dev/hde10      /mnt/homebis   	ext3    defaults        0       2
/dev/hde5       /var            ext3    defaults        0       2
/dev/hde2       none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/sda1      /mnt/HOMEhdb1	ext3    defaults        0       2
/dev/hdf1       /mnt/HOMEhdd1	ext3    defaults        0       2
usbfs  /proc/bus/usb   usbfs defaults       0 0

I connected a PATA harddisk to the inner jmicron SATA port thanks to an Abit IDE->SATA adapter, and it was recognized as /dev/sda
My slave PATA drive is recognized as /dev/hdf

Good luck to you!

One last tip: my onboard Intel 965G graphics card is only recognized as a VESA card, and with 131072 kbytes of RAM, and not as an Intel i810 family of cards.

---

### Post by Xerix on 2006-10-11
I was finally able to install Ubuntu using the latest live cd build from today. Installation went without any problems on my P5B motherboard with the hard drive connected to ICH8.

---

### Post by SFAOK on 2006-10-11
Same here, very happy to have Ubuntu back :)

It's been a frustrating month for me but really, it just goes to show how quickly things can change and how good the Ubuntu team are. I have a P5B as well, what with the JMicron problem, ICH8 issue and the network card too really it's pretty good how quickly the issues have been met. Sure, it's been a frustrating few weeks of wait-and-see and trial-and-error but it's paid off in the end!

---

### Post by salbefe on 2006-10-11
Hi,

Could you tell from where exactly did you get these working build.?

Thanks

---

### Post by Xerix on 2006-10-11
I got my build from:
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

---

### Post by sleeperknight on 2006-10-11
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/) need to have the controller in IDE

---

### Post by pooslinger on 2006-10-11
**Working:**
Xubuntu
Asus p5b
1 SATA (ACHI) + 2 PATA (IDE mode)
Grub 22 error if installed to PATA and SATA.
If installed to SATA, edit grub "e" to reflect root at GRUB menu.  

Both SATA and PATA work. 

Image used:
[http://cdimage.ubuntu.com/xubuntu/daily-live/20061011/](http://cdimage.ubuntu.com/xubuntu/daily-live/20061011/)

---

### Post by lazerradial2003 on 2006-10-12
Anybody had any luck using this live CD to install with the hard drive connected to the Jmicron IDE controller?

---

### Post by SweVoyager on 2006-10-12
> **lazerradial2003 said:**
> Anybody had any luck using this live CD to install with the hard drive connected to the Jmicron IDE controller?

I would also like to know of any progress on supporting the JMicron PATA interface. I dont want to mess with my XP installation on my only SATA disk. :)

---

### Post by SFAOK on 2006-10-12
Before the ICH8 patch made it in, I installed with the drive connected to the JMicron controller. The problem was Grub was unable to see the drive so couldn't boot the installation on it.

Connect the drive to the JMicron controller, boot up the latest live CD and see if it detects your drives (i.e. have a look in /dev to see if it's recognised). If not, add to the bug report with any helpful details.

---

### Post by lazerradial2003 on 2006-10-12
Well the latest live CD doesnt work for me, comes up with a list of error messages to do with JMicrsomething (Presumably the jmicron controlleR), not being able to allocate resources to channels 1 - 4 and then hangs, i seem to remember a similar message flashing up with an alternative install CD from a week or so ago but the install then continued.

The install i managed to get to run all the way through using the older alternate install CD ran ok but i now get grub error 21 (i was installing to a PATA drive with a PATA cdrom and a SATA device connected, which has on it an older (no longer active) Ubuntu install. All were connected to the Jmicron ports. 

My next step is to download the latest daily builds alternate install CD and then try installing to the PATA drive, deleting the existing linux install and installing to the SATA drive and installing to the PATA drive with the SATA drive unplugged. 

Will let everyone know what results i get with those combinations but if anyone has any comments on what i've found so far i'd be very grateful.

Thanks.

---

### Post by gslavik on 2006-10-12
thanks

---

### Post by salbefe on 2006-10-13
I have the same problem with the last alternate build from 20061013.

Motherboard: MSI P965 NEO

---

### Post by lazerradial2003 on 2006-10-13
Hmm, looks like yesterdays daily might have been a step backwards, anyone had any luck with yesterdays/ todays?

---

### Post by shawncorn on 2006-10-13
Greetings from my new Asus P5B!  

Today's live cd worked:
[http://cdimage.ubuntu.com/daily-live/20061013/](http://cdimage.ubuntu.com/daily-live/20061013/)

Maybe the other daily works too, but I probably messed up the burn and the whole cd was corrupt and I have to go to campus to burn cds so...

So, I was able to boot into the live cd with no problem.  Then I installed ubuntu with no problem too.  Then I tried to install lilo but got some errors.  This you may be able to do from the live cd, but I did it from some previous daily cd I had.  I moved /target/dev to /target/~dev to back it up because I wasn't sure if this would work, and then I did
mount --bind /dev /target/dev
mount --bind /proc /target/proc
And then the lilo installation worked.  I also put /dev/hda explicitly in /target/etc/fstab because it was complaining about that too.  I rebooted and now I'm posting this from my new machine!  I have lots of configuring to do.  Just wanted to post a success story.  Note that I'm using a PATA drive.

Sat Nam!
Brian

---

### Post by lazerradial2003 on 2006-10-14
hey shawncorn, looks like you may have found a solution, could you give any more details of exactly what u did, because i had similar problems installing Grub or lilo after a successful install. thanks.

---

### Post by apple2_91 on 2006-10-14
Todays daily-live 10/14 works fine for me. Sata hdd and dvd-rw are detected and there are no problems with grub as well I havent changed anything in the bios.
I really feel a lot better when working under ubuntu and I think it was worth waiting (and wasteing cds).
Cheers.

---

### Post by DeeZiD on 2006-10-14
Yes, the livecd from today at least starts on my pc with irqpoll option. :)

But the whole systems hangs when installing at 31% everytime, no matter what other boot options I use: noapic acpi=off irqpoll (without it just takes forever to boot). It hangs even if my PC isn't overclocked. I even set the bios options to default but it hangs at 31% :???: 

PC:
P5W DH Deluxe with Jmicron JMB376
Core2Duo e6300@2.8GHz
2GB Buffalo DDR2 (800MHz, DualChannel) 
Geforce7900GTO, 512MB

I tested VESA Mode, too, but nothing :(

](*,) ](*,) ](*,) ](*,) 


I want my Ubuntu back. :twisted: 


regards Dennis

---

### Post by wilsonywx on 2006-10-14
When I tried yesterday's image I get this error:
Target file system doesn't have /sbin/init

I will try today (10/14)'s image again. If that happenes I think I will not bother till edgy is released.

---

### Post by wilsonywx on 2006-10-14
> **apple2_91 said:**
> Todays daily-live 10/14 works fine for me. Sata hdd and dvd-rw are detected and there are no problems with grub as well I havent changed anything in the bios.
I really feel a lot better when working under ubuntu and I think it was worth waiting (and wasteing cds).
Cheers.

lol I use a cd-rw disk everytime I dl a new image.

---

### Post by shawncorn on 2006-10-14
> **lazerradial2003 said:**
> hey shawncorn, looks like you may have found a solution, could you give any more details of exactly what u did, because i had similar problems installing Grub or lilo after a successful install. thanks.

Well, I wasn't writing it down, but from memory:

I have ubuntu installed on my pata drive, which is /dev/hda.
I did not modify the partition table, though if I knew this was going to work, I probably would have. =P  So I have /dev/hda1 as the root partition and /dev/hda5 as the swap space, as ubuntu's partitioner sets by default.
After I installed everything with the livecd I chrooted into the new system, which the livecd mounts under /target.  First, you need to get your network connection working in the new environment because lilo wasn't on my livecd.  So, to do that, I did:
```
mount --bind /proc /target/proc
```
Also, when trying to run /sbin/lilo, it complains about /dev/hda.  I don't know why, exactly, but it seems like /target/dev/hda was actually missing.  So I made a backup of /target/dev and then binded the ramfs one to it:
```
mv /target/dev /target/~dev
```
```
mkdir /target/dev
```
```
mount --bind /dev /target/dev
```
Finally, to resolve domain names, you have to make /etc/resolv.conf:
```
echo "nameserver www.xxx.yyy.zzz" > /target/etc/resolv.conf
```
Note that I have a static ip address. If you're using DHCP, you might have to find this information elsewhere (/etc/resolv.conf exists?)
That's all I had to do, I think, to get everything working.

Oh, except for fstab.  If /target/etc/fstab doesn't exist, copy the other one over, otherwise, edit it.  For me, I had:
```
# /dev/hda1
UUID=da8a33e9-6a11-4864-992c-edf1595cf0a7 /               ext3    defaults,errors=remount-ro 0       1
```
So I commented out the UUID line and wrote a like like this:
```
/dev/hda1   /  ext3   defaults,errors=remount-ro  0  1
```
Note that when you reboot into the new system, it will put this back to the way it was automatically.

Now to install lilo:
```
cd /target; chroot /target; su -
```
```
apt-get update
```
```
apt-get install lilo
```
The installer will tell you what to do next.  Run liloconfig, take a look at /etc/lilo.conf and make sure it's sane and then run /sbin/lilo.  Then logout of the chroot, ^D^D, unmount the filesystems and reboot:
```
umount /target/proc
```
```
umount /target/dev
```
```
reboot
```
And boot from the hard drive.  The lilo prompt will come up and everything should be fine.  If this wasn't complete, post back here and I'll try and remember what I forgot ;)

Good luck,
Brian

---

### Post by bhamail on 2006-10-14
FYI, I had this problem and using a USB attached CDROM drive allows Dapper Live CD to boot. Now I'm off to see if the puppy will install.

Dan

---

### Post by morphix on 2006-10-15
i hate to be annoying but, i have an Asus P5W DH Deluxe motherboard, which has the JMicron ide/sata controller on it.

They do not work in Dapper last time i tried. Has the problem been fixed at all??

---

### Post by sandlidl on 2006-10-15
Hello, Sorry I haven't read the entire thread to know if anyone has said something about it...

I have an ASUS P5B Deluxe and if I set the SATA to ahci, then it will install. I tried patching the kernel (didn't work) tried compiling the new kernel (didn't work), so I'm stuck with it as ahci. It installs, everything works, so I'm happy with it.

Maybe this helps, maybe not. Maybe someone can tell my why it will work as ahci and not ide.

Thanks

---

### Post by ColDebug on 2006-10-15
Just reconfigured my modules config and compiled a new kernel using the fresh 2.6.18.1 kernel image at kernel.org and so far it seems everything works just great. Didn't patch it for evms so that's still off, but other than that it's doing quite well.

BTW, there was a huge increase in snappiness and bootup speed between 2.6.18 and 2.6.18.1

---

### Post by lazerradial2003 on 2006-10-16
Was just wondering if anyone has made GRUB work with a PATA drive, whatever i do i end up with the Error 21.

If not then has anyone made LILO work and if so does anyone have any instructions they cold share about how to sort out installing LILO (ideally without network access since network access seems to be somewhat problematic with these boards) 

Also all the live CD's i have used (12th and 13th i think) give me this error message when i choose 'start or isntall ubuntu":

PCI: JMB36x: Enabling Dual Function
PCI: Cannot Allocate resource regision 0 of device
PCI: Cannot Allocate resource regision 1 of device
PCI: Cannot Allocate resource regision 2 of device
PCI: Cannot Allocate resource regision 3 of device

And if i plug the PATA hard drive into one of the intel SATA ports (which gets around GRUB error 21) using a converter i get the same error message when the instalation i did using a slightly older alternative daily build install CD when this instalation tries to boot. I have a TV card and Soudblaster Audigy installed and am using a PATA DVD RW drive.

One tip for anyone using converters to plug PATA drives itno the SATA ports, remember to remove any jumpers from the drive, if you don't then the drive takes ages to detect and if it does detect is unusabley slow. (with my adaptor anyway)

Finally i've seen several references to 'setting the SATA to ahci', can anyone expand on this, what it does and how to do it? 

Any comments on this appreciated.

lazerradial

---

### Post by morphix on 2006-10-16
> **ColDebug said:**
> Just reconfigured my modules config and compiled a new kernel using the fresh 2.6.18.1 kernel image at kernel.org and so far it seems everything works just great. Didn't patch it for evms so that's still off, but other than that it's doing quite well.

BTW, there was a huge increase in snappiness and bootup speed between 2.6.18 and 2.6.18.1

I downloaded the 2.6.18.1 source and used menuconfig and then compiled it.. but modules fail to compile. And then trying to boot up fails using that kernel :(

I have never compiled a kernel before.. what steps did you take to compile it?

---

### Post by pooslinger on 2006-10-16
> **morphix said:**
> I downloaded the 2.6.18.1 source and used menuconfig and then compiled it.. but modules fail to compile. And then trying to boot up fails using that kernel :(

I have never compiled a kernel before.. what steps did you take to compile it?

[http://doc.gwos.org/index.php/2.6.14_Vanilla](http://doc.gwos.org/index.php/2.6.14_Vanilla)

---

### Post by nuggien on 2006-10-16
2.6.18.1 from kernel.org solved all my problems :)

---

### Post by morphix on 2006-10-17
well this is odd.. i just installed the 16th Oct daily Edgy beta release.. i cant boot up if i have any ide devices connected to the intel ide controller :/ but the system works fine without it.

except i now have no cd/dvd drive and 1 hdd disconnected.

---

### Post by Andcor on 2006-10-17
Hi Laz
You say that the live-cd's from the 12th and 13th gave you an error message and stopped booting. Have you in any way found out how to get rid of this problem and have you had any luck with the later cd's? eventually the alternate ?
I've written to Ben Collins who answered me:

Try booting the alternate CD and see if just that works. Also, give the
liveCD more time. It's very slow to boot in some cases.

---

### Post by morphix on 2006-10-17
I tried compiling the 2.6.18.1 kernel, pretty much default except for a few things but when booting up.. it starts loading then goes to a black screen (even after removing quiet & splash from kernel parameters) and hangs there.. the last text i see (which flashes really fast) is something about 'net'.

---

### Post by morphix on 2006-10-17
> **ColDebug said:**
> Just reconfigured my modules config and compiled a new kernel using the fresh 2.6.18.1 kernel image at kernel.org and so far it seems everything works just great. Didn't patch it for evms so that's still off, but other than that it's doing quite well.

BTW, there was a huge increase in snappiness and bootup speed between 2.6.18 and 2.6.18.1

i compiled 2.6.18.1 kernel, when booting i either get: 
hdb/hda(my dvdrw drive) request sense failure
or it locks up detecting drives.

does pretty much the same if i enter irqpoll kernel parameter

if i go into my bios and set it to sata+pata mode, and use kernel parameter it gets past the above errors and gets to:
ipv6 over ipv4 tunneling device and locks up

if i disable my NIC it gets to evms and locks up.

i am beginning to give up.

---

### Post by wwuster on 2006-10-18
Does anyone know when the fix will be in a regularly updated kernel image in edgy? I still can't see my ide dvd drive.

William

---

### Post by ColDebug on 2006-10-18
morphix, because these drivers are new toi the kernel, they are not yet configured. Following the instructions on that kernel page linked above, when you are running kconfig, make sure to enable the jmicron (NEW) support. If you don't select this module you don't get it.

Also, you should use synaptic to remove evms. It's very unlilkely you need it, ubuntu isnt really setup to take advantage of it ootb, and it will cause problems with a new unpatched kernel.

---

### Post by DeeZiD on 2006-10-18
@Morphix, Coldebug: I have the same problem. I'll try to uninstall evms temporarly from livecd (if that's possible) and then install ubuntu. Hope the livecd doesn't freeze then. It always freezes when I try to install ubuntu at 20% until 40%. I don't know why.

[https://launchpad.net/distros/ubuntu/+bug/64474](https://launchpad.net/distros/ubuntu/+bug/64474)

regards Dennis

---

### Post by morphix on 2006-10-18
> **ColDebug said:**
> morphix, because these drivers are new toi the kernel, they are not yet configured. Following the instructions on that kernel page linked above, when you are running kconfig, make sure to enable the jmicron (NEW) support. If you don't select this module you don't get it.

Also, you should use synaptic to remove evms. It's very unlilkely you need it, ubuntu isnt really setup to take advantage of it ootb, and it will cause problems with a new unpatched kernel.

i cant find anything about jmicron support :( where abouts is it??

---

### Post by pooslinger on 2006-10-18
[http://rapidshare.de/files/37270231/linux-image-2.6.18.1_archck7_i386.deb.html](http://rapidshare.de/files/37270231/linux-image-2.6.18.1_archck7_i386.deb.html)

everything default.  Works with SATA ACHI + PATA DVDRW
i686 SMP high mem, asus p5b

---

### Post by morphix on 2006-10-18
I managed to compile my own 2.6.18.1 kernel, everything works absolutely fine, might recompile it later to add some other hardware support and such.

Just a quick question, when adding the version info and revision, modules install to /lib/modules/2.6.18.1customversion, but when installing the kernel-image via the made .deb package, it looks for /lib/modules/2.6.18.1 instead of 2.6.18.1customversion and also the kernel image installs as /boot/vmlinuz-2.6.18.1 instead of /boot/vmlinuz-2.6.18.1customversion .. how do i specify these options.

[edit]

I went googling for make-kpkg and come across "--append-to-version=", so now my question isnt needed.

---

### Post by Andcor on 2006-10-19
You all talks about compiling your own kernel, but how did you get either the desktop or alternate daily cd to boot. 
No matter how I config my bios I can't get the computer to boot because of the latest problems in [https://launchpad.net/bugs/57502](https://launchpad.net/bugs/57502). Anyone got rid of this problem ?

Andreas

---

### Post by morphix on 2006-10-19
> **Andcor said:**
> You all talks about compiling your own kernel, but how did you get either the desktop or alternate daily cd to boot. 
No matter how I config my bios I can't get the computer to boot because of the latest problems in [https://launchpad.net/bugs/57502](https://launchpad.net/bugs/57502). Anyone got rid of this problem ?

Andreas

Well i have a 975 chipset board, so i can still use the intel ide's for my dvd/cd drive, i am just unable to get the jmicron controller to work initially.

I am assuming you have a 965 chipset board? which the only ide it has is the jmicron ide.

Apparently if you download the current beta of edgy and use "all-generic-ide" kernel parameter when booting the cd it will work with the 965 chipset boards.

What motherboard do you have exactly?

---

### Post by DeeZiD on 2006-10-19
@Morphix:
A few questions ;):


Does the live- or alternatecd work without using the irqpoll parameter? 

Which bios options do you use?

How are your hdd (for ubuntu) and your cd/dvd-drive connected (controller and type please)?

Do you use any other boot options?


I have nearly the same hardware config.

The problem is, that the ubuntu cds don't boot without irqpoll for me and with it the whole livecd freezes (but only when installing at 20 to 32%). The alternate cd doesn't work either. It stops installing after calculation 500 to 600 dependencies.

Very strange. :-k 

regards Dennis

---

### Post by morphix on 2006-10-19
> **DeeZiD said:**
> @Morphix:
A few questions ;):

Does the live- or alternatecd work without using the irqpoll parameter? 

i have to use irqpoll for everything yes.

> Which bios options do you use?

In terms of what? For sata/pata my in onboard devices mode its set Standard IDE > SATA (even though i use SATA+PATA, SATA mode seems to be the most compatible mode with linux) the Jmicron controller options are just set to basic ide.

> How are your hdd (for ubuntu) and your cd/dvd-drive connected (controller and type please)?

my hdd for ubuntu is SATA connected to the Intel ICH7 sata controller, dvdrw drive is connected to the Intel ICH7 ide controller. I have my other IDE hdds connected to the JMicron controller

> Do you use any other boot options?

For some unknown reason i sometimes have to also use acpi=no otherwise ubuntu locks up detecting ACPI CPU index.

> I have nearly the same hardware config.

Which is what exactly??

> The problem is, that the ubuntu cds don't boot without irqpoll for me and with it the whole livecd freezes (but only when installing at 20 to 32%). The alternate cd doesn't work either. It stops installing after calculation 500 to 600 dependencies.

Yeah mine wont boot without irqpoll either (i had same thing with my old P4 motherboard aswell). The Ubuntu Dapper live cd works, and so does the Ubuntu Dapper alternate cd, the Edgy disks DO NOT work AT ALL for me.

------

To get mine working, i installed dapper and then compiled 2.6.18.1 kernel, works MUCH faster and everything is supported (well pretty much apart from a little mishap i did in kernel configurations for sound, but it was 3am when i did it. so yeh).

---

### Post by DeeZiD on 2006-10-19
Thx for the reply.

1. I'll try the newest alternate iso this evening when I come home from work.


> my hdd for ubuntu is SATA connected to the Intel ICH7 sata controller, dvdrw drive is connected to the Intel ICH7 ide controller. I have my other IDE hdds connected to the JMicron controller
My p-ata hdd (for ubuntu) is connected to the jmicron controller and completely recognized. It starts installing until 20 to 30% and then freezes :(

> For some unknown reason i sometimes have to also use acpi=no otherwise ubuntu locks up detecting ACPI CPU index.
Strange. Ubuntu Livecd only hangs when I try to install from the livecd. But I'll try that option, thanks.

> Which is what exactly??
Core2Duo e6300 @ 2800MHz
ASUS P5W DH Deluxe
2GB DDR2 PC6400 Dualchannel
MSI Geforce 7900GTO
1 Pata HDD (where I want to install ubuntu)
1 DVD atapi drive

(Even if it's not overclocked the livecd hangs when I try to install always around 25%.
And it doesn't have anything to do with vesa, nvidia or nv driver.)

> Yeah mine wont boot without irqpoll either (i had same thing with my old P4 motherboard aswell). The Ubuntu Dapper live cd works, and so does the Ubuntu Dapper alternate cd, the Edgy disks DO NOT work AT ALL for me.


As I said before, I'll try the edgy alternate cd. 

:)


regards Dennis

---

### Post by shiver on 2006-10-19
I just installed kubuntu-daily and accidentally noticed something that might help those people who get a grub error when trying to boot the installed system. I happened to have several Linux installations on my HDDs so my grub menu filled up and didn't even show Edgy. So I edited an existing entry, changed the partition and kernel names to match etc. It booted nicely and I took a look at the grub menu.lst.

The interesting part is that the default entry, had I booted using it, would have had an incorrect partition setting:

```

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd2,5)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/sda6 ro quiet splash irqpoll
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

```

It should definitely say root (hd0,5) since the root partition is /dev/sda6 and not /dev/sdc6 Maybe grub-install is adding up my IDE HDDs connected to the JMB controller and makes everything go haywire. I have a feeling this might be the cause of those grub 21 errors people are having, even though I'm not familiar with grub's arbitrary error codes.

---

### Post by uMax on 2006-10-20
Hi,

I have followed this thread for a while and just waited for RC1 to appear to try it out on my new and shiny Core2Duo system with the ICH8 and JMicron controller.
Unfortunately, the desktop version did not seem to find any disk (stopped with the error "Can't Access tty, Job control turned off").
The alternate install CD showed me at least a text menu, but then failed to find the PATA CDROM. :( 
Can anyone confirm that the issue has NOT been solved in the RC1 (and probably will not in the final version) or am I missing something?

Thanks,

Marcus

---

### Post by shiver on 2006-10-20
F this, I thought I finally got it working, but when I started copying my data from the ide drives on the JMB to the new sata disk on ICH7, the system hard locked. Twice. And there's nothing in the logs. :mad:

---

### Post by wilsonywx on 2006-10-20
> **uMax said:**
> Hi,

I have followed this thread for a while and just waited for RC1 to appear to try it out on my new and shiny Core2Duo system with the ICH8 and JMicron controller.
Unfortunately, the desktop version did not seem to find any disk (stopped with the error "Can't Access tty, Job control turned off").
The alternate install CD showed me at least a text menu, but then failed to find the PATA CDROM. :( 
Can anyone confirm that the issue has NOT been solved in the RC1 (and probably will not in the final version) or am I missing something?

Thanks,

Marcus

I have a DP965LT motherboard and when I tried the latest (Oct 17) livecd I also had "can't access tty, job control turned off" problem. I don't know what exactly happened there. I find the startup graphics very annoying, as it prevents me from accessing the text console until that error occurs. 

I am sure there is some bug in the cd that makes this not work. I thought that they should have test it on a mobo made by Intel, not a mobo based on the Intel chipset.

---

### Post by wwuster on 2006-10-21
> **uMax said:**
> Hi,

I have followed this thread for a while and just waited for RC1 to appear to try it out on my new and shiny Core2Duo system with the ICH8 and JMicron controller.
Unfortunately, the desktop version did not seem to find any disk (stopped with the error "Can't Access tty, Job control turned off").
The alternate install CD showed me at least a text menu, but then failed to find the PATA CDROM. :( 
Can anyone confirm that the issue has NOT been solved in the RC1 (and probably will not in the final version) or am I missing something?

Thanks,

Marcus

I've been trying to find this out also. I have a similar system and all of the updates but edgy still doesn't see the cdrom. I've read that this has been fixed but would like to know if the fix will be in edgy.

William

---

### Post by rocktorrentz on 2006-10-23
This thread and [this bug page](https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/57502) have got me really confused. Will the latest edgy cds now work on my Asus P5B or not?

---

### Post by lazerradial2003 on 2006-10-23
Don't know if this helps anyone, but I disabled ahci (or something similar, might have been acpi but can't remember what it was exactly but look through the BIOS and see what you can find. This solved all my problems and i now have a working system however i think i read somewhere that this stops both cores from being detected and i can't find anything to say its detected mine to be a dual core but i figure this is a good enough fix until there is some stable support for these systems. Once i'd done this i was able to install with my PATA CD ROM using my PATA DVD RW and LILO as my boot manager.

Also a tip for anyone using PATA drive -> SATA interface converters, sometimes you have to remove all jumpers from the drives or detection is hugely slow and there are constant timeouts and so-on.

lazerradial

---

### Post by Old Fart on 2006-10-23
>>This thread and this bug page have got me really confused. Will the latest edgy cds now work on my Asus P5B or not?


I am running the daily buid of Oct 15 on my P5B and I haven't had any issues :p   I've also booted into the RC live cd and expect the final release to work just as well \\:D/

---

### Post by a8ne on 2006-10-23
RC1 server installs on Jmicron controller but with grub error 21 on boot.  Can be resolved by switching to an ICH8 controller.

---

### Post by morphix on 2006-10-23
Anyone here had any success on one of the gigabyte 965 boards? friend has one and has no luck with ubuntu as of yet.

---

### Post by grv575 on 2006-10-23
Asus P5B works with the oct 17th desktop release.  You must disable legacy usb support in the bios to get the install to complete (there is some ahci bios posting suboption under it which might be the problem).

I'm using a sata hd on the jmicron controller configured as ahci, pata dvdrw on the ide, and the livecd works fine.  After installation you will get a grub 21 error.  Just boot from the livecd and then:

(mknod /dev/sda b 8 0; mknod /dev/sda1 b 8 1; mknod /dev/sda2 b 8 2 if /dev/sda* doesn't exist)
mount /dev/sda2 /mnt (assuming sda2 is your root partition)
chroot /mnt /bin/bash
cd /; mount -t proc proc /proc
apt-get install lilo
edit /etc/lilo.conf
/sbin/lilo

Lilo works fine with the hd on the jmicron controller.

---

### Post by the kaz on 2006-10-24
Afgter quite some struggles with getting Ubuntu onto my system, I can confirm that both the JMicron and the ICH8 seems to be supported correctly in at least the DVD versions of Ubuntu Edgy released Oct 17th or later. I have a Foxconn P9657AA mainboard, a Core2Duo E6600, 2 gigs of RAM, a NEC PATA DVD-Writer (connected to the JMicron) and a Samsung SATA hard drive, and the installation runs smoothly. At boot time, there are a few error messages concerning the Jmicron chip, but the system continues to boot after a few seconds. Apart from the Marvell Gigabit Ethernet controller, which is an unknown device for the kernel, everything seems to run fine.

**BUT** - the installed system itself doesn't run smoothly at all, but completely freezes (screen frozen, keyboard and mouse not working anymore) at random moments when under load. This happens regardless of the kernel used (i've tried the original kernel sources from Ubuntu as well as several vanilla and/or patched ones from kernel.org up to 2.6.19-rc2-mm2), but only in standard mode (and never in single-user mode). The hardware itself has proven to run stable under load with both Windows XP and Vista, so I can rule out any hardware problem. 

Can anyone confirm this? The logs don't show anything shortly before or during the freeze, so I don't know what I can do about it. :???: 

Any help appreciated, kaz.

---

### Post by jornahow on 2006-10-24
I have been strugling to install ubuntu on my MSI P965 Neo with E6400 (windows XP on a sata harddrive, an ide dvd and ide hard drive with ububntu installed).

The current Edgy install disk worked for me, proceeding through the full install to the ide harddrive until I rebooted. On reboot I got a Grub loading Error 21 and the system hanged.  I found the following note in the wiki on Core 2 Duo support:

"Note #2: GRUB does not appear to support (all versions of the) JMicron controller, resulting in "Error 21". The workaround is to install LILO during the installation process. Before rebooting, go "Back" and from the menu choose "Install the LILO Bootloader". You may need to manually create a lilo.conf referencing /dev/sda as your boot drive. Another option is to use a Windows/FreeDOS bootloader to boot into a small DOS partition on the drive, containing the linld.com ( [http://195.66.192.168/linux/linld/](http://195.66.192.168/linux/linld/)) Linux booter for DOS (loadlin, on the other hand, chokes on Ubuntu's large initrd, so cannot be used), copy the kernel and initrd to it and boot from there."

I thought this was the solution, but I could not find any way to go back to install LILO or to install LILO at the beginning of the install process.  This is not an available option on the current edgy cd.  My neophyte efforts to install LILO directly failed miserably - using the package installer with LILO package on floppy the package installer running on the live disk just freezes. Help would be appeciated.

---

### Post by lolikapuxa on 2006-10-24
Yeah, thats a bug related with grub and Jmicron. Plug your hard drive to the ich8 channel, & voilá :D.
 I have the same hardware, and ubuntu running.

---

### Post by junglistmaster on 2006-10-24
i have the intel 965 chipset and a pata cd rom drive with a sata hard drive and the latest build from saturday did not work. still the job access failure.
i hear whispers that they will finally cure this bug in the new kernel 2.6.18
but i am not sure if this will even be by the final release tomorrow??

---

### Post by junglistmaster on 2006-10-24
ps lolikapuxa, how do i plug my sata drive into the ich8 channel? excuse my stupidity as i'm new to ubuntu and new hardware.

---

### Post by wilsonywx on 2006-10-24
Is Edgy going to use the 2.6.18 kernel? I read about support for the 965 chipset in that kernel, but am not sure whether edgy is going to incorporate it. As of now only Mandriva and Fedora Core installs worked for me (but they also can't detect my cdroms after install). I am trying out fedora core 6 (just released today) to see if something good happens.

---

### Post by jornahow on 2006-10-25
Lolipuxa said:

"Yeah, thats a bug related with grub and Jmicron. Plug your hard drive to the ich8 channel, & voilá .
I have the same hardware, and ubuntu running."

My harddrive with ubuntu installed is a pata (IDE) drive.  there is only one IDE conncector - ich8 is sata.  I need to find out how to put LILO on my IDE in place of GRUB. Anybody?

---

### Post by robenroute on 2006-10-25
If this is a GRUB bug (hmmm, I thought all grubs were bugs ;)), we shouldn't be too optimistic to see this fixed any time soon. I just had a look over at [this page]("http://savannah.gnu.org/bugs/?func=detailitem&item_id=17882#options") and it doesn't seem to have seeped through yet. As a matter of fact, it seems that the activity around the GRUB project is a tad on the low side (check [here]("http://savannah.gnu.org/bugs/?group=grub")). Could it be that people over there are focussing on GRUB2?

---

### Post by junglistmaster on 2006-10-25
any joy with fedora core 6? i am beginning to think there maybe months before  
support for our hardware with ubuntu...

---

### Post by robenroute on 2006-10-25
As a general comment, I would like to say that the majority of people posting their struggles in this thread could help solving the situation by being a bit clearer about their set-up: instead of writing that your DVD is connected to the IDE and the HD to the SATA connectors, make it very explicit as to what is connected where and how:

DVD connected to JMicron via IDE (JMicron on IDE in BIOS)
HD connected to ICH8 via SATA or HD connected to JMicron via SATA (JMicron on AHCI in BIOS)

...or something along similar lines. It's often not clear how things are connected and what the BIOS settings are.

Thanks for bearing with me.

Rob

---

### Post by robenroute on 2006-10-25
> **junglistmaster said:**
> any joy with fedora core 6? i am beginning to think there maybe months before  
support for our hardware with ubuntu...

Junglistmaster, if, as I wrote in my previous posting, the problem lies with GRUB and Fedora Core 6 also uses GRUB, you might still be looking at the same issue. From what I've read on the Fedora Forums, the Core 6 kernel should, however, be able to recognize your ICH8(R) and JMicron controllers.

Unfortunately, I can't try this because I simply don't have the hardware in question. The reason I'm interested is purely because I'm looking at buying new hardware and I've got my mind set on a Core 2 Duo processor and a Gigabyte GA965 motherboard (currently still running, quite happily, Dapper on an old laptop).

Give FC6 a try and let us know, please.


Rob

---

### Post by the kaz on 2006-10-25
> **jornahow said:**
> 
My harddrive with ubuntu installed is a pata (IDE) drive.  there is only one IDE conncector - ich8 is sata.  I need to find out how to put LILO on my IDE in place of GRUB. Anybody?

Have you tried grv575's approach from post #179 in this topic?

[QUOTE=grv575]
I'm using a sata hd on the jmicron controller configured as ahci, pata dvdrw on the ide, and the livecd works fine. After installation you will get a grub 21 error. Just boot from the livecd and then:

(mknod /dev/sda b 8 0; mknod /dev/sda1 b 8 1; mknod /dev/sda2 b 8 2 if /dev/sda* doesn't exist)
mount /dev/sda2 /mnt (assuming sda2 is your root partition)
chroot /mnt /bin/bash
cd /; mount -t proc proc /proc
apt-get install lilo
edit /etc/lilo.conf
/sbin/lilo
[/QUOTE]

My system still freezes erratically, by the way - has anyone experienced anything like it with P965 boards?

Greetings, kaz.

---

### Post by robenroute on 2006-10-25
Could it be that the following bugs ([8497]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/8497") and [66667]("https://launchpad.net/distros/ubuntu/+source/grub/+bug/66667")) are related (and if so, would it be presumptuous to start advising to shy away from GRUB in favour of LILO - because it involves tinkering with the GRUB configuration files)?

Just my very humble opinion....

---

### Post by jornahow on 2006-10-25
> **the kaz said:**
> Have you tried grv575's approach from post #179 in this topic?



My system still freezes erratically, by the way - has anyone experienced anything like it with P965 boards?

Greetings, kaz.

I have copied grv575's post, but have not tried it yet.  I messed with linux years ago, but have forgotten what little I learned.  Do I enter his instructions in a console (terminal?) and if so must I be logged in in any special fashion?  Also if i don't have lilo on my machine what becomes of the instruction "apt-get install lilo"?

jornahow

---

### Post by wilsonywx on 2006-10-25
well lets wait until edgy is released and test it. hopefully it will actually work for a dp965lt board. if not...screw it then. I'll use other distros (looking forward for debian 4.0 in Dec)

---

### Post by jornahow on 2006-10-26
Well I managed to install lilo and attempted to follow the instructions to run liloconfig and then execute /sbin/lilo.  I received the following message when I ran liloconfig.  I have posted it because it might shed some light on the 965 problems to someone more knowledgeable than me.  My IDE drive and volumes show up in device manager, but I saw nothing like "unionfs".  partition editor shows me as having /dev/hda1 ext3 Boot, /dev/hda2 extended and /dev/hda5 linux swap. I have not used raid.

JornaHow
 
 Liloconfig message:
  
   " WARNING!
        Your /etc/fstab configuration file gives device unionfs as the root
        filesystem device. This doesn't look to me like an "ordinary" block
device. Either your fstab is broken and you should fix it, or you are
using hardware (such as a RAID array) which this simple configuration
program does not handle. 

You should either repair the situation or hand-roll your own
/etc/lilo.conf configuration file; you can then run /usr/sbin/liloconfig
again to retry the configuration process.
Documentation for LILO can be found in /usr/share/doc/lilo/."

---

### Post by Cynical on 2006-10-26
I installed dapper using instlux and upgraded to edgy recently. The problem is solved, I can use my ide cdrom drive just fine. The issue is that the daily iso hasn't been updated yet. Tomorrow when the release hits the servers you guys will be set.

---

### Post by robenroute on 2006-10-26
> **Cynical said:**
> I installed dapper using instlux and upgraded to edgy recently. The problem is solved, I can use my ide cdrom drive just fine. The issue is that the daily iso hasn't been updated yet. Tomorrow when the release hits the servers you guys will be set.

We'll see... (or am I Cynical now? ;))

---

### Post by junglistmaster on 2006-10-26
new version is here.
[http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download](http://www.ubuntu.com/products/GetUbuntu/download?action=show&redirect=download)
i hope it is updated for our 965 chips or i may cry like a baby.

---

### Post by Lupe0 on 2006-10-26
Ahh... I just installed Edgy Server. Finally JMicron PATA controller works. :) 

Ethernet controller still isn't working, but I bought 3COM ethernet card so that's not a problem for me anymore.

Motherboard: Asus P5B

---

### Post by robenroute on 2006-10-26
> **Lupe0 said:**
> Ahh... I just installed Edgy Server. Finally JMicron PATA controller works. :) 

Ethernet controller still isn't working, but I bought 3COM ethernet card so that's not a problem for me anymore.

Motherboard: Asus P5B

Lupe0, let me start by saying I'm happy for your successful installation. Just for clarity sake, could you specify how and what, please? This would be of great help to all of us (see my post ([#189]("http://ubuntuforums.org/showpost.php?p=1660311&postcount=189")) earlier in this thread). Thanks a lot in advance.

Rob

---

### Post by v8YKxgHe on 2006-10-26
Well I still get no luck, I've just installed it again and see if it will boot, last time it just got stuck as soon as usplash loaded. *sighs*

---

### Post by robenroute on 2006-10-26
> **AlexC_ said:**
> Well I still get no luck, I've just installed it again and see if it will boot, last time it just got stuck as soon as usplash loaded. *sighs*

Might be more informative and eventually helpful if you could specify your hardware configuration, AlexC....

---

### Post by v8YKxgHe on 2006-10-26
Sorry, I posted them in another topic and forgot to post them here:

Intel Core 2 Duo E6600
Abit AB9
1GB ( 2x512mb ) GeIL PC3500
1xIDE 80GB Maxtor hard drive used as a Storage Drive so I can easily transfer files between Win/Lin
2X SATA 2 Western Digital 120GB ( 1 for WinXP and one ... hopefully for Ubuntu Edgy )
1X IDE DVD RW
ATI X800XT

I can get Edgy to install, but once installation has finished it wont restart - there is still a little bit left of the progress bar and it hangs there so I have to do a hard restart.

Once I take the CD out and try to boot into my new Edgy I get to the GRUB screen a see a few errors but they go past to quick to see them. After than I am shown the usplash but it just hangs there, no hard drive activity at all.

---

### Post by aurimas on 2006-10-26
I have a long story with Core 2 duo. My original comp "was" E6300 with MSI p965 neo motherboard. CD/DVD is connected to JMicron IDE. And hard drive was connected to SATA 2 port through JMicron controller (BIOS option was IDE and my BIOS has not AHCI option at all). Now I'm writing from Ubuntu :). Hm, but problems persist. 
I did not manage to install nor FC5, nor FC6 (I installed both but they do not boot (grub I guess).
Edgy I installes from live CD. Installation went fine, but... after rebooting I get "stage 1.5, grub error 21" - known thing to this forum :).
Solution was _after_ installation (maybe before works too) to plug hard drive connector to sata port without JMicron. My mobo has only one JMicron controlled sata port. After this I guess I do not have CD/DVD access. But it is a small problem compared to using windows.
That's all :).

---

### Post by Lupe0 on 2006-10-26
> **robenroute said:**
> Lupe0, let me start by saying I'm happy for your successful installation. Just for clarity sake, could you specify how and what, please? This would be of great help to all of us (see my post ([#189]("http://ubuntuforums.org/showpost.php?p=1660311&postcount=189")) earlier in this thread). Thanks a lot in advance.

Rob

DVD connected to JMicron via IDE (JMicron on IDE in BIOS)

HD connected to ICH8 via SATA

Asus P5B
Intel C2D E6400
Corsair 2x1gb
SATA1 (ICH8 ) Samsung 250GB
SATA2 (ICH8 ) Seagate 320GB
LG DVD+-RW JMicron IDE

Let me know if you want some more info. :)

E: As we see, I'm a beginner with Ubuntu. :D
Now the Ethernet card works too after adding these line to
/etc/network/interfaces

```
auto eth0
iface eth0 inet dhcp
```

---

### Post by jornahow on 2006-10-26
The 6.10 amd64 distro still will not boot on my:

MSI P965 Neo - 6400 core 2 duo
LG DVD writer slave on Jmicron IDE
80 GB IDE master on Jmicron IDE
(windows xp pro on 160 gb sata)

The live cd boots - the install proceeds without a hitch - I allow the install to erase and default partition the ide drive.  On restarting after install the system hangs before shutting down and I must hit reset switch; reboot still yields grub error 21.


JornaHow

---

### Post by v8YKxgHe on 2006-10-26
> **jornahow said:**
> The 6.10 amd64 distro still will not boot on my:

MSI P965 Neo - 6400 core 2 duo
LG DVD writer slave on Jmicron IDE
80 GB IDE master on Jmicron IDE
(windows xp pro on 160 gb sata)

The live cd boots - the install proceeds without a hitch - I allow the install to erase and default partition the ide drive.  On restarting after install the system hangs before shutting down and I must hit reset switch; reboot still yields grub error 21.


JornaHow

I get very similar behavior, though I do not get the Grub error - instead usplash loads but hangs with no hard drive activity

---

### Post by robenroute on 2006-10-27
@AlexC & Lupe0: thanks for adding the config info.

@All: see also [this]("https://launchpad.net/distros/ubuntu/+source/linux-source-2.6.17/+bug/66747") bug report. So far, this bug is only related to the unofficial Edgy release; it might be good to add your personal findings to this report in order to get things solved.

Thanks, Rob

---

### Post by robenroute on 2006-10-27
According to the changelog of kernel 2.6.18.1 (see [here]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18.1")), we can get our hands on a proper JMicron driver as of kernel 2.6.19....

BTW, has anyone had any luck yet by replacing GRUB by LILO? I mean, has anyone solved the IDE/SATA installation & boot problems by replacing GRUB in favour of LILO?

Thanks, Rob

---

### Post by SweVoyager on 2006-10-27
> **jornahow said:**
> The 6.10 amd64 distro still will not boot on my:

MSI P965 Neo - 6400 core 2 duo
LG DVD writer slave on Jmicron IDE
80 GB IDE master on Jmicron IDE
(windows xp pro on 160 gb sata)

The live cd boots - the install proceeds without a hitch - I allow the install to erase and default partition the ide drive.  On restarting after install the system hangs before shutting down and I must hit reset switch; reboot still yields grub error 21.


JornaHow
I've got the same exact pattern with my Asus P5B. Hangs before shutting down (but after the cd is ejected) and then error 21 when rebooting. Both my HD and my CD-ROM is connected to the PATA JMicron interface. I guess release wasn't any different to the RC in this case. It sucks!

---

### Post by robenroute on 2006-10-27
> **SweVoyager said:**
> I've got the same exact pattern with my Asus P5B. Hangs before shutting down (but after the cd is ejected) and then error 21 when rebooting. Both my HD and my CD-ROM is connected to the PATA JMicron interface. I guess release wasn't any different to the RC in this case. It sucks!

SweVoyager, GRUB error 21 means that GRUB can't see the disk that is specified in its menu.lst file (based on device.map (?) in the same directory (/boot/grub)). Can you boot from a live-CD and check (and post) the contents of both menu.lst and device.map, please.

According to your information (if I understand correctly, that is), you have an optical IDE device and one HDD in your system, both connected to the JMicron controller (IDE connector).

Thanks, Rob

---

### Post by wilsonywx on 2006-10-27
> **robenroute said:**
> According to the changelog of kernel 2.6.18.1 (see [here]("http://www.kernel.org/pub/linux/kernel/v2.6/ChangeLog-2.6.18.1")), we can get our hands on a proper JMicron driver as of kernel 2.6.19....

BTW, has anyone had any luck yet by replacing GRUB by LILO? I mean, has anyone solved the IDE/SATA installation & boot problems by replacing GRUB in favour of LILO?

Thanks, Rob

I have a dp965lt mobo, corsair 1gb, a sata hdd, and 2 dvd drives connected via ide. I tried the edgy live cd but does not work. I am running mandriva, which uses lilo.

---

### Post by robenroute on 2006-10-27
> **wilsonywx said:**
> I have a dp965lt mobo, corsair 1gb, a sata hdd, and 2 dvd drives connected via ide. I tried the edgy live cd but does not work. I am running mandriva, which uses lilo.

Hi there wilsonywx. Now it becomes interesting (in my humble opinion, that is). It would be most helpful if you could post the contents of the LILO equivalent of GRUB's menu.lst file and (keeping my fingers crossed here ;)) would be willing to give Ubuntu another try and then post the menu.lst contents (supposing you don't know these off the top of your head when you were struggling with Ubuntu).

The theory is as follows: apparently, LILO has got the drives figured out correctly, where GRUB makes a bit of a mess (alledgedly). So when one would install both systems to the same drive/partition and check the references to the drives in question, one could find out how to manually adjust (via a live-CD) the GRUB configuration files to get the system booting.

If anyone can see where my theory goes boobs up, please jump in, by all means.

Rob

P.S. Of course, wilsonywx's hardware is different (Intel board?) and SweVoyager's board is an Asus. There are also people with GigaByte and MSI boards. I realize that this may be a complicating factor.

---

### Post by robenroute on 2006-10-27
Sorry lads and ladinas, I'm off to noddieland. It's 1 in the morning and I'm crackered; 'til tomorrow!

Rob

---

### Post by jornahow on 2006-10-27
Yesterday I said:

The 6.10 amd64 distro still will not boot on my:

"MSI P965 Neo - 6400 core 2 duo
LG DVD writer slave on Jmicron IDE
80 GB IDE master on Jmicron IDE
(windows xp pro on 160 gb sata)

The live cd boots - the install proceeds without a hitch - I allow the install to erase and default partition the ide drive. On restarting after install the system hangs before shutting down and I must hit reset switch; reboot still yields grub error 21."

Now I have edgy 6.10 amd64 running -I gave up on the 80 gb IDE hard drive and bought a 250 gb WD sata II hard drive connected to ICH8 and reinstalled the official edgy live cd.  I installed the nvidia drivers and have 3d acceleration working.  Internet works and alc883 sound works (once I put the sound controls on the menu and unmuted everything.  Why these controls are not visible and muted by default after install i do not comprehend.)

The only remaining issue is that when booting, although grub reports the presence of windows xp on my 160gb harddrive, if I try to boot this from grub it says "drive not found".  I believe my windows drive is plugged into the jmicron sata port and I am reluctant to change it for fear of having to go through the windows activation nightmare again.  The workaround is that the MSI bios advanced options has a menu item to change hard disk priority. By going into bios setup I can change disk priority and boot windows, then change it back for ubuntu.

I can now report that a cup of ubuntu costs $92.00 (price of new hard drive).

JornaHow

I should have added that my LG H10N dvd drive now connected as master on jmicron ide works fine-I don't know about burning, but I am listening to a cd as I type

---

### Post by robenroute on 2006-10-27
Hi JornaHow, it's definitely good news that the JMicron IDE issues concerning optical drives seem to have been resolved with the release of Edgy. However, there are flocks of people still using IDE HD drives and when using the 965 chipset, connecting such a drive to the JMicron PATA controller is one of the few options (one could get an external casing (USB/Firewire) or opt for a mainstream/supported IDE conroller PCI-card, I suppose).

So, going all SATA is probably your best chance, but for now I wouldn't mind getting a grip on what's happening GRUB-wise.

Thanks very much for posting your findings here. This is really helpful for lots of us here on the Ubuntu forums.

Thanks again, Rob

---

### Post by jornahow on 2006-10-27
Hi Robenroute;

There is one other option - I am told that there is a cheapish ($20) pci card that converts ide to sata and allows multiple ide drives to be plugged in, with better performance than the ide to sata converters that plug directly into the back of the drive.

---

### Post by robenroute on 2006-10-28
> **jornahow said:**
> Hi Robenroute;

There is one other option - I am told that there is a cheapish ($20) pci card that converts ide to sata and allows multiple ide drives to be plugged in, with better performance than the ide to sata converters that plug directly into the back of the drive.

Sounds like a good option (I didn't know these cards existed), and this might help some people. But, once again, I think the trick is to stick to straightforward and beaten-track hardware; such PCI cards might be too exotic for Linux....

Rob

---

### Post by SweVoyager on 2006-10-28
> **robenroute said:**
> SweVoyager, GRUB error 21 means that GRUB can't see the disk that is specified in its menu.lst file (based on device.map (?) in the same directory (/boot/grub)). Can you boot from a live-CD and check (and post) the contents of both menu.lst and device.map, please.

According to your information (if I understand correctly, that is), you have an optical IDE device and one HDD in your system, both connected to the JMicron controller (IDE connector).

Thanks, Rob

You understood my configuration correctly. :) One NEC DVD-ROM as master and a 80 Gb Seagate as slave.

I'm not sure where to look for the file(s) you specified. I think that my harddrive doesn't get detected (and automounted) when running the LiveCD, since I only got the LiveCD file tree available.

I do see my HD in the Device Manager as /dev/hdb (partitions 1,2 and 5). I've tried to mount /dev/hdb1 but it complains that it isn't in /etc/fstab or /etc/mtab (both of which I cannot open without "read only").

I'm a real newbie, which I guess I dont need to write. :p

---

### Post by SweVoyager on 2006-10-28
Fedora Core 6 detects the harddrive as hdf, if thats any help at all.

---

### Post by v8YKxgHe on 2006-10-28
Hum will the updated Kernel ( 2.6.18/19 ) make it's way onto the Edgy CD when released? Because this is a pretty big issue if people can not even install any Linux distro with ease, or at all with the jmicron controller.

---

### Post by robenroute on 2006-10-29
> **SweVoyager said:**
> You understood my configuration correctly. :) One NEC DVD-ROM as master and a 80 Gb Seagate as slave.

I'm not sure where to look for the file(s) you specified. I think that my harddrive doesn't get detected (and automounted) when running the LiveCD, since I only got the LiveCD file tree available.

I do see my HD in the Device Manager as /dev/hdb (partitions 1,2 and 5). I've tried to mount /dev/hdb1 but it complains that it isn't in /etc/fstab or /etc/mtab (both of which I cannot open without "read only").

I'm a real newbie, which I guess I dont need to write. :p

SweVoyager the fact that you see your HDD in the Device Manager means that the live-CD does detect the hardware; well, that's a start.

The /etc/fstab file can only be edited by the super-user (root) what you need to do is (from the command line/terminal) type the following:

```
sudo gedit /etc/fstab
```
Make sure you make a copy of the fstab file first, before mucking about....

Read up on the fstab ( in a terminal: "man fstab" is a good start). You should have a line in your fstab similar to this (assuming your system resides on the first primary partition (hdb1) and its file system is formatted as ext3):

```
/dev/hdb1 / ext3 defaults,auto,rw,dev,exec,suid 0 1
```

After changing the contents of fstab, you can mount your file system ("/", in the line above) using the mount command (do this using "sudo" again). This way you can mount your installation and check the contents of the GRUB files and the fstab file of your initial installation (NOT the ones from the currently running live-CD!).

---

### Post by robenroute on 2006-10-29
> **AlexC_ said:**
> Hum will the updated Kernel ( 2.6.18/19 ) make it's way onto the Edgy CD when released? Because this is a pretty big issue if people can not even install any Linux distro with ease, or at all with the jmicron controller.

Hi AlexC, I do agree that this whole installation issue is utterly frustrating, completely unnecessary and not doing the Linux "project" any good. The problem seems to be the installation of Ubuntu on IDE HDDs connected to the JMicron controller. As long as people use SATA disks only (and connect them to the Intel ICH8(R) controller), things seem to go all right. Also see post [#215]("http://ubuntuforums.org/showpost.php?p=1674689&postcount=215") by jornahow.

The fact that Mandriva, using LILO as a boot loader, installs correctly on the same hardware (see post [#212]("http://ubuntuforums.org/showpost.php?p=1672553&postcount=212") ) means that things can and definitely ought to work....

---

### Post by v8YKxgHe on 2006-10-29
robenroute, So if I get an IDE to SATA converter for my IDE DVD RW and my 80GB Storage IDE Hard drive I should be able to install Ubuntu perfectly?

---

### Post by eran- on 2006-10-29
Actually I think that the problem might be with the GRUB loader itself, not the kernel anymore.

Explanation:
I tried to install Fedora Core 6 after various failures of booting up Ubuntu. Ubuntu managed to boot itself from the Edgy Eft cd (desktop found the ich8-connected hard drive, alternate didn't), but not from the GRUB menu. Dapper Drake didn't boot from the CD at all.

Well, with EE the problem was the kernel version .17, which didn't support ich8 or jmicron raid controllers.


But, Fedora Core has kernel .18 built inside. It found my hard drives at the installation process too like Edgy Eft Desktop CD and managed to finish it without any problems. But those problems occured when trying to boot from the GRUB, as it either showed two kind of errors:

- when HD connected to ICH8, it couldn't boot itself, as "BIOS doesn't support cylinders", which I think one kind of nonsense.

- when HD connected to JMicron RAID controller, GRUB shows "Error 21." Which is kinda common to all of us with this problem.


Solution? After kernel update to .18 version, I think that updating GRUB might be the best solution for all people with new hardware. :???:

---

### Post by SweVoyager on 2006-10-29
I've also tried Fedora Core 6 as I said before, but I couldn't get it to install. Various hangs in the installation program and the famous "can't dismount the cd"-error.

---

### Post by SweVoyager on 2006-10-29
How do one go around and install say Ubuntu Edgy Eft with Lilo instead of Grub?

---

### Post by robenroute on 2006-10-29
> **eran- said:**
> Actually I think that the problem might be with the GRUB loader itself, not the kernel anymore.

Explanation:
I tried to install Fedora Core 6 after various failures of booting up Ubuntu. Ubuntu managed to boot itself from the Edgy Eft cd (desktop found the ich8-connected hard drive, alternate didn't), but not from the GRUB menu. Dapper Drake didn't boot from the CD at all.

Well, with EE the problem was the kernel version .17, which didn't support ich8 or jmicron raid controllers.


But, Fedora Core has kernel .18 built inside. It found my hard drives at the installation process too like Edgy Eft Desktop CD and managed to finish it without any problems. But those problems occured when trying to boot from the GRUB, as it either showed two kind of errors:

- when HD connected to ICH8, it couldn't boot itself, as "BIOS doesn't support cylinders", which I think one kind of nonsense.

- when HD connected to JMicron RAID controller, GRUB shows "Error 21." Which is kinda common to all of us with this problem.


Solution? After kernel update to .18 version, I think that updating GRUB might be the best solution for all people with new hardware. :???:


Well, it could be the specific hardware (e.g. different versions of the JMicron controller?) or the BIOS settings, but according to post [#215]("http://ubuntuforums.org/showpost.php?p=1674689&postcount=215"), an all-SATA set-up (for the HDDs, optical can be IDE) does work!

---

### Post by robenroute on 2006-10-29
> **SweVoyager said:**
> How do one go around and install say Ubuntu Edgy Eft with Lilo instead of Grub?

Hi SweVoyager,

Have a look at [this]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") page (and optionally [this ]("http://users.bigpond.net.au/hermanzone/")page as well). I'm not sure you have these options using the live-CD (standard Desktop version). You might need to install from the Alternate CD (downloadable from [here]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease")).

Rob

---

### Post by eran- on 2006-10-29
> Well, it could be the specific hardware (e.g. different versions of the JMicron controller?) or the BIOS settings, but according to post #215, an all-SATA set-up (for the HDDs, optical can be IDE) does work!

Yes, I came up to that too. But as I tried to use different BIOS -settings (at the I/O settings, RAID/IDE/disabled), I wasn't able to find Ubuntu nor Fedora Core 6 to work in my computer. I've tried to install those distros in question many times my HD connected to either JMicron and ICH8 port, but the problem is not getting solved at all.

I have MSI Neo-F P965 motherboard, which has JMicron port and four ICH8 ports onboard. At the BIOS, I/O settings are currently set as "IDE". I've also tried other options as mentioned before.

EDIT: I read that post through, and somehow it makes a little bit sense. But my problem is, that I have only one 250gb SATA HD, and I have no money to buy new one until Christmas. (Aka. student's properous lifestyle. sigh.)

[offtopic] My intenton is not to insult anyone, but isn't these two OS's supposed to be somehow universal to work around on PC's...? I suppose it also means that you don't need to reconfigure your BIOS or change your hardware to get your OS working. I love Debian based distros, mostly I mean Ubuntu and I hope this problem could be solved asap...! :neutral:  [/offtopic]

---

### Post by robenroute on 2006-10-29
> **eran- said:**
> 
[offtopic] My intenton is not to insult anyone, but isn't these two OS's supposed to be somehow universal to work around on PC's...? I suppose it also means that you don't need to reconfigure your BIOS or change your hardware to get your OS working. I love Debian based distros, mostly I mean Ubuntu and I hope this problem could be solved asap...! :neutral:  [/offtopic]

Ideally, yes. However, modern BIOSes (is that how you spell the plural of BIOS?) offer many advanced hardware configuration features (e.g. RAID-related) and this creates additional technical challenges for anyone, regardless of the OS (yes, also Windows is affected by this).

Eran, have you tried installing LILO, instead of GRUB? Have a look at the pages I mentioned (and linked to) in my previous post. People have reported successful installations on similar hardware using Mandriva, and as Mandriva uses LILO, this may be the way to address this issue for the time being.

I'm looking forward to reading about your findings....

Regards, Rob

---

### Post by eran- on 2006-10-29
Thank you, :)  I've been thinking about that. I'll try that when I'm finished reading to one exam, which is going to be held tomorrow... I'll also need to download new alternate image for dapper, I hope it'll recognize my HD. ](*,) 

I'll report my results by this evening...!

---

### Post by SweVoyager on 2006-10-29
> **robenroute said:**
> Hi SweVoyager,

Have a look at [this]("http://users.bigpond.net.au/hermanzone/p6.htm#If_you_choose_No__to_Install_GRUBs_IPL_to_a_custom_location") page (and optionally [this ]("http://users.bigpond.net.au/hermanzone/")page as well). I'm not sure you have these options using the live-CD (standard Desktop version). You might need to install from the Alternate CD (downloadable from [here]("http://www.ubuntu.com/products/GetUbuntu/download#currentrelease")).

Rob
Ok, now I have tried this without succes. Everything installs nicely and the CD is ejected without me being able to chose back to install Lilo. I click back with the CD out, the CD goes back in, and I chose Install Lilo. So far so good, but now the installer hangs with a 50% complete of installing Lilo to the MBR. I wait for 15 minutes and then reboot the computer. Nothing works. In with the CD again and trying to get to the Install Lilo bit again. Cant get to it without a complete reinstallation! FRUSTRATION! I reinstall everything, swearing not so little about rigid installation procedures! And now I await the results of the second installation.

*makes some coffe*

*walks the cat*

*water some plants*

*drinks some more coffe*

*admires the paint on the walls*

*gets bored with the paint on the walls, watches the ceiling instead*

*realises the ceiling needs a repaint*

Finally done! Repeats procedure. 

*expects the worst*

Yep, it hangs at 50% again! I'll think I'll give up on Ubuntu until my motherboard (Asus P5B vanilla) is officially supported (so that I can download the files for swedish locale at install as well).

---

### Post by SweVoyager on 2006-10-29
BTW, nothing gets installed at all when I chose Install Lilo. I still get the Grub error 21 when I try to boot that HD.

---

### Post by robenroute on 2006-10-29
> **SweVoyager said:**
> BTW, nothing gets installed at all when I chose Install Lilo. I still get the Grub error 21 when I try to boot that HD.

Sorry to hear this SweVoyager....:( :( :(  I definitely do understand the frustration you're feeling.

I'm a bit flustered over the fact that you get a GRUB error without even having GRUB installed! I'm also puzzled why the LILO install hangs. I'm getting an eerie feeling about this whole thing. The best thing you can do is report a bug (or perhaps 2?). That's the best way to get the developers' attention. This forum is just for us, mere mortal end-users; I don't think the developers listen in here.

The whole thing is sad, sad, sad....

Rob

---

### Post by SweVoyager on 2006-10-29
> **robenroute said:**
> Sorry to hear this SweVoyager....:( :( :(  I definitely do understand the frustration you're feeling.

I'm a bit flustered over the fact that you get a GRUB error without even having GRUB installed! I'm also puzzled why the LILO install hangs. I'm getting an eerie feeling about this whole thing. The best thing you can do is report a bug (or perhaps 2?). That's the best way to get the developers' attention. This forum is just for us, mere mortal end-users; I don't think the developers listen in here.

The whole thing is sad, sad, sad....

Rob
I think that Grub gets automatically installed as the primary boot loader. I dont have any other HD installed, so theres no need to chose a boot loader and therefor the installer choses for me. And when I chose to install Lilo after the installation has run its course I actually trying to overwrite the already existing Grub with Lilo. Maybe thats the reason the installation of Lilo hangs.

Ive booted up the LiveCD now and managed to mount my HD in Ubuntu, and heres my fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=d636745f-1a6d-410d-9719-e80bc081ebae /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb5
UUID=87e3d768-220e-458a-a8e3-a904c5c3474b none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0

```

and my grub files (menu.lst first and device.map after):
```

# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=d636745f-1a6d-410d-9719-e80bc081ebae ro
# kopt_2_6=root=/dev/hdb1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## should update-grub lock old automagic boot options
## e.g. lockold=false
##      lockold=true
# lockold=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdb1 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

```
```
(hd0)	/dev/hdb
```

PS: my keyboard has gone all american on me, and I cant find some of the right characters. Thats the reason this post is missing some. Ill correct it in Windows if I find can find the energy at a later time. :)

---

### Post by eran- on 2006-10-29
This is getting even better...

Alternate Dapper Drake installation cannot even recognize my DVD -drive which is connected to JMicron controller...!! :mad: 

It boots up the menu, where I can select the installation option. (Orange title, text, server etc.). After that I enter the installation, and then it reports me that installation can't find CD-drive at all...! Now THIS is something I call annoying...

EDIT: Surely, I browsed some old topic through google at Ubuntu forums. Some of the JMicron problems are to be fixed in kernel 2.9.18, which is NOT included in Edgy Eft, nor Dapper Drake. 

Would it be possible to include this kernel in daily builds...? And also including Dapper Drake, since this problem is concerning all the people with JMicron controller on their motherboard.

It seems that I'll have to wait for Debian, since I can't boot Fedora with GAG. I was able to install FC6, but at the bootup it reports something about partition that doesn't even exist...

---

### Post by SweVoyager on 2006-10-29
> **eran- said:**
> This is getting even better...

Alternate Dapper Drake installation cannot even recognize my DVD -drive which is connected to JMicron controller...!! :mad: 

It boots up the menu, where I can select the installation option. (Orange title, text, server etc.). After that I enter the installation, and then it reports me that installation can't find CD-drive at all...! Now THIS is something I call annoying...

EDIT: Surely, I browsed some old topic through google at Ubuntu forums. Some of the JMicron problems are to be fixed in kernel 2.9.18, which is NOT included in Edgy Eft, nor Dapper Drake. 

Would it be possible to include this kernel in daily builds...? And also including Dapper Drake, since this problem is concerning all the people with JMicron controller on their motherboard.

It seems that I'll have to wait for Debian, since I can't boot Fedora with GAG. I was able to install FC6, but at the bootup it reports something about partition that doesn't even exist...
The JMicron problem is fixed in Edgy Eft _as long as you install to a SATA-drive_! I've installed numerous times already, so I should know. :) But you cant install to a PATA drive connected to the JMicron controller, at least as far as I know (and tried).

---

### Post by jornahow on 2006-10-29
Although a linux neophyte, I want to respond to eran's problems since I have the same MSI P965 Neo mobo and have Edgy running.  In one post he said:

"Yes, I came up to that too. But as I tried to use different BIOS -settings (at the I/O settings, RAID/IDE/disabled), I wasn't able to find Ubuntu nor Fedora Core 6 to work in my computer. I've tried to install those distros in question many times my HD connected to either JMicron and ICH8 port, but the problem is not getting solved at all.

I have MSI Neo-F P965 motherboard, which has JMicron port and four ICH8 ports onboard. At the BIOS, I/O settings are currently set as "IDE". I've also tried other options as mentioned before."

I don't know if this is true of other 965 boards, but The MSI board has some functions that are 'pre-bios'; that is invoked prior to the bios -there is a Realtek gigabit boot loader that can be configured by hitting "shift F10 during boot.  Mine is set to boot mode "Rom Disable".  As far as bios settings are concerned.  The bios does not seem to directly handle any of the Jmicron connected drives, whether IDE or sata.  It does display my sata connected to Ich8 on the information screen, but not one connected to Jmicron, either IDE or sata and it will not autodetect these drives.  It does, however list my two hard drives on the advanced settings "Boot priority" menu."

Rather than go through all the individual bios settings that can be tinkered with, I would suggest to eran that he simply load the bios "optimized defaults" - they work for me. As far as drive settings:

IDE/Raid - set to IDE, IDE Block mode enabled, pci busmaster enabled, basically everything else set to auto - these are the default optimized settings.

Jornahow

---

### Post by robenroute on 2006-10-29
> **SweVoyager said:**
> The JMicron problem is fixed in Edgy Eft _as long as you install to a SATA-drive_! I've installed numerous times already, so I should know. :) But you cant install to a PATA drive connected to the JMicron controller, at least as far as I know (and tried).

I think that is a correct conclusion and going the all-SATA way is the best choice for the time being. I think the Intel 965-based boards are promising, but perhaps a bit too far ahead of the current state of things. The 965 chipset is primarily a SATA-only chipset (the JMicron controller is only added for legacy drives). With shedloads of IDE/PATA drives (both optical and HD) still in use, the 965 chipset is a debatable choice. If you're building from scratch and being able to afford everything SATA, it's probably okay....

I'm planning to build a completely new system early next year and I will probably go the AM2 route.

Rob

P.S. I think it would be wise of Ubuntu/Canonnical to be clear about the system requirements/limitations (I've searched the Ubuntu site and not found any specific hardware limitations); this would help people steer clear of a lot of frustration, aggravation and headaches.

---

### Post by SweVoyager on 2006-10-30
> **robenroute said:**
> I think that is a correct conclusion and going the all-SATA way is the best choice for the time being. I think the Intel 965-based boards are promising, but perhaps a bit too far ahead of the current state of things. The 965 chipset is primarily a SATA-only chipset (the JMicron controller is only added for legacy drives). With shedloads of IDE/PATA drives (both optical and HD) still in use, the 965 chipset is a debatable choice. If you're building from scratch and being able to afford everything SATA, it's probably okay....

I'm planning to build a completely new system early next year and I will probably go the AM2 route.

Rob

P.S. I think it would be wise of Ubuntu/Canonnical to be clear about the system requirements/limitations (I've searched the Ubuntu site and not found any specific hardware limitations); this would help people steer clear of a lot of frustration, aggravation and headaches.
Yeah, as far as harddrives it's best to go all SATA it seems, but my DVD on PATA is detected and used at installation. I dont think the problem with my HD is related to Linux either, since it seems it's just Grub that has problems with it (the fact that I can mount it in the LiveCD is rather telling). Maybe I could get Grub to work if I changed some of the HD's parameters but I dont know where to start and I dont think I'll achieve much fumbling in the dark.

Regarding the PS I would tend to agree, even if you could get an overview of the different problems by viewing the forum. I bought my computer way before the majority of the problems arose here though, and I'm a bit saddened that I cant run Ubuntu as of yet. Maybe I'll go buy myself a new SATA HD, but my budget is kind of limited at the moment.

---

### Post by eran- on 2006-10-30
> **jornahow said:**
> I don't know if this is true of other 965 boards, but The MSI board has some functions that are 'pre-bios'; that is invoked prior to the bios -there is a Realtek gigabit boot loader that can be configured by hitting "shift F10 during boot.  Mine is set to boot mode "Rom Disable".  As far as bios settings are concerned.  The bios does not seem to directly handle any of the Jmicron connected drives, whether IDE or sata.  It does display my sata connected to Ich8 on the information screen, but not one connected to Jmicron, either IDE or sata and it will not autodetect these drives.  It does, however list my two hard drives on the advanced settings "Boot priority" menu."

Rather than go through all the individual bios settings that can be tinkered with, I would suggest to eran that he simply load the bios "optimized defaults" - they work for me. As far as drive settings:

IDE/Raid - set to IDE, IDE Block mode enabled, pci busmaster enabled, basically everything else set to auto - these are the default optimized settings.

Jornahow

That sounds quite reasonable... When I get home, I'll try this method. I hope it'll work. :S Although I was going to buy another HD to install Ubuntu natively on it if I can't dual-boot XP and Ubuntu. The funniest thing, Ubuntu installation is able to find my USB-connected HD if it doesn't find my SATA HD. If things are getting to be too frustrating, I'll use USB-HD instead. :D

EDIT: Also, alternate installation of 6.10 EE doesn't find my ICH8 -connected... I think I may be repeating myself, but when connected to JMicron, installation finds it. sigh...

Well, later this evening I'll try to connect my HD to JMicron controller, install LILO instead of GRUB since I have GAG on a floppy disk. (yes. I had to put floppy drive in my PC. haven't used floppy disks in... uh. 5 years or so?) And see if it works.
And, the best, I have to use the broken Edgy Eft, since kernel of Dapper Drake doesn't support ICH8 nor JMicron drives. :D  complicated...? nonono. You're just dreaming... And I'm in the middle of the testweek. doh.

---

### Post by eran- on 2006-10-30
Good news...!

By the time I'm writing this, Ubuntu 6.10 is running, and quite smoothly. 
I installed LILO boot manager as I was adviced to and use GAG (one kind of graphical boot manager) to boot up linux. If I want to boot windows, I'll just need to take the floppy out from the floppy drive...!

I connected my SATA-HD to JMicron controller, and Edgy Eft's installer was able to find my HD perfectly, and installation process went without problems...! Then I selected to install LILO instead of GRUB, and then I went to Windows (as Ubuntu wasn't able to boot yet) and downloaded GAG and installed it to one floppy disket. It's also possible to install it on a CD, but you'll have to set up everything all over in GAG every time you boot your computer.

So... FD in, reboot, some working with GAG and whoa! It worked!

And like jornahow said, optimized defaults worked the best way for me. :)

---

### Post by jornahow on 2006-10-30
Good news eran!  Although I just went into my bios and discovered that I misled you with my last post about defaults.  I noticed that my bios advanced settings under "integrated peripherals" had usb keyboard and mouse support set to "disabled" (I have a ps2 mouse and keyboard).  Out of curiosity I set them both to "enabled" and when I booted Ubuntu from Grub it hung up.  I switched both back to "disabled" and Ubuntu started normally.  I don't know whether this is due to the fact that they were set to disabled when I installed Edgy, or whether there is some other conflict with Edgy (Grub) and usb support on this motherboard.

jornahow

---

### Post by ShadowRage on 2006-10-30
I had jmicron issues until I upgraded to the latest security release of the default kernel. also, make sure you upgrade your usbids and pciids every week or so if you do lspci on your HW.

I'm typing this on dapper with my SATA2 HDD connected to the SATA2 interface on my mobo which uses the jmicron chip.

---

### Post by viskonde on 2006-10-31
hello

i have a gigabyte DS3(chipset 965), and a cant install ubuntu 6.06.. it 'breaks' on mounting root files..
Hdd = sata2
DVD/cd = ide/jmicron

maybe you already answer this,but  but does 6.10 aka edgy run on this board/ chipset 965?

if yes, what do we need to do? just put CD on drive and run it?


cumpts
and sorry english :P

---

### Post by rocktorrentz on 2006-10-31
When I installed Edgy on my P5B (965 based) it installed fine with no tweaking. But I didn't use the RC, I used a daily build from the 25th.

---

### Post by jboehm on 2006-10-31
> **rocktorrentz said:**
> When I installed Edgy on my P5B (965 based) it installed fine with no tweaking. But I didn't use the RC, I used a daily build from the 25th.

Do I understand correctly that you have successfully installed from an IDE optical drive on a JMicron port to a SATA HD either on the JMicron part or off with no issues??

Thanks,
Jon

---

### Post by wilsonywx on 2006-11-10
Can someone confirm that the problem is solved on their p965 board? FOr me, I  am still unable to install because it does not detect my cdrom (the alternate edgy cd).

---

### Post by jinx099 on 2006-11-10
> **wilsonywx said:**
> Can someone confirm that the problem is solved on their p965 board? FOr me, I  am still unable to install because it does not detect my cdrom (the alternate edgy cd).

the PATA works on my Gigabyte P965 DS3 with Edgy

---

### Post by ThunderTor on 2006-11-11
I am just posting here since I have gotten ubuntu 6.10 (edgy) amd64 alternate iso to work on my rather new (maybe a month old) Abit Ab9pro. It normally hangs during " uncompressing kernel" but now I got an error message that suggested adding " irqpoll " to the startup paramaters, which kept the boot from freezing the system.
But with other builds I got the "No cd-rom detected", but suprisingly my dvd drive on a Jmicron PATA controller was now easily discovered.
After that it was a perfectly regular text based install apart from the fact that it failed to find any of my two built in NIC's, :-k but suprisingly they where both there when I first logged into X with the OEM account just not configured. Posting this from inside ubuntu now. :-D 

Base hardware list.
[LIST]
[*]Abit Ab9pro
[*]Intel Core 2 Duo E6400
[*]Kingston DDR2 1GB 533Mhz
[*]Nvidia Geforce 7900GT
[*]1 250GB SataII hardisk (forgot make)
[*]Nec DVD-Dual layer/CD RW
[/LIST]
Dual booting with XP-pro with Grub installed to the MBR.

---

### Post by lazerradial2003 on 2006-11-12
Hi, i got past my problems by installing with IOAPIC turned off in the BIOS and using a PATA cd rom and hdd.

I know IOAPIC has something to with the control of dual core processors and i have a feeling that disabling it meant that only one core was detected, does anyone know how i can check to see if both cores are being used? 

Thanks, lazerradial

---

### Post by v8YKxgHe on 2006-12-09
Guys, 

Will someone please help me to install Ubuntu? I was up first thing to download Edgy and was very disapointed that I could not install Edgy, or any other Linux distro because of my PC specs:

Abit AB9
Intel Core 2 Duo E6600
ATI X800XT
2x SATA 2 Hard drives ( 1 for Windows, and 1 hopefully for Ubuntu )
1x IDE 80GB Hard drive as a storage hard drive
1x IDE DVD RW - slave to the 80gb hard drive, if I remember correctly

I havn't used linux for 2-3 months because of the problems with Jmicron! I need my Ubuntu back!

Please....someone....*cries*

I'm gonna download the Alternate installer CD now and try that - but what else can I do? Will upgrading my BIOS be of any help?

---

### Post by v8YKxgHe on 2006-12-09
I have managed to Install Ubuntu but I can not boot into it at all. When it starts up I get the smallest bit of progress bar and then it locks up!

---

### Post by f0rmula on 2006-12-18
> **AlexC_ said:**
> Guys, 

Will someone please help me to install Ubuntu? I was up first thing to download Edgy and was very disapointed that I could not install Edgy, or any other Linux distro because of my PC specs:

Abit AB9
Intel Core 2 Duo E6600
ATI X800XT
2x SATA 2 Hard drives ( 1 for Windows, and 1 hopefully for Ubuntu )
1x IDE 80GB Hard drive as a storage hard drive
1x IDE DVD RW - slave to the 80gb hard drive, if I remember correctly

I havn't used linux for 2-3 months because of the problems with Jmicron! I need my Ubuntu back!

Please....someone....*cries*

I'm gonna download the Alternate installer CD now and try that - but what else can I do? Will upgrading my BIOS be of any help?

Nope.  I don't think it's fixed.

I've just tried the Feisty Fawn daily build, and I'm still suffering from the same problem.

(This build uses kernel 2.6.19-7-generic)

James

---

### Post by Gehaktbal on 2006-12-24
I still can't get edgy eft to install. I have set the ide controller to ide or raid in bios but it doesn't matter.

I have a:
Abit AB9
core2duo 6300
XFX 7900GT
1 SATA disk
1 IDE cd-rom
1Gb memmory

These are the errors. Is there any sollution?


PCI:cannot allocate resource 0 of device 0000:04:00.0
PCI:cannot allocate resource 1 of device 0000:04:00.0
PCI:cannot allocate resource 2 of device 0000:04:00.0
PCI:cannot allocate resource 3 of device 0000:04:00.0
PCI:error while adapting region 0000:04:00.0/0
PCI:error while adapting region 0000:04:00.0/1

---

### Post by robenroute on 2006-12-26
> **AlexC_ said:**
> I have managed to Install Ubuntu but I can not boot into it at all. When it starts up I get the smallest bit of progress bar and then it locks up!

AlexC, first of all, let me make clear that I don't have a similar motherboard, nor any experience with a similar configuration. But anyway, I'm just trying to help....

The AB9 is one of the Intel 965 chipset boards and people have reported succesful installations. So, let's just assume it's not impossible (although it might require some acrobatics).

This is how I would approach the problem (assuming Ubuntu is installed on one of the SATA drives, with GRUB installed into the boot record of the Ubuntu partition):
1. Disconnect all IDE devices (and possibly disable the JMicron controller in the BIOS).
2. Try booting your PC.
3. If it doesn't boot, try installing Ubuntu again (with GRUB in the boot record of the Ubuntu partition), without the IDE devices connected.
4. If it boots, check if everything works (drives etc.) and shutdown the PC.
5. Start up and go into the BIOS, enabling the JMicron controller again.
6. Try booting your PC.
7. If it doesn't, disable the JMicron controller (again) and buy/borrow (35 US$/euro) a Samsung SATA optical drive, connecting it to the ICH8 SATA controller. Reboot. If it works, great, if not, well.....
8. Following step 6, if your PC does boot, shutdown and reconnect your IDE HDD.
9. Reboot.
10. No go? Well, you'll have to make do without the IDE HDD.
11. Yes go? Shutdown and reconnect the IDE optical drive (to the JMicron controller, that is). Again, boot=go --> Bob's your uncle. Boot=no-go --> Hmmm....

I hope it's a bit clear, what I've written above. I all makes sense to me, but I would understand if that weren't the case for you....

Let me know how you fare.

P.S. I'm not familiar with the exact BIOS settings as they could/would influence the behaviour of the configuration, but perhaps someone else could lend a hand with the "BIOS SATA/IDE/Legacy USB Support/etc." can of worms....

---

### Post by v8YKxgHe on 2006-12-26
Thank you for taking the time to help me out Robenroute, but in the end I just brought a new motherboard (AW9D)

---

### Post by robenroute on 2006-12-26
Not to worry, not at all. I suppose it's a learning process, for all of us. Taking the time is no more than a normal thing to do, really. It's one of those things I like about the Linux community.

I'm happy it's working out for you with a new motherboard.

Take care.

---

### Post by v8YKxgHe on 2006-12-26
sure is a learning process, I even ended up installing Gentoo and playing around with that to see if the problem was Ubuntu-specific, but no Gentoo didn't work either.

---

### Post by lazerradial2003 on 2006-12-30
For people having problems, i found the following to help:

anyone getting error 21 or similar from grub after installing, its worth using lilo instead (this can be done by installing form the alternative install CD, if anyone wants more details i can give them). Also if anyone has any updates on whether Grub is supporting Jmicron IDE / SATA then i'd be very interested! 

The "Error allocating resource to PCI:xxxx" error repeated several times (sorry thats not the exact message im doing it from memory) was solved for me by disabling USB mouse support in the BIOS (possibly USB legacy support in some BIOS's).

Another option is disabling IOAPIC in the BIOS, this may well help but beware only one core will be detected so this is a bit of a zero option. 

It's also worth downloading the latest alternate install CD daily of Edgy, some worked for me some didnt. 

IT took me weeks to get a stable Edgy install running on my dual core box and i can't remember all the steps off the top of my head but i'll be happy to try and answer any questions...

lazerradial

---

### Post by xtknight on 2006-12-30
After you manage to get Dapper/Edgy installed, put pata_jmicron on the blacklist.

$ sudo gedit /etc/modprobe.d/blacklist-pata

add "blacklist pata_jmicron" to the end and reboot.

This will make it stop loading the primitive JMicron driver and use the more advanced libata one instead.  This one has many less bugs in it.  Make sure libata has support for JMicron in your kernel before doing this.  Enable DMA so you don't get freezing during I/O.

$ sudo hdparm -d1 /dev/hde
$ sudo hdparm -d1 /dev/hdf

(etc, etc...)

I'm using my kernel here: [http://www.ubuntuforums.org/showthread.php?t=326343](http://www.ubuntuforums.org/showthread.php?t=326343)

It seems to work great.  I had a few problems before I blacklisted pata_jmicron, however.  Now all I'm getting is this, and I'm trying to debug it:

[65028.757253] hdf: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.
[65065.710222] hde: cdrom_pc_intr: The drive appears confused (ireason = 0x01). Trying to recover by ending request.

And this:

[   43.540410] device-mapper: table: 253:0: linear: dm-linear: Device lookup failed
[   43.540416] device-mapper: ioctl: error adding target to table

---

### Post by xtknight on 2006-12-30
> **lazerradial2003 said:**
> 
It's also worth downloading the latest alternate install CD daily of Edgy, some worked for me some didnt.

Where do you get the daily Edgy CD?  All I see is Feisty Fawn and the install in that is broken for me.

---

### Post by wilsonywx on 2007-01-08
> **AlexC_ said:**
> sure is a learning process, I even ended up installing Gentoo and playing around with that to see if the problem was Ubuntu-specific, but no Gentoo didn't work either.

I would say that I would better spend my time learning to program the system than living with its hardware incompatibilities.

---

### Post by robenroute on 2007-01-12
> **xtknight said:**
> After you manage to get Dapper/Edgy installed, put pata_jmicron on the blacklist....

This may be a workaround. However, scores of people cannot install Ubuntu in the first place. So, for the time being, it's advisable to stay away from the Intel 965-based boards (or go full-SATA).

---

### Post by SweVoyager on 2007-01-14
> **robenroute said:**
> This may be a workaround. However, scores of people cannot install Ubuntu in the first place. So, for the time being, it's advisable to stay away from the Intel 965-based boards (or go full-SATA).
I have finally managed to install Ubuntu. I had to buy a new SATA-harddrive, but it installed nicely from my PATA dvd-rom. Both the LiveCD and the Alternate-install-cd worked fine, and both the 32 bit and the 64 bit installed fine.

Feisty on the other hand hanged, but that is to be expected from beta media I guess. :)

---

### Post by popeyeray on 2007-01-23
I don't know about all this modification for a problem a couple of other distro's (Mandriva 2007, and Zenwalk 4.2) have solved with no user input/modifications whatsoever. It's sad but the kernel in Zenwalk 4.2 is 2.6.18 and it installs without a hitch on my Intel 965 Gigabyte w/jmicron. I tried the Ubuntu 6.10 and the latest and greatest Fiesty with kernel 2.6.20 no dice. I even went to the trouble of buying the Lite-On Corp CD-RW/DVD Model SHC-S257K0SC SATA Drive Ubuntu still won't install that I know of without some exotic pre-kernel commands that I don't have a week to spend trying to figure out. No gentlemen i'm sure that this problem will be solved but for now i'll have to wait for the final Fiesty edition. I will be using Zenwalk on my most powerful system and of course Ubuntu on my older compatible systems. Ubuntu does rule, and maybe they are doing the right thing in getting the problem solved at their speed, but a few of us have these Intel 965 boards and can't use it for now.

---

### Post by NetGhost on 2007-01-27
with SUSE 10.1 Kernel 2.6.16 I have the same problems....at installation NO CDROM :-(

---

### Post by robenroute on 2007-01-29
> **popeyeray said:**
> I don't know about all this modification for a problem a couple of other distro's (Mandriva 2007, and Zenwalk 4.2) have solved with no user input/modifications whatsoever. It's sad but the kernel in Zenwalk 4.2 is 2.6.18 and it installs without a hitch on my Intel 965 Gigabyte w/jmicron. I tried the Ubuntu 6.10 and the latest and greatest Fiesty with kernel 2.6.20 no dice....

This is causing some anxiety! Not only Mandriva and ZenWalk install without a problem, FC6 also knows how to deal with the JMicron stuff on board.

What's going on? Why is Ubuntu not capable of doing this? When Edgy was lauched, they (launchpad) said it would be solved in 2.6.18. Now, Feisty is on 2.6.20 and still no-go? I really hope this is not true....

---

### Post by mcbacker on 2007-01-30
> **lazerradial2003 said:**
> For people having problems, i found the following to help:

anyone getting error 21 or similar from grub after installing, its worth using lilo instead (this can be done by installing form the alternative install CD, if anyone wants more details i can give them). Also if anyone has any updates on whether Grub is supporting Jmicron IDE / SATA then i'd be very interested! 

The "Error allocating resource to PCI:xxxx" error repeated several times (sorry thats not the exact message im doing it from memory) was solved for me by disabling USB mouse support in the BIOS (possibly USB legacy support in some BIOS's).

Another option is disabling IOAPIC in the BIOS, this may well help but beware only one core will be detected so this is a bit of a zero option. 

It's also worth downloading the latest alternate install CD daily of Edgy, some worked for me some didnt. 

IT took me weeks to get a stable Edgy install running on my dual core box and i can't remember all the steps off the top of my head but i'll be happy to try and answer any questions...

lazerradial

Hi my friend,

I own a P5B DLX with the JMicron Controller and i'm not beeing able to boot [K]Ubuntu, error 21 freezes the PC during the BOOT.

Can you provide some more information about LILO Installation/Configuration process?

I really appreciate that!

Regards,

MC

---

### Post by jzlharvey on 2007-02-04
Well, I am in the same boat as most of you guys.

I have a p5b-e and upon what seems to be a good install. I get a error 21 in GRUB.  All I have connected is a PATA HD (MASTER) and DVD-RW (Slave).

I have been up all night trying to figure it out.  please anyone with a final answer chime in.

---

### Post by jzlharvey on 2007-02-04
err.. oops double post

---

### Post by acankat on 2007-02-06
Success at last with msi p965 neo and an external dvd drive;

from [https://wiki.ubuntu.com/Core_2_Duo_Support](https://wiki.ubuntu.com/Core_2_Duo_Support)

1. disable IOAPIC from bios
2. boot edgy live cd from your external usb drive
3. install and restart
4. compile kernel 2.6.19 as it shows in [http://ubuntuforums.org/showthread.php?t=311158](http://ubuntuforums.org/showthread.php?t=311158)
5. restart and enable ioapic from bios

at last I got rid of vindov$ hexp.

---

### Post by sveri on 2007-02-16
I finally did it :-)

Specs:

MSI P965 Neo
Core 2 Duo E6300
Jmicron Controller
IDE CD-Rom attached to the sata controller with an SATA-IDE Converter

After a week of endless trying with usb-stick install, Dapper, Edgy, Feisty herd 1-3, 
Fedora, Zen... and so on i tested the new Kubuntu Herd4 today, and see, it installs.

All i did was disabling usb mouse and keyboard in the bios settings,
unplug all drives i dont need, means i only had one sata drive plugged on which i wanted
to install.

Pass the arguments irqpoll and all-generic-ide while booting from Livecd, it should work.

Before i did that i totally cleaned up my disk, formatted and deleted the mbr.
(Maybe u dont need this, but especially my mbr was corrupted after one week of endless
installs without success)

Partioning the whole disk without user interaction didnt work for me, afterwards it tried to
install to my usb stick which still was connected and ended with telling me i dont have enough space :-)

So i started the Installation again and partitioned my harddisk manually with gparted,
choosing 1 / partition and one swap partition.

Thats all i did.

Happy day i have now, playing around with kubuntu again after 2 months living without any
Unix :(

At least theres still a lot of things to handle with, right now i doenst recognize my hdd
on the ide controller, graphic cards and so on, but hey, its just an alpha release and it works.

Feel free to mail me if u have any questions, cause i dont look often into this forum.

---

### Post by Viper_iii on 2007-02-16
okay....  I have the P965 Neo Platinum and would like to install it... read a lot of posts but still not sure...

here is my setup...

Standard DVD-Rom to the IDE port...

3 320gb SATA II's configured in a Raid 5 and I want to install Ubuntu as a LAMP so I can move all of my hosted sites and crap to a redundant box and back it up to another but installing to the RAID5 is what I want....

If I change it non-raid just IDE or whatever in the bios it will see the drives individually... I want to install to the raid...

I'm getting ready to look at this patch [https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/+viewstatus](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502/+viewstatus)
but not sure if anyone else has tried this...

apparently it doesn't like the duo either not just the controllers...


--------Update-------
I forgot that It also doesn't recognize the Ethernet either... is there a driver that will work?

and lastly should I use the 64bit or standard i386?

anyway if there is a good way that someone has done this I would love to read that.. even if I missed it just give me quick link to go read more...  

thx and Much appreciated!

---

### Post by sveri on 2007-02-16
Like i wrote, i had to buy an IDE-SATA Converter [f.i.]("http://www.winner-leipzig.de/product_info.php?info=p16030_Converter-IDE---SATA-DeLOCK.html"), because Feisty Herd 4 still doesnt recognize the drives on the IDE Controller, maybe theres
a workaround i dont know.
I had the bios set to IDE, but like stated above, it doesnt matter for me.

Herd4 recognizes the Ethernet Controller and it works out of the box unlike Edgy.
Tried on the Neo Board, not Platinum.

Just try it out with the settings i posted above, its really fun to have it work, and its
fast as hell.

It recognizes my duo with usb and keyboard disabled in the bios.

Proprietary Ati driver works for me, i also got my dual head config working.
VMware is tricky, but i read some people got it working on feisty.

If somebody knows bout getting the IDE controller working i'd be much more happy
to hear it, all my music is on the drive there, thank god we have enough good streaming
channels.

---

### Post by samjh on 2007-02-18
> **jzlharvey said:**
> Well, I am in the same boat as most of you guys.

I have a p5b-e and upon what seems to be a good install. I get a error 21 in GRUB.  All I have connected is a PATA HD (MASTER) and DVD-RW (Slave).

I have been up all night trying to figure it out.  please anyone with a final answer chime in.

This is my exact situation - same motherboard and PATA configuration as yours, and the same error too.

Have you tried a Parallel-to-SATA converter yet?  I've tried everything except using a converter or making kernel modifications.

[EDIT]

I'm gonna try updating BIOS:

[http://www.sabayonlinux.org/forum/viewtopic.php?p=12456&sid=bae2c5d6f04c7e09bc849c20b441ca8d](http://www.sabayonlinux.org/forum/viewtopic.php?p=12456&sid=bae2c5d6f04c7e09bc849c20b441ca8d)

---

### Post by samjh on 2007-02-20
I can now confirm that Ubuntu 6.10 will install and boot with the latest BIOS update for JMicron motherboards.

For me, the mobo is ASUS P5B Deluxe with the latest BIOS update (any of the two that were released on Jan 07).

This is because the JMicron controller's BIOS need to be updated to support booting using Grub.  This is documented on JMicron's support FAQ.

---

### Post by sveri on 2007-02-20
> **samjh said:**
> I can now confirm that Ubuntu 6.10 will install and boot with the latest BIOS update for JMicron motherboards.

For me, the mobo is ASUS P5B Deluxe with the latest BIOS update (any of the two that were released on Jan 07).

This is because the JMicron controller's BIOS need to be updated to support booting using Grub.  This is documented on JMicron's support FAQ.

Does ubuntu recognize hard disks on the IDE controller with the bios update?

---

### Post by samjh on 2007-02-20
> **sveri said:**
> Does ubuntu recognize hard disks on the IDE controller with the bios update?

Yes, both my drives - the hard disk and DVD/CD - are IDE (ie. PATA), plugged into the P-IDE connector of the motherboard using one standard IDE connection cable with HDD set as Master and DVD/CD as Slave.

---

### Post by sveri on 2007-02-20
> **samjh said:**
> Yes, both my drives - the hard disk and DVD/CD - are IDE (ie. PATA), plugged into the P-IDE connector of the motherboard using one standard IDE connection cable with HDD set as Master and DVD/CD as Slave.

Sounds great, maybe i can hear music tomorrow :-)

---

### Post by proto on 2007-02-23
I have also confirmed this.  

After wresling with the JMicron installation issue for some time with my MSI P965 Neo, I updated the BIOS to version 1.6.  I was able to install 2.6.17.11 from a PATA DVD drive onto a PATA hard disk.  Simple, clean install.  Boots fine.  I have not tested SATA drives.

I did disable IOAPIC in the BIOS first -- no idea if it was really necessary.  Other than that, no tricks or hacks.  (Of course, I had to first install Win XP and the Realtek Ethernet drivers to run MSI's LiveUpdate process.)

Now my life is full of Ubuntu goodness!

---

### Post by exc220 on 2007-02-23
> **proto said:**
> I have also confirmed this.  

After wresling with the JMicron installation issue for some time with my MSI P965 Neo, I updated the BIOS to version 1.6.  I was able to install 2.6.17.11 from a PATA DVD drive onto a PATA hard disk.  Simple, clean install.  Boots fine.  I have not tested SATA drives.

I did disable IOAPIC in the BIOS first -- no idea if it was really necessary.  Other than that, no tricks or hacks.  (Of course, I had to first install Win XP and the Realtek Ethernet drivers to run MSI's LiveUpdate process.)

Now my life is full of Ubuntu goodness!

awesome!!! can't wait to try it!!!!
So everything works fine in ubuntu?

---

### Post by robenroute on 2007-02-23
> **exc220 said:**
> awesome!!! can't wait to try it!!!!
So everything works fine in ubuntu?

And, have you?

It would be great for all of us to get more "news from the field". Thanks.

---

### Post by Nodiz on 2007-02-23
It actually works. After several (and miserable) attempts at trying to install Ubuntu with my Asus P5B Deluxe Wifi, I finally succeeded. All I had to do was update my BIOS and now 6.10 installs and boots without a problem :)

---

### Post by Nodiz on 2007-02-24
However, I can't get the onboard sound card (SoundMAX HD Audio) to work...

---

### Post by robenroute on 2007-02-24
> **Nodiz said:**
> It actually works. After several (and miserable) attempts at trying to install Ubuntu with my Asus P5B Deluxe Wifi, I finally succeeded. All I had to do was update my BIOS and now 6.10 installs and boots without a problem :)

That's good news!

It would be great to hear from other 965-board owners (Gigabyte has some very popular boards) whether they've seen any improvements with their latest BIOS upgrades.

Cheers.

---

### Post by willnapier on 2007-02-25
Hi everyone.  I bought a pc in september and due to problems with the jmicron issue I have put my head in the sand (and waited to find solutions here) until now. My motherboard is an ECS P965t-a rev 1. The north bridge is P965, the south bridge is intel ICH8. In my first attempts to solve the problem, I bought a samsung sata dvd drive. Unfortunately this didn't work. I can install edgy, but when I reboot it hangs (actually I get pci errors similar to ones mentioned recently in this thread). The motherboard has the JMicron JMB361 sata and pata controller on it,  but I'm not too sure which connectors are associated with it. According to an independent source, the BIOS is Phoenix Award 6.0. Unfortunately the ECS website is down 'for maintenance'.

Do you think that a BIOS upgrade might do the trick for me as it has for some here with other motherboards? If so, can I get this upgrade from somewhere other than the ECS site? Also, since I don't have any OS installed on this new machine apart from the unbootable edgy that installed from the sata dvd drive, how can I get the bios upgraded? I can download on my old machine (from where I am posting this) and onto a floppy if that would be any use? Or I can get Edgy working as a live cd and go online that way and download - but I suppose that I can't save the file to use if i do it with a live cd. I'll see if there are any options given to upgrade bios when I try and boot the new pc.

Any help greatly appreciated. I have been greatly discouraged by not being able to use my new machine (I refuse to use windows) for several months, and I'm really glad that some of you have found success at last.

I have now discovered by trial and error that of the five sata sockets, one is red and removed from the others. Here is the [link]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetailPhoto.aspx?DetailID=681") to a photo of the layout. This appears to be attached to the JMicron controller, because when I put either the sata dvd or the sata hdd into it, these are registed as being ide. I installed successfully by putting the sata dvd into that socket, but then couldn't boot it. Now, when I remove all other connectors, including the two ide optical drives (the ones that came with the new pc as opposed to the sata dvd drive I bought), and then I put the hdd into the JMicron sata socket, it still gives me the pci error messages (cannot allocate resource region 1, 2, etc).. but it then carries straight on and boots up to the login screen. I thought I'd got somewhere.. but it turns out that the keyboard doesn't work (it is not a usb keyboard and I wonder if this would make a difference). So it boots up, but I can't log in! Again, if anyone can shed light on this I would be very grateful.

Will

---

### Post by honkyjesus on 2007-03-01
Hi,

I can confirm that edgy final boots after a bios update (using MSI P965 Neo, bios update to 1.6). Although it wasn't what I would call a seamless install. I had no support for ethernet (fixed by ripping an old ethernet card from a different computer.... disable onboard ethernet in bios), I had no luck installing with a usb keyboard and usb mouse connected (again, cracked out an old computer and am using PS/2 mouse and keyboard.... disabled usb mouse, usb keyboard in bios). I disabled IOAPIC (in the bios) to be on the safe side. I am also not sure if disabling IOAPIC is necessary.  I am not going to bother with any other versions until feisty final is released. I will just wait. I am happy it is running for now.

Thanks to everyone who has shared their experiences installing Ubuntu on P965 chipsets.

H. J.

---

### Post by strange_cathect on 2007-03-04
> It would be great to hear from other 965-board owners (Gigabyte has some very popular boards) whether they've seen any improvements with their latest BIOS upgrades.

I've been following this problem for over a month now and was encouraged when people began saying that a BIOS update solved the issue.  I have a MSI Neo board and, even after a BIOS update, I continue to have the PCI error message when attempting an install of Ubuntu.

---

### Post by jeff_p on 2007-03-04
Hello,

I have just updated the BIOS on my Intel 965G board, with no luck.  I am using Herd 5 (feisty fawn).  What is happening here...is there a way I can make this work?

---

### Post by Nomeko on 2007-03-15
And this is the story about how my iPod nano saved my life... :D

I have an ASUS p5b mainboard and grub wouldn't load (error 21). When I finally realized that I had to upgrade my bios I had no flash drive around.

Luckily I had my iPod nano next to me, so I plugged it in while running the live-cd enabling me to download and unzip the bios rom. After a reboot into bios setup I used ASUS' nifty EZ Flash 2 utility to upgrade the bios. 


No more Grub problems!!!

---

### Post by tqft on 2007-03-19
From 
[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/57502)
JMicron PATA/SATA Controller does not work
"On all 2.6.17 and below kernels, the JMicron JMB363 controller, found on the ASUS P5B motherboard, does not work"

Status has just been changed to Fix Released - hopefully it will hit the repositories soon.

Not yet at my end of the world.

---

### Post by Datamanius on 2007-03-19
> **proto said:**
> 
After wresling with the JMicron installation issue for some time with my MSI P965 Neo, I updated the BIOS to version 1.6.  I was able to install 2.6.17.11 from a PATA DVD drive onto a PATA hard disk.  Simple, clean install.  Boots fine.  I have not tested SATA drives.


I updated the BIOS to version 1.6 too. But I have SATA DVD and SATA hard disk. Ubuntu not install. :confused:

---

### Post by robenroute on 2007-03-19
> **jeff_p said:**
> Hello,

I have just updated the BIOS on my Intel 965G board, with no luck.  I am using Herd 5 (feisty fawn).  What is happening here...is there a way I can make this work?

Apparently, the fix from JMicron needs to be integrated into the motherboard's BIOS. You could email Intel and ask them about it. For good measure, check out JMicron's website.

Good luck.

---

### Post by shanedog on 2007-04-23
I have a MSI P965 Neo motherboard. I downloaded Feisty Fawn and was able to get it to install (after I moved my SATA drive to the Intel controller and disabled RAID in the BIOS). But I haven't been able to get it to boot from the hard drive. It hangs and then drops into busybox after like 5 minutes or so. Does anyone have Ubuntu installed on a SATA hard drive with this motherboard working?

---

### Post by johnbick on 2007-04-23
First let me warn you that I am a newbie to Ubuntu/Kubuntu and I am having a different set of problems with a P5B-E setup ( [http://ubuntuforums.org/showthread.php?t=417455](http://ubuntuforums.org/showthread.php?t=417455) ). But maybe I can shed some light on your situation based on my recent Windows Vista experience. Had you said "Vista" instead of "Ubuntu/Kubuntu" on these posts it would have perfectly described my first 72 hours with my new machine...

First, a quick clarification concerning JMicron on this board. The IDE is SUPPOSED to on all the time whether you set the JMicron controller into IDE or RAID. HOWEVER, sometimes you will wonder about that! Read on.... 

I finally decided I had a hardware problem and disconnected everything except the disk I wanted to install to and the DVD (on the IDE). For my Vista the disk is a RAID-1 on positions 3-4 (of 1-6). (There is a comment in the manual about this pair being preferred for a RAID-1, so I did that.) No other SATA or IDE plugged in. Installation went just fine. THEN I went back and added a second drive, a RAID-5 for data using connectors 1-2-5-6. It was recognized, formatted, etc. with no problems and works like a charm. 

I wanted to add another SATA on the JMicron. Initially it failed. After discovering the drive was bad, and then that the cable was bad (many four letter words omitted here) I got a good drive/cable and it still failed. I set the JMicron to RAID and, of course, it worked -- but I lost the IDE and DVD. Set it back to IDE and the drive works like a charm as does the IDE/DVD. I have even added a slave to the IDE and am able to access it without problems from Vista. And, using Alternate Install, I have installed Kubuntu on it. (I have not actually gone back and changed that to a RAID configuration as I do not have an external drive to connect to it anyway.)

SO, for you, I would recommend trimming things down to the basics for your install and add the "extra" drives after you get things working. 

BUT REMEMBER, I AM A NEWBIE TO UBUNTU/KUBUNTU SO THIS MAY NOT APPLY. But the parallels are definitely there so it may be of help to you. 

Good luck! 

(My problem is that I cannot get the GRUB dual boot to work on that RAID-1 drive that is my main boot drive. Either it installs to only one side of the mirror or it installed to the drive in the #1 position - my RAID-5 - or something. If anyone knows a fix for that please go to [http://ubuntuforums.org/showthread.php?t=417455](http://ubuntuforums.org/showthread.php?t=417455) and post a reply!)

---

### Post by Pixman on 2007-07-09
Hello folks,

I've tried 2 months ago to install Ubuntu 7.04 , but since then, it still fails.

I've got a Foxconn P9657AA Motherboard with a JMB361 SATA Controller. All (2) hard disks are SATA and connected to that controller and I think my DVD drives are too (even though I'm not sure, nor if this is even relevant).

Everything works fine in Windows XP SP2

Everytime I try to boot, it fails with the usual errors, "can't set xfer mode" from the ata module.

I recognized a lot of the same errors in here.

I tried with  apic=off nolapic noapic irqpoll all-generic-ide  as parameters but I received the same error.
It seems like I'm completely unable.

First, I thought, it was just an old problem which will be fine in the 7.10 or is already fixed by now in the daily versions.

So I downloaded an alternative Ubuntu, a daily 7.10 version and I still received the same errors.

Other distributions work like a charm (OpenSUSE, Fedora) but I don't want them at all, they're not fine for my environment I'm developing software in.

Is there still no solution for this? I'm desperate to have a native Ubuntu environment since I'm sick of working in a VMware environment and I don't want to buy a new computer.

Sure, I'm not saying that anyone is guilty for that than me or that I even can expect anything since this is a free community project, but I don't get, why this is till not built-into the current kernel configuration if there is a solution around, looking at other distributions.

Has anyone got some ideas?

Thanks a lot for your support!

---

### Post by Cyberapoc on 2007-07-10
I've got the same problems, had to reformat.

I got Feisty running now though, with help from Wubi. It works,  however not optimal, it enables me to run ubuntu with JMicron controller.

Won't use Grub until there's a fix though...

---

### Post by Pixman on 2007-07-12
Good news!

It DOES work... but it took me a long time to figure it out.

I saw, that I had to change in the BIOS the IDE controller (onboard) to AHCI instead of SATA.


After that, it went perfectly with me. No BIOS upgrades etc., nothing.

Already saw that somewhere in the forum, worked for them try.

Have a try.. :)

---

### Post by rennen01 on 2007-09-19
JMicron was working for me fine on Edgy.  When I upgraded to Feisty, I had to remove several different items including the Nvidia drivers.

Now, bootup is really slow.  Thinking about recompiling the kernel.  I will post here if anything I do helps with the bootup speed.

---

### Post by rennen01 on 2007-09-25
Re-compiled to 2.6.22.7 Kernel and everything is back to normal.

---

