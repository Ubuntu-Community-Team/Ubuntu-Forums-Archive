---
title: "Dual boot Win10 + Ubuntu 20.04 but I can not find a way now to ever access ubuntu!"
date: 2022-07-11
forum: Installation &amp; Upgrades
---

### Post by crazybear on 2022-07-11
Please HELP! I should have asked for help long, long ago....and have been working on this and pulling out my hair for literally months. I have another computer, but now I must take that laptop on my travels and can only boot to Windows [which I use only 1% of the time]. Several things happened / I did - so relating all of them likely  will not help [and I can't remember all the fixes I've tried]. Both were on a smaller M.2 MVMe SSD that I cloned to a larger one. I also changed the SSID of both windows and Ubuntu partitions.
This is an EFI disk, but things can get confusing as my other computer is NOT and can NOT BE EFI and sometimes I use it to, for  example, made a boot drive or drive for some installation or boot repair, etc....and some [not all] programs state incorrectly that the laptop [Dell XPS 15 9550 with 64GB memory and good processor] is not EFI [I think because it was loaded onto a thumbdrive in BIOS mode...but don't know]. For a while I was ONLY able to access Ubuntu if I used Refind or SuperGrubBoot - now nothing works. The 'best' I can accomplish is to get a grub prompt or grub-rescue prompt or some prompt like them. I have tried all of the fixes on the internet, but to no avail. I have both the EFI partition and a separate Ubuntu boot partition, but neither works as it should - so Ubuntu now never boots. Despite the fact I had put over 2 years work into the 20.04, I was even willing to try to re-install it [not that I wanted to at all! - in fact want to avoid that at all costs], but no boot disk will load. I get the message 'out of memory' - followed by kernel panic and/or 'you must boot from the kernel first'. It can't be out of memory with 64GB. Can someone help me diagnose it. Boot-Repair fails every time - sometimes saying it had repaired it, sometimes saying it could not, sometimes claiming there was a conflict with EFI and BIOS I don't understand. The Win 10 I thought was EFI [but maybe not - I know nothing about Windows except it has so MANY small partitions in addition to the main one]. I post the last report from Boot Repair. it is long because I have a Ventoy disk [large] with every imaginable repair program and several different Ubuntu releases. It just adds clutter to the report, but does not confuse Boot-Repair, as I have also tried  it on a zip-drive alone with the same results. I leave on a trip soon on which I must work and all of my work is in  Ubuntu - not in Windows, which I hardly know how to navigate in and only use for the few programs that do not run in Ubuntu. Please some suggestions! Thanks in advance. If the laptop took two MVMe's I'd definitely have Win on one and Ubuntu on the other. Dual boot seems to always cause problems. I have never used it before. On my desktop they are on separate physical drives, so I am new at dual booting on one hard drive, let alone a SSD M.2 MVMe. HELP!!

---

### Post by Impavidus on 2022-07-11
So, it's a mess. You don't know what caused the mess and you can't tell us exactly what the mess looks like, aside from a cluttered boot-repair summary. I hate to be the bringer of bad news, but basically, you scrambled an egg, scrambled it the wrong way, and want help from us, who can't even see the egg, to unscramble the egg, so you can rescramble it the right way.

You could run boot-repair, right? Then you can boot from an external drive, provided you've got a good live disk. Create a good live disk, boot using that, make backups of any files that need backups, wipe the disk and perform a fresh install. Do it all in UEFI mode and use a GPT partitioned drive. It is possible to dual boot Ubuntu and Windows 10 on a single hard drive, but a computer with 64 GB memory should be capable of running Windows in a virtual machine too.

The kernel panic while booting a live disk could indicate a broken live disk, a computer with specs too low for the live disk, a live disk with a kernel too old for your hardware or broken hardware. I suggest a fresh 22.04 LTS live disk.

We can help you with a fresh install. Any attempt to save your current system will likely end in frustration. Even if we can manage to make it boot once, it might break again at the next update. It would be like a car held together with duct tape. You want a reliable, clean system.

---

### Post by DuckHook on 2022-07-11
> **Impavidus said:**
> So, it's a mess. You don't know what caused the mess and you can't tell us exactly what the mess looks like, aside from a cluttered boot-repair summary. I hate to be the bringer of bad news, but basically, you scrambled an egg, scrambled it the wrong way, and want help from us, who can't even see the egg, to unscramble the egg, so you can rescramble it the right way…

…We can help you with a fresh install. Any attempt to save your current system will likely end in frustration. Even if we can manage to make it boot once, it might break again at the next update. It would be like a car held together with duct tape. You want a reliable, clean system.
+1

@crazybear

Though unsparingly candid, Impavidus is right—it makes little sense to try salvaging this situation. You will be better off backing up all of your important data, then reinstalling from scratch, this time taking care to keep your base system as close to its default state as you can.

In future, when attempting OS repairs/tinkering, it is always advisable to take the time to log your steps. I do this by opening a simple text file and typing each step as I go along, so reversing them is straightforward.

Moreover, if you use Windows only 1% of the time, then consider simplifying your system by running Windows in a VM and dedicating your bare metal solely to Linux. Your system will be more robust and less brittle if you get rid of Windows and don't have to accommodate its selfish, system&#8209;hogging behaviour.

---

### Post by oldfred on 2022-07-11
I am having trouble reading .doc file. 
Better to just post the link to the summary report.

It looks like you have many UEFI entries, most can be & should be deleted. A reinstall will not fix that.
# from liveDVD or flash booted in UEFI mode and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:, with Ubuntu you need sudo, others must be at root. some need all 4 hex chars, others only need significant digits
sudo efibootmgr -b XXXX -B
man efibootmgr

Years ago there were a few systems where if UEFI memory was half full, it locked up system & it had to be returned to vendor to fix. They originally blamed Linux, but found with Windows you could also do it, so it was a vendor issue. And the UEFI memory was only half full. 
So best not to have too many entries in UEFI.

---

### Post by crazybear on 2022-07-14
I was disappointed in  most of the replies. I see total sense in trying to save 'the situation' [SSD with Win10 and Ubuntu 22.04]. I know it is easier for you experts to tell others to 'just start over', but it is for me months of work to get it back to where it is now. Windows works fine. As mentioned, I can not get Ubuntu to boot, but I think the solution while hard to determine, will be EASY to repair once determined. Some command line scripts to determine the problem would be appreciated. I know almost nothing of EFI and how it works. It is new to me, as I have been using a BIOS system until I bought this laptop.   I don't have time to mess around with trying to rebuild both Windows and Ubuntu. I actually once did a new install of the Ubuntu quite some time ago, but the situation remained as it is and as it was. Strange to me, boot-repair says repair successful, but it is  not. It also reports problems! I don't know how to proceed. I have reduced the number of EFI entries [none of which I put in on purpose but Win and Ubuntu] - showing how little I understand EFI. I give the URL, but know they don't stay up too long. It is [https://paste.ubuntu.com/p/y4TGWZGWxq/](https://paste.ubuntu.com/p/y4TGWZGWxq/)  Once I saw some posts that 22.04 had such large kernels that they caused problems if some extra space was not allowed, leading to 'out of memory' reports...but this is unclear and not much on internet.

By the way, at this point no installation drive with Ubuntu will work. I get 'out of memory' that then leads to a kernel panic. I can not be out or memory.  The laptop has 64GB. What is leading to the kernel panic and strange report of 'out of memory'? Windows has plenty of memory, and Ubuntu uses less - no? 

What is going on in this statement and does it show a problem? "
 Boot file info:      Grub2 (v2.00) in the file 
                       /0-super_grub2_disk_hybrid_2.04s1.iso looks at sector 
                       0 of the same hard drive for core.img, but core.img 
                       can not be found at this location. Grub2 (v2.00) in 
                       the file /0-ubuntu-22.04-desktop-amd64.iso looks at 
                       sector 0 of the same hard drive for core.img, but 
                       core.img can not be found at this location. Grub2 
                       (v2.00) in the file /redorescue-4.0.0.iso looks at 
                       sector 0 of the same hard drive for core.img, but 
                       core.img can not be found at this location."
Are the core.img supposed to be at that location?
Any help appreciated. Thanks in advance.

Some possible leads. When it goes to kernel panic, the following are listed:

RAID detected, if you don't use raid, use raid=noautodetect [[I don't use RAID - and how can one with only one drive!?!]
VFS: Cannot open root device "UUID=........" or unknown-block(0,0): error -6
Please append a correct "root=" boot option; here are the available partitions: (then is does not list any available partitions, but I know which contains Ubuntu)
Not tainted 5.15.13-051513-generic 
call Trace:
.........
end Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

