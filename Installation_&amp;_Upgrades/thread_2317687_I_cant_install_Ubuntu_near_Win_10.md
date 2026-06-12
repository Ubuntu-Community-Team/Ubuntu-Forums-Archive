---
title: "I cant install Ubuntu near Win 10"
date: 2016-03-18
forum: Installation &amp; Upgrades
---

### Post by kacper3 on 2016-03-18
**Hi, im burn Ubuntu 14.04.4 LTS 64-bit on DVD-R by Infra Recorder and 15.10 64-bit on USB by Universal USB Installer.**
I can try install Ubuntu near Windows 10 and im getting errors while try install Ubuntu, look for videos:
With no parameter nomodeset: [https://www.youtube.com/watch?v=XRub20RL6Uc](https://www.youtube.com/watch?v=XRub20RL6Uc)
With parameter nomodeset: [https://www.youtube.com/watch?v=_TpxkmrFp9g](https://www.youtube.com/watch?v=_TpxkmrFp9g) some errors with nouveau.modeset=0


[COLOR=#ff8c00]**Help me please :(**[/COLOR]


**My PC specs:**
MOBO: Asus Z97-Pro
CPU: Intel i7 4790K
GPU: Asus GTX970 Strix

---

### Post by fantab on 2016-03-18
Try booting the USB/DVD with '[NOMODESET]("http://ubuntuforums.org/showthread.php?t=1613132")' option. This should load your Ubuntu in 'failsafe graphics mode'. Later you can install the specific graphics driver.
It is recommended that you go through the following:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://askubuntu.com/questions/207175/what-does-nomodeset-do](https://askubuntu.com/questions/207175/what-does-nomodeset-do)

I would suggest the you 'Try Ubuntu before Installing' first, then setup your internet, they install ubuntu from desktop...

---

### Post by kacper3 on 2016-03-19
How install ubuntu from dekstop?
After adding nomodeset [https://www.youtube.com/watch?v=_TpxkmrFp9g](https://www.youtube.com/watch?v=_TpxkmrFp9g) some errors with adding nouveau.modeset=0

---

### Post by oldfred on 2016-03-20
With my AsusZ97-AR, I had to change a variety of settings in UEFI to get it to boot in UEFI mode, it wanted to default to BIOS mode.I also had to turn off fast boot in UEFI (different than fast start in Windows). And change to "other" not Windows for UEFI without Secure boot. 
You also need nomodeset, not sure of nouveau.modeset=0 is same or not.

 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
[http://ubuntuforums.org/showthread.php?t=2258575](http://ubuntuforums.org/showthread.php?t=2258575)
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu) 

Slightly older version of Ubuntu, but should be otherwise similar.
      
 Asus z97-A with nVidia GTX 970 Maxwell Ubuntu  15.04
[http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896](http://askubuntu.com/questions/615896/ubuntu-15-04-uefi-cannot-install-blank-screen-no-signal?noredirect=1#615896)

---

### Post by kacper3 on 2016-03-21
I need to disable secure boot?

---

### Post by fantab on 2016-03-21
> **kacper3 said:**
> I need to disable secure boot?
Well you can try both, enabled and disabled... and like oldfred points out you may have to try a few combinations in UEFI to reach the ideal one...
Since OEMs don't adhere strictly to the UEFI Standard there are a few weird or 'differently abled' UEFIs out there...

---

### Post by kacper3 on 2016-03-31
What to do to finally be able to install Ubuntu?

---

### Post by oldfred on 2016-03-31
Can you now boot live installer?
If too many issues with nVidia try just Intel video until you get it installed and configured.

Did you review the procedures in link in my signature?
That links to many very good install examples with screen shots.

---

### Post by kacper3 on 2016-04-01
Even with Debian are almost the same errors, some errors with disabling PCI-E on BIOS. Help me please, i need Ubuntu :(

---

### Post by fantab on 2016-04-01
Can you boot Ubuntu without installing? That is, when you boot the install media you get an option to 'Try Ubuntu without installing'...?

---

### Post by oldfred on 2016-04-01
Some other threads with Asus z97
With my Asus I had to change many settings in UEFI. Use "Other" not Windows which is really the secure boot setting. Then change to UEFI only for flash drive & sysem.
Do not overclock.

 Asus Motherboard Change UEFI from Windows (secure boot only) to other OS
[http://ubuntuforums.org/showthread.php?t=2298896](http://ubuntuforums.org/showthread.php?t=2298896)
[http://ubuntuforums.org/showthread.php?t=2245911](http://ubuntuforums.org/showthread.php?t=2245911)
[http://ubuntuforums.org/showthread.php?t=2258575](http://ubuntuforums.org/showthread.php?t=2258575)
[http://ubuntuforums.org/showthread.php?t=2296538](http://ubuntuforums.org/showthread.php?t=2296538)
Minor problems with using an ASUS Z97-A Motherboard
[http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard](http://askubuntu.com/questions/503168/minor-problems-with-using-an-asus-z97-a-motherboard)
[http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu](http://askubuntu.com/questions/554735/good-z97-motherboard-for-ubuntu)

---

### Post by kacper3 on 2016-04-01
You are bot oldfred?

I cant try Ubuntu without installing but some errors displaying at video.

---

### Post by fantab on 2016-04-01
Is your Windows booting alright?

---

### Post by kacper3 on 2016-04-01
Yes, windows booting alright. I can install Windows 7, 8, 10 normally with graphical mode, but cant install Debian, Ubuntu with UEFI/graphical mode, errors on video.

---

### Post by slickymaster on 2016-04-01
*Moved to the ***Installation & Upgrades*** sub-forum*

---

### Post by fantab on 2016-04-01
A hibernating Windows won't let you install anything... Is your Windows Hibernating... if yes, [disable hibernation]("http://www.tenforums.com/tutorials/2859-hibernate-enable-disable-windows-10-a.html").

Edit: Win10 may have [InstantGo]("http://windows10-update.blogspot.in/2014/12/instantgo-power-state-in-windows-10.html") feature which is similar to hibernate.

---

### Post by Rocky_Bennett on 2016-04-01
It is important to also disable FAST START UP in the BIOS,

---

### Post by kacper3 on 2016-04-01
@Rocky_Bennett Fast Startup(Fast Boot) ? [IMG]http://i2.wp.com/pcdiy.asus.com/wp-content/uploads/2014/07/2.jpg[/IMG]

---

### Post by oldfred on 2016-04-01
Please attach screen shots not post in line. Not everyone has high speed Internet and it can slow them down a lot.
Easy to attach with paper clip icon in Forum's advanced editor (Go Advanced).

UEFI fast boot is not the same as Windows fast start up.
UEFI fast boot skips hardware check, assumes everything is the same and just boots immediately. But if anything is different you just about have no time to press a key to get into UEFI to get a normal start where it will find changes/new devices. I turned it off for install & configuration when I was rebooting a lot and needed to get into UEFI regularly. After total configuration I set cold boot to normal and warm/reboot to 3 sec delay, just to have time to press a key.
Windows fast start is always on hibernation.

But you have USB Support disabled. So nothing in USB will work?
Turn that on.

---

### Post by fantab on 2016-04-01
FastStartup is a Windows 8 feature and not a BIOS feature... not sure if its in Win10...

---

### Post by kacper3 on 2016-04-01
I disabled fast startup in Windows 10, but i have enabled fast boot on BIOS.

---

### Post by kacper3 on 2016-04-01
> **oldfred said:**
> Please attach screen shots not post in line. Not everyone has high speed Internet and it can slow them down a lot.
Easy to attach with paper clip icon in Forum's advanced editor (Go Advanced).

UEFI fast boot is not the same as Windows fast start up.
UEFI fast boot skips hardware check, assumes everything is the same and just boots immediately. But if anything is different you just about have no time to press a key to get into UEFI to get a normal start where it will find changes/new devices. I turned it off for install & configuration when I was rebooting a lot and needed to get into UEFI regularly. After total configuration I set cold boot to normal and warm/reboot to 3 sec delay, just to have time to press a key.
Windows fast start is always on hibernation.

But you have USB Support disabled. So nothing in USB will work?
Turn that on.

I set these settings in the BIOS such as those on the 5 pictures, no effects look video:
[https://www.youtube.com/watch?v=Nku5c2r_njM](https://www.youtube.com/watch?v=Nku5c2r_njM)

---

### Post by oldfred on 2016-04-01
Just about unwatchable.

But did you add nomodeset? Or try Intel video connection until you get it installed?
 # Usually nVidia or AMD work with this:
nomodeset 


 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by kacper3 on 2016-04-01
i used integrated graphic card intel and nomodeset, some errors.

---

### Post by oldfred on 2016-04-01
With Intel you may need different boot parameters.

       # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size 
      
 Skylake needs this boot parameter:  i915.preliminary_hw_support=1
[http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support](http://www.phoronix.com/scan.php?page=news_item&px=Intel-SKL-Prelim-Support) 
           
 Best Ubuntu version for new Z170 motherboards /w Intel video? Oct 2015
[http://ubuntuforums.org/showthread.php?t=2292521](http://ubuntuforums.org/showthread.php?t=2292521)
[http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work](http://askubuntu.com/questions/698168/cant-get-intel-hd-graphics-530-skylake-i7-6700-to-work)

Not sure what your issue is. Just about everyone that posted with issues was able to boot but had different types of issues.
Did you review all the posted links to see if someone posted more details?

Do you have overclocking set. That often causes issues.

---

### Post by kacper3 on 2016-04-01
Yes, i have overclocked I7 4790K propably from 4.0 to 4.4GHz

---

### Post by kacper3 on 2016-04-01
None of these parameters it did not work, they are always the same errors.

---

### Post by oldfred on 2016-04-01
Take the overclock off at least until installed.
Different systems work differently.
And Windows may not report all the errors where Linux often does. Or you may think Windows is working, but is it

---

### Post by kacper3 on 2016-04-01
How to disable overclock?

---

### Post by oldfred on 2016-04-01
Go back into UEFI, reset to defaults, and then change again to settings as posted above for UEFI, etc.
Best to also check that you have latest UEFI from Asus. Installing new UEFI version always resets to defaults, so you have to keep track.
That is why I have screen shots and also written down all the changes I make.

---

### Post by kacper3 on 2016-04-02
And if I can return the overclock? I not configuring this computer, so i dont know how to overclock again.

---

### Post by oldfred on 2016-04-02
I do not overclock, so do not know details, but there are lots of details.
Usually it is bumping various timings up a little at a time until system becomes unstable and then back off. 
But I never want a system close to the edge, nor running hot potentially stressing components.

Not sure I understand that you say you are not configuring system. Installing another operating system is a major reconfiguration.

---

### Post by kacper3 on 2016-04-03
still same errors :(((

---

### Post by kacper3 on 2016-04-03
SOLUTION:
[IMG]http://i.imgur.com/PRAsjBf.jpg[/IMG]

---

### Post by oldfred on 2016-04-03
Did you change to SATA0?
Best to always put drives in order and start with first SATA port.

---

