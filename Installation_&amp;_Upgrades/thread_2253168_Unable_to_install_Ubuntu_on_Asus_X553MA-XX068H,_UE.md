---
title: "Unable to install Ubuntu on Asus X553MA-XX068H, UEFI"
date: 2014-11-17
forum: Installation &amp; Upgrades
---

### Post by Michael_Coracin on 2014-11-17
Hello,

I just bought an Asus laptop (model X553MA-XX068H), with Windows 8.1 preinstalled (UEFI mode).
I'm trying to install Ubuntu 14.10, in dual boot, but didn't succeed so far. The installation process systematically hangs/freezes on the first purple screen, I see some activity during few seconds, and then no more activity, and I have to force shut down of the PC.

I've tried an installation from DVD or from USB, and same behaviour in both cases.

At boot time, I can see the GRUB menu (the black and white one), and I've tried to do "Install Ubuntu" or "Try Ubuntu without installing", also same behaviour...

I've tried to disable the Secure Boot in BIOS, then I also tried to Enable the CSM mode... but not better...

Does someone have any idea of what could be the problem?
I don't get any message or anything, except a frozen screen, and I'm running out of ideas... :(

Thanks in advance.
Regards,
Michael

---

### Post by secretservgy on 2014-11-17
Did your checksum data match on the downloaded ISO as well as what was burned/copied?

---

### Post by fantab on 2014-11-18
Windows 8 and greater has 'FastStartup" feature, which keeps the Windows in 'Hibernation' even when you think you have shutdown the PC. [Disable FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").
Also 'Fastboot' needs to be disabled... 

You must also read through : [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
I also suggest that you feed your Laptop model in the forum Search box and search for any known issues...

---

### Post by Michael_Coracin on 2014-11-18
Hello,

Thanks for your answers.

1) I've tried several ISO versions, for Ubuntu 14.04 and 14.10, and get same issue in every cases.

2) The Windows FastStartup feature is disabled on my laptop. Fastboot in BIOS is also disabled.

Any idea?

Is there a way to have logs from Ubuntu installation process, to have more info about what is happening in background the purple screen?

Regards,
Michael

---

### Post by Michael_Coracin on 2014-11-18
Hello,

I could finally install the version 14.04 64bits. Installation seemed to be ok, I just had to plug the network to have it starting (even though, for 14.10 it does not help). I could complete the installation process.

But still, it is not completely working.

1) shutdown operation is freezing (I've seen several threads speaking about this, so I'll figure it out, if I can login again...)
2) I'm not able to restart ubuntu anymore, it hangs at startup with a message like:
BUG: soft lockup - CPU#1 stuck for 22s!
BUG: soft lockup - CPU#2 stuck for 22s!

