---
title: "Help! How to Dual Boot, UEFI?"
date: 2012-11-17
forum: Installation &amp; Upgrades
---

### Post by PrinceOfJudah on 2012-11-17
I attempted to DUal Boot Ubuntu with my new gaming laptop, which shipped with windows 8. I turned off secure boot, and dual booted 12.04 by clicking "install alongside windows." I then started my laptop, only to discover that Windows 8 would no longer boot. I did not even try to start with Ubuntu and took it to Geek Squad and they restored it back to factory default. I want to know how to dual boot Ubuntu 12.04 (or 12.10 but I would prefer 12.04), without any problems and without any long complicated process, that will let me boot both Windows and Ubuntu from the windows 8 OS selection screen. I do NOT want to have to take it back to Geek SQuad. I don't want it to start with grub, since starting Windows from grub failed last time. It also wiped out the backup drives when I installed it so Geek Squad had to find another laptop of the same model with Windows 8 to make a recovery USB.

---

### Post by PrinceOfJudah on 2012-11-17
Anyone around?

---

### Post by coffeecat on 2012-11-18
First thing - please do not bump threads more than once every 24 hours.

To your issue, you don't provide enough information to be able to say what went wrong, but this wiki page will give you some useful information:

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Grub will boot Windows 8 in Uefi mode so long as the correct version of grub was installed. One of the things that might have gone wrong is if you booted the Ubuntu installer in legacy mode. Take your time reading that link. There are a lot of things to consider with Uefi booting and different makes of hardware seem to present different issues. My own experinec with Win8/Ubuntu dual-boots is with two different (makes of) Uefi capable motherboard. One reduced me to a quivering enraged heap on the floor. The other was fairly straightforward.

---

### Post by PrinceOfJudah on 2012-11-18
Okay sorry about the bump. I'll read that link. 

OKay after a quick glance, it looks far too complicated for me. Is there any way I can get phone support to walk me thru this step by step? (I cannot afford to pay for support.)
EDIT: I've read it, and I am still afraid of messing it up. I really do not understand what I've read.

---

### Post by coffeecat on 2012-11-18
> **PrinceOfJudah said:**
> Is there any way I can get phone support to walk me thru this step by step?

Not that I know of. Phone support from Canonical is a paid-for service.

So that people can help you, let's get some information about your system. I won't have all the answers myself (far from it!) because my experience of Windows 8/Ubuntu dual-booting is from using the pre-release Windows 8 installer and machines devoid of any operating system so that I had a clear field to start from. There are extra considerations when you are creating a dual-boot with a pre-existing Windows installation.

The first thing to do...

> **PrinceOfJudah said:**
> Geek Squad had to find another laptop of the same model with Windows 8 to make a recovery USB. 

Make yourself a set of recovery DVDs. All laptops with pre-installed Windows should come with a utility to create recovery DVDs from the recovery partition so that you can re-install Windows if all else goes wrong. That is - if the recovcery partition is still there. Also, what make and model of laptop is it? Someone might have experience of it or a similar model.

Next - boot into Windows 8 and open Disk Management. Take a screenshot of the open window (you can use "snipping tool") and post that so that we can see how Windows interprets the partition layout. Now - boot into the Ubuntu live session by choosing "try Ubuntu" when you boot up with the live Ubuntu CD/DVD/USB. Open Gparted and take a screenshot of the open window by press Alt+PrintScr. We need that to compare with what Windows says, because Gparted will show hidden partitions that Windows' Disk Management will not. Post the screenshot. Don't do anything else with Gparted. 

If youlre not sure how to post screenshots, the best way is with a thumbnail attachement, uploading the images to the forum. Use the "Manage Attachments" button which you can find below the message field, or the [img]http://ubuntuforums.org/images/editor/attach.gif[/img] button in the message toolbar above the message field.

---

### Post by PrinceOfJudah on 2012-11-18
Unfortunately, I have no DVDs and cannot buy any. The only reason why I got this laptop is that another model was defective and they finally replaced it. It only cost 20 USD to make up the price difference. Right now I can barely pay the bills. So I guess I can't do this until some other time. Could you lock this thread and then reopen it upon my request? THat way I can do what you ask when I have the money to do so.

---

### Post by coffeecat on 2012-11-18
If you really want me to lock the thread, just pm me and I'll do so. But how about we leave it open for the time being? Someone else may have something constructive to add which, even if you can't act on it immediately, might give you some useful information. I have the thread subscribed, so if anyone tries to hijack the thread or post spam I will know about it and can remove anything spurious fairly quickly.

