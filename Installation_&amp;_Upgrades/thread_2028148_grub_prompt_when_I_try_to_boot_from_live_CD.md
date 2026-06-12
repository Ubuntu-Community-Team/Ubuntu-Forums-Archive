---
title: "grub prompt when I try to boot from live CD"
date: 2012-07-17
forum: Installation &amp; Upgrades
---

### Post by webcomm on 2012-07-17
I have a new computer that came with Windows 7.  I shrunk the windows partition, added an unformatted partition for ubuntu, and added a big storage partition.  I burned the ubuntu iso to a DVD (I don't have a CD handy), and edited the windows boot order so I can boot from the ubuntu iso.  But when I select ubuntu from the boot options, I get the grub prompt.  

In the past when I have run a live CD on other computers, it has not shown me the grub prompt.  Instead it boots up ubuntu directly.

What's my next move?  

Thank you

---

### Post by Easy Limits on 2012-07-17
Is your DVD the 32 bit or 64 bit version of Ubuntu?

---

### Post by webcomm on 2012-07-18
It's the 64-bit version.  File name: ubuntu-12.04-desktop-amd64.iso

I'm new to Windows 7, and when I burned the disc, I was prompted to decide whether to burn it "like a USB flash drive," or like a CD/DVD.  I chose to burn it "like a USB flash drive".  I couldn't find any information on the WWW about whether the choice matters for an Ubuntu live CD.

---

### Post by Quackers on 2012-07-18
Try burning the iso file "as an image"

---

### Post by oldfred on 2012-07-18
I did not think CD uses grub to boot for normal BIOS boots. But I do think it uses grub-efi to boot in efi mode. 

So is this a very new system using UEFI? 
UEFI systems should give two options to boot one UEFI and the other BIOS/AHCI/legacy or whatever.

If first partition is efi or drive is partitioned gpt then you have UEFI and Windows is in efi mode. 
But even with UEFI, Windows may still be in BIOS/MBR mode and then Ubuntu would also have to be installed in BIOS/MBR mode.

---

### Post by webcomm on 2012-07-18
@oldfred, It's a very new system, but is not configured to use UEFI.  I used a program called EasyBSD to edit the boot order, and this system apparently does not respect the bios settings that you get when you click F10 on startup.  Instead you have to edit the Boot Configuration Data, which can be done either via the command line or with a program like EasyBSD.  So now when I turn the computer on I'm presented with an option to boot from the CD or boot Windows 7.  If I choose the CD (really it's a DVD), I get the grub prompt.

@Quackers, there is no "as an image" option in windows 7.  That language isn't used anymore.  The choices are burn like a USB flash drive, and burn like a CD/DVD.  

Thanks for your responses.

---

### Post by oldfred on 2012-07-18
Last I had heard was EasyBCD did not work with UEFI, but maybe its updated, or because you are using BIOS mode it may work.

Both Windows & Ubuntu will from UEFI boot menu have two boot/install choices. 
One is UEFI and the other is BIOS/AHCI/legacy or whatever your UEFI calls it. Both Windows & Ubuntu should be installed in the same mode or both UEFI with gpt partitions or both BIOS with MBR(msdos) partitioning. How you boot installer is how it will install.

---

### Post by webcomm on 2012-07-18
@oldfred, I think you misunderstood.  I am not using UEFI.  EasyBCD did its job.  It moved the CD to the top of the boot order, so that if I made no choice at all, the CD would boot after however many seconds.  It so happens that I'm not waiting -- I'm choosing the CD.   Regardless of whether I wait or make the selection manually, if I choose the CD, I get the grub prompt.

---

### Post by oldfred on 2012-07-18
Not sure then if it only presents BIOS version when booting from CD that way. Normally UEFI boots and CD offers two choices UEFI or BIOS to boot/install. But it may be defaulting to the wrong one as it still sees system as UEFI. 

Is yours one that can turn UEFI boot off in UEFI settings or is it one that defaults to boot from efi and only if not found then boots from MBR or in BIOS mode?

If defaulting to efi, then it is finding the UEFI install when it should find the BIOS install. Perhaps a bug?

---

### Post by YannBuntu on 2012-07-19
Hello

EasyBCD is a bootloader located on the hard drive. It comes AFTER the BIOS, and it is called by the BIOS because your BIOS "boot order" is setup to boot on your hard drive.

Please enter your BIOS setup, then setup your "boot order" (in the BIOS) to make it boot on the CD. If you don't find, please show us pictures of your BIOS screens.

---

### Post by webcomm on 2012-07-19
There is some kind of disconnect in this thread.  I've stated twice that UEFI is not in use here.  I don't know why @oldfred is still talking about UEFI.  I don't know what UEFI is, exactly, but I see that there is a setting for booting with UEFI.  However, that setting is turned off by default, and I have not turned it on.  So the system is not booting with UEFI.

@YannBuntu, the first thing I tried, before starting this thread, was changing the boot order in BIOS, since that's what was needed in my old computer, which ran Windows XP.  Changing the boot order in BIOS had no effect, and I learned from some searches that the BIOS settings do not affect boot order on this machine (if I understand correctly).  There is something else that affects boot order -- the Boot Configuration Data.  That's what I edited with EasyBCD.  In other words, my computer is set up to boot from CD first in *both* the BIOS settings and BCD settings.  But why are we even talking about boot order?  It seems completely irrelevant to this topic.  As stated, I already have established the means to boot from the CD.  I am presented with that option when I turn on the computer, and I choose that option.  So why are we still talking about boot order at all?  The problem here is that instead of booting into Ubuntu, I get the grub prompt.  Since grub is not a windows thing, doesn't the fact that I'm seeing the grub prompt demonstrate that the machine is trying to use the CD to boot?  So the question remains... why the grub prompt?  Or, to put it another why, why might the live CD not be working?

Thanks for your responses

---

### Post by drs305 on 2012-07-19
I can understand your frustration at not being able to solve this, but the boot order keeps getting brought up because the 'helpers' have a lot of experience with GRUB problems and none have ever seen the LiveCD present a Grub prompt before. 

I reviewed this thread earlier and didn't respond because my thinking was along the same lines as what was already being presented. About the only suggestion I can make if it's not a boot order issue is to burn the CD/DVD again and see if the same thing happens. (Don't use the same image, redownload it before burning.)

---

### Post by YannBuntu on 2012-07-19
Generally the "GRUB prompt" indicates that the BIOS is booting on a hard disk which has GRUB in the MBR but the rest of GRUB is broken.
For example, this can happen if you tried&failed to install Ubuntu (or another Linux distro) on this PC.

According to your post#1, I think that you never installed (successfully or not) any Linux distribution on this PC. If I am wrong, please tell it. If I am right, then the GRUB prompt comes from the CD, and I'm sorry I can't help much, maybe other helpers here know more. EDIT: can you boot on another distro (eg [Boot-Repair-Disk]("http://ubuntuforums.org/showthread.php?t=1831869")) ?

---

### Post by webcomm on 2012-07-19
I am going to give your responses another read in a second.  I don't think I understand everything.  In the meantime here are some pictures.  Thank you.

These BIOS settings seem to have no effect on anything, but note that I have moved the CD to the top of the boot order:
[IMG]http://farm9.staticflickr.com/8151/7604011258_8d6484cf9e.jpg[/IMG]
I have not tried doing anything with the UEFI box checked.  When I click the question mark there is a disclaimer about UEFI being unsupported by the maker of this computer, HP.  So I haven't tried it.

BCD settings:
[IMG]http://farm9.staticflickr.com/8028/7604012976_9a3dc7497f.jpg[/IMG]

Once I add the entry for ubuntu as seen above, and restart the computer, I get two boot options similar to what editing BIOS would have given me in Windows XP:

[IMG]http://farm8.staticflickr.com/7258/7604011856_c1921f4032.jpg[/IMG]

And here's the grub prompt I get if I choose ubuntu from the boot options:
[IMG]http://farm8.staticflickr.com/7123/7604012440_55f82861bf.jpg[/IMG]

---

### Post by webcomm on 2012-07-19
> **YannBuntu said:**
> According to your post#1, I think that you  never installed (successfully or not) any Linux distribution on this  PC.

That's correct.

> **YannBuntu said:**
> can you boot on another  distro (eg [Boot-Repair-Disk]("http://ubuntuforums.org/showthread.php?t=1831869")) ?

I haven't tried that but I suspect nothing is in need of repair.  Just a hunch.

I'm going to try burning another disc and this time choose the "burn like a CD/DVD" option.

---

### Post by YannBuntu on 2012-07-19
If you can boot on another Linux CD, that would mean that the problem is not a BIOS configuration problem, and that it is specific to Ubuntu.
You can also check if you can boot on a Ubuntu 10.04 CD for example.

---

### Post by drs305 on 2012-07-19
Note that it's Grub4DOS and not straight GRUB. Someone familiar with Grub4DOS might be able to shed some light on this and where it came from.

---

### Post by oldfred on 2012-07-19
Is grub4dos from EasyBCD?

I do not know about EasyBCD and how it works but found this:

[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[> ]("http://neosmart.net/wiki/display/EBCD/NeoGrub")[NeoGrub]("http://neosmart.net/wiki/display/EBCD/NeoGrub") is  NeoSmart Technologies' implementation of the open-source GRUB bootloader  (ported over to Windows by the Grub4Dos team) intended to allow Windows  users to boot into Linux without having to resort to rescue discs,  second bootloaders, or messy install routines for GRUB or LILO.

the only reason I keep mentioning UEFI, was in an recent thread Ubuntu installed the grub-efi not grub-pc (or grub2 for BIOS). User has an UEFI system but had it set to boot with BIOS. This bug was filed by the user.

UEFI computer in BIOS mode, installer installs grub-efi - New July 2012
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1026616)
[http://ubuntuforums.org/showthread.php?t=2028699](http://ubuntuforums.org/showthread.php?t=2028699)

---

### Post by webcomm on 2012-07-19
> **oldfred said:**
> Is grub4dos from EasyBCD?

No, I don't think so.  EasyBCD is just a way to edit the BCD settings (from what I understand).  In fact, if I uninstall EasyBCD, I still have an option to boot into Ubuntu, and if I do, I still get the grub prompt (or grub4dos, or whatever it is).

If I try reading about this stuff... I just think it's a waste of time, to be honest.  I don't think there's much chance I'm going to understand these things, and if I did, I'd probably just reach the conclusion that none of what I had learned was relevant to the problem.

The underlying problem seems to be that the BIOS settings don't work.  I don't know if that's normal in Windows 7.  I guess the obvious move is to contact HP for support re: the boot order... though I'm not terribly optimistic about getting good support from a computer maker.  They probably don't field a lot of questions about boot order.

---

### Post by webcomm on 2012-07-19
I think the verdict is that my machine cannot boot from the optical drive.  I do not need EasyBCD to run a live ubuntu CD.  Instead, I probably need to copy the ISO onto a flash card and boot from there.  My computer recognizes the SD card reader (and also USB ports) as a bootable device, but not the optical drive.  I can't test this at the moment because I don't have an SD card or USB stick handy, but I think the solution is to not use the optical drive.

---

### Post by kreemoweet on 2012-07-19
The BIOS boot order is a completely different thing from any "boot order" you 
may see in a boot manager menu. EasyBCD is not a bootloader, it is a Windows
user-mode program for editing the BCD store (configuration file used by the
Windows Boot Manager). EasyBCD does not and cannot affect the BIOS boot
order, and I don't think it can cause your computer to boot from the CD. The
"grub" screen you see is something installed by EasyBCD (on your Windows
file system!!), so your computer has not even attempted to load/boot from the
CD/DVD, and you do not have a real Grub installed anywhere. I think you need
to figure out a way to get your Ubuntu image installed on the hard disk (not
on CD) before you will be able to boot from it.

---

### Post by Quackers on 2012-07-19
Just one observation.
Your bios boot order screenshot shows that the USB CD ROM is the first boot device.
Is your cd drive a USB device? My boot order shows a USB cd rom option but the main cd-rom is listed as optical drive and this is the one I use to boot from a cd on my laptop.
Having said that, I don't see a different option in your settings for such a device.

As has been previously mentioned a grub4dos prompt should not be appearing in an Ubuntu iso.
As for burning the iso file as an image, it would depend on which version of Windows you have. There are free programmes available for Windows that can burn an isofile to disc as an image (I believe Imgburn is one such programme).

---

### Post by oldfred on 2012-07-19
I do not know what is going on with grub4dos either. That is used by Windows type machines, not Ubuntu.

---

