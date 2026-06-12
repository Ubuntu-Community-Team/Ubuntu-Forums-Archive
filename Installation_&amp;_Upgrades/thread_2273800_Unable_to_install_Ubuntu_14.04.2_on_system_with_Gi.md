---
title: "Unable to install Ubuntu 14.04.2 on system with Gigabyte Z97x motherboard"
date: 2015-04-15
forum: Installation &amp; Upgrades
---

### Post by jd.russell2006 on 2015-04-15
Hi all, I am new to the forums and was wondering if anyone could help me. I have used linux Ubuntu before several years ago I believe version 12. something. So I am somewhat familiar with linux basics and installation, however I can not seem to get to the installer for the latest version of ubuntu. I'd really like to install a linux distro on my computer for cross platform software and game development (I'm currently working with an indie game studios kickstarter group). As mentioned I have some but very limited knowledge when it comes to linux distros and I am only really familiar with ubuntu (although this time I did try installing linux mint as well - that also fails).

The problem is that when I try to boot into the installer it either hangs on a black screen (in UEFI mode) or goes to a blank (sometimes a few lines of text) grey screen in the legacy mode. The installer I am using is a 30 gigabyte flash drive formatted and created with the universal usb installer program (excessive but I don't have anything else not in use atm). I have followed the basic instructions I found from the ubuntu wiki (i think) about installing on a UEFI machine - i.e. I have disabled fast boot and secure boot. This still resulted in the same blank screen behavior.

I am attempting to do this install alongside a Windows 8.1 partition (like I said before interested in cross platform development) that I would like to keep. I just recently built my first desktop (in a while) and some of the rough system specs are as follows:

Motherboard: Gigabyte GA-Z97x gaming 3 motherboard.
Processor: Intel i5-4690k
GPU: Geforce 750ti Windforce Black Edition (also from Gigabyte)
Memory: G-Skill 8 GB

The motherboard came with the DualBios UEFI setup. The bios version was F3 I upgraded to F5 (the latest).

Any help would be greatly appreciated as I would really really like to be able to do some cross platform development sometime in the near future.

---

### Post by Vladlenin5000 on 2015-04-15
Hi and welcome.

This is your "problem", not UEFI:
```
GPU: Geforce 750ti Windforce Black Edition (also from Gigabyte)
```

It's one of the most "touchy" nvidia chips when it comes to drivers and new enough to not be supported by the default open source *nouveau* driver. So, you need to make a couple of workarounds:

1) Use *nomodeset* to install (generic video)
2) For 15.04 (recommended) -> The correct proprietary driver - 346 - is offered in "Additional Drivers"; for 14.04 you need to add the X-edgers PPA.

---

### Post by jd.russell2006 on 2015-04-15
Yes I recall seeing something about nomodeset in a couple of the threads when researching gigabyte hardware and the installation. This explains why linux mint crashed when it got to the part about verifying the graphics drivers... makes sense now.

How do I go about setting this? Exactly what is it and what does it do for me just out of curiosity?

Also, should I use the mentioned 15.04 version instead? Isn't that the latest non-long term version?

Also thanks for the help and the quick reply you were much more helpful than Gigabyte tech support lol.

---

### Post by Vladlenin5000 on 2015-04-15
Yes, 15.04 is the soon-to-be released new non-LTS. For now the only advantage I foresee in your case is the possibility of using the drivers that work right out of the Ubuntu's tool for proprietary drivers. The driver offered in 14.04 is stuck at the old 331 and that one doesn't work for your card*.

Now... [I]nomodeset 
[/I]You can press SHIFT in the first screen when booting from the installation media. That will take you to the "Try Ubuntu" (etc.) menu. There - if I'm remembering it correctly - you press F6 for the additional options/parameters and one of them is *nomodeset*.

The purpose of *nomodeset *has been discussed several times but I'm yet to find a better answer than the one NikTh usually gives at Ask Ubuntu:
> The newest kernels have moved the video mode setting into   the kernel. So all the programming of the hardware specific clock   rates and registers on the video card happen in the kernel rather than   in the X driver when the X server starts.. This makes it possible to   have high resolution nice looking splash (boot) screens and flicker   free transitions from boot splash to login screen. Unfortunately, on   some cards this doesnt work properly and you end up with a black   screen. Adding the nomodeset parameter instructs the kernel to not   load video drivers and use BIOS modes instead until X is loaded.



* Don't even try. It won't work and you'll have to edit Grub by adding *nomodeset* again, purge all the installed nvidia drivers and finally install the one that works via PPA or other methods.