---

### Post by offgridguy on 2012-11-18
coffeecat; thanks for this url.


[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Since more of the new computers are going this way, I am going to need this probably
sooner than later.

---

### Post by oldfred on 2012-11-18
If you had posted here before going to geek squad we probably could have fixed the Windows boot issue.

With UEFI both Windows and Ubuntu's boot loaders are installed to the efi partition. From the UEFI menu you can directly boot either one. But if booting grub2 as a default it will let you boot both (if corrected see below). 

You do have to use the 64 bit version of Ubuntu and have to boot in UEFI mode as how you boot install disk is how it will install. That has worked for many. 
But Boot-Repair will convert a incorrect BIOS type install to UEFI install if 64 bit version of Ubuntu.

Grub does have a bug in creating the Windows chain load entry.
Again Boot-Repair can add a correct entry or we can walk you thru the process of manually creating a correct entry.

       grub-update fails to detect windows bootloader on a uefi system
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/807801)
Wrong style chain boot entry
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1024383)


       
 Post the link to the BootInfo report that this creates.

   Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.Install in Ubuntu liveCD or USB or:
Full RepairCD with Boot-Repair (for newer computers) 
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by PrinceOfJudah on 2012-11-19
OKay so you are saying I can (as long as Ubuntu boots in EFI mode) simply install Ubuntu normally and then use boot repair while running Ubuntu to fix Grub so that it will boot both Windows 8 and Ubuntu? Does this have a 100% chance of working? I really really want to use Ubuntu and use windows only for things that I absolutely cannot run on wine. Is there a way to install Ubuntu without Grub at all? I want to boot Windows 8 and Ubuntu via the Windows 8 bootloader if at all possible. Will installing "alongside Windows" delete the special recovery partitions? Geek Squad said that happened. I don't want to have to go thru a long process of making 250 MB partitions for EFI something or other which I don't understand to begin with.

---

### Post by oldfred on 2012-11-19
Cannot guarantee it, as it does depend on exactly your hardware. 

But it has worked for these. And we only get those who have issues & then resolve them. Those that it just works do not have to ask for help. 

       [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode](https://help.ubuntu.com/community/UEFI#Converting_Ubuntu_into_EFI_mode)
How Boot-Repair fixes a Ubuntu with grub-pc with efi Windows
[http://ubuntuforums.org/showpost.php?p=12205679&postcount=516](http://ubuntuforums.org/showpost.php?p=12205679&postcount=516)
UEFI installs in BIOS, Boot-Repair to fix
[http://ubuntuforums.org/showthread.php?t=2048457](http://ubuntuforums.org/showthread.php?t=2048457)
[http://ubuntuforums.org/showthread.php?t=2058453](http://ubuntuforums.org/showthread.php?t=2058453)

    
       UEFI dual boot two drives
[http://ubuntuforums.org/showthread.php?t=2072950](http://ubuntuforums.org/showthread.php?t=2072950)
[http://ubuntuforums.org/showthread.php?t=2031836](http://ubuntuforums.org/showthread.php?t=2031836)
UEFI boot Issue with Alienware X51 
[http://ubuntuforums.org/showthread.php?t=2039451](http://ubuntuforums.org/showthread.php?t=2039451)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Dual Video Intel & nVidia
[http://ubuntuforums.org/showthread.php?t=1994622](http://ubuntuforums.org/showthread.php?t=1994622)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

---

### Post by offgridguy on 2012-11-19
> **PrinceOfJudah said:**
>  I really really want to use Ubuntu and use windows only for things that I absolutely cannot run on wine. 

I realize i am getting off topic here but i am curious as to your reasoning.
:)

---

### Post by davelindberg on 2013-01-08
> **offgridguy said:**
> I realize i am getting off topic here but i am curious as to your reasoning.
:)
 
 
I too am looking to install Ubuntu and Windows 8 on the same laptop with UEFI loader.
 
Some applications I use like, Corel Draw, do not have a Ubuntu counterpart good enough to be equal to Dorel Draw. I have tried WINE to load 3 apps in Ubuntu vis WINE... all failed.
 
Solution to attempt and buyy a Windows 8 PC laptop with two hard drive bays and install Ubuntu on second drive in a way UEFI will see the Ubuntu drive and give me an option to boot either.
 
I will need to read this post in detail, with the links shown, to get a handle if I can also do this too.

---

