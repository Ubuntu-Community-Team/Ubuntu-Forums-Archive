---
title: "Not able to install Ubuntu 18.04 on Clevo laptop (Intel HM370 rev. 10 and CPU i7-8750"
date: 2018-06-04
forum: Installation &amp; Upgrades
---

### Post by axel-heyst on 2018-06-04
I have a few questions regarding my problems with installation of Ubuntu 18.04 on my laptop. The laptop is based on Clevo N871EJ1 and has the following configuration: chipset Intel HM370 rev. 10, CPU i7-8750H 6 x 2.20 - 4.10GHz Turbo, RAM 16 GB (2 x 8) DDR4 2400 MHz, storage Samsung SSD 512GB 960 Pro NVMe M.2 2280, graphics card NVIDIA GeForce GTX 1050 4GB GDDR5. When trying to install it from USB stick or even loading Live version I could see lots of ACPI-related errors. Live version was loaded but all I could do was moving cursor with touchpad but no touchpad button worked. When I tried to install Ubuntu 18.04 it broke quickly with stack displayed on the screen. Then I used FWTS tool to get some details. It reported a lot of errors, below you can see some of them:

```
FAILED [HIGH] KlogAcpiBadAmlCode: Test 1, HIGH Kernel message: [ 0.010017] ACPI
Warning: Unsupported module-level executable opcode 0x70 at table offset 0x34C6A
(20150930/psloop-222)

ADVICE: ACPI AML interpreter has found some non-conforming AML code. This should
be investigated and fixed.



FAILED [HIGH] KlogAcpiNamespaceLookupFailure: Test 1, HIGH Kernel message: [
0.259471] ACPI Error: [_SB_.PCI0.RP05.PXSX] Namespace lookup failure,
AE_NOT_FOUND (20150930/dswload2-191)

ADVICE: The kernel has detected an error trying to execute an Method and it
cannot find an object. This is indicates a bug in the DSDT or SSDT AML code.



FAILED [HIGH] KlogAcpiObjectNotFound: Test 1, HIGH Kernel message: [ 0.259479]
ACPI Error: Method parse/execution failed [\_SB.PCI0.RP04.PXSX] (Node
ffff88046ccca230), AE_NOT_FOUND (20150930/psparse-542)

ADVICE: This is a bug picked up by the kernel, but as yet, the firmware test
suite has no diagnostic advice for this particular problem.

```


I have the whole report available.
Just a note: I also tried Ubuntu 16.04 but with the same effect. 

I was looking for some ACPI-related BIOS/UEFI settings but I found BIOS/UEFI (vendor: American Megatrends Inc., version: 5.13, released on 04/13/2018) to be very simple with none option related to ACPI.
Here's my questions:

1. Shall it be possible to overcome these issues with some changes to BIOS/UEFI only (meaning no update of kernel required)?
2. If answer to above question is "No" what is the chance that a new version of kernel with fix will be released in near future?

I understand that my hardware is fairly new but more and more laptops with 8th gen high voltage core i7 CPUs are expected to show up soon so the problem might not be limited to a single user.
Thank you for any help.

---

### Post by pars94 on 2018-06-20
I am very very novice at ubuntu and linux. Therefore, I just share my experience.

I have a almost same computer as you specified except the SSD (I have 256 gb ssd + 1tb hdd). Also I did similar steps as you did and I even do not know how I can get the error messages. I am trying to make dual-boot my pc after installing windows; screen or touchpad is freezing as similar to you. Both MBR and GPT in Rufus are tried with different USBs and nothing changed.

My solution is installing ubuntu on virtual machine. Now I have been using Ubuntu 18.04 for an hour and it seems fine for me :) If it is an option for your work, give it a try.

I hope a fix will be released in near future. I really want to be more familiar with linux enviroment.

---

### Post by oldfred on 2018-06-20
Have you updated UEFI from vendor?
Just about required for Meltdown and Spectre CPU vulnerabilitie, both Windows & Ubuntu kernels have been updated.

Are you using nomodeset? The nVidia card/chip will require a proprietary driver, but until installed nomodeset may work.
Some with nVidia have turned off nVidia in UEFI and installed with Intel video. Then installed correct nVidia driver from Ubuntu repository, yours is new enough to use ppa to get very newest, and then nomodeset not required.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[URL="http://ubuntuforums.org/showthread.php?t=1613132"]http://ubuntuforums.org/showthread.php?t=1613132

      [/URL]
 If wrong nVidia driver or upgrade, you must purge & install correct driver
