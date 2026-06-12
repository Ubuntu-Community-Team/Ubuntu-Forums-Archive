---
title: "live cd hangs"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by radha on 2007-05-20
Hi
I just built a new machine
intel core 2 duo (E6600)
intel 965 chipset (msi p965 platinum)
nvidia 8800 gts
sata hard drive and optical drive

I got a feisty amd64 cd.
i cannot get the cd to boot...
any boot params i should pass given my particular setup??

Thanks

---

### Post by Ubimad on 2007-05-21
is not bootable:D  either you do not boot from cd or cd is not propper burned

---

### Post by radha on 2007-05-21
I got the cds shipped. I did not download/burn them.
And its the same with ubuntu and kubuntu. So i am assuming its not an issue with the media

I boot from the cd. I tried the default boot and boot with safe graphics. It hangs after 2-3 seconds

---

### Post by Schnyd on 2007-05-22
I'm having same issue. I can get it to the UBUNTU screen with the load bar but nothing loads. I was able to I have:

Nvidia 8800gts
amd 64 dual core 4400
Asus crossfire motherboard
2 gig ram

---

### Post by Adler on 2007-05-22
I posted this Yesterday without a response

[B]Hi All,

I've just gotten a new COMPAQ Presario Notebook with the following specs:

- AMD Turion 64 X2 Dual Core TL-60
- 15.4" WXGA Bright View Wide Screen
- NVIDIA GForce Go 6150 w/ Ports
- IMPRINT Finish + Microphone(s)
- 2GB DDR System Memory (2Dimm)
- 160 GB 5400 SATA HDD
- Light Scribe Super Multi 8X DVD+/-RW w/ DL
- 802.11 pre-n WLAN & Bluetooth

It has Vi$ta loaded, and I want to wipe the entire 160GB SATA drive and install Ubuntu 7.04. I did burn both the 32 and 64-bit Cs with the default M$ burner app Roxio, then used QParted to wipe the drive and format the entire thing to ext3. 

When I tried to install UBUNTU the Live CD hangs. From what I am reading SATA drives seem to be an issue. Am I right or am I wrong? Any help, please!
[/B]

Adler

---

### Post by PsyDev on 2007-05-22
I am having a problem too, where my 7.04 desktop installation CD hangs. I know it's not a media problem because I got it to work (in safe graphics mode) on another computer.

Basically what happens (either normally or in safe graphics mode) is the CD boots, then displays the ubuntu logo with a status bar. Once it's done loading, it switches to a black screen with a blinking cursor in the top-left. It then stays here indefinitely.

I'm running a Toshiba Satellte 1800 laptop.

any help would be appreciated... trying to kick windows out for good!

---

### Post by DUNC4N on 2007-05-22
Did you guys hit f6, and change the "splash", to "noapic"?  Try that


Eventually I changed  the grub from "splash" to "nosplash"

And everything has been good since.

GL

---

### Post by PsyDev on 2007-05-29
Hey. I changed the options by pressing f6 and turned off the "silent" switch and turned off the splash.

