---
title: "Installing OS to HP Envy M6 I5 Laptop"
date: 2017-01-28
forum: Installation &amp; Upgrades
---

### Post by rcaca0 on 2017-01-28
Hello,

I am trying to help a friend of mine restore a laptop of theirs by reloading a new OS to it.  

Laptop info:

HP Envy M6
Processor: Intel I5-4200M @ 2.5Ghz
Ram 8 GB KINGSTON 2 FOUR GB
System Board ID: 229E  <-- Not too sure what this means
System Board CT #: PEEWD00WD6Q1W2  <-- Not too sure what this means either -- hopefully it helps
Bios Version: F.04
Bios Vendor: Insyde
Ram 8 GB, Type unknown
Bios says Os Installed is Win 8.1  <-- It's not and cannot change
Hard Drive (replaced one but is supposed to be the original) is Toshiba 360 GB MK3265GSX  HDD2H83 F VL01 B

Background:
My friend purchased this laptop about 2 years ago new.  After about a year she spilled some liquid (says it was water) on it.  It stopped working so she brought it in to Best Buy (where she purchased the laptop).  They looked at it and convinced here to purchase a much bigger HD.  She was okay with that and they replaced the hard drive and moved her files over (how if the HD was no good beats me).  About a year ago the laptop stopped working again.  

I took a look at it and figured out it was the hard drive.  She saved the old hard drive so I replaced the bad one.  I ran the system check from HP and it says the HD was okay.  At first it would not read from the HD so I messed with the Bios.  I am unfamiliar with InsydeH20 Bios.  I have built multiple computers in the past but I don't remember this Bios.  When it first ran from the HD, nothing was working correctly plus it had Wind 7 on it.  I figured this may have come from another computer that she had.  So I decided to reload the OS. That is where I ran into a problem.  I first try to load Win 7 iso (An iso I have and used in the past for other computers) from a usb using YUMI 2.0.3.6.  It would not read it.  So I took a look at the Bios again and noticed the Secure Boot was enabled.  So I disabled it. It still did not work.  The bios also had two different Boot Orders which I am not familiar with: UEF I and Legacy.  Can someone explain what these are?  Originally I made the UEF I (could be a 1) to read from the HD and thats how it got it to read it the first time.  So when I went to load the OS I changed the boot order to USB Diskette on Key/USB Hard Disk, that did not work.  I still got the error of no OS.  Just in case, I changed the Legacy Boot Order to match.  That did nothing; I even cleared all of the Boot Keys and enabled Legacy Support.  Just in case my Win OS ISO file was bad I decided to try my trusted Ubuntu ISO.  I ran into the same issue.  I even tried to load an order version that I know that works but still nothing. I think I am running into some sort of security issue: either USB are disabled or maybe the HD is encrypted.   

I looked on the internet and found other people with the same issue loading an OS from Scratch.  I decided to call HP and after an hour of explaining why I wanted to reload the OS they said I needed to purchase their recovery disk for $55.  When I asked about the details about the recovery disk they told me that it has Win 7 on it which is what came with the computer (????) the bios and the sticker does not say that but it matches the old HD.  I asked them if the disk has instruction on how to load it, they told me no and that I will need to spend and extra $50 -$75 for HP support for each issue I ran into.  That didn't make sense to me so thats why I am here again to see if anybody knows how to load an ISO file from an USB on a HP laptop?  I loaded some pictures of the Bios just in case I left something out.  If there is any information missing please let me know and I will get it.  My next step is to see if it will load from an external CD but I don't think this will work since it will need to go through a USB anyways.  

Thanks again,
R

[ATTACH=CONFIG]273427[/ATTACH][ATTACH=CONFIG]273428[/ATTACH][ATTACH=CONFIG]273429[/ATTACH]

---

### Post by oldfred on 2017-01-28
If you see a Windows 8 entry system originally came with Windows 8.

And then it seems like your friends at Best Buy did not know how to reinstall Windows 8 and installed Windows 7.
And that may not be a legal install, anyway. As Windows 8 has Product key embedded in UEFI, but only for reinstall of UEFI Windows and maybe only the HP distribution of Windows 8.
 Product key now in UEFI/BIOS
[http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/](http://reviews.cnet.com/8301-33642_7-57554240-292/windows-8-moves-to-bios-based-product-keys/)
[http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c](http://answers.microsoft.com/en-us/windows/forum/windows_8-windows_install/bipass-uefi-provided-product-key-to-install/a271067b-d655-4b46-8b52-b3f191b9370c) 

But UEFI uses gpt partitioning and Windows in UEFI mode will only boot from a gpt partitioned drive.
But almost all Windows 7 installs are BIOS with MBR partitioning and in BIOS mode will not install to gpt.
A Windows 7 installer can be converted to UEFI boot, but not with UEFI Secure boot on.

I do not know if this is still valid or not. There was a free upgrade to Windows 10, but that is not free anymore unless you are handicapped.

 Microsoft Windows 8.1 reinstall/refresh
[http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media](http://windows.microsoft.com/en-us/windows-8/create-reset-refresh-media)

So is drive UEFI/gpt or BIOS/MBR?

If not installing Ubuntu, I will move to the forum's Windows sub-forum where those who dual boot may be able to help.
 
From Ubuntu live installer you can add this tools which will run a full report on your current configuration.
But it may just be UEFI vs. BIOS settings in UEFI to make how system is installed.
      
 May be best to see details, you can run from Ubuntu live installer or any working install:
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info) and:
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

