---
title: "Ubuntu efi disaster."
date: 2012-11-21
forum: Installation &amp; Upgrades
---

### Post by viking777 on 2012-11-21
Just got a new laptop, Fujitsu Lifebook AH532. Installed Ubuntu 12.10 on it (overwriting Windows) because I had heard it had good efi support. Indeed it does, too good perhaps, because now the only thing I can do is to boot Ubuntu, nothing else. 

I can't access the bios, cant boot from usb, cant boot from cd/dvd, all those options are gone. I installed boot-repair carried out a repair but nothing has changed. The comprehensive information it provides is here:

[http://paste.ubuntu.com/1375041/](http://paste.ubuntu.com/1375041/)

Maybe boot-repair is not the answer since Ubuntu boots perfectly, but what is? I can't install a second distro, I can't reinstall the first one, I can't run any repair tools (unless they run from within Ubuntu like boot-repair), I can't use tools like gparted (because all my partitions are mounted). I have a disk image of the original disk, but I can't use it because I can't run Clonezilla to clone it back to the drive.

Basically I am just completely stuck. 

Any ideas?

NB. If you read the pastebin output ignore all refernces to /dev/sdb, it is not a boot device and it makes no difference to anything even if it is unplugged.

---

### Post by darkod on 2012-11-21
The machine surely has a way to enter bios. Can you refer to some manual or contact support?

Maybe it only has some sort of fast boot combined with a logo that's hiding the good old DOS like messages on the screen. Most manufacturers do that now hoping to present the computers as fast booting, not thinking about situations when you actually need time to go into some bios options, and similar.

I never want a machine that will just speed through boot.

---

### Post by viking777 on 2012-11-21
> **darkod said:**
> The machine surely has a way to enter bios. Can you refer to some manual or contact support?

Maybe it only has some sort of fast boot combined with a logo that's hiding the good old DOS like messages on the screen. Most manufacturers do that now hoping to present the computers as fast booting, not thinking about situations when you actually need time to go into some bios options, and similar.

I never want a machine that will just speed through boot.

Yes it has a way to enter the bios - press f2 at boot up - except it no longer works since installing ubuntu in efi mode, it just ignores it (it used to work before I installed Ubuntu, but not any more). 

I agree with you 100% about machines that speed through boot without messages and I disable that function in every distro I install including this one, I see all the boot messages on the screen as they happen, but it doesn't help, there are no errors.:confused:

---

### Post by oldfred on 2012-11-21
It is my understanding that Ubuntu uses the same secure boot key as Windows, so there should not be any difference. And installing a system does not modify UEFI or BIOS in any way.

Unless UEFI had options in the Windows boot loader to boot back into UEFI but I have not seen that. But this new secure boot is different. 

Did you turn secure boot off or is it still on? Ubuntu should work either way. Some have reported dual booting both Windows 8 & Ubuntu with secure boot setting in UEFI on or off after install without issue. But again that varies by how vendor has implemented UEFI secure boot.

You still have the Microsoft efi files in the efi partition. You could experiment with booting those from grub 's menu and see what happens after that crashes as it of course has no place to go.

> menuentry "Windows 7 UEFI" {
  search --file --no-floppy --set=root /efi/Microsoft/Boot/bootmgfw.efi
  chainloader (${root})/efi/Microsoft/Boot/bootmgfw.efi
}

    

#Add above to 40_custom
       gksudo gedit /etc/grub.d/40_custom
            sudo update-grub

---

### Post by viking777 on 2012-11-21
Thanks for the reply oldfred, I don't think that was a solution, but I found a workround at least, although it was absolutely terrifying with such a new machine. I had to follow the process mentioned here:

[http://www.linlap.com/fujitsu_lifebook_ah532](http://www.linlap.com/fujitsu_lifebook_ah532)

about removing the ram modules and shorting the cl1, cl2 pins. 

If Ubuntu caused me to have to do this then they need to rapidly rethink their handling of efi booting. 

This is only a workround because I still have no access to my bios (f2 still doesn't work). However f12 does and this gives you access to the boot choices menu. Before shorting those terminals there was nothing in there except Ubuntu. After shorting them all boot choices show up (although there is no way to order them as in the bios) at least you can choose which to boot from. 

And Linus thinks that efi is not a problem does he?

Hmm?

---

### Post by YannBuntu on 2012-11-21
> **viking777 said:**
> Yes it has a way to enter the bios - press f2 at boot up - except it no longer works since installing ubuntu in efi mode, it just ignores it

:(
maybe a bug in efibootmgr... Please report the hole bug here: [https://bugs.launchpad.net/ubuntu/+source/efibootmgr/+filebug](https://bugs.launchpad.net/ubuntu/+source/efibootmgr/+filebug)
and tell us the link so that we can follow-up.

---

### Post by viking777 on 2012-11-22
I will do that when I get the time Yannbuntu, in the meantime an update. 

I decided to reinstall Ubuntu in the hope of getting my bios access back, instead of that it reverted to having no bios access (f2) and the boot options access (f12) displayed two versions of Ubuntu and nothing else  (despite there only being one Ubuntu version installed). So I had to short my motherboard yet again. 

I have a good deal of experience with Linux and use it exclusively, but I can tell you I don't find this remotely funny. If novice users get UEFI experiences like this then Linux on the desktop is finished.

BTW before I removed windows I had access to the bios and I searched through the entire bios menu and found no controls relating to uefi or secure boot whatsoever. Here is the dmidecode output:

```
BIOS Information
        Vendor: FUJITSU // Phoenix Technologies Ltd.
        Version: Version 1.09
        Release Date: 05/22/2012
        Address: 0xE0000
        Runtime Size: 128 kB
        ROM Size: 4096 kB
        Characteristics:
                PCI is supported
                PC Card (PCMCIA) is supported
                PNP is supported
                BIOS is upgradeable
                BIOS shadowing is allowed
                Boot from CD is supported
                Selectable boot is supported
                EDD is supported
                3.5"/720 kB floppy services are supported (int 13h)
                Print screen service is supported (int 5h)
                8042 keyboard services are supported (int 9h)
                Serial services are supported (int 14h)
                Printer services are supported (int 17h)
                CGA/mono video services are supported (int 10h)
                ACPI is supported
                USB legacy is supported
                BIOS boot specification is supported
                Function key-initiated network boot is supported
                Targeted content distribution is supported
                UEFI is supported
        BIOS Revision: 1.9
```

There is a bios update on their site (10Aug2012) but needless to say it is a windows exe file and therefore I would need to put Windows back on to install it.

---

### Post by darkod on 2012-11-22
I might be wrong but I am starting to think that UEFI is actually designed to be more difficult to users, not easier. Especially yo users that want freedom.

They want to tie you to a certain manufacturer or OS.

I am planning my desktop upgrade and I am watching out very carefully the board model and have downloaded the manual from their website to confirm you can disable UEFI boot and run legacy boot only.

---

### Post by viking777 on 2012-11-22
> **darkod said:**
> I might be wrong but I am starting to think that UEFI is actually designed to be more difficult to users, not easier. Especially yo users that want freedom.

They want to tie you to a certain manufacturer or OS.

I am planning my desktop upgrade and I am watching out very carefully the board model and have downloaded the manual from their website to confirm you can disable UEFI boot and run legacy boot only.

Good idea, but too late for me. I did consider the bios manufacturer (for instance I would steer well clear of 'Insyde' as I had one before and it was a nightmare) Pheonix OTOH seemed like a good enough maker.

---

### Post by grahammechanical on 2012-11-22
May I say something?

All this is very new to all of us. With secure boot enabled it will only be possible to install an OS that supports Secure Boot and there are not many of them around at the moment. Ubuntu 12.10 is perhaps one of two for the time being.

[http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/]("http://web.dodds.net/~vorlon/wiki/blog/SecureBoot_in_Ubuntu_12.10/")

Secure boot is just a part of the UEFI (Unified Extensible Firmware Interface) specification. What does the rest of the specification say?

[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface]("http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface")

Here are my questions: If we install an OS with Secure Boot on do we get UEFI instead of BIOS? If so, then how does a user access the UEFI set up? Do we still have a BIOS that can be accessed by F2 or Del or whatever?

UEFI is a replacement for BIOS.

[http://www.uefi.org/learning_center/]("http://www.uefi.org/learning_center/")

Regards.

---

### Post by viking777 on 2012-11-22
Another update in case anyone is still reading this. 

Before installing Ubuntu on this machine I took a full image of the disk as it was when I got the machine - when everything worked. Today I restored the image and what do I find? 

Ubuntu's Uefi boot system has locked me out of the bios in Windows as well! Pressing f2 in windows now ,takes you to the windows boot menu not the bios. I also find out the another user posted an almost identical topic 2 weeks ago:

[http://ubuntuforums.org/showthread.php?t=2079168](http://ubuntuforums.org/showthread.php?t=2079168)

Same machine, same bios, same problem. He claims to have fixed it by 'reinstalling' the bios although he fails to explain how. 

Whilst I have been in windows today I flashed the bios with the latest update. It makes no difference because I can't access it. 

This is pretty obviously a problem with Ubuntu's implementation of Uefi which is preventing any bios access, similar to having a bios password - which I have never used.

Presenting someone with a machine that doesn't boot is one thing - you can always try another distro, but permanently locking somebody out of their own hardware is a different matter altogether. I now have a £450 laptop that is one day old, worked perfectly when I got it,  but is now bordering on useless and surprise, surprise, I am not best pleased about it. I hope that is not being unreasonable.

---

### Post by oldfred on 2012-11-22
Ubuntu does not change UEFI. And it makes sense that if both Windows & Ubuntu's efi loaders are in the efi partition even un-installing a system will leave efi loader and still be an option in UEFI boot menu. Somewhat like having grub in the MBR and un-installing Ubuntu and not being able to boot Windows with BIOS.

But it does not make sense that f2 does not work. UEFI/BIOS should always work. And it should even work without hard drive even plugged in and Ubuntu is only modifying hard drive. 

It would have to be that UEFI is copying something to hard drive to boot and then  grub/Ubuntu is overwriting that sector on drive. And that type of thing did happen with BIOS and flexnet DRM software where grub2 and flexnet were writing to same sector.

Best to file bug report and those that really understand how these systems work resolve it. 

Not related, but how UEFI can be enabled in unusual ways. 
       Lenovo ThinkCentre M92p only boots Windows or Redhat.
[http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg](http://www.phoronix.com/scan.php?page=news_item&px=MTIyOTg)

---

### Post by darkod on 2012-11-22
That was my understanding too. With UEFI, same like with BIOS boot, still the bios/uefi part should be accessible before the OS kicks in (regardless of the OS). It is very strange not to have a way to enter bios.

But since I don't know UEFI, even less the deep tech details, I don't have anything smart to say, the above is only my assumption.

---

### Post by viking777 on 2012-11-22
Thank you both for your input, I freely admit that I know far less about Uefi than either of you. I just had a feeling it would be a disaster and of course it has been. 

I will eventually get around to filing some bug (to be ignored probably) but in the meantime my energies are mainly devoted to trying to save my investment in this new laptop from being completely wasted. 

My next option (having gone back to a Ubuntu only install - Clonezilla is absolutely wonderful) is to try installing another distro to see if their invocation of Uefi is any better than Ubuntu's. 

Little as I know about the subject, I doubt very much that any distro would be able to undo the damage already caused by Ubuntu, but I am desperate, so I have to try anything I can.

---

### Post by YannBuntu on 2012-11-22
1) Before you erase Ubuntu, I insist strongly: please report the bug where I told you, it WILL for sure be reviewed quickly. (i will push the GRUB devs myself, because i think the issue is severe).
Best if you create the bug via the 'ubuntu-bug grub2' command, because it will automatically attach data to your report.

2) If i were you, i would then try Fedora, because it generally has very recent GRUB packages.

---

### Post by viking777 on 2012-11-23
> **YannBuntu said:**
> 1) Before you erase Ubuntu, I insist strongly: please report the bug where I told you, it WILL for sure be reviewed quickly. (i will push the GRUB devs myself, because i think the issue is severe).
Best if you create the bug via the 'ubuntu-bug grub2' command, because it will automatically attach data to your report.

2) If i were you, i would then try Fedora, because it generally has very recent GRUB packages.

I never intended to erase Ubuntu, just add another distro to it - it didn't alter anything.

The bug is reported here:

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1082418](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1082418)



I might give Fedora a try later, thanks for the suggestion.

---

### Post by YannBuntu on 2012-11-23
> **viking777 said:**
> [https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1082418](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/1082418)

Thanks, i'll follow-up.
Keep us in touch for Fedora...

---

### Post by lsatenstein on 2012-11-23
> **viking777 said:**
> Thanks for the reply oldfred, I don't think that was a solution, but I found a workround at least, although it was absolutely terrifying with such a new machine. I had to follow the process mentioned here:

[http://www.linlap.com/fujitsu_lifebook_ah532](http://www.linlap.com/fujitsu_lifebook_ah532)

about removing the ram modules and shorting the cl1, cl2 pins. 

If Ubuntu caused me to have to do this then they need to rapidly rethink their handling of efi booting. 

This is only a workround because I still have no access to my bios (f2 still doesn't work). However f12 does and this gives you access to the boot choices menu. Before shorting those terminals there was nothing in there except Ubuntu. After shorting them all boot choices show up (although there is no way to order them as in the bios) at least you can choose which to boot from. 

And Linus thinks that efi is not a problem does he?

Hmm?


Is it possible that besides jumpering out the bios memory keep alive voltage, that there is a set of parameters stored within the clock chip?  You could try the jumper again and also or alternatively, remove the battery (flat mercury Oxide) battery. 

I am reading this problem 10 days after you first reported it.

---

### Post by viking777 on 2012-11-24
@lsatenstein
> Is it possible that besides jumpering out the bios memory keep alive voltage, that there is a set of parameters stored within the clock chip? You could try the jumper again and also or alternatively, remove the battery (flat mercury Oxide) battery. 

I could try that, but first of all I would have to find the cmos battery (I have been so busy trying to fix this I haven't even found a mobo manual yet, in fact I don't even know the mobo type). Then of course there is the argument that I really shouldn't need to be doing stuff like that just to install a major distro. So I will keep it in mind but leave it for now - thanks anyway.

@YannBuntu

> Keep us in touch for Fedora... 

Fedora was a complete disaster, exactly the same as Ubuntu. It removed all other operating systems from the grub menu, it removed all other entries from the f12 boot choices menu and left me fiddling around with shorting mobo posts again in order to make anything work at all.

In between installing Ubuntu and Fedora I installed the Arch based Manjaro. Although it didn't give me any bios settings back, it correctly installed grub showing the other installed operating systems and did not interfere with the f12 boot choices menu either. So maybe Arch/Manjaro have a better grasp of this problem than Ubuntu/Fedora. 

After installing Fedora and shorting the mobo I was still left with no other choices in the grub menu (Fedora only). In order to try and rectify this I installed Mint 14 in the hope that it would restore a full grub menu (and I should add that in every install I have done I have elected to install grub to the MBR not the PBR so they have all had an equal chance). It restored a grub menu certainly, but not a full one, it had no entries for itself or Fedora. I tried update-grub which identified the Mint install but failed to add it to the grub menu and completely failed to identify Fedora. 
I next tried your own Boot-Repair tool which identified all installed operating systems and added them all to grub (so thanks for that).

The log file is here:
[http://paste.ubuntu.com/1382319](http://paste.ubuntu.com/1382319)
maybe that will help you a bit, as you will notice the partitioning has changed quite a lot since the last one I posted due to the number of OS's I have installed.

Summary I now have 4 operating systems installed, all working, but still no access to the bios settings via f2, and the only OS that has not caused me any problems has been Manjaro.

---

### Post by YannBuntu on 2012-11-24
> **viking777 said:**
> I next tried your own Boot-Repair tool which identified all installed operating systems and added them all to grub (so thanks for that).

The log file is here:
[http://paste.ubuntu.com/1382319](http://paste.ubuntu.com/1382319)

For information your UEFI firmware (~BIOS) is setup to boot the HDD in UEFI mode, and SecureBoot seems disabled.
(these information may be useful for the bug report)


> **viking777 said:**
> the only OS that has not caused me any problems has been Manjaro.

From Manjaro's GRUB menu, had you tried to boot 12.10? if yes, did it work?

---

### Post by viking777 on 2012-11-25
Good news. 

I finally have my bios back. I got information on this site: [http://www.linlap.com/fujitsu_lifebook_ah532?&#comment_7ae19c0f23cda94b44c75f4284beda30](http://www.linlap.com/fujitsu_lifebook_ah532?&#comment_7ae19c0f23cda94b44c75f4284beda30) where someone else had done it and I have added my own how-to there to expand the information (the posts aren't in date order for some reason I can't work out, but I am sure you will work it out). I won't bother reporting it all here as you can read it on that site if you want to. Basically the solution was a bios flash from within Linux.

I will mark the thread as solved, but really this is not a fix it is a workround,(I am pretty sure it will return if I reinstall Ubuntu another time) and it confirms that the bug affects many Linux users with this machine.

@YannBuntu
Thanks for that information, I haven't tried booting Ubuntu from the Manjaro menu, but I will when I have finished posting this. 

Now I have bios access back I can confirm there are no settings in there for switching secure boot on or off, the nearest I have is to set a bios password (which is NOT set).

NB The first thing I did was to change the boot order to something more sensible than having the hard disk first and usb last!

Edit. Yannbuntu, I can't answer your question about Manjaro grub because Ubuntu grub is the one on the mbr not Manjaro, they are not chainloaded, so the Ubuntu one is the only one I see.

---

### Post by YannBuntu on 2012-11-25
> **viking777 said:**
> you can read it on that site if you want to.

Thanks for having detailed the procedure, it will help other others.


> **viking777 said:**
> there are no settings in there for switching secure boot on or off

So probably this computer didn't have SecureBoot at all. When you bought it, did it have preinstalled Windows7 or Windows8 ?


> **viking777 said:**
> The first thing I did was to change the boot order to something more sensible than having the hard disk first and usb last!

Was HDD first by default when you bought it?

> **viking777 said:**
> I can't answer your question about Manjaro

No problem.

---

### Post by viking777 on 2012-11-27
> so probably this computer didn't have SecureBoot at all. When you bought it, did it have preinstalled Windows7 or Windows8 ?

Win7

> Was HDD first by default when you bought it?

Yes.

Thanks for your continued interest, let me know if I can help you any further.

---

### Post by YannBuntu on 2012-11-27
> **viking777 said:**
> Win7

ok, so I am 99% sure that there is no SecureBoot at all on your PC.



> **viking777 said:**
> Yes.

Strange default setting, but ok.


It's good that you found a workaround for this naughty issue.
Now let's wait and see on the Launchpad report, i hope that GRUB developers find a long-term solution...

---

### Post by directhex on 2012-11-28
> **YannBuntu said:**
> ok, so I am 99% sure that there is no SecureBoot at all on your PC.

Windows 7 does not support Secure Boot at all. It doesn't even fully support UEFI boot (Windows 7 x64 SP1+ supports it, as long as legacy video BIOS support is enabled)

---

### Post by baobab33 on 2012-12-09
> Here are my questions: If we install an OS with Secure Boot on do we get UEFI instead of BIOS? If so, then how does a user access the UEFI set up? Do we still have a BIOS that can be accessed by F2 or Del or whatever?


No, whatever you install as OS, the "BIOS CSM" (i.e. "legacy BIOS") or "UEFI" are memorized into a NVRAM somewhere in your motherboard.
So, you normaly have a UEFI mode activated at first, altogether with a preinstalled UEFI MS-Windows (7 or 8) and according the possibility offered by the manufacturer you may disable UEFI to CSM BIOS **directly from your OS** (Windows at least).

Be careful, this is what I did (I have a - europe only - P870-319 TOSHIBA laptop) and I am now stuck as there is absolutely no key taken into account from the keyboard at bootup (UEFI is supposed to be accessed ONLY through the OS for "security" reasons...) I suppose I am in CSM BIOS as I deactivated secured-boot and I also deactivated UEFI from Windows before rebooting. Though, it is still not accessible at bootup.

Hopefully I could boot from the UBUNTU CD and install it but I am now stuck as I cannot access back to the BIOS

If anyone knows something about **getting access** or **reactivate UEFI** from a boot CD (for example), many thanks in advance for your input (I actually have two different HDD, the original preinstalled with W8 which does not boot anymore, complains "NO UEFI AVAILABLE"... because partitioned as GPT and the present one on which Ubuntu runs, of course the traditional "MBR" not "GPT")

*Needless to say I firmly advise NOT to buy such laptop unless you want to waste ~ $1,000. I already lost an entire week asking the support (no reply yet) and I can only run Ubuntu. Moreover the keyboard is awfully cheap !*

---

### Post by oldfred on 2012-12-09
@baobab33
Better to have your own thread.

Post link to BootInfo. Are you Booting Ubuntu in BIOS, not UEFI? Best to have both systems in UEFI mode.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
Install in Ubuntu liveCD or USB or Full RepairCD with Boot-Repair (for newer computers) 
[http://sourceforge.net/p/boot-repair/home/Home/](http://sourceforge.net/p/boot-repair/home/Home/)
[https://help.ubuntu.com/community/UbuntuSecureRemix](https://help.ubuntu.com/community/UbuntuSecureRemix)

---

### Post by directhex on 2012-12-10
> **baobab33 said:**
> If anyone knows something about **getting access** or **reactivate UEFI** from a boot CD (for example), many thanks in advance for your input (I actually have two different HDD, the original preinstalled with W8 which does not boot anymore, complains "NO UEFI AVAILABLE"... because partitioned as GPT and the present one on which Ubuntu runs, of course the traditional "MBR" not "GPT")

Grub provided with Ubuntu installed as UEFI includes a "setup" option at the bottom of the GRUB menu. This launches your motherboard's UEFI setup, and can be used to get into UEFI setup on "fastboot" systems which skip the setup screen entirely when a valid OS is installed.

---

### Post by johanneslandin on 2013-01-23
Please relax everyone! UEFI may cause us all some headache for the moment but trust me, it does make computing safer and if you can login with administrator privileges in the windows system it is very possible to disable it.

1. I tried this with my Fujitsu AH532 and it worked: 
[[SOLVED] Disable UEFI, EFI from preinstalled Windows 8 computer - multix.org]("http://www.skrivmaskin.se/linux/artikel.php?id=112")

Please realize that the point with UEFI is to prevent alien users to run alien systems on your computer. UEFI force you to first login to the installed system to remove the security. ( With a unique BIOS password in every PC this could also be done, but "vogon" people dont set passwords for BIOS, do you even do that, and not many understand to keep factory set passwords safe. "Normal" people just run things! )

:popcorn: 
As a Wogon once said before firing on the president (who had kidnapped himself): "We are here for your protection". Please read "The Hitchhiker's Guide to the Galaxy", or at least see the movie, and you will understand how decisions are made in real life.

Sorry about by poor English.

---

### Post by timschumi on 2024-04-19
I've recently looked into fixing this issue, and came up with a consistent way of restoring the laptop to full operation.

The boot menu entries can be partially restored by bridging the "CL1_CL2" test point  that is located under or next to the RAM slots.
It may be required to have the laptop powered (or even powered on) while bridging the contacts for the test points to have any effect.
This brings back the  device-based boot menu entries, but does not yet restore access to the  BIOS Setup menu.
For that, a USB stick with [Fujitsu's BIOS update tool]("https://support.ts.fujitsu.com/")  (search by serial number to make sure you find the correct hardware revision) needs to be prepared, booted from, and run.
This restores most BIOS  settings to their default, including the missing BIOS Setup menu.

Alternatively, if the currently installed Linux system is still  bootable, one can use [this tool]("https://github.com/timschumi/ah532-biostools") to restore all entries  without having to go through a BIOS update and reset.
This works by manually  rewriting all broken EFI variables with their expected content.
Please do make note of the list of supported configurations and of the  disclaimer (and let me know in case the tool does or doesn't work on  some previously untested configuration).
In case you want to know more about this works, there is a [post explaining the underlying details]("https://blog.timschumi.net/2024/01/20/ah532-bios-investigation.html").

Lastly, a [workaround for the issue]("https://git.kernel.org/pub/scm/linux/kernel/git/torvalds/linux.git/commit/?id=f45812cc23fb74bef62d4eb8a69fe7218f4b9f2a") has been merged into the Linux  kernel, which should keep this from occurring on any new  installations.
This patch already ended up in the current installation  media for the Ubuntu 24.04 beta (which I have confirmed to be not affected), and it will presumably be included in  all installation media going forward.

---

