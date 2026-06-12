---
title: "Black screen of death after after upgrade to 8.10"
date: 2008-10-30
forum: Installation &amp; Upgrades
---

### Post by 12__monkeys on 2008-10-30
Hello,

I've upgraded from Hardy to Intrepid using the update manager command *'update-manager -d'*.  30 minutes later the upgrade finished and I was asked to reboot.  

Following the usual bios info, I see the splash screen but then the monitor screen goes black and reports 'no signal'.  

I don't think there's anything wrong with the OS as I hear the startup sound a few minutes later but I never the monitor never switches back on.

I believe this may be a problem with the screen resolution or frequency but can't be sure.  
I know that the problem is not with the graphics card hardware as I see the splash screen before losing signal.  The graphics card I'm using is an ATI 9600.  

Does anyone have any suggestions?

Thanks

---

### Post by garyedwardjohnston on 2008-10-30
I'm not a fan of upgrades...clean installs for me :)

---

### Post by revoman3 on 2008-10-30
Let me guess your using a laptop...
[Check this out]("http://ubuntuforums.org/showthread.php?t=962779")

---

### Post by aurics on 2008-10-30
I tried clean install exactly the same ubuntu 8.10 doesn't recognize
my video card ati even live desktop won't load

booting normal there is desktop welcome sound 
but "monitor screen goes black and reports 'no signal'"

So Ubuntu 8.10 NOT working on ATI video cards, at least on mine ...

---

### Post by Arabiest on 2008-10-30
I cant really add something, but Iam surprised by the download time as 30min...mine it says it needs 22hrs from a local net caffee.

Despite of this, my suggestion if u can download the ISO file and convert it to bootable CD from where you install the 8.10 with ease...btw, this is what I am doing now and believe me it will take a day to do that...so I am letting the PC downloading and doing my own business.

Hope this will help.

---

### Post by bym007 on 2008-10-30
hi everyone,

I'm facing similar issue here. I updated from 8.04 to 8.10 using "update-manager -d" on my desktop (amd64 3400+, 1.5g ram)

Well it took its time to download and update the binaries (more or less an hour, using my 10mbit connection exclusively.

Upon rebooting, I get the bios screen, then ubuntu screen, and then it goes blank...

So I'm thinking that it is not a laptop only related issue...

Any workarounds found yet ?

---

### Post by 12__monkeys on 2008-10-30
I'm actually using an ATI 9600 series in a desktop and not a laptop.

Is there a way that I can interupt the boot sequence at the GRUB stage and load to a terminal prompt.  I could then have a look at my xconf file perhaps?

Thanks

---

### Post by anettehe on 2008-10-30
Hi guys. 

Me and my bf have the same problem. We both have ATI Radeon HD 3870 graphics card. But on one of our PC we stopped the installer, booted and choosed the "continiue installation in safe graphics mode" and its seems to work. 

So now im going to try to reboot and uninstall compiz and see if it works.

---

### Post by anettehe on 2008-10-30
we solved it for ATI cards!

You mount the file in windows, do as always. When the computer boots push esc so you get the menu and choose continiue install in safe graphics mode, then ubuntu will be installed without compiz and it works.

:)

---

### Post by peakshysteria on 2008-10-30
> **aurics said:**
> I tried clean install exactly the same ubuntu 8.10 doesn't recognize
my video card ati even live desktop won't load

booting normal there is desktop welcome sound 
but "monitor screen goes black and reports 'no signal'"

So Ubuntu 8.10 NOT working on ATI video cards, at least on mine ...

Hmm, sounds like the black-screen-of-death problem are back. Might be screen out of range = X is running to large resolution. Most threads concerning this seems to be older ATI cards. Not sure if this affects newer cards.

The release note states:
> ATI "fglrx" video support

The ATI video driver in 8.10 drops support for video cards with r300 based chips (the Radeon 9500 - X600 Series of cards). If you have such a card, please use "Hardware Drivers" at System/Administration to disable it before the upgrade. Please see [bug 284408]("https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408") for more information


It would really help if people posted what card they have **aurics**. Without it you keep the rest of us hanging.

---

### Post by gtg on 2008-10-30
Same problem here ...

Clean install
Machine previously supported 7.10 and 8.04
Dell Optiplex DX260, Pentium 4, 512 MB RAM, Intel 82845G graphics controller
Installation indicates successful
Reboot
No splash screen
Enter user name
Enter user password
BLACK SCREEN and no disk activity

Any suggestions would be appreciated.