---

### Post by jd.russell2006 on 2015-04-15
Ok Thanks so much for clearing that up! You've been very helpful! Is there a way to give rep on this site? Cause I'd definitely give you some. :)

I found the 15.04 Beta 2 i386 desktop iso on the ubuntu site. I am assuming this is the one I want for an Intel system. So I will be making a new boot loader and attempting to install this shortly. I'll report back what happens! :)

---

### Post by grahammechanical on 2015-04-15
> I found the 15.04 Beta 2 i386 desktop iso on the ubuntu site. I am assuming this is the one I want for an Intel system.

No. You need the amd64 ISO image and not simply because your Intel CPU is 64 bit but because of what it says here

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

> 
[LIST]
[*]Use a 64bit disk of Ubuntu. ([Ubuntu32bit cannot be easily installed in UEFI mode]("https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1025555").   This is a problem if 32-bit UEFI is the only way your computer can  boot, e.g. if you have a modern Intel Atom based laptop.  In this case,  you will need [a complicated work-around]("https://github.com/lopaka/instructions/blob/master/ubuntu-14.10-install-asus-x205ta.md").) 

[/LIST]


The i386 ISO will work on any 32 bit or 64 bit CPU made by Intel and AMD. And the amd64 ISO will work on any 64 bit CPU made by AMD and Intel. But when it comes to Windows 8 and UEFI on 64 bit CPUs it must be a 64 bit ISO image.

Regards.

---

### Post by Vladlenin5000 on 2015-04-15
> **jd.russell2006 said:**
> I found the 15.04 Beta 2 i386 desktop iso on the ubuntu site. I am assuming this is the one I want for an Intel system.

Actually no... i386 is for 32-bit systems (regardless of the CPU vendor); **amd64** is for 64-bit systems like yours (regardless of the CPU vendor). A 32-bit OS can be installed in yours and it'll work but it won't take advantage of all the RAM you have, among other details.

Currently I recommend 32-bit only for systems that are really 32-bit. There was some controversy about using 64-bit with 2GB RAM or less, ie, some users suggested that due to the memory "shortage" it would make sense to use a 32-bit OS even with a 64-bit CPU; this discussion, however, has nothing to do with your system.


For the rest, you're welcome (and no need for anything else). When you're happy with the solution you can use the thread tools to mark this one as solved so future forum users may benefit. 

Happy Ubuntuing... :p

---

### Post by jd.russell2006 on 2015-04-15
Ok, well good thing I didn't do it yet lol. I downloaded the amd64 version instead. I'll attempt to install it momentarily.

---

### Post by jd.russell2006 on 2015-04-15
Wow! That was alot easier and faster than expected. It just worked... didn't even have to set nomodeset. 15.04 looks great too. I'm so happy been scratching my head for a couple days now trying to get a version that would install. I verified that windows 8.1 was working correctly the grub boot menu was displayed properly and I am currently in ubuntu typing this response! Marking this thread as solved.

---

### Post by jd.russell2006 on 2015-04-15
*Accidental double*

---

### Post by oldfred on 2015-04-15
Did you have any issues with USB ports or the Gigabyte IOMMU issue.
Every Gigabyte board so far has needed IOMMU setting changed in UEFI. 
Or did you change that before you started?

---

### Post by jd.russell2006 on 2015-04-16
I did not have to change anything related to IOMMU as far as I'm aware. I did change secure boot fast boot and the boot order to load UEFI first. It turns out for starters my Windows 8.1 was installed in legacy bios mode somehow - I don't know if that makes a difference. So I had to install ubuntu in that mode as well.

So I am back with a new related problem... the graphics card driver from Nvidia when I go to Additional Drivers in the software and updates and change it to the latest (346.59) seems to install correctly however on reboot I was getting an empty monitor. And I have a Tv / Monitor all in one so it wasn't even connecting the monitor... (the monitor's default unconnected screen was active). Does this mean I can't use the driver? Is there a fix for this or have I missed a step in installing this somewhere? The only way I could boot was to do a recovery mode boot and then continue to normal boot. I suppose it complicates matters that I did other updates before restarting from the Software Updater app. So I'm not sure if that caused it or if the driver change caused it. When I did get it to boot the "System Program Error" message popped up and I did the terminal command to remove old error reports (because it continued to show repeatedly).

Any Ideas on how to fix this issue?

---

