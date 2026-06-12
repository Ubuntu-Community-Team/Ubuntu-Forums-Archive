---
title: "Nvidia, DMRAID, and kernel modules."
date: 2007-04-04
forum: Installation &amp; Upgrades
---

### Post by nox216 on 2007-04-04
I use Linux quite extensively at work and occasionally I try it out at home.

Last night, I installed the 7.04 beta of Feisty and did all of the appopriate upgrades and configuration to make it dual-boot with Windows XP on my primary 80gig hard drive. Worked wonderfully, as did the drivers for the graphics card. I was quite impressed.

The problems came when I tried to mount my RAID-5 array under an nForce chipset. Yes, I know it's fake (software) RAID pretending to be hardware. 

I had hoped dmraid would be the solution, so I installed it.. and my system promptly stopped booting, locking up at "Setting up dmraid devices..." After a bit of research, I found dmraid only supports RAID-0 and RAID-1 by default.

After some more research, supposedly it CAN support RAID-5, with a kernel module raid45 loaded. I'm not entirely sure, but it looks like the raid45 module was phased out with kernel 2.6.18 in favor of module raid456. The dmraid package, on Feisty (kernel 2.6.20), is still looking for module raid45.

Is there an effective solution to this beyond waiting for changes to be made to dmraid and/or the kernel?

I appreciate that most offered suggestions will be something along the lines of "use mdraid," but my RAID being incompatible with Windows is a dealbreaker. If you can live without Windows, power to you, but that's not an option for me.

Thank you.

---

### Post by rmjb on 2007-04-06
nox216, thanks for your info and subsequent bug report. I'm working on a patch but need you to test it before I commit it. I've also posted this info in the bug report.

Are you using the i386 or x86_64 architecture?

- rmjb

---

### Post by monoufo on 2007-04-06
Do you seriously have a dm-raid4-5.ko patch?

I need the draid45 target in my kernel but can't find a patch for the 2.6.20 kernel that Feisty is using.  

I's love to test it.  I'm using 2.6.20-14 with amd64

---

### Post by rmjb on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/102973](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/102973) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				I didn't add back the raid45 module to the kernel, I patched dmraid to use raid456 instead.

I can only build for i386 unfortunately. I ask a MOTU if they can build a version of dmraid for 64bit.

- rmjb

---

### Post by nox216 on 2007-04-07
I can confirm the dmraid patch lets dmraid see the RAID5 properly (i.e. dmraid -r lists the devices, now, instead of hanging), but it's still not mountable, as I suspect there needs to be a kernel module loaded for that that we don't have.

I know we've gone over some of this in the bug report, just wanted to reiterate for the forums.

---

### Post by monoufo on 2007-04-08
The 64bit version of the patch does not change anything.  the only difference is a slight change in an error message from raid45 to raid456.  The long hang and inability for dmraid to activate anything remain.

why won't anyone volunteer to patch feisty's kernel with dm-raid-4-5.ko?

---

### Post by rmjb on 2007-04-09
Feisty's kernel is frozen solid for the release and nothing new is going to be added. FakeRAID5 access will have to wait till feisty +1.

- rmjb

---

### Post by monoufo on 2007-04-09
Well yea, obviously.  that doesn't mean someone can't take the fesity kernels source code, patch it, and redsitribute it through the web. Or even just make the patch file compatilble with the source of fesity, and make us apply it ourselves.  If compiling a custom kernel is what it takes to get fesity working, then I'll do it.  otherwise, It's goodbye ubuntu and hello Fedora Core.  Why come back to Ubuntu for feisty +1?

anyone who has a fake raid5 array is certainly capable of compiling a kernel.

---

### Post by nox216 on 2007-04-09
Thank you much for your help, Richard. 

I know it's not yet a solid solution on any distro, and I still have some hope that a package solution can be found for Feisty that will work, but I suppose even if it takes till October, so be it. I'm glad we at least made a little progress regarding the dmraid package on i386.

I appreciate the effort.

---

### Post by bagadonitz on 2007-04-22
Any update on this?   I'm willing to be a guinea pig but I honestly don't know enough about symbolic links.  I don't know where to put this link such that dmraid will find it and look to the raid456 pacakge.  I tried but I know the links are probably all wrong.  If someone could show me the links commands and where to create them I'll give it a whirl.

What  have so far:

```

jeff@enghlol:/usr/bin$ sudo dmraid -s
Password:
*** Set
name   : nvidia_eabddcbc
size   : 2500569600
stride : 128
type   : raid5_ls
status : ok
subsets: 0
devs   : 5
spares : 0

```

```

jeff@enghlol:/usr/bin$ sudo dmraid -r
/dev/sda: nvidia, "nvidia_eabddcbc", raid5_ls, ok, 625142446 sectors, data@ 0
/dev/sdb: nvidia, "nvidia_eabddcbc", raid5_ls, ok, 625142446 sectors, data@ 0
/dev/sdc: nvidia, "nvidia_eabddcbc", raid5_ls, ok, 625142446 sectors, data@ 0
/dev/sdd: nvidia, "nvidia_eabddcbc", raid5_ls, ok, 625142446 sectors, data@ 0
/dev/sde: nvidia, "nvidia_eabddcbc", raid5_ls, ok, 625142446 sectors, data@ 0

```

