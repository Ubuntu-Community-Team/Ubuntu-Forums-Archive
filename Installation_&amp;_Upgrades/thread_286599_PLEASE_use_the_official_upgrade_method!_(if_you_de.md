---
title: "PLEASE use the official upgrade method! (if you decide to upgrade)"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by PWill on 2006-10-27
Please, people; if you plan on upgrading to Feisty Fawn 7.04, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

---

### Post by magicfab on 2006-10-28
EXCEPT for Xubuntu...! Please read:
[http://www.ubuntuforums.org/showthread.php?t=285951](http://www.ubuntuforums.org/showthread.php?t=285951)

There is a critical bug when upgrading with the standard method fro Xubuntu:
[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027)

Modifying the sources, etc. when following the instructions to upgrade is OK, BTW. It causes problems when you have external repos, etc.

---

### Post by kjbetz on 2006-10-28
How can you say that modifying your source list is unofficial, etc... when it's right here in the documentation?

[https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by PWill on 2006-10-28
I could be wrong, but I was going by this: [https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0](https://wiki.ubuntu.com/EdgyReleaseNotes#head-b07f8bdf28ae0444c03e1a61110c683c77e56cd0)

---

### Post by ubuntu_demon on 2006-10-28
I stickied this thread. If you decide to upgrade I recommend upgrading through :
```

$ gksu "update-manager -c"

```

---

### Post by Bigglez on 2006-10-28
Um ...
It seems that Kubuntu 6.06 does not have 'update-manager'. What to do?

---

### Post by muxecoid on 2006-10-28
The problem is that the official method is not working at all, it just did nothing for me. And repository-upgrade, I already learned, is breaking dependencies.

---

### Post by Timothy Butwinick on 2006-10-28
> **ubuntu_demon said:**
> I stickied this thread. If you decide to upgrade I recommend upgrading through :
```

$ gksu "update-manager -c"

```

I, kind of, used the other method, and now my system is broken: X does not find the required graphics drivers and neither my wireless card nor my ethernet card can access to the network. 

When I log in on a virtual terminal, it looks like this:

```
laptop login: me
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
Password:
```

Is there any way to revert the upgrade, or do I have to make a fresh install?

[B]Edit: Problem solved. To activate the ethernet card do
sudo ifup eth0
After this you can use apt-get to install the missing graphics drivers:
sudo apt-get install xserver-xorg-video-vesa
and then restart X:
sudo /etc/init.d/gdm restart[/B]

---

### Post by Akoluth of Nandus on 2006-10-28
> **ubuntu_demon said:**
> I stickied this thread. If you decide to upgrade I recommend upgrading through :
```

$ gksu "update-manager -c"

```

What does the update-manager do besides automatically changing your sources.list and performing a dist-upgrade?

---

### Post by linuxnoob40 on 2006-10-28
~$ gksu "update-manager -c"
this method starts to work but only gets to 39 of 40 files and just hangs

---

### Post by Paradoxdruid on 2006-10-28
> **Bigglez said:**
> Um ...
It seems that Kubuntu 6.06 does not have 'update-manager'. What to do?
That is indeed a problem, since using the sudo aptitude dist-upgrade methods has failed horribly on 3 separate Kubuntu machines for me, now, leaving one in an unrecoverable state (so far).

You can see my problem [here]("http://ubuntuforums.org/showthread.php?t=285176&highlight=debconf+nice+edgy") (Debconf saying Nice values are out of range, perl warning, and dpkg script dying, failing the whole process.)

---

### Post by Milambar on 2006-10-28
gksu "update-manager -c" assumes you're NOT running headless (no monitor or keyboard attached). My only access to the box is via a ssh session.

I now have a broken PC and am looking at a full reinstall. Thank's Ubuntu developers, for making invalid assumptions (You assumed everyone would have an attached monitor/keyboard and be sat in front of the machine being upgraded)

Does anyone have any solutions for repairing a borked upgrade, short of reinstalling from the ground up?

---

### Post by philipacamaniac on 2006-10-28
I borked my main machine using apt-get dist-upgrade. I tried the update-manager first, but it wouldn't complete the process and said there were errors.

So now I have a machine with a non-functioning xserver-xorg and a lot of error output here and there. Since I can't seem to get xorg to work, and I'm fairly experienced, I'm going to try ```
dpkg-reconfigure --all
``` I don't have any CD-Rs around, or else I would just try reinstalling.

EDIT: I'm getting errors like missing font directories and parse errors in conf files. Yargh!

---

### Post by daffy_d on 2006-10-28
This is amazing. I followed the "official" guidelines on how to update. Some errors while upgrading, but nothing that seemed fatal. Until I rebootet. The new '386' kernel-image fails to detect my usb keyboard and spits out error messages about usb-device not working. (also in recovery mode). (In addition, it will not start X) The 'general' kernel-image manages to boot to log-on screen (X), but mouse and keyboard still does not work. 'general' kernel in recovery mode has keyboard support. But what good is that. Older kernel-images just fail miserably at an early stage. Downloading FC6 as we speak, done in another 10 minutes. Good bye Ubuntu :( (At least FC6 has good 64bit support. I tried using Ubuntu 6.06 64bit for a while, lots of stuff unavailable, and lots of stuff not working. So I ended up with 32bit version, and has been happy until now.)

PS My original ubuntuforums-user 'daffy_' is automatically kicked out every time I'm logging in. (Welcome, etc. and on the next page I'm not logged in anymore.) What's up with that?

---

### Post by steveneddy on 2006-10-28
I upgraded last night using the -c method and woke up every so often to hit the "Yes" key. My daughter clicked a few for me this morning after I had to go to work. She said there was a screen saying the x-server failed, but I'll bet that I can go home and configure the x-org file....again....and get it up and running in no time. I made sure that I uncommented the lines in gconf-custom to disable XGL and restarted. THEN I started the upgrade process - I just hope that I don't have the nightmare that some of these other folks have that I've been reading about.

I'll get back to this later with the results of my upgrade.

I'm using nVidia and and old PIII with 512 mb RAM, & I've never really had a problem that I couldn't get past, it just means that I'll get to hack around a little more tonight.

Results soon.

SE

---

### Post by theosib on 2006-10-28
There have been reports of breakage by those who were using software RAID.  It seems that the Dapper and possibly Edgy installers don't set things up right in the first place.  Doing the upgrade is even worse, because it doesn't even take RAID into account.

Here's a reference:
[https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/68308](https://launchpad.net/distros/ubuntu/+source/ubuntu-meta/+bug/68308)

---

### Post by steveneddy on 2006-10-28
> **steveneddy said:**
> I upgraded last night using the -c method and woke up every so often to hit the "Yes" key. My daughter clicked a few for me this morning after I had to go to work. She said there was a screen saying the x-server failed, but I'll bet that I can go home and configure the x-org file....again....and get it up and running in no time. I made sure that I uncommented the lines in gconf-custom to disable XGL and restarted. THEN I started the upgrade process - I just hope that I don't have the nightmare that some of these other folks have that I've been reading about.

I'll get back to this later with the results of my upgrade.

I'm using nVidia and and old PIII with 512 mb RAM, & I've never really had a problem that I couldn't get past, it just means that I'll get to hack around a little more tonight.

Results soon.

SE

This is not even funny. I am running vesa with no acceleration just to get back to  GUI screen. I am lost. I did the nvidia-glx restricted-modules and such driver instqlls to no avail. 

Someone please help.

It seems like the ones who are usually in the forums answering these questions are conspicuously absent.

When are we going to get an answer to this?

-SE

** EDIT: **

I gave up and reinstalled, which is probably as much work as trying to get Edgy running. I'm normally not a quiter, but I have to go to work on Monday AM and I need to come home and do work, also. I used bad judgement by taking a system that was working perfectly with the Nvidia Beta driver and beryl and borked things up beyond repair.

I think I learned my lesson.

I installed Firefox 2.0 and am trying to remember what I did to customize my system before, like the icon themes, the window borders and the wallpapers. I did save the pics and wallpapers on the other HD, so everything wasn't lost.

I don't think that Edgy is ready for everyone. I think I'll try the LiveCD first next time.

Thanks for the help. I appreciate your time.

-SE

---

### Post by reyfer on 2006-10-28
> **Bigglez said:**
> Um ...
It seems that Kubuntu 6.06 does not have 'update-manager'. What to do?

I used the method described her [http://www.ubuntuforums.org/showthread.php?t=285099](http://www.ubuntuforums.org/showthread.php?t=285099) and I have experienced no problems so far, been in Edgy for 48 hours without problems

---

### Post by LuisC-SM on 2006-10-28
I used every "oficial" method, -c option, DL edgy and burn the CD, I had to install dapper 3 times again... the problem is that my daughter's pc originally was using Breezy, with dapper I had no upgrade problem as it took all my breezy values with no problems (maybe some little things any noob can fix), but now, I canot even go back to dapper, I really feel frustated.

My lspci:
> 00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE]
02:01.0 Multimedia video controller: Brooktree Corporation Bt878 Video Capture (rev 11)
02:01.1 Multimedia controller: Brooktree Corporation Bt878 Audio Capture (rev 11)
02:02.0 Multimedia audio controller: Creative Labs SB Audigy LS
02:03.0 Modem: Motorola Unknown device 3052 (rev 04)
02:08.0 Ethernet controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) integrated LAN Controller (rev 02)
I really hope someone can enlighten me as far as my pc is all FU,

Kind Regards

Luis C. Suárez

PS. Please, dont tell me to dpkg-reconfigure all (I've done this 10 times) plus all ATI HOWTOs found here and some other wikkis.  This is really driving me knuts

---

### Post by Milambar on 2006-10-29
> **Milambar said:**
> gksu "update-manager -c" assumes you're NOT running headless (no monitor or keyboard attached). My only access to the box is via a ssh session.

I now have a broken PC and am looking at a full reinstall. Thank's Ubuntu developers, for making invalid assumptions (You assumed everyone would have an attached monitor/keyboard and be sat in front of the machine being upgraded)

Does anyone have any solutions for repairing a borked upgrade, short of reinstalling from the ground up?

Stranely enough, after doing aptitude update && aptitude dist-upgrade a whopping 6 times (I kept redoing it until it no longer found anything that needed upgrading), most of ubuntu started working again, and what didn't work was made to work by aptitude purge <packagename> && aptitude install <packagename>. 

The machine still doesn't reboot cleanly, ie, the networking doesn't start up, which means I have to walk over to the actual server rack, plug in a monitor and keyboard, and type "sudo ifconfig eth1 192.168.x.x up" to bring up the eth1 interface. This allows me to at least ssh in so that I can go and sit down at my nice comfy console in the office, and set up the routes ("route add default gw 192.168.1.1" for those who need to do the same).

This is NOT ideal, in fact, I might make a bash script in /etc/init.d to bring up the networking interfaces on boot.

Sorry Ubuntu, I'm really NOT impressed this time, and have stopped recommending you to people looking to change from Windows to Linux. I do have a working web/mail server again, and yes, its running edgy, but the upgrade path could have been better, a lot better, and it still needs manual intervention on boot.

---

### Post by igorzolnikov on 2006-10-29
sudo update-manager -c
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

What next? Software Updates have status: "Your system is up-to-date".

---

### Post by igeldard on 2006-10-29
[QUOTE=xiamcitizen;1675449]Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

I used gksu "update-manager -c -d" (what does the -d switch do anyway), got the option to upgrade distribution but got several warnings about upgrade failures. After a reboot my system froze.

So can I correct this and get a working 6.10 system, or do I have to go back to 6.06? Is there a way to do this without a complete reinstall?

Ian

---

### Post by igorzolnikov on 2006-10-29
gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Software Updates have status: "Your system is up-to-date".

---

### Post by moooooooo on 2006-10-29
as a long time Linux user and early adopter of Ubuntu...my upgrade to Edgy has been a disaster.
I have my main computer paging video as if its swapping to disk a la early Windows 3.0/3.1 and me getting the himem.sys and emm386 stuff wrong under DOS 4. 
Where previously i had hardware accelerated OpenGL capable of playing the Linux version of Unreal Tournament 2004 and relevant settings working flawlessly even with ATIs poor Linux support of the ATI Radeon 9600.

Can't say i'm happy as i have 5 computers all having ATI cards, although not all require a video head (ie they are servers).

So when i hit the pagedown key while reading my email now, it's like getting in the Tardis and watch video circa 1988. Fantastic.

Wheres my Atari 1024 STFM? graphics back then mattered and seem overlooked in this release of Ubuntu....of COURSE i'm venting.

I'll have to hack my xorg.conf and check dmesg and all the stuff that I know how to get HWOGL acceleration working again, and i KNOW i'll get it working but what about your Joe Citizen users who have NFI about computers???

You guys need to test your upgrades much better.
not happy Jan!!!
cheers
peter

---

### Post by moooooooo on 2006-10-29
oh and my Amarok tracks are all in song order.....under the artist...no album delineating them. Awesome. Not.
feck. maybe i need to join the Windows club and <ctrl>-<alt>+<del> to see if this is just a weird thang or a "known bug".....that i need to reboot to fix??....

oh and my mouse wheel scrolls like in my previous post....video page swapping aaah...i i have a full length x86 CGI graphics card on my desk salvaged from a cleanout. I may as well use that....
yep still venting
peter

---

### Post by moooooooo on 2006-10-29
seeing theres been no replies which is fine as i'm going away for two weeks camping in a few hours...
i upgraded thus:
cp -p /etc/apt/sources.list /etc/apt/sources.list.dapper
vi /etc/apt/sources.list
in vi i did:
:g/dapper/s//edgy/g

save the file

then 
cp -p /etc/apt/sources.list /etc/apt/sources.edgy

then as root of course, apt-get update, apt-get dist-upgrade

init 6

and then yes i get my graphics and graphcis performance issue. 


Alas, i am away for two weeks as of Monday morning AEST, so i can't do anymore than i have described until i come back.
take care
peter

---

### Post by drseuk on 2006-10-29
Just upgraded from 6.06 to 6.10 using sudo update-manager -c (which is essentially the same as gksu update-manager -c).

It asked me to confirm a couple of config file changes (chose "Replace") and whether I wanted to remove some obselete files (chose "Keep").

Everything works perfectly including Firefox 2.0 which was upgraded automatically. Fonts look even better than they did. Some programs seem to work better (e.g., Gaim sound works now). My machine is loaded with thousands of applications and used as a server as well as for development and general use.

If anything, the only thing I don't like about Ubuntu is that it's too easy to use :-)

---

### Post by moooooooo on 2006-10-29
ok. i should say i did some compiz and xgl stuff before i upgraded to Edgy.
Hence my graphics issues due to me not reading as much as i should have.

as i have my emails still on my Gentoo partition, consider my complaints trite (bollocks even) and i shall re-install due to some issues i hadn't considered.

Apologies to all. I mean it. Ubuntu has not failed for me apart from this PC which well...has everything on it.

Everything:
Disk 1 Windows XP, BeOS (remember BeOS???), 
Disk 2 Solaris 10 x86 (actually Open Solaris Nevada build 50...aka SunOS 11 aka Solaris 11) 
Disk 3 Gentoo, Ubuntu (was Dapper, now Edgy)

beers and maybe i should have had a few before posting.
peter

---

### Post by nimrod_abing on 2006-10-29
> **Milambar said:**
> The machine still doesn't reboot cleanly, ie, the networking doesn't start up, which means I have to walk over to the actual server rack, plug in a monitor and keyboard, and type "sudo ifconfig eth1 192.168.x.x up" to bring up the eth1 interface. This allows me to at least ssh in so that I can go and sit down at my nice comfy console in the office, and set up the routes ("route add default gw 192.168.1.1" for those who need to do the same).

This is NOT ideal, in fact, I might make a bash script in /etc/init.d to bring up the networking interfaces on boot.


Let me guess, when debconf asked if you wanted to replace or keep your old config files, you said "Replace" to everything?

Look in [FONT=Courier New][SIZE=4]/etc/network[/SIZE][/FONT], you should find a file in there [FONT=Courier New][SIZE=4]interfaces.dpkg-old[/SIZE][/FONT]. This is your old [FONT=Courier New][SIZE=4]interfaces[/SIZE][/FONT] file that got replaced. You can check if anything has been added to the new [FONT=Courier New][SIZE=4]interfaces[/SIZE][/FONT] file and manually merge it with your old [FONT=Courier New][SIZE=4]interfaces[/SIZE][/FONT] file. If there are no changes in the new [FONT=Courier New][SIZE=4]interfaces[/SIZE][/FONT] file, then it should be safe to copy [FONT=Courier New][SIZE=4]interfaces.dpkg-old[/SIZE][/FONT] to [FONT=Courier New][SIZE=4]interfaces[/SIZE][/FONT].

If a lot of your stuff does not work, then it's probably just because the upgrade replaced some of your old config files. Do:

```
sudo find /etc -name '*.dpkg-old'
```

To see what got replaced and begin restoring them one by one, make sure that you merge any changes in the upgraded config files. As with your interfaces file, if you don't see any major changes in the new version of the config file, then it should be safe to copy the .dpkg-old version over the new one.

If you don't mind my asking, why did you upgrade your server to Edgy knowing full well that this is an "edgy" release? If you were using Dapper on such a mission critical server, you should not have upgraded. That's why Dapper is an "LTS" release, which means for production and mission critical tasks, you should use that release and you can safely ignore other new releases until the next LTS release.

If Edgy has some packages that you need and you simply cannot compromise with an upgrade, then ask for that package to be **backported**. It's that simple. If no one is willing to backport it, then you can try to do the backport yourself by downloading the package sources and build them using deb-build. Or get someone (and pay them) to do it for you.

---

### Post by Pedro Martins on 2006-10-29
> **Bigglez said:**
> Um ...
It seems that Kubuntu 6.06 does not have 'update-manager'. What to do?
I'm have the same problem. How can I update Kubuntu?

---

### Post by nimrod_abing on 2006-10-29
> **Pedro Martins said:**
> I'm have the same problem. How can I update Kubuntu?

Uhm, install the update-manager package first?

```
sudo apt-get install update-manager
```

---

### Post by bobpaul on 2006-10-29
> **Milambar said:**
> gksu "update-manager -c" assumes you're NOT running headless (no monitor or keyboard attached). My only access to the box is via a ssh session.

...

Does anyone have any solutions for repairing a borked upgrade, short of reinstalling from the ground up?

You might be able to use ```
ssh -Xc username@server
``` to enable X forwarding. I can log into my box remotely using this method and then type something like "gcalctool" in the ssh terminal and calculator will open on my local machine. If the client machine is Windows, you can use Cygwin to install an X server...

As far as fixing your box, how exactly is it b0rk3d? There is a solution to every problem, but it's hard to know the specific solution without knowing the specific problem.

---

### Post by grkravi on 2006-10-29
> **Timothy Butwinick said:**
> I, kind of, used the other method, and now my system is broken: X does not find the required graphics drivers and neither my wireless card nor my ethernet card can access to the network. 

When I log in on a virtual terminal, it looks like this:

```
laptop login: me
configuration error - unknown item 'FAIL_DELAY' (notify administrator)
Password:
```

Is there any way to revert the upgrade, or do I have to make a fresh install?

[B]Edit: Problem solved. To activate the ethernet card do
sudo ifup eth0
After this you can use apt-get to install the missing graphics drivers:
sudo apt-get install xserver-xorg-video-vesa
and then restart X:
sudo /etc/init.d/gdm restart[/B]

I had the same problem...couldnt get gdm working after upgrade, used aptitude though.
How to install the vesa driver while doing a fresh install from Live CD ? GDM is not coming up in my Dell Inspiron 5160 laptop to do a fresh install from Live CD.

---

### Post by iposner on 2006-10-30
I attempted to upgrade two systems -- a Pentium III 850MHz Dell Inspiron and an old Pentium II 300MHz running Xubuntu. What a disaster! In both cases I tried the recommended "update-manager -c" method and it roundly trashed both machines.

Ubuntu was becoming a firm favourite of mine -- however this upgrade is an example of how to take a sterling product with a growing reputation and trash it in one fell swoop. If Microsoft had have released such ropey, poorly tested trash, it would have been the end of the company and we'd be reading it on the front pages of broadsheets around the world.

It's not good enough for an OS attempting to become mainstream to continue the practices of the enthusiast open-source community: Releasing poorly tested code and relying on the user-base to provide your testing AFTER RELEASE will ensure that Linux remains where it is -- nothing more than a plaything of enthusiasts and small businesses without a pot to piss in.

---

### Post by goser on 2006-10-30
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

I would do it but this doesn't work for me at all - my update manager doesn't inform me about new versions. Am I the only one with this problem? There must be some point I'm missing.

---

### Post by nocturn on 2006-10-30
> **Milambar said:**
> 
Sorry Ubuntu, I'm really NOT impressed this time, and have stopped recommending you to people looking to change from Windows to Linux. I do have a working web/mail server again, and yes, its running edgy, but the upgrade path could have been better, a lot better, and it still needs manual intervention on boot.


I agree that the Dapper -> Edgy upgrad is somewhat Edgy.

But don't disrecommend Ubuntu for that.  Dapper is the one for most users to go, the purpose of Edgy was taking risks.  If they get Dapper LTS, they should have a good install.

---

### Post by nocturn on 2006-10-30
> **goser said:**
> I would do it but this doesn't work for me at all - my update manager doesn't inform me about new versions. Am I the only one with this problem? There must be some point I'm missing.

That's correct.  You need the -c switch for that.

The reason is that Dapper is LTS, so by default the upgrade to Edgy is not recommended.  Only for those who are willing to track a semi-stable version.

---

### Post by Bigglez on 2006-10-30
You know what? There is **no indication** on ubuntu.com that Edgy is **not** an upgrade...
There is **no mention **that it's semi-stable...

For all intents and appearances,6.10 is the update to 6.06.

Is there going to be a stable update from 6.06 in two years time to 8.01 or something like that?


Note:
I ***may have missed*** this information, but I follow the RSS feeds and this is still surprising to me!


*Confused*
:(

---

### Post by goser on 2006-10-30
> **nocturn said:**
> That's correct.  You need the -c switch for that.

The reason is that Dapper is LTS, so by default the upgrade to Edgy is not recommended.  Only for those who are willing to track a semi-stable version.

I mean it isn't working also when I type the -c - ```
gksu "update-manager -c"
```  I think I'll try editing the sources.list or a new install.

---

### Post by diff_sky on 2006-10-30
> **nimrod_abing said:**
> 

If you don't mind my asking, why did you upgrade your server to Edgy knowing full well that this is an "edgy" release? If you were using Dapper on such a mission critical server, you should not have upgraded. That's why Dapper is an "LTS" release, which means for production and mission critical tasks, you should use that release and you can safely ignore other new releases until the next LTS release.

If Edgy has some packages that you need and you simply cannot compromise with an upgrade, then ask for that package to be **backported**. It's that simple. If no one is willing to backport it, then you can try to do the backport yourself by downloading the package sources and build them using deb-build. Or get someone (and pay them) to do it for you.

I'm glad to read opinions like this.

At first I thought I might want to upgrade to Edgy but realised that I'm more after stability than shiny, wizzyness for my server. I've got a fairly complex software raid5 setup for storage of all my music/photos and (in terms of apps) on the box I've just about got stuff how I like it - so I don't need to take the risk.

---

### Post by Mr Green on 2006-10-30
Please make the official upgrade method work then!

As it apparantly does when running 
sudo apt-get install xserver-xorg before rebooting or in recovery mode :D

---

### Post by Soyle Mycelf on 2006-10-30
> **nimrod_abing said:**
> 

If you don't mind my asking, why did you upgrade your server to Edgy knowing full well that this is an "edgy" release? If you were using Dapper on such a mission critical server, you should not have upgraded. That's why Dapper is an "LTS" release, which means for production and mission critical tasks, you should use that release and you can safely ignore other new releases until the next LTS release.

If Edgy has some packages that you need and you simply cannot compromise with an upgrade, then ask for that package to be **backported**. It's that simple. If no one is willing to backport it, then you can try to do the backport yourself by downloading the package sources and build them using deb-build. Or get someone (and pay them) to do it for you.

This is a very condescending statement. Please show me on [this announcement page]("http://www.ubuntu.com/news/610released") where there is any indication that edgy is somehow "experimental" or "beta". In fact, they state that 
> Significantly faster boot up times and **the best in leading edge free software technologies** make the latest Ubuntu the **first choice** for many new and **existing** Linux users. 
(emphasis mine)

Please stop blaming the users for taking the upgrade path encouraged to them. Those creating that path obviously left gaping potholes.  Don't get me wrong, Ubuntu is a fantastic distribution and those working on it deserve heaps of praise.  As a software developer I know all too well that things can and will go wrong.  But blaming the user for following instructions is **never** good policy.  Admit that there are problems with the upgrade, apologize, fix them, **test them**, release, and apologize again.  Users easily forgive mistakes when corrected quickly and with humility, but rarely forgive being treated rudely.

---

### Post by myname on 2006-10-30
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

I tried this on my Kubuntu system, and it got a message telling me that "gksu  --  command not found", or something simliar.  I since borked my system like everyone else trying to upgrade (from CD, which didn't work either), then had to do a fresh install.

ARGH!  :)

--Kevin

---

### Post by Paradoxdruid on 2006-10-30
I wish I had known, before struggling with 3 separate Kubuntu systems, that I MUST ```
dpkg-reconfigure debconf
``` and set it to use dialog, else the installation will fail on installing x11-common and fairly bork your system (it's a KDE thing, I guess...).

Since knowing that, editing the sources.list and ```
sudo aptitude update
sudo aptitude dist-upgrade
``` has worked fine for Kubuntu.

So, yeah..  For Kubuntu, need to make sure debconf is using dialog, don't have update-manager or gksu...  The "official" method is pretty unusable.

---

### Post by nimrod_abing on 2006-10-30
> **Soyle Mycelf said:**
> This is a very condescending statement. Please show me on [this announcement page]("http://www.ubuntu.com/news/610released") where there is any indication that edgy is somehow "experimental" or "beta". In fact, they state that 
 
(emphasis mine)

Please stop blaming the users for taking the upgrade path encouraged to them. Those creating that path obviously left gaping potholes.  Don't get me wrong, Ubuntu is a fantastic distribution and those working on it deserve heaps of praise.  As a software developer I know all too well that things can and will go wrong.  But blaming the user for following instructions is **never** good policy.  Admit that there are problems with the upgrade, apologize, fix them, **test them**, release, and apologize again.  Users easily forgive mistakes when corrected quickly and with humility, but rarely forgive being treated rudely.

:-k My apologies if that came across as rude or condescending to **you**, but I just wanted to ask the original poster (Milambar) an honest question. I thought I was being very civil in asking too. But what's done is done, so if I stepped on any toes, then I apologize :mrgreen: 

Apologies aside, I pointed out the available options for mission-critical setups. **An upgrade is not the only solution, and in most cases on a mission-critical setup, it's not the ideal solution.**

I also wanted to point out that **if you want to use Ubuntu as your OS for a mission-critical system, you should use the LTS version** which at this time is **Dapper**. Unless Edgy contains some packages that you absolutely must have and backports are impossible, then by all means upgrade to Edgy.

I mean, would **you** risk your company's mission-critical system just so **you** can have the latest and greatest packages? It appeared that Milambar upgraded a mission critical system to Edgy when it was working fine on Dapper, all without making any backups. I could be wrong but that's what I can gather from the posts he/she made, and I hope he/she was able to get the system back up to a usable state.

I believe if you trackback up this thread you will find that Milambar's comments against the Ubuntu Developers are totally uncalled for: even if it was just an attempt at sarcasm to vent his/her frustration. Yes, the upgrade process is **not** perfect. [B]It will not work properly if you had done a lot of tinkering with your system prior to the upgrade.
[/B] 
I managed to upgrade my Dapper to Edgy with no major problems. The only problem I had was fglrx not using DRI, but that was it and I managed to have it resolved eventually through the help on this forum.

It is unfortunate for him/her and others who are having problems that the developers are not very active on these forums. And when these users post bug/problem reports to the developers list, they get shooed away to IRC or the forums :( (I'm subscribed to the developers list and there are a lot of instances of this happening.) it's starting to look like the early days of the Debian mailing lists (Ugh! My age is starting to show!) I guess working on Edgy has made some of these developers "edgy" :D

As a developer, you should also know the frustration and anger you get when users blame you when $h!t happens when all along, it was the users who were doing something that was out of spec. Users being "users" tend to deviate from your well-laid plans most of the time doing things that you did not expect during testing and development. With a continuously growing user base all spanning a wide range of "noobiness", this was bound to happen with Ubuntu. This is a very unfortunate happenstance, but it will serve as a learning experience for **everybody**: especially the Ubuntu developers.

As far as I can tell, **a lot of the problems experienced by those who are upgrading from Dapper** **are caused by a lot of tinkering done prior to the upgrade**. I list them in the order that causes the most problems:[LIST=1]
[*]Installing proprietary drivers that are not from the official Ubuntu archives (NVIDIA, ATI, WLAN cards)
[*]Installing packages from source. Like packages that are not yet "Debianized".
[*]Installing packages from binary "installers" or alien packages (rpm to deb). Like the Sun JDK or IBM DB2 Express-C.
[*]Replacing the official Grub packages with gfxboot-grub.
[*]Must-have that bling! A lot of the problem reports seem to come from users who have installed compiz/beryl.[/LIST]#1 is a major source of pain for many users because a lot of these users would have resorted to manually installing these packages and editing configuration files. **During upgrade they do not pay enough attention when debconf asks if they want to replace or keep their current configuration files.** While that in itself is not a problem if you have a few manually edited config files, it becomes burdensome if you have a lot of these files. **They just choose whatever makes sense to them and most would choose "Replace".**

#2 is a problem because when you install packages from source, dependencies are not properly tracked. An upgrade may replace those dependencies with an incompatible version **and break** your system.

#3 is similar to #2, but only if you chose to install these as root. You can install most of these packages with binary-only installers as a normal user and you should not have any problems. But if you install them as root, you introduce untracked dependencies into your system.

#4 the probable cause of a lot of systems not booting properly.

#5 users with compiz/beryl installed **will** have problems. This is related to #1.

I agree with you on your point that the upgrade path left a lot of room for mistakes. The "official" instructions make a some assumptions for the current state of your system without taking into account the customizations made by the users prior to the upgrade.

It totally assumed that everyone will be installing from a pristine Dapper install :( and there are no notices or warnings about heavily customized Dapper installs (and no, PLF packages do not count as a "heavy" modification).

In my case, I have an *almost* pristine installation. VMWare server and Zend Platform are the only alien packages on my system. Everything else (over 1000 packages) is from the official Ubuntu archives, the PLF archives, or my own local repository of packages built from source. The upgrade caused me no major problems to these alien systems. And FYI, since I installed from Warty over a year ago, I have never done a clean install -- not ever! A dist-upgrade always did the trick for me and for Edgy the graphical Update Manager worked without a hitch.

I have a few suggestions that might those users who are still planning to upgrade from Dapper:[LIST]
[*]If you are on a mission-critical system **DO NOT UPGRADE FROM DAPPER** (I know it's hard to resist, but resist you must!). If you need packages from Edgy, then request for a backport. Or if you cannot wait for a backport, learn how to roll your own .deb files.
[*]If you have a mission-critical system and you absolutely **must upgrade**, **backup your current installation!** Even if your system is not a server but you're in the middle of very important work, do not risk the upgrade without making any backups. More importantly, do not risk the upgrade if you do not know how to restore from backups!
[*]**Systems being upgraded should not be left unattended, it is very important that the user pay attention when being asked to replace or keep configuration files.** Especially if you have hand-edited your configuration files!
[*]It should also be noted that **people using gfxboot-grub may experience problems booting their system after the upgrade.** Your course of action at this point is to remove gfxboot-grub, install the official grub packages and run grub-install again. You can always re-install gfxboot-grub after you have upgraded.
[*]If you have installed graphics card (ATI, NVIDIA) or WLAN drivers directly from the hardware manufacturer's provided packages, **backup your config files in your /etc directory. These drivers may have parts that are installed as kernel modules**. **The upgrade will replace your kernel, but it will not take into account these additional modules as they are untracked by the APT system**. So make sure that you have the driver packages ready after the upgrade, [B]especially for your WLAN card. Once you have upgraded re-run the driver package installation.
[/B][/LIST]That covers just about every possible way of screwing up an upgrade that I can think of. Now go enter gksu "update-manager -c" on your terminal or Run dialog. Cross your fingers and if something fails. Don't panic!

Go here: [http://www.duggmirror.com/linux_unix/Ubuntu_Edgy_Eft_Ugrade_Common_Problems_and_with_their_Solutions/](http://www.duggmirror.com/linux_unix/Ubuntu_Edgy_Eft_Ugrade_Common_Problems_and_with_their_Solutions/)

Hope this helps and good luck to everyone. Especially those who are still having problems.

---

### Post by myname on 2006-10-30
What if typing in gksu update-manager results in an error saying gksu is a bad command?  I don't remember the actual message as I since did a clean wipe/install.  I was running Kubuntu at the time, does kubuntu have "gksu" as a command/program?


--Kevin

---

### Post by angkor on 2006-10-30
> **nimrod_abing said:**
> :-k My apologies...*snip*....still having problems.

*agrees wholeheartedly* ...a bit long but agreeing nonetheless ;)

---

### Post by finite9 on 2006-10-31
> **diff_sky said:**
> I'm glad to read opinions like this.

At first I thought I might want to upgrade to Edgy but realised that I'm more after stability than shiny, wizzyness for my server. I've got a fairly complex software raid5 setup for storage of all my music/photos and (in terms of apps) on the box I've just about got stuff how I like it - so I don't need to take the risk.

This is truly amazing.  How did Canonical manage to F* Up a well tested system of upgrading.  That must have really taken some effort!  Debians system of upgrading has worked flawlessly for many years and thousands of developers daily upgrade to the latest *development* version of Debian without issue, never mind an official release version!

This really is a question of quality testing at Canonical (or lack of).  They have been great so far with breezy and Dapper, but this is going to really harm their reputation...it may knock them off the top spot after this.  I think it is an indication that maybe their six month release cycle is just too optimistic.

---

### Post by knichel on 2006-10-31
I have read many posts on upgrading from dapper to edgy.  If I do upgrade and it does not work properly, can I continue to use dapper or will the upgrade kill dapper on my HD?

Pardon my newbieness... Not familiar with upgrades like this.

--
Mike

---

### Post by mdz on 2006-10-31
> **Akoluth of Nandus said:**
> What does the update-manager do besides automatically changing your sources.list and performing a dist-upgrade?

It does a LOT more than this, including ensuring that any new packages you need are installed, preventing the unexpected removal of metapackages, hinting for tricky dependency situations, etc.

This is THE supported way to upgrade from one Ubuntu release to the next.  If you do it by hand, the correctness of the upgrade can't be guaranteed.

---

### Post by Akoluth of Nandus on 2006-10-31
> **mdz said:**
> It does a LOT more than this, including ensuring that any new packages you need are installed, preventing the unexpected removal of metapackages, hinting for tricky dependency situations, etc.

This is THE supported way to upgrade from one Ubuntu release to the next.  If you do it by hand, the correctness of the upgrade can't be guaranteed.

That means there is no supported way of doing updates in text-mode?
And does it mean that apt is not capable of doing correct dependency resolution? Is aptitude (which is nowadays the recommended Debian-way of upgrading to a new release) a solution?

---

### Post by Bokonon on 2006-10-31
I did both methods and both worked fine.

Server:  Text based aptitude update during one of the RC's.  I broke X, but didn't care because it doesn't need it.  Subsequent updates fixed everything and it is working fine now.  :cool: 

Desktop:  Upgraded via this 'official' method.  No problems and X worked fine from the start.  :p  FWIW, this was a relatively new dapper install with very little unofficial packages installed (i.e. no compiz).  I think the less you deviate from the base install, the easier the upgrade will be.  

If you have a lot of custom stuff installed, try the official way, but have the alternate install disk handy in case you need to reinstall.  Of course backup your important data before trying any of this.

---

### Post by Fritti on 2006-11-01
> **mdz said:**
> It does a LOT more than this, including ensuring that any new packages you need are installed, preventing the unexpected removal of metapackages, hinting for tricky dependency situations, etc.

This is THE supported way to upgrade from one Ubuntu release to the next.  If you do it by hand, the correctness of the upgrade can't be guaranteed.

Then this is the problem. IMHO it's pretty stupid to require a *graphical* program to do things like upgrading. I always thought it was just a frontend for apt-get dist-upgrade, and I still think it should be.

(sidenote: I've upgraded to Edgy without any problems, but I "accidentally" used the update-manager, if circumstances had been different I would have tried dist-upgrade as well)

---

### Post by mdsmedia on 2006-11-01
my root password has always been the same. It's accepted for sudo. Why is it not accepted for the recommended method of upgrading? Is it something I missed along the way?

---

### Post by ajarmoniuk on 2006-11-01
Well..

I have ruined my machine by upgrading to Edgy. And it wouldn't even boot as the grub menu had some strange UID entries in place of device names. Then it wouldn't continue to load at all.

My whole setup was messed up and I had no network and I couldn't fetch all packages I needed to even try to fix the install.

I wanted to install another fresh instance of Ubuntu on the same drive but my failed Edgy partition was on an XFS partition and it was filling up the whole disk. It was then when I learned that, although you can expand an XFS partition, you cannot shrink it.

So I installed Debian on the Ubuntu partition (you can do it without doing the format, unlike in Ubuntu). And only then, after having the network set up properly, only then could I install Ubuntu on it -- by changing the sources.list and messing with the apt preferences file... Hard work, but now I'm on Edgy again. ](*,)

---

### Post by el_itur on 2006-11-01
I upgraded from the oficial method and it went PERFECT. Dapper was imposible to upgrade from breezy, at least form me, but edgy rulz. Great work.

---

### Post by thiebaude on 2006-11-01
When I do a software upgrade to get 6.10 this is what I get, any ideas?Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)

---

### Post by todak on 2006-11-01
Users of Kubuntu 6.06 LTS can upgrade to 6.10 over the internet by following these instructions:

    * NOTE: This procedure upgrades your system over the Internet, which requires a large download of several hundred megabytes.
    * In Konqueror go to /etc/apt, right click on sources.list and choose Actions -> Edit as Root
    * Change all instances of dapper to edgy
    * Launch a console with KMenu -> System -> Konsole
    * In the console run: sudo apt-get update
    * In the console run: sudo apt-get dist-upgrade and follow the prompts to upgrade
    * In the console run: sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal and follow the prompts to install
    * Reboot your computer

(Per the Kubuntu.com site)

---

### Post by regeya on 2006-11-01
EDIT:  In the next post, I vent my spleen.  That feels better, ahh.  Also, I was far too kind in this post.  So nyah.

---

### Post by regeya on 2006-11-02
> **nimrod_abing said:**
> 
I also wanted to point out that **if you want to use Ubuntu as your OS for a mission-critical system, you should use the LTS version** which at this time is **Dapper**. Unless Edgy contains some packages that you absolutely must have and backports are impossible, then by all means upgrade to Edgy.

I mean, would **you** risk your company's mission-critical system just so **you** can have the latest and greatest packages? It appeared that Milambar upgraded a mission critical system to Edgy when it was working fine on Dapper, all without making any backups. I could be wrong but that's what I can gather from the posts he/she made, and I hope he/she was able to get the system back up to a usable state.

I'd accept that statement if you were talking about pre-release Edgy.

Look, the thing about Ubuntu is that you could rely on each six-month release **not** being bleeding-edge.  You could rely on the core to **just work.**  I don't know if you have any connection to the Ubuntu development process, this reeks of **blaming your own incompetence on the user.**

I'll agree that enterprise users should probably have read the website to make sure that they're doing the right thing, and that if they're not smart enough to make the connection between 'Long Term Support', 'LTS', and 'Enterprise Release', they're probably doomed anyway ;) but I've got to say I've had my share of problems with the current LTS release.  

I'll probably be going back to 6.06 since 6.10 is apparently a development release and not a true release, but don't blame users when they can't figure out that 'release' actually means 'ok well it's actually a development release so keep using 6.06 LTS lamers lol'

---

### Post by roblaus on 2006-11-02
Sirs,

I'm done with Ubuntu.

It took me two days to get 6.06 running (including WPA and the damned touchpad) and I am NOT going to repeat the story with 6.10. I tried the aforementioned "official" method with the result that literally nothing worked anymore and I had to do a clean install. 

And what did I get? Network manager is still not there, my wireless card (standard Broadcom) was not recognized and my touchpad again behaves like a virgin at her first date. Let alone all my (now missing) settings I did in the course of the past three months.

I believe there is a LONG LONG way to go before Linux will even get near to become mainstream (at least on the desktop market) and this is not going to happen until developers and sponsors realize that the majority of potential users out there want to USE a computer rather than setting it up.

I will continue using Linux, yes. As server. As database machine and on countless "invisible" devices. But not as OS for my desktops.

rgds
rl

---

### Post by Kieranties on 2006-11-02
I had a few probs with my intial install of edgy, so I went the long way round.

I installed from an official DD.LTS disk and then went to upgrade using the offical "gksu ~" method.

However, once DD had updated itself, the upgrade manager had a button to perform the upgrade.  Clicky clicky and half an hour later one clean build of edgy.

After I used automatix2 (against the grain of some peoples thinking) my system was done and dusted.

The only thing it has not recognised is my wifi card.  However it is non-standard and I haven't tried ndis yet as work was calling.  Guess that will be done tonight8)

---

### Post by rlandrum on 2006-11-02
Maybe I'm the only one, but it looks like most folks are using the network upgrade rather than the CD upgrade.

I work over satellite, which stinks, so I always upgrade from CD.  My last upgrade from 5.10 to 6.06 resulted in missing USB drivers.  No keyboard or mouse functionality.  I did a fresh install of 6.06 to get it working.  Having the CD made that easy.

Yesterday I was planning to go to 6.10.  FF2 is worth the upgrade, I think.  I was optimistic that my previous upgrade failures would have been remedied with 6.10.  After all, 6.06 to 6.10 seems like a smaller (and easier) step than a 5.10 to 6.06 upgrade.

The documentation suggests using update-manager -c.  A little later on though, it says that if I have the CD, I should use a different command, a /cdrom/cdromupgrade.

This asks me if I want to pull down the latest packages via the network.  Nope.  I want to load them from CD.  Then it tells me my system is up-to-date and it exits without doing an install.

I then thought that maybe the sole purpose of /cdrom/cdromupgrade was actually to add the Edgy CD to the sources list, but I couldn't find it in my sources list after I ran it.

I then decided to run the update-manager -c.  But that started downloading packages from the network, which I totally wanted to avoid.  I let it run for a few minutes, but when it couldn't reach a location to download a package, it errored out.

I then tried booting from CD to see if it offered some sort of upgrade function via the menu.  It didn't.

I then tried booting off the hard drive, using apt-cdrom to add the edgy CD to the sources list, and tried running the update manager.  That told me that it couldn't find the CD.

So far, I'm zero for 4.  As far as I can tell, the only way to get packages from the CD to the drive is by doing a fresh install, which I'd really like to avoid.

Any suggestions as to what I might be doing wrong?

Thanks,

Rob

---

### Post by mvo on 2006-11-03
> **rlandrum said:**
> Maybe I'm the only one, but it looks like most folks are using the network upgrade rather than the CD upgrade.


[..]
The documentation suggests using update-manager -c.  A little later on though, it says that if I have the CD, I should use a different command, a /cdrom/cdromupgrade.

This asks me if I want to pull down the latest packages via the network.  Nope.  I want to load them from CD.  Then it tells me my system is up-to-date and it exits without doing an install.


Could you please re-run the upgrade from the cdrom?
gksu "sh /cdrom/cdromugprade"
and then report a bug in launchpad.net against the update-manager package? Please make sure that you include the log files in /var/log/dist-upgrade/. This will help me to identify what went wrong and how it can be fixed.

Thanks,
 Michael

---

### Post by mvo on 2006-11-03
Hello everyone!

I'm very sorry to hear that a people are having trouble with the upgrade. We are analyzing the issues currently and I would really appreciate if people with trouble using the official upgrade method (update-manager -c) report a bug against the update-manager package in launchpad. Please make sure that the logs in /var/log/dist-upgrade are included in the report.

Thanks,
 Michael

---

### Post by BobBlum on 2006-11-04
Two questions:

What is the "-c" switch?  

Does this command require GNOME, or can it be used from KDE as well?

---

### Post by pcolamar on 2006-11-04
I must be lucky.

I upgraded my HP Pavilion AMD64 from Dapper 32 -->> Edgy 32 with the official method. So far no problem at all

Touching  wood !!!  :)

---

### Post by Zentropic on 2006-11-05
Wow. There's a fair amount of anger here, regarding upgrade problems.

Remember people, it's free. I'm willing to bet all the complainers have given  nothing to the FOSS ( free/open source software ) world, and what has it given you?

You get a free OS that, despite its issues, is amazing. You get free updates,  free downloads of the OS, the updates, free forums... And yet you have the audacity to rail against it. :confused:

I'm sorry you had problems. I guess I'm lucky, but I think more people have success than failure. I'm typing right now on a system I just updated to Edgy, just after reading this thread. I started the install and pretty much walked away for 30 minutes. Came back, and 8) 

Thanks again to all the people who dedicate their time, selflessly I migh add, to producing a wonderful alternative to Windows and overpriced Macs.

---

### Post by verk on 2006-11-05
It took me 5 days to make egdy work/install properly. At first, I had to reformat my dapper partition cause I figured that the upgrade path is more troublesome than a clean install. Well in my situation, I was wrong.

1st few tries, I was having the gdm blank screen problem (live installation cd). I searched for every solution I can find but to no avail.
Tried to install dapper again and did a cd-rom upgrade, successful, but with few problems (ati related). But I was pissed that it had to download 600+mb again considering that the files was already in the cd.

Then I learned about the alternate cd, downloaded it, reformat and did a clean install again, successful. But after reboot, nada, I can't login, lots of errors. So inserted back my dapper cd, reformat and reinstalled again, then did a cd-rom upgrade using the alternate cd this time. Files was accessed/upgraded from the cd as it should be, successful. rebooted. but...

errors.

At this stage i was ready to give up. I started downloading fedora. 

Then a miracle happened. I decided to boot on my ubuntu partition again and... it did. No errors. Installed automatix, beryl, etc. with no problems. Now I'm enjoying it.

---

### Post by Lou_Cypher on 2006-11-05
Make sure you are using the Alternate CD, and not the Live CD to make the upgrade (as stated in the [official upgrade page]("https://help.ubuntu.com/community/EdgyUpgrades")).

Best,
LC.

> **rlandrum said:**
> Maybe I'm the only one, but it looks like most folks are using the network upgrade rather than the CD upgrade.

[..snip]

The documentation suggests using update-manager -c.  A little later on though, it says that if I have the CD, I should use a different command, a /cdrom/cdromupgrade.

This asks me if I want to pull down the latest packages via the network.  Nope.  I want to load them from CD.  Then it tells me my system is up-to-date and it exits without doing an install.

[..snip]

Any suggestions as to what I might be doing wrong?

Thanks,

Rob

---

### Post by pwlodarczak on 2006-11-05
Hi there,
I upgraded my Ubuntu 6.06 to edgy and it wouldn't boot anymore. I got a screen with some shapes and colors. Booting in recovery mode got me to a /bin/sh: can't access tty; job control turned off
I'm using kernel 2.6.18.1.
Booting in 2.6.17.11 got me to a Failed to start X server error.
Reconfiguring the x server as sugested didn't help.
Th ndiswrapper doesn't work anymore either. I'm using the 64 bit version. Edgy eft isn't really ready. How can I get back to 6.06?
Thanx

---

### Post by pwlodarczak on 2006-11-05
> **pwlodarczak said:**
> Hi there,
I upgraded my Ubuntu 6.06 to edgy and it wouldn't boot anymore. I got a screen with some shapes and colors. Booting in recovery mode got me to a /bin/sh: can't access tty; job control turned off
I'm using kernel 2.6.18.1.
Booting in 2.6.17.11 got me to a Failed to start X server error.
Reconfiguring the x server as sugested didn't help.
Th ndiswrapper doesn't work anymore either. I'm using the 64 bit version. Edgy eft isn't really ready. How can I get back to 6.06?
Thanx

I got it working using the vesa driver instead of the nvidia driver as suggested in this forum and using kernel 2.6.17.11, 2.6.18.1 doesn't boot.

---

### Post by rlandrum on 2006-11-07
> **Lou_Cypher said:**
> Make sure you are using the Alternate CD, and not the Live CD to make the upgrade (as stated in the [official upgrade page]("https://help.ubuntu.com/community/EdgyUpgrades")).

That language could be so much clearer.  I definitly didn't get the Alternate Install CD.  Capitalization clarify that bit.

I modified the wiki page to reflect my suggestions.  It now reads:

"If you have the edgy Alternate Install CD (not the Live CD), you can save bandwidth by using:"

Thanks again for your help,

Rob

---

### Post by Roobert on 2006-11-07
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.



What if I run your command, and get this error?

```
 warnings.warn("apt API not stable yet", FutureWarning)
```

And the update window just hangs, without ever downloading the upgrade tool. I have to force quit just to close the update manager. I've let it sit there for about 15 minutes with no progress towards the update tool download.

---

### Post by Roobert on 2006-11-07
I should also mention that I am running the update using a virgin /etc/apt/sources.list:

```
deb http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://ca.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

---

### Post by keekaboo on 2006-11-10
I've been trying to update Kubuntu from Dapper to Edgy for the last couple of days. I've tried both of the methods on the official pages and neither works correctly. The first way just does nothing much and the second does an upgrade, that takes hours, and I can no longer boot into graphic mode. I'm faced with a black screen and get into text mode by pressing the 'alt' button. I then have to start the xserver and change run level to graphical with alt-f7. 

 This is obviously totally unnacceptable so can someone please let me know how to revert to Dapper until Edgy is actually ready for release. 

My lesson learned is not to be a guinea pig and wait at least a month after a release until it's actually stable.

---

### Post by Roobert on 2006-11-10
Did you actually manage to connect to the servers when you tried 
```
gksu "update-manager -c"
```? When I do this it just seems to hang and the progress bar never builds. Or does this just take hours and I need to wait for it?

---

### Post by keekaboo on 2006-11-10
> **Zentropic said:**
> Wow. There's a fair amount of anger here, regarding upgrade problems.

**Remember people, it's free**....

That kind of reasoning isn't really good enough. You either produce   quality product or none at all. I'd imagine that the guys at canonical wouldn't agree with your reasoning, that people should accept preoblems just because the software is 'free'. 

Most of the comments I've read so far have been that people are irritated with the install process and the problems they're having but I'm sure they're delighted with the overall experience of Ubuntu/Linux (except for one or two glaring exceptions).

Despite the fact I've had problems I'd still like to say to any Ubuntu developers reading this, thanks and keep up the good work.

---

### Post by cudaman73 on 2006-11-10
To start off, I didn't even know about the

```
$gksu "update-manager -c"
```

method.

I actually had no problems at all upgrading to edgy from dapper.

the edgy discs I had didn't want to work right (problems reading media, bad burner probably), and I only had a 6.06 version to run off of. I installed it, booted it up, changed my /etc/apt/sources.list with

```
$sudo gedit /etc/apt/sources.list
```

and using gedit's find and replace to replace all instances of dapper with edgy.

Then I did the standard 

```
$sudo apt-get update
```

to update my sources, then

```
$sudo apt-get dist-upgrade
```

It ran once, and once it finished, I ran it again, just to be sure I got every package. It found another 20 odd packages that needed upgrading, and, after the second dist-upgrade and a reboot, the only problems I had was the standard nvidia module not working due to a lack of having the nvidia drivers installed for my running kernel (used the drivers from nvidia's website the first time, I just have to go back and reinstall it).

I'm wondering where everyone's problems are coming from, because I had absolutely no problems upgrading to edgy. As a matter of fact, my main box at home (i'm at school right now) is running edgy right now, just without X (as I haven't had time to reinstall the nvidia drivers).

Just thought I'd let you guys know that not everyone's having problems with it.

---

### Post by dhartge on 2006-11-12
> **Lou_Cypher said:**
> Make sure you are using the Alternate CD, and not the Live CD to make the upgrade (as stated in the [official upgrade page]("https://help.ubuntu.com/community/EdgyUpgrades")).

Best,
LC.
Has anyone noticed that contrary to the the instructions on the upgrade page there is no "/cdrom/cdromupgrade" on the alternate CD - at least on the "Ubuntu 6.10 "Edgy Eft" - Alpha i386" that I downloaded from one of the repositories on Saturday 11/10. "cdromupgrade" does appear on the desktop install disk the I downloaded to try to do a complete install after the upgrade errored out with "E: /var/cache/apt/archives/x11-common_1%3a7.1.1ubuntu5_i386.deb: trying to overwrite `/usr/share/man/man5/Xsession.5.gz', which is also in package xinit".

There also appears to be an error in the cdromupgrade script on the desktop cd (the .disk/info file contains "Ubuntu 6.10 "Edgy Eft" - Release i386 (20061025)"). The script expects to find edgy.tar.gz on the cd under dists/stable/main/dist-upgrader/binary-all/ when the file is actually under dists/edgy/main/dist-upgrader/binary-all/. Does anyone test these things?

After editing this post to add the second paragraph I realized that I probably have two different releases. The alternate CD appears to contain an old alpha release and the desktop the latest release. Has the alternate CD been updated to the release and did I just get it from a repository that has not been updated (don't remember which US repository I used)?

I realize this is all "free", but having errors in the install scripts referred to on the official pages doesn't inspire confidence. Repositories that have not been updated in over two weeks after a major release also don't inspire much confidence. The alternate cd files are dated 8/31 and the desktop cd files are dated 10/25. I downloaded both iso files on 11/10.

---

### Post by houstonbofh on 2006-11-13
Wow! After reading all this I can truly say that I have seen more polite bar fights!  That said, I have a lot of comments.

Go to [www.ubuntu.com](www.ubuntu.com) and look at the links for Ubuntu Server...  No Edgy.  Look at the downloads for Ubuntu Desktop.  Makes it fairly clear which is going to be more solid...

As to instant upgrades, Are y'all new or something?  I have known since 1995 that upgrades are never painless.  Test on a spare system, or watch the cannon fodder test it for you.

And a reminder; You had to go out an get this upgrade.  I have been making a lot of money lately from people that came in to the office to find a new browser and a broken system.  MS made IE7 a critical upgrade, and for most it just installed without asking.  **Not an Ubuntu problem.**

But all is not hearts and roses.  Ubuntu communications sucks.  Is edgy stable or not?  Well are you reading the download page or the press release?  How do you upgrade? (Several methods)  Where do you get help?  Until development, marketing and support are all on the same page, this will keep happening.

I still recommend Ubuntu, but I also sell my support services.  If a customer doesn't want that, I tell them to just get a new Dell every 6 months.

---

### Post by vloveya08 on 2006-11-13
I'm trying to upgrade to Edgy from Dapper.  I tried both the "official upgrade method" and the "apt-get" method.  For some reason, both said I was "not authorized" to upgrade!  How do I change this?  I have not edited any of my os aside from installing extra packages (as I'm assuming most people do)  I wanted to try updating now so that when I get my "critical computer" later this year I might be able to fix any problems.  But I'm not quite sure why I'm not authorized to upgrade if this whole thing is free and why my computer is being screwy.

Anyway, if anyone has any suggestions, that'd be great.

---

### Post by Kieranties on 2006-11-14
What was the actual code you used?  You need to sudo to do it.
Just open a terminal and type
```
gksudo update-manager -c
```

---

### Post by vloveya08 on 2006-11-14
I've tried

> $ gksu "update-manager -c"
$ gksu update-manager -c
$ gksudo update-manager -c

all three open up the update manager and I can click on the "upgrade" button to move to Edgy.  But then when it goes to download the files, it stops on the last two and comes up with this error message:

> Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


when I try to follow the instructions to use apt-get I get all the way to editing the sources.list file and come up with this:

> (gedit:2794): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


As I said before, I haven't edited anything in Ubuntu except to add packages so I don't know why I'm not "authorized."

---

### Post by Kieranties on 2006-11-15
Hmmmm

I assume you added those repositories into your sources.list at some point?  It looks like the problem lies with whatever you installed from there.  Incidently, looking at the links, they are breezy repositories but you said you were upgrading from dapper....

I suggest you comment out those two (use a # at the start of the line)

Then try upgrading again.  If you are actually using breezy then you need to update to dapper first, then update to edgy.

---

### Post by julienm on 2006-11-15
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

It is exactly what I have done. And it has put such a mess that now, the only  solution I see is re-install it (windows like finally here for the first time  . In more than ten years never this has happened to me.

Let's give the details :

```
$ gksu "update-manager -c"
```

This has launched the process and it has stopped at a moment with a broken system. Asking me to proceed *apt-get update update* manually then *dist-upgrade*.

I did but the system finally got broken and I had to type *apt-get -f install *which finally couldn't be successful at all.

So I tried to give a solution manually at doing *apt-get install this that those etc ...* but then i was given a list with more troubles than I was supposed to solve.

After (but later) I used *aptitude*. That one made feel more optimistic because he accepted to do some stuffs and install some packages which were looking relevant with the dependancies trouble of the system.

I must say that it was finally not a success because after the process my laptop refused to boot saying it couldn't find the root filesystem, this just after complaning it couldn't find the file **mdadm.conf**. Actually this shouldn't be a problem on a laptop because nobody is using raid filesystem on laptops. Are some ?

OK. At that moment it was really getting on my nerves. I took off the hard disk and put in an usb box to look in it with my desktop. Everything was looking ok, I couldn't understand why it couldn't find the root filesystem. Anyway I mounted all the partitions of my laptop's disk above the root filesystem and did a chroot. Re-launch *aptitude* who asked me to proceed a *dpkg --configure -a* : I did and it didn't help.

Right, I have copied the .iso file on a partition and I will reconfigure grub to boot with the iso file directly from it, stored on the hd.
If some are interested by this, I wrote an HOWTO here : [//http://julien.mary.free.fr/blog/?p=33]("//http://julien.mary.free.fr/blog/?p=33")

I have to do like this because my dvd player is dead and my computer can't boot from networtk.

Here was my story at upgrading my laptop from dapper to edgy.

---

### Post by dahlek on 2006-11-15
> **todak said:**
> Users of Kubuntu 6.06 LTS can upgrade to 6.10 over the internet by following these instructions:

    * NOTE: This procedure upgrades your system over the Internet, which requires a large download of several hundred megabytes.
    * In Konqueror go to /etc/apt, right click on sources.list and choose Actions -> Edit as Root
    * Change all instances of dapper to edgy
    * Launch a console with KMenu -> System -> Konsole
    * In the console run: sudo apt-get update
    * In the console run: sudo apt-get dist-upgrade and follow the prompts to upgrade
    * In the console run: sudo apt-get install kubuntu-desktop python-qt3 python-kde3 ubuntu-minimal and follow the prompts to install
    * Reboot your computer

(Per the Kubuntu.com site)

That lead to my current system, which is a MESS and which is about to be wiped. I STRONGLY encourage anyone considering this method to just roll up their sleeves, back up their data/home folder and start from scratch or just stick with 6.06!

Every day I keep finding new issues and this system is more unstable than any version of Windows I've used, and I haven't been a very active Windows user since 98, so that's really saying something, alas...

I just tried to write a DVD ISO image only to have k3b crash complaining about libqt-mt.so.3 and others. The game Boson crashed the other day also complaining about the same library - I blamed it on my half-arse graphics chipset (savage8). A non-working K3b is simply unacceptable to me.

Konq often crashes when I close file manager windows. Every so often, a KDE app that attempts to make a sound will grind my system to a halt complaining about ARTS overloading my CPU - the thing is, I have this time, like I always do in KDE, turned OFF ARTS, and as far as I can tell, it does not appear to be running. KDE also seems to randomly log me out if left alone for long periods. Usually it doesn't, sometimes it does - very unpredictable.

I appreciate the hard work the Ubuntu crew put into their distro, but after reading about the very many issues with 6.10, I think a message from the top is in order, something along the lines of an apology, a recognition of a major goof, a warning for folks to remain at 6.06 and an announcement of an upcoming 6.10.1 which will fix most of these issues. Surely folks can't be expected to wait 6 months for the next official release?

I give up trying to resolve these issues one by one - many of the posts here at the forum intersecting my problems are left unanswered/unresolved.

I'll continue to recommend 6.06 but will not recommend 6.10 as it stands now. Every major distro has had issues like this - I recall that Fedora was known as a bug-house several versions ago, and I also recall reading that a recent OpenSUSE was released with a non-working software installer system. They've come through just fine, and I expect Ubuntu will do the same - the momentum seems to be with this distro.

---

### Post by DarkW0lf on 2006-11-15
What is this ?

"sudo update-manager -c"  does not update, I get the error regarding the API not being stable and then update manager loads telling me that my system is up to date. What is uyp with the -c switch, I don't want to download the updated packages from repositories I want to use the ones on the CD. There are packages on the CD right ?

The official method says to use the Alternate CD. Why, I just spent two weeks or so downloading the Live CD on dialup and it's the wrong one ? Why, I used the Live CD last time to install Dapper. But that's the thing I "installed" not "upgraded".

Do I need to spend another two weeks downloading the Alternate ?
I don't care if the OS is free or not, this is a complete and total debacle. No communication, no clear instruction and nothing works as you are told it does. Is anyone actually cheking up on this. There is no official statement that Edgy is a development or beta release. The only people who state as such are forum staff. So the forum says one thing and Canocial another.

Somebody somewhere clear this up and let us know what it is we are supposed to do. Like I said FOSS has nothing to do with this, it is piss poor planning 100 % and please stop using YAUA's (Yet Another Useless Acronym).

---

### Post by mdwatt on 2006-11-16
withdrawn -- fixed.

---

### Post by HushTheVoices on 2006-11-17
OK, I think through my own inexperience I've managed to bork the install :(  But I'm really hoping someone here can tell me otherwise

I VNC'd in to my mother-in-law's PC and followed the gksu "update-manager -c" command from terminal where it then started the upgrade.  After downloading the files it then began to install them (so far, so good).  Unfortunately after a few minutes and the orange bar slowly creeping along it ground to a halt with they keyboard no longer working - the mouse and clock worked, but not a lot else.

Twitching nervously, I told my her to do a hard reboot, hoping any praying that it hadn't screwed anything up.  Thankfully, it booted fine in to the old 6.06 Unbuntu.  Phew!

OK, next step I noticed the update manager icon on the top bar was grey and it was saying it was 'working', but as there was no disk activity I clicked on it.  Can't remember what the message was exactly, but it said something along the lines of there was a problem with the files and these must be fixed before it can continue.  It instructed my to run the Synaptic Package manager where it said I had 30 broken files and to remove them.  I did this and then went back to the update manager and the installation continued.  I have a sneaky suspicion this is where I went wrong.  Still VNC'd in to her machine I monitored the installation.

It got to almost the end (gnome-utils I believe) when it froze again.  Somehow knowing this wasn't to end well, I disconnected and got her to do a hard reboot and waited for the errors to come up.  I need to actually go and see the errors, but I believe it's to do with the x-server.

Unfortunately there is no router by rather a USB ADSL modem, so downloading the files via the command line is possible...or should I say I have no idea how to do it if it is.

So apologies for the lack of specifics, but does anyone have any idea's where to start?


[B]Fixed:
Followed the instructions in this thread [http://ubuntuforums.org/showthread.php?t=187177](http://ubuntuforums.org/showthread.php?t=187177) - rebooted and everything worked like a dream.  Only slight snag is that the screen refresh is a little off and I can't seem to change it within Ubuntu or work out how to update the graphics driver.  Personally I'm just glad it's working again though.[/B]

---

### Post by DarkW0lf on 2006-11-17
Hush - 

you don't specify what type of PC your MIL has but I wouldn't use up any further bandwidth with a VNC connection even if she has ADSL. You said it was a several hundred MB download, let it do it's thing.

Which of course leads me to my situation. I don't want to do a net upgrade, that why I downloaded the CD iso to begin with. I want to avoid the HUGE download issue becasue I am on dialup, yet had to download a cd iso anyway.

What is wrong with the liveCD, what is up with the API not stable issue, and is there any techs on this board at all ?

---

### Post by HushTheVoices on 2006-11-19
Sorry Dark, it's a home made PC, but if you look at my thread I managed to fixed the problem.  Thanks anyway.

Regarding your problem, I saw this regarding the LiveCD and API, but it was back in May and which referred to the 6.06 version (I think) - [http://ubuntuforums.org/showthread.php?t=177027](http://ubuntuforums.org/showthread.php?t=177027).

The only other thing I could think of was this, but it's probably way off base - [http://ubuntuforums.org/showthread.php?t=290655](http://ubuntuforums.org/showthread.php?t=290655)

---

### Post by cantormath on 2006-11-19
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

Think that is for kubuntu.....no? in ubuntu.....I dont do it that way.

---

### Post by superba on 2006-11-19
> **cantormath said:**
> Think that is for kubuntu.....no? in ubuntu.....I dont do it that way.

I just used the official upgrade method to upgrade from a flakey dapper drake, v6.06, to edgy eft.  In v6.06 I was unable to access my network no matter what I tried.  When I invoked <$gksu "update-manager -c">, system took over, accessed the network, downloaded about 1,000 files, and did the entire install without a single hitch.:D 

I was using ubuntu, not kubuntu.

Cheers!

---

### Post by nfs510 on 2006-11-20
I have also experienced problems upgrading to Edgy from Daper. If this continues, Unbutu will be a lost cause. 

This is expected since the product is free and resources are limited. Solutions will appear however, if we can wait.

Similar or even worse scenarios will appear in the future. May I suggest Ubuntu to provide an "unistall" or "restore" application so that for those who ventured and got into trouble can restore to their previous system easily, until solutions are found.

---

### Post by newagelink on 2006-11-20
> **igorzolnikov said:**
> gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

Software Updates have status: "Your system is up-to-date".This happened to me, too.

I downloaded the ISO, verified the hash, burnt it to CD-R, booted from it, tried it for 1.5 hours, decided I liked it -- it works so much better with my monitor!! -- so I decided to try to upgrade. At first I double-clicked "Install" on the desktop, but by the time I go to the "manually edit partition tables" I realized this probably wasn't the way to go.

So I go to ubuntu.com, and find my way to [where it says to use that command]("https://wiki.ubuntu.com/EdgyReleaseNotes"). So I restart w/o disc in Ubuntu 6.06 and Alt+F2, copy/paste, "run in terminal" ... and yeah, see attached screenshots.
Copy/pasted from terminal:
```

  warnings.warn("apt API not stable yet", FutureWarning)
```
I guess I'll continue reading through this thread -- I was on page three when I decided to respond -- to see if this has already been addressed and resolved. 

edit: in the Software Updates window there's a button 'Upgrade' for me to click, with the message "New distrobution release 6.10 is available" but I'm going to not do that, given the error I got and the problems I see others having.

Also, [I searched]("http://ubuntuforums.org/search.php?searchid=9968615") and got a ton of results; I guess I'll read through those, rather than asking an already-asked question. Maybe I should try ```
sudo apt-get update
``` like [that person suggested]("http://ubuntuforums.org/showpost.php?p=1726476&postcount=4").
```
daniel@daniel-laptop:~$ sudo apt-get update
Password:
Ign http://wine.budgetdedicated.com breezy Release.gpg
Ign http://wine.budgetdedicated.com dapper Release.gpg
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://security.ubuntu.com dapper-security Release.gpg [191B]
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Hit http://archive.ubuntu.com dapper Release
Get:4 http://security.ubuntu.com dapper-security Release [30.9kB]
Hit http://archive.canonical.com dapper-commercial Release
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://wine.budgetdedicated.com breezy Release
Hit http://archive.canonical.com dapper-commercial/main Packages
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://wine.budgetdedicated.com dapper Release
Hit http://archive.ubuntu.com dapper/restricted Packages
Ign http://wine.budgetdedicated.com breezy/main Packages
Ign http://wine.budgetdedicated.com dapper/main Packages
Hit http://wine.budgetdedicated.com breezy/main Packages
Hit http://wine.budgetdedicated.com dapper/main Packages
Get:5 http://security.ubuntu.com dapper-security/main Packages [80.5kB]
Get:6 http://security.ubuntu.com dapper-security/restricted Packages [6460B]
Get:7 http://security.ubuntu.com dapper-security/main Sources [14.9kB]
Get:8 http://security.ubuntu.com dapper-security/restricted Sources [968B]
Get:9 http://security.ubuntu.com dapper-security/multiverse Packages [2782B]
Get:10 http://security.ubuntu.com dapper-security/universe Packages [41.5kB]
Err http://us.archive.ubuntu.com dapper Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed  out
Err http://us.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed  out
Fetched 178kB in 8m0s (371B/s)
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg  Co uld not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection timed out
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release .gpg  Could not connect to us.archive.ubuntu.com:80 (146.137.96.7), connection t imed out
Reading package lists... Done
W: Some index files failed to download, they have been ignored, or old ones used  instead.
daniel@daniel-laptop:~$
```
If anyone can help me out (and save me a bunch of time sifting through threads), I'd really appreciate it. I'm going to try [deepwave's advice]("http://ubuntuforums.org/showpost.php?p=1749713&postcount=2").

---

### Post by barbz127 on 2006-11-21
Thought id throw this in.

After reading this thread i went through and set off on the official upgrade and went to bed.

Woke up this morning, still in 6.06, package manager had some problems with broken dependancies and missing packages - hey a restart will fix this!!

next thing turns up file system errors so i run through this in maintenance mode and tell it to fix all its problems.

reboot again

next time round its running, hardware drivers initialising failed, so no xwindows - no biggie - try apt-get - no go but tells me to go dpkg --configure -a ....20 minutes later its all good to go

reboot again

gets to my log in screen, im in

stop acpid and firestarter apt-get update and install -f....alll good!


reboot again to make sure

package manger tells me it didnt do the update theres still 66 or so packages left so let it download and its back up tested, run all good!



so i guess theres no point going off at someone else, be patient at that the end of the day it will work itself out. Nothing is ever painless!!

---

### Post by newagelink on 2006-11-22
A restart didn't fix my errors when trying to apt-get or with the package manager thing (if I'm thinking of the right stuff -- see the images I attached in my previous post.)

---

### Post by bjacquet on 2006-11-22
I've just completed a ```
$ gksu "update-manager -c"
``` with no problem at all. :KS

---

### Post by Blis on 2006-11-24
Just another "It all worked well" comment. :)

---

### Post by melkor12 on 2006-11-27
hi,
I was going to upgrade to edgy today but when I opened up the update manager 
I tried to check for updates I get the following error: 

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


Anyone knows whats going on?

thanks in advance

---

### Post by tomane on 2006-11-27
Hi,
I searched a bit but couldn't find any clear info on this. I have an ubuntu 5.10 server running on a headless machine. I want to upgrade it to 6.06. The only way I access it is through ssh. Is there any upgrade method that I can use in the command line instead of update-manager but with the same reliability? It is running an ssh and samba server, and I wouldn't want any of these to break after the upgrade because we rely heavily on them in the office.

Do you have any advise on them best method to perform the upgrade on this machine?

cheers,
--to

---

### Post by Kieranties on 2006-11-28
> **tomane said:**
> Hi,
I searched a bit but couldn't find any clear info on this. I have an ubuntu 5.10 server running on a headless machine. I want to upgrade it to 6.06. The only way I access it is through ssh. Is there any upgrade method that I can use in the command line instead of update-manager but with the same reliability? It is running an ssh and samba server, and I wouldn't want any of these to break after the upgrade because we rely heavily on them in the office.

Do you have any advise on them best method to perform the upgrade on this machine?

cheers,
--to

```
sudo aptitude update
sudo aptitude dist-upgrade
```

Should do the trick for an update on the server.  Have a look at the man page for aptitude.  It provides some better functionality then apt-get if something breaks

---

### Post by melkor12 on 2006-11-28
> **melkor12 said:**
> hi,
I was going to upgrade to edgy today but when I opened up the update manager 
I tried to check for updates I get the following error: 

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

[http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:](http://archive.ubuntu.com/ubuntu/dists/dapper-updates/universe/binary-i386/Packages.gz:) Sub-process gzip returned an error code (1)


Anyone knows whats going on?

thanks in advance

I got stuck and can't even do a normal update...
anyone?

---

### Post by PDuffman004 on 2006-12-06
Does this have a similar effect to reinstalling? Obviously the system is being upgraded to 6.10, but other than that does it have the same effect as reinstalling?

If not, I would I go about reinstalling 6.10?

---

### Post by nivek1385 on 2006-12-08
Okay, I've had a bit of success and a bit of failure upgrading to Edgy.  First, let me explain the number of systems I have *ubuntu on.  I have Ubuntu Dapper installed on my business server which I use for webhosting, DNS, email, samba server, etc. (I still have X setup on that machine).  That system is a P2-233 MHz with ~256 MB RAM.  I also have my personal computer set up with a dual boot of WinXP and Ubuntu (was Dapper, now Edgy).  This computer is a P4-3.0Ghz with 1 GB RAM.  Also, under WinXP, I have an ubuntu VMWare VM (dapper, but was mid-update when I has it open last...so, once I open it, it should continue upgrading...I hope).  Finally, I have my sister's Edubuntu\Xubuntu combo install (dapper) on a Celeron 500 MHz with 196? MB RAM (greater than 128, but if I remember, it's less than 256).

The first attempt at upgrading to edgy was with the VM, but when it said it was going to take ~22 hours to download all the updates, I decided to continue it at another time (I needed to do something else on that machine that night).  I have yet to attempt to continue this upgrade.

Attempt number two was with my HD install on the P4.  Prior to attempting the upgrade I had to get my wireless card working (had not yet attempted to get it or my TV tuner card working under *ubuntu, after a few hours, I had both working).  I used "update-manager -c" with either sudo or gksudo (don't remember which).  At first, I thought that this worked perfectly.  Upon later checking, though, I realized that all was not perfect.  For some reason, Edgy did not recognize my swap partition until I installed GParted and reformatted it and rebooted.  Other than that, I have not noticed anything else not working.

Now...attempts three through...lost count was with my sister's computer.  First, I tried using the "update-manager -c" method.  It failed giving the error "Fork failed" followed by another error (I think it was along the lines of "InstallPackages() failed" but don't recall the exact error).  So, I tried the apt-get method.  This, too failed, giving the fork error, but not the second error.  I then tried to go through Synaptic, but I had several broken packages  I had to fix beforehand.  After the broken packages, I tried to "Mark all Upgrades" and apply.  I received the same two errors that update-manager gave.  I have since tried the various methods repeatedly to no avail.  I had the following packages installed from debs I created from source using checkinstall or straight from source: SeaMonkey v1.0.5 or v1.0.6 (I hate Firefox and TBird), Gambas Dev v1.9.45, the latest Flash Player for linux, and the several packages in order to link to a Texas Instruments calculator.  Now, the system is inn a semi-usable state, with most things working.  Things that keep crashing are Thunar, a program written in Gambas2 (aka v1.9.45) that worked before the upgrade attempts, a few other programs, and when the screensaver locks the screen, it will not recognize any password as correct (but command-line and gksudo both recognize passwords correctly).

I wasn't planning on upgrading the server to Edgy as I thought it best to stick with the LTS version for that, but the others I would like to upgrade.  Any help would be greatly appreciated.  As for Edgy (once installed and working), so far it seems like a nice improvement on the already-well-written Dapper.

Nivek

---

### Post by jtwadsworth on 2006-12-10
I tried the above recommendations to upgrade to Edgy from Dapper, and it goes through everything with no errors, but I am still running Dapper according to Linux even after a reboot.

jtw

---

### Post by nivek1385 on 2006-12-12
Well, after many headaches and long nights, I was finally able to get my sister's system to upgrade.  Well, at least everything is working now and it looks like it's different.  I've not checked to see if it thinks it's Dapper or Edgy yet, but it's working again.  I had to change the repos in sources.list to the Canadian servers (the main servers rarely work for me and the US ones failed...I couldn't remember which repos were the default ones, so I just grabbed someone else's from the net...it happened to be a Canadian and I didn't bother changing them to US).  I then did a series of ~8-10 "sudo apt-get update && sudo apt-get dist-upgrade" followed by a "sudo apt-get -f install" and a "sudo dpkg --configure -a"...after that, I checked to make sure that x was still installed as well as xubuntu-desktop then rebooted.

Hope this might help others.

Valete,
Kevin

---

### Post by b3tzi on 2006-12-12
It worked fine for me, the only problem is that I had a Kernel Panic with the 2.6.17 Kernel. 
That's why I'm using the Ubuntu 6.10 with a 2.6.15 Kernel. ;)

---

### Post by A_608 on 2006-12-12
Here's what I did.

First, downloaded and burned the image for Edgy 6.10 alternate version.
Second, ran this command,
 
gksu sh /cdrom/cdromupgrade

This worked for me though my machine needed 1.5 hours to install. I did not try to start the process and leave thinking the installation would occur automatically. Also, I did not tinker with 6.06. I did not install programs apart from Ubuntu servers except for printer drivers for my Brother 2040 printer. After the upgrade the printer works. I plan to install vmware server and that's about it for stuff I need. Being a newbie, I did not see the need to tinker. I plan to bookmark Linuxcommand.com and learn my way around.

---

### Post by mgortgan on 2006-12-14
Has anyone else had problems with incredibly slow downloads?  I'm currently upgrading from dapper to edgy using the 'official' method and it's been downloading files for over 13 hours on a 384k DSL connection (currently at 1219 of 1229 files).  Download rates vary from 0 to about 23k/s.  I usually download at about 41k/s.  Had I known the server might be this slow I would've just downloaded the iso and done a fresh install.  Re-doing my whole system would have been faster :(

---

### Post by mgortgan on 2006-12-14
Well, at least when it finally downloaded everything the upgrade went smoothly and everything seems to work ;)

---

### Post by TimelessRogue on 2006-12-14
'Official' or not, here's the story of my upgrade to Edgy from the Dapper using both recommended methods and one that is different and just a little bit new-ish (also on another posting):

Well okay then ... this has to be one of the easiest upgrades I've ever had fun with ... aside from that unpleasant experience a few days ago, that is ... and with no loss of data!

I'm now working with Edgy on my HP Pavilion n5000 laptop after upgrading from the Dapper last evening. I had previously tried the recommended methods of 'sudo update-manager -c' and 'sudo sh /cdrom/cdromupgrade' from a 'terminal' with a downloaded/burned copy of the 'alternate' i386 iso with results that, while not exactly disastrous 'cuz I didn't lose any data, were somewhat way the other side of satisfactory in that I ended up reinstalling the Dapper both times. Not a big deal really, just a little aggravating ...

This time, while in the graphical mode of the Dapper and being in something of a curious mood, I loaded the Edgy 'alternate' cd, opened the folder and double-clicked on the 'cdromupgrade' file. Lo and behold! It opened on screen and allowed me to do the complete upgrade from Dapper to Edgy on screen and in graphic mode. Edgy accomplished the entire upgrade, including downloading newer versions of some files over my DSL internet connection. in a matter of just a few hours ... basicly unattended once it got started. I then used Synaptic to check for updates and that was it.

All is well and everything is functioning ... except for my Linksys wireless, that is. And because there was no reformatting involved, there was no loss of data ... including my various custom settings (such as fonts, network settings, etc) as well as my Firefox bookmarks!

I ask you: How much easier could it be? And yet no one has mentioned managing the update in this manner. Am I the first?

Anyway ... there you have it: the story of my 'Edgy Upgrade' ,,,

---

### Post by andry1 on 2006-12-17
after experiencing some problems to upgrade my ubuntu dapper to edgy, i finally concluded the upgrade processes.. the system asked me to reboot, and so i did... when starting the computer, a CRC error came up, and the system halted! i can't pass through that point, except if i reset the computer and chose to boot with and old version of kernel. but when i log into the session, though i can open apps and all, the apps don't stay in the panel so i can switch between them.
any ideas? :confused:

---

### Post by raul_ on 2006-12-17
What problems have you experienced? Does the panel appear at all? if you minimize the applications they simply disappear?

---

### Post by houstonbofh on 2006-12-17
> **andry1 said:**
> after experiencing some problems to upgrade my ubuntu dapper to edgy, i finally concluded the upgrade processes.. the system asked me to reboot, and so i did... when starting the computer, a CRC error came up, and the system halted! i can't pass through that point, except if i reset the computer and chose to boot with and old version of kernel. but when i log into the session, though i can open apps and all, the apps don't stay in the panel so i can switch between them.
any ideas? :confused:
Keep checking for updates.  You got borked halfway through.

---

### Post by andry1 on 2006-12-17
yes, the panel appears and if i minimize the apps they simply disappear.. i can't even switch with alt+tab.. 
and trying to use update manager or synaptic, when my password is asked, it says invalid password :-?
and trying in the terminal to change user, the password is valid..

---

### Post by clw on 2006-12-19
> **nocturn said:**
> ... The reason is that Dapper is LTS, so by default the upgrade to Edgy is not recommended.  Only for those who are willing to track a semi-stable version.

> **Bigglez said:**
> ... For all intents and appearances,6.10 is the update to 6.06.
Is there going to be a stable update from 6.06 in two years time to 8.01 or something like that? ...

I know this is from a long time ago, but please could someone (perhaps Nocturn??) answer Biggles (very reasonable) question?

If I could be sure (from an official source), that when the LTS for 6.06 runs out, that there will be a supported upgrade method from 6.06 to the new LTS version, I would have no interest in upgrading to 6.10. What I fear is that when 6.06 LTS runs out the only upgrade method to the new LTS version will be from 6.10/7.99/8.01 or whatever.

TIA

---

### Post by golem3 on 2006-12-19
I just wiped my hard drive and installed Edgy...really liking it so far.

---

### Post by TimelessRogue on 2006-12-21
Well, I've now 'upgraded' my 'me-built' base station (specs if you need 'em, but suffice it to say that it is not just a 'plain vanilla' set-up) to Edgy after installing a couple of new hard-drives to the RAID array plus a new DVD/CD RW drive and reflashing the bios (to accomodate the larger drives) ... and it went smoothly and painlessly last evening in just a couple of hours with the 'official method' of using the 'alternate' CD.  Immediately after upgrading, I was online (Linksys wireless, by the way) upgrading via Synaptic ... all went well with that also.  And Ubuntu recognized ALL of my miscellaneous hardware with no problems encountered ...  so far ...

So to say that I am pleased with Ubuntu would be putting it mildly ... this has got to be one of the easiest installing/upgrading and smoothest operating systems I've come across through the years (and there are a lot of them, believe me!)

---

### Post by clw on 2006-12-21
> **clw said:**
> I know this is from a long time ago, but please could someone (perhaps Nocturn??) answer Biggles (very reasonable) question?

If I could be sure (from an official source), that when the LTS for 6.06 runs out, that there will be a supported upgrade method from 6.06 to the new LTS version, I would have no interest in upgrading to 6.10. What I fear is that when 6.06 LTS runs out the only upgrade method to the new LTS version will be from 6.10/7.99/8.01 or whatever.

TIA

Ok to answer my own question. 
From [http://www.ubuntu.com/support/faq]("http://www.ubuntu.com/support/faq") (which, I guess, counts as an official source):
"**What is the current stable release?**
*The current stable release is 6.10, sometimes referred to by its development name of Edgy Eft.* "

So this would seem to be duff info:
> **nocturn said:**
> ...The reason is that Dapper is LTS, so by default the upgrade to Edgy is not recommended.  Only for those who are willing to track a semi-stable version.


And to answer Bigglez question (again from the official FAQ):
> **Bigglez said:**
> ...Is there going to be a stable update from 6.06 in two years time to 8.01 or something like that?...

"**Once I have installed Ubuntu, will I be able to upgrade to the next release?**
*We fully support upgrades from one release to the next. However, we do not support upgrades that skip a release. Thus we support upgrades from 5.10 to 6.06, but not from 5.04 to 6.06 unless you first upgrade to 5.10.*"

---

### Post by Bigglez on 2006-12-27
> **clw said:**
> 
And to answer Bigglez question (again from the official FAQ):
"**Once I have installed Ubuntu, will I be able to upgrade to the next release?**
*We fully support upgrades from one release to the next. However, we do not support upgrades that skip a release. Thus we support upgrades from 5.10 to 6.06, but not from 5.04 to 6.06 unless you first upgrade to 5.10.*"

Right, I knew as much. It shows that the stuff others are saying on pages in this thread about people somehow *knowing*, as if by psychic email or something, that "edgy" is an unstable and risky update are all wrong. Edgy is merely an upgrade and if you want to move forward in a natural way from Dapper you have to pass through Edgy.

Still haven't had time to suffer an upgrade yet. When I do, it'll be a re-install.

Pity this thread is now being spammed by the lowlifes flogging drugs and dating sites - time to unsub I think.

---

### Post by Budnoser on 2006-12-28
[1 teen chats](http://1-teen-chats-134f1.live-adult-chat.org/) 
[adult baby chat](http://adult-baby-chat-134f1.sexy-chat-rooms.org/) 
[adult cam chat](http://adult-cam-chat-134f1.flirt-online.org/) 
[adult cam chat web](http://adult-cam-chat-web-134f1.swinger-sex-chat.org/) 
[adult chat cam](http://adult-chat-cam-134f1.live-adult-chat.info/) 
[adult chat flirt](http://adult-chat-flirt-134f1.adult-chat-world.info/)

---

### Post by DarkW0lf on 2006-12-29
I have the Alternate Install CD but now have a problem.

The script didn't work unless I ran it form gksudo (why gk isn't it a shell script ?)
Then it wouldn't work because it couldn't find the meta-package (well duh, I removed it and some other unwanted apps). And wanted to reinstall the whole package and the apps I removed, which I don't want that's why I removed them. When I used synaptic to update my existing packages from the CD (which worked successfully from Breezy to Dapper) now X is all borked.

I have tried to run the reconfigure from the shell but it won't recognize my password. I think something is wrong with the shell because it is slow to respond to my keystrokes.

Okay so now what, keep trying to use dpkg-reconfigure or what ?

---

### Post by mhoskins on 2006-12-30
I used the official upgrade method - downloaded 1208 packages (not a typo) to a 6.06 updated system. The update to 'courier-authlib' failed. This was apparently not good. I have a half updated machine with a corrupted packages list. I ran 'apt-get install -f' and that appears to have corrected the list, but the library still will not install.

I'm stuck. This is my wife's computer, so I'm not really popular right now.

HELP!

---

### Post by mhoskins on 2006-12-31
More info about what's happening:

mike@java2:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  courier-authlib-userdb: Depends: courier-authlib but it is not installed
                          Depends: courier-authlib (>= 0.58) but it is not installed
  courier-base: Depends: courier-authlib but it is not installed
E: Unmet dependencies. Try using -f.

mike@java2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
8 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
mike@java2:~$ Errors were encountered while processing:
 courier-authdaemon

I was hoping the -f would just jam these two packages in and let me move on.  ](*,) 

Any help or idea on how to get past this would be appreciated. I'm not the best with apt-get. I know several other distributions pretty well, but this is my first real adventure with apt-get.

TIA and Happy New Year

---

### Post by mhoskins on 2006-12-31
I'm still here banging away at this but I seem to be completely hung up on this courier-authdaemon package. Nothing I've tried has been able to stop the complaints about this package being in a bad state:

```

I decided to get a bit less delicate with the problem and removed about 8 packages all associated with "courier" and it worked - all except courier-authdaemon. 

$ sudo apt-get -f -t 6.10 remove courier-authdaemon courier-base courier-authlib-userdb courier-imap courier-pop courier-ssl courier-imap-ssl courier-pop-ssl
Reading package lists... Done
Building dependency tree... Done
The following packages were automatically installed and are no longer required:
  courier-imap courier-imap-ssl courier-pop courier-ssl courier-base
  courier-authlib-userdb courier-authdaemon courier-pop-ssl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  courier-authdaemon courier-authlib-userdb courier-base courier-imap
  courier-imap-ssl courier-pop courier-pop-ssl courier-ssl
0 upgraded, 0 newly installed, 8 to remove and 2 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3695kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 126653 files and directories currently installed.)
Removing courier-pop-ssl ...
Removing courier-imap-ssl ...
Removing courier-ssl ...
Removing courier-pop ...
Removing courier-imap ...
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
mike@java2:~$ Removing courier-base ...

```

So I tried to reinstall the package...

```

$ sudo apt-get -f -t 6.10 remove courier-authdaemon courier-base courier-authlib-userdb courier-imap courier-pop courier-ssl courier-imap-ssl courier-pop-ssl
Reading package lists... Done
Building dependency tree... Done
The following packages were automatically installed and are no longer required:
  courier-imap courier-imap-ssl courier-pop courier-ssl courier-base
  courier-authlib-userdb courier-authdaemon courier-pop-ssl
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  courier-authdaemon courier-authlib-userdb courier-base courier-imap
  courier-imap-ssl courier-pop courier-pop-ssl courier-ssl
0 upgraded, 0 newly installed, 8 to remove and 2 not upgraded.
8 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3695kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 126653 files and directories currently installed.)
Removing courier-pop-ssl ...
Removing courier-imap-ssl ...
Removing courier-ssl ...
Removing courier-pop ...
Removing courier-imap ...
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
mike@java2:~$ Removing courier-base ...

```

I thought I was getting somewhere about now - still the problem with this one package. So I attempt to reinstall it :

```

mike@java2:~$ sudo apt-get -f install courier-authdaemon
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

mike@java2:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of courier-authlib-userdb:
 courier-authlib-userdb depends on courier-authlib; however:
  Package courier-authlib is not installed.
 courier-authlib-userdb depends on courier-authlib (>= 0.58); however:
  Package courier-authlib is not installed.
dpkg: error processing courier-authlib-userdb (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 courier-authlib-userdb

mike@java2:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  courier-authdaemon courier-authlib
The following NEW packages will be installed:
  courier-authlib
The following packages will be upgraded:
  courier-authdaemon
1 upgraded, 1 newly installed, 0 to remove and 2 not upgraded.
3 not fully installed or removed.
Need to get 0B/83.9kB of archives.
After unpacking 164kB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Reading changelogs... Done
dpkg: error processing courier-authdaemon (--remove):
 Package is in a very bad inconsistent state - you should
 reinstall it before attempting a removal.
terminate called after throwing an instance of 'std::logic_error'
  what():  basic_string::_S_construct NULL not valid
Aborted
mike@java2:~$ Errors were encountered while processing:
 courier-authdaemon

```

And I **finally** note here that apt-get is trying to remove the package before it is installed again, when the request is to install the package again before it is removed.  I tried the upgrade command with apt-get and got the same result.

Poking around I found **dkg**:

```

$ sudo dpkg -i courier-authdaemon
dpkg: error processing courier-authdaemon (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 courier-authdaemon

```

I'm beginning to think I'm on a wild goose chase. Is there a way to simply remove this package name from a list somewhere and move on?

TIA

---

### Post by reb68 on 2007-01-01
I tried the OFFICIAL upgrade method 2 times. I have ver. 6.0.6 and did the gksu "update-manager -c" I do not get the notice that an update is available or ask to install it. What am I doing wrong?

---

### Post by dewarrior on 2007-01-03
Spam.

---

### Post by lovedeva on 2007-01-03
Spam.

---

### Post by loveinlove on 2007-01-05
Hey, really cool. 
See [phentermine](http://phentermine.alldating.org/phentermine.htm). 
Test <a href="http://phentermine.alldating.org/phentermine.htm">phentermine</a> online. 
Bye.

---

### Post by saphil on 2007-01-06
I run the Xfce desktop most of the time, however, sometimes the K desktop and sometimes Gnome.  I wasn't sure what flavour of Ubuntu I was running, since I use everything.  So, having a bit of free time, I ran the "Official Upgrade" line.  It is very simple and was soon showing me the status of my upgrade, as over 1600 new packages were downloaded to my box.  It was entertaining to see the predicted download time jump about from 3 hours to 45 days and more (Mathematically dependent upon download speed - checked every few seconds).  

**I got the predicted xubuntu fatal error.  **

When I got done feeding the chickens this morning, I came and attempted to log in at the screensaver security dialog.  It told me that my password was wrong.  Oh Fun!!!  I rebooted the machine.

Could not start at all with the new kernel from boot, so I hit [esc] during the post procedure and chose the 2.6.15-386 kernel.  This booted linux, but the xorg functions failed and the gui was disabled (This just looked like a flashing insert cursor at the top left of the screen).

I knew that some amount of the 1600 files being downloaded had probably done so.  240 had come by the time I went to sleep last night.

I used [Ctrl] + [Alt] + [F2] to get a command line prompt.  I logged in as root (I find this far easier than sudo, and I was not positive that the sudo function would work anyway, in the condition of the install) 
then entered ```
view /etc/apt/sources.list
``` to check and see what repositories would be pulled.  The process is "supposed to" rewrite this file to edgy repositories, but what if it hadn't?  Apt wouldn't work right!

The sources list was ok, aimed at edgy repositories, so I typed
```
aptitude dist-upgrade
``` if you were using the sudo command the entry would be ```
sudo apt-get dist-upgrade
```Aptitude is a front-end for apt that checks and tries to fix dependency problems, so I use it in preference to apt-get most of the time.

The dist-upgrade failed and the error message said I had to run 'dpkg --configure -a'.

I typed in ```
dpkg --configure -a 
``` and watched for an hour and a half while it configured some large number of packages.  In TTY1 through TTY6 ([Ctrl] + [Alt] + [F2..F6]) there is no scrollbar, so you cannot go back and look at anything that has scrolled off-screen.

During this time, the xorg error reappeared again and again, as gui-based messages that would have appeared failed again and again.  This was a bit annoying, however, I was expecting something like this because I was using the earlier kernel and half the packages on the box were from a newer distribution (and we already knew the GUI was broken).  Remember-- DON'T PANIC --  This apt has super cow powers.

Eventually I got back my CLI prompt.  I restarted the box and let edgy boot.  The boot worked fine.  When my GUI was in place, I ran the upgrade manager again, and it said I had 4 packages to update, if I wanted to run a dist-upgrade.  I did that, and now I am running a working version of Xubuntu, with a kubuntu splash screen and xubuntu login screen.  

Cheers
-Wolf

---

### Post by swlbc on 2007-01-07
It doesn't matter if you use the offical upgrade method or if you install from a CD or if you install from a download ~ all methods are dodgie and prone to complete failur more often than not ...
Dapper has got grief just as much as Edgy ... get one working an' don't expect too much for all you troubles. You'll be re-installing forever if your'e looking for a stable O/S as this will not happened without major compromises ...

Steve

---

### Post by APA on 2007-01-07
I have 6.06 on a 64 bit machine (athalon 64) and cant getmy  d-link wireless card to run so using a (spit loudly) windows machine downloaded the 64 bit 6.10 dist and tried loading it, i get a kernel panic and numbers which change each time i try a restart.
the "method of preferance says use an alternate cd" since im still a "noob" is it ok to use the alternate cd , im just using the machine for regu;lar stuf, i dont want a server just a desktop machine 

sugestions in the simple speak would help greately asmy learning curve is steep enough as it is , 

Many thanks  Andy
](*,)

---

### Post by ions on 2007-01-07
I think it is possible that upgrading from Dapper instead of a fresh install could cause problems with ipods.  [The beginning of my theory is here](http://ubuntuforums.org/showthread.php?t=333614).  On IRC I had managed to find someone who got their ipod to just plug and play on a system that had been upgraded but it was PPC.  I'd like to see evidence in x86 that it works.

---

### Post by saphil on 2007-01-07
> I have 6.06 on a 64 bit machine (athalon 64) and cant getmy d-link wireless card to run so using a (spit loudly) windows machine downloaded the 64 bit 6.10 dist and tried loading it, i get a kernel panic and numbers which change each time i try a restart.
 the "method of preferance says use an alternate cd" since im still a "noob" is it ok to use the alternate cd , im just using the machine for regu;lar stuf, i dont want a server just a desktop machine So is your machine unbootable?
If not, maybe you could just back up your home folder do a clean install and copy the contents of your home folder onto the new OS.

If your machine is unbootable, the live 6.10 disk can boot and then you can look at the hard drive as a piece of that OS
Go to the disk manager in gnome and add the hard drive with your home files as a new folder on the desktop, then burn the files to a disk.  Remember to choose show hidden files in the nautilus view menu, or you might not get your old email files and personal settings.  

If you are running a basic desktop "not a server" you don't have any fancy server apps set up, and so the configuration files in /etc are not important.

You could consider setting up your windows box as a file server (once you get the wireless card working), keep all the files there, and samba into it to save and open.

---

### Post by WesleyWex on 2007-01-08
I did the upgrade by the suggested way, and look what I have to deal now, my apt-get is unusable and I can't fix it!

[http://www.ubuntuforums.org/showthread.php?p=1984323](http://www.ubuntuforums.org/showthread.php?p=1984323)

---

### Post by sfsdfdsff on 2007-01-09
Hallo, interesting. 
Look at my site: 
[phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">phentermine</a>, 
 
[buy phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">buy phentermine</a>, 
 
[cheap phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">cheap phentermine</a>, 
thanks a lot.

---

### Post by vimihrju on 2007-01-10
Hey, thanks author. 
Go here: 
[phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">phentermine</a>, 
 
[buy phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">buy phentermine</a>, 
 
[cheap phentermine](http://phentermine.alldating.org/phentermine.htm), 
<a href="http://phentermine.alldating.org/phentermine.htm">cheap phentermine</a>, 
thanks a lot.

---

### Post by The Pinny Parlour on 2007-01-12
delete

---

### Post by The Pinny Parlour on 2007-01-13
delete

---

### Post by The Pinny Parlour on 2007-01-13
Hi, 

I get the following message and the whole things stops.  Can anyone help please?: 

**Error during update**

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2](http://www.getautomatix.com/apt/dists/dapper/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/Packages.gz](http://xgl.compiz.info/dists/dapper/aiglx/binary-i386/Packages.gz) 404 Not Found

RESOLVED:  removed the lines from sources.list

---

### Post by tagginannie on 2007-01-14
Ubuntu/Kubuntu is my first Debian distro and I did try the "official" way of updating Kubuntu after I installed it, after apt got the list of updates it started the up date, When I got back to my computer I had the prompt so I tried to start KDE (startkde) it was removed as well as X-server. Now I use Synaptic or do it manually if it is only just one or two packages

Suzy

---

### Post by Tulx on 2007-01-19
> **igorzolnikov said:**
> sudo update-manager -c
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

What next? Software Updates have status: "Your system is up-to-date".

Ive got this message too when entering the command to terminal but when I copyed it to ALT-F2 window there were not any problems.

Im total Linux noob but my dapper updated to edgy and is working just fine.8-)(I got my Ubnutu cd for free from local computer store and decided to try that out.)

---

### Post by euler_fan on 2007-01-20
maybe I'm just really lucky, but I've been upgrading to 6.10 from fresh 6.06 installs by first installing 6.06 from live CD, then letting the updater do its thing for a few hours. After that I change all the /etc/apt/sources.list file to point to edgy repos (the unofficial way) and then go into the terminal and say "gksudo update-manager -c". Usually at that point it pops up a message saying there is a new distribution available and everything comes down fine. Only after a full update to 6.10 Ubuntu do I try to switch over to Xfce.

This has worked for four upgrades. Three were fresh, one was with a few-week old install of 6.06. Twice on my Compaq v5000, once on my Dell Inspiron 1150 and a third time on a friend's Dell Inspiron (5150?).

I also do this for regular Ubuntu and then strip off the Gnome desktop and use sudo aptitude xubuntu-desktop to get it. Then comes reinstalling synaptic and a few other things. I use a command I found in the community documents aysiu wrote a while back. (To make room for KDE, admittedly. Can't find the bookmark on this machine, must be on my alt.) Then I end up reinstalling synaptic and a few other gnome bits I like and bingo! nice fresh happy 6.10 Xubuntu.

Good luck to everyone out there who is having trouble.  I hope it all comes together sooner rather than later.

**Is there an option "-d" for update-manager that looks for developmental versions? I am pretty sure I included that option as well as "-c" and life was yet better still.**

---

### Post by rainwalker on 2007-01-27
Just a question before upgrading: If I go from my current 6.06 version to 6.10, does it overwrite everything? When I say that I mean will I have to install all of my applications again (Thunderbird, LimeWire, Amarok, etc.) and redo all of my personal settings, or does it copy all of that stuff into the next version?

---

### Post by magichsjx on 2007-01-31
I was just browsing through and experimenting with upgrading from Dapper Drake to Edgy and I found out that the official implementation using:

       $ gksu "update-manger -C"

did not work with me, Rather the alternatative (spelt-out) version:

       $ gksu "update-manager --check-dist-upgrades"

works beautifully under Ubuntu 6.06 to upgrade to 6.10. I refrained from upgrading, but this may prove helpful to some who have tried the first command above to do the upgrade and found out that it did not work as expected. Later I found out that it has to be a lower-case c instead of a capital. The lower-case works. Anyhow seems like a useless post but might still help someone out there who is new and inexperienced.

---

### Post by Red Knuckles on 2007-02-06
> **xiamcitizen said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

Will this also update Edgy to Feisty?

):P

---

### Post by Red Knuckles on 2007-02-06
> **Red Knuckles said:**
> Will this also update Edgy to Feisty?

):P

Apparently not. At least it didn't work for me in Kubuntu.:( :confused:

---

### Post by houstonbofh on 2007-02-07
> **Red Knuckles said:**
> Apparently not. At least it didn't work for me in Kubuntu.:( :confused:
Well it won't work before Feisty is released!
:lol:

---

### Post by Red Knuckles on 2007-02-07
> **houstonbofh said:**
> Well it won't work before Feisty is released!
:lol:

Been having a problem installing from live CD as well:

[http://kubuntuforums.net/forums/index.php?topic=13556.0](http://kubuntuforums.net/forums/index.php?topic=13556.0)

Will now try with alternate CD.

---

### Post by serlex on 2007-02-08
Do not know if it has been asked before, but do i need to update dapper before upgrading to Edgy? (215 updates)

---

### Post by houstonbofh on 2007-02-08
> **serlex said:**
> Do not know if it has been asked before, but do i need to update dapper before upgrading to Edgy? (215 updates)
All of the information I have read says that you need to go one distribution at a time.  However, I have not tried skipping a distribution personally.  Try it (after a good back up) and let us know!  I suspect that an "update-manager -c" will only show a single step upgrade.

---

### Post by serlex on 2007-02-08
I updated then installed Edgy, smooth.

---

### Post by jarekl on 2007-02-08
Since so many people have problems with upgrading, is there an official howto what to do when the official method (update-manager -c) fails?

---

### Post by Shampyon on 2007-02-10
When I first tried to upgrade from Dapper to Edgy, it completely failed and I ended up having to wipe everything and do a clean install of Dapper again. Same with just installing Edgy straight, fro some reason.

I'm gonna try again (mainly 'cause I really, REALLY wanna try out Beryl!) and I was wondering how I'd go about backing up my current Dapper setup. I want to be able to return things to the exact state they are now if anything goes wrong.

---

### Post by Shampyon on 2007-02-11
Well I just tried to upgrade to Edgy using the Alternate Install disc.
Now my setup is completely messed up.
 Edgy refuses to start up. It'll begin the boot screen and just hang forever.

I couldn't log in to the previous version in the GRUB list. I had to go two versions back, PLUS I couldn't use the fglrx drivers anymore - I had to switch over to vesa just to get a GUI, and now I'm at a lower resolution and everything's still moving chuggily.

What the hell went wrong? How can I fix this?

Edit: Oh wow. I also have no sound. Basically I'm reduced to being able to open a single webpage at a time, and nothing else. Even that is so chuggy it almost causes an epileptic fit.

---

### Post by Shampyon on 2007-02-11
I reinstalled xserver-xorg and ubuntu-desktop, and reconfigured xserver-xorg to use vesa instead of ati or fglrx. Now I can get back into Ubuntu, although my resolution is low and certain things (like viewing pages in Firefox) are chuggy.

I'm gonna try reinstalling the official ATI drivers to see if that helps any.

---

### Post by remat457 on 2007-02-11
A couple of thoughts after reading this thread. Of course, I didn't think to check here until  after upgrading :)

It wasn't clear to me that I should stick with the LTS releases and wait. In fact, most of what I read said that the upgrades must be from release to release unless you want to wipe and reload clean.

Let's be honest, I work in I.T. so I familiar with with testing on non-production boxes, but how many home users have a readily available test box identical to their primary? I don't.

Anyway here is my upgrade experience:
So, I used update-manager -c to upgrade. It seemed to go ok, but I noticed a few packages held back. My workstation rebooted and seemed ok. 

However, any subsequent reboots attempting to boot runlevel 5(GUI)  resulted in a black blank screen. hmm...Booting to safe-mode worked ok and several apt-get upgrade and many  apt-get dist-upgrade the held back packages were installed and I am pleased to say I am writing this from Edgy. Edgy does seem faster!

Perfect upgrade? No, but a lot easier than when I skipped a couple of upgrades and tried to upgrade Hoary to 6.06!!

regards

---

### Post by Shampyon on 2007-02-12
> **Shampyon said:**
> I reinstalled xserver-xorg and ubuntu-desktop, and reconfigured xserver-xorg to use vesa instead of ati or fglrx. Now I can get back into Ubuntu, although my resolution is low and certain things (like viewing pages in Firefox) are chuggy.

I'm gonna try reinstalling the official ATI drivers to see if that helps any.

Update: Sometimes I get to the login screen. I enter my uname and pass, and it goes to a blank purple screen. Other times, the loading screen before the loging page just crashes and changes to wierd colours with a green line in the middle of the screen.

I'm stuck using my Windows partition for the first time in a year, because no part of my Ubuntu partition is usable anymore. I'm on the verge of tears here :(

---

### Post by LeShifer on 2007-02-15
Spam.

---

### Post by Shampyon on 2007-02-15
Reinstalling the official ATI drivers did nothing. It's still broken. I still have no sound. Using the vesa drivers so I can log in. Damn, this is frustrating. It took me ages to get Dapper working the way I needed, now I'm going through it all again with Edgy...

---

### Post by Geministorm on 2007-02-25
"Official" upgrade method resulted in an "officially" hosed system.

I should have known better than to trust an upgrade (does _any_  OS do it right?). Thank goodness for back ups...

---

### Post by bmilner on 2007-02-26
I was pretty worried about upgrading due to the large amount of negative posts. Other than a slow mirror, it seemed to work just fine.  I still have unresolved bugs registered for dapper, but I can work around them.  FYI, amd64,  Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] .
I did have to remove plf from source.list for the upgrade to continue.

---

### Post by hhbuukkd on 2007-02-26
spam.

---

### Post by hnumhnuj on 2007-02-26
Spam.

---

### Post by siuymhnuj on 2007-02-27
Spam.

---

### Post by cubanresourceful on 2007-03-04
What is with all the spam? But heres my question, when Fiesty Fawn comes out, would this update  command also work?

---

### Post by William Pickett on 2007-03-05
Upgrades care think etc...

I concur that an upgrade- especially if not at stable version release date RC final etc, is a learning experience. I highly recommend folks stay with the current LTS version because generally- more is put time and effort- but, in all fairness, I am certainly glad that Canonical and everyone who puts in volunteer hours, do so because these forums sure are a big help to the rest of us-especially those like me new to Linux/Ubuntu (6.10-awaiting 7.04 Final).

William Pickett
Albuquerque

---

### Post by tubunu on 2007-03-11
So I took the plunge and upgraded from Edgy to Fiesty (sudo apt-get dist-upgrade) as suggested by many on the forum elsewhere. As expected, I ran into problems straight on. During the download (around 800MB), which took the whole night, some three or four packages weren't fetched for some unknown reason. :confused: 
During the upgrade there were two error messages #-o and after shutting the PC down, I cannot boot the system. The error message reads: 
```

VFS: Cannot open root device "hdb6" or unknown-block(0,0) 
Please append a correct "root=" boot option 
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

How do I go about appending my root partition hdb6 if I can't boot into system? Please help. :(

---

### Post by Memocjro on 2007-03-18
You can chroot into your environment from a live-cd.
That's what i am doing right now after an unsucessfull upgrade from edgy to feisty.

Boot from your live cd, 
create a directory in the /mnt directory:

sudo mkdir /mnt/ubuntu 

after that mount your root sistem in that directory (i have my root in the /dev/hda1 partition):

mount /dev/hda1 /mnt/ubuntu

After this chroot in your installation:

sudo chroot /mnt/ubuntu

you are now in your installed system.

---

### Post by jiminid on 2007-03-22
> **PWill said:**
> Please, people; if you plan on upgrading to Edgy Eft 6.10, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

Hi,
I have the dapper version installed and tried to upgrade to Edgy using the official way noted above and got my software update window...but it says system is updated., the rest of the window is grayed out. Only thing I've done on this install is to update firefox to 2.0.0.3 using the script on psychocats.

Any suggestions?
Thanks for your help.
Jiminid

Celeron D 351 3.2 ghz
1.2 GB pc3200 400 mhz ram
dual boot  XP (drive 1-80GB) and Dapper on drive 2 (80 GB)
XFX Geforce 6200 256 mb nvidia video
Integrated sound and lan w/ DSL broadband  internet hookup

---

### Post by kb9tua on 2007-03-22
The only version that I've been able to install is a downloaded copy of 5.04. The 6.06 LTS cd's that were mailed to me won't install...something about ubiquity. I've downloaded 6.06 LTS, 6.10 cd and dvd, and none of them will install. When I reinstalled 5.04 and then put in the 6.06 LTS cd, a message popped up asking my if I wanted to upgrade to 6.06. I clicked yes. It then told me I had a broken package and to resolve it. I resolved it and now that message won't reappear. HELP!!!!

---

### Post by aldegaz on 2007-03-24
this broke my system wihtout ben able to even get to a terminal, so my advice is to either do a clean install or wait to get to the final release

more info on: [http://ubuntuforums.org/showthread.php?p=2344123#post2344123](http://ubuntuforums.org/showthread.php?p=2344123#post2344123)

---

### Post by HarmonicaGoldfish on 2007-03-24
Hello

I am trying to upgrade from 6.06 to 6.10. I have followed all of the instructions on ubuntu's official upgrade page and have tried the process 3 times. Each time it stops during the first part of the upgrade process (the 'preparing' part) as it tries to get repository 22 of 31 with this message:

[http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz:](http://theli.free.fr/packages/dists/dapper/listen/binary-i386/Packages.gz:) 301 Moved Permanently

What should I do?

thanks.

I posted this in a new thread...
[http://ubuntuforums.org/showthread.php?p=2346711#post2346711](http://ubuntuforums.org/showthread.php?p=2346711#post2346711)

---

### Post by HarmonicaGoldfish on 2007-03-24
part 2...

Just tried the process again and can not even get to the point where my update manager notifies me of the opportunity to upgrade to 6.10.

I get the same error as I previously mentioned with the added bonus of this warning:

W: GPG error: [http://mirror.randumb.org](http://mirror.randumb.org) dapper-darkmagez Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY DB5D6B0AA3012FB3

I added this to a new thread: [http://ubuntuforums.org/showthread.php?p=2346711#post2346711](http://ubuntuforums.org/showthread.php?p=2346711#post2346711)

---

### Post by ubunter1 on 2007-04-03
ive upped to edgy as well,better late than never i guess,my problem is the update manager work work because of a malformed line 2? any one with this expirence?,ive made a thread documenting the problem ive had.thanks for your time- [http://www.ubuntuforums.org/showthread.php?t=399936](http://www.ubuntuforums.org/showthread.php?t=399936)

---

### Post by johnthemax on 2007-04-09
i am having prb installing as I need drivers not in 6.10 at start up
how to install driver when installing and whare to get them
mb is n680 giabyte

---

### Post by Kizilbas on 2007-04-10
> **ubuntu_demon said:**
> I stickied this thread. If you decide to upgrade I recommend upgrading through :
```

$ gksu "update-manager -c"

```

Hi there demon, can you explain that command word by word

I mean what is the function(s) of it

'$'
'gksu' 
'update-manager' '
-C'

I know its the commands to update, but what does each of the above do?

Thanks for your time :)

---

### Post by madscientist on 2007-04-10
> **Kizilbas said:**
> 
'$'
'gksu' 
'update-manager' '
-C'


The '$' is the shell prompt; you shouldn't type that.

The 'gksu' command is the program that asks for your password via a graphical dialog window and, if it's correct, runs the command that you give on the command line with root privileges.

'update-manager' is the program that runs when you click the update icon in the notification area, that installs updates for you.

The '-c' is an option to update-manager that tells it to allow upgrading to new releases; normally for LTS releases update-manager only offers updates to your current release (or, presumably, offers an upgrade to the next LTS release, although we've only ever had one so far :) )

---

### Post by wildbillnj1975 on 2007-04-10
Kevin --
a dumb noob question - how do you make it tell you what it "thinks" it is (dapper or edgy or whatever) ??
I'm halfway between dapper and edgy, nto sure just how broken the system is, but it would be nice to know what it thinks it is running.

---

### Post by rcmullins on 2007-04-12
39 of 40?? are you kidding?  Im upgrading from Edgy to Feisty, and there are 954 files.  (been running it all day, and so far im at 357.


*sorry didnt realize this post had 18 pages. this is in response to a post back on page 1*

---

### Post by btioplkjgfdsdm on 2007-04-15
[Blackjack Ballroom Casino](http://leokop.bizhat.com/blackjack-ballroom-casino.html)  	 
 
[http://leokop.bizhat.com/strip-poker.html](http://leokop.bizhat.com/strip-poker.html)                                   strip poker

---

### Post by Give_Peace_A_Chance on 2007-04-16
Somebody that can help PM me.
[IMG]http://i5.photobucket.com/albums/y183/shadyichigo/youneedtoroot.png[/IMG]

---

### Post by Murador on 2007-04-16
I'm planning to upgrade to Feisty when it will be released on the 19th of April, but I'm concerned by the fact that I've installed software from other repos. 
Will it affect the process in any way? 
Should I uninstall the packages that are not included in a standard Ubuntu distribution? so far i've added at least 6 new repos and I've compiled 3 or 4 programs (luckily with checkinstall).

Thanks in advance.

---

### Post by TimelessRogue on 2007-04-18
Hmmm ... official or not, I just (night before last and again last night) upgraded both an older HP n5000 laptop (night before last) as well as my rather esoteric desktop (last evening) that I put together about four years ago with AMD processor, ATI 9700 graphics card, Creative sound card, Linksys wireless, etc (the only thing that I am still working on is the wireless) to Feisty from Edgy using the "unofficial" method of editing the sources.list (see [http://ubuntuforums.org/showthread.php?p=2473354#post2473354)](http://ubuntuforums.org/showthread.php?p=2473354#post2473354)).  It went perfectly on both ... no glitches whatsoever inspite of the intrepidation I went through both times before I hit the enter key ... but then that has been the case everytime I upgrade any OS ... and with good reason judging by the many reports of problems using either method.

Sooo ... as I said, "unofficial" or not, it worked for me ...

---

### Post by Xan.Manning on 2007-04-18
Not sure if anyone here would appreciate this, but it is a file that can help...
It is basically a bash script to initiate the update.

Uses the update-manager command.

Just thought may be useful for people to try when they all surge to upgrade to 7.04.

Regards, Xan Manning

---

### Post by YaseenKriel on 2007-04-19
Any way to use the cd to upgrade?

---

### Post by Binary Jay on 2007-04-19
I changed my sources.list to Feisty, did an update, dist-upgrade...  it went alright from what I saw in the log...

Restart...

X doesn't start, assume fglrx doesn't like the new kernel, replace xorg.conf with OSS driver from a previously working config...  X starts, dual head now broken, everything extremely slow.

Noticed that my second harddrive will no longer mount, complaints that it "doesn't exist".  Was there a huge change to warrant THIS not working all of a sudden?

mt-daapd no longer starts up, segmentation fault, there goes my music library.

-- That's what I get for trying to upgrade the night before the "official release".  As of this morning I had all of the latest packages being offered.  The latest fglrx installer complains it can't find a proper X folder... had to give up and come to work.  ARGH.

---

### Post by galotzas on 2007-04-19
root@galotzas-desktop:~# gksu "update-manager -c"
Introspect error: The name org.freedesktop.UpdateManager was not provided by any .service files
no listening object (The name org.freedesktop.UpdateManager was not provided by any .service files) 


what is this ?


thanos

---

### Post by dweez on 2007-04-19
I have been testing Feisty for a few months now.  Do I have to do anything special to get the "official" release or am I already there?  I did update, upgrade, and dist-upgrade yesterday and had some needed updates, but so far today, I haven't had any.  Did the testers get the official release early?

---

### Post by Roland of Gilead on 2007-04-19
So, the update servers are hammered right now...but I have the complete ISO from a bittorrent download.

Is there any method to upgrade using this ISO image?

I tried mounting it and then using apt-cdrom...it added the appropriate line to sources.list, but running apt-get update and then apt-get dist-upgrade does nothing.  It reports 0 packages to be upgraded.

Any thoughts?

---

### Post by DarkStarAeon on 2007-04-19
Upgrading from Edgy to Feisty right now...*crossing fingers, please don't break my system*

I'm sure the servers are overloaded right now, my download speed is currently ranging from bytes to kb's, slower than dial up so far. Been downloading for 4 hours and has only fetched 140 files of 1,199, sigh.
I have a fast computer and fast internet connection, but it's not helping, lol

I wish the update manager gave some instructions as to what, if anything, might break. I use a very dark theme and highly modified, and I have a feeling it's going to cause a problem. I hope Envy still works in case X craps out on me.

I'm trying my computer first, if all goes well I'll upgrade my wifes too. She'd kill me if I upgraded and it didn't work anymore though. lol

Anyone on Feisty have any tips or pointers we should know about?

I wish I could just run to a store and get an upgrade cd, of course, then it wouldn't be free. doh.

---

### Post by odelay on 2007-04-19
I'm sure someone's said this before, by maybe try downloading a torrent instead of an .iso directly.  For one, it gives the people hosting the .iso's a break.  For two, my downloaded at an average 400 kb/s...and that was 5 hours ago.

---

### Post by DarkStarAeon on 2007-04-19
Every single time I have ever tried to download a torrent for anything, it has taken longer than a normal download. Don't know why, maybe just bad timing for when I try.

---

### Post by houstonbofh on 2007-04-19
Several things people have forgotten.

'sudo update-manager -c' is for Dapper to Edgy.

With Feisty, you get a button automagically.

The alt-install CD has an upgrade script so you don't have to download multiple upgrades.
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
gksu "sh /cdrom/cdromupgrade" from alt-F2.

---

### Post by odelay on 2007-04-19
The download speed you get depends on two major things:

* The number of people "seeding" (uploading the torrent) vs. the number of people "leeching" (downloading).  If your have 500 people downloading and 1 person uploading, it will crawl.  If you have 500 people uploading and you're lucky enough to be downloading, you'll be fine.

*  Port forwarding.  Getting this working correctly is usually the crux for most people.  If you aren't using both a uPnP-enable router & torrent client you'll have to manually forward ports.  Doing this requires forwarding ports both on your software firewall and router.  Read more at [www.portforward.com](www.portforward.com) for details.

Perhaps it's not worth it to cancel your download and figure out the torrent now, but with all the advantages of torrents nowadays, it'd probably be worthwhile to get things working in the future.  A bit off topic, but hope that helps in the future.

---

### Post by DarkStarAeon on 2007-04-19
lol, I know how it works mate, seeding is usually the problem, most of the time no one is uploading when I go to get the file. A few times it has been a leeching problem though as you said, one person uploading and 500 downloading.

When I said "I don't know why" in my other post I meant I think it's karma or something. lol just my luck.

---

### Post by lunadesign on 2007-04-19
I don't get the upgrade button and I've downloaded the ISO and burned it twice but no Alt-F2 upgrade. Yes I'm running Edgy. I installed it fresh April 1st. I'm tempted to do the upgrade via bash but my system runs really nice and I'd like to keep it that way.

Any idea why I don't get the auto button update or Alt-F2 methods?

Toshiba Satellite 2410 P4 1.8GHz

Thanks,
Andrew

---

### Post by karellen on 2007-04-20
[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)
well, this seems the official upgrade method to me ;) (as it's on ubuntu.com, not on a wiki/ubuntuguide etc)

---

### Post by raspark on 2007-04-20
> **DarkStarAeon said:**
> Every single time I have ever tried to download a torrent for anything, it has taken longer than a normal download. Don't know why, maybe just bad timing for when I try.

I hear you.  The same happens to me just about every time I try to torrent something.  I've checked all my settings, but I just can't get throughput.

---

### Post by raspark on 2007-04-20
>Any idea why I don't get the auto button update or Alt-F2 methods?
>Toshiba Satellite 2410 P4 1.8GHz

Andrew,

I just did this a little bit ago, and I didn't get the prompt either.  Have you tried opening up a file manager, going to the CD and clicking (or double-clicking) on the cdromupgrade (script) icon?  I did and the upgrade panel did then come up.  I'm progressing thrtough the upgrade fine now, when I couldn't get past repository problems in the network upgrade earlier.

Randy

---

### Post by epee on 2007-04-20
I started with 7.04 (beta) about a week ago. Have run Update Manager a couple of times since. Notably last night (Uk time) it seemed to stall - I gave up on it in the end.

Anyway, my question: will Update Manager get my machine to 7.04 (release) from where I am or do I need to start with a CD? Do I need to re-install completely?

Thanks.

---

### Post by mdz on 2007-04-20
The official upgrade instructions for upgrading to 7.04 (Feisty) are at [http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading).  The instructions in this thread are for upgrading from 6.06 LTS (Dapper) to 6.10 (Edgy).

I would appreciate if a forum moderator would help make it clear that this thread is about upgrades to 6.10, and post the above as official instructions for upgrading to 7.04.  The instructions here will also work for upgrading to 7.04, but the ones on [www.ubuntu.com](www.ubuntu.com) don't require the command line and contain additional step-by-step instructions and caveats.

---

### Post by dostor on 2007-04-20
after clicking the Upgrade button i get::

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/main/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/restricted/source/Sources.gz) 404 Not Found
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz](http://security.ubuntu.com/ubuntu/dists/edgy-security/universe/source/Sources.gz) 404 Not Found



retried few mins later and it was okay

---

### Post by DarkStarAeon on 2007-04-20
just close the dialog for that error message, go to update manager, and click on upgrade again. it picks up where it left off.

---

### Post by Sterkarm on 2007-04-20
ARGH

exuse me for proberly being a bit of a newb but why is everyone saying to use the update manager - it dosent do anything - nothing pops up with any option to upgrade to fiesty... why the hellnot ?

im running on a machine that was upgradged from the 6.06 version to 6.10 - i dont have to go through the cd way of upgrading do i ? 

plz plz plz help

---

### Post by DarkStarAeon on 2007-04-20
Hmm, not sure why you don't see the upgrade button in the update manager, maybe it's because you went from  6.06 to 6.10 first? Don't really know mate, sorry.

---

### Post by lunadesign on 2007-04-20
MDZ: Sorry about that I didn't realize this was only for Drapper to Edgy but that makes sense. I'll just quickly reply to Randy and maybe help out someone else who had the same experience as I did.

> **raspark said:**
> 
I just did this a little bit ago, and I didn't get the prompt either.  Have you tried opening up a file manager, going to the CD and clicking (or double-clicking) on the cdromupgrade (script) icon?  I did and the upgrade panel did then come up.  I'm progressing thrtough the upgrade fine now, when I couldn't get past repository problems in the network upgrade earlier.

Randy

Randy I got it working but this is really wierd. I downloaded and created the 7.04 CD twice from ubunto.com mirrors. The download was pretty quick but neither CD has the update icon inside and F2 doesn't work. It's like I'm in a little time warp.

Here's how I updated:
I changed my sources.list file 
I got my sources from: [http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

After I edited my sources, I ran update manager but it told me that I needed to upgrade to 6.10.

Since I had nothing really to loose, I said ok. It ran throught the network update for about and hour all the while telling me that it was for 6.10

Once it was complete I rebooted and went to: System >> About Ubuntu where under Version and release numbers it says I'm running 7.04.

Thanks for the help and I hope this helps anyone else.
Andrew

---

### Post by HarmonicaGoldfish on 2007-04-20
> **Sterkarm said:**
> ARGH

exuse me for proberly being a bit of a newb but why is everyone saying to use the update manager - it dosent do anything - nothing pops up with any option to upgrade to fiesty... why the hellnot ?

im running on a machine that was upgradged from the 6.06 version to 6.10 - i dont have to go through the cd way of upgrading do i ? 

plz plz plz help

Click on 'check'. Mine doesn't show that the update is available until I manually check for it with this button. 

Hope it helps.

---

### Post by ardya on 2007-04-20
> **magicfab said:**
> EXCEPT for Xubuntu...! Please read:
[http://www.ubuntuforums.org/showthread.php?t=285951](http://www.ubuntuforums.org/showthread.php?t=285951)

There is a critical bug when upgrading with the standard method fro Xubuntu:
[https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027](https://launchpad.net/distros/ubuntu/+source/update-manager/+bug/68027)

Modifying the sources, etc. when following the instructions to upgrade is OK, BTW. It causes problems when you have external repos, etc.

None of which covers going from edgy to feisty...are there any issues doing this particular dist-upgrade?

---

### Post by Cauda_Draconis on 2007-04-21
I tried to upgrade by pressing the "upgrade" button in the update manager, but it didn't work; said that bzip2 returned an error code (2) on a couple of the packages. Now the upgrade button doesn't show at all in the update manager, even if I press the "check" button, and most of the files it says it's fetching fail when I press "check." Then it comes up with a message saying that not all repositories could be downloaded:
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy/multiverse/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2:](http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/multiverse/i18n/Translation-en_US.bz2:) Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
[http://givre.cabspace.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2:](http://givre.cabspace.com/ubuntu/dists/edgy/main/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)
[http://givre.cabspace.com/ubuntu/dists/edgy/main-all/binary-i386/Packages.bz2:](http://givre.cabspace.com/ubuntu/dists/edgy/main-all/binary-i386/Packages.bz2:) Sub-process bzip2 returned an error code (2)

Then I close that, and it comes up with a message saying "An error occured:"
W: GPG error: [http://ubuntu.beryl-project.org](http://ubuntu.beryl-project.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 3FF0DB166A7476EA
W: GPG error: [http://gandalfn.club.fr](http://gandalfn.club.fr) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CBF6E0B8483170E9
W: GPG error: [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: GPG error: [http://givre.cabspace.com](http://givre.cabspace.com) edgy Release: The following signatures were invalid: NODATA 1 NODATA 2


When I start update manager through the terminal, with gksu "update-manager -c", it says it can't initiate dbus.

Anyone know how to fix it?

---

### Post by sumgi on 2007-04-21
I also get connection refused messages for several files. I've tried several times, it's always the same. Only the tmp location changes.

> A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Obviously my network connection is working if I'm making this post.

```
 gksu "update-manager -c"
warning: could not initiate dbus
extracting '/tmp/tmpkSRQ1_/feisty.tar.gz'
authenticate '/tmp/tmpkSRQ1_/feisty.tar.gz' against '/tmp/tmpkSRQ1_/feisty.tar.gz.gpg' 

```

Should it be retrieving edgy updates? Or is it supposed to say edgy?

```
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/main/i18n/Translation-en_US.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/restricted/i18n/Translation-en_US.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy/universe/i18n/Translation-en_US.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/Release.gpg Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/i18n/Translation-en_US.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/edgy-updates/restricted/i18n/Translation-en_US.bz2 Could not connect to ca.archive.ubuntu.com:80 (206.167.141.10). - connect (111 Connection refused)

```

```
ping 206.167.141.10
PING 206.167.141.10 (206.167.141.10) 56(84) bytes of data.
64 bytes from 206.167.141.10: icmp_seq=1 ttl=47 time=63.3 ms
64 bytes from 206.167.141.10: icmp_seq=2 ttl=47 time=64.9 ms
64 bytes from 206.167.141.10: icmp_seq=3 ttl=47 time=62.7 ms
64 bytes from 206.167.141.10: icmp_seq=4 ttl=47 time=63.3 ms
64 bytes from 206.167.141.10: icmp_seq=5 ttl=47 time=62.4 ms

ping ca.archive.ubuntu.com
PING gulus.usherbrooke.ca (206.167.141.10) 56(84) bytes of data.
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=1 ttl=47 time=61.8 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=2 ttl=47 time=62.3 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=3 ttl=47 time=62.1 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=4 ttl=47 time=64.8 ms
64 bytes from gulus.usherbrooke.ca (206.167.141.10): icmp_seq=5 ttl=47 time=64.4 ms

nslookup ca.archive.ubuntu.com
Server:         24.93.40.62
Address:        24.93.40.62#53

Non-authoritative answer:
ca.archive.ubuntu.com   canonical name = gulus.usherbrooke.ca.
Name:   gulus.usherbrooke.ca
Address: 206.167.141.10

```

---

### Post by DarkStarAeon on 2007-04-21
Servers are just overloaded guys, I'm in the same boat, we just have to wait and try again later. sigh.

---

### Post by sumgi on 2007-04-21
> **DarkStarAeon said:**
> Servers are just overloaded guys, I'm in the same boat, we just have to wait and try again later. sigh.

Actually I figured it out, I made a copy of my /etc/apt/sources.list and my /etc/apt/sources.list.distUpgrade files and then replaced all references to edgy with feisty and used one of the mirror servers on this list:

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

Thanks to jdong for [the solution]("http://ubuntuforums.org/showpost.php?p=2497099&postcount=13")!!

---

### Post by DarkStarAeon on 2007-04-21
Yeah I did the same, jdong saves the day!

---

### Post by sumgi on 2007-04-21
Alright, success. I have rebooted with feisty fawn and all looks good, only had to set up wireless again. Thanks for everyones help!

---

### Post by Carlo1973 on 2007-04-21
when I first saw the notice in the normal update-manager that there was an upgrade I clicked on it. However I was in the middle of a few things I had to deal with on my end prior to updating so I canceled it. Now that i'm ready to perform the upgrade, I no longer seem to be getting the message saying that I can upgrade.

I tried the command gksu "update-manager -c" but I got a GK error stating it couldn't display the window

I tried the instructions found in the website as well : System -> Administration -> update-manager from within gnome


Suggestions?

thanks in advance

Carlo

---

### Post by cutterjohn on 2007-04-21
You know, after looking through a number of posts in this sticky, I'd have to suggest one of two things, preferably both:

1) a command line run script that does the official method for people from the CLI with one command

AND

2) a system menu command that runs it from the GUI


(and now that I think of it)

3) an "update manager" menu option that restarts the update-manager in such a state

All 3 SHOULD have a means of checking as to whether or not the next official release has actually been released and is available for updating otherwise it should give a nice warning dialog box(continue unstable or quit).  Further thinking about it, even if there is an official release it SHOULD give a warning again just in case the user accidentally some how ran that and didn't need to or more importantly WANT to upgrade at the time.

It is possible that Ubuntu (and variants) could go even further in the case of:  if a high speed link is detected and an official "distro update" is available that the update notifier could pop up another dialog when clicked asking if a distro update is wanted or just stay as installed, preferably with a check once flag.

Further looking at the posts suggest one of the GUI based alternatives to be highly preferable although a script would still likely be needed to kick it off(dependent upon how it's implemented) which would still be available via the CLI, which would also be useful for non-GUI server installations.

Bottom line here, is that doing the above would, hopefully, eliminate the need for a sticky just such as this, and anyone monkeying around with their sources list outside of the update manager should be able to handle that on their own anyways as it DOES require a certain small degree of proficiency.

Personally, I've updated through both variants, and have had few problems other than getting my proprietary drivers back in place, as expected at the time, but nothing insurmountable as they were entirely unsupported and I expected the hassles.

As to feisty, I believe that I'll be holding off a while before I make yet another foray into a distro-update, allowing server loads to drop(presumably) and see if anything fairly major slipped by testing...  (Normally, I'd do a clean upgrade at this point, but I've customized/added so much stuff that re-installing and setting up everything would be incredibly time consuming, if not painful... even with a 10M link...)

---

### Post by Timothy Butwinick on 2007-04-21
I have some problems with the official method. During the first step of upgrading, update-manager pops up an error message saying 
>  Failed to fetch [http://archive.progeny.com/symphonyos/apt/./Packages.gz](http://archive.progeny.com/symphonyos/apt/./Packages.gz) 410 Gone


This is the output of gksu "update-manager -c":
> jonne@laptop:~$ gksu "update-manager -c"
warning: could not initiate dbus
extracting '/tmp/tmp7PEHKX/feisty.tar.gz'
authenticate '/tmp/tmp7PEHKX/feisty.tar.gz' against '/tmp/tmp7PEHKX/feisty.tar.gz.gpg' 


/var/log/dist-upgrade/main.log:

> 2007-04-21 16:52:39,958 INFO release-upgrader version '0.59.20' started
2007-04-21 16:52:45,816 DEBUG lsb-release: 'edgy'
2007-04-21 16:52:45,817 DEBUG _pythonSymlinkCheck run
2007-04-21 16:52:58,436 ERROR IOError in cache.update(): 'Failed to fetch [http://archive.progeny.com/symphonyos/apt/./Packages.gz](http://archive.progeny.com/symphonyos/apt/./Packages.gz) 410 Gone
'. Retrying (currentRetry: 0)
2007-04-21 16:53:06,871 ERROR IOError in cache.update(): 'Failed to fetch [http://archive.progeny.com/symphonyos/apt/./Packages.gz](http://archive.progeny.com/symphonyos/apt/./Packages.gz) 410 Gone
'. Retrying (currentRetry: 1)
2007-04-21 16:53:10,587 ERROR IOError in cache.update(): 'Failed to fetch [http://archive.progeny.com/symphonyos/apt/./Packages.gz](http://archive.progeny.com/symphonyos/apt/./Packages.gz) 410 Gone
'. Retrying (currentRetry: 2)
2007-04-21 16:53:10,588 ERROR doUpdate() failed complettely


---

### Post by derspiess on 2007-04-21
Hi, I guess I am getting the same error lots of people are getting.  In Update Manger, I click on the button to update to 7.04 & after some progress, I hit a brick wall with:

Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)


I'm a little hesitant to make changes in sources.list, because I'm not sure exactly what needs to be changed.  Is there any way to do the upgrade (as opposed to a clean install) from Edgy to Feisty with the CD?

If not, I suppose I can wait until traffic dies down or whatever-- not the end of the world, but today is a rare day that I actually have time to work on it.


TIA/Regards/etc. :)

---

### Post by jomonbre on 2007-04-21
Ok, some help needed here, please.

I did the last update and checked that my Update-Manager version was 0.45.2.

Then I used the Upgrade button from the Update-Manager and waited, slept, went to work and went back home to see that some questions about some rewriting of conf files. I checked the changes and went on with the process.

My problem came after returning from a screensaver. I saw the Update-Manager window completely blank. So I decided to wait, and wait, and after 4 hours without any change, I rebooted.

Now, when I boot my machine, the last thing that I see on the screen is:
```
 * Checking file systems...
fsck 1.40-WIP (14-Nov-2006)
/dev/evms/hda2: recovering journal
/dev/evms/hda2: clean, 257993/4938304 files, 2984943/9863910 blocks
                                                                              [ OK ]

```Any clue to solve this?

Thank you in advance

---

### Post by derspiess on 2007-04-21
I tried what I thought was the upgrade via cd method mentioned earlier in this thread, no dice.

I also tried to change the servers in the source.list files as mentioned; also no dice.  Gonna restore the backups I made & just wait.

---

### Post by secular on 2007-04-22
I'll just add my upgrade experience to the thread, for what it's worth.

Before upgrading, I backed up my files and updated everything through synaptic.


I then used "Method 1 - Using GUI" from here: [http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html]("http://www.ubuntugeek.com/upgrade-ubuntu-610-edgy-eft-to-ubuntu-704-feisty-fawn-2.html") .

It took a couple of hours but worked just fine. I've rebooted a couple of times since then, just to see what would happen, but all is well. I didn't have Compiz/Beryl installed, so that likely helped.

I'm glad that I don't have to reinstall my programs and codecs and set up the appearance, theme, Firefox, etc.

---

### Post by AcesAndEights on 2007-04-22
Using the method stated at the beginning of the thread results in this error is terminal: "Could not initiate dbus." The update manager opens, but it finds nothing. So, what am I to do?

---

### Post by Shampyon on 2007-04-22
I used:
gksu "update-manager -c -d"

and it worked almost perfectly. I say almost because, despite having downloaded the Alternate Install ISO no more than ten minuted before starting the upgrade, I still had to go through about six hours of internet updates.
It took six hours because the massive server strain limited my speed at some points, but it was still a lot more downloading than I would have expected.

---

### Post by dolphinsonar on 2007-04-22
I tried using this technique and got this output:

warning: could not initiate dbus
could not send the dbus Inhibit signal: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Ignoring this and clicking "update" results in the window freezing and no progress is visible.  Any suggestions?  I have checked the forums, but I have not found a conclusive solution to this particular problem.

---

### Post by dolphinsonar on 2007-04-22
Jdong solved the problem I was having:

[http://ubuntuforums.org/showpost.php?p=2497099&postcount=13](http://ubuntuforums.org/showpost.php?p=2497099&postcount=13)

Thanks!

---

### Post by Carlo1973 on 2007-04-22
> **Shampyon said:**
> I used:
gksu "update-manager -c -d"




I have tried gksu "update-manager -c -d" as well as gksu "update-manager -c" and the error I get is this:

(gksu:5536): Gtk-WARNING **: cannot open display:


I'm relatively new to Ubuntu, and i've run this command from within gnome from the terminal program in super user mode.

Any other suggestions?

I've downloaded the Install CD but its not giving me an option to upgrade, only a fresh install. And i've matched architectures. x86 for x86 (even tho I have a 64 bit system, my experience as of late with linux 64 distributions is that a lot of things seem to be missing or lacking vs the x86 platform. So until things move along I'll stick with x86)


Suggestions?

Tips?

hints?

Thanks

Carlo

---

### Post by jtsop on 2007-04-23
try from a terminal:

$ sudo su
# export DISPLAY=":0.0"
# update-manager -c -d

---

### Post by jtsop on 2007-04-23
I tried updating but a package that was downloaded did not match its signature and the upgrade stopped. Now I am stuck with 6.10 and even running update manager -c does not give me an otpion to upgrade

---

### Post by frisket on 2007-04-23
> **PWill said:**
> Please, people; if you plan on upgrading to Feisty Fawn 7.04, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

What's the difference between this and clicking on Upgrade to 7.04 in the update manager tool (or is it the same thing?

---

### Post by jtsop on 2007-04-23
it is the same thing!

---

### Post by dweez on 2007-04-23
Carlos1973, in a terminal, do:
```
sudo gedit /etc/apt/sources.list
```If the entries in this file end with "feisty main", "feisty universe", or something similar, then you already have the updated sources.list.  I suspect that since you cancelled the upgrade, the sources.list got updated and now the system no longer realizes you haven't actually ran the update.  I would simply run the following and check in "System"|"About"|"Versions and Release Numbers" to see if it lists 7.04.

Run each line individually, letting each finish before moving on.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```

---

### Post by tombott on 2007-04-23
jomonbre i get the same thing as well. if anybody has got any ideas please let us know.

Regards,

Tom.

---

### Post by datakid on 2007-04-23
Ok, using the official upgrade method for edgy->feisty, I'm getting the following error:

The upgrade aborts now. Please free at least 4542k of disk space on /boot. Empty your Garbage Bin and remove temporary packages of former installations using 'sudo apt-get clean'.

a df -H shows:

Filesystem             Size Used Avail Use% Mounted on
/dev/hda4              213G    46G   157G  23% /
varrun                 514M    99k   514M   1% /var/run
varlock                514M      0   514M   0% /var/lock
procbususb              11M   107k    11M   2% /proc/bus/usb
udev                    11M   107k    11M   2% /dev
devshm                 514M      0   514M   0% /dev/shm
lrm                    514M    19M   496M   4% /lib/modules/2.6.17-11-generic/volatile
/dev/hda1               62M    21M    38M  36% /boot
/dev/hda3              100G    42G    59G  42% /media/hda3
/dev/hdc               3.9G   3.9G      0 100% /media/cdrom0


As you can see, /boot has plenty of room for 4542k of disk space.

Something is wrong somewhere, methinks? Any ideas appreciated.

Cheers

---

### Post by Karl S. on 2007-04-23
datakid.

Look in [this thread.]("http://ubuntuforums.org/showthread.php?t=414639&page=3&highlight=%2Fboot+size+feisty")

---

### Post by Carlo1973 on 2007-04-24
because of the buggy upgrade process I decided to download and burn the cd image and start from scratch basically. Lucky for me this wasn't so bad. I've learned from experience that its a good idea to have your /home directory on a seperate drive from your system files. So I through the cd in and started the live environment. I wanted to see if there was an upgrade script like in Edgy... There wasn't. How odd.. I have to asume that because there was no update script made either they inteded that 7.04 be installed fresh, or they had suspicions of possible upgrade issues but weren't 100% sure untill release time.

Anyhow, installing fresh worked. I had to reinstall all my software (luckly I'm a packrat and had stored under my /home folder - which is on a secondary drive as a full 40gb - where the main / folders and files are located under my primary drive at 120gb of space available to it).  Installed 7.04 fresh. Reinstalled my software (including GyachiE) and things seem to be working overall quite well. No crashing. No issues. I find the packages seem to install better with less errors of missing dependencies. All is good so far.

Besides I really had nothing to loose. A few software packages I would need to reinstall. I realise this isn't good for anyone who's been using Edgy for quite sometime, but i've only been using it for about 2 months. I had nothing to loose by re-installing. I was worried about my email but thankfully that to was stored under my /home folder.

To those who are starting out or reltively new to Ubuntu who have nothing to loose by reinstalling - This is probably the best and safest way to do it. I hope that the creators of Ubuntu do monitor this board and see that their update process needs a bit of fine tuning. But from what I understand this was one instance in a long history of success (and anyone who's run windows that nothing is flawless in this world - especially at release time lol).  More power to Ubuntu and its users :)



And I know I shouldn't be typing at 2:44am when I've only had 1 cup of coffee the whole day cause I ramble and make no sence LOL Okay off to bed lol 

I think I shall stick with Ubuntu awhile longer and see how things go. My history with Linux has been 2 months here and there for any particular flavor. Sabayon, Fedora, Slackware, etc etc.  So far Ubuntu is the most user friendly - to us people who are trying to migrate away from windows.

Oh speaking of migrate... When I did my fresh install it saw my windows installation on my drive. It then said it would migrate the information and settings from windows into Ubuntu under my main profile.. But what in the world for? I dont see it anywhere. I dont seem to have access to it... and it doesn't seem to be associated with anything in KDE or Gnome...  Anyone know what thats about?


Okay i'm done ranting

Night

Carlo
LOL
:lolflag:

---

### Post by nardis_Miles1 on 2007-04-25
I am trying to use the official upgrade method. I'm going through an apt-cacher. The installation is hanging with many size-mismatch errors and MDSUM errors. Are the servers simply slammed, or are there significant bugs in the upgrade.

Also, why can't we use the simple (what was called hacky) way to upgrade. Namely change the repositories and aptitude update & aptitude dist-upgrade?

---

### Post by MikeB5862 on 2007-04-25
I've tried ALL methods... nothing works.  I keep getting this error message:  Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1) .......

What the hell does that mean.  Guess I'll not be upgrading to 7.04 Feisty Fawn

---

### Post by GuiGuy on 2007-04-25
> **Carlo1973 said:**
> 
To those who are starting out or reltively new to Ubuntu who have nothing to loose by reinstalling - This is probably the best and safest way to do it. I hope that the creators of Ubuntu do monitor this board and see that their update process needs a bit of fine tuning. But from what I understand this was one instance in a long history of success (and anyone who's run windows that nothing is flawless in this world - especially at release time lol).  More power to Ubuntu and its users :)


Also good advice for those of us who have been struggling along for some years. 

It went pearshaped for me when I "upgraded" to 6.10 and it fell over big time when I tried the current upgrade. But this time I had a back up image. Ha Ha!
:) 

regards

---

### Post by nardis_Miles1 on 2007-04-25
GuiGuy

Thanks for your response. However, if I were interested in reinstalling every time I had an update, I would use Windoze. I come from a debian background. In fact, my firewall machine still runs debian stable. Updates on debian can always be "hacky" (read simple) and, with some little pain, do not require reinstallation.I have no interest in rebuilding ATLAS, for example, and other, third party tools. I do hope ubuntu can straighten out its repositories, because that seems to be the problem.

---

### Post by tombott on 2007-04-25
your busy today then, post reported

---

### Post by arvevans on 2007-04-25
> **MikeB5862 said:**
> I've tried ALL methods... nothing works.  I keep getting this error message:  Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz](http://archive.ubuntu.com/ubuntu/dists/edgy-updates/universe/binary-i386/Packages.gz) Sub-process gzip returned an error code (1) .......

What the hell does that mean.  Guess I'll not be upgrading to 7.04 Feisty Fawn

==============
Same here.  I have tried the officially sanctioned method many times and it always hangs on:

[INDENT]
[COLOR="Red"]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error cod[/COLOR]e (2)[/INDENT]

Posting to the forum doesn't get any help.

I guess they rushed this out the door before it was really tested (sounds like Microsoft...?), probably hoping that the users would fix their problems.  I'm going to stick with Edgy 6.10 for a while longer until all the screams of pain & suffering calm down a bit.

Arv
_._

---

### Post by Carlo1973 on 2007-04-26
I think thats probably for the best. As I said. i"m realtively new to Ubuntu. I had nothing really to loose and I know its not ideal for someone to reinstall everything fresh - not if they have been using the system for quite sometime. 

I also dont really lay blame on the Ubuntu team or programers. It happend. It was unexpected. Its hard to account for every unexpected thing, cause if they did, then it wouldn't be unexpected now would it.  I wouldn't go  comparing them to Microsoft because of this incident. From what i've read in older forums and older blogs, people have had little problems using the upgrade scripts and features in the past. Something broke this time. I'm sure it has taken them by suprise and I'm sure they are trying to find out exactly what happend in order to fix and avoid the same issue again in the future. 

The reason why I chose Ununtu is because of its user friendlyness for someone who is realtively new or inexperienced with the back end of linux, but robust and powerful enough for more advanced or pro people. It has a good support network. It doesn't crash easily. Its flexible. After the other flavours I've tried this is still my favorite despite the issues that have creeped up. 

Something like this is gonna be hard for them to pin point the exact problem because there are actually multiple issues here happening. Over loaded servers, Servers that either dont have certain files or have outdated files, some people are reporting that their PC's are no longer even booting to Ubuntu anymore - kernel crashes, Grub/lilo crashes/corruption, I've read about software crashing, stuttering and even failing to run properly.   I'm sure everything seemed to be working okay on their end when they anounced the release. Something just broke. Although I do have to admit, that some of my software that I had downloaded that worked with Edgy flawlessly, is no longer so flawless anymore now that I have installed Fiesty (Fresh installed). No real crashing, its just not working lol So I cant generate a bug report or get any kind of crash output. An example would be I installed GyachiE ([http://gyachi.sourceforge.net/](http://gyachi.sourceforge.net/)) which is a full featured Yahoo messenger replacement. It worked fine in Edgy. In Fiesty, it works, but when I load up my webcam it seems to work okay till I click anywhere on the screen. The cam application freezes. Whats really funny about its freeze is that it just stops. I get no crash error. Just stops. It wont let me close it. I get no option to force quit. Its just - well. Stopped lol So I have to reboot to clear everything off my screen lol. Oh well. I'm sure they will get the bugs out. Hopefully sooner rather than later. Right now i'm gonna play around with Fiesty a bit longer. If I cant figure out why the cam stopped working properly in Fiesty, i'll go back to edgy.

The other thing I cant figure out - that maybe others can, is how to get my Radeon All-In-Wonder (Ubuntu identifies it as a Radeon 7200 series) to work the TV capture side of it. I cant get the tuner to work for the life of me. Fiesty has v4l2 but its not identifying my capture/tuner card properly. Just says "Unknown" It works in Windows okay. But I cant get it to work in linux. I know about 4 years ago I had got it to work fine in Redhat/Fedora (although I had to remove my webcam to make it work cause it was an either or type thing) but I dont remember how or even if those steps would still be relevant today. 

Anyhow happy teching

Carlo

---

### Post by tjk on 2007-04-26
> **arvevans@earthlink.net said:**
> ==============
Same here.  I have tried the officially sanctioned method many times and it always hangs on:

[INDENT]
[COLOR="Red"]Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2](http://security.ubuntu.com/ubuntu/dists/feisty-security/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error cod[/COLOR]e (2)[/INDENT]

Posting to the forum doesn't get any help.

I guess they rushed this out the door before it was really tested (sounds like Microsoft...?), probably hoping that the users would fix their problems.  I'm going to stick with Edgy 6.10 for a while longer until all the screams of pain & suffering calm down a bit.
_._

Ditto, ditto and ditto

Unfortunately I don't think waiting will help ... it's been out for some time now and I don't see any significant changes to the upgrade manager.  Seems they've messed up pretty bad this time -- it's too bad, things like this can really set back Ubuntu's positive reputation -- especially as being user friendly and bug free.  

I'd like to see a poll on who had problems upgrading, who had an uneventful (pleasant)  upgrade and who couldn't upgrade using the "manager"  because of insurmountable problems...

---

### Post by regeya on 2007-04-26
Yah; I flipped a coin and heads was Dapper and tails was Etch.  I got tails.  Unlike the Feisty installer my LVM2 volume was found and my drive controller was identified as an Ultra ATA card rather than a SCSI card.  

Yeah, yeah; I know, Dapper is the stable version.  But I went Dapper -> Edgy because of promised bug fixes and Edgy -> Feisty because of more fixes.  I didn't expect a "release" to mean "this will not work for you, ever." 

Ah, well; 'twas a good run, Ubuntu.  May your next release actually work.  Hopefully someone will let me know if it does or not.

---

### Post by nardis_Miles1 on 2007-04-26
First, I have heard on the mailing list that many people had been successful with the debian (hacky) way of simply pointing to the feisty repositories and using apt-get update and apt-get install.

My biggest dissapointment is in the ubuntu development community. This is a very nice forum environment, kind of like H2G2 (don't panic) except that no one monitors a thread like this. If there's a problem, ubuntu should own it. They should post that they are, in fact, having problems with either the upgrade manager or with the repositories (my guess). Even if they said "sit tight, we are working on it," I would have confidence. 

Believe me, if I have to reinstall now, it will probably mean going back to debian, or possibly trying the new sidux distribution.

Very sad.

---

### Post by usererror on 2007-04-27
> **nardis_Miles1 said:**
> First, I have heard on the mailing list that many people had been successful with the debian (hacky) way of simply pointing to the feisty repositories and using apt-get update and apt-get install. Very sad.

That was harsh dude!  If you don't like the community then leave!  This is all free stuff, so don't expect everyone to be here 24/7.  Ubuntu development isn't a full time paying job, it's a full time volunteer job, to the best of my knowledge.

In any case, I did have a problem doing the upgrade on my 3rd desktop.  My first two were flawless.

The problem on the 3rd one was not an Ubuntu Problem but a 3rd party repository I had added to my sources.list, I disabled it, since the URL Path no longer existed on the host...then reran the upgrade tool and now it's going fine! :D

---

### Post by Carlo1973 on 2007-04-27
Just thought I'd let you guys know. I was surfing the net looking to find a way to setup NTFS in fiesty (although I'm going back to Edgy, to many of my softwares are locking up) and fell apon a user guide for Ubuntu Fiesty [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)    Searching through it I get to what I'm looking for which links to this site: [http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html](http://www.ubuntugeek.com/widows-ntfs-partitions-readwrite-support-made-easy-in-ubuntu-feisty.html)

Now why am I posting this? because scroll to the bottom of this page. You come across the "Related Articles" section. One being "Ubuntu Edgy Upgrade Common Problems With solutions"

I dont know if this will help you guys any. As I said I fresh installed Fiesty, its not working out for me. was stable for about 3 days then my software that used to work in Edgy started freezing and halting without rhyme or reason, so back to Edgy I go.

Carlo

---

### Post by jerrylamos on 2007-04-28
> **PWill said:**
> Please, people; if you plan on upgrading to Feisty Fawn 7.04, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

(Admins, can this be posted as a sticky? People need to see it...)

Hi, we're enjoying Feisty Fawn, HOWEVER there seem to be a Bugs that hit quite a few of us.  Now if we dig thru Launchpad we can find some fixes by Canonical and other developers, see my post "Workarounds" in this Installation & Upgrade forum.

I think it would save a bunch of users frustration & time if there were a "Sticky" posting on Installation and upgrades with some of the more sanctioned solutions such as Ben Collin's fix for the widely experienced "can't access tty" bug #106864.  Ben's fix, buried in Launchpad, isn't widely seen judging by the number of people that run across the situation.

So how about it, a Sticky suitably titled?

Thanks, Jerry Amos:)

---

### Post by nardis_Miles1 on 2007-04-28
> **usererror said:**
> That was harsh dude!  If you don't like the community then leave!  This is all free stuff, so don't expect everyone to be here 24/7.  Ubuntu development isn't a full time paying job, it's a full time volunteer job, to the best of my knowledge.

In any case, I did have a problem doing the upgrade on my 3rd desktop.  My first two were flawless.

The problem on the 3rd one was not an Ubuntu Problem but a 3rd party repository I had added to my sources.list, I disabled it, since the URL Path no longer existed on the host...then reran the upgrade tool and now it's going fine! :D

First, quoting is a good idea, but quoting out of context is not. The "very sad" came at the end of my post ( a paragraph away) from my lament that developers were not announcing bugs. It had nothing to do with the hacky way of upgrading.

Second, it is true that this is free stuff. I serve as sys-admin on a debian-based Beowulf cluster (~45 nodes) and on probably four production debian (testing) machines at a government laboratory. I also sys-admin on six ubuntu machines and one debian (stable) at home. My interest is professional more than personal. We use, for example ATLAS, that, for optimal performance, requires about a two hour, unattended tuning session. For me re-installation to overcome some fundamental upgrade issues is not a welcome option. For many years (since 1997, when I installed RH 4.0!, and 1999, when I switched to debian)  have been quite willing to role my own kernels, and to work through bugs. My point is that ususally, on the analogous debian lists, many of the developers look to see what's going on and offer suggestions. I have posted several times on this forum and on the user mail list with no indication that the problem is acknowledged. My "very sad" is a personal response because in many ways ubuntu is a good idea. However, leaving a released distribution (including an announcement at the top of the upgrade manager) unattended when the download itself fails with errors like "size mismatch" and "MD5SUM error" is crucial. These appear to me to be repository issues. When the list and forums go dead for days, I'm left with no tools to address this problem. Even if ubuntu developer said, "No, others are still able to download successfully, so this is not a repository issue," I would then purse other avenues. Better still would be "you did ..... wrong."
They could even start with a "Hey stupid," and I wouldn't mind.

Finally, if this were on an isolated machine, I wouldn't be so insistent. However, on three out of three 32 bit installs, I have had the same failure mode. I'm wondering whether the 3rd of your desktop-upgrades happened a few days after the two successful upgrades. This would be consistent with a degradation of the repositories.

---

### Post by Pietr The Engineer on 2007-04-28
39 of 40?
You were lucky!
Of course, we had it hard; when we started to try to upgrade and for each attempt since  release, no files were downloaded and all of them were supposed to come from ntfs-3 and sweetsitesweet.
I wouldn't expect there still to be server issues at this stage.
Any ideas?:confused:

---

### Post by nardis_Miles1 on 2007-04-28
Can you say which thread your workaround post is? This is a very large topic\

Thanks

---

### Post by bdalzell on 2007-04-30
I have Ubuntu on two systems - the laptop is an old pentium 3 Gateway with a 802.11b wireless card. The wirless worked fine with our Apple Airport when I had Edgy installed.

So last night I clicked on the offered Update button in Synaptic and the Feisty update downloaded itself and installed itself and now I have no wireless card appearing in my Network Settings GUI. When I try manual configuration there does not seem to be a way to add a wireless card to it.

I can go and trash the Feisty installation and put Edgy back and I am certainly not going to put Feisty on my work machine until this problem is worked out.

How do I get back the wireless card?

---

### Post by DarkStarAeon on 2007-04-30
I don't know how to help you with your problem, but sounds like you should have started by using the official upgrade method. Best of luck.

---

### Post by DarkStarAeon on 2007-04-30
Lovely, not only did that spambot hit the forums, but for those of us subscribed to a topic we got an email with the spambots post too. greeeat.

I hate spammers.

---

### Post by houstonbofh on 2007-05-01
> **bdalzell said:**
> I have Ubuntu on two systems - the laptop is an old pentium 3 Gateway with a 802.11b wireless card. The wirless worked fine with our Apple Airport when I had Edgy installed.

So last night I clicked on the offered Update button in Synaptic and the Feisty update downloaded itself and installed itself and now I have no wireless card appearing in my Network Settings GUI. When I try manual configuration there does not seem to be a way to add a wireless card to it.

I can go and trash the Feisty installation and put Edgy back and I am certainly not going to put Feisty on my work machine until this problem is worked out.

How do I get back the wireless card?
Knowing what card helps.  And how you connect is something to look at before the upgrade. :)  Post in Absolute Beginners with the card brand and model in the subject.

---

### Post by inphektion on 2007-05-03
I'm trying to upgrade an edgy eft server to feisty following this:
Install update-manager-core: 
sudo apt-get install update-manager-core

Launch the upgrade tool: 
sudo do-release-upgrade

Well first I got "Couldn't find package" when trying to install update-manager-core.  I then added edgy-proposed to my sources.list and then that successfully installed.  Now when I run do-release-upgrade I get this:

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/restricted/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.6 80]
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/universe/binary-i386/Packages.gz) 404 Not Found [IP: 91.189.89.6 80]


should I just use the live cd or are the sources just not available??  Should I just wait a week or something?  Weird when the recommended method they put on their site gives so much trouble.

---

### Post by lunadesign on 2007-05-03
I'm pretty certain that the reason I had trouble with the upgrade was a conflict in my sources file. It may have been that I had the right sources but because I had made quite a few edits and additions they were somehow compromised. That's my theory anyway. 

I just selected all and deleted my repositories, replacing them with the ones I got from here:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/) 

Or you could use the CD.

Good luck,
Andrew

---

### Post by Janisok on 2007-05-04
Spam.

---

### Post by jerrylamos on 2007-05-04
Wow.  Some of those URL's.  Anyway, for the "unofficial" method of upgrading Feisty to whatever pieces of Gutsy are available, I just changed "feisty" to "gutsy" in sources.list, enabled every Synaptic repository in sight, and did update/upgrade.  And by the way, saw a later kernel 2.6.22-1 on Synaptic and installed that.

So it's running (at the moment) and I have gotten some automatic upgrades and fixes.  Now if this method didn't work, not to worry, this is a quad boot system with Dapper, Feisty, and partly upgraded Gutsy, and so far at least one of them is running at any one time....

Cheers, Jerry:)

---

### Post by Scrappy_D on 2007-05-04
Using the Official upgrade method killed my PC  .... everything went great until the reboot and then bam .... Lost all my data (yes it was very important!) Am not impressed and seriously consdering other options ... Fedora Core is looking good at the moment ....


Why is there no recovery options with the live CD's (none are abvious!) .... get a grip, not all people have the time to be geeks and those who try often do not have the time!


I'm really pissed .....

---

### Post by Scrappy_D on 2007-05-04
You would think there would be an option or warning about backing up data .... but oh no, they are too bothered about the new fancy online upgrade shite and you are just a test dummy so you dont matter  ..... Well great, maybe in 10 years when it actually works I might look at it again but for now I'll stick with what actually does work and is not a fantasy ......

---

### Post by tombott on 2007-05-05
> **Scrappy_D said:**
> Using the Official upgrade method killed my PC  .... everything went great until the reboot and then bam .... Lost all my data (yes it was very important!) Am not impressed and seriously consdering other options ... Fedora Core is looking good at the moment ....


Why is there no recovery options with the live CD's (none are abvious!) .... get a grip, not all people have the time to be geeks and those who try often do not have the time!


I'm really pissed .....

Frankly if you choose to upgrade any OS without backing up your data first then your a f**king idiot.

To a certain extent I agree with you with regard to the recovery option, but then on the other hand Ubuntu is so easy to configure and install software for that if you've backed up your Home folder it takes no time at all to get things up and running again.

> **Scrappy_D said:**
> You would think there would be an option or warning about backing up data .... but oh no, they are too bothered about the new fancy online upgrade shite and you are just a test dummy so you dont matter ..... Well great, maybe in 10 years when it actually works I might look at it again but for now I'll stick with what actually does work and is not a fantasy ......

It's a shame to hear you had such problems, but bear in mind this OS is free! I happen to think the people who have made Ubuntu have done a superb job.

---

### Post by redmarkerdown on 2007-05-05
:lolflag:

---

### Post by finalzero on 2007-05-05
I happen to think this is the buggiest pile of s... release of Ubuntu yet.  I loved Ubuntu 6.10 due to its polished feel.

The new release breaks so many rules and as MANY people have noted, the upgrade process is a joke.  The only way to resolve a bricked system is to then downgrade to Ubuntu 6.10 (doing a clean install) and then upgrade up to 7.04 where it then preserves the disk structure.

I am seriously considering Debian again, at least I have control over the system (wtf is up with treating my Raptor IDE drives as SATA and then running in 16bit mode?!)

---

### Post by YorYor on 2007-05-06
I personally have had a seemingly smooth and troublefree upgrade process, on my Presario R3000 from Edgy to Feisty.

I'm of the opinion that doing anything to something already working is a risk. As they say, "don't fix it if it ain't broken". What happened to the approach to OS?
I didn't start the upgrade immediately because I was a little concerned that it would affect my main working platform (all my office work and development codes are in it), and that if anything went wrong with the OS I'd have to spend some time reconfiguring everything. After 2 weeks, and having experimented with Feisty on another desktop, I thought "hey, I would like to have a good integrated and working network applet so that my wireless configurations would finally be able to be saved correctly", so I took the plunge and did the upgrade.
Why blame Ubuntu for the upgrade process not being as smooth as everyone hopes for? If you are using the exact same hardware and software packages and the upgrade blipped for you, then perhaps there is a reason to grouse.
The development team has done exceptionally well in my opinion, for being to push out the release on time. I'm not equating Ubuntu to Windows, but you pay for Windows and still you can get botched up systems due to hardware incompatibility, or upgrade failures. But why is it oh-so-natural to just say "oh well, too bad, it's windows again. time to format and reinstall"?

As with any new OS/Distro/Release, it's always best to test install it first to determine suitability before deploying it live. But well, not everyone has basic decency to show some form of appreciation for something that is free. Some people are just so self-centric that they expect the world to bend over backwards for them.

---

### Post by mjgumbley on 2007-05-07
Well, it's nice to know that those wo use the LTS releases should stick to those, and not the intervening untested/unstable releases. The 6.10/7.04 releases need some serious branding to indicate that they're for enthusiasts. I agree entirely with iposner here - the likes of Dell are simply NOT going to cope with the level of mess that the Edgy/Feisty upgrades have caused - untested upgrades like this have more than likely knocked Ubuntu's reputation.

Is it possible to have a Feisty.1 patch release that upgraders can take that'll fix all the breakage?

I'll be sticking to LTS releases from now on - and more than likely waiting a few months so that all the breakage they introduce is documented/fixed.

And I'm seriously looking at Fedora again - I have been so badly let down by Ubuntu upgrades (to Edgy; to Feisty).

---

### Post by finalzero on 2007-05-08
I hear you, I am burning Debian as I write this, okay its not bleeding edge like Feisty but at least its tried and tested and I will have control over how I want my OS to be packaged together - shame, I was really hoping Feisty would bring Ubuntu into the mainstream a little more.

---

### Post by Josh Kurtz on 2007-05-12
> **finalzero said:**
> I hear you, I am burning Debian as I write this, okay its not bleeding edge like Feisty but at least its tried and tested and I will have control over how I want my OS to be packaged together - shame, I was really hoping Feisty would bring Ubuntu into the mainstream a little more.

Isn't Edgy pretty tried and tested?  Why didn't you just stick with that if you wanted tried and tested?

I don't get it how people can get so upset when a*** free ***OS upgrade that hasn't been out for a month yet messes up their system.  And isn't it basic common sense to back up your data before you make some big changes Scrappy D?  

I'll just sit back and enjoy the show, waiting for a little longer before I upgrade or until I have a reason to.:popcorn:

---

### Post by DarkStarAeon on 2007-05-12
Yeah Edgy was really stable, why not just stick with that?

Despite the upgrade issues I had, which weren't that bad in retrospect, Feisty has been running really nicely since I got it running, I am glad I upgraded.

---

### Post by Josh Kurtz on 2007-05-13
DarkStarAeon, how did you get that desktop theme set up?  Did you download the theme or just tweak it yourself until it looked like that?  It looks great!

---

### Post by kamaboko on 2007-06-02
hmmm...and how many posts have i read in other threads about how "easy" and "intuitive" linux is?  lol.  i'll stick with edgy.  if it ain't broken, don't fix it.

---

### Post by castoroil97 on 2007-06-02
Hello all, I am sure I can find an answer with my ubuntu family.
I have 6.10 on a Toshiba Sattilite model L35-S2171
1.6 Ghz Celeron 512 MB RAM.  I tried to update to 7.04 and got the following error:

Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)
Failed to fetch [http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2](http://archive.canonical.com/ubuntu/dists/edgy-commercial/main/binary-i386/Packages.bz2) Sub-process bzip2 returned an error code (2)



thanks in advance!

---

### Post by boby11 on 2007-06-15
thank you.

---

### Post by nickabram on 2007-06-19
[IMG]http://s3.bitefight.gr/c.php?uid=16049[/IMG]

---

### Post by azadian on 2007-06-22
Pardon my ignorance, but what is a 'gksu' ?  The man page helpfully says "GKsu - manual page for GKsu version 1.9.0".

Furthermore, what is an update-manager?  I have no manpage at all for this.

I'm trying to cure myself of the habit of leaping over cliffs without at least looking first.

---

### Post by smartboyathome on 2007-06-22
Update-manager: it updates your system when needed.
GKSU: it is the graphical form or SU.

---

### Post by CescoAiel on 2007-07-01
Well, just upgraded my server from 6.10 to 7.04 using the official upgrade method, and am already regretting it!

It was unable to upgrade update-manager and MySQL 5.0 (which I use for several different packages!!!)

Furthermore after reboot, the GUI does not come up after log in, EVEN WHEN USING SAFE-MODE GNOME!

I am now *removing* all X11 elements (ie all XOrg stuff *and* all X11 apps!) and will reinstall it after it is done!

I *really* hope that works, because if it doesn't I'll be really pissed, as it is nigh impossible to install Ubuntu on an MD Raid5 array without having a boot-disk outside of the array (which I do not want, simply to preserve as many slots for drives to add to the array as needed)

So much for the 'official upgrade method'!   :(

---

### Post by CescoAiel on 2007-07-01
Remove and reinstall (with deleting all gconf and gnome related folders, etc.) did not help, but 'pkill -SIGKILL -f dbus' does!

So now I have to figure out:
[LIST]
[*]How to get dbus working without stalling XOrg/Gnome session startup
[*]How to get mySQL working again
[*]How to get update-manager installed again
[/LIST]


#-o ](*,)

So much for a 'problem-free' upgrade! (And I even gave it 2 months before doing the upgrade! *sigh*)

---

### Post by Hachi-Roku on 2007-07-03
> **inphektion said:**
> I'm trying to upgrade an edgy eft server to feisty following this:

Error during update
A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/restricted/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/restricted/binary-i386/Packages.gz) 404 Not Found 
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/universe/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/edgy-proposed/dists/main/universe/binary-i386/Packages.gz) 404 Not Found 


should I just use the live cd or are the sources just not available??  Should I just wait a week or something?  Weird when the recommended method they put on their site gives so much trouble.

Hey all! 
After ubuntu friends telling me good things about fiesty. I backed up and tried the official method, after making changes noted by Jdong, and i get the same "404 not found" errors. It's now july so servers shouldn't be overloaded.

Anyone found a cure yet?

---

### Post by fcp on 2007-07-04
I tried the official method and get the following:
fcp@fcp-desktop:~$ gksu "update-manager -c"
warning: could not initiate dbus
extracting '/tmp/tmpCTxiqs/feisty.tar.gz'
authenticate '/tmp/tmpCTxiqs/feisty.tar.gz' against '/tmp/tmpCTxiqs/feisty.tar.gz.gpg' 
exception from gpg: GnuPG exited non-zero, with code 131072
fcp@fcp-desktop:~$ 


I also tried just sudu update-manager but got the same result.  Int eh gui teh update manager starts and runs.  I click on upgrade to 7.04 and confirm that I want it.  Two files get downloaded and then I get an error saying there is a problem with the network or the server.  

Any ideas?

Help!

Thanks
fcp

---

### Post by Hachi-Roku on 2007-07-07
I tried updating edgy first. Still got all the same strange errors i was getting.... so in the end i just backed up and did the install cd style. SO MUCH MORE PAINLESS. You have to set up everything again....but thats way less of a drama than updating!!!

Feisty runs pretty good!

J

---

### Post by morvael on 2007-07-09
My update from alternate cd went smoothly and without problems. Only evolution icon was missing and apache2 had to be installed which is great improvement since during previous updates I had to recreate my desktop or fix symlinks to sun java. Now everything works :) Note: my system was installed as 5.04 2 years ago and updated through 5.10, 6.06, 6.10 to 7.04!

---

### Post by Copter on 2007-07-18
Hi!

I have to disagree with statement that upgrading by gksu "update-manager -c" is a safe method. In my case (Xubuntu 6.10 -> Xubuntu 7.04) after 7 hours of downloading and installing 1171M of 1200 packages (worst than in Win XP) and after the reboot my system crashed badly. Restart ended up in the terminal logged as root with messages from fsck that my root partition is missing superblock or it is broken. After some digging I found that my hardisk was not any more in /dev as hda1, hda2 and so on but as sda1, sda2 ... Grub's menu.lst was modified so instead of /dev/hda8 it used UUID but /etc/fstab was untouched. I had to change it manualy. Now everything works fine.

Some time ago I read a post titled like 'Is Ubuntu ready for desktop?'. Now I know the answer - not even close.

One thing that was successful after all was my PCMCIA wifi card (DWL-650+). It stiil works fine. Previously after Dapper to Edgy upgrade it was broken.

good luck to all,
copter :]

---

### Post by rolnics on 2007-07-21
Well I decided to take the plunge and upgrade last night. After two error messages, and searching forums to find that if you get a "failed to fetch" blah blah "error code (2)" error you need to remove automatrix repos, it was all fine. 
I don't know why I was getting sound issues with the livecd, cos I ain't getting them now. (fingers crossed) Now to try Ubuntu Studio me thinks!

---

### Post by mulder_edu on 2007-07-21
The official install killed on me too.  What I had to do was download ALL available updates prior to the upgrade.  Once I'd installed the available updates for Edgy Eft (is that how it's spelled?), I was able to run the upgrade tool.
Just a thought.  So if you have trouble, try that first.

This was running Ubuntu, by the way.  Not Xubuntu or Kubuntu.

---

### Post by cjpetrie on 2007-07-22
I'm a newbie but have installed the last to versions of Ubuntu from disk. I wanted to try
to go to 6.10 online, so I tried gksu "update-manager -c"

The GUI goes through the first phase of upgrading, loading many files, but ultimate 
fails with the error that it could not reach:
  [http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz](http://us.archive.ubuntu.com/ubuntu/dists/edgy-updates/main/binary-i386/Packages.gz)
However, this site is reachable via my browser.
The system always aborts after "modifying the software channels". What I see in the
shell is
$ gksu "update-manager -c"
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
extracting '/tmp/tmp_WQ8p-/edgy.tar.gz'
authenticate '/tmp/tmp_WQ8p-/edgy.tar.gz' against '/tmp/tmp_WQ8p-/edgy.tar.gz.gpg'

Does anyone have any suggestions other than trying to upgrade from disk?

Thanks, Charles

---

### Post by KJ55 on 2007-07-25
I also used the alternate CDs to upgrade from 6.06 to 6.10, and from 6.10 to 7.04.  I had no problems afterwards.  I had to use this upgrade path due to my slow dial-up Internet connection.  I still ended up having to download approximately 250MBs of updates though for 7.04...took forever.

---

### Post by Dead_$partan on 2007-07-26
Are there any differences from upgrading to doing a fresh install?

The reason I asl is because anytime I have tried doing upgrades as opposed to fresh installs the upgrade overall look isnt what it would be if I installed afresh.

What I mean by this is the looka nd shapoe of icons stays the same as the older version, or a splash screen and desktop wallapapers are missing or not updated to what the new dist should display,lots of little things like that dont seem to be installed when doing an upgrade.

I hope this makes sense, if so does anyone know if I am doing something wrong?

---

### Post by bribaetz on 2007-07-26
well its pretty much been beating a dead horse try to do it officialy

---

### Post by wpollans on 2007-07-28
Hello,

I had been running Dapper LTS on my Dell Inspiron 700m laptop ever since it was released.  A couple of days ago I decided, more out of boredom than necessity, to upgrade.

I used the "official method" (update-manager -c) to upgrade to Edgy.  It took about 1.5 hours.  The only problem I had was that firestarter couldn't find it's config file - reinstallation of firestarter fixed that.

After a little cleanup (removal of unused packages via synaptic), I decided to try it again.  An hour and a half later, Feisty was up and running with no problems.

Everything appears to be working fine.  I assume that minor problems will surface - this was, afterall, a major upgrade and it may take an old Dapper guy a little while to get used to how Feisty works.

Thanks Ubuntu folks


Waren

---

### Post by frisket on 2007-08-01
> **PWill said:**
> Please, people; if you plan on upgrading to Feisty Fawn 7.04, use the OFFICIAL upgrade method:
```
$ gksu "update-manager -c"
```

This really isn't useful, especially to newcomers. 
What's wrong with clicking "Upgrade to 7.04" in the regular updates GUI (whatever it's called)?

---

### Post by merlin666 on 2007-08-10
I have tried updating about 5 times in the last few months and was not successful. Fortunately, I was able to restore the edgy functionality. It seems that there may be different versions of the upgrade manager that cause various effects. I have a slow DSL connection and downloading the packages takes about 8 to 12 hours, so when I come back after many hours and I see that it did not work is somewhat frustrating. 

Anyway, I have received the liveCD and I am wondering if the upgrade can be done using the liveCD? The gksu path suggested on the upgrade page certainly is not there.

---

### Post by LaneLester on 2007-08-26
The only way I feel safe upgrading to a new version is by having two partitions on my first hard drive: one for the version that's now working and one for the new version to be installed from scratch.

If the new install goes OK, then I start to tweak it with stuff from the old partition. I have a text file of notes of changes to make. It's somewhat tedious, but I will never lose everything that way.

It also makes it possible to try "bleeding edge" releases without too much danger. I've tried Gutsy 4 & 5 recently. The install went fine, as did the Nvidia driver install. But when I let Synaptic do an update, I lost the ability to boot to Gutsy. So I just edited its menu.lst to put Feisty back at the top, and I'll wait for the next release. :)

Lane

---

### Post by masters09 on 2007-09-08
Hi I am a new with UBUNTU ...:confused:
but actualy started with penguin linx...this forum is great !:guitar:
Thanx alot guys !:lolflag:
:guitar::guitar::guitar:
Masters09

---

### Post by Noviesse on 2007-09-09
Hello,

I did download kubuntu gusty and recorded to cd, so i tried install gusty to my new laptop by this cd. but it didnt work.

My laptop intsalled just freedos, i need format etc.?

---

### Post by abhilash82 on 2007-10-08
Can the admin post a Sticky on the possible methods(safe) to upgrade to Gutsy from Feisty? And also list out the benefits of fresh install compared to a network update?

:lolflag:

---

### Post by mmxbass on 2007-10-12
I could not disagree more strongly with this. I have never ever seen update_manager do a better job than apt or adept. There's a reason that adept is the recommended method for upgrading Debian proper. The fact is that apt and adept are far more mature pieces of software.

---

### Post by zoot_ on 2007-10-14
Hi

I'm no Debian/Ubuntu guru but have used Ubuntu for a few months on my laptop and would like to upgrade from Feisty to Gutsy.

If I have the Gutsy beta CD (ie already downloaded packages), how would I go about using

gksu "update-manager -c -d"

but telling update-manager to use the packages I already have on the beta CD?

I assume it will look in the usual apt cache? If I don't have sufficient disk space, how would I go about this without being able to copy all the new packages into the cache?

By the way, the beta CD fails when I try a normal install, as per the numerous bugs reported... hence my trying this route.

Thanks

---

### Post by houstonbofh on 2007-10-15
First, toss the beta CD and get the RC or the daily build.  There have been a LOT of patches.  Now once you have the latest CD pop in in, and you can try to click "Run Upgrade" from the window that appears.  I am not that daring. :)  The other way is to run the cdromupgrade script.  Call it with the "real" path of /cdrom/cdromugprade and watch the magic happen.  Of course, remove Envy or other compiled drivers first.

---

### Post by paxmark1 on 2007-10-17
I got rid of automatix a couple months back.  I religiously use aptitude for updates.

I did the sed script to go from feisty to gutsy in /etc/apt.source.list   and then
sudo aptitude upgrade and then sudo aptitude dist-upgrade

It worked like a charm.  I had been nervous because I had gotten rid of all but mplayer (xine, totem, etc.) and also scanner stuff I did not use.  

It was my easiest update ever.  peace, mark

---

### Post by johann_p on 2007-10-18
> **abhilash82 said:**
> Can the admin post a Sticky on the possible methods(safe) to upgrade to Gutsy from Feisty? And also list out the benefits of fresh install compared to a network update?

:lolflag:

And maybe also discuss the disadvantages of a fresh install? 
I find it strange that so many people recommend fresh installs --- are you all just using a standard installation and thats it?
I probably have installed and configured hundreds of additional packages and a lot of additional software that was not available through packages. 
Re-doing this after a fresh install is simply unacceptable. Not to mention configuration data, and other data that is somewhere outside of my /home partition.

There simply should be no benefit of a fresh install over an update IMO. If there is, there is something broken or buggy about the update process.

---

### Post by abhilash82 on 2007-10-18
Will Gutsy upgrade using the update manager work seamlessly with all the additional settings and packages I had installed with Feisty?

---

### Post by farish on 2007-10-18
> **paxmark1 said:**
> I got rid of automatix a couple months back.  I religiously use aptitude for updates.

I did the sed script to go from feisty to gutsy in /etc/apt.source.list   and then
sudo aptitude upgrade and then sudo aptitude dist-upgrade

It worked like a charm.  I had been nervous because I had gotten rid of all but mplayer (xine, totem, etc.) and also scanner stuff I did not use.  

It was my easiest update ever.  peace, mark

----------------------------------------------------------------------

Sorry if I've missed it, but what sed script did you use?  Do you have a link?

Thanks!
Farish

---

### Post by jetpeach on 2007-10-18
shouldn't this thread be unstickied and a new one made for gutsy? is the method mentioned in the first post still the "official" upgrade method? it seems stupid that it's out of date, talking about how to upgrade to feisty. a much more comprehensive first post, addressing how to upgrade the various ubuntu flavors and any hiccups with each would be much more fitting...

EDIT: i believe these pages are the best general upgrade guide, since it has official methods for the various ways you may wish to upgrade (using the CD to upgrade etc)
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")
for kubuntu, although it doesn't address how to do it with the CD (only how to upgrade over the network)
[http://kubuntu.org/announcements/7.10-release.php#upgrade]("http://kubuntu.org/announcements/7.10-release.php#upgrade")

---

### Post by Rob500 on 2007-10-18
I'm upgrading now, the instructions are on the (Kubuntu) website, very clear to follow.

---

### Post by boyturtle on 2007-10-18
By doing the upgrade, will I lose all my files, docs, email, history etc or will they all be retained like they would be in a windows upgrade?

---

### Post by Dritz on 2007-10-18
Just a quick question. Is it a good idea to use the alternate CD to upgrade when you have network access. I'm asking a little late as that's what I'm doing right now. Basically I followed the alternate CD upgrade instructions and when the GUI launcehed I was asked if I wanted to use the network to install additional upgrades (or something along those lines). Since I did that am I actually using the CD at all or am I simply doing a normal upgrade?

---

### Post by rbmorse on 2007-10-18
Boyturtle: If you use update manager all your user data will be retained.  Still, making a good backup before you update is NEVER a bad idea.

---

### Post by sjatkins on 2007-10-18
The official upgrade method sucks.  It takes hours and hours.  I have a gutsy alternate CD and tried to install from that only (official method #5).  For some unknown reason it still downloads from the internet event though I told it not to when asked.  How can I most efficiently and without hitting the net upgrade using this CD?  I don't need fancy GUI during the upgrade.  I do need a method to upgrade my 3 machines today without waiting hours for each one.   

Thanks for any solution.

---

### Post by sjatkins on 2007-10-18
> **Dritz said:**
> Just a quick question. Is it a good idea to use the alternate CD to upgrade when you have network access. I'm asking a little late as that's what I'm doing right now. Basically I followed the alternate CD upgrade instructions and when the GUI launcehed I was asked if I wanted to use the network to install additional upgrades (or something along those lines). Since I did that am I actually using the CD at all or am I simply doing a normal upgrade?

When asked I told it NOT to go to the net and it is anyway.  Something is messed up.

---

### Post by jetpeach on 2007-10-18
It may have still gone to the net for packages not on the alternate CD - e.g., if you run any KDE packages not on the GNOME ubuntu alternate CD, it can only get the new ones through the web. Or, if you run Kubuntu and any GNOME pacakges were needed... If it doesn't do this, there really isn't any way for it to complete the upgrade, unless it just removes all the packages that can't be found directly on the the CD and will have unmet dependencies...

However, if it's actually going to the web to get updates from packages that are actually on the alternate CD you are using, that's pretty messed up.

---

### Post by sjatkins on 2007-10-18
> **jetpeach said:**
> It may have still gone to the net for packages not on the alternate CD - e.g., if you run any KDE packages not on the GNOME ubuntu alternate CD, it can only get the new ones through the web. Or, if you run Kubuntu and any GNOME pacakges were needed... If it doesn't do this, there really isn't any way for it to complete the upgrade, unless it just removes all the packages that can't be found directly on the the CD and will have unmet dependencies...

However, if it's actually going to the web to get updates from packages that are actually on the alternate CD you are using, that's pretty messed up.

The entire idea of an install CD is that it is self-contained regarding dependencies, right?  It does notify me that it is not upgrading a lot of stuff not in the official set and will later give me a chance to remove them.  So I don't see why the heck it is going to the net.  It is doing so for the vast majority of the files.  I haven't heard my CD spin in a while now.  It claims it will take over 4 hours to get the rest.  YIKES!   In the first place where are the torrents?  In the second place, why can't I just load everything in one go that I need to my quite ample local disk and finish up from there.  To make it even worse it periodically asks some question during the install so I can't even walk away.  Like I say, this sucks.

---

### Post by sjatkins on 2007-10-18
[QUOTE=usererror;2546525]That was harsh dude!  If you don't like the community then leave!  This is all free stuff, so don't expect everyone to be here 24/7.  Ubuntu development isn't a full time paying job, it's a full time volunteer job, to the best of my knowledge.


That it is "free" is no reason to put out a krap upgrade or not have someone monitoring how it is going.   This is a community isn't it?  I would expect us at least to help each other without beating folks up that report problems on the grounds that the bits are free.

---

### Post by jetpeach on 2007-10-18
I wholeheartedly agree - believe me, I have found upgrading one of the least smooth of all the things when using Kubuntu (it's generally even worse for Kubuntu than Ubuntu, since they don't spend as much time on it...)
 
This was part of what I just wrote to someone else:
what we need is an alternate DVD that would contain nearly all the packages, including those only on one of the two K/Ubuntu distributions.

Searching through the torrent list
[http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)
I see two big DVDs, one for Ubuntu and one for Kubuntu. Last time when I upgraded to 7.04 I tried one of these, but it still didn't have all the packages needed and I had to wait for stuff off of the repositories. I think I even posted complaining, "what is on this 4GB dvd if not the packages for both KDE and GNOME programs?" I think the reply was, it could be used as a live CD or alternate and maybe had some other things. This time around I haven't yet downloaded the DVD so don't know if it would have everything needed this time, but if it doesn't then we should file a bug - they really need to have a DVD with virtually everythingon it...or at least a method to upgrade without waiting for the repositories.

---

### Post by kristianz on 2007-10-18
> **jetpeach said:**
> 
[http://www.ubuntu.com/getubuntu/upgrading]("http://www.ubuntu.com/getubuntu/upgrading")
How did you find that page? There is no link to it from the Get Ubuntu page, and searching for "upgrade" or "upgrading"only  gives the kind of irrelevant search results we used to get in the pre-google days, ie. nothing useful and certainly not the page you link to above.

---

### Post by sjatkins on 2007-10-18
WOW.  The alternate CD downloaded has corrupt .deb files on it.  Wonderful.  No wonder I had such pain with this.  No wonder it won't even install much less upgrade an existing installation.   Thanks a whole heck of a lot for the fish and the waste of time.

---

### Post by prrawls on 2007-10-18
Wow, from the tone of things it sounds like a lot of upgrade gone bad so far.  

I do have a question, with all I've been seeing is it worth to upgrade my server from EDGY to Gibson?  
If so what is the process?

Since I run my server on a VM it makes it easier to take a snapshot and at least give it a shot.

Thanks in advance.

---

### Post by DavidTangye on 2007-10-18
There are all preserved

---

### Post by rennen01 on 2007-10-19
> **paxmark1 said:**
> I got rid of automatix a couple months back.  I religiously use aptitude for updates.

I did the **_[COLOR="Red"]sed script[/COLOR]_** to go from feisty to gutsy in /etc/apt.source.list   and then
sudo aptitude upgrade and then sudo aptitude dist-upgrade

It worked like a charm.  I had been nervous because I had gotten rid of all but mplayer (xine, totem, etc.) and also scanner stuff I did not use.  

It was my easiest update ever.  peace, mark

What is this sed script you are talking about? Can we just manually change our sources.list file and aptitude upgrade and aptitude dist-upgrade?

Is this the method you are talking about?

sudo sed -e 's/\sfeisty/ gutsy/g' -i /etc/apt/sources.list
sudo apt-get update
sudo apt-get upgrade

---

### Post by jetpeach on 2007-10-19
> **prrawls said:**
> Wow, from the tone of things it sounds like a lot of upgrade gone bad so far.  

I do have a question, with all I've been seeing is it worth to upgrade my server from EDGY to Gibson?  
If so what is the process?

Since I run my server on a VM it makes it easier to take a snapshot and at least give it a shot.

Thanks in advance.
It really depends on your needs and if you want to spent the time. For myself, I can't stand have out of date software so always upgrade pretty much right away, sometimes even in release candidate.

My advice if you do decide to, definitely wait at least a day or two - it will take forever and just hammer the servers more if you do it now. You will need to first upgrade to Feisty, then follow the steps to Gutsy. I believe the "official" method in this thread should work for each stage (see first post). I hate the way it hasn't been updated, I wish they did here on these forums what Fatwallet.com's forums do (see my post recommending it here [http://ubuntuforums.org/showthread.php?t=320115](http://ubuntuforums.org/showthread.php?t=320115) ), where there is a user editable wiki directly after the first post. That way if the original poster isn't updated, the community can update info in the beginning of the thread to keep it up to date... who wants to read 30 pages just to *try* to figure out the pros/cons and methods of updating?!

---

### Post by luminair on 2007-10-19
Is there an official workaround to this bug that stops upgrading from even starting?  [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980)

---

### Post by happymonkey on 2007-10-19
> **luminair said:**
> Is there an official workaround to this bug that stops upgrading from even starting?  [https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/153980)

I don't know if there is a fix yet. I'm going to attempt to run ```
'update-manager -c'
``` tonight if I still can't get the upgrade process to work. When I attempted to use the upgrade process, it would start downloading and then halt on the 43rd prerequisite file.

---

### Post by mattme on 2007-10-19
> **PWill said:**
> Modifying your sources.list is unofficial, hacky, and can cause problems, as many users have experienced.

Whatever do you think the update manager does?!    It just substitutes the present release's repositories for the next's, disabling any others, and then calls apt-get with dist-upgrade.

---

### Post by mmxbass on 2007-10-19
> **mattme said:**
> Whatever do you think the update manager does?!    It just substitutes the present release's repositories for the next's, disabling any others, and then calls apt-get with dist-upgrade.Except somehow update manager seems to do it not as well as adept.

---

### Post by kevmaster on 2007-10-20
> **mattme said:**
> Whatever do you think the update manager does?!    It just substitutes the present release's repositories for the next's, disabling any others, and then calls apt-get with dist-upgrade.

Update-manager does use apt underneath the hood. But it does do more than just changing the sources.list and execute a dist-upgrade.

If you upgrade with update-manager you will see that it first downloads some files before commencing the actual upgrade procedure. These files are specific for your dist upgrade (whether it's from dapper->edgy, edgy->feisty, from feisty->gusty or whatever) and contain additional package information on your new release in relation to the old one. 

Still skeptic? Have a look at the python sources in /usr/share/update-manager/*.cfg
And you will find that they contain information on demoted packages, **removal blacklist**, and (maybe most important) **additional packages** that come with the new distribution. 

This is something apt is unable to detect, yet it provides fixes for common upgrade problems.

That's one of the reasons why [Ubuntu says]("http://www.ubuntu.com/getubuntu/upgrading"):

> Manual command-line upgrade (not recommended)

Please note - this method is less reliable. If you use this method, you MUST be prepared to fix problems manually, such as packages being unexpectedly removed, apt crashing unexpectedly, etc. Using Update Manager (see above) is likely to be much less problematic.

Don't get me wrong. I love apt. It's what has made (Debian &) Ubuntu what it is today. Great. It's just not the best way to upgrade your Ubuntu release nowadays. Open up. 

From [tips on upgrading ubuntu]("http://kevin.vanzonneveld.net/techblog/article/upgrade_any_version_of_ubuntu_desktop/")

---

### Post by mmxbass on 2007-10-20
> **kevmaster said:**
> Don't get me wrong. I love apt. It's what has made (Debian &) Ubuntu what it is today. Great. It's just not the best way to upgrade your Ubuntu release nowadays. Open up.Belittling other users won't get you anywhere. No amount of official documentation is going to change my mind when my personal experience has update-manager failing utterly every single time on every computer. What happens after the system becomes unusable? Adept to the rescue like always.

---

### Post by mlind on 2007-10-20
Would it be possible to make a sticky thread or a visible forum notification for Gutsy users that they should review any issues and/or tips provided in Gutsy release notes? This could save a lot of different people from unnecessary hassle.

[http://www.ubuntu.com/getubuntu/releasenotes/710](http://www.ubuntu.com/getubuntu/releasenotes/710)

---

### Post by Cauda_Draconis on 2007-10-21
How would one get the official upgrade method to work? Mine keeps failing to fetch the last of the files. 

Here's my /var/log/dist-ugrade/main.log:
```
2007-10-21 15:37:33,273 INFO release-upgrader version '0.81' started
2007-10-21 15:37:34,643 DEBUG lsb-release: 'feisty'
2007-10-21 15:37:34,644 DEBUG _pythonSymlinkCheck run
2007-10-21 15:37:38,825 DEBUG checkViewDepends()
2007-10-21 15:37:38,826 DEBUG getRequiredBackports()
2007-10-21 15:38:57,984 DEBUG cancelClicked
2007-10-21 15:38:58,020 ERROR IOError in cache.update(): 'Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/binary-i386/Packages.gz Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main/binary-i386/Packages.gz 404 Not Found
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main-all/binary-i386/Packages.gz 404 Not Found
'. Retrying (currentRetry: 0)
2007-10-21 15:38:58,204 ERROR IOError in cache.update(): 'Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/Release.gpg 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2 
'. Retrying (currentRetry: 1)
2007-10-21 15:38:58,383 ERROR IOError in cache.update(): 'Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/Release.gpg 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/dists/feisty/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/Release.gpg 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://ca.archive.ubuntu.com/ubuntu/dists/feisty-updates/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/Release.gpg 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/main/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/restricted/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/universe/i18n/Translation-en_US.bz2 
Failed to fetch http://security.ubuntu.com/ubuntu/dists/feisty-security/multiverse/i18n/Translation-en_US.bz2 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://givre.cabspace.com/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://ntfs-3g.sitesweetsite.info/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/Release.gpg 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main/i18n/Translation-en_US.bz2 
Failed to fetch http://flomertens.keo.in/ubuntu/dists/feisty/main-all/i18n/Translation-en_US.bz2 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/Release.gpg 
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/feisty-backports/main/debian-installer/i18n/Translation-en_US.bz2 
'. Retrying (currentRetry: 2)
2007-10-21 15:38:58,384 ERROR doUpdate() failed complettely
2007-10-21 15:39:00,958 DEBUG marking 'release-upgrader-apt' for install
2007-10-21 15:39:01,207 DEBUG marking 'release-upgrader-dpkg' for install
2007-10-21 15:39:01,526 DEBUG pre-requists item: '<pkgAcquire::ItemIterator object: Status: 1 Complete: 0 Local: 0 IsTrusted: 0 FileSize: 1924684 DestFile:'/tmp/tmpvCTftC/backports/partial/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' DescURI: 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ub' 
2007-10-21 15:39:01,526 ERROR pre-requists item 'http://us.archive.ubuntu.com/ubuntu/pool/main/r/release-upgrader-dpkg/release-upgrader-dpkg_1.14.5ubuntu11.2_i386.udeb' is NOT trusted
```

---

### Post by Arjunanda on 2007-10-22
I am getting similar results:

```

Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)


```

---

### Post by kevmaster on 2007-10-22
My guess would be that you need to clean up your sources.list. I see references the the Ubuntu CD and to repositories like:

flomertens.keo.in
ntfs-3g.sitesweetsite.info
givre.cabspace.com

I can imagine that they aren't trusted or don't have gutsy packages yet. To cleanup our sources list press **ALT**+**F2**, type *gksudo "gedit /etc/apt/sources.list"* and click **Run**.

Ubuntu only needs:
```
deb http://nl.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
deb http://nl.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse
```
(maybe replace NL with a mirror closeby)

The rest is 3rd party and might not work with Gutsy. For example, your ntfs-3g repository  enables NTFS write support (for windows disks), but that's already included in Gutsy, so no need to import those unsupported 3rd party feisty reps. More details on this at my blog article: [How to: Upgrade to Ubuntu Gutsy with Compiz-Fusion]("http://kevin.vanzonneveld.net/techblog/article/upgrade_to_ubuntu_gutsy_with_compizfusion/")

---

### Post by wburden on 2007-10-22
Is it possible to perform an upgrade to a previous Ubuntu version using a new downloaded 'iso' burned to CD? The reason I ask is that the download took only an hour +/_ on my hi-speed cable connection but the  recommended up-grade method seems to take forever and sometimes breaks before all the required files finish downloading.

---

### Post by houstonbofh on 2007-10-22
> **Arjunanda said:**
> I am getting similar results:

```

Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)


```
And you are wondering why a repo for Breezy Badger, a no longer supported distribution, is having issues with Gutsy?  I have some 3rd party repos in my sources, but I am not surprised when they break.  WineHQ didn't get Gutsy until 2 days before release.  Medibuntu had it, but you had to look for it until 2 days before release. If you want to add unsupported stuff, be ready to support it.

---

### Post by houstonbofh on 2007-10-22
> **wburden said:**
> Is it possible to perform an upgrade to a previous Ubuntu version using a new downloaded 'iso' burned to CD? The reason I ask is that the download took only an hour +/_ on my hi-speed cable connection but the  recommended up-grade method seems to take forever and sometimes breaks before all the required files finish downloading.

Yes.  It actually will pop up with that option when you insert the CD.  If that is disabled, browse the CD to cdupgrade.

---

### Post by jimdhall2 on 2007-10-22
When I try to use the above upgrade method it fails and I get the following msg on the console terminal:

extracting '/tmp/tmp8oCCAx/gutsy.tar.gz'
authenticate '/tmp/tmp8oCCAx/gutsy.tar.gz' against '/tmp/tmp8oCCAx/gutsy.tar.gz.gpg' 
could not send the dbus Inhibit signal: org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

Any idea what's going on????

Thanks in advance

---

### Post by houstonbofh on 2007-10-22
It is trying to verify the file, and is failing to do so.  You should start a new thread about this, and perhaps bug it in launchpad.  It is more than a 2 post fix.

---

### Post by jimdhall2 on 2007-10-23
:)Thanks to Kevmaster's post on the previous page, I fixed my problem.  Here's his suggestion:


 Re: PLEASE use the official upgrade method! (if you decide to upgrade)
My guess would be that you need to clean up your sources.list. I see references the the Ubuntu CD and to repositories like:

flomertens.keo.in
ntfs-3g.sitesweetsite.info
givre.cabspace.com

I can imagine that they aren't trusted or don't have gutsy packages yet. To cleanup our sources list press ALT+F2, type gksudo "gedit /etc/apt/sources.list" and click Run.

Ubuntu only needs:
Code:

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-security main restricted universe multiverse

(maybe replace NL with a mirror closeby)

The rest is 3rd party and might not work with Gutsy. For example, your ntfs-3g repository enables NTFS write support (for windows disks), but that's already included in Gutsy, so no need to import those unsupported 3rd party feisty reps. More details on this at my blog article: How to: Upgrade to Ubuntu Gutsy with Compiz-Fusion


I cleaned up my source list per his suggestion.  Tried upgrade again and it worked like a charm.  I'm now running 7.10 gutsy gibbon!!!

Thanks for the help kevmaster!!!


__________________

---

### Post by Arjunanda on 2007-10-23
> **Arjunanda said:**
> I am getting similar results:

```

Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)
Failed to fetch http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-fi.bz2 Yhteyttä antesis.freecontrib.org ei voitu muodostaa: 80 (213.251.190.135) - connect (111 Connection refused)


```
Disabled the /antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/non-free/i18n/Translation-fi.bz2 repository solved the problem. And then the upgrade went through perfectly with no errors :)

---

### Post by Highway on 2007-10-24
Is it only possible to do a upgrade using the CD if it's the alternate Cd.
I spent hours downloading the non-alternate cd, and seems you cannot use this to do an upgrade, only a full install.  There is no cdupgrade program on this cd either.  

Do i need to now go and download the alternate cd.

Highway

---

### Post by shafin on 2007-10-24
> **Highway said:**
> Is it only possible to do a upgrade using the CD if it's the alternate Cd.
I spent hours downloading the non-alternate cd, and seems you cannot use this to do an upgrade, only a full install.  There is no cdupgrade program on this cd either.  

Do i need to now go and download the alternate cd.

Highway
Sadly,That is the way to go.You do need the alternate CD for CD upgrade.

---

### Post by mistermax on 2007-10-27
I have tried using the update manager ( it prompts me there is a distribution upgrade from the upgrade notification icon).

However, this doesn't work - it complains about the lack os space in /boot stating it needs at least 31.5M?

---

### Post by mlippert on 2007-10-28
I just had the same problem, not enough space on /boot, when I tried to update (Edgy to Fiesty) via the button in the "Update Manager".

Now I originally installed using the alternate CD, so that I could dual boot w/ Windows and leave the Windows boot manager primary.

My hard drive is partitioned:
/dev/sda1 fat32 (primary boot partition w/ Windows boot manager)
/dev/sda2 ext2 mount point /boot, is 62.75MB with 35.02MB unused, this contains the GRUB boot loader
/dev/sda4 ext3 mount point / 19.94GB with 17.33 GB unused, this is where I installed Ubuntu Edgy
/dev/sda3 extended partion 53.72GB
contains:
 /dev/sda5 Windows NTFS partition 50GB
 /dev/sda6 linux-swap 3.72 GB

This was my 1st foray into Linux, although I have used Unix in the distant past.

I'm playing with Ubuntu because I don't ever want Windows Vista on ANY of my computers so I need to get comfortable with an alternative.

I've been slowly finding software that I like and doing some small configurations to my Ubuntu setup.

Now that Gutsy Gibbon is out I'd like to upgrade to it. I saw that the recommended method was to upgrade to Feisty Fawn and then upgrade to Gutsy Gibbon. However that 1st step failed.

I think I'm going to have to do a re-install, but I'd like to get my system back to where it is today preferably with the least effort, but mostly I'd like to not lose something I'd configured.

One thing I saw while googling, was to move /home to its own partition. I can do that.

However, then what? I don't think preserving /home will preserve the set of software packages that I've installed.

If I've been relatively good about using synaptic [color="red"]Is there somewhere that I can find (and save perhaps as a text file) the list of software I've installed?[/color] I think I also installed some stuff using automatix, and there might have been 1 or 2 things I installed from the command line using apt get (or maybe aptitude it depended on the instructions I found online).

Next question, while doing a re-install from CD I'd like to preserve my current partition structure. Can I do this?

Thanks to anyone who can answer these questions.
Mike

---

### Post by mlind on 2007-10-28
> **mistermax said:**
> I have tried using the update manager ( it prompts me there is a distribution upgrade from the upgrade notification icon).

However, this doesn't work - it complains about the lack os space in /boot stating it needs at least 31.5M?

remove previous kernels you have installed to free space in /boot.
if your /boot contains orphaned .bak files, you should remove those as well.

---

### Post by mightyteegar on 2007-11-04
> Is there somewhere that I can find (and save perhaps as a text file) the list of software I've installed?

In a terminal:

```
dpkg --get-selections | grep -v deinstall | sed -e 's/[    ]install//g' | sed -e 's/    //g'
```

---

### Post by wuhaa on 2007-11-05
Hi,

When upgrading my kubunut, the process just dies.  I tried running it manually and got this error..

Any Ideas on how it could be fixed?!:confused:

Thanks,

WuHaa: /etc/init.d # do-release-upgrade
Checking for a new ubuntu release
Done Upgrade tool signature
Done Upgrade tool
Done downloading
extracting '/tmp/tmp-CyK9G/gutsy.tar.gz'
authenticate '/tmp/tmp-CyK9G/gutsy.tar.gz' against '/tmp/tmp-CyK9G/gutsy.tar.gz.gpg'

Reading cache

Checking package manager
Reading package lists: Done
Reading state information: Done
Reading state information: Done
Reading state information: Done


A fatal error occured
Please report this as a bug and include the files /var/log/dist-upgrade/main.log and /var/log/dist-upgrade/apt.log in your report. The upgrade aborts now.
Your original sources.list was saved in /etc/apt/sources.list.distUpgrade.
Traceback (most recent call last):

  File "/tmp/tmp-CyK9G/gutsy", line 59, in <module>
    app.run()

  File "/tmp/tmp-CyK9G/DistUpgradeControler.py", line 1346, in run
    self.fullUpgrade()

  File "/tmp/tmp-CyK9G/DistUpgradeControler.py", line 1251, in fullUpgrade
    if not self.getRequiredBackports():

  File "/tmp/tmp-CyK9G/DistUpgradeControler.py", line 1140, in getRequiredBackports
    outfile = open(os.path.join(apt_pkg.Config.FindDir("Dir::Etc::sourceparts"), sourceslistd), "w")

IOError: [Errno 2] No such file or directory: '/etc/apt/sources.list.d/prerequists-sources.list'

---

### Post by ragunalth on 2007-11-09
When trying to update from the DVD I get the following error. 

**Failed, please check the ISO image!!**

I can view the ISO image from my other machine, but this machine will not budge.

---

### Post by la3875 on 2007-11-15
Upgraded using update manager. Had to remove wine from the repos but otherwise complete success! Great job all! Keep up the great work.

---

### Post by ArtechnikA on 2007-12-28
Clicked 'Upgrade' in update manager.
got a bunch of files.
quits every time (3 so far) with:
" Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found "

which would be only mildly troublesome if it didn't then try to blame my network connection.

it's fine...

Searched this thread and the Updates & Upgrades forum for hits on NTFS-3g but got nothing.
Am I the only person running NTFS-3g trying to upgrade to 7,04?  is the NTFS-3g repository off the air?

What's my next step here?

I did all the regular updates (161 of them) and restarted before trying to upgrade.

Thanks.

-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-

Update: found the place where "3rd party" components were listed - ntfs-3g was there.  Since the object of the game was to update to the latest stuff, which did not involve being able to write to that drive, i deselected it and retried the upgrade.  Worked.  Then upgraded to 7,10 where AFAIK I am now.  Still need to see if I can print stuff or if the ntfs-3g functionality has been propagated for me to the new version, but the original problem of Upgrade cratering because it could not find the ntfs-3g repository is behind me.  The other problems I've fixed before...

---

### Post by fst_odl on 2008-01-18
Currently I'm not able to acces the file [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/dist-upgrader-all/current/gutsy.tar.gz.gpg) - it seems unreadable....I tried it via Firefox and wget. Anyone having the same problems? Suggestions?

---

### Post by marcocec on 2008-01-27
I did upgrade and after restart I have no sound, How can I enable it??

---

### Post by THEMEDIA on 2008-03-06
I'm trying to upgrade from 6.06 to 6.10 (to 7.04 to 7.10)

I have typed into the termial:
gksu "update-manager -c"

Then I am prompted for, and type, the root password. 

Then I get the error:
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)

The Update Manager opens, but there is no option to update to version 6.10.

I have searched this issue extensively, but the only solution I found was to install "python-vte."
When I try that I get:
python-vte is already the newest version. 

Any help would be very much appreciated.

---

### Post by jetpeach on 2008-03-06
themedia, i hate to tell you to wait, but when hardy haron comes out i _believe_ they will have a method that goes straight from 6.06 to 8.04. this is in one month, and would save you a ton of downloading (since currently you've have to go 6.06->6.10->7.04->7.10 then next month to 8.04

somebody else might be able to verify that 6.06 will be able to go to 8.04, but i'm pretty sure this will be the case

as for your problem (if you want to upgrade now still), your 6.06 version is fully up to date correct? are your repositories set up correctly? if a repository was disabled that contained a  newer python-vte then it would think it was uptodate but it is not. other than these checks, i can only suggest using an unofficial upgrade method, which involves changing the repos manually, then "sudo apt-get dist-upgrade " .  the big drawback of this is it sometimes messes up with dependencies, i've had to spend a while in the past using unofficial methods to get the packages back installed correctly... (the reason for the difficulty with upgrading unofficially, is it doesn't know what packages can be removed or have to be removed before their new replacements come in. this is because  a new package isn't compatible with an old, and the old must be removed first...)

---

### Post by THEMEDIA on 2008-03-06
Jetpeach, 

Thank you so much for the quick and thorough reply!

How can I check to see if any of the repositories are disabled?

---