---

### Post by oldfred on 2022-07-14
You still have a lot of UEFI boot entries.
Out of memory may be the UEFI is full? Otherwise not sure what it is referring to.

Did you change UEFI setting for drives from RAID or Intel RST to AHCI? And first install AHCI drivers into Windows or else it will not work with the AHCI setting? And update may also have reset it.

If Windows or Linux firmware updater did UEFI update, that may reset some settings back to defaults. You then have to go back into UEFI and change settings again. My motherboards are not in fwupdate data base, so I get no auto updates. But when system was newer several years ago, I and manually did updates I had to redo multiples settings. I had to keep a list, as I could not remember all of them. Some were required & some optional.

At some point you reinstalled grub in BIOS boot mode. That installed grub to gpt's protective MBR. With UEFI the only purpose of the protective MBR is to have one partition table entry saying drive is gpt, so old partition tools (almost none now) would see drive as partitioned and would try to partition drive, damaging it. With MBR, it then is possible to install the old BIOS boot version of grub on a gpt partitioned drive, if you also have a bios_grub partition. You also show the bios_grub partition.
Since you have UEFI system, UEFI install of Windows, you should only boot system in UEFI mode. The old incorrect versions of grub in BIOS mode, just will not be used. It can be erased, but may be more dangerous to do as you have to use dd, which is known as data destroyer. Any typo when running it can totally damage system.