:(

Michael

---

### Post by oldfred on 2014-11-19
UEFI often is similar across models. Not sure then if any of these threads will help or not.
Did you install in UEFI mode?

 Asus ROG G75VW  with Windows 7 in UEFI boot mode.
[http://ubuntuforums.org/showthread.php?t=2251167](http://ubuntuforums.org/showthread.php?t=2251167)
Asus ASUS D550MA-DS01 - 14.04 only Ubuntu
[http://ubuntuforums.org/showthread.php?t=2223928](http://ubuntuforums.org/showthread.php?t=2223928)
 Installation of Ubuntu 14.04 on ASUS N550JV (a Status Report)
[http://ubuntuforums.org/showthread.php?t=2208852](http://ubuntuforums.org/showthread.php?t=2208852)
[http://ubuntuforums.org/showthread.php?t=2184383](http://ubuntuforums.org/showthread.php?t=2184383)
ASUS Zenbook UX301LAA ultrabook under Linux  - reboot, power issues
[http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ](http://www.phoronix.com/scan.php?page=news_item&px=MTcwOTQ)
 ASUS Zenbook Prime UX32VD
[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
[http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_ux32ultrabook_linux&num=1)
[https://help.ubuntu.com/community/AsusZenbookPrime](https://help.ubuntu.com/community/AsusZenbookPrime)
 Asus X401U notebook
[http://ubuntuforums.org/showthread.php?t=2169462](http://ubuntuforums.org/showthread.php?t=2169462)

---

### Post by Michael_Coracin on 2014-11-21
Hello,

Yes, I've installed in UEFI mode.

What I can see now is that if I try to boot using the regular "Ubuntu" user choice, it won't boot, with error described above.

But if I choosse advanced option and start in "recovery mode", it will boot. But video resolution is stuck to 800x600.

Could it be related to a bad support of my video card? (integrated intel HD graphics)

I'll go through all the links given above, thanks!

Michael

---

### Post by Michael_Coracin on 2014-11-21
Some update:

From Grub boot menu I can choose between 2 versions of kernel: 3.13.0-39-generic and 3.13.0-24-generic.

If I choose version 3.13.0-24-generic, it will boot fine, and I'll get Ubuntu Desktop in full resolution (at least most of the time, I've seen some hangs, but not frequently).
(and I still have the shutdown/restart freeze issue)

But when I choose version 3.13.0-39-generic, it won't boot, as described above. It can boot in 3.13.0-39-generic (recovery mode), but I'll have reduced video resolution (800x600).

I've installed the updated intel graphics driver, through the installer:
[https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7](https://01.org/linuxgraphics/downloads/2014/intelr-graphics-installer-linux-1.0.7)

> sudo lshw -c video

  *-display               
       description: VGA compatible controller
       product: ValleyView Gen7
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0e
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:106 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)

Any idea what could be the problem with kernel v39?

Thanks,
Michael

---

### Post by oldfred on 2014-11-21
I would test several Intel boot parameters to see if they help. If one works then you can make it standard in grub.

You add boot parameters just like adding nomodeset, but nomodeset usually does not work with Intel.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

Others with Intel have used the i915 setting or the specific X by Y as shown in ubfan1's post. Just be sure to use your size not example he shows.

---

### Post by Michael_Coracin on 2014-11-22
Thank you oldfred, but none of the listed grub options seem to fix the issue. :(

So to recap, I have 3 issues with the current installation:

1) kernel 3.13.0-39-generic won't boot, it hangs on log:
Adding 8000508k swap on /dev/sda9.  Priority:-1 extents:1 across:8000508k FS

2) kernel 3.13.0-24-generic will boot, but have 2 issues:
2.1) Touchpad is only seen as a "PS/2 Logitech Wheel Mouse". I've seen several threads on this topic, but for now couldn't fix it. For now, it's minor, I can disable it.
2.2) I can't shutdown or reboot, it always hang on "Will Now Halt" message. For now I don't have any solution for this, it is quite annoying...

Concerning problem 1), if I check syslog file on kernel 3.13.0-24-generic boot, around the message on which it hangs for 3.13.0-39-generic, I see:

Nov 22 22:20:18 mick-X553MA kernel: [   12.847669] Adding 8000508k swap on /dev/sda9.  Priority:-1 extents:1 across:8000508k FS
Nov 22 22:20:18 mick-X553MA kernel: [   12.904423] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
Nov 22 22:20:18 mick-X553MA kernel: [   13.438729] lp: driver loaded but no devices found
Nov 22 22:20:18 mick-X553MA kernel: [   13.465883] ppdev: user-space parallel port driver
Nov 22 22:20:18 mick-X553MA kernel: [   13.538516] dw_dmac INTL9C60:00: DesignWare DMA Controller, 8 channels
Nov 22 22:20:18 mick-X553MA kernel: [   13.660514] Bluetooth: Core ver 2.17
Nov 22 22:20:18 mick-X553MA kernel: [   13.660560] NET: Registered protocol family 31
Nov 22 22:20:18 mick-X553MA kernel: [   13.660563] Bluetooth: HCI device and connection manager initialized
Nov 22 22:20:18 mick-X553MA kernel: [   13.660578] Bluetooth: HCI socket layer initialized
Nov 22 22:20:18 mick-X553MA kernel: [   13.660582] Bluetooth: L2CAP socket layer initialized
Nov 22 22:20:18 mick-X553MA kernel: [   13.660589] Bluetooth: SCO socket layer initialized

Could it be an issue with ethernet driver or bluetooth driver occuring with latest kernel?
How could I disable those drivers loading in order to check if it will progress a little more in boot process?

Thanks and regards,
Michael

---

### Post by oldfred on 2014-11-22
Post last 10 or 15 lines from kernel -39.

this is now older?
 Asus i3 with Intel graphics, boot options
acpi_osi=Linux
video=1280x1024-24@75 or whatever native resolution is

[http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1](http://www.phoronix.com/scan.php?page=article&item=asus_zenbook_ux301la&num=1)
But then he started getting thermal issues
[http://www.phoronix.com/forums/showthread.php?101418-Thermal-Issues-Appear-To-Cause-My-ASUS-Zenbook-Linux-Woes&highlight=zenbook](http://www.phoronix.com/forums/showthread.php?101418-Thermal-Issues-Appear-To-Cause-My-ASUS-Zenbook-Linux-Woes&highlight=zenbook)

---

### Post by Michael_Coracin on 2014-11-23
Here are the logs I get with kernel 39:
[https://mega.co.nz/#!g0tHmJLa!muWkEskt0IK2kyb2gDWL-gzTXeYBU9hRGlOQjS-MmAQ](https://mega.co.nz/#!g0tHmJLa!muWkEskt0IK2kyb2gDWL-gzTXeYBU9hRGlOQjS-MmAQ)

I can't find the logs in the syslog file.
Tell me if you prefer another way for posting it here. :)

Thanks!

---

### Post by Michael_Coracin on 2014-11-23
Better like this maybe:
[IMG]https://www.dropbox.com/s/7sv5mwndighvl9s/IMG_20141123_114020.jpg?dl=0[/IMG]

---

### Post by oldfred on 2014-11-23
You originally mentioned 14.10, but then  kernel, 3.13 which is 14.04.

Then you installed the very newest Intel drivers directly from Intel. Often that requires you to have the very newest kernel and other support software so all the new bits work together.

 All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)
New kernels ppa
[https://wiki.ubuntu.com/Kernel/MainlineBuilds](https://wiki.ubuntu.com/Kernel/MainlineBuilds)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D](http://kernel.ubuntu.com/~kernel-ppa/mainline/?C=N;O=D)
Ubuntu Kernel Mainline PPA
[http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1](http://www.phoronix.com/scan.php?page=article&item=amd_cat144_hd56&num=1)
[https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed](https://launchpad.net/~kernel-ppa/+archive/ubuntu/pre-proposed)

---

### Post by Michael_Coracin on 2014-11-24
Hello oldfred,

Yes I originally mentionned 14.10, but on comment #5 I said that finally I was able to install 14.04, but not 14.10. Which is fine for me, I'm ok to have 14.04.

Then, with 14.04, I've 2 kernels installed: 24 and 39.
By default grub was pointing to version 39, on which boot is not successful, as described in previous posts.
It boots ok on kernel 24 though, with various issues with touchpad and shutdown.

Sorry if I wasn't clear...

What do you suggest for the kernel version issue on 14.04?
Is there a version more recent than 39 that I could try?
Or should I try to recompile version 39 with specific options?

Thanks,
Michael

---

### Post by oldfred on 2014-11-24
I have never recompiled nor installed newer kernels.

Some that like to test or experiment will install the newest released kernel or even Linus' beta and compile that to test. The latest kernels are in the ppa and can relatively easily be downloaded, but often you also need all the other support files and are into all the issues that a developer has in getting all the bits to work together.

Some with very new hardware do need the latest release to get new features to work.

---

### Post by Michael_Coracin on 2014-11-25
Hello,

Finally, I've returned this laptop, I was not really happy with it, even beside issues with Ubuntu install.

I'll go for a more powerful laptop (for family Windows usage), and also try to get info about Ubuntu support before choosing the model (for my embedded dev needs).

Thanks a lot for your support, I hope that it will go smoother with next machine. :)

Regards,
Michael

---

### Post by janne-m-heikkinen on 2014-11-29
> **Michael_Coracin said:**
> Hello,

I could finally install the version 14.04 64bits. Installation seemed to be ok, I just had to plug the network to have it starting (even though, for 14.10 it does not help). I could complete the installation process.

But still, it is not completely working.

1) shutdown operation is freezing (I've seen several threads speaking about this, so I'll figure it out, if I can login again...)
2) I'm not able to restart ubuntu anymore, it hangs at startup with a message like:
BUG: soft lockup - CPU#1 stuck for 22s!
BUG: soft lockup - CPU#2 stuck for 22s!

:(

Michael

I found that solution for this was to change "OS Selection" in BIOS Advanced settings from "Windows 8" to "Windows 7".

---

### Post by oldfred on 2014-11-29
That may be what we recommend in turning off secure boot. My mother board just calls it Windows or other.

---

### Post by gordon12 on 2014-11-30
> **janne-m-heikkinen said:**
> I found that solution for this was to change "OS Selection" in BIOS Advanced settings from "Windows 8" to "Windows 7".

Yes I just found out that this change worked for me as well!! All other changes like disable UEFI, etc, did not fix my issue of booting (boot halted with "soft lockup"). Only changing this from windows 8 to windows 7 could fix it. NOw it works fine.

---

### Post by lupulin on 2014-12-13
> **gordon12 said:**
> Yes I just found out that this change worked for me as well!! All other changes like disable UEFI, etc, did not fix my issue of booting (boot halted with "soft lockup"). Only changing this from windows 8 to windows 7 could fix it. NOw it works fine.

I just wanted to say thanks to Janne. This was causing me a lot of trouble and that was the fix for me too. On a Asus D553M

---

### Post by negora on 2015-05-22
I just purchased an ASUS X553MA-SX451B some days ago and yesterday I had the same problems to install Kubuntu 14.04. Switching the option "OS selection" to "Windows 7" also worked for me (thank you Janne). However, it had some consequences:

[LIST]
[*]It enabled the CSM module of the UEFI, so the computer started to run in "Legacy BIOS mode" after the next boot.
[*]It disabled the XHCI interface. So the USB 3.0 stopped working... Or so it seemed.
[/LIST]

So I decided to start from scratch again. I loaded the default settings. I enabled the "Windows 7" mode, saved and rebooted. Then I enabled "FastBoot", "SecureBoot" and "XHCI" and rebooted again. Next, I tried to install Kubuntu and it worked fine :) . I don't know what the "Windows 7" option does exactly, but it seems that it enables or disables "something" that causes the hang in the Ubuntu family. By the way, before all this, I tried to run in "Legacy BIOS mode" by hand, simply enabling the CSM module, but it didn't work either. So it confirms that the "Windows 7" mode does something else.

Just out of curiosity, Has anyone tried to install Windows 8 + Ubuntu with the "Windows 7" mode enabled? Does Windows 8 work fine?

Note #1: Yesterday I also installed the same Kubuntu 14.04 in an ASUS X551MAV-SX970B. I updated the BIOS to the latest version, from the beginning, and the installation was OK in UEFI mode. I had not to enable any extra mode. It's curious.

Note #2: In the case of the X553MA, I also tried updating the BIOS. But it wasn't enough, of course.

---

### Post by oldfred on 2015-05-22
I have an Asus motherboard.
On it the secure boot UEFI setting is just called Windows. So I think your Windows 7 is the secure boot setting. Windows 7 does not support secure boot, but can be installed in either UEFI or BIOS/CSM boot mode. 
And Windows 8 then can be installed in all three modes, UEFI with secure boot, UEFI, or CSM. But all vendor installed Widnows 8 systems are UEFI with secure boot on.

With my Asus motherboard I had to go into CSM to change to UEFI only to be able to boot in UEFI mode, not CSM and not Secure boot. But could not get into CSM settings with secure boot on, as CSM also is never a secure boot mode.

Fast boot setting in UEFI can cause issues. It assumes hardware has not changed so skips all the hardware check to boot much faster. But then you do not have time  to get into UEFI to change boot or other settings. And if system does not boot then you want to get into UEFI to change to boot flash drive. My motherboard had settings for cold boot that could be different from warm reboot. So I have normal boot on cold or power off, fast boot but with a 3 sec delay on reboot and 3 seconds on grub menu. Not sure if Asus laptop has all those settings, but best to check what you do have and if not, turn off UEFI fast boot.

---

### Post by negora on 2015-05-23
Hello Oldfred:

It's weird, because this UEFI shows SecureBoot and the OS Selection as different options. I can enable the "Windows 7" mode but also enable SecureBoot separately. Indeed, that's what I finally did. However, I can not confirm if SecureBoot is really enabled or not, because I decided to get rid of Windows 8.1, which is supposed to "need" it. Maybe SecureBoot is not enabled at all and it's just a fault in the UEFI, which does not hide the SecureBoot option when the "Windows 7" mode is selected. Anyway, I made a backup of the entire disk before wiping Windows 8.1, so in the future I might test that.

I also agree with you that it's better to disable FastBoot. Some times I've restarted the computer to enter the UEFI but it has been impossible because it has booted too fast. I've needed to press the power button for 3 seconds in order to do a proper turn off. I'll disable it in my computers, because the boot speed is not important for me.

Thank you ;).

---

### Post by oldfred on 2015-05-23
Windows 8 will boot with secure boot off.

Not sure if they fixed grub, but you could not boot Windows from grub menu with secure boot on, only UEFI boot menu. 
And you cannot boot Windows with Windows 8 fast-startup or always on hibernation on.

Since Windows 7 can boot in either UEFI or BIOS mode, not sure what it is then in your settings. 
But Windows 7 default install is BIOS/CSM, as you have to copy to flash drive & make a few changes to convert to UEFI boot.

---

### Post by bradley28 on 2015-07-31
> **janne-m-heikkinen said:**
> I found that solution for this was to  change "OS Selection" in BIOS Advanced settings from "Windows 8" to  "Windows 7".

I know this bumps an old thread, but I feel saying this worked (setting OS to win7 from win8 in the bios) is worth it.

For ubuntu 14.04:
Fixed purple-screen hang on a new asus-A553M; in uefi mode; with windows 8.1 (which still boots with the win7 bios setting).

cheers mate, I was all caught up on the nomodeset fix, but it was this all along.

---

### Post by anshuman3 on 2015-10-13
Janne!! you're a life saver. Thanks for coming back and posting this for everybodys benefit. Somehow this option just didn't occur to most of us.

---

