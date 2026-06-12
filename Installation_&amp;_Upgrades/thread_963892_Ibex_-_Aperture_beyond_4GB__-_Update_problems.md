---
title: "Ibex - Aperture beyond 4GB ? - Update problems"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by mmeclimate on 2008-10-30
Hi,

I upgraded my Ubuntu 8.04 to 8.10, Intrepid Ibex, today.
The reboot process did not work and I got the following message:

0.004000 Aperture beyond 4GB. Ignoring.

I've read some threads that other people had the same problem. I rebooted it again and pressed 'ESC', then I selected the following kernel: 2.6.24-24-generic and then I was able to reboot properly and go to the log in window.

Why isn't kernel 2.6.27-7-generic not working?
Is there a fix for this?

Thanks!

Michael

---

### Post by chromatic.glissando on 2008-10-31
I had this same problem...

I hit the power button out of frustration (probably not a good idea) and it continued with the boot process though....

---

### Post by framebuffer on 2008-10-31
Hi!

I have 8.04 running perfectly on my AMD Machine. Today I tried to install 8.1 using the live cd but I am unable to execute any option wheter its trying or installing or checking CD. It give this 

0.004000 Aperture beyond 4GB. Ignoring.

And then nothing happens.

Pls help.:confused:

---

### Post by galv on 2008-10-31
> **framebuffer said:**
> Hi!

I have 8.04 running perfectly on my AMD Machine. Today I tried to install 8.1 using the live cd but I am unable to execute any option wheter its trying or installing or checking CD. It give this 

0.004000 Aperture beyond 4GB. Ignoring.

And then nothing happens.

Pls help.:confused:

The same thing here ...

---