You should have good backups. Then all the effort you have put in configuring your system would not be wasted. Windows seems to use a image backup, but since Ubuntu can be easily reinstalled, you do not need to backup system, but back up your data & any settings you change. If your backup includes a list of installed applications, it makes it easy to reinstall all the apps you manually added. User settings are all in /home, only if you changed some system settings may you want those from /etc. I edit several grub files, but just copy into /home, so I do not backup /etc as some suggest.

---

### Post by Impavidus on 2022-07-15
Reinstalling Ubuntu, reinstalling all applications and reconfiguring it all shouldn't take more than a day. If you prepared for it by keeping the right backups and you have a decent internet connection, it should take no more than an hour.

When somebody comes here with a problem and can show us what's going on, we can usually solve it. If you had come here at the first sign of trouble, we could probably have solved it. But on top of your problem, you have a pile of attempted fixes and a cluttered boot-repair summary. I can't tell which bits belong to the original configuration and which bits belong to attempted fixes. I cannot guess which fragments of your system belong to which layer of fixes. So I stand by my original suggestion: make sure you've got backups of your important files and reinstall.

Boot-repair can fix some problems, but not all. It isn't very smart. That's why it can create a boot-info summary, so that the people here, who are smarter than boot-repair, can learn more about the problem and attempt a fix. But this is just too much of a mess.

So, can you tell a bit more about the specs of this computer? Which version of Ubuntu have you used for the live disk? Have you verified the integrity of the live disk image? What tool to create the live usb? Sometimes, some settings don't work on all computers. A simple clone (without persistence) is most reliable. That's to make sure the live disk is working. Failure to boot it may also result from a kernel incompatible with your hardware or broken hardware. That Windows does work doesn't prove the hardware is OK. Windows memory management is different, so it might never attempt to use a broken part of RAM that causes a crash in Ubuntu.

---

### Post by crazybear on 2022-07-18
> **Impavidus said:**
> Reinstalling Ubuntu, reinstalling all applications and reconfiguring it all shouldn't take more than a day. If you prepared for it by keeping the right backups and you have a decent internet connection, it should take no more than an hour.

.......

