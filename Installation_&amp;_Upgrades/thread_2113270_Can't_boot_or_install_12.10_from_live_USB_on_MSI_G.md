---
title: "Can't boot or install 12.10 from live USB on MSI GT70-0NC"
date: 2013-02-06
forum: Installation &amp; Upgrades
---

### Post by harphauler on 2013-02-06
Hi All,

Am having a frustrating time trying to install 12.10 64 bit on my new MSI GT70-0NC.  I successfully killed Win 8 dead, at least that step is done.

After setting my bios to legacy instead of UEFI, using a USB stick I can boot the machine to the purple screen and at that point regardless of what I do it won't boot further.  Said USB stick successfully boots on three other computers.  I also tried two other USB sticks of different brands, same problem.  Have tried other bios settings also, force fdd, hdd, etc. for the USB device.  The problem occurs whether I use Unetbootin or Startup disc creator in my current box running 12.10.

I can boot the machine with a USB stick running 12.04 64 bit.  I can also install 12.04 but the machine won't boot after the install without that USB stick inserted.  Regardless of what I do that USB stick has to be inserted for the machine to boot into 12.04 and I have to leave the bios set at legacy.

In all the searching I've done it seems there might be a problem with the video card.  The machine has a NVIDIA GeForce GTX 670M.

Suggestions?  I really really don't want to put Win 8 back on this machine!

Thanks much!

---

### Post by carl4926 on 2013-02-06
> I can also install 12.04 but the machine won't boot after the install without that USB stick inserted. 