However it doesn't show up (/dev/sdf1 is another seperate partition on the single primary drive (where the xp for the dual boot lives)):

```

jeff@enghlol:~$ sudo fdisk -l | grep NTFS
/dev/sdb1               1      155653  1250282691    7  HPFS/NTFS
Disk /dev/sdc doesn't contain a valid partition table
Disk /dev/sdd doesn't contain a valid partition table
Disk /dev/sde doesn't contain a valid partition table
/dev/sdf1   *           1        5100    40960048+   7  HPFS/NTFS

```

Lastly, the error:

```

jeff@enghlol:/usr/bin$ sudo dmraid -a y
ERROR: device-mapper target type "raid45" not in kernel

```

Again, 100% total newb in this domain so please don't yell at me!

Oh, System Specs

ASUS M2N32-SLI Deluxe
The RAID 5 Array is from a previous windows installation.  It is NTFS.
The system is dual booted currently with XP Pro 64 bit.
I'm Running a i386 build of Fiesty Fawn from a few days before release, fully updated to my knowledge.

---

### Post by monoufo on 2007-04-24
raid 5 requires additional support. I'm sorry to say that if you don't even know about making symbolic links, you can not handle getting raid5 to work.  It requires patching kernel sources, then compiling your own kernel. You will have to wait until Gutsy, unless you want to undertake such a task.


[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97655](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/97655)

---

### Post by bagadonitz on 2007-04-25
I won't undertake such a task any time soon but I will in the next little bit.  How do you learn anything if you don't blow it up first.

I know how to create symbolic links but what I don't know is how to get rid of them.  I believe I created one backwards at first and ended up seeing an error message about some kind of circularity.

At any rate, it's been a while since I looked at this as I set up the environment for my Java development and been busy doing work.  When time permits, I'll prod with this some more.  It isn't a hurry as the 60gigs of flac I had on that raid array got trashed somewhere along the way so my motivation to get it working is low.  I dont know how it got trashed but the last time I booted windows it took two hours while it ran through chkdsk and rebuilt everything fine except, of course, the one thing I didn't have backed up.  It may still be onthere somewhere and be recoverable but that's for another day.

---

### Post by nox216 on 2007-05-02
Small update: I've been doing some checking around, and discovered dmraid rc14 ([http://rpmfind.net/linux/RPM/fedora/devel/i386/dmraid-1.0.0.rc14-2.fc7.i386.html](http://rpmfind.net/linux/RPM/fedora/devel/i386/dmraid-1.0.0.rc14-2.fc7.i386.html)), which looks like the next release candidate of dmraid for Fedora Core 7.

