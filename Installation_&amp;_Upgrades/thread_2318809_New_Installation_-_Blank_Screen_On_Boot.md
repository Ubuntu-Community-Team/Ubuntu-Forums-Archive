---
title: "New Installation - Blank Screen On Boot"
date: 2016-03-29
forum: Installation &amp; Upgrades
---

### Post by joe203 on 2016-03-29
I am completely new to Ubuntu, but wanted to try it. 

Installed 14.04 from a CD onto a usb 8gb stick so I could dual boot either Win XP or Ubuntu.

During installation I noticed a couple of things, but don't know if of any significance:
1) Said "No swap partition", but I continued on
2) Near the end, I noticed messages "completely removing Ubiquity ...." and "completely removing apt-clone..."
    There may have been other messages, but I did not stay & watch -- needed to do something else.

Now when I try to boot, I get the Grub menu just fine. XP will still boot fine, BUT:
1) Ubuntu does not boot - goes to blank screen - nothing else!
2) Advanced Ubuntu Recovery will boot, but screen is small & has vertical lines in background. If I select
    Displays, it says 'Built-in display".

I followed the 'sticky' here & went thru many of the steps editing linux /boot/.... in all the various ways
mentioned. Last attempt was with .... video=VGA:1024x768-16@60 However, nothing has helped.
GRUB> vbeinfo shows various entries including 1024x768 both 16 & 32 bit.

The hardware is a Dell Inspirion 1100 which has an Intel 82845G graphics controller. When running XP
the screen resolution is 1024x768x32. Usb stick shows 3.4Gb used & 4.4Gb free.

At this point, I have tried everything I can find to do. Any help will be much appreciated.
TIA, joe

---

### Post by oldfred on 2016-03-29
My old laptop with Intel chip did not need any boot parameters.
Have you removed quiet splash which may show something, or tried second entry for recovery mode?
Also how much RAM?

What flavor/version of Ubuntu?
Older systems often cannot run Ubuntu, and need Lubuntu or Xubuntu. My old laptop was so slow with Unity/Ubuntu that I installed fallback/flashback/gnome panel which worked well and is another lighter weight gui choice.
 # Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size
# Other settings in addition to above for other hardware related issues
acpi=0
acpi_osi=linux
acpi_backlight=vendor
noalpic

---

### Post by grahammechanical on 2016-03-29
Is Ubuntu installed to the hard disk? I am confused by this statement

> Installed 14.04 from a CD onto a usb 8gb stick so I could dual boot either Win XP or Ubuntu.

If you used a different machine to install Ubuntu to a USB memory stick and you ticked the box to install third party software, then you also installed a proprietary video driver that was appropriate for the machine you were installing Ubuntu from but not necessarily appropriate for running Ubuntu on the USB stick on any other machine.

If Advanced options> recovery mode> recovery menu> Resume gets you to a working desktop but the normal boot from the Grub menu does not, then I suspect a video driver conflict. Go to System Settings>Software & Updates>Additional Drivers tab and change video drivers.

By the way,

> 1) Said "No swap partition", but I continued on

I do not think that we will get a swap partition if Ubuntu is installed onto a USB memory stick.

> 2) Near the end, I noticed messages "completely removing Ubiquity ...." and "completely removing apt-clone..."

This is normal activity for the installation process. Ubiquity is the installer program itself and it runs in memory during the installation process as does a lot of other stuff. All of which have to be removed from memory as a polite way of bringing the installation process to an end and allowing the live session to continue running.

Regards.

---

### Post by joe203 on 2016-03-29
Thanks for the replies. The machine only has 512Mb of RAM, but I would upgrade to 1Gb if I can get the other kinks worked out.

In the beginning: I downloaded a Ubuntu 14.04LTS .iso file using a Win 10 machine. From there, I burned a DVD (not a CD).

This DVD is bootable & will run Ubuntu, albeit slowly AND the screen is full, as it should be. So, I believe the DVD is good.

When the DVD boots, I get a window giving a choice to Run from DVD OR Install. Using Install was how I created the usb stick.

I did check for additional video drivers, but it said there were 'No additional drivers available'.

Any suggestions? Should I just format the usb stick again & rerun Install?

---

### Post by oldfred on 2016-03-29
Pretty sure 512MB is not enough for Ubuntu and is close to bottom for any lightweight GUI.
[https://wiki.ubuntu.com/Lubuntu](https://wiki.ubuntu.com/Lubuntu)

 [http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by grahammechanical on 2016-03-29
You installed Ubuntu on a USB stick from a machine running Windows 10. If you ticked the box "Install third party software" then a proprietary video driver for the video adapter in that machine would have been installed. This is how things work.

When we go to Additional Drivers we need to be connected to the internet and allow time for the utility to work. That video driver would not be suitable for the video adapter in the machine with XP on it. Even if it is from the same manufacturer as the video adapter in the Windows 10 machine. Newer proprietary video drivers drop support for older video adapters. And if that machine only has 512 MB RAM then it is certainly using an obsolete video adapter. No shame in that. My video adapter is obsolete according to Nvidia.

When we use recovery mode Resume we use a fallback open source video driver and not the installed proprietary video driver. That is how we can sometimes get to a working desktop using recovery mode resume when the normal method of loading the OS fails.

If we install & do not tick the box "Install third party software" we get an installation that is using the open source video driver. The Ubuntu live session uses the open source video driver.

It is acceptable to install Ubuntu on a USB stick and then run it on different machines but not with a proprietary video driver.

Regards.

---

### Post by joe203 on 2016-03-29
grahammechanical - obviously I did not clearly explain. I used the Win 10 machine to burn the DVD - not to create the usb stick.

The usb stick was created on the target machine after having booted the target machine from the DVD.

Also, the DVD runs Ubuntu just fine, albeit slowly which means the DVD and the target machine are using the correct video driver.

Somehow, when I installed Ubuntu on the usb stick - using the target machine - the usb stick did not get the required video driver.

However, you gave me a very excellent clue. I did NOT check the "Install 3rd party software" box. So, if this caused the usb stick to get the open source driver instead of the correct Intel driver, that almost certainly explains the situation I have.

Is there a way I can copy the driver from the target machine to the usb stick? I'm sure I can find the driver file name within the XP environment, but I have no idea where to put it on the usb stick. As I said above, ... Additional Drivers did NOT find anything even though the target machine was connected to the internet.

best regards

---