### Post by jd.russell2006 on 2015-04-16
So, I reapplied the driver from the Additional Drivers tab to see if that was causing the issue and restarted. It does the same thing, however interestingly enough I can still boot in recovery mode. Also the screen before the monitor turns off says something to the effect of ACPI PCC Probe failed loading version 219. What does this mean? Should I be worried about this and is it related to the blank monitor? And if so how do I go about fixing this?

---

### Post by oldfred on 2015-04-16
Before you added the 346.xx nVidia driver, did you have a different driver. With nVidia, you must totally purge all old versions before installing any new version or else you get conflicts. 

If recovery mode works, then that is using nomodeset which is more to use open source driver. Or is then nVidia driver not actually working?

---

### Post by jd.russell2006 on 2015-04-16
So I did not at first do the purge. The first time I tried it I was just on the nouveau driver. If I set it back to that It works fine. If I set it to any of the other Nvidia options (the proprietary drivers) it turns off the monitor when trying to boot the OS. I looked at the Nvidia site it says the 750ti is a supported card for this driver. So the second time I tried changing it I did the purge still no change the blank monitor again. So I tried downloading the actual installer from the nvidia site. For future users with my kind of set up don't do this... I had to reinstall the entire OS after installing the driver manually. So now I'm at a loss as to what else to try... It would be strange if Nvidia says it works for my card and yet I can't boot with it correctly.

---

### Post by oldfred on 2015-04-16
With the very newest nVidia driver and new cards, you may need a newer kernel and support software and default in Ubuntu. I thought perhaps the 14.04.2 was new enough?

Many have posted that with older versions of Ubuntu, they had to use ppa to update just about everything to make it work.

I would just try 15.04 as then you have all the newest from Ubuntu.

 Maxwell 750 - kernel 3.15 required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)
[http://ubuntuforums.org/showthread.php?t=2261714](http://ubuntuforums.org/showthread.php?t=2261714)
[http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1](http://www.phoronix.com/scan.php?page=article&item=evga_geforce_gtx750&num=1)
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell_750linux&num=1)

      
 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)