[https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946](https://ubuntuforums.org/showthread.php?t=2362351&p=13649946#post13649946)
[https://ubuntuforums.org/showthread.php?t=2380061](https://ubuntuforums.org/showthread.php?t=2380061) 


Some systems also need other boot parameters. But many & you have to experiment if no one has posted what works with your system.
      
 Some other Intel boot options Each line is one that may work
acpi_osi=Linux  
acpi_backlight=vendor
 i915.i915_enable_rc6=1 
     

Your chip - *Launch Date* Q2'18, so you cannot get much newer.  Generally kernel is updated fairly quickly. Often Intel has updates into kernel before chip is released. But Distributions like Ubuntu have lead time to include a kernel, verify apts all work, freeze configuration and finally release it. 

If knowledgeable you can update to latest kernel, drivers & support software.
       
 [https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe](https://www.phoronix.com/scan.php?page=news_item&px=Intel-2018Q1-Gfx-Recipe)
The 2018Q1 Intel Graphics Stack Recipe for a recommended configuration is using the Linux 4.16 kernel, Mesa 18.0, xf86-video-intel 2.99.917, libdrm 2.4.91, libva 2.1.0, VA-API Intel Driver 2.1.0, Cairo 1.15.10, and X.Org Server 1.20 RC1.
[https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe](https://01.org/linuxgraphics/downloads/2018q1-intel-graphics-stack-recipe) 
    
If willing to experiment, accept that it may break, you can download the 18.10 version which may be updated daily. Not sure which kernel it is using yet. When first available it essentially was just a copy of 18.04, and each day newer updates are added.
[https://ubuntuforums.org/showthread.php?t=2391372](https://ubuntuforums.org/showthread.php?t=2391372)

---

### Post by pars94 on 2018-08-04
> Are you using nomodeset? The nVidia card/chip will require a proprietary driver, but until installed nomodeset may work.
Some with nVidia have turned off nVidia in UEFI and installed with Intel  video. Then installed correct nVidia driver from Ubuntu repository,  yours is new enough to use ppa to get very newest, and then nomodeset  not required.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)[URL="http://ubuntuforums.org/showthread.php?t=1613132"]
[/URL]

As oldfred mentioned, nomodeset option makes it work. I installed ubuntu 18.04 with adjusting to the nomodeset.

However there are other problems with my laptop. First of all, my laptop is this:
[https://www.monsternotebook.com.tr/abra/MONSTER-ABRA-A5-V13-2-1.html](https://www.monsternotebook.com.tr/abra/MONSTER-ABRA-A5-V13-2-1.html)

There is a review video on youtube about Monster series notebooks, but in Turkish. They show some problems about ubuntu. Especially about the Fn+key combinations.
[https://www.youtube.com/watch?v=-6XCs0OyYDo](https://www.youtube.com/watch?v=-6XCs0OyYDo)

In this video there is a problem about sleep mode. I did not see any similar problem, but I install ***pm-utils. ***I do not know it whether it helps or not.


After installing ubuntu and nvidia drivers, it works fine. However, touchpad does not work and I cannot changing the color of keyboard. 

RGB keyboard color problem
--- There is Windows program (***MONSTER Control Center***) on Monster notebook site that gives choices about color and brightness of keyboard, fan speed, etc. 

Touchpad problem
--- Even touchpad does not work after installing the windows 10. There is a ***Intel Serial IO*** driver that makes it work. Unfortuantely, I cannot find that driver on their drivers link after they updating that.

Drivers Link >> [URL="https://www.monsternotebook.com.tr/suruculer.html"]https://www.monsternotebook.com.tr/suruculer.html
[/URL]Touchpad driver is something like that >> [https://downloadcenter.intel.com/download/25601/Intel-Serial-IO-Driver-for-Windows-10](https://downloadcenter.intel.com/download/25601/Intel-Serial-IO-Driver-for-Windows-10) 

I did not use Ubuntu for a time to see other problems. Now I am on windows with ubuntu on virtualbox.


Sorry for very late reply:(:oops: and thank you for interest. I hope there is a solution for these problems. Many people from Turkey look for that.:D

---

### Post by kosme on 2018-08-13
Im am in the same situation, same chipset, processor, etc, and looking forward for being able to install Ubuntu on my machine.

> **pars94 said:**
> 

Touchpad problem
--- Even touchpad does not work after installing the windows 10. There is a ***Intel Serial IO*** driver that makes it work. Unfortuantely, I cannot find that driver on their drivers link after they updating that.

Drivers Link >> [URL="https://www.monsternotebook.com.tr/suruculer.html"]https://www.monsternotebook.com.tr/suruculer.html
[/URL]Touchpad driver is something like that >> [https://downloadcenter.intel.com/download/25601/Intel-Serial-IO-Driver-for-Windows-10](https://downloadcenter.intel.com/download/25601/Intel-Serial-IO-Driver-for-Windows-10)


You can download the most recent version of **Intel Serial IO controller driver** from this link >> [https://www.asus.com/Laptops/ASUS-VivoBook-Pro-15-N580GD/HelpDesk_Download/](https://www.asus.com/Laptops/ASUS-VivoBook-Pro-15-N580GD/HelpDesk_Download/)

---

### Post by QIII on 2018-08-13
@kosme -- It appears that your link is to a Windows driver download page.

An updated Windows driver will not solve an issue with a Linux distribution if the firmware driver is not used by the Linux kernel.

---

### Post by kosme on 2019-02-21
I just tried with the newly released version of Ubuntu, 18.04.02, and it is running flawlessly.

---