So, can you tell a bit more about the specs of this computer? Which version of Ubuntu have you used for the live disk? Have you verified the integrity of the live disk image? What tool to create the live usb? Sometimes, some settings don't work on all computers. A simple clone (without persistence) is most reliable. That's to make sure the live disk is working. Failure to boot it may also result from a kernel incompatible with your hardware or broken hardware. That Windows does work doesn't prove the hardware is OK. Windows memory management is different, so it might never attempt to use a broken part of RAM that causes a crash in Ubuntu.

I had to make some very difficult [for me] changes to the system in order to control the laptop fans and a few other things. It is a Dell XPS 15 1550 with an i7CPU, 64GB of absolutely new G. Skill memory. As I bought this used from someone and having moved the original small MVMe SSD to a larger one, that already has Windows saying it now is not genuine and not activated - even though Win10 comes OEM with this computer [a matter I will try to fix later, but makes me worry, as I have no installation media for Windows other than using something from some p-bay type place.
I have used two or three differently generated install disks. One is using Ventoy [a program that allows as many .iso as can fit to operate via a menu]. I also tried on another USB zip drive using rufus and one using Startup Disk Creator [on the BIOS desktop] with just one ISO. They all were Ubuntu 20.04 - and I tried 22.04 too. All [and MANY other programs, but not all, I tried to fix system with] said 'out of memory' and then went to some kernel panic. I don't know what 'a clone without persistence' would mean, sorry....but I don't think it is the manner of how the install media is made.

---

### Post by crazybear on 2022-07-18
> **oldfred said:**
> You still have a lot of UEFI boot entries.
Out of memory may be the UEFI is full? Otherwise not sure what it is referring to.

Did you change UEFI setting for drives from RAID or Intel RST to AHCI? And first install AHCI drivers into Windows or else it will not work with the AHCI setting? And update may also have reset it.
[COLOR=#0000ff]
_*<< I have never used RAID in my life and how can one with only one disk in the laptop? It is set and always has been set at AHCI. It works fine for over a year and half, so assume it doesn't need drivers. No updates, but I migrated to a new drive, which windows doesn't like and also seemed to screw up Ubuntu somehow. I HATE dual boots and on my desktop never use them. I have a separate drive for every OS. This 'fancy' laptop has only one MVMe drive allowed - nothing else except external.>>*_[/COLOR]

If Windows or Linux firmware updater did UEFI update, that may reset some settings back to defaults. You then have to go back into UEFI and change settings again. My motherboards are not in fwupdate data base, so I get no auto updates. But when system was newer several years ago, I and manually did updates I had to redo multiples settings. I had to keep a list, as I could not remember all of them. Some were required & some optional.

[COLOR=#0000ff]_*<< I know nothing about UEFI updates. I know nothing about how to mess inside of UEFI settings either, nor what they should be.>>*_[/COLOR]

At some point you reinstalled grub in BIOS boot mode. That installed grub to gpt's protective MBR. With UEFI the only purpose of the protective MBR is to have one partition table entry saying drive is gpt, so old partition tools (almost none now) would see drive as partitioned and would try to partition drive, damaging it. With MBR, it then is possible to install the old BIOS boot version of grub on a gpt partitioned drive, if you also have a bios_grub partition. You also show the bios_grub partition.
Since you have UEFI system, UEFI install of Windows, you should only boot system in UEFI mode. The old incorrect versions of grub in BIOS mode, just will not be used. It can be erased, but may be more dangerous to do as you have to use dd, which is known as data destroyer. Any typo when running it can totally damage system.

[COLOR=#0000ff][U][I]<< I never intentionally installed grub in BIOS boot mode - the laptop has UEFI 'BIOS' - My desktop is old and can only have BIOS 'BIOS.. Yes, I was trying to set up disks that could work on both BIOS and UEFI systems, but seem to have built one that doesn't much work on either..... >>
[/I][/U][/COLOR]
You should have good backups. Then all the effort you have put in configuring your system would not be wasted. Windows seems to use a image backup, but since Ubuntu can be easily reinstalled, you do not need to backup system, but back up your data & any settings you change. If your backup includes a list of installed applications, it makes it easy to reinstall all the apps you manually added. User settings are all in /home, only if you changed some system settings may you want those from /etc. I edit several grub files, but just copy into /home, so I do not backup /etc as some suggest.

[COLOR=#0000ff]_*The last time I tried a 'simple re-install it took me a very very long time to get back to where I was. I hear all you old-hands-with Ubuntu that it takes an hour....but NOT for me...weeks last time.*_[/COLOR]

---

### Post by oldfred on 2022-07-18
Please only refer to Windows as Windows. Edited the others.

Did you houseclean some of the UEFI entries?

---

### Post by crazybear on 2022-07-19
> **oldfred said:**
> Please only refer to Windows as Windows. Edited the others.

Did you houseclean some of the UEFI entries?

Yes, but as I said, I don't understand UEFI and what is needed or not in it. It seems that any boot attempt is permanently kept, so every time I use a new boot or repair program on a USB to boot or repair, it is stored. I would think it  should only contain those I specify as part of the 'system'....I found online a way to delete entries and deleted about 80%  of them I knew didn't belong there. The Ventoy removable disk has about 25 iso's on it. I saw all of them listed, even if I didn't use them - again making no sense. I removed those I did not use and some I used that didn't seem to make any sense being there.

By the way, on the 'out of memory' events, I am subscribed to a bug and just got this today [attached]. Others are having the same problem if they upgraded from  20.04 to 22.04 as I did. Why it would apply to new install media doesn't make sense to me...but....

---

### Post by oldfred on 2022-07-19
that is an older bug with kernel 5.2 and either 19.04 or 19.10. 
I would not think it would then apply to either 20.04 or 22.04.

---

### Post by crazybear on 2022-08-15
I have been fighting with the MVMe disk all this time [without any real help from the Forum, sadly - I only 'sort of understand how it went....I'm under duress in my life, so my computer is also....]. I could NOT even reinstall any version of Ubuntu.
Anyhow, I finally found a way to get into the Ubuntu 22.04! [on my own]...but there are still a few problems [that may or may not have been causing the problems past - but certainly are causing problems now].
They seem solveable, and I think in the distant past I have had the same problem, but do not remember how to go about it...nor can I find a coherent and applicable answer on internet that doesn't lead into the endless loop I seem to get in terminal.

Immediately after celebrating finding a way into my Ubuntu, I [having been kept out for months!] updated it...I had a HUGE list of updates and I think it tripped itself up and now wants me to repair it.
It updated [rather tried to!] the image to Linux-image-5.15.0-41-generic, BUT that failed with the following in terminal: [see attachment]

As far as the message to install OpenSSL_1_1_1l, I can not now due to problem above stopping anything being installed or uninstalled!...

It shows a number of things I tried and it goes around and around. I have tried to use synaptic to fix broken files - doesn't work. I have tried to delete the ? half installed new image - it doesn't work. I have tried the suggested 'apt --fix-broken-install and that doesn't work. However, it seems that the real problem perhaps is the first thing I did before any updating...thinking of the problem with the dual boot I was going to do first 'update-grub' - but it failed with errors that lead me in circle I do not know how to get out of, but think if I can, all can be fixed with the Ubuntu AND the dual boot~! Any suggestions, and please go easy on me...I'm stressed out. My life is on the line and falling apart. I need a computer to keep it maybe going.... Thanks in advance!!!!

---

### Post by oldfred on 2022-08-15
Please copy & paste the pastebin link to the Bootinfo summary report ( do not post report), do not run the auto fix till reviewed.Lets see details, use ppa version with your USB installer (2nd option) or any working install,  not Boot-Repair ISO
 [https://help.ubuntu.com/community/Boot-Repair%20&](https://help.ubuntu.com/community/Boot-Repair%20&) 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

You are showing grub proxy files.
Those are from grub customizier, a gui app that replaces grub with its own files.
Often better to just modify grub manually.

I was trying to help another user and they just could not get rid of the proxy files.
I thought a total reinstall of grub over wrote them, but it seemed to leave them and then double entries on most things.
You may need to totally erase/backup /etc/grub.d folder & reinstall grub.

---

### Post by crazybear on 2022-08-15
This also came into my email today....I too have a Dell XPS! I too updated to Ubuntu 22.04.....I'm not sure what he means by the first 'fix' to get to Modules=dep.

---

