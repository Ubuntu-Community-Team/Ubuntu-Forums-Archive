---
title: "Ubuntu on Asus p5q3 p45 motherboard"
date: 2008-09-09
forum: Installation &amp; Upgrades
---

### Post by berman56 on 2008-09-09
Wondering if anyone has been able to get any version of Ubuntu working on an Asus p5Q3 motherboard.  I've tried 8.04 and 8.10 alpha 5 and both freeze immediately after I choose "install ubuntu."  I am able to get opensuse 11 to install fine.  I really prefer ubuntu and hope the p5q3 will be supported upon the final release of intrepid.  Thanks for any help!

---

### Post by toxicfeet on 2008-09-10
Yea, I have been working on this as well.

I'm running:

QuadCore 9550 @ 2.83
P5Q3 Deluxe WIFI-AP @ n (P45 chipset)
2 GB of Corsair 1600 DDR3 @ DDR1333 (I can't put all 4GB in otherwise it hangs)
Nvidia 9800GX2

This motherboard sucks, plain and simple. 

I have tried the following bios (they all like to randomly hang at post)

0704
1303
1306

I have tried Enhanced IDE, Raid, and AHCI all to no avail. I had somehow had 8.04 running w/ a ATI 1900x w/ all 4GB of ram. So when I put the 9800GX I had to take out 2GB to get it even post.

8.04 crashes to busybox when it tries to load the livecd gnome environment to try to install
8.10 does the same
8.10 w/ updated LiveCD via uck-gui crashes to busybox
OpenSUSE LiveCD will run but when I try to install to the hard drive something break w/ GRUB (LILO failed as well)

The USB controller goes nuts on every distro. Its weird seeing as my mouse is hooked up via USB

Windows XP will install without any hiccups which does me no good as I don't want to go back.

0 errors in Memtest

Looking back at my browser history

[http://ge.ubuntuforums.com/showthread.php?t=890604](http://ge.ubuntuforums.com/showthread.php?t=890604)
[http://ubuntuforums.org/showthread.php?t=889556&highlight=p45](http://ubuntuforums.org/showthread.php?t=889556&highlight=p45)

I will come back and update all my references as I've spent the last 4 days working on this.

---

### Post by berman56 on 2008-09-10
Thanks, it is good to know I'm not alone.  Sounds like you've gone a lot further than I.  I too messed with IDE vs AHCI to no avail.  Opensuse 11 installation has been stable (I didn't try the liveCD and I installed from the complete DVD).  I am really hoping this gets resolved in one of the intrepid early releases.  Thanks for sharing more details on what you've tried/found.

---

### Post by toxicfeet on 2008-09-10
How did you get OpenSuse to install? I downloaded Suse 11 and it failed leaving me with a locked up screen and my Caplock and Scroll-lock lights on my keyboard flashing.

I have tried the following O/S since my last post:

OpenSuse 11 DVD
OpenSuse 11 Network Installer CD
Xubuntu Alternate CD

All of them failed miserably.

Which bios are you running, what type and how much ram? CPU? Graphics Card?

I would also be interested in what bios options you have enabled/disabled - I'm at my wits end w/ this and I do not want to install XP since I have used it since April.

---

### Post by Shazaam on 2008-09-10
Have you tried adding one or both of the following options to the kernel line while booting?
noalpci
acpi=off

---

### Post by ChinoxR on 2008-09-10
I think Ubuntu does not support chipser P45.
I have a MSI P45 platinum, and halt the live cd when installing on busybox.
I´m new on linux, in fact I´m a noob linux, no idea what happen, have tried change the IDE and SATA hard disk, and useless.

---

### Post by Sef on 2008-09-10
Yes, there is a problem with the P45 chipset, but here's how one OP got [Ubuntu installed on it]("http://ubuntuforums.org/showthread.php?t=890604"). (See post #10)

Copy of Post #10:

>  [newguy1950]("http://ubuntuforums.org/member.php?u=195513")

                                 **Re: Don't buy P45 chipset (especially Asus P5Q)**             
                                                                I seem to have solved the problem on my system, at least it has been running without issues for at least half-a-day so far and is letting me write this posting, which is a new record. A full 1 TB RAID-5 reconstruction also went through without hiccups.

Here's what you need.

1. Kernel 2.6.26-5-generic from Intrepid
2. Correct BIOS Settings.

Set your BIOS to use AHCI, disable unneeded extras. I use ACPI 2.0 as well.

Installing the kernel is another matter. Compiling a backport is not recommended, as it is quite complicated - the binary packages for Intrepid should work fine. In short (I won't give a long explanation, as I do not recommend the faint of heart or new users to try this), easiest way to get it working is to update, dist-upgrade; then add Intrepid repositories, install the packages linux-image-2.6.26-5-generic, gcc (this will update to gcc 3.4) and nvidia-glx-177.

(Gcc 3.4 is needed, because the kernel was compiled with it and will usually reject modules not compiled with the same version.)

Once all the packages are installed, remove the Intrepid repositories and update again. You now have a new kernel, new libc with a bit of fluff, and new gcc installed. If you use ATI, you don't need nvidia modules, if you bought an ATI card you're f.ucked in so many ways that you should stick to 2D anyways.

Do not boot with irqpoll. It messes up things again on my system and is not needed.


---

### Post by berman56 on 2008-09-11
> **toxicfeet said:**
> How did you get OpenSuse to install? I downloaded Suse 11 and it failed leaving me with a locked up screen and my Caplock and Scroll-lock lights on my keyboard flashing.

I have tried the following O/S since my last post:

OpenSuse 11 DVD
OpenSuse 11 Network Installer CD
Xubuntu Alternate CD

All of them failed miserably.

Which bios are you running, what type and how much ram? CPU? Graphics Card?

I would also be interested in what bios options you have enabled/disabled - I'm at my wits end w/ this and I do not want to install XP since I have used it since April.
I used the opensuse 11 64-bit DVD to install.  Here is my system:

Bios V1306
E8500
2x1GB Muskin DDR3 1066
ATI 3650 256mb
WD Raptor 150gb sata (vista)
Seagate 7200.11 750gb (opensuse)

Sorry to hear you're having trouble with opensuse.  It seemed to just work for me.  I did install with SATA setting as IDE legacy mode, but I doubt it matters.  I try and remember if I did anything else unusual.  Man what a headache.

---

### Post by berman56 on 2008-09-11
> **Shazaam said:**
> Have you tried adding one or both of the following options to the kernel line while booting?
noalpci
acpi=off
Yes tried that, didn't make a difference.  Still freezes during installation right at the beginning.  Thanks for the thought.

---

### Post by toxicfeet on 2008-09-11
The P5Q3 is extremely picky w/ memory, I retested my memory and got 50k plus errors on each 1GB stick of memory exactly at 20% of the 2nd test. I am gonna retest w/ a new stick I have coming in. Long story short it is both hardware and software issues now plaguing me.

I tested each 1GB individually using both auto and manual timings on both channels.

Never again will I buy a top of the line motherboard, or one from asus. Also those instructions are nice, but there are no instructions on how to update the live cd, to make it work. That method failed as well, maybe uck-gui isn't the correct way to do it since I'm still getting v86d errors - I hear its a kernel issue (source google)

---

### Post by glittalogik on 2008-09-15
Ditto, I'm having the exact same problem. Specs:

Asus P5Q3 Deluxe mobo
2 x 2GB G.Skill PI DDR3 RAM
Gigabyte 512MB 9800GT gfx
Intel Quad Q6600

---

### Post by glittalogik on 2008-09-15
Right, I can't even remember where I found the suggestion 'cos I've been trawling everywhere for info on this, but I went into the BIOS settings and in Storage Configuration, set SATA Configuration to AHCI. The 8.04 and 8.04.1 LiveCDs both boot every time, no boot flags required.

I'm installing 8.04.1 now, will update once it's done...

[UPDATE]
No go, hangs on flashing cursor, doesn't even make it to GRUB. Tried switching SATA Configuration back to IDE with same result.

---

### Post by berman56 on 2008-09-18
Dear Ubuntu God,

Pleeeeaaaase, please, pretty please.  Throw a loyal Ubuntu fan a bone, who happens to have inherited a p45 chipset, and throw in a little support in Intrepid alpha 6.  I would be forever grateful.

---

### Post by glittalogik on 2008-09-18
I'd been holding off from trying other distros this month due to download caps, but then I discovered my ISP's unmetered mirror server. Will attempt a random selection and see how they fare until a new release of Intrepid appears. Any suggestions? I'm thinking OpenSUSE, PC-BSD and Gentoo for a start...

Just tried Alpha 6, no go. The graphics spacked out before dropping to Busybox unless I was in safe graphics mode, so it might have been issues with my 9800GT as well. Didn't try any boot flags, I want it to just work, dammit.

Gonna give Slackware a shot now...

---

### Post by berman56 on 2008-09-19
Tried alpha-6 desktop CD and alternate CD.  No luck.  Looks like we will have to stick with opensuse for now.  Still hopeful for the final release of intrepid...

---

### Post by Therion on 2008-09-19
> **berman56 said:**
> Wondering if anyone has been able to get any version of Ubuntu working on an Asus p5Q3 motherboard. 
I'm running [COLOR="Blue"]Ultimate Edtion v1.9[/COLOR] (which is Hardy Heron based) on my Asus PQ5-SE.  I just double checked to make SURE that it does indeed have the Intel P45 chipset, and yeah, it does.  

Only problem I ran into was getting the onboard LAN recognized.  Fell back on an old dLink PCI card I had lying around and everything else installed like a treat.  Just thought I'd mention it in case it helps anyone else out.  Other than the Atheros LAN chipset issue, my install of Ultimate Edition was flawless.  Runs like a champ!  

Link in my sig if you want to try it out.

---

### Post by berman56 on 2008-09-21
> **Therion said:**
> I'm running [COLOR="Blue"]Ultimate Edtion v1.9[/COLOR] (which is Hardy Heron based) on my Asus PQ5-SE.  I just double checked to make SURE that it does indeed have the Intel P45 chipset, and yeah, it does.  

Only problem I ran into was getting the onboard LAN recognized.  Fell back on an old dLink PCI card I had lying around and everything else installed like a treat.  Just thought I'd mention it in case it helps anyone else out.  Other than the Atheros LAN chipset issue, my install of Ultimate Edition was flawless.  Runs like a champ!  

Link in my sig if you want to try it out.
Thanks for information, very interesting.  It establishes that the p45 chipset is not necessarily the problem.  I did try the Ultimate Edition and it crashes during installation the same as all 8.04 or 8.10 distros.  Perhaps this is a Marvell specific issue.  There are a number of known troubles with Marvell controllers, for one example see:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/104929](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/104929)

Marvell does offer a Linux driver install package:

[http://www.marvell.com/drivers/driverDisplay.do?driverId=204](http://www.marvell.com/drivers/driverDisplay.do?driverId=204)

In the launchpad discussion, there is some suggestion that installed the Marvell driver might help.  Alas, I don't have the expertise to install this package without first getting Ubuntu installed.  I would greatly appreciate if anyone could provide some advice.  Thanks!

---

### Post by berman56 on 2008-09-22
For those interested, my searching has turned up a couple of people who appear to have successfully installed Ubuntu on the p5q3.  Unfortunately, each thread doesn't provide much detail regarding their version(s) and whether they had to jump any hoops to get to install without freezing.  Here are the links:

[http://ubuntuforums.org/showthread.php?p=5816900](http://ubuntuforums.org/showthread.php?p=5816900)

[https://answers.launchpad.net/ubuntu/+question/44232](https://answers.launchpad.net/ubuntu/+question/44232)

---

### Post by Redalert Commander on 2008-10-11
I've got it pretty much working :)

System:
Asus P5Q3 Deluxe Wifi-AP @n (with the Intel P45 chipset)
Intel Quadcore Q9550 2.83 Ghz
MSI N9800GT Zilent 1G (Nvidia GeForce 9800 GT 1024MB DDR3)
2 bars of 2 GB DDR3 RAM (OCZ3P1600EB4GK 4096MB kit)
OCZ 1000 Watt EliteXStream Power Supply OCZ1000EXS-EU
WESTERN DIGITAL 640GB 16MB SATA II (7200/300) WD6400AAKS
2 drives of 1TB: WESTERN DIGITAL 1000GB 32MB SATA II (7200/300) CAVIAR BLACK WD1001FALS

First I entered the BIOS and set the storage type to raid, then in the raid storage manager I created a raid block (raid 1, mirror) using the 2 1TB drives (connected on sata 2 and 3, the 640 GB drive uses slot 1).

I installed Ubuntu 8.04 (32-bit alternate install disk) on the 640 drive without problems, and without additional boot flags.
The 640 drive has been divided in 3 partitions: 1 for linux, 1 for the swap, and a third 120GB partition to install windows. I should have thought about it before... to install windows first and then linux.. but ok.. mistakes happen.

so after ubuntu got installed, I installed windows XP (had to fiddle with the raid drivers to get it installed), then tried fixing ubuntu again by reinstalling grub.. didn't really work out.

So then I just did a clean Ubuntu installation using the same parameters as before. I set up a software raid (md) in the Ubuntu installer for the 1TB disks, and gave it 1 ext3 partition.

after this second installation of Ubuntu, everything seemed to work, except for the WLAN (will look for the driver later, don't need it as I use the gigabit LAN) and my speakers, I use a 5.1 setup, and I only get stereo sound(tried to fix it, but haven't got it to work yet).
Apart from those 2 things, I didn't come across any problems with ubuntu (yet?) This post is made from my fresh installation :)
I installed the ext 2 driver for windows (fs-driver.org) and I now have a working raid 1 (read and write in both OS'es) with 2 1TB drives, and a dual boot with Ubuntu 8.04 and win xp.

Perhaps the key to make some of those stuck issues go away is the raid option in the BIOS, Linux doesn't care about the fakeraid set up or not, I think...
I was able to use every drive separately in the installer.

---

### Post by jimbaker4linux on 2008-10-12
I have my P5Q3 Deluxe running Ubuntu Studio 8.04.1
I have sata drives and dvd.
My bios is 1201
I did the following:
Set bios to defaults
Set sata to AHCI
Set ACPI 2.0 Support to enabled
Set ACPI APIC support to enabled
Added noapic to kernel boot line in grub. (HAVE to do this based on above!)
Everything works just fine.

Historical Note: At first I tried acpi=off with default bios and 
sata on ahci and everything worked, 
but I couldn't shutdown from the gui. 
However, the new stuff listed above works fine.

---

### Post by heluani on 2008-10-12
> I have my P5Q3 Deluxe running Ubuntu Studio 8.04.1
I have sata drives and dvd.
My bios is 1201
I did the following:
Set bios to defaults
Set sata to AHCI
Set ACPI 2.0 Support to enabled
Set ACPI APIC support to enabled
Added noapic to kernel boot line in grub. (HAVE to do this based on above!)
Everything works just fine.

Ditto, I just installed Hardy 8.04.1 on a P5Q3 Deluxe without problems at the first try. Don't need to add noapic as a kernel parameter and it booted out of first try.

BUT: 1) This is a fresh install because my new P5K3 Deluxe Asus which was 13 months old just died without warning, from one day to the next one. That mobo did show 50K+ erros on new and old RAM sticks as someone in this thread posted before. Looking at the Asus forums, it seems like a bad idea these days to get a top of the line mobo... Since I had never had a problem with them I decided to give'em a try with the P5Q3

2) I can't resume from Suspend, couldn't fix this with any real solution. Will post back if I can solve this issue.

R.

---

### Post by teogeo on 2008-10-12
> **jimbaker4linux said:**
> I have my P5Q3 Deluxe running Ubuntu Studio 8.04.1
I have sata drives and dvd.
My bios is 1201
I did the following:
Set bios to defaults
Set sata to AHCI
Set ACPI 2.0 Support to enabled
Set ACPI APIC support to enabled
Added noapic to kernel boot line in grub. (HAVE to do this based on above!)
Everything works just fine.

Historical Note: At first I tried acpi=off with default bios and 
sata on ahci and everything worked, 
but I couldn't shutdown from the gui. 
However, the new stuff listed above works fine.

Good job this really works on my setup:

ASUS P5Q3 Deluxe
CPU: Intel Q5500 Quad Core 2.83GB
2 SATA drives

I have only tried to run the Live CD yet thought... But previously i had problems even with that, so now I'm positive that the installation will also work! :-)

However, with the above changes in the BIOS, my vista couldn't boot (okk the truth is that I don't like vista, I'm a mac user, however I want to have a triple boot system that works smoothly).

So I had to restore again the default settings in BIOS, to make them boot again...

That means every time I want to use Ubuntu or Vista I will have to make the above changes? :/

---

### Post by berman56 on 2008-10-12
Looks like we are finally making some progress here.  I also managed to get things working.  Here is a detailed list of the steps I took:

[http://ubuntuforums.org/showthread.php?t=943848](http://ubuntuforums.org/showthread.php?t=943848)

Cheers.

---

### Post by berman56 on 2008-10-12
> **teogeo said:**
> Good job this really works on my setup:

ASUS P5Q3 Deluxe
CPU: Intel Q5500 Quad Core 2.83GB
2 SATA drives

I have only tried to run the Live CD yet thought... But previously i had problems even with that, so now I'm positive that the installation will also work! :-)

However, with the above changes in the BIOS, my vista couldn't boot (okk the truth is that I don't like vista, I'm a mac user, however I want to have a triple boot system that works smoothly).

So I had to restore again the default settings in BIOS, to make them boot again...

That means every time I want to use Ubuntu or Vista I will have to make the above changes? :/
There is a solution to getting Vista to work after you change SATA settings (from IDE->AHCI or reverse).  See this link:

[http://support.microsoft.com/kb/922976](http://support.microsoft.com/kb/922976)

Cheers.

---

### Post by glittalogik on 2008-10-14
Already had SATA set to AHCI from previous attempts and ACPI APIC support was already enabled. Set ACPI 2.0 Support to enabled and IT WORKED! 8.04.1 is up and running on my machine!!! :guitar:

No boot flags, no RAID setup, no nothing. It Just Works. :biggrin:

---

### Post by heluani on 2008-10-14
Did you have any problems on suspend/resume? I can't get it to resume after suspend. Dmesg doesn't spit any message that I can recognize as related.

On my thinkpad, I had similar problems and it got resolved my adding thinkpad_acpi to the list of modules to remove/reload before/after each suspend/resume cycle, do you know of anything similar for this board?

R.

---

### Post by glittalogik on 2008-10-14
No idea, sorry! I never use the suspend function so it's not so much of an issue for me. Hopefully someone else will have an idea...

---

### Post by teogeo on 2008-10-15
> **teogeo said:**
> Good job this really works on my setup:

ASUS P5Q3 Deluxe
CPU: Intel Q5500 Quad Core 2.83GB
2 SATA drives

I have only tried to run the Live CD yet thought... But previously i had problems even with that, so now I'm positive that the installation will also work! :-)


After many tries I have to say that I didn't make it... :-(

Firstly, I must mention that I'm trying with Ubuntu 8.04..1, 32bit and no 64bit because they told that it is more stable...

So, live CD boots normally (with apci=off it boots faster), then I load the installer, choose to install and the installation fails at the very end, when it tries to install grub! :S

I get the error "'install grub' on device hd0 failed, this is a fatal error". I tried many things like changing from Advanced the grub installation in other devices but with not better results...


I have a SATA II drive (500GB) and have partitioned it with the Vista install DVD in 4 partitions. The first for vista (installed), the second for Ubuntu (trying) and the third for Mac OS X (not yet tried). The forth only for data...
This disk is connected in the SATA1 port of the motherboard. The DVD drive is connected in the SATA3 port and I have the SATA2 port empty, waiting for a second disk (which will be for data only so I haven't connected it yet just to be sure).

The other thing I tried is to install Ubuntu without installing GRUB. The installation was successful but I couldn't boot from Ubuntu (obviously :p). I booted again with the live CD and tried to fix the problem from there. But I encountered a big problem: after getting in GRUB shell, I typed `find /boot/grub/stage1` and I got "Error 15: file not found"! :-(
I found [an other thread in this forum]("http://ubuntuforums.org/showthread.php?t=224351") that have some tips for this problem, but there were no use.....


What else should/could I do? :confused:

---

### Post by teogeo on 2008-10-15
I erased everything, formated the HD and tried to install Ubuntu first and leave vista for later.


Well... it worked! :p

---

### Post by Redalert Commander on 2008-10-31
Since the new ubuntu came out yesterday, I upgraded my system.
I upgraded using the new alternate install disk, things were going great.. until reboot, xorg.conf got messed up (leaving X with an error), but an update run afterwards and a reset of the Xorg.conf to default, did the trick, everything was running again. Set the driver for nvidia to the non-free 177, and needed to disable the cd repository, there seems to be an error with the alternate install there, not being recognized as the proper disc, naming I guess... Anyhow after that the driver installed properly.

I described my expirience with 8.04 Hardy Heron earlier in this thread.

Time to check on how the system was doing on my P5Q3 motherboard.
I'll throw in some more details later about suspend/hibernate.

Before the upgrade I had sound, although only stereo, it took me several tutorials on how to get my 5.1 surround working, yet didn't have any luck, on top of that, my C&C3 game in wine had no sound and was running awkwardly fast (at least the intro movies... gameplay was a bit more normal speed, yet still faster than it should be). At the time I managed to get sound in wine running nice with alsa and custom .asoundrc file in my home dir.

Now after the upgrade to 8.10, I went in to check, much to my to my rejoice the new ubuntu instantly recognized the surround, I just had to adjust preferences in volume control to show the controls for 'surround' and 'center', then unmute them and turn up the volume, had a test on rythmbox, and heard a nice sound on all speakers :)
I threw out any custom configurations I had left from 8.04 to get sound in wine and had a go on it, sound worked in my C&C3 game.. yet choppy and it slowed everything down, in winecfg things where just hanging when I pressed 'test sound', so I had to kill its process.
A change from alsa to OSS and 44100 to 48000 sample rate, both in winecfg got everything running nice, good sound, normal gameplay :)

So I see some true improvements when using the P5Q3, next to overall distribution improvements.
At the moment my advice to everyone using this motherboard would be: upgrade to 8.10 Intrepid Ibex ;)

I'll have a go on hibernate and suspend later on, as well as wireless, but I don't expect any trouble on WLAN as it worked perferctly before.

I'd very much like to hear from others how clean install or upgrade went with 8.10 using this motherboard, any problems? things that work better? Or stopped working at all?
Or if you guys have any suggestions on things I should check for the P5Q3 let me know :)

Edit: perhaps I should mention this, after upgrading from the cd, grub showed me the following options to boot.
- Ubuntu 2.6.27 kernel (normal and single user)
- Ubuntu 2.6.24-21 kernel (normal and single user)
- memtest
- windows XP pro
So the upgrade removed some the old kernels, wich is fine, freeing discspace etc.. (see 8.10 release notes for more info on that one)

However after the update I mentioned above, grub didn't show the 2.6.24-21 anymore, I saw the update installing the new kernel, wich at that time was already installed by the upgrade from cd... seems a bit buggy to me... ah well, it works, so I don't complain.

---

### Post by Redalert Commander on 2008-10-31
As I said in my previous post: some updates on my tests :)

- wireless connection: didn't work anymore, I had to recompile the driver, but afterwards it worked fine :)
instructions can be found here: [http://inatie.wordpress.com/2008/09/04/p5q3-deluxe/](http://inatie.wordpress.com/2008/09/04/p5q3-deluxe/)
I do need to add that you'll probably need to comment out a bit more than the page says, the article was written on a previous version, I use the driver from september 25th, 2008, version 1.4.0.0 (article published on the 4th).
I commented the following lines using gedit(standard text editor): line 133 till 141 and 145 till 153 (to see line numbers: edit - preferences - tab 'view' - check line numbers)

- suspend: seems to be working fine

- hibernate: the computer seemed to be doing this rather well at first sight, however, I couldn't type in my password or move the mouse, seems that my mouse and keyboard (on the same USB device, it's a wireless set) didn't get reinitialized. Re-pluggin the device did the trick, but I suspect other devices might be affected too, such as camera's, joysticks etc, I didn't test them though. Wired network, and sound however seems to work fine after hibernate.

Anyone else has had some experience on this? how is the new ubuntu working for this motherboard for you guys?

---

### Post by heluani on 2008-11-01
Well, I haven't tried 8.10 as 8.04 is supposed to be quite stable, I rather try to solve these issues before on 8.04. I feel I have no control whatsoever over this motherboard so I was wandering what was your situation with regard to:

Fan speed control: sensors-detect only finds coretemp as a sensor and I have no control over the fan speed. I have to use the ASUS Q-fan control to spin down the fans and that sucks

No wake after suspend: With all kinds of BIOS settings and both generic and server kernels I can't wake up after suspend. If I dissable the APIC support on BIOS its even worse cause the server kernel won't boot in high resolution graphics!

Speedstep, nothing relevant on /proc/acpi/

Any help, share thoughts would be appreciated.

---

### Post by Redalert Commander on 2008-11-01
Your suspend/hibernate issues might have been solved in the new version, as those procedures have been rewritten in the new 2.6.27 kernel Intrepid uses ( [http://kernelnewbies.org/Linux_2_6_27#head-6b295ec8ec9b422bd646b5f20db0070644085525](http://kernelnewbies.org/Linux_2_6_27#head-6b295ec8ec9b422bd646b5f20db0070644085525) ). Or you might end up with the same results as I did, see my previous post.

As for sensors, I did notice that I can't get a CPU temperature readings, but only 2 readings from my graphics card. no change here between 8.04 and 8.10. I must say I'm fairly new when it comes to fan speed control en temperatures on linux. I tried about every relevant entry in synaptic with regard to fan speeds and temperatures, but I got nothing except for 'GPUCoreTemp' and 'AmbientTemp', both on my NVidia graphics card.

---

### Post by heluani on 2008-11-01
Thanks for your answer redalert... I'll wait a little bit before upgrading, I managed to get hibernate working... As for temperature, I certainly can see my CPUtemp, coretemp is that module, but I can't see any sensors for fans.... I could with my P5K3 and I thought it was the same chipset, but I might be wrong.

R.

---

### Post by Redalert Commander on 2008-11-02
The P5K3 uses the P35 intel chipset, whereas the P5Q3 uses the P45.
Thanks for the reply :) Although I can't seem to get it working, gdesklets was installed as well, but the various applets there didn't find any sensors, I just saw a text "No sensors found, is lmsensors installed and working?" Only thing I found was lm-sensors, I think that's the right one, but it was already installed, and I think it was running... :p
As said I'm a total newbie when ik comes to fans and temperature readings in linux, I'm used to the windows speedfan application.

So no luck there.

---

### Post by heluani on 2008-11-02
Hi there, if you have lm-sensors installed, then try ```
sudo sensors-detect
``` on a terminal. This will give you a series of modules to add to your /etc/modules file. If you just want to check wether they work or not, for example, if by the end of that command you get that you should add "coretemp" to your /etc/modules, just run the command ```
sudo modprobe coretemp
``` and then run sensors or the applet if you want, the error message you're having should dissapear. 

As for the P35 vs P45, I was referring just to the sensor part of the chipset (to control fan speed for example) and I don't know if they're different.

R.

---

### Post by Redalert Commander on 2008-11-02
ah, thanks :) worked like a charm, the applet that previously detected nothing is now seeing 4 different temperatures, the one I use for the GPU readings is still only showing the 2 GPU readings, giving me a total of 6 different readings.
I didn't have to run any commands when I installed 7.10 on my laptop (or after upgrading to 8.04), they were just showing :)

---

### Post by rigol2000 on 2008-11-15
Hello. I hope this isn't thread hijacking, but it deals with the P5Q

My system is:

Asus P5Q Deluxe p45
Intel E8400 Core 2 Duo 3GHz
Asus EAH4850 HTDI 512MB Video Card
SATA 0 250GB boot
SATA 1 250GB
SATA 2 500GB

I am Dual Booting:

Windows XP Pro SP3
Ubuntu Studio 8.04.1 kernel 2.6.24-21-rt

I was able to install and dual boot on my new system.  I have been using it for a few days without any major issues until today.  I was in Ubuntu, using it as normal.  I made a change to the menu.lst by adding the "default 4" line.  I rebooted, but this time, while booting it stayed on the Ubuntu Studio splash screen.  It stayed there for a couple minutes until the following lines appeared repeatedly.  

[B]irq 10: nobody cared (try booting with the "irqpoll" option)
handlers:
[<f8894c70>] (usb_hcd_irq+0x0/0x60 [usbcore])
[<f8914ec0>] (ata_interrupt+0x0/0x1f0 [libata])
[<f88c3be0>] (ohci_irq_handler+0x0/0x8f0 [ohci1394])[/B]

menu.lst
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
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default		4

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		10

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

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
# kopt=root=UUID=c6fdb2eb-8746-4c04-9527-9ba50969c253 ro

## Setup crashdump menu entries
## e.g. crashdump=1
# crashdump=0

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,1)

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

## Xen hypervisor options to use with the default Xen boot option
# xenhopt=

## Xen Linux kernel options to use with the default Xen boot option
# xenkopt=console=tty0

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

## should update-grub add savedefault to the default options
## can be true or false
# savedefault=false

## ## End Default Options ##

title		Ubuntu 8.04.1, kernel 2.6.24-21-rt
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-21-rt root=UUID=c6fdb2eb-8746-4c04-9527-9ba50969c253 ro quiet splash noapic 
initrd		/boot/initrd.img-2.6.24-21-rt
quiet

title		Ubuntu 8.04.1, kernel 2.6.24-19-rt (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.24-19-rt root=UUID=c6fdb2eb-8746-4c04-9527-9ba50969c253 ro single
initrd		/boot/initrd.img-2.6.24-19-rt

title		Ubuntu 8.04.1, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sdb1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

I tried rebooting several times with the same result.  Then, it booted.  Being new to Linux, I don't know why.  Though it booted, I have a feeling it may happen again.

Thanks.

---

### Post by Frankenpunk on 2008-11-16
> **teogeo said:**
> Good job this really works on my setup:

ASUS P5Q3 Deluxe
CPU: Intel Q5500 Quad Core 2.83GB
2 SATA drives

I have only tried to run the Live CD yet thought... But previously i had problems even with that, so now I'm positive that the installation will also work! :-)

However, with the above changes in the BIOS, my vista couldn't boot (okk the truth is that I don't like vista, I'm a mac user, however I want to have a triple boot system that works smoothly).

So I had to restore again the default settings in BIOS, to make them boot again...

That means every time I want to use Ubuntu or Vista I will have to make the above changes? :/

If you want to use Vista without going into the BIOS everytime, you need to either install Vista (with SP1) in AHCI mode, or go to the microsoft website to see what registry changes you need to make in order to make your IDE mode Vista usable in AHCI mode.

---

### Post by Redalert Commander on 2008-11-25
@ rigol2000:
I'm guessing you got the wrong number, I think it should be 3, although I'm really not sure on that, considering the line saying "Other operating systems"
Another possibility is to move the lines for xp up, to just above "### BEGIN AUTOMAGIC KERNELS LIST" and then set the default back to 0

Perhaps someone can shed a more clear light on the exact number.

And.. yes, hijacking... :p at this point I don't think it has to do with the motherboard. But I thought I post a reply anyway, I hope you find it usefull.

---

### Post by SyL on 2008-12-02
Hi Guys,

I'm planning my new config for the year ahead. This box will only run Ubuntu.
Up to now, I was thinking to go for an ASUS P5Q3 Deluxe.
Then, i discover this topic. And now, .... hum i doubt. 

So could you please say me:
- how Intrepid is going with P45?
- despite all troubles you had/have, would you recommend me to go for this motherboard? or should P45 be avoided?

Cheers!

---

### Post by Redalert Commander on 2008-12-02
As said, it is going fine with me, Intrepid is doing better that hardy, which was running fairly well. Check my posts for a more detailed description on my expirience.

Both suspend and sleep are working to an acceptable degree for me (except I have to re-plug the mous/keyboard after sleep.
Since 8.10, sound is working on 5.1 surround system.
Wireless needs a driver, but that is relatively easy to install, and once done it works like it would on one that would have worked out of the box.
The fakeraid is no good for ubuntu though, I use it to set up a raid 1 on windows, but linux uses that array as a pure software raid, no issues though.

Installation was done with the 8.04 cd, but went on without any issue, I expect the same from 8.10.

the dual gigabit lan works as well, haven't really seen an issue with this board myself.

---

### Post by SyL on 2008-12-03
Ok, so there is no big issues.
Regarding the fakeraid, i won't use it. I would rather go for a pure Linux software based RAID.

Your box looks very nice BTW!!

---

### Post by Swerve1000 on 2008-12-24
Just read the entire thread, glad I found it.

I'm planning on buying the P5Q3 also, and am glad to see 8.10 has corrected a lot of the issues.

I intend though, to install 8.10 64bit edition, and was wondering if everyone has been using the 32bit edition?

I'm worried that using the 64bit edition of Ubuntu may bring some problems not found with the 32 bit version.

My planned build is:

Intel 9550 Quad core
ASUS P5Q3
4gb (2x2) OCZ 1600
Velociraptor 150gb HDD

I've only just made the switch from XP to Ubuntu full time and no way want to go back.

---

### Post by glittalogik on 2008-12-24
I'll be installing 64-bit onto my machine next week, will keep you posted

---

### Post by IeU on 2009-01-03
Also having issues, noted the tips from this thread, going to try out now . . .
[B]
Edit1,[/B]

HD AHCI Enabled
USB EHCI off


Botting 8.10 x64 off an USB Pen Drive. It boots but just after loading the linux image, i get a black screen.

Botting Sidux x64 off the CD, it also loads, after i choose to load Sidux, i do also get a black screen.

Going to try later, Ubuntu off the CD.


**CPU Type**->                                          QuadCore Intel Core 2 Quad Q6600, 2400 MHz (9 x 267)
**Motherboard Name **->                                 Asus P5Q  (3 PCI, 2 PCI-E x1, 1 PCI-E x16, 4 DDR2 DIMM, Audio, Gigabit LAN, IEEE-1394)
**Motherboard Chipset**->                               Intel Eaglelake P45
**System Memory**->                                     8192 MB  (DDR2-800 DDR2 SDRAM)
**Video Adapter**->                                     NVIDIA GeForce 8800 GT  (512 MB)
**Monitor**->                                           Hannstar HW191D  [19" LCD]  623GH32CY3758
**Monitor**->                                           Samsung SyncMaster 245B/245BW (Digital)  [24" LCD]  (HS4P705257)
**Audio Adapter**->                                     Creative SB X-Fi XtremeGamer Sound Card
**Disk Drive**->                                        Kingston DT HyperX USB Device  (7 GB, USB)
**Disk Drive**->                                        ST31500341AS ATA Device  (1500 GB, 7200 RPM, SATA-II)
**Disk Drive**->                                        ST3160023AS ATA Device  (160 GB, 7200 RPM, SATA)
**Disk Drive**->                                        USB Flash Disk USB Device  (964 MB, USB)
**Disk Drive**->                                        WDC WD1500AHFD-00RAR5 ATA Device  (150 GB, 10000 RPM, SATA)
**Optical Drive**->                                     _NEC DVD_RW ND-3520AW SCSI CdRom Device  (DVD+R9:4x, DVD-R9:4x, DVD+RW:16x/8x, DVD-RW:16x/6x, DVD-ROM:16x, CD:48x/24x/48x DVD+RW/DVD-RW)

[B]
Edit2,[/B]
Yes, botting of ubuntu cd. Not successful . . . :/
I get that screen with those options of booting as live cd, install, etc . . .
I press boot as livecd or install, get a next black screen with a blinking point . . .

Tried with noapic and acpi=off
Also failed . . .

---

### Post by Frankenpunk on 2009-01-10
64-bit Ubuntu 8.10; cpu: Q6600; mobo: p5q-e p45
Completely stable system. Running Compiz-fusion, conky, etc. Wi-fi, updates, all working swimmingly.
Running in AHCI mode (BIOS setting)
Dual booting with Vista (for the sole purpose of Adobe & iTunes).

I don't recommend the p45 chipset, if you haven't bought it already. But if you have one, you shouldn't have any problems with Ubuntu 8.10.

---

### Post by fajarhp on 2009-01-14
how can i know the detected hardwares? i 'm looking for a program such as "Device manager on Windows OS" that working on ubuntu?

any solution?

---

### Post by SyL on 2009-01-28
> **Swerve1000 said:**
> Just read the entire thread, glad I found it.

I'm planning on buying the P5Q3 also, and am glad to see 8.10 has corrected a lot of the issues.

I intend though, to install 8.10 64bit edition, and was wondering if everyone has been using the 32bit edition?

I'm worried that using the 64bit edition of Ubuntu may bring some problems not found with the 32 bit version.

My planned build is:

Intel 9550 Quad core
ASUS P5Q3
4gb (2x2) OCZ 1600
Velociraptor 150gb HDD

I've only just made the switch from XP to Ubuntu full time and no way want to go back.



Did you build it up?
Finally, due to "cost saving" i won't build up my new box this year...

---

### Post by SyL on 2009-01-28
> **fajarhp said:**
> how can i know the detected hardwares? i 'm looking for a program such as "Device manager on Windows OS" that working on ubuntu?

any solution?



Try *[I]Applications* / System Tools / *Ubuntu* Device Database[/I]

---

### Post by fajarhp on 2009-02-09
I had some problem with ubuntu that working on my p5q3.

1. how do i configure my modem (integrated with sony ericsson k530i) on ubuntu?if it need driver, where can i get it?

2. where can i get driver for my p5q3, so all of the devices can be detected?

3. i have 2 x 2gb of ram but ubuntu only detect approximately 3,02 gb? why ?is there any hope, so it powered maximum?

---

### Post by koma77 on 2009-02-10
As for question 3) you have to run the 64-bit version of Ubuntu (or any other OS actually) in order to use 4 GB or more memory.

---

### Post by fajarhp on 2009-02-12
I'm sorry for my dumb questions:(

---

### Post by Redalert Commander on 2009-05-28
I know this thread is kind of old... but anyhow.. some new information:
ever since intrepid, I got random freezes using this motherboard. Sometimes twice a day, sometimes not for a week. It's completely random, sometimes when watching a movie, or when using bittorrent, other times when just browsing the web, or even while not yet being logged in for a while and leaving it on the login screen.

I got tired of it and had no clue to the cause whatsoever, nothing in the logs, not anything...
I hoped a BIOS update would help, but alas, it only got worse, the system became very unstable, and it doesn't get past 3 hours uptime, mostly not even 15 minutes.
Even trying a clean install fails, the sccreen just got corrupted during the debian lenny install.
Tried both lenny and jaunty right now.

I'll try to get the old bios back in and hope for the best.
Next time, I'm buying another board, gigabyte seems to have some nice ones.

---

### Post by glittalogik on 2009-05-28
Redalert: I've had no such problems. Intrepid gave me some sound issues but Jaunty's been smooth as silk. I would say that either your board is faulty or the problem lies elsewhere.

Come to think of it, this sounds almost exactly like the problem I had with a mobo fault in '04 that killed my Windows install and drove me to Ubuntu in the first place. Have you memtested your RAM?

---

### Post by Redalert Commander on 2009-05-30
I suspect either the board, or a HDD, although knoppix had the same problem running from a live CD, so I'd say the board (although I was checking the properties of my old home dir on the drive to see what size it was, then again, it would freeze my ubuntu as well when idle).

Good point to check memory, I'm currently running memtest86 from the Jaunty beta install disc, no errors yet (pass 29%, currently on test #4), but I'll report back when it completes.

What worries me most is that thee freezes started from occurring occasionally a couple of times a week to about every 5 minutes after I installed that BIOS update. Because of that I suspect the board itself, especially because even the ubuntu and debian text installers freeze at some point. Mostly after installing the base system and exactly when installing language packs at 1%, the cd would stop spinning and it would stay at that point till I hit the reset button. I almost installed completely, but frooze at the end of the installation, right before completing the installation of the desktop packages.

Sound was running fine since Intrepid, in Hardy, there was only stereo sound, upgrading to Intrepid brought me surround, no issues there.

(Memtest currently at 41% Pass and Test#6, still no errors)

---

### Post by Redalert Commander on 2009-05-30
Ok, now I'm really concerned.
The memtest got stuck on 41% on test 6 at 36% or so (not sure anymore)
It didn't react to keyboard input such as C (config memtest), Esc (reboot from within memtest) or Ctrl + Alt + Del. what does that mean?
It didn't show any error's though.
My guess of faulty motherboard with faulty BIOS seems to remain?

Edit: 
Second run freezed at Pass 35%, Test 83%, Test 5.
I'm out to buy a new board -.-

---

### Post by dwayne.hale on 2009-06-04
Running Jaunty on a Asus P5Q SE2 mobo without problems, haven't really had any problem with the 64 bit linux distro's I've used on it.

Asus P5Q SE2 
Intel Q9400 
8Gb of G.Skill memory
Nvidia Geforce 9800GTX+
WD 500 Green Drive 
WD Raptor 37.5 Drive.

---

### Post by Redalert Commander on 2009-06-11
I replaced my P5Q3 with an MSI P45 Diamond (same chipset), installed Lenny, once it's up, the system seems rock solid, but there are occasions when booting fails, and I need to do a hard reset, after that it loads just fine, no freezes yet (running for about a week).
I guess it was just a faulty motherboard.

---

### Post by Anubis on 2009-07-16
P5Q SE2 replacing my excessively loud XFX680i nforce. I have not even reinstalled yet. Just swapped boards and I have no issues. Other than lm-sensors does not seem to detect fans. But this board has no fans on the chipsets, so it is absolutely quiet. I jsut effortlessly upgraded the BIOS to the latest version 4/09. There are a lot of this mobos @Microcenter. I can't understand why all the returns?

---

### Post by Ciarlingo on 2009-08-24
Hy to all, I read this thread with big interest.

My hardware list is:

motherboard Asus P5Q3 Deluxe
Intel Q9550 2,83 Ghz - Core 2 Quadcore – 12 Mb cache fsb 1333
8 Gb Ram DDR3 1333 Transcend
Nr. 01 Hard disk Western Digital 250 Gb Sata2 7.2 rpm 8Mb cache (where to install SO)
Nr. 02 Hard disk Western Digital Caviar RE3 1.000 Gb Sata2 7.2 rpm 32Mb cache Raid Edition (software raid mdadm for data storage)

Ubuntu server 9.04 64bit installation is all OK without problems. All seems to work, but after vmware server 2.0.1 installation (by needed patch) often system freeze, expecially transferring big files by samba. I only can to push reset button [IMG]http://ubuntuforums.org/images/icons/icon9.gif[/IMG].
Stopping vmware service, no more freeze problems.

I know that vmware server doesn't support Jaunty, so I tried to install Ubuntu Server 8.04 LTS 64bit in another partition. After few troubles I'm able to do it (thanks to BIOS ide to ahci modification).

It seems to be OK but.........after vmware server installation freeze problems return!! (Worse than in Jaunty)  [IMG]http://ubuntuforums.org/images/icons/icon8.gif[/IMG]. 

I hope that only solution isn't to wait vmware server upgrades.

Can someone help me?

Thanks

---