### Post by sakis on 2008-10-31
I get the same message too :(

I upgraded from 8.04 and every time i choose to boot with the latest kernel i have the "Aperture beyond 4GB. Ignoring." message... but it continues o.k and the system works just fine!

Here is the bug reference i found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

---

### Post by surj08 on 2008-10-31
I get the same thing! i get the error but it hasnt stopped anything.

We all using the 86_64x version here?

---

### Post by framebuffer on 2008-10-31
> **surj08 said:**
> I get the same thing! i get the error but it hasnt stopped anything.

We all using the 86_64x version here?

Yes, 64 Bit Ubuntu 8.1 and 64 Bit Processor AMD x2

---

### Post by framebuffer on 2008-10-31
> **sakis said:**
> I get the same message too :(

I upgraded from 8.04 and every time i choose to boot with the latest kernel i have the "Aperture beyond 4GB. Ignoring." message... but it continues o.k and the system works just fine!

Here is the bug reference i found [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

Thanks for the link. Till the bug gets resolved, is there any other way of installing? Is the same problem coming in alternate CD too? Can somebody please confirm whether its with live cd only?

---

### Post by PumpAction on 2008-10-31
Also got this message, but the computer started like normal.
I also have a couple of other problems in intrepid, that i didn't have in hardy which i think might be related. 
1. I'm running intrepid 64-bit but only get 3.2 GB out of 4 GB memory
2. 3D performance in Quake Wars is very bad compared to hardy. (8800gt)

For now I'm going to take a look in the BIOS, because I had to do a reset before installing. Something was causing problems with grub when installing and it would not boot (error 17) until I've done a BIOS reset(could not figure out what was the problem so, 'fail safe' reset).

Edit: Sysinfo, 64-bit hardy installed from Alternate CD, PCIe 8800gt, 4GB memory and Phenom Quad. 780g chipset.

---

### Post by brenx on 2008-10-31
> **framebuffer said:**
> Hi!

I have 8.04 running perfectly on my AMD Machine. Today I tried to install 8.1 using the live cd but I am unable to execute any option wheter its trying or installing or checking CD. It give this 

0.004000 Aperture beyond 4GB. Ignoring.

And then nothing happens.

Pls help.:confused:

Same here.:confused:

---

### Post by surj08 on 2008-10-31
I havent tryed the 32bit on the same machine but at least mine bypasses the error. 

Its wierd you wouldnt expect a 64bit machine to give a crap about 4gb or more of ram.

For everyone who cant even get it to install take out some ram as a last resort. (just guessing that might fix)

OR i did use the cd and booted to live and installed from there <try that after updateing (cuz i think one of the upgrades was for the installer)

Also are the people having this error using intel, amd or both? 

Mines a AMd 4200 X2

---

### Post by JCM3000 on 2008-10-31
I got this with the alternate AMD64 install despite having only 2GB RAM.  The installation continued but wouldn't recognise my RAID HDDs properly for partitioning so I had to abort.

System: AMD Athlon 64 X2 4800+, 2GB RAM, GeForce 8800 GTS 512MB Gfx 

I've done an install from the Update Manager instead which plainly doesn't work properly. System>Administration>Software Sources just hangs, amongst other problems.

Oh well, back to Hardy I suppose.  Another disappointing upgrade day :(

---

### Post by Divide_Overflow on 2008-10-31
I see this message every time I boot into 2.6.27-7 but so far it doesn't seem to cause any problem. 

EDIT: AMD Athlon 64 X2 system with 2 gigs of RAM, clean install to 8.10 x64 from a LiveCD.

---

### Post by ljoslin on 2008-10-31
I noticed something weird today, this was my second upgrade, the first went perfect.  The second however when I was rebooting it appeared to lock just like what you guys are saying.  I went to hit ctrl-alt-f1 to see what the other terminals showed and noticed as I hit ctrl-alt it started booting again...I lifted my fingers and it stopped again...pressed again and it started again?!?!  I rebooted again just to test my theory, and the same thing happened?!  This has been several reboots with the same thing?!?!  Seems crazy but hey, give it a try!

-=Larry=-

and i mean MANY reboots, for some reason the update also changed permissions on /etc/sudoers   so that was fun to figure out! :)

---

### Post by chromatic.glissando on 2008-10-31
I'm running AMD 64...I rebooted a few times more and the boot process just stopped working altogether. Strange, considering I didn't change anything.

Shutdown process wouldn't work correctly either. It would freeze at a certain point (i think it was trying to disable networking or something...) and stay there until I held the power button. 

I've read in some places that it could be something to do with the BIOS....something called IOMMU...I'm unfamiliar with it though.

Here is the bug report...but it is listed as low importance...
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/271070)

I had to revert back to 8.04. Luckily, I backed up my important files!

---

### Post by sakis on 2008-10-31
> **framebuffer said:**
> Yes, 64 Bit Ubuntu 8.1 and 64 Bit Processor AMD x2

> **PumpAction said:**
> Edit: Sysinfo, 64-bit hardy installed from Alternate CD, PCIe 8800gt, 4GB memory and Phenom Quad. 780g chipset.

> **surj08 said:**
> Mines a AMd 4200 X2

> **JCM3000 said:**
> System: AMD Athlon 64 X2 4800+, 2GB RAM, GeForce 8800 GTS 512MB Gfx

> **Divide_Overflow said:**
> EDIT: AMD Athlon 64 X2 system with 2 gigs of RAM, clean install to 8.10 x64 from a LiveCD.

As i can see the message apears only on AMD cpu's with the x64 Ubuntu version, mine system is similar too:

AMD 3800+ X2, 2GB RAM, PCIe 9500GT, 8.10 x64

---

### Post by Aflack on 2008-10-31
Same here. Quad core 2.4GHz  AMD 64, 5GB RAM, 8300 and 9300 GeForce 256MB... I'm very mad... cannot find a solution.

---

### Post by jaypeesmith on 2008-10-31
Same here: laptop with AMD TL-60 dual-core w/ 4 GB ram.

---

### Post by elaar on 2008-11-01
I get the same 4GB aperture problem, AMD64 with 2GB ram, it does however boot.

I do however have the same problem as another poster, the boot process just hangs (for ever) unless I keep pressing a key (enter) on my keyboard.  I have to press the enter key about 20 times during the boot process otherwise it just hangs at particular processes (sata, ata, network initialising to name a few). I have no idea what could be wrong and why key pressing sorts it.

Also, when I close my laptop up, it won't come out of the sleep process no matter what I do.

It's a shame because I was very happy with 8.04

---

### Post by sonu 1807 on 2008-11-01
I get the same message.... but the boot proceeds. Earlier the boot used to hang and I had to hold down a key. But this is no longer required.I don't know ... may be it was automatically solved by any system update. I get the same message while booting to Fedora 9. Again the boot proceeds normally from there. I have 2 GB of RAM with AMD 64 and running 64-bit edition

---

### Post by Aflack on 2008-11-01
anyone know how to bypass?

---

### Post by marcos_vs77 on 2008-11-01
Funny. I've got exactly the same message, then right after the boot process stops and only continues when I press some key. I have to keep pressing keys on the keyboard until it goes on by itself. Any idea?

---

### Post by marcos_vs77 on 2008-11-01
> **marcos_vs77 said:**
> Funny. I've got exactly the same message, then right after the boot process stops and only continues when I press some key. I have to keep pressing keys on the keyboard until it goes on by itself. Any idea?

By the way, mine was a fresh install.

---

### Post by paulkchen on 2008-11-02
I got the same "0.004000 Aperture beyond 4GB. Ignoring." message on my screen and then the boot process stopped. I've got an ASUS M2A-VM (non-HDMI) board with 2GB RAM and an Athlon64 X2 3600. I upgraded my motherboard BIOS to a more recent version (from 0503 to 2001 if anyone is curious), and now I can boot into the  live desktop.

I hope this info helps someone else.

---

### Post by phpadik on 2008-11-02
I get the same problem.

0.004000 Aperture beyond 4GB. Ignoring.

It's on a 64-bit Live CD. My system is HP Pavillion TX1210AU.

Processor: AMD Turion 64 X2 mobile technology TL-58
RAM: 2GB (2x1GB)

Please help me. :D

---

### Post by johnboy1967 on 2008-11-02
Same problem myself.

Tried both updating from Hardy and also a clean install from live cd.

Machine stops booting with the IOMMU error.

AMD 64 chip and 4gb ram.

Looks like its either back to Hardy or a good reason to try a new distro.

---

### Post by jolly.lucifer on 2008-11-02
Ubuntu AMD64, Kubuntu AMD64 and 32bit all have the same problem in 8.10.

I got it working by hitting Enter (and removing "quiet" from the boot options).

Now am stumped with a network error.

---

### Post by Vince4Amy on 2008-11-02
I have had other 64 bit distros do this too, I've just ignored it.

---

### Post by framebuffer on 2008-11-02
> **paulkchen said:**
> I got the same "0.004000 Aperture beyond 4GB. Ignoring." message on my screen and then the boot process stopped. I've got an ASUS M2A-VM (non-HDMI) board with 2GB RAM and an Athlon64 X2 3600. I upgraded my motherboard BIOS to a more recent version (from 0503 to 2001 if anyone is curious), and now I can boot into the  live desktop.

I hope this info helps someone else.

Hi, I am having the same motherboard but With HDMI. I tried to upgrade the bios today but the updater told me that no new bios file is available on the server.

Can you please send me the link from where you downloaded the bios?

thanks.

---

### Post by Ozzi on 2008-11-02
Same problem here: Aperture beyond 4 gb with 2 gb of ram on a 64 bit system... and it won't boot on it's own.

Hope they fix it soon.

---

### Post by LilyAyanami on 2008-11-02
Did the upgrade to 8.10 and got the message on boot.  The message would be flashed onto the screen before moving on in the boot process.  Took a few reboots to see the whole message.

MB: ASUS M3A32-MVP Deluxe
CPU: AMD Phenom 9850 Quad-Core
Memory: 4GB

---

### Post by gforster on 2008-11-02
I am glad to see I am not the only one!

I am having the exact same problems. If I keep pressing the enter key, it finally boots (sometimes). 

I filed a bug for it - [#288464]("https://bugs.launchpad.net/ubuntu/+bug/288464")

Please add something there - it seems they look there to fix things more than on the forums. This is somehting that should be fixed immediately. Not all of us can easily ignore it.

---

### Post by Darth Buh on 2008-11-02
I have the same issue too- the Ubuntu loading screen hangs for about a minute, then loads.  I see the error flash prior to X loading up.

I did have an issue with GRUB before missing an initialization line, I ran update-grub and the system loads with the latest kernel now.

I play Warcraft, and am noticing some performance difference.

For some odd reason, my microphone and sound recording is nuked now...

Specs: 2GB RAM, Raid-0 2X WD Raptor HDD, Athlon FX55 processor.

DB

---

### Post by TonyMontana on 2008-11-03
Same problem.  After inserting the install CD I see a splash screen for about a minute or so, then I get this error message.  I haven't found a way around it.  Ubuntu 8.10 is completely unusable for me.

'cat /proc/cpuinfo' returns 'AMD Athlon(tm) 64 X2 Dual Core Processor 5200+'... 2 GB ram.

---

### Post by Vince4Amy on 2008-11-03
It doesn't freeze my computer, it just displays for a second before usplash starts and Ubuntu loads.

---

### Post by paulkchen on 2008-11-03
> **framebuffer said:**
> Hi, I am having the same motherboard but With HDMI. I tried to upgrade the bios today but the updater told me that no new bios file is available on the server.

Can you please send me the link from where you downloaded the bios?

thanks.

I booted into XP and used the ASUS update program which fetched and flashed the BIOS for me. I'd suggest going to [http://support.asus.com/](http://support.asus.com/) and going to the download section for the M2A-VM HDMI.

---

### Post by em4r1z on 2008-11-03
AMD64 Mobile Sempron 3500+, Nvidia GeForce Go 6100, Nvidia chipset
Ubuntu 8.10 64-bit

While I see that message before the system starts loading it doesn't stop the boot nor have I noticed a problem. Still, I'm intrigued about it.

---

### Post by nutz on 2008-11-03
Same issue here and I get it both on the live cd and the alternate. The computer will not boot and will not move past that message screen we are talking about here. I even left it there for about an hour to see if it would eventually move past but no luck...

Sure would like to check out the new version so I hope they find a work around for this. Been looking forward to Ibex for a while now so this has me pretty bummed out that I can't even install it.

---

### Post by dsmex on 2008-11-04
I did a fresh install of kubuntu 8.10 on a 2xAMD64 HP pavilion dv6610. I get the aperture message, but it doesn't cause any problem as far as I have seen.

The hold-a-key-to-boot issue is a known issue and it is very easy to fix. You just need to add a parameter in the grub menu file.

Instructions here:
[http://www.ensode.net/roller/dheffel...buntu_intrepid](http://www.ensode.net/roller/dheffel...buntu_intrepid)

Bug report here:
[https://bugs.launchpad.net/ubuntu/+s...sh/+bug/272247](https://bugs.launchpad.net/ubuntu/+s...sh/+bug/272247)

My laptop cannot resume from suspend on 8.10. It could on kubuntu 7.10. I have no idea if this problem is related.

---

### Post by causeitsme on 2008-11-04
AMD64 / 1.5 G RAM

Get the message every boot. Doesn't seem to affect anything though.

---

### Post by ghostofcain on 2008-11-04
I have the same problem,

running on AMD 4450e x 2
           4GB RAM
           ATI on board graphics

and although the message appears before splash screen, it boots fine but takes about 5-10 minutes to shut down

---

### Post by mmeclimate on 2008-11-05
> **nutz said:**
>  The computer will not boot and will not move past that message screen we are talking about here. I even left it there for about an hour to see if it would eventually move past but no luck... Sure would like to check out the new version so I hope they find a work around for this.

I guess the only solution so far is to reboot the computer, press ESC and use the other kernel (not the newest one). I also hope they find a solution for this problem soon!
Cheers!

---

### Post by lotharjade on 2008-11-05
:confused: I got this problem too.  When booting up it says something about the 4 mg aperture, but also something about IOMMU.  Not sure what that is about.  Today was the first time I found someone else with the same problem.  I have a previous thread seeking info on this issue, but no one has responded.  I will link here.

[http://ubuntuforums.org/showthread.php?t=965267]("http://ubuntuforums.org/showthread.php?t=965267")

---

### Post by Aflack on 2008-11-05
i cant even boot into ubuntu at all. i did one time, but then once i installed updatse and drivers back to the error

---

### Post by Aflack on 2008-11-05
i really wish there was a fix.. anyone find one yet?

---

### Post by sakis on 2008-11-06
Today i had a kernel update and everything is o.k now :)

---

### Post by Aflack on 2008-11-06
> **sakis said:**
> Today i had a kernel update and everything is o.k now :)

Well i guess ill try reinstalling...

---

### Post by olpec on 2008-11-07
Ok guys!!! I had the same problem with upgrade of ubuntu 8.04 to 8.10 and with a new installation of 8.10.I've an AMD64 pc too...I think it's a ubuntu 8.10 on AMD64 problem!!!I TOTALLY SOLVED THE PROBLEM upgrading the BIO.It's incredible!!!!..But it's true!!!!Now...If you solve "aperture beyond 4gb.ignoring" upgrading your BIO (like me) please reply to this thread.I hope to help you....Sorry for my bad english!!!:):)

---

### Post by mark2741 on 2008-11-07
Do you mean upgrade the BIOS?

I've been meaning to do that, but I'm scared : (

My AMD64x2 system is all custom-built with the exception of the motherboard, which is actually a holdover from an HP. It's a GigaByte motherboard, but it's BIOS is custom for HP. Whenever I power up the computer, since I'm no longer using the old HP case/case fans with it, the BIOS stops the boot process and says that the fans are not working. I have to hit F2 to continue the boot process. Been doing that for a couple of years now without problem, but it's annoying.

---

### Post by Retrograde77 on 2008-11-07
Have got that message too, pops up when booting for a second then boots up as if nothing happened.  Far as I can see my system is running fine.  Is very odd though, only running 3gb atm.

---

### Post by jaypeesmith on 2008-11-07
Upgrading the BIOS is not always the answer.  I have the latest and greatest BIOS for my HP DV9720us (bios version F.30) and I am still having this issue.  However, I will concede that this BIOS version was released in May 2008 so, maybe there is some as-yet unreleased BIOS feature that would fix this problem for me.

---

### Post by mark2741 on 2008-11-07
Yeah same here. I'm only running 2GB of RAM, so where it's getting the 4GB "Aperture" I have no idea. What exactly does the "4GB Aperture" mean anyway?

---

### Post by lotharjade on 2008-11-07
Yeah, my BIOS is the latest too.  I have a Biostar 8200 and the BIOS is the only option they have.

I have this problem, but am I the only one here who has an aperture problem with their monitor?  You all seem to have problems with booting up (mine has a bit of a hitch from 8.4 - 8.10), but my biggest problem is my video space won't match the monitor area.

I have all the updates, so no new kernl is fixing my issue.  Do you suggest reinstalling one of the kernel packages?

---

### Post by thorner on 2008-11-09
Just wanted to add my experiences.

I upgraded over network (recommended method) and the process hung during "installing" with "6 min remaining". I waited many hours, and computer was still siting at "6 min remaining".

I finally did a hard reboot and I am now where everyone else in this thread seams to be. 

If I select my previous kernel from GRUB, I get to an "Ubuntu is running in low graphics mode" screen, however i have no mouse or key board control (both USB). 

Currently downloading upgrade CD, hope that will fix things...

---

### Post by framebuffer on 2008-11-10
Hi!

Can anyone confirm whether its an issue with both 32bit and 64 bit versions of Ubuntu 8.1?

Thanks.

---

### Post by lotharjade on 2008-11-10
My problem is with a 64 bit version of Ubuntu 8.10, but it should be noted that my issue is mostly with video output.  Here is the bug I am having **[Launchpad bug#292320]("https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-177/+bug/292320")**.

Although it should be noted, I do have glitches, flickers and quirks with startup, shutdown, and when video is doing stuff, as compared to 8.04, but that is not causing any major problems right now.

I have posted the problem to launchpad, and to ubuntu forums, and have yet to hear a single comment except for this thread.  It is rather depressing really.  :icon_frown:  I wish we at least heard someone was working on this.

---

### Post by cikson on 2008-11-11
I have installed Linux kernel version 2.6.27 and still have "Ibex 64 bit - Aperture beyond 4GB" problem. :confused:

---

### Post by lotharjade on 2008-11-16
My Motherboard company just released a new BIOS.  I just installed.  It did not fix the problem.  Anyone hear if anyone is fixing this?

---

### Post by blitzer on 2008-11-16
Same problem here as everyone else.  My machine won't shut down it hangs untill I hit the power button ? 


> **framebuffer said:**
> Yes, 64 Bit Ubuntu 8.1 and 64 Bit Processor AMD x2

---

### Post by life4himsq on 2008-11-17
I am getting the Aperture beyond 4GB error on an ECS GF6100-M754 using onboard 6100se Nforce 430 video and 2x512MB ram. I dual boot ibex 8.10 64bit and hardy 8.04 32bit. The error only shows on the 64bit ibex. It looks like every one having the error also has Nvidia GPU. The only issues running either 8.10 or 8.04 is glxgears will only go 300 to 500 max FPS.

---

### Post by thepanch on 2008-11-21
Hi 
Is there any one trying to fix this bug, or is there a way around it. I am just not using my laptop for the time being, but if there is a way to get past it, it would be great to know. 
thanks for any tips.
pancho

---

### Post by z00 on 2008-11-22
I have a similar problem. This is my first time with Ubuntu and I've been trying a fresh install (formatting + 2 partitions.)

No matter how I configure the bios I get the '4Gb' message and the installation jumps to the busybox, where I'm totally stuck. **I can't install at all!**

AMD 3000+ 1 GB RAM 6600GT.

My XP install is virus ridden and so at present I have no usable desktop OS (posting this on my macbook). I can't update my bios as I have no floppy drive (old q-flash version).

Sigh. Any help would be appreciated.

---

### Post by mmeclimate on 2008-11-24
Hi,

The only way around it (that I know of) is to reboot your computer and press ESC. Select a different kernal for your Ubuntu and that should work. 

(Take a look at the first posting on this thread for more info)

Good luck,

Michael

---

### Post by thepanch on 2008-11-24
i press escape, and these options appear:

Ubuntu 8.10, kernel 2.6.27-8-generic
Ubuntu 8.10, kernel 2.6.27-8-generic(recovery mode)
Ubuntu 8.10, kernel 2.6.24-21-generic
Ubuntu 8.10, kernel 2.6.24-21-generic(recovery mode)
Ubuntu 8.10, kernel 2.6.22-14-generic
Ubuntu 8.10, kernel 2.6.22-14-generic(recovery mode)
Ubuntu 8.10, memtest86+



i have tried all the kernels, but i have no 2.6.24-24 or 2.6.27-7, 
any tips? i am new to linux and ubuntu, so dont know much 
thanks
thepanch

---

### Post by mmeclimate on 2008-11-26
> **thepanch said:**
> i press escape, and these options appear:

Ubuntu 8.10, kernel 2.6.27-8-generic
Ubuntu 8.10, kernel 2.6.27-8-generic(recovery mode)
Ubuntu 8.10, kernel 2.6.24-21-generic
Ubuntu 8.10, kernel 2.6.24-21-generic(recovery mode)
Ubuntu 8.10, kernel 2.6.22-14-generic
Ubuntu 8.10, kernel 2.6.22-14-generic(recovery mode)
Ubuntu 8.10, memtest86+



i have tried all the kernels, but i have no 2.6.24-24 or 2.6.27-7, 
any tips? i am new to linux and ubuntu, so dont know much 
thanks
thepanch


Hi,

The one which worked for me was the Kernel 2.6.24-21-generic. Did you try that one? What happened when you tried?

Michael

---

### Post by thepanch on 2008-11-27
hi again

when i selected 
-------------------
Ubuntu 8.10, kernel 2.6.24-21-generic

it came up with this 

[   20.598703] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...

Ubuntu 8.10 pancho-laptop tty1

pancho-laptop login:
--------------------
any tips??

thepanch

---

### Post by LinuxGuy1234 on 2008-11-27
> **thepanch said:**
> hi again

when i selected 
-------------------
Ubuntu 8.10, kernel 2.6.24-21-generic

it came up with this 

[   20.598703] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
Loading, please wait...

Ubuntu 8.10 pancho-laptop tty1

pancho-laptop login:
--------------------
any tips??

thepanch

Login and do:
```
sudo /etc/init.d/gdm start
```

---

### Post by thepanch on 2008-11-27
me again
sudo /etc/init.d/gdm start=

sudo: unable to resolve host pancho-laptop
 *Starting GNOME Display Manager...
                                [ OK ]



i dont know what im doing wrong. or is it the laptop

---

### Post by LinuxGuy1234 on 2008-11-28
> **thepanch said:**
> me again
sudo /etc/init.d/gdm start=

sudo: unable to resolve host pancho-laptop
 *Starting GNOME Display Manager...
                                [ OK ]



i dont know what im doing wrong. or is it the laptop

The stupid case of the gummed up /etc/resolv.conf and /etc/hosts...

Post me your /etc/resolv.conf and /etc/hosts.

---

### Post by dsginter on 2008-11-28
WORKAROUND:

At the live cd boot menu, select the language, highlight the desired selection but then press F6 instead of ENTER.  This will allow you to customize the kernel boot options.  Erase "quiet splash--" and replace it with "vga=771 noapic" (minus the quotes).

This allowed me to boot the LiveCD and install normally.  Once the install was finished, I was able to boot normally.

Good luck!

---

### Post by thepanch on 2008-11-30
> **LinuxGuy1234 said:**
> The stupid case of the gummed up /etc/resolv.conf and /etc/hosts...

Post me your /etc/resolv.conf and /etc/hosts.

i've tried them

/etc/resolv.conf  resulted in -bash: /etc/resolv.conf: Permission denied

and the /etc/hosts has the same "Permission denied"

any clues?

pancho

---

### Post by TheForkOfJustice on 2008-12-07
Yes I have the 4GB Aperture warning too but it doesn't seem to cause any problems.

Compaq Presario laptop V2570CA
AMD 64-bit Turion
ATI Xpress 200M graphics

---

### Post by dustin_44 on 2008-12-09
HP DV6110us laptop - latest bios installed
AMD X2 CPU
1GB Ram
Nvidia 6200 gfx
Ibex 8.10 AMD64
(seems that other posters have common hardware)

I was using 8.04 without this error previously.  I did a "fresh" install using the netboot image to install over the network (similar to the alternate install).  The install went fine. 

I receive this error at every boot up - system only displays the error for 1 second and then it boots up and runs fine.

Everything is working hardware wise - 3D accel, wifi card, etc.  Also sleep & shutdown working fine.  Minor problem with hibernate which I don't think is related.

I will mention that this laptop is ubuntu only so I don't get the full grub screen, just the 3 second timer - not sure if that would make any difference.

---

### Post by cncsc on 2008-12-10
i have the same error message when startup, but the system still works normally

---

### Post by FireKitty on 2008-12-10
ECS 780A-gm mobo w/4GB ram
Kubuntu 8.10 x64

I had the Aperture beyond 4GB. Ignoring. message too.  It didn't prevent me from booting, and the third line of the message said "Please enable the IOMMU in the BIOS setup" or something like that.  When I searched for that message, I found someone (sorry, can't remember where now) who posted that adding iommu=noaperture (or iommu=soft) to the kernel line in the /boot/grub/menu.lst file would take care of this problem.  It worked for me, but like I said, the error didn't keep me from booting.

---

### Post by LinuxGuy1234 on 2008-12-14
> **thepanch said:**
> i've tried them

/etc/resolv.conf  resulted in -bash: /etc/resolv.conf: Permission denied

and the /etc/hosts has the same "Permission denied"

any clues?

pancho

Post me them, using the LiveCD. Do this:
```
Applications>Accessories>Terminal
sudo mkdir /fix
sudo mount /dev/ubuntu-partition /fix #replace ubuntu-partition
sudo cat /fix/etc/resolv.conf /fix/etc/hosts #Post the output of this
```

If you get a "[sudo] password for ubuntu:" prompt, I think you need to type in "ubuntu" or enter.

---

### Post by bbbl67 on 2008-12-28
> **mmeclimate said:**
> Hi,

I upgraded my Ubuntu 8.04 to 8.10, Intrepid Ibex, today.
The reboot process did not work and I got the following message:

0.004000 Aperture beyond 4GB. Ignoring.

I've read some threads that other people had the same problem. I rebooted it again and pressed 'ESC', then I selected the following kernel: 2.6.24-24-generic and then I was able to reboot properly and go to the log in window.

Why isn't kernel 2.6.27-7-generic not working?
Is there a fix for this?

Thanks!

Michael

Just add "iommu=noaperture" to the end of your "kernel" line in your Grub's menu.lst. For example here is my entry:

```
title Ubuntu 8.10, kernel 2.6.27-7-generic
kernel /boot/vmlinuz-2.6.27-7-generic root=UUID=bffa3f1f-5bf5-4488-a028-07d42a7b8277 ro quiet splash iommu=noaperture
initrd /boot/initrd.img-2.6.27-7-generic
```

---

### Post by Arenlor on 2008-12-31
> **thepanch said:**
> i've tried them

/etc/resolv.conf  resulted in -bash: /etc/resolv.conf: Permission denied

and the /etc/hosts has the same "Permission denied"

any clues?

pancho

Try using nano:
```
nano /etc/resolv.conf
```

---

### Post by venci72 on 2009-01-08
I have "Aperture beyond 4GB. Ignoring." with 2.6.27-xx kernel and can not boot. Even Live CD. After upgrade from 8.04 I boot with 2.6.24-xx kernel, but I have not working n vidia drivers and 3d acceleration.

---

### Post by Martin Marshalek on 2009-01-11
I get that message but Ubuntu boots normal and woks fine.

---

### Post by Ripose on 2009-02-04
[LEFT][FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]I have the same problem: keep hitting a key to complete boot.[/SIZE][/FONT][/SIZE][/FONT][FONT=Times New Roman][SIZE=3]
[SIZE=3][FONT=Times New Roman]Same error message as everyone else.[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]ASUS - M3N-HT Deluxe[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]AMD - Phenom 9850 2.5 GHz Quad[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]G.Skill - 4GB DDR2 PC2-1600[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]The error message stated: Enable IOMMU in BIOS, however it is difficult to figure out which setting they mean since there is no setting labelled IOMMU.[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]Updating the BIOS had NO effect. [/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]I am getting closer to solving this, when I do I will definitely post again.[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]I did find this quote from AMD.[/FONT][/SIZE][/LEFT]
 
[SIZE=3][FONT=Times New Roman]> 
[LEFT][SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]1 Overview[/FONT][/SIZE][/LEFT]
 
[LEFT][/FONT][/SIZE][FONT=Times New Roman][SIZE=3][FONT=Times New Roman][SIZE=3]The[COLOR=blue] Input Output Memory Management Unit (IOMMU)[/COLOR] is a chipset function that translates addresses used in DMA transactions and protects memory from illegal access by I/O devices.[/SIZE][/FONT][/SIZE][/FONT][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman][SIZE=3][FONT=Times New Roman]The IOMMU can be used to:[/FONT][/SIZE][/LEFT]
 
[LEFT][SIZE=3][FONT=Times New Roman]• Replace the existing GART mechanism.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]• Remap addresses above 4GB for devices that do not support 64-bit addressing.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]• Allow a guest OS running under a VMM to have direct control of a device.[/FONT][/SIZE]
[SIZE=3][FONT=Times New Roman]• Provide fine-grain control of device access to system memory.[/FONT][/SIZE][/LEFT]
[SIZE=3][FONT=Times New Roman]• Enable a device direct access to user space I/O.[/FONT][/SIZE]
 
[/FONT][/SIZE]
 
[LEFT]I'll post more info even I don't find the fix.[/FONT][/SIZE][/SIZE][/FONT][/LEFT]

---

### Post by Ripose on 2009-02-04
Well so far I have found 3 settings to try in_ /boot/grub/menu.lst_ for this issue.

iommu=noaperture <--- According to ASUS
iommu=memaper   <--- According to AMD
iommu=calgary      <--- According to linux.com

I was born in Calgary, Alberta, Canada but I'm still not sure what the calgary setting does.:D
--------------------------------------------------------------------------------------------------
But even after setting iommu=memaper in menu.lst _ /boot/config-2.6.27-7-generic_ does not show this setting, it shows:

GART_IOMMU=y
AMD_IOMMU=y
CALGARY_IOMMU=y
CALGARY_IOMMU=enabled by default
---------------------------------------------------------------------------------------------------
System Messages displays:

Phoenix BIOS detected, possible corruption [forgot this part] trying to work around.
---------------------------------------------------------------------------------------------------

Anyways AMD says if you don't have an IOMMU setting in BIOS you should add iommu=memaper to the kernel line in menu.lst This got rid of the error message but I still have to repeatedly hit a key to boot.
---------------------------------------------------------------------------------------------------

Confused? :(

Me Too! :confused:

---

### Post by lotharjade on 2009-02-04
Good job Ripose.  Keep up the good work.  I wouldn't know where to start on this.  :KS

It would be nice if you had assistance from the Kernel team though.  They have seemed to have ignored this issue.  :(

---

### Post by Ripose on 2009-02-06
Read **[THIS POST]("http://ubuntuforums.org/showthread.php?t=1059545")** for a fix to the hold down a key to boot issue.

---

### Post by Ripose on 2009-02-06
ASUS online says to ensure MEMORY HOLE MAPPING is enabled in BIOS. 

They also said it might have something to do with Graphics Memory Aperature but did not give me a fix.:rolleyes:

ASUS on-line sucks for actually getting a simple answer.:mad:

Also check your RAM, if you only have 2 sticks they should be in the Black slots NOT the Yellow ones.

---

### Post by elalbibe on 2009-03-07
I am getting this error also.  AMD Athlon 64  duo core, microstar motherboard.  The boot is usually successfull, but sometimes freezes with the splash bar at 25%.  A reboot almost always works.  I have had some freezing of firefox also.

---

### Post by zieglerj on 2009-03-07
could this be the result of using the manually installed Nvidia driver? I tried to instal an older version and it gave me a message that the Nvidia drivers don't work with the Intrepid kernel.

---

### Post by zika on 2009-03-07
> **Ripose said:**
> Well so far I have found 3 settings to try in_ /boot/grub/menu.lst_ for this issue.

iommu=noaperture <--- According to ASUS
iommu=memaper   <--- According to AMD
iommu=calgary      <--- According to linux.com

I was born in Calgary, Alberta, Canada but I'm still not sure what the calgary setting does.:D
--------------------------------------------------------------------------------------------------
But even after setting iommu=memaper in menu.lst _ /boot/config-2.6.27-7-generic_ does not show this setting, it shows:

GART_IOMMU=y
AMD_IOMMU=y
CALGARY_IOMMU=y
CALGARY_IOMMU=enabled by default
---------------------------------------------------------------------------------------------------
System Messages displays:

Phoenix BIOS detected, possible corruption [forgot this part] trying to work around.
---------------------------------------------------------------------------------------------------

Anyways AMD says if you don't have an IOMMU setting in BIOS you should add iommu=memaper to the kernel line in menu.lst This got rid of the error message but I still have to repeatedly hit a key to boot.
---------------------------------------------------------------------------------------------------

Confused? :(

Me Too! :confused:

add _iommu=noaperture_ at the end of the line in */boot/grub/menu.lst* starting with *#defoptions*. then do *sudo update-grub* and, finally reboot ...

update: or, better, read this:```
IOMMU (input/output memory management unit)

 Currently four x86-64 PCI-DMA mapping implementations exist:

   1. <arch/x86_64/kernel/pci-nommu.c>: use no hardware/software IOMMU at all
      (e.g. because you have < 3 GB memory).
      Kernel boot message: "PCI-DMA: Disabling IOMMU"

   2. <arch/x86_64/kernel/pci-gart.c>: AMD GART based hardware IOMMU.
      Kernel boot message: "PCI-DMA: using GART IOMMU"

   3. <arch/x86_64/kernel/pci-swiotlb.c> : Software IOMMU implementation. Used
      e.g. if there is no hardware IOMMU in the system and it is need because
      you have >3GB memory or told the kernel to us it (iommu=soft))
      Kernel boot message: "PCI-DMA: Using software bounce buffering
      for IO (SWIOTLB)"

   4. <arch/x86_64/pci-calgary.c> : IBM Calgary hardware IOMMU. Used in IBM
      pSeries and xSeries servers. This hardware IOMMU supports DMA address
      mapping with memory protection, etc.
      Kernel boot message: "PCI-DMA: Using Calgary IOMMU"

 iommu=[<size>][,noagp][,off][,force][,noforce][,leak[=<nr_of_leak_pages>]
    [,memaper[=<order>]][,merge][,forcesac][,fullflush][,nomerge]
    [,noaperture][,calgary]

  General iommu options:
    off                Don't initialize and use any kind of IOMMU.
    noforce            Don't force hardware IOMMU usage when it is not needed.
                       (default).
    force              Force the use of the hardware IOMMU even when it is
                       not actually needed (e.g. because < 3 GB memory).
    soft               Use software bounce buffering (SWIOTLB) (default for
                       Intel machines). This can be used to prevent the usage
                       of an available hardware IOMMU.

  iommu options only relevant to the AMD GART hardware IOMMU:
    <size>             Set the size of the remapping area in bytes.
    allowed            Overwrite iommu off workarounds for specific chipsets.
    fullflush          Flush IOMMU on each allocation (default).
    nofullflush        Don't use IOMMU fullflush.
    leak               Turn on simple iommu leak tracing (only when
                       CONFIG_IOMMU_LEAK is on). Default number of leak pages
                       is 20.
    memaper[=<order>]  Allocate an own aperture over RAM with size 32MB<<order.
                       (default: order=1, i.e. 64MB)
    merge              Do scatter-gather (SG) merging. Implies "force"
                       (experimental).
    nomerge            Don't do scatter-gather (SG) merging.
    noaperture         Ask the IOMMU not to touch the aperture for AGP.
    forcesac           Force single-address cycle (SAC) mode for masks <40bits
                       (experimental).
    noagp              Don't initialize the AGP driver and use full aperture.
    allowdac           Allow double-address cycle (DAC) mode, i.e. DMA >4GB.
                       DAC is used with 32-bit PCI to push a 64-bit address in
                       two cycles. When off all DMA over >4GB is forced through
                       an IOMMU or software bounce buffering.
    nodac              Forbid DAC mode, i.e. DMA >4GB.
    panic              Always panic when IOMMU overflows.
    calgary            Use the Calgary IOMMU if it is available

  iommu options only relevant to the software bounce buffering (SWIOTLB) IOMMU
  implementation:
    swiotlb=<pages>[,force]
    <pages>            Prereserve that many 128K pages for the software IO
                       bounce buffering.
    force              Force all IO through the software TLB.

  Settings for the IBM Calgary hardware IOMMU currently found in IBM
  pSeries and xSeries machines:

    calgary=[64k,128k,256k,512k,1M,2M,4M,8M]
    calgary=[translate_empty_slots]
    calgary=[disable=<PCI bus number>]
    panic              Always panic when IOMMU overflows

    64k,...,8M - Set the size of each PCI slot's translation table
    when using the Calgary IOMMU. This is the size of the translation
    table itself in main memory. The smallest table, 64k, covers an IO
    space of 32MB; the largest, 8MB table, can cover an IO space of
    4GB. Normally the kernel will make the right choice by itself.

    translate_empty_slots - Enable translation even on slots that have
    no devices attached to them, in case a device will be hotplugged
    in the future.

    disable=<PCI bus number> - Disable translation on a given PHB. For
    example, the built-in graphics adapter resides on the first bridge
    (PCI bus number 0); if translation (isolation) is enabled on this
    bridge, X servers that access the hardware directly from user
    space might stop working. Use this option if you have devices that
    are accessed from userspace directly on some PCI host bridge.
```

I vote for```
iommu=off,noagp,noaperture
```if You do not have AGP card.

---

### Post by warpasylum on 2009-03-09
Having the same issue on my acer aspire 5050-3087. I get the message "Aperture beyond 4 GB ignoring / Your BIOS doesn't leave a aperture memory hole / Please enable the IOMMU option in the BIOS setup / This costs you 64 MB of RAM". BIOS is V1 3302. Tried version 3309 and 3315. Blank screen with blinking cursor after boot splash on 3309, just a blank screen with 3315. I get the message and then Ubuntu boots like normal. No issues other than not seeing all the RAM. BIOS doesn't have an IOMMU option. Hope this helps.

---

### Post by Slim Odds on 2009-03-21
> **zika said:**
> [/code]I vote for```
iommu=off,noagp,noaperture
```if You do not have AGP card.

"iommu=off" disables my USB ports.

I think that the noagp and noaperture are fine.....

---

### Post by zika on 2009-03-21
> **Slim Odds said:**
> "iommu=off" disables my USB ports.
I think that the noagp and noaperture are fine.....
sorry to hear that. it did not in my case. I hope that I did not cause You to loose any time or data ...

---

### Post by Slim Odds on 2009-03-21
> **zika said:**
> sorry to hear that. it did not in my case. I hope that I did not cause You to loose any time or data ...

No problem, I just had to edit /boot/grub/menu.lst

But my point was that there is no need to turn iommu off just to fix the AGP issue. Just use iommu=noagp,noaperture, which works just dandy.

---

### Post by zieglerj on 2009-03-24
So I came back to this thread after your fix worked perfectly to thank you. I would do so formally but the little icon disapeared. Anyway thank you guys, I would have never got this on my own.

---

### Post by cisono on 2009-04-24
> **surj08 said:**
> I get the same thing! i get the error but it hasnt stopped anything.

We all using the 86_64x version here?

Yes, 64 Bit Ubuntu 8.10 and 64 Bit Processor AMD x4

Just thought I'd mention this as well:
PC boots fine but am stuck with 800x600 graphics resolution.
The old proprietary nVidia video drivers (177) would not activate.
The new proprietary nVidia video drivers (180) seemed to install but won't start, so still stuck in low graphics mode.

---