---

### Post by duanedesign on 2008-10-30
Screen Blanks/Monitor Turns Off

Using a laptop with a GeForce Go card, or connecting the sole display via DVI on a dual-head system sometimes results in the screen not receiving a picture. This is caused by the driver outputting video to the VGA port on the graphics card, instead of DVI.

The usual hint that you have this problem is when you hear the startup sound but nothing appears on the screen. If you do not hear any sound, you are more than likely experiencing unrelated problems.

This is a launchpad bug about displays on digital outputs being blank when using NVIDIA binary driver, and can be resolved by editing your /etc/X11/xorg.conf file:

    *

      Switch to the console (Try using ctrl+alt+F1, or reboot and select recovery mode from the GRUB menu.)
    *

      Use your text editor to open /etc/X11/xorg.conf. (try sudo nano /etc/X11/xorg.conf)
    *

      Find the line that says Section "Screen"
    *

      Insert a new line that says Option "UseDisplayDevice" "DFP".
    *

      Save the file. If you had to restart into recovery mode, type reboot, otherwise restart your display using sudo /etc/init.d/gdm restart.


here is the Launcpad bug   [https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/82312](https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.24/+bug/82312)

---

### Post by aurics on 2008-10-30
ati HD2600XT

---

### Post by peakshysteria on 2008-10-30
> **aurics said:**
> ati HD2600XT

Try [Ubuntu Intrepid Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

And please post back your results. Good luck man :)

---

### Post by bym007 on 2008-10-30
Right guys, I have just installed 8.04 back on my system to bring it back to working conditions. However, I noticed that some people are having similar issues while using ATI cards, while my mobo has built-in VIA S3 Unichrome Pro VGA sharing memory from my RAM.