Install with Asrock Z97 & nVidia 970
[http://ubuntuforums.org/showthread.php?t=2257406](http://ubuntuforums.org/showthread.php?t=2257406)
[http://ubuntuforums.org/showthread.php?t=2259210](http://ubuntuforums.org/showthread.php?t=2259210)

---

### Post by jd.russell2006 on 2015-04-16
Oh I am using 15.04... sorry I guess I didn't specify that in the response or you missed it. Yes 15.04 is the version I'm using. I think I need to enable the nomodeset option... but because I'm so new to this I don't really know where or how to do that. Could you explain in easy to understand steps as to how to enable that boot option? Also is this something I should have set when installing only or something I need to enable with the boot in general?

---

### Post by jd.russell2006 on 2015-04-16
Ok, so I figured out how to set nomodeset option. I had to hit e in the grub boot menu and type "nomodeset" on the end of the line that starts with "linux boot/vmlinuz". This is apparently where you specify the boot options, unless I'm wrong. So I did that and it boots correctly with the new driver installed (set the option for the latest nvidia driver 346.59 under the Additional Drivers tab in Software and Updates). However, when booting it shows what I am assuming is a boot loading screen before actually booting with a couple of warning/error messages. The first is still the "ACPI PROBE failed" message at the top and the second is something like "Could not turn on power on the i915" What do these mean and should I be concerned about them? If so how do I fix?

---

### Post by oldfred on 2015-04-16
Is this a dual switchable video system, or do you just have Intel video & added a nVidia card?

If not using i915 I do not think it is an issue. 
But I have an older nVidia card an Intel video and get no errors as I am not using the Intel video.

Adding nomodeset, I thought set nouveau video mode. Adding it as a boot parameter on grub menu when booting is for occasional use or testing to see what works. If a boot parameter is requried all the time, we can edit /etc/default/grub to add it.

Did you check IOMMU settings and the posts where other users resolved issues by changing it in UEFI and adding boot parameter for it?

 turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to Gigabyte boards.
Gigabyte Z97-HD3 Intel Z97 Motherboard
[http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1](http://www.phoronix.com/scan.php?page=article&item=gigabyte_z97_hd3&num=1)
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)


> Without this IOMMU fix, no networking works.  No wireless cards (pci-e  or pci) and no wired cards (built in or pci) work.  This only applied to  64bit, 32bit worked fine with IOMMU disabled.                 


[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

You can also test this on grub line like nomodeset - iommu=soft. before changing permanently.
GRUB_CMDLINE_LINUX="iommu=soft"

---

### Post by jd.russell2006 on 2015-04-16
So IOMMU is not an option in my UEFI bios... I checked that before I installed because I thought it might be a problem with the UEFI setup. I didn't see it. Is it called something else?

I'm assuming i915 is the intel built in graphics with the i5 processor I have then right? If you mean that I can switch between the Intel graphics and Nvidia graphics on windows that would be yes. However I don't use the intel graphics so it's not a problem for me really.

So with the nomodeset I'm getting the original nouveau driver? It says its still on the Nvidia driver in the Software and Updates manager... is there another way to check what Driver is actually being used for the GPU? Sorry I'm very new to this.

---

### Post by jd.russell2006 on 2015-04-16
Also I'm not sure but I do have built in PCI on this board and the networking is working fine in ubuntu (im on it right now).

---

### Post by jd.russell2006 on 2015-04-16
Ok so I found out how to check the driver actually in use by the system with "sudo lshw -c video" command.

I found this Ask Ubuntu link:
[http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system](http://askubuntu.com/questions/23238/how-can-i-find-what-video-driver-is-in-use-on-my-system)

Which says to look for the line marked "configuration:"

Min says this:
"configuration: driver=nvidia latency=0"

Is this correct and does it mean that it is actually running the installed nvidia driver?

---

### Post by oldfred on 2015-04-16
It is running the nVidia driver.

Also good to see what nVidia is integrated into what kernels:
 #Resolution:
xwininfo -root
#What is installed
dkms status

If installing from terminal you can see what is in repository. But I normally have just used System Settings.

 # list drivers available, same list as system settings,  software updates,  additional drivers or last tab
ubuntu-drivers devices
# or
ubuntu-drivers devices | grep recommended

---

### Post by jd.russell2006 on 2015-04-16
so this is the result of xwininfo -root command:

Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1920
  Height: 1080
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1920x1080+0+0

this is the result of dkms status:

bbswitch, 0.7, 3.19.0-10-generic, x86_64: installed
bbswitch, 0.7, 3.19.0-14-generic, x86_64: installed
nvidia-346, 346.59, 3.19.0-14-generic, x86_64: installed

and this is result of ubuntu-drivers devices | grep recommended

driver   : nvidia-346 - distro non-free recommended


So it looks to be everything is in order, from what I can tell. Did I miss anything i should worry about here?

And so just to clarify I don't need to really worry about the ACPI PCC Probe and Could not load power for i915 messages?

Also if this setup works should I just go ahead and modify the file you mentioned to make it load in nomodeset everytime?

---

### Post by oldfred on 2015-04-16
I do not know enough as I do not have nVidia 750. I was thinking of getting that card for its low power use, but my old nVidia card has worked well enough for now.

Another link which says you have to leap though some hoops as you have done.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.1-GTX-750-Nouveau](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.1-GTX-750-Nouveau)

---

### Post by jd.russell2006 on 2015-04-16
Ok so I solved the problem with i915 message by simply turning off the intel integrated graphics in the bios options. I don't need this anyways as I'm not using the integrated graphics in linux or windows. The ACPI PCC message still remains and it seems to slow down the boot a bit too... not sure how to fix that or if it needs to be fixed. I edited the grub file and updated grub so it starts with nomodeset permanently now and double checked that the nvidia driver is being loaded still. Everything appears to be working now except for the error message mentioned before.

Next Question is what other drivers do i need to install? I have a Bigfoot Networks killer card in this system is there a driver for that in linux?

Also I don't appear to have any sound... when I go to websites but i did the system test app and when i plugged in headphones they worked for the beep test... Is there a setting I need to change for it to use my monitor speakers?

Also one more thing, how do I check and make sure all the fans are running correctly? I can see the ones on the sides of the case spinning but im more interested in seeing if the cpu fan is on (im paranoid about overheating after what happened with my last computer). Is there an app to check this?

---

### Post by jd.russell2006 on 2015-04-16
I didn't have adobe flash plugin installed for linux... now I feel stupid. Ok so sound problem fixed for the most part... interestingly enough I keep getting an Program Error has been detected message when I do things with sound attached (sometimes). Not sure what this means. I reported the error.

---

### Post by jd.russell2006 on 2015-04-16
The error in the bug message screen actually says Sorry, Ubuntu 15.04 has experienced an internal error.

Below the package given is aptdaemon, this is the app manager thing isn't it? Should I be worried about this?

---

### Post by oldfred on 2015-04-16
Well 15.04 is still beta, so you are a tester. 
Some errors are to be expected, hopefully none that prevent booting at all.

---