It seemed to take forever to do things so I left it for a few hours and went outside. When I came back it was displaying this screen:
[http://www.lowenergy.net/linux.jpg](http://www.lowenergy.net/linux.jpg)

It just kept doing what seemed like a refresh of this screen and never moved beyond that.
Anyone have insight?

Could it be that Ubuntu simply doesn't want to install because it doesn't like my laptop? (Toshiba Satellite 1800, from about 2001).

Thanks

---

### Post by globalist on 2007-05-29
Same thing just happened to me! The live cd install hangs (on a black screen) after a few seconds.

I had no such issues when I tried to install from this CD previously and the only thing that's changed is I swapped my ATi x1950pro vidcard for a nVidia 8800GTS (oh the irony! now ati is the good one with linux :D ).

Any ideas? And no, Safe Graphics mode doesn't work either- it even starts to emit these rapid beeps from my motherboard after it hangs the same way... weird.

---

### Post by handydan918 on 2007-05-29
I'm beginning to think this is a bona fide bug. I have tried this cd on a gateway amd (single core) laptop, an amd dual core desktop, an intel core2 desktop, an old pIII, and a pIV. I get exactly the same behavior. It loads the menu screen, and regardless of options, hangs while loading the kernel. if this distro won't boot on the variety of hardware I have tried it on, what good is it? Mark, you listening? This is the release that Dell is shipping?!
 Oh, BTW, all of the machines I mentioned have another distro already installed, so before some hack starts in with the "did you check the md5sum" crap, yes, I did, and I probably did more than most people know how to do. I have installed various flavors of linux at least 50 times over the last 5 yrs.
Somebody needs to take a look at this installer issue. I can't understand how this got out of QA.
The really funny thing is that all these machines work with MEPIS 6.0/6.5, which is a debian/ubuntu derivative!

---

### Post by teejay17 on 2007-05-29
> **PsyDev said:**
> I am having a problem too, where my 7.04 desktop installation CD hangs. I know it's not a media problem because I got it to work (in safe graphics mode) on another computer.

Basically what happens (either normally or in safe graphics mode) is the CD boots, then displays the ubuntu logo with a status bar. Once it's done loading, it switches to a black screen with a blinking cursor in the top-left. It then stays here indefinitely.

I'm running a Toshiba Satellte 1800 laptop.

any help would be appreciated... trying to kick windows out for good!
I used to have the same probem with Ubuntu 6.10, and for some reason the problem was rectified, at least for me, in version 7.04. I was able to boot into the live CD no problem. 
I did get many helpful suggestions, however, when I posted this problem. Check out the thread here: [http://ubuntuforums.org/showthread.php?t=330118](http://ubuntuforums.org/showthread.php?t=330118)
Perhaps there will be something in there to help you guys out.

---

### Post by Adler on 2007-06-01
Guys,

I've learned several important lessons here.

1. I've a new Vi$ta notebook, and tried the 7.04 download, and burn with the default Vi$ta burner. They were not bootable. I then downloaded the Nero 7.0 trial version, and then burned the ISO with my USB Lite-On CD/DVD burner. That booted my Notebook to 7.04. 

2. I had the same install issue with Dapper that most have had. Go F6, then add "noapic" without the quotes. This should take you through the launch of the Gnome Desktop, and install.

Now, if I could get my WiFi card going...

BCM 4321AG 802.11 a/b/g/draft-n WiFi adapter. 

Adler

PS I'm now dual-booting into Vi$ta. GAWD, before I installed FF, IE was so, so strange to work with. LOL!

---

### Post by teejay17 on 2007-06-01
> **Adler said:**
> Guys,

I've learned several important lessons here.

1. I've a new Vi$ta notebook, and tried the 7.04 download, and burn with the default Vi$ta burner. They were not bootable. I then downloaded the Nero 7.0 trial version, and then burned the ISO with my USB Lite-On CD/DVD burner. That booted my Notebook to 7.04. 

2. I had the same install issue with Dapper that most have had. Go F6, then add "noapic" without the quotes. This should take you through the launch of the Gnome Desktop, and install.

Now, if I could get my WiFi card going...

BCM 4321AG 802.11 a/b/g/draft-n WiFi adapter. 

Adler

PS I'm now dual-booting into Vi$ta. GAWD, before I installed FF, IE was so, so strange to work with. LOL!
Glad you were able to get things running.

---

### Post by sk545 on 2007-06-01
guys, this is still Linux.  The live Cd is going to be hit or miss...there is no way its going to work will every machine out there.  There just isn't much vendor support for linux, so if it installs and works, you got lucky.

---

### Post by teejay17 on 2007-06-01
> **sk545 said:**
> guys, this is still Linux.  The live Cd is going to be hit or miss...there is no way its going to work will every machine out there.  There just isn't much vendor support for linux, so if it installs and works, you got lucky.
I'm not sure if "got lucky" is a satisfactory explanation. Linux is not veiled in mysticism or couched in the unexplained. It's a compilation of programs that is put together by individuals who listen to user feedback. Hence this forum. 
Hence this thread.

---

### Post by Adler on 2007-06-01
> guys, this is still Linux. The live Cd is going to be hit or miss...there is no way its going to work will every machine out there. There just isn't much vendor support for linux, so if it installs and works, you got lucky.

sk545,

Before we start a Flame War I have to disagree. I'm doing this from M$ Vi$ta. Never in Linux have I had to quit everything because an update was found. I'm tired of baloons **telling**me what to do. I gave up M$ years ago. 

Solutions are out there to boot Ubuntu, or other Linux distros. 

Just in case others have issues, here is what I found regarding possible solutions. I'd sent this to a buddy of mine. He is the Uber Linux Guru.

[I]It appears that the issue of not being able to install the latest Ubuntu, or Linux Mint is a pretty common issue. This throws me back to the days of Dapper. I've got several collected ideas when running the install - 
 
1. acpi=off - Press F6
2. noapic
3. noapic nolapic/acpi=off
4. pci=conf1
5. live noapic nolapic - Hit ESC @ initial boots.[/I]

Just to add, the default M$ burner with Vi$ta did not produce a bootable Live CD. I downloaded the trial version of Nero 7, then used my Lite-On CD/DVD burner to work around M$ issues. I have to come back to your comments. *Try getting commercial support from M$ to solve an issue.* Duh? Really.

> I'm not sure if "got lucky" is a satisfactory explanation. Linux is not veiled in mysticism or couched in the unexplained. It's a compilation of programs that is put together by individuals who listen to user feedback. Hence this forum. 
Hence this thread.

teejay17,

I could not agree more. Forums like this help others to enjoy all that Linux goodness. With the help of others I could dual-boot, triple-boot, get harware going that M$ could not. The list goes on, and on.

It is -- afterall -- an open source community that I am proud to be a memeber of, and contribute where I can with possible solutions. I'll get off my soapbox now. LOL!

BTW -- great come back there.

Adler

---

### Post by pacman2440 on 2007-06-01
Thank you guys!

I have been posting and searching forums for days now trying to figure out why my 3 previous installs worked and now my brothers wont. Its good to know that i'm not alone and there are solutions out there, now I just have to see if it works. This should be made a sticky since so many people have had issues with it.

---

### Post by Adler on 2007-06-01
Hey pacman2440,

Dude -- I'm in Arizona, but never joined the local IRC chat as of late. 

Glad to have helped, and again, we all help each other. I guess that I'll see you @ Ubuntu Arizona LoCo Team.

Adler

---