System boots till the username/password login screen, and from there I do not see anything. :(

I wonder whats causing this issue.

---

### Post by bym007 on 2008-10-30
Parallel to my adventures above, I have run 8.10 x86 LiveCD on my Acer Ferrari 4005wlmi laptop as well (AMD64 2.0, 1gb RAM, ATi X700).

While first time video crashed (flicking screen), I had to cold reboot the laptop. Second time, I was able to get the X run properly. So, to be sure, I booted 8.10 from LiveCD 3-4 times, and it worked fine everytime afterwards. So it must be probably a one off hitch...

---

### Post by peakshysteria on 2008-10-30
> **bym007 said:**
> Parallel to my adventures above, I have run 8.10 x86 LiveCD on my Acer Ferrari 4005wlmi laptop as well (AMD64 2.0, 1gb RAM, ATi X700).

While first time video crashed (flicking screen), I had to cold reboot the laptop. Second time, I was able to get the X run properly. So, to be sure, I booted 8.10 from LiveCD 3-4 times, and it worked fine everytime afterwards. So it must be probably a one off hitch...

Have you installed it or have you just ran it of the LiveCD? And how did you install it if you did (clean install (LiveCD/Alternate CD) or Upgrade)??

---

### Post by kohoutec on 2008-10-30
Similar problems for me. Acer Aspire 5650 laptop with an NVidia Geforce go 7600 card

Booting from the live CD, I see the Ubuntu logo, then gets to a blank screen (The monitor is still switched on, eg it's backlit but nothing output), I also hear the usual logon sounds. So, I burnt and installed the alternative CD and get the same issue once installed.

I've just booted into a Mandriva Live CD I had hanging around and checked my xorg.conf on the newly installed Ubuntu system, it's completely blank! I'm not too experienced with Linux but know enough to realise this isn't good :)

Off to bed now but will be interested to catch up with this again tomorrow if anyone has any ideas...

---

### Post by peakshysteria on 2008-10-30
From 8.10 on X can run without xorg.conf. So this sounds like it should be. This looks more like a driver issue: check the release notes: [nVidia "legacy" video support]("http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support")

---

### Post by bym007 on 2008-10-30
> **peakshysteria said:**
> Have you installed it or have you just ran it of the LiveCD? And how did you install it if you did (clean install (LiveCD/Alternate CD) or Upgrade)??

As I mentioned earlier, I was running it off the LiveCD. Sorry if I was not clear enough. I had tried to install it earlier, and ended up frustrated. So I did not want to risk my working laptop as well ... Hence, the LiveCD trial ...

Hope this helps ...

---

### Post by jerrylamos on 2008-10-30
> **gtg said:**
> Same problem here ...

Clean install
Machine previously supported 7.10 and 8.04
Dell Optiplex DX260, Pentium 4, 512 MB RAM, Intel 82845G graphics controller
Installation indicates successful
Reboot
No splash screen
Enter user name
Enter user password
BLACK SCREEN and no disk activity

Any suggestions would be appreciated.

Sounds like the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

---

### Post by BlackIrish on 2008-10-30
Same here, I get "Video Mode Not Supported" on a ATI Radeon 4850 :(

---

### Post by kohoutec on 2008-10-31
> **peakshysteria said:**
> From 8.10 on X can run without xorg.conf. So this sounds like it should be. This looks more like a driver issue: check the release notes: [nVidia "legacy" video support]("http://www.ubuntu.com/getubuntu/releasenotes/810#nVidia%20%22legacy%22%20video%20support")

Ah, didn't realise that (xorg.conf). I've already checked the NVidia legacy notes and that *shouldn't* be affecting me from what I understand. Going to have a proper look at things over the weekend, no doubt I'll be back here asking for help :)

---

### Post by bym007 on 2008-10-31
> **jerrylamos said:**
> Sounds like the same black screen problem I've been getting with Intel graphics since Aug 13...

...From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

So are you suggesting that compiz has to be stopped or removed to make X work even for VIA S3 Chrome chipset VGAs ?

---

### Post by peakshysteria on 2008-10-31
I think you just have to follow the install guide for your ATI card. No more, no less:> **peakshysteria said:**
> Try [Ubuntu Intrepid Installation Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide")

And please post back your results. Good luck man :)

In addition some positive old news regarding we the ATI people: [Canonical Publishes ATI Catalyst 8.10 Beta]("http://www.phoronix.com/scan.php?page=article&item=canonical_catalyst_811&num=1")

---

### Post by flamarro on 2008-10-31
I also done the upgrade and i could never have ATI working, only using vesa driver.
Then, with official release, done a clean install, even worse, the damn black screen, and more, empty xorg.conf.
Took a backup of it, a part of the mandriva xorg that i was testing and some pieces of others xorgs builted in time.
My xorg now:```

# File generated by XFdrake (rev 247269)
# **********************************************************************
# Refer to the xorg.conf man page for details about the format of
# this file.
# **********************************************************************

Section "ServerLayout"
	Identifier     "layout1"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
	InputDevice    "Keyboard1" "CoreKeyboard"
	InputDevice    "Mouse1" "CorePointer"
	Option	    "AIGLX" "true"
EndSection

Section "Files"
EndSection

Section "Module"
	Load  "glx" # 3D layer
	Load  "dri" # direct rendering
EndSection

Section "ServerFlags"

 # allows the server to start up even if the mouse does not work
	Option	    "allowmouseopenfail"
EndSection

Section "InputDevice"
	Identifier  "Keyboard1"
	Driver      "kbd"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "pt"
	Option	    "XkbOptions" "compose:rwin"
EndSection

Section "InputDevice"
	Identifier  "Mouse1"
	Driver      "mouse"
	Option	    "Protocol" "ExplorerPS/2"
	Option	    "Device" "/dev/mouse"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	Option	    "UseFastTLS" "1"
	BusID       "PCI:3:0:0"
EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection

Section "DRI"
	Mode         0666
EndSection

Section "Extensions"
	Option	    "RENDER" "Enable"
	Option	    "DAMAGE" "Enable"
	Option	    "Composite" "Enable"
EndSection

```

with this xorg and vesa driver i manage to login into X then made a lot of attempts changing a lot, always black screen. Then on one reboot in "safe mode" did apt-get remove fglrx* and apt-get remove compiz and compiz-core. Restarted and follow [this]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually"), restarted and i saw ( i have splash to show text )a error in something related to fglrx and DPMK. X didn't start, not black but with low resolution screen. changed to vesa again, login and update manager says that i have some updates to do, all related to xorg, done it and restarted...... All i can say is that everything is working, even compiz that i installed again, and even updating xorg with update manager i have the line in /etc/default/linux-restricted-modules-common that blacklists with fglrx on it ?????
hope someone can understand because all i can say is that i felt lucky  :)

---

### Post by jerrylamos on 2008-10-31
> **bym007 said:**
> So are you suggesting that compiz has to be stopped or removed to make X work even for VIA S3 Chrome chipset VGAs ?