Because you probably didn't make sure grub was set to sda
[https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png](https://dl.dropbox.com/u/10573557/Ubuntu/12.10_tips/12.10_set_root_home.png)
Often I see it default to the USB, which is wrong

---

### Post by harphauler on 2013-02-07
Will try that later this morning and get back.  No way to boot/install 12.10?

---

### Post by oldfred on 2013-02-07
With nVidia you need nomodeset on live installer and on first boot.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

    
And with 12.10 you need to install headers first before doing anything with the nVidia driver.
       Re: How To Install Nvidia Drivers [v8.1.2.12 by Bogan]. post 1126
[http://ubuntuforums.org/showthread.php?t=1743535&page=113](http://ubuntuforums.org/showthread.php?t=1743535&page=113)
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)
[http://ubuntuforums.org/showthread.php?t=2081649](http://ubuntuforums.org/showthread.php?t=2081649)
# You may need headers - meta package for 12.10 version:
sudo apt-get install linux-headers-generic

---

### Post by harphauler on 2013-02-07
Using the NOMODESET option (I have to type it in manually, otherwise no joy if I select it from the F6 option screen) I get as far as the Ubuntu 12.10 purple screen with the four chasing dots.  After 6-7 minutes the screen blanks and nothing more happens.  Depressing any key, sweeping the touchpad, etc. does nothing.  If I tap the power button I get a text screen of the typical Ubuntu shutdown process and the computer shuts down.

If I choose the Install Ubuntu option and use the NOMODESET option I get 3-5 minutes of scrolling text screens then the machine goes blank and shuts down.

---

### Post by harphauler on 2013-02-07
-> carl4926, I did need to change grub to sda.  Installed 12.04 fine, machine boots normally.  Thank you.

Still trying to figure out how to boot/install 12.10 . . .

---

### Post by carl4926 on 2013-02-07
> **harphauler said:**
> -> carl4926, I did need to change grub to sda.  Installed 12.04 fine, machine boots normally.  Thank you.

Still trying to figure out how to boot/install 12.10 . . .

Sounds like 12.04 is a better choice?!

---

### Post by oldfred on 2013-02-08
Is this an UltraBook with both a Hard Drive and a small SSD for caching Windows?

        Intel Smart Response Technology
[http://www.intel.com/p/en_US/support/highlights/chpsts/imsm](http://www.intel.com/p/en_US/support/highlights/chpsts/imsm)
Some general info in post #3
[http://ubuntuforums.org/showthread.php?t=2071242](http://ubuntuforums.org/showthread.php?t=2071242)
ubuntu 12.10 & Windows 8 oem Sony T & Intel SRT
[http://ubuntuforums.org/showthread.php?t=2090605](http://ubuntuforums.org/showthread.php?t=2090605)

---

### Post by sanderj on 2013-02-08
> **harphauler said:**
> Using the NOMODESET option (I have to type it in manually, otherwise no joy if I select it from the F6 option screen) I get as far as the Ubuntu 12.10 purple screen with the four chasing dots.  After 6-7 minutes the screen blanks and nothing more happens.  Depressing any key, sweeping the touchpad, etc. does nothing.  If I tap the power button I get a text screen of the typical Ubuntu shutdown process and the computer shuts down.

If I choose the Install Ubuntu option and use the NOMODESET option I get 3-5 minutes of scrolling text screens then the machine goes blank and shuts down.

Have you also tried NOACPI NOAPIC (or something like that) as boot parameters? That always helped with unwilling systems. See [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
You would also need the "no-flash" option so that Ubuntu does not start the chasing dots, but only the system boot lines. But I can't find that option right now...

---

### Post by karlheinz.ade on 2013-02-08
> **harphauler said:**
> Hi All,

Am having a frustrating time trying to install 12.10 64 bit on my new MSI GT70-0NC.  I successfully killed Win 8 dead, at least that step is done.

After setting my bios to legacy instead of UEFI, using a USB stick I can boot the machine to the purple screen and at that point regardless of what I do it won't boot further.  Said USB stick successfully boots on three other computers.  I also tried two other USB sticks of different brands, same problem.  Have tried other bios settings also, force fdd, hdd, etc. for the USB device.  The problem occurs whether I use Unetbootin or Startup disc creator in my current box running 12.10.

I can boot the machine with a USB stick running 12.04 64 bit.  I can also install 12.04 but the machine won't boot after the install without that USB stick inserted.  Regardless of what I do that USB stick has to be inserted for the machine to boot into 12.04 and I have to leave the bios set at legacy.

In all the searching I've done it seems there might be a problem with the video card.  The machine has a NVIDIA GeForce GTX 670M.

Suggestions?  I really really don't want to put Win 8 back on this machine!

Thanks much!

Hi
I have  a new  PC with a EFI Bios and were running in the same problem.  
The solution is:
format your USB Stick with WIN 7 (64Bit), then put the system you want (i prefer unetbootin) without a new formatunder Linux  on the stick. This worked, a saw now the stick with the bios bottmanager and could boot the live system from the stick

good luck and regards

Karlheinz

---

### Post by harphauler on 2013-02-08
> **carl4926 said:**
> Sounds like 12.04 is a better choice?!

This is probably the direction I'll go; it isn't bad.  I'm somewhat stuck on trying to get 12.10 on there because that's what I started with, it didn't work so I backed up to the current LTS "just to see if" and it worked.

---

### Post by harphauler on 2013-02-08
> **oldfred said:**
> Is this an UltraBook with both a Hard Drive and a small SSD for caching Windows?

I'm not quite sure how to answer this one - on the one hand I ordered the machine without an SD card for the OS.  None shows in the bios.  However using Ubuntu's disk utility I see a SDD, unmounted, no media detected.  If I click format I have that option.  Haven't tried doing that.

I should have tried to help those helping me a bit better, here's further specs for my machine:

Model GT70-0NC-008US; tag under the battery shows GT70-0NC-494US
Win 8 64 bit was pre-installed
Intel Core i7-3610QM Processor, 2.3 GHz
NVIDIA GeForce GTX 670M
750GB HDD
16GB RAM
No raid

---

### Post by harphauler on 2013-02-08
> **sanderj said:**
> Have you also tried NOACPI NOAPIC (or something like that) as boot parameters? That always helped with unwilling systems. See [https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options](https://help.ubuntu.com/community/BootOptions#Common_Kernel_Options)
You would also need the "no-flash" option so that Ubuntu does not start the chasing dots, but only the system boot lines. But I can't find that option right now...

No, haven't tried that yet.  Will put it on my list of things to do; am going in the direction oldfred is pointing; might be on to something with the SDD.

---

### Post by oldfred on 2013-02-08
The UltraBook is a Intel trademark and maybe a few vendor have done something similar. It usually is a small SSD soldered onto the motherboard or built into the Hard drive but seen as a separate device from Linux. It uses RAID somehow and that often causes install, or install of grub issues. 

If you cannot boot Live installer or after install, then it is often video issue but can be many other boot parameters with these new (or old) systems. It is a work around for a special configuration.  Best to search for same system to find if someone posted details, otherwise it an be a lot of trial an error.

There also are many BIOS settings that can cause issues and some are not obvious. Sometimes just leaving a non-bootable CD or another flash drive. Is system UEFI/BIOS? Often newer Intel systems have the new UEFI even if booting in BIOS mode.
 I have posted before a long list of BIOS issues, but the vast majority do not apply to any one user. If you cannot boot with boot parameters I will post list again for you to review.

---

### Post by harphauler on 2013-02-09
> **karlheinz.ade said:**
> Hi
I have  a new  PC with a EFI Bios and were running in the same problem.  
The solution is:
format your USB Stick with WIN 7 (64Bit), then put the system you want (i prefer unetbootin) without a new formatunder Linux  on the stick. This worked, a saw now the stick with the bios bottmanager and could boot the live system from the stick

good luck and regards

Karlheinz

Should have included in one of my posts that this is one of the steps I tried before posting my first plea for help.  Thanks anyway!

---

### Post by harphauler on 2013-02-09
-> carl4926 and -> oldfred -

carl4926, Since 12.04 will work I may wind up using it for the short term.  That said, here's more for

oldfred,  I posted a note in the MSI forums.  A user there is going to attempt to install 12.10 sometime this weekend on a box that appears to be the same as mine.  He suspects as you do that something with EFI is a problem and/or a SDD that might be there.  To that end I'm restoring the box to factory to get some info from WIN 8.

So I'm unsure of board etiquette here, should I mark this as solved (since I can install 12.04 and am willing to do so) and start a new thread after getting more info from MSI or just sit on this thread?  I certainly willing to share whatever info I get from here or elsewhere!

Thanks again!

---

### Post by oldfred on 2013-02-09
I would just post in this thread when you get a better solution. Many search forum and finding your MSI system may think a solution is here is already solved.

12.04 will boot with UEFI but not with secure boot on pre-installed Windows 8 systems which all have secure boot. Some systems let you turn it off and will still boot Windows (actually all should). 12.04 will get new updates with next point release in just a few days and then is supposed to also work with secure boot. It is getting the version of grub2 2.00 that 12.10 currently has. 12.04 is currently grub2 1.99.

We are seeing the entire gamut of UEFI issues. Some systems just work, some require some effort and work arounds and some just do not work.

---

### Post by harphauler on 2013-02-10
We might be getting somewhere -

In BIOS turn off/disable fast boot; choose Legacy boot mode
At first boot screen hit F6, tic acpi=off; delete "quiet splash" from Boot Options text.
I chose Try Ubuntu without installing option on next screen.

Machine completed booting into 12.10.  It did not recognize my Synaptics touchpad but did recognize the mouse I plugged in.  Other than the touchpad not functioning (haven't looked for a driver, etc.) the system seems to work as the designers intended.

Have not yet tried to install 12.10 from here, that will need to wait until later today, have to run.

Thanks again.

---

### Post by oldfred on 2013-02-10
If you have Ubuntu in BIOS mode you will not be able to easily dual boot. YOu only then can boot Windows by going into UEFI/BIOS and change to UEFI to boot Windows.

Boot-Repair will convert a BIOS install by uninstalling grub-pc and installing grub-efi. If you can boot you can probably do the same. 

But grub2's os-prober still creates BIOS only chain entires to Windows which do not work with UEFI. You also can manually add correct entries or use Boot-Repair.

       How Boot-Repair works with UEFI systems - post 687 Dec 15, 2012
[http://ubuntuforums.org/showthread.php?t=1769482&page=69](http://ubuntuforums.org/showthread.php?t=1769482&page=69)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
Boot-Repair - Updated Jan 1, 2013 to not rename first time, but rename if first time Windows does not boot. Post 706
[http://ubuntuforums.org/showthread.php?t=1769482&page=71](http://ubuntuforums.org/showthread.php?t=1769482&page=71)

    
       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
grub2's os-prober creates wrong style (BIOS) chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)
Type of entry that does not work:
'Windows ...) (on /dev/sdXY)'

---

### Post by harphauler on 2013-02-10
> **oldfred said:**
> If you have Ubuntu in BIOS mode you will not be able to easily dual boot. YOu only then can boot Windows by going into UEFI/BIOS and change to UEFI to boot Windows. 

I didn't think to mention I'm not going to install as a dual boot.  I want to run Ubuntu as the only OS so for me dual boot isn't an issue.  If I need to run Windows I'll do it in a VM within Ubuntu.

I will read the threads you have provided - thanks!

---

### Post by harphauler on 2013-02-16
In the last week have tried to boot several flavors of linux on USB live; DVD; CD, none are able to boot UEFI.  This occurs with or without the Windows 8 that came preinstalled on the system.  (Did a factory restore on the system and then tried the above with Ubuntu 12.04 & 12.10; Fedora, OpenSuse, Knoppix, etc.)  All with Secure Boot = OFF.  Some are able to boot when BIOS is set to Legacy.

Tried installing 12.10 - (booting as per prior post with acpi=off ticked and "quiet splash" deleted from boot options.) Installation went fine but system won't boot after restart.  Just stays at a black screen right after the MSI logo disappears, no further HD activity, etc.  Can't get a terminal (Ctrl + Alt + T, Ctrl + Alt + F1, etc.)  It acts as if it's gone into sleep or suspend mode.  As above, have tried other distros as well, the few that install and boot to a usable system are distros that are at least six months old or one or more versions prior to current release.

oldfred - read the various threads you provided and haven't found anything yet to work, work around, patch, etc.  Maybe this box is one that just isn't going to let linux live peacefully on it?

Seems backwards that newer distros won't work and older ones do . . .

---

### Post by oldfred on 2013-02-16
If you needed nomodeset or other boot options on live installer you will need those on first boot until you install correct video. And you may need other boot options permanently which can be added to grub. Until then you have to use e on grub menu and manually add boot parameters in place of splash quiet with each boot. Post #4 had links to screen shots.

Usually newer kernels and other updates do work better. Especially when it is new hardware.

---

### Post by harphauler on 2013-02-16
Can I change grub on the installed OS on HDD from a live USB?  If so, how?  

Thanks -

---

### Post by oldfred on 2013-02-16
I do not know how with UEFI.

With grub-pc you install grub to the flash drive and manually create grub.cfg. I have several flash drives with that and loop mount my ISO and have an entry or two to boot hard drive. I have several flash drives with gpt partitioning so that is not an issue.

       Install grub2 to USB -general info
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB]("http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB")
Label partition & mount (example do not use):
sudo grub-install --root-directory=/media/grub2 /dev/sdb


This is in my notes:
       
 [https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT](https://help.ubuntu.com/community/UEFIBooting#Chainloading%20Windows%20x86_64%20UEFI-GPT)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
sudo grub-install --target=x86_64-efi --boot-directory=/mnt/sdb1/EFI/BOOT --efi-directory=/mnt/sdb1 --removable

---

### Post by harphauler on 2013-02-16
Installed 12.10 on the box again.  Holding SHIFT key during boot I got the options screen.  Edited regular Ubuntu boot with apci=off, deleted "quiet splash" with that combination only can boot into 12.10 ok.

Realizing this isn't part of the thread title, my touchpad is not operational even with installing synaptiks and any other touchpad apps. Mouse work fine.

Did some rudimentary debugging of APCI, this box just doesn't want to boot 12.10 with any hint of it.  Since the fan(s) don't work either I'm going to give up on this, I just don't want to spend more time trying to debug and file a bug report.  Hopefully future releases of some flavor of Linux will work.

In addition, any attempt at UEFI is useless, nothing Linux will boot on this machine, just reporting that fact.  Since Legacy boot will work I'll stick with that.

Still seems backward that older software will function and the new won't.

---

### Post by harphauler on 2013-02-18
oldfred, I'm sorry I got snippy in my last post.  Decided to try submitting a bug report for both being unable to boot UEFI and that 12.10 won't work unless acpi is disabled.  Will try to work through that process and see if anything happens.  Thanks for helping, will report back here if anything happens with the bug reports.

---

### Post by harphauler on 2013-02-19
I've submitted this as a bug, [https://bugs.launchpad.net/bugs/1129511](https://bugs.launchpad.net/bugs/1129511) and it has been confirmed.  Hopefully a resolution is on the way :D

---

### Post by aspireone722 on 2013-02-19
Have you tried unetbootin?

---

### Post by aspireone722 on 2013-02-19
or possibly another Live Distro just to see what works and what does not.

---

### Post by oldfred on 2013-02-19
Do expect a bug to be fixed right away. Best option is if others also report bug and someone finds the work around.

Unless bug has extremely high priority update may take months. And only if multiple users report same issue and can document that is it repeatable or logs how details that it is  a system issue not a user issue.

I have seen some other threads with workarounds or ppas for touchpads. But I have not paid attention if just that model computer or maybe a model of touchpad that may apply to other computers.

---

### Post by harphauler on 2013-02-19
This might be fixed in upstream linux-kernal, v3.8.  With it installed have now successfully booted the box in a normal manner into a usable OS.  Additionally the touchpad works, fan(s) work; shuts down normally and restarts normally.  Still won't boot with BIOS set to UEFI but I'm not going to worry about that part.

---

### Post by BradenB on 2013-03-16
> **harphauler said:**
> Using the NOMODESET option (I have to type it in manually, otherwise no joy if I select it from the F6 option screen) I get as far as the Ubuntu 12.10 purple screen with the four chasing dots.  After 6-7 minutes the screen blanks and nothing more happens.  Depressing any key, sweeping the touchpad, etc. does nothing.  If I tap the power button I get a text screen of the typical Ubuntu shutdown process and the computer shuts down.

If I choose the Install Ubuntu option and use the NOMODESET option I get 3-5 minutes of scrolling text screens then the machine goes blank and shuts down.

I am having this exact same problem but with 12.04. Any solutions for me? NOMODESET is on, but I get this EXACT same issue.

---

### Post by harphauler on 2013-03-18
> **BradenB said:**
> I am having this exact same problem but with 12.04. Any solutions for me? NOMODESET is on, but I get this EXACT same issue.

From post #9 this thread, this worked for me:
> Have you also tried NOACPI NOAPIC (or something like that) as boot parameters? That always helped with unwilling systems.

---