Seeing as the author of dmraid is associated with Red Hat, and the release date for FC 7 is later this month ([http://fedoraproject.org/wiki/Releases/7/Schedule)](http://fedoraproject.org/wiki/Releases/7/Schedule)), I'd say we've got decents odds on there being kernel support set up in FC7 as well as the next release of dmraid working properly with said support.

Hopefully Ubuntu can copy some of this by Gutsy?

---

### Post by erman on 2008-01-02
I just have same raid5 configuration than nox, but I use a 64 bit 7.10 UBuntu.
It seems to present still the same issue, no raid support.

Can I hope for a dmraid update shortly?
Thanks

---

### Post by rmjb on 2008-01-02
Due to dmraid's constant struggle to work in ubuntu I've given up on it and I'm just using LVM now, which works great.

To get raid functionality you can use md. You wont be able to put /boot on any raided volumes, but everything else can be raided.

- rmjb

---

### Post by monoufo on 2008-01-02
Yea, but your method isn't adequate for everyone.  most people who want dmraid support are doing it for compatibility with windows.  using LVM/md/linux software raid is only good if you use only linux, and don't have any data on the array already.  The last one is extra crucial.  What if you are willing to give up windows, but already have 2TB of data on the array? You'd have to back that up somewhere.  If someone had that much backup space, they probably wouldn't be using raid5 in the first place. Yea, of course Raid5 isn't exactly a substitute for proper backup.  But if you backup the most important stuff, it's enough protection for everything else.  That doesn't mean you'd be willing to lose it all on purpose just to get Ubuntu installed.

I don't use raid5 yet, as i never ended up with the hardware.  So I can't really help or anything right now.  I was trying it out a while ago for someone else.

To everyone here who still can't do it, your best bet would be to try Fedora.  I think Fedora can do that, you'd have to go check. 

> **rmjb said:**
> Due to dmraid's constant struggle to work in ubuntu I've given up on it and I'm just using LVM now, which works great.

To get raid functionality you can use md. You wont be able to put /boot on any raided volumes, but everything else can be raided.

- rmjb

---

### Post by erman on 2008-01-03
ok monoufo, but..
since nvidia is quite a common platform for pcs..
i agree, not everyone uses raid 5 for their data.
since not everyone can start with a clean hard disk and a new linux distro but he still uses windows and he WOULD migrate tu Linux
Someone could think to use gradually ubuntu to manage his lot of documents, that he CAN'T, at the moment,  use only with linux...
WHY ubuntu developers can't consider to fix this issue?
You must always say 'yes, ubuntu is nice, but not everithing works with it...' It's a bit frustrating, isn't it?
erman

---

### Post by monoufo on 2008-01-03
yes it is.  maybe someone will work on it for Hardy.  I would install Hardy, apply the current patches, recompile my kernel, and see if I could get it all to work.  Then maybe they'd accept the changes into the kernel.  However, I don't have a raid5 array.  I do have a raid0 array, but that is a much simpler problem.  I also don't even have that computer hooked up since the combination of my and my sisters laptops meets all my current needs.

Raid5 support isn't a huge issue though. I might easily solve the whole thing by getting a real raid card, or by only running windows in a virtual machine, or some other solution.  maybe not run windows at all.  I do acknowledge that some people are stuck with dmraid, their best bet is to try another distro.  I would help if I could.

the biggest problem with linux is the lack of MS Office.  I want Office 2007 working perfectly.  Even with Crossover, you can't get office 2003 running perfectly.  Some people claim OpenOffice.Org is just as good.  I laugh at them.  They aren't even close.  OOO isn't even good enough to view and print microsoft documents.  They come out looking different.  Google Documents is a better replacement for Office than OOO is.  I can't vouch for everyone, but I absolutely need to use MS formats.  

Next down the list is hardware support.  It isn't quite as important as the MS Office problem because you can usually just not buy incombatible hardware.  I have a IBM thinkpad because I knew it would work with linux.  

Next up is games of course.  This is the primary concern of a bunch of people.  I'm putting it lower because many games can be made to run with wine and cedega.  Also, the majority of people don't care about the latest windows games.  Also, you don't need these games on all your computers for people with more than one.

my biggest problem with linux right now is I can't get certain java websites to work. most people don't need those websites.  I have pretty much bypassed the need for the unstable portions though, so it isn't actually that big a deal right now. I hope that hardy has better java support though. I have been finding workarounds for all my problems, but I can't help but need to use a windows computer every now and then. This is a problem for people who don't have regular access to more than one computer.

---

### Post by kevpatts on 2008-01-11
Hey guys,

I'm new to this chat but I'm just doing some resaerch as I'll be putting together a RAID 5 Windows XP machine next week and was looking to INSTALL Ubuntu on it as a dual boot.

I think it's a shame the Ubuntu dev guys don't consider this a priority. It seems like something that would be very easy to fix (apart from GParted crashing (which didn't happen in older Ubuntu disrtos)) going by the RAID 0 instructions here: [http://ubuntuforums.org/showthread.php?t=630644](http://ubuntuforums.org/showthread.php?t=630644).

Another thing I tried to do a while ago on another machine was to use my NTFS windows RAID 0 array as the "hard disk image" (for lack of a better term) of a VMWare or VirtualBox machine. I tried and tried and never got it working.

If these two relatively simple things could be taken care of, the only hurdle would then be games. Even that may be overcome soon by the news that VMWare are experimenting with OpenGL and DirectX support for 3D graphics in their virtual machines.

If anyone can help me with any of these tasks I'd be grateful. I'm gonna try recompiling the kernel and patching dmraid DURING installation as per the link I supplied and may hopefully get Ubuntu installed directly onto a RAID5 array, but I will need some help!

Kevpatts

Kevpatts

---

### Post by Phkillah on 2008-05-13
```
modprobe dm-raid4-5
```

8.04.1 will not have this "bug". The module was renamed.

:popcorn:

---

### Post by mattwynne on 2008-06-12
Hi folks,

I too have this problem. I'm running the AMD 64 build of 8.04 which I downloaded a couple of days ago.

I have a FakeRaid array (RAID5) full of data that I was using in windows.

I've tried doing the following at the command line:

matt@server:~$ sudo modprobe -v dm-raid4-5
[sudo] password for matt: 
insmod /lib/modules/2.6.24-18-generic/ubuntu/md/dm-raid4-5.ko 
matt@server:~$ sudo dmraid -ay
ERROR: device-mapper target type "raid45" not in kernel
matt@server:~$ 

So what am I doing wrong? Have I missed something obvious?

Thanks in advance, I'm really new to linux but very impressed so far - I hope I can get this working.

cheers,
Matt

---

### Post by mattwynne on 2008-06-12
OK I've figured this out. It's a problemette in the current version of the kernel, which will be fixed in the next version. Read more here:
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/220493)

---

### Post by monoufo on 2008-06-12
maybe intrepid will finally have real fake raid5 support.  If they get it stable in the kernel and stuff, they should have able to add support into the install program and stuff. only a couple years behind Fedora.

---