It's not X, it's compiz that's hanging up.  The "official fix" for Intrepid for some graphics is to not start compiz.  See developers comments on launchpad bug 259385.  They think it is the hardware failing.  I think it is compiz doing "fancy tricks" with "graphics hardware and drivers" all for "eye candy".  The price for "eye candy" for some is "pc freeze" on others.

If you really want "eye candy" then install 8.04 where compiz works.  8.04 has long term support anyway.

Jerry

---

### Post by HeWhoE on 2008-11-03
I just upgraded from 8.04 to 8.10 on my Dell Dimension 4500S.  It's a desktop with an Intel 845 G chip set.  Now I get the black screen too.  I see a brown screen from gdm as it logs me in automatically, but then it turns black and all I can see is my mouse pointer.

I'd like to use the older Intel video driver with 8.10 if at all possible.  

Even with Hardy, I preferred using the old Intel video driver (the one that was the default with Feisty Fawn and Edgy Eft).  I used it in combination with 915resolution on my widescreen monitor because I got better performance with compiz that way.

---

### Post by the lush on 2008-11-03
Yep, white screen issue here (laptop inverter still supplies power to panel despite lack of signal, therefore white not black). ATI 3650. Really quite unimpressed that this was a known error over a month ago (launchpad) and yet there was no obvious warning that people using ATI should not try 8.10... also, removing Compiz, the integration of which has been such a USP for Ubuntu is not a solution. The only real solution is to stick with 8.04 and hope that none of the updates to it lead to this issue (please Ubuntu developer people, please don't put this change in the updates)

---

### Post by gzambianchi on 2008-11-03
> **bym007 said:**
> So are you suggesting that compiz has to be stopped or removed to make X work even for VIA S3 Chrome chipset VGAs ?
It worked for me.
I've got the same problem with an Intel 82845.

Removing compiz and compiz-core solved my problem.

thanks

---

### Post by ByteJuggler on 2008-11-03
FWIW, I've had gobs of trouble with one of my machines and Intrepid, with an ATI 9800XT (AGP).  One of the recent driver updates seem to have killed even the OSS driver support (ati/radeon driver) and the proprietary one crashes as well (fglrx) at present. 

However, if anyone is having similar trouble getting X to start on a fully up to date Intrepid system using the OSS ati/radeon driver, then you might try installing the latest not-yet-releaesd one [from here]("http://ppa.launchpad.net/tormodvolden/ubuntu/pool/main/x/xserver-xorg-video-ati/"), which fixed the issue (at leat for the OSS driver) for me.

The bug report on Launchpad is [here]("https://bugs.launchpad.net/ubuntu/+source/xserver-xorg-video-ati/+bug/292868").

---

### Post by 12__monkeys on 2008-11-04
Unfortunately removing compiz hasn't resolved the problem for me.  Does anyone know of any log files that could be of any help that I can check and post the contents of on this forum?

Thanks

---

### Post by lpevey on 2008-11-05
I just want to report that I have the same problem.  It happens both when I upgrade from Hardy and when I try to boot from the live CD.  The startup screen displays fine, but when the login screen is supposed to appear (I can hear the sound), the screen is blank.  I had no problems upgrading a second computer with an almost identical configuration, and the live cd also boots fine on that computer.  Both computers have the same motherboard, memory, etc., and had very similar Hardy configurations.  The only hardware differences are in the video card and monitor.  The computer that upgraded fine has an nvidia 8600 GT card and an NEC LCD display.  The computer that has the black screen problem has an Nvidia 8800 GTS and Dell 30" monitor.  I suspect it's a monitor problem, though I have no idea why it wasn't a problem under Hardy.  I've tried adding 'Option "DPMS"' to the monitor section of my xorg.conf, but that didn't help.  Also tried removing compix and compiz-core and using dpkg-reconfigure.  Does anyone have any other suggestions?

---

### Post by lpevey on 2008-11-05
Oops, that should have read, "compiz and compiz-core."

---

### Post by bym007 on 2008-11-07
> **jerrylamos said:**
> Sounds like the same black screen problem I've been getting with Intel graphics since Aug 13.  Excerpting Developers comments from my Launchpad Bug #259385:

"== Desktop effects and Intel 830MG and 845G video cards ==

There is a bug in the intel video driver for the older intel 830 and 845 integrated video cards that are used on laptops like the IBM R30. Desktop effects with compiz will not work on those chips and freeze the system."

From what I've seen on the posts there are a LOT More chips that have symptoms like this.

My workaround is:
Boot in rescue mode
select root shell prompt
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit
resume

If that works you're O.K. except no special visual effects.  If you want to try compiz again, install with Synaptic.

Jerry

Has anyone tried removing compiz and compiz-core from Interpid and noticed any difference ?

I am awaiting any feedback on this... (I have Mobo builtin S3 Chrome VGA card) and a Dell LCD ...

Many thanks ,,

---

### Post by a_sad_snowman on 2008-11-12
I am having similar issues as everyone else. I have an older HP Pavilion with the Intel 845 chipset. I tried removing compiz and compiz core, and it did work the first time i rebooted afterwards. But after I shut it down and rebooted it again, I'm right back to where I started.

The black screen is back and compiz and compiz-core are already gone. Let me know if there are any updates with this. I'd really like to get 8.10 working because of my wireless. It works so much better with 8.10 than 8.04, where I had to use ndiswrapper with a couple of changed drivers.

---

### Post by guitarMan666 on 2008-11-14
Removing Compiz does indeed fix the problem (at least for me).  Ubuntu will boot with Metacity instead, this has to be an issue with the Intel driver.

My integrated Intel chip worked fine with Compiz under Hardy and even under Gutsy and it works fine with all other 3D accelerated programs like the screensavers supplied with Ubuntu and some games I had on hand.

I certainly hope this issue is resolved soon (especially before Jaunty comes out), while they aren't essential, it is nice to have those effects.

---

### Post by peakshysteria on 2008-11-14
[ATI Catalyst™ 8.11 Proprietary Linux x86 Display Driver]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") is out since two days ago. [Please select your operating system, product family and the product and then select GO.]("http://ati.amd.com/support/driver.HTML")

It's strange but it doesn't say that it supports Xorg 7.4. But the releasenotes (pdf) says it does. Anyway this driver is compatible with more graphics cards than the 8.10 version. Haven't tried this version myself since 8.9 is working very smooth in my end :)

---

### Post by Guilden_NL on 2008-11-14
Had one easy clean install on a new HP Pavilion HDX18t laptop, two easy upgrades and now have been going through plenty of problems with a clean install on an Acer Aspire 3050 laptop.  Had this black screen problem, I fiddled around using startx to get the GUI going and got to the point where I could download the ATI driver and install it.  That took care of the black screen problem.  Still working through plenty of others.

It appears that Intrepid has issues with ATI and some Phoenix Bios versions.

Will post more as I get through the other problems on this laptop.

---

### Post by peakshysteria on 2008-11-14
> **peakshysteria said:**
> [ATI Catalyst&#8482; 8.11 Proprietary Linux x86 Display Driver]("http://ati.amd.com/support/drivers/linux/linux-radeon.html") is out since two days ago. [Please select your operating system, product family and the product and then select GO.]("http://ati.amd.com/support/driver.HTML")

It's strange but it doesn't say that it supports Xorg 7.4. But the releasenotes (pdf) says it does. Anyway this driver is compatible with more graphics cards than the 8.10 version. Haven't tried this version myself since 8.9 is working very smooth in my end :)

Guilden_NL: 8.11 fixes a few of the 8.10 driver issues. Also state the other problems you have.

---

### Post by Guilden_NL on 2008-11-14
> **peakshysteria said:**
> Guilden_NL: 8.11 fixes a few of the 8.10 driver issues. Also state the other problems you have.

The Acer Aspire 3050 has an ATI Radeon 1100 in it, so it's not supported by this driver.  I have everything working with the ATI FGLRX driver from the Ubuntu repositories.  But thanks for the link, I've bookmarked it for future use for other systems.

I didn't mention the other issues because they aren't graphics related. The issues that I didn't have with Hardy are sound isn't working, shut down from GUI just drops to the terminal and I have to shut down from there. A known bug with the Phoenix BIOS was worked around in Hardy but manifests itself in Intrepid in a slow down during boot up; it's the old  "IOMMU" issue.  All things that I am sure that I will work out, but were new to Intrepid on this particular laptop.

---

### Post by peakshysteria on 2008-11-14
ATI Mobility RadeonTM X1100 is supported according to the [AMD release notes for the 8.11 driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/catalyst_811_linux.pdf").

---

### Post by zaine_ridling on 2008-11-17
**How do I install the driver from a CD?**
Got the same black screen a couple of weeks ago (going from kubuntu 8.04 to 8.10) and have been waiting for the Catalyst 8.11 driver. It's here. I burned it to a CD on another computer. But here's what I need to do:

[LIST]
[*]Boot from a LiveCD to get to a prompt
[*]Switch the LiveCD with the driver CD?
[*]If so, what command do I use to mount the CD?
[*]After mounting, just type in the filename? (ati*.run)
[/LIST]

That's where I am. Maybe I could download it, but the ATI ubuntu installation wiki didn't help when switching the version to 8.11 catalyst.

Thanks.

---

### Post by peakshysteria on 2008-11-18
Have you tried: [Installing the restricted drivers manually ]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")

This still seems to be the most successful howto out there judging from the different threads in the various forums. (I myself am currently holding in to my 8.9 driver on Hardy).

Edit:

After an irritating trouble with recurring problems with sound in Flash I decided to upgrade to Intrepid. After the upgraded I also got the black screen. Rebooting gave me low graphics mode. Had some trouble with getting my ATI driver up and running. But after following: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") Everything booted fine and dandy. With working flash, java, ATI ccc, Compiz, SAMBA, NTFS, Google Earth etc.

Intrepid seem stable as a rock (but I guess it's still early coming from a fresh upgrade).

---

### Post by zaine_ridling on 2008-11-18
Did not work. Did every [manual] command twice after rebooting and I'm still at a black screen. I can get the mesa drivers to work with the LiveCD boot, but the resolution is distorted. But only black screen from the hard drive.

Thanks, though.

---

### Post by peakshysteria on 2008-11-18
Did you also try: [Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")?

---

### Post by zaine_ridling on 2008-11-18
> **peakshysteria said:**
> Did you also try: [Installing the restricted drivers manually]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_manually")?

Yes, that's exactly what I did... twice. No avail. Thought I'd done something wrong the first time, and started from scratch the second time. There were no errors or surprises. Just boot to the same black screen.

---

### Post by peakshysteria on 2008-11-18
Hmm, strange. You are aware that I've posted two different methods? If so:

Have you disabled/turned of compiz before proceeding with installing the driver? After disabling Compiz have you tried the restricted drivers manager? If this didn't work go for the howto(s) I linked to above once more. If the first method don't work go for the next method. And when ```
sudo gedit /etc/X11/xorg.conf
``` ....I can't remember the name of the section. But you can see one of the sections listing different screen resolutions. Make sure that your right screen resolution is listed first (cut and paste it). Each time I've successfully installed the driver I've also changed this section of my xorg. After reboot the section listing the different screen resolutions is no longer visible in xorg. Not sure why. See if that small detail might help you.

* Edit: I'm sorry I didn't see that the howto says;
> Installing the restricted drivers manually
Please note that for the current version 8.11 of the catalyst drivers, this method of installing with deb packages is broken in intrepid. Use the automated installation method instead.* 
The manuall method won't work at the time being then.

---

### Post by Springy2 on 2008-11-18
Hello

I just upgraded from 8.04 to 8.10 and I'm having the same problem of the black screens, my video card is Radeon 9200 and it happens about 30 secs after I login either as a regular member or root and same when I choose that hardware reconfigure option in the small menu before the system loads which reports about low graphics

Is there any solution anyone can advice me? I'm relatively new to all this so please keep it simple

---

### Post by zaine_ridling on 2008-11-18
Thanks again, **peakshysteria**, I'll give that a try.

---

### Post by peakshysteria on 2008-11-18
> **Springy2 said:**
> Hello

I just upgraded from 8.04 to 8.10 and I'm having the same problem of the black screens, my video card is Radeon 9200 and it happens about 30 secs after I login either as a regular member or root and same when I choose that hardware reconfigure option in the small menu before the system loads which reports about low graphics

Is there any solution anyone can advice me? I'm relatively new to all this so please keep it simple

What's the output of:
```
fglrxinfo
```

The solution which worked for me:

> **peakshysteria said:**
> Have you tried: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22")

This still seems to be the most successful howto out there judging from the different threads in the various forums. (I myself am currently holding in to my 8.9 driver on Hardy).

Edit:

After an irritating trouble with recurring problems with sound in Flash I decided to upgrade to Intrepid. After the upgrad I also got the black screen of death. Rebooting gave me no working choice but low graphics mode. Strangely enough low graphics mode booted the right resolution (1280x1024). fglrxinfo showed as anticipated the dreaded MESA hell. Had some trouble with getting my ATI driver up and running. But after following: [Installing the restricted drivers "the Ubuntu way"]("http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide#Installing_the_restricted_drivers_.22the_Ubuntu_way.22") Everything booted fine and dandy. With working flash, java, ATI ccc, Compiz, SAMBA, NTFS, Google Earth etc.

Intrepid still seems stable as a rock and faster than ever (but I guess it's still early coming from a fresh upgrade). But things are looking very good after a disappointing, but anticipated, start with Intrepid 

---

### Post by Springy2 on 2008-11-18
> **peakshysteria said:**
> What's the output of:
```
fglrxinfo
```

The solution which worked for me:

I dunno where to run this command in, in the few secs I have inside the system before the screen goes black I tried it in terminal and it wasn't recognized

And with that suggested solution, because of the problem mentioned above I can't disable or enable anything, only thing I can do if it helps in anything is drop to root shell from recovery mode

---

### Post by zaine_ridling on 2008-11-18
**peakshysteria**, none of the methods worked -- manual install, open source, or restricted-drivers. Still a black screen. I **know** it's not kubuntu's fault; ATI drivers are just that way sometimes. In fact, many video drivers are. 

But after a couple of weeks and no luck, I don't have the time to wait anymore. In the meantime, I'll try a different distro and come back to Ubuntu for 9.04. I'm grateful for the help.

---

### Post by dprestemon on 2008-11-19
I also upgraded from Hardy with "upgrade-manager -d" and got the black screen of death.  I get the normal splash screen with the orange bar followed by a frozen spinning disc mouse pointer, followed by black, but no indication of a lost monitor signal. Tried all the fixes available in recovery mode with no effect.  My video is an onboard VIA K8M890 chip which worked fine with the open source Open Chrome drivers in Hardy.  What now??

---

### Post by sinned3k on 2008-11-19
I had the same problem. I do not think it was a video card issue because I tried a number of alternatives which did not work. 
I bet you partitioned your drives yourself too?? Am no genius.. but after 8.10 partitioned install, it loses place of the boot systems file hence why you get a blank screen.

I suggest you do a clean boot by default and after installation partition your drives. 

Hope that helps..!

---

### Post by zaine_ridling on 2008-11-19
The odd thing is, the LiveCD boots and works fine. Just the reboot blacks out. Other distros like OpenSUSE, Fedora, and ZenWalk load and display fine after installation. I've always had hard luck with Ubuntu among my various machines going back as far as 6.06. And yet kubuntu is my fav distro! Go figure.

:)

---

### Post by dprestemon on 2008-11-20
If you have a Via Chrome video chipset, and after upgrading to Intrepid your system freezes with a black screen during start-up, this is a known bug with a fairly simple workaround.  It is fully explained at
 
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

In a nutshell,  choose "Recovery Mode" at startup, then drop to a root prompt when the menu appears.  First, make sure you have the Openchrome drivers installed by running ```
sudo apt-get install xserver-xorg-video-openchrome
``` Then, open the file xorg.conf for editing with

 ```
sudo nano /etc/X11/xorg.conf
```
In the "Device" section add the following lines;

```
Driver            "openchrome"
Option            "XaaNoImageWriteRect"
Option            "swcursor"

```
I'm happily writing this from my Ubuntu 8.10 installation, so I can confirm that it works.

---

### Post by bym007 on 2008-11-28
> **dprestemon said:**
> If you have a Via Chrome video chipset, and after upgrading to Intrepid your system freezes with a black screen during start-up, this is a known bug with a fairly simple workaround.  It is fully explained at
 
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

In a nutshell,  choose "Recovery Mode" at startup, then drop to a root prompt when the menu appears.  First, make sure you have the Openchrome drivers installed by running ```
sudo apt-get install xserver-xorg-video-openchrome
``` Then, open the file xorg.conf for editing with

 ```
sudo nano /etc/X11/xorg.conf
```
In the "Device" section add the following lines;

```
Driver            "openchrome"
Option            "XaaNoImageWriteRect"
Option            "swcursor"

```
I'm happily writing this from my Ubuntu 8.10 installation, so I can confirm that it works.

After using your steps, I am still stuck with same white "frozen" screen before the login screen!

Any more tips please ?

Update: I am happily using the system now !!

---

### Post by canucks222 on 2009-01-04
i experience a similar problem:
i can see ubuntu starting, but the screen disappears before splash/login screen.
after i enter my id/password, without seeing anything (black monitor with the massage no-supported mode H: 75.0 kHz, V: 60Hz)), regular screen comes back.
i didn't change/do anything with xorg or anything else.
ubuntu 7.x was working without any issues.
i am using FUSE LCD monitor.
any idea how to fix this problem, please?

---

### Post by talkeetnaweb on 2009-01-04
I had the same problem with an earlier version and it turned out the programmers decided to set the screen resolution at 1200 width which my monitor wouldn't handle. Try finding an external monitor with a high resolution and then set the resolution lower. Maybe next version they will set the default resolution to 800x600 until the user changes it higher. I know this is frustrating and very unwindowslike.

---

### Post by canucks222 on 2009-01-04
i tried to use a lcd tv with vga input as a monitor, but no luck.
is there any other way except to replace/change the monitor?
update/edit xorg, etc?

---

### Post by sethtriggs on 2009-01-05
I am having this issue, but with a little twist.

I had successfully installed Ubuntu 8.04 and upgraded it to 8.10 for a spare computer I am letting my girlfriend borrow, but was using a small spare monitor which I keep for emergencies.

She has a much larger Neijiang Direction LCD monitor (Model L-172 Type L7-AK5). When starting the computer, the Ubuntu logo flashes briefly and the loading bar goes through, and then blackness (although occasionally the orange background will show with the spinning disc progress icon).

She can log in blindly and the system starts up normally except for the lost video.

And the screen remains blank from here out. If the power is cycled on the monitor, the screen appears for a second and then goes blank. This occurs with the Console too as I tried to have her switch into Ctrl-Alt-F1. Switching between console and X also causes the screen to work for a second and then go blank.

The kicker is, this is an older integrated video card, on an older MSI motherboard with an Athlon processor.

I have to send a LiveCD to have any hope of this, I suppose...to see if the Live CD environment will work for her as the other computers in the house are not available for her to burn an ISO image.

Are there any commands that can be invoked blindly to install restricted drivers as you suggested in this thread and see if they're in play? I was hoping for a Hail Mary where doing something like that would make the system work properly.

-Seth

---

### Post by canucks222 on 2009-01-06
I was able to fix my problems in two steps:

1) Login screen - by adding "Screen" section into my xorg
[http://dkseto.wordpress.com/2008/10/31/ubuntu-81-login-screen-resolution-problem/](http://dkseto.wordpress.com/2008/10/31/ubuntu-81-login-screen-resolution-problem/)

2) Splash screen - by installing startup manager and changing the resolution

Now everything is working and no more black screens.

---

### Post by pessimizer on 2009-02-08
> **dprestemon said:**
> If you have a Via Chrome video chipset, and after upgrading to Intrepid your system freezes with a black screen during start-up, this is a known bug with a fairly simple workaround.  It is fully explained at
 
[https://help.ubuntu.com/community/OpenChrome]("https://help.ubuntu.com/community/OpenChrome")

In a nutshell,  choose "Recovery Mode" at startup, then drop to a root prompt when the menu appears.  First, make sure you have the Openchrome drivers installed by running ```
sudo apt-get install xserver-xorg-video-openchrome
``` Then, open the file xorg.conf for editing with

 ```
sudo nano /etc/X11/xorg.conf
```
In the "Device" section add the following lines;

```
Driver            "openchrome"
Option            "XaaNoImageWriteRect"
Option            "swcursor"

```
I'm happily writing this from my Ubuntu 8.10 installation, so I can confirm that it works.

Registered to Ubuntuforums just to tell you thanks, because this absolutely did the trick on my ancient Averatec 3280 laptop.  I could feel the blind rage building, but ever since your post headed it off after less than an hour of frustration, I'm having a nice Sunday morning.  I owe you lunch or something.

To repeat: VIA CHROME - Option(XaaNoImageWriteRect + swcursor) = ORANGE SCREEN OF DEATH

---

### Post by emusbau on 2009-05-22
This is the best way I've found to upgrade from 8.04 to 8.10. It's simple and it works for me.




Network Upgrade for Ubuntu Desktops (Recommended)

You can easily upgrade over the network with the following procedure.

   1. Start System/Administration/Software Sources
          *

            intrepid_upgrade1.png
   2. click on the "Updates" tab and change "Show new distribution release" to "Normal releases"
          *

            intrepid_upgrade2.png
   3. Start System/Administration/Update Manager
          *

            intrepid_upgrade2.5.png
   4.

      Click the Check button to check for new updates.
   5.

      If there are any updates to install, use the Install Updates button to install them, and press Check again after that is complete.
   6. A message will appear informing you of the availability of the new release.
          *

            update-manager-upgrade-810.png
   7.

      Click Upgrade.
   8. Follow the on-screen instructions.

---

