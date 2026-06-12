---
title: "Dual Boot Ubuntu 14.04 &amp; Windows 8, Ubuntu won't boot"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by LMollins917 on 2014-04-21
I get the impression that this has been asked a lot, so I'm sorry for doing so as well, but I've read through a lot of different threads on how to do this, just to get to this point, and I'm no longer sure what I'm doing wrong.  

 I am trying to install ubuntu alongside Windows 8.  
I have disabled secure boot and fast boot.  
I've installed ubuntu, seemingly with no errors, and can boot back into Windows, but I don't get an option to choose between it and ubuntu.  
I tried boot-repair, and this is the url output:  
[http://paste.ubuntu.com/7302022/](http://paste.ubuntu.com/7302022/)   
I really hope someone can help as I've been at this for hours. Thanks in advance.

---

### Post by oldfred on 2014-04-22
Starting about line 9429 you have several extracts from your UEFI.

 BootOrder: 0000,0005,0001,0002,0003
Boot0001* Windows Boot Manager
Boot0002* UEFI: IP4 Qualcomm Atheros PCIe Network Controller
Boot0003* UEFI: IP6 Qualcomm Atheros PCIe Network Controller
Boot0005* UEFI: JetFlashTranscend 4GB 1100
Boot0000* ubuntu,BootCurrent: 0005

Never understood why there are multiples, but assume one may be UEFI with secure boot, one UEFI, and one BIOS boot mode?
Have you tried with secure boot off? It does look like you have installed the signed kernel that should work with secure boot on.

It looks like ubuntu is first in boot order, but I would double check that. Can you boot ubuntu entry from either UEFI or one time boot key?
You may need extra boot parameters for i915 Intel Video. You put them in like nomodeset on grub menu, but usually nomodeset does not work with Intel video.

      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Possible boot options suggested by ubfan1
[http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710](http://ubuntuforums.org/showthread.php?t=2184839&p=12871710#post12871710)

At various places it does say this , but others seem to have similar errors and get it to work:

 Wrong GRUB version detected.

   An error occurred during the repair.

This is an email.
Report bugs to <[EMAIL="bug-grub@gnu.org"]bug-grub@gnu.org[/EMAIL]>
But I might suggest:
[https://bugs.launchpad.net/ubuntu/+source/grub2](https://bugs.launchpad.net/ubuntu/+source/grub2)
But they want a lot of logs like this one:
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1310068](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1310068)

So I do not know exactly what error is occurring.

---

### Post by LMollins917 on 2014-04-22
Hey, thanks for getting back to me with this. 

So, I originally had installed ubuntu with secure boot on, and this failed to boot to ubuntu, so I then went back and switched it off. So, the stage I was at when I had made the thread was that I still couldn't boot into ubuntu, and secure boot was off. 
To be more clear, when I said I couldn't boot into ubuntu, I meant that I didn't even get the option too (no grub, nothing). I would turn on the computer, and it would boot straight to windows. 

I did as you suggested, and restarted to check the UEFI settings. My boot order was listed as following: 

FIXED BOOT ORDER PRIORITIES 
Boot Option #1		[CD/DVD] 
Boot Option #2		[USB Key] 
Boot Option #3		[USB CD/DVD] 
Boot Option #4		[USB Hard DIsk] 
Boot Option #5		[Hard Disk:Windows Boot Manager] 
Boot Option #6		[Network: UEFI: IP4 Qualcomm Ath...] 

So, no mention at all of ubuntu. 

On a seperate menu option 
'UEFI Hard Disk Drive BBS Priorities' 
I was able to switch ubuntu to boot option 1. 

 
Since then, I've managed to re-enable secure boot, and everything now still works. 
As of now, everything is working fine. On start, I'm met with Grub, which gives me the option of ubuntu, or switching to the Windows Bootloader on sda2. Both options work fine, and I'm able to go with either ubuntu or Windows.   

Leaving this here mainly for completion, in case anyone else runs into a similar problem. The computer in question is an msi gaming laptop, and at least according to google, a lot of people seem to have run into problems trying to dual boot. 

Again, thank you!

---

### Post by oldfred on 2014-04-22
Glad that worked. :)

Does i915 video then work without any boot parameters?
 It used to need some, but they also said Intel updated kernel, support software and video drivers that now are in 14.04.

---

