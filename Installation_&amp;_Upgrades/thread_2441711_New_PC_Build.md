---
title: "New PC Build"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by ivatt1815 on 2020-04-26
I have a new PC on which I intend to dual boot with W10 and Ubuntu.

Everything I have read so far recommends doing a fresh install of Ubuntu on the new system rather than copying over the old. The fresh install will also create the grub boot loader.

My existing Ubuntu includes various settings, under I think rules, to make my Saitek hardware for x-plane 11 work correctly. If I do a fresh install how can I copy over the settings etc. in my existing Ubuntu so that the new install works as before? Do I need to install the same version on the new as on the old?

Secondly, I would prefer to have W10 as my first choice on boot, how do I change grub to reflect this?

Thanks

---

### Post by TheFu on 2020-04-26
I don't dual boot. Cannot help with that.

User settings are located in your HOME directory. IF you copy that over, maintaining permissions, then the new OS will see them.  Cannot say those settings will be compatible with the new OS, especially new GUI programs. That's the risk.

System settings are located in a few different places. The system admin should have kept track of all modifications to the system so those would be known and easily backed up.  Most system settings are in /etc/, but only those specific files that have been manually modified should be compared to the files on the new install, then merged. DO NOT JUST COPY ALL FILES from /etc/ OVER.  This can lead to a system that will not boot.

All 3rd party software that is installed onto a new system (or fresh OS install), is a risk.

You don't mention which release of Ubuntu you hope to install. Last week, 20.04 and all the flavors was released.  Many 3rd party software teams haven't migrated their code to support it yet. You'll want to check for the top 20 software you plan to run to see when they expect to support the release.

Of course, you can just pull the HDD from the old system and put it into the new system and almost everything should be fine provided most of the hardware is generic in the new machine.  The major problem will be with any proprietary GPU drivers. Those need to be disabled before the move.  I've done successfully this a number of times.

If you search for "what to backup" in these forums, hopefully, there will be threads that say where the different stuff is located.

---

### Post by oldfred on 2020-04-26
If a new system, it will be UEFI as all systems since 2012 are UEFI. Microsoft required vendors to install Windows 8 in UEFI boot mode to gpt partitioned drives.

Is old system, UEFI or BIOS?

You want to be sure to install both Windows & Ubuntu in UEFI boot mode and use gpt partitioning.
Systems still have old BIOS mode as option, actually CSM. 
CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode, only available with secure boot off.

You can set UEFI to boot Windows first and use UEFI one time boot key often f12 or f10, check manual to choose Ubuntu if you only want it occasionally. Or you can change boot order in grub so it boots Windows first. 
Grub only boots working Windows, so if Windows turns fast start up back on, which it will do with some updates, then grub will not boot it and you have to use UEFI one time boot key. Or if Windows is not shutdown correctly or otherwise needs chkdsk, grub will not boot it.

More info on UEFI install in link in my signature.

Shows installer with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 10 screens or similar to Windows 8
[https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi](https://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-10-with-uefi)

---

### Post by ivatt1815 on 2020-04-28
Thanks **OLDFRED** for the reply.I am in the process of rading the various links in your signature. Also thanks to **TheFu**.

My current Ubuntu build is 18.04.03 LTS and my BIOS shows as Legacy.

My "plan" is/was to do a fresh install of W10 on one partition of the news ssd and then once I have everything working on that OK to install the **SAME** Ubuntu build on the other partition of the SSD. This seemed to the simplest option but perhaps not the correct route to take e.g should I install the latest build.

The only software I currently run on Ubuntu is x-plane 11 and although I could reinstall x-plane 11 I would lose the tweaks that have been done to make x-plane recogise my Saitek hardware. I still have the  threads from the x-plane forum on the subject so if push came to shove I could work my way through them to make the changes on the new install but that would not be ideal. To the best of my memory, without reading through them again (there are 4 pages) the changes were made to the rules folder.

As I have said on other threads I have posted I am very much a novice when it comes to Ubuntu which makes life difficult when trying to work out what I need to backup and transfer across. Obviously the hardware and the GPU on my new build will be completely different to my current system.

At the moment I am looking at Ubuntu backup software to see which one would be best for me to use, given my lack of experience. I don't want to do a complete back up just those parts of Ubuntu that I need to keep the x-plane chnages and which I can then copy back.

Once Ubuntu is working correctly I will introduce a regular back up regime. With Windows I have always used Macrium Reflect to make an image of the system, just in case, and I have then updated this from time to time as needs demand. This has saved me on more than one occassion.

---

### Post by oldfred on 2020-04-28
I do not know x-plane.
But looked at one site on installing and it mentioned 32 bit drivers.

Linux has just about obsoleted 32 bit. 
If it needs 32 bit drivers, then you may be better with 18.04 as it is more & more difficult to find anything 32 bit.

---

