---
title: "Grub, UEFI, ThinkPad x120e"
date: 2011-08-31
forum: Installation &amp; Upgrades
---

### Post by RMOP on 2011-08-31
I'm in the process of setting up my 8gb dual-core ThinkPad x120e with Ubuntu 10.10, an O/S which I use on other machines. So far, I've managed a decently working install to my 16gb Class 4 (slow, get a Class 10!) micro SD.

I am keeping Windows 7 Pro 64-bit on this system (no apologies to the purists), and want to install Ubuntu to my HD w/o trashing my nicely-working Windows install.

I've read about 20 pages of the extended ThinkPad x120e discussion in this forum, and am still reading. Lots of good if highly fragmented tips there, which I've employed to get WiFi working.

I'd appreciate some *experience-based* advice.

1) Can I do a regular CD-based install of 10.10 and expect both Ubuntu & Windows to play nicely?

2) What, if any, implications does UEFI have for my plans?

3) Does GRUB care about BIOS/UEFI distinctions? Does Ubuntu? Does GRUB version matter?

4) Any caveats regarding the choice of 32-bit vs 64-bit Ubuntu?

5) Should I re-consider Natty? I did an install on a markedly less capable machine (Toshiba NB-205) and HATED the default interface and the MISERABLE performance. If I can easily get the Maverick interface, I'd be happy to consider Natty on my new machine.

I'm committed to the ThinkPad platform, financially and otherwise. It is a very nice machine. I will be appreciative of any practical advice on getting a capable Ubuntu dual-boot install up and running on this PC.

Many thanks.

---

### Post by dino99 on 2011-08-31
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

[http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now](http://blog.pault.ag/post/3107062816/why-64-bit-computing-is-really-dumb-right-now)

---

### Post by oldfred on 2011-08-31
I disagree with Dino on 64bit. I have been using it for 2 years on two computers. Even my older portable with only 1.5GB of RAM works with 64bit. Only if you have one of very few now applications that is 32bit only should you even consider 32bit.

[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)
Ubuntu 32-bit, 32-bit PAE, 64-bit Kernel Benchmarks Dec 2009
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_32_pae&num=1)
Essentially says if you can use the 64bit kernel you should.
[http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_natty_pae64&num=1)

grub EFI -skodabenz
1. Most of the modern UEFI systems come with GPT instead of MBR.
2. GRUB needs to be installed to the ESP (EFI SYSTEM PARTITION). The ESP has to be the first partition in the drive, with file system of a FAT variant, and it has to be larger then 100 MiB. Ubuntu mounts the ESP by default in /boot/efi .
3. After you install grub in the ESP, you need to make a boot enrty for it using efibootmgr, or you could launch it with the UEFI shell

Ubuntu does not care, but grub2 really does care about BIOS or UEFI. You will want the very newest version of grub2. Some suggest just backing up the windows efi partition, then install grub2 as it currently overwrites the windows efi partition. Or install Ubuntu first then windows. But there still seems to be some issue about partition format.
[http://www.rodsbooks.com/bios2uefi/](http://www.rodsbooks.com/bios2uefi/)
Updates - Avidanborisov created compile script
[http://ubuntuforums.org/showthread.php?t=1772310](http://ubuntuforums.org/showthread.php?t=1772310)
UEFI issues srs5694 post #58  Solutioin see above
[http://ubuntuforums.org/showthread.php?t=1719851&page=6](http://ubuntuforums.org/showthread.php?t=1719851&page=6)
Grub2 efi info ArchLinux
[https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems](https://wiki.archlinux.org/index.php/GRUB2#Bootloader_Installation_for_UEFI_systems)
Has chainload window efi grub entry:
[https://help.ubuntu.com/community/UEFIBooting](https://help.ubuntu.com/community/UEFIBooting)

---

### Post by YesWeCan on 2011-09-01
How about posting the output of sudo sfdisk -luS so we can see if you are currently using GPT or not?

---

### Post by RMOP on 2011-09-01
Thanks, all. I'd seen some of the links, but can't say that I found them particularly encouraging. I'm not booted to Ubuntu now, so will check in a bit regarding the sfdisk readout.

After further poking around, I'm not currently willing to risk trashing my W7 install so am going to approach this rather indirectly. The various suggestions in the links and other sites I've visited seem way beyond my level of expertise and patience.
[B]
Might THIS be a work-around?[/B]

1) Install Ubuntu as usual to its own partitions, but place GRUB not on the HD at all, but on an SD card. This isn't necessarily a bad thing, as my microSD card in its SanDisk USB reader is rather portable, and having GRUB there adds a clunky but effective layer of security to the Ubuntu part of the machine.

2) Once I've gotten the system fully operational w WiFi, graphics driver and the like, my thought is to then install GRUB to the Ubuntu partition, keeping well away from the Windows junk.

3) Coerce the Windows boot manager into seeing the Ubuntu install and offering it as a choice on its menu.

[http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3](http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3)

4) If Windows boot manager can't haul the water, I'll still have my microSD GRUB for backup. And, if my incoming Class 10 microSD card is fast enough, I might just chuck the whole install onto the card. BUT, I'd rather like to take advantage of my HD and get a real dual boot system.

*Now if I can snatch the ThinkPad back from my wife... She using it for the first time, and loves it.*

More soon. Thanks again.

---

### Post by joris1977 on 2011-09-02
The UEFI stuff is not really easy to solve...

I recently bought a x120e and want to dual boot win 7 and ubuntu. I will use ubuntu mostly, but need  windows for stuff like Tomtom updates and nokia ovi (phone). 

For some reason I just can't get ubuntu installed because of the UEFI issue. Live usb and install work ok, but after install ubuntu will not reboot, because grub does not start. Wubi seems to be the only working option, it works, but I don't really like it because it gives me a virtual partition of Ubuntu. 

It would be really helpful if there is a step for step guide on installing dual boot on a UEFI bios/motherboard. The UEFI boot community wiki doesn't really make it look very easy to do. (although I am going to give it another try this evening...)

---

### Post by YesWeCan on 2011-09-02
> **RMOP said:**
> 
Might THIS be a work-around?[/B]

1) Install Ubuntu as usual to its own partitions, but place GRUB not on the HD at all, but on an SD card. This isn't necessarily a bad thing, as my microSD card in its SanDisk USB reader is rather portable, and having GRUB there adds a clunky but effective layer of security to the Ubuntu part of the machine.

2) Once I've gotten the system fully operational w WiFi, graphics driver and the like, my thought is to then install GRUB to the Ubuntu partition, keeping well away from the Windows junk.

3) Coerce the Windows boot manager into seeing the Ubuntu install and offering it as a choice on its menu.

[http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3](http://oreilly.com/linux/archive/dual-boot-laptop.html?page=3)

4) If Windows boot manager can't haul the water, I'll still have my microSD GRUB for backup. And, if my incoming Class 10 microSD card is fast enough, I might just chuck the whole install onto the card. BUT, I'd rather like to take advantage of my HD and get a real dual boot system.

*Now if I can snatch the ThinkPad back from my wife... She using it for the first time, and loves it.*

More soon. Thanks again.
Need to see your sfdisk output but if it is MBR I'd suggest you create an extended partition and make all Ubuntu partitions logical. Install Grub to a low-profile USB stick (so it can be left plugged in all the time) and boot off that for ever more.

---

### Post by RMOP on 2011-09-02
Output follows below. The USB GRUB install would be easiest. Not elegant, but workable. Is there experiential reason to think I could not make the Windows BM --> GRUB bit work? 

When I reflect on the security advantage of booting from a USB device, I realize it's minimal. All of my data for use w Ubuntu will be shared with Windows on an NTFS drive. My real security is keeping physical control of my machine at all times, which is not really that difficult.

myname@MYBOX:~$ sudo sfdisk -luS
[sudo] password for myname:

Disk /dev/sda: 38913 cylinders, 255 heads, 63 sectors/track
Warning: extended partition does not start at a cylinder boundary.
DOS and Linux will interpret the contents differently.
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sda1   *      2048   2459647    2457600   7  HPFS/NTFS
/dev/sda2       2459648 399859711  397400064   7  HPFS/NTFS
/dev/sda3     399859712 604659711  204800000   f  W95 Ext'd (LBA)
/dev/sda4     604659712 625139711   20480000   7  HPFS/NTFS
/dev/sda5     399861760 604659711  204797952   7  HPFS/NTFS

Disk /dev/sdb: 1949 cylinders, 255 heads, 63 sectors/track
Units = sectors of 512 bytes, counting from 0

   Device Boot    Start       End   #sectors  Id  System
/dev/sdb1      20482875  21511034    1028160  82  Linux swap / Solaris
/dev/sdb2      21511035  31310684    9799650   b  W95 FAT32
/dev/sdb3   *        63  20482874   20482812  83  Linux
/dev/sdb4             0         -          0   0  Empty
MyName@MYBOX:~$

---

### Post by oldfred on 2011-09-02
You are not using UEFI, but BIOS. New systems with UEFI also have BIOS mode. Your windows then installed just like any computer. If you had used UEFI with windows you also would have gpt partitions and the first partition would be the efi partition.

You then just have a standard dual boot with windows install. Grub2's boot loader can be installed to the MBR and you then can choose to boot Ubuntu or Windows. A few running proprietary apps with DRM or some Windows virus checkers that think grub is a virus have issues with grub2's boot loader. They often use Neosmarts boot loader. I have never used it but a few here say it works. Others find grub2 works well also.

[http://neosmart.net/blog/2010/welcome-to-easybcd-2/](http://neosmart.net/blog/2010/welcome-to-easybcd-2/)

---

### Post by YesWeCan on 2011-09-02
You are using MBR format and you already have an extended primary partition so that makes everything relatively easy.

> **RMOP said:**
> Output follows below. The USB GRUB install would be easiest. Not elegant, but workable. Is there experiential reason to think I could not make the Windows BM --> GRUB bit work?
Yes you can. It is just a little fiddly because the Ubuntu installer and Grub are not designed to boot from a partition. Instead, they hijack your MBR and this is what causes OS conflicts.

There are several ways to get around this to make Ubuntu MBR compliant. It's just that you intimated you wanted to keep things pretty simple and the simplest solution is to avoid the problem by using a USB stick.

Just this week I discovered a fairly simple way to keep everything linux out of harms way inside your extended partition and allow you to add Ubuntu to your Windows boot manager or to boot it directly by setting the right boot flag in your MBR.

---

### Post by RMOP on 2011-09-03
Ok. Thanks, all. If I understand this, I can install Ubuntu along side Windows just like I've done in the past, and put Grub OR Grub 2 on the MBR and all should work. I've always used Grub Legacy. No experience w Grub 2.

---

### Post by joris1977 on 2011-09-03
> **RMOP said:**
> Ok. Thanks, all. If I understand this, I can install Ubuntu along side Windows just like I've done in the past, and put Grub OR Grub 2 on the MBR and all should work. 

I am probably just an idiot, but as I wrote earlier in this thread,on my x120e I cannot  install ubuntu (natty) along side windows just like I always did a 100 times in the past. Install will go fine but grub will not start after installation. 


Maybe the usb/sd card way you suggested in this thread will work and maybe I will try it as a last resort. But I would very much prefer to be able to run ubuntu without the need for an extra usb/sd card...

If someone would be able to write down some instructions on how to get ubuntu running on x120e without removing and reinstalling windows I would be very thankfull!

---

### Post by walt.smith1960 on 2011-09-03
I use a paid/shareware option which makes both Windows and Linux or any other O.S. think they're the only O.S. installed so no problems or conflicts with GRUB.  I don't know or if this solution would work with EFI/UEFI/GPT because it relies on BIOS manipulation but I think that doesn't come into play until the drive exceeds 2TB or so.  Google "Terabyteunlimited+BootitBM" for what works for me.  The caveat is to put GRUB in the Linux partition, SDA1 or what ever, not the default SDA or Windows won't show up or boot.  I don't have any stake in this company or software but it saves the angst of dealing with GRUB and Windows boot managers, 4 primary partitions limitation and the rest.

---

### Post by Hakunka-Matata on 2011-09-03
> **joris1977 said:**
> I am probably just an idiot, but as I wrote earlier in this thread,on my x120e I cannot  install ubuntu (natty) along side windows just like I always did a 100 times in the past. Install will go fine but[COLOR=Red] grub will not start after installation[/COLOR]. 


Maybe the usb/sd card way you suggested in this thread will work and maybe I will try it as a last resort. But I would very much prefer to be able to run ubuntu without the need for an extra usb/sd card...

If someone would be able to write down some instructions on how to get ubuntu running on x120e without removing and reinstalling windows I would be very thankfull!


[LIST]
[*] On first boot after installation?
[*]Is that where grub stalls (apparently)?
[*] Is it a video driver issue?
[/LIST]

---

### Post by joris1977 on 2011-09-03
Thanks for your interest in the problem Hakunka-Matata. 

> **Hakunka-Matata said:**
> [LIST]
[*] On first boot after installation? 

Yes on first boot after installation

> **Hakunka-Matata said:**
> 
[*]Is that where grub stalls (apparently)?

Grub just doesn't start only the windows bootloader that starts windows 7

> **Hakunka-Matata said:**
> 
[*] Is it a video driver issue? 

No I don't believe this is a video driver issue. The live-usb works very well, without any proprietary amd driver.

[/LIST]

---

### Post by Hakunka-Matata on 2011-09-03
> **joris1977 said:**
> Thanks for your interest in the problem Hakunka-Matata. 



Yes on first boot after installation



Grub just doesn't start only the windows bootloader that starts windows 7



[COLOR=Red]No I don't believe this is a video driver issue. The live-usb works very well, without any proprietary amd driver.[/COLOR]
[/LIST]


LiveCD uses different video drivers than the installed OS.  The first boot after installation is where the problem (if it's going to present) shows itself.

Download and run (from live cd if necessary), the boot_info_script package and post the resulting RESULTS.txt file into a reply, wrapped in code tags please

---

### Post by RMOP on 2011-09-03
> **joris1977 said:**
> I am probably just an idiot, but as I wrote earlier in this thread,on my x120e I cannot  install ubuntu (natty) along side windows just like I always did a 100 times in the past... 

There are serious reasons for doubting your idiocy. The 100 past successes among them. Your experience is what gives me pause. It sound so like *it should just work, and it doesn't.*

Once I've gotten around to imaging my current drive to DVD, I'll probably suck it up and dive in and hope for the best. But I sure want a way out of the woods if the thing tanks.

Agreed, the SD Card is less than satisfying, but I'll probably try it first as well.

I just did, BTW, go into my setup and disabled UEFI so that Legacy Only is set. It didn't affect Windows at all, so I'm convinced that UEFI is not in play, as already pointed out in this thread. Don't know if that will matter, but shouldn't hurt. Don't know if you tried that or not.

---

### Post by Hakunka-Matata on 2011-09-03
@RMOP"
apologies for posting post# 16, I usually don't respond to anyone except the OP, but I missed that one.

---

### Post by joris1977 on 2011-09-03
> **Hakunka-Matata said:**
> @RMOP"
apologies for posting post# 16, I usually don't respond to anyone except the OP, but I missed that one.

Sorry, I really didn't mean to hijack this thread. I found this thread while searching for a solution on this forum to get ubuntu to boot on a dual boot with a x120e. I was warning the OP that I was having problems, that I could not get solved and hoped someone more experienced than me would be so kind to post some clear howto install ubuntu on a thinkpad x120e  instructions. That would help the OP, it would help me and probably some other ubuntu users

I'm actually amazed that I cannot find these instructions somewhere since there seem to be a lot of people running linux on this (very nice) netbook.    

I can start a new thread if you or the OP think that is more appropriate, but I would have to name it almost similar as this one... 

For what it is worth: I ran the boot_info_script from the natty live-usb. 

You can find the RESULT.txt on pastebin here: [http://pastebin.com/v8GhtjEh](http://pastebin.com/v8GhtjEh)

---

### Post by joris1977 on 2011-09-03
> **RMOP said:**
>  Your experience is what gives me pause. It sound so like *it should just work, and it doesn't.*

Well my experienced is pretty limited. Most Ubuntu installs I did for friends and relatives just worked... The only boot problems I ever experienced were when I re-installed windows XP on a computer with Ubuntu on it. To solve this I could find lots of great info on blogs and on the ubuntu wiki. 


> **RMOP said:**
>  I just did, BTW, go into my setup and disabled UEFI so that Legacy Only is set. It didn't affect Windows at all, so I'm convinced that UEFI is not in play, as already pointed out in this thread. Don't know if that will matter, but shouldn't hurt. Don't know if you tried that or not.

I played with this bios options, but it didn't make a difference.

---

### Post by Hakunka-Matata on 2011-09-03
You do not have grub installed.  Look at your RESULTS.txt file, right at the beginning it says no bootloader installed in the MBR of sda
here's a link on how to reinstall grub, you need to do that.
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD]("https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD")
it is always better to start your own thread because it gets confusing (more confusing) when multiple people ask questions on the same thread, we lose track, or at least I do.  Better for you, better for me. peace

---

### Post by RMOP on 2011-09-04
> **joris1977 said:**
> Sorry, I really didn't mean to hijack this thread. I found this thread while searching for a solution on this forum to get ubuntu to boot on a dual boot with a x120e. I was warning the OP that I was having problems, that I could not get solved and hoped someone more experienced than me would be so kind to post some clear howto install ubuntu on a thinkpad x120e  instructions. That would help the OP, it would help me and probably some other ubuntu users

I'm actually amazed that I cannot find these instructions somewhere since there seem to be a lot of people running linux on this (very nice) netbook.    

I can start a new thread if you or the OP think that is more appropriate, but I would have to name it almost similar as this one... 

For what it is worth: I ran the boot_info_script from the natty live-usb. 

You can find the RESULT.txt on pastebin here: [http://pastebin.com/v8GhtjEh](http://pastebin.com/v8GhtjEh)

As the originator of this thread, I find your comments and related questions to be entirely relevant, and appreciate them. NP on my part, no apology indicated and no offense taken! There needs to be a bit of unstructured ramble in a thread, or responses become essentially binary. But, back to the theme...

I share your consternation about the lack of a good "Ubuntu on the ThinkPad X120e: a Pain-Free Installation HowTo." But, as I've not figured out how to manage a safe and complete install as of yet, I'll not bother to feel guilty about not writing that HowTo.

At present, I'm not sure I understand what to do anymore than when I began this thread.

To sum up by take on all said:

1) Ubuntu should install easily on the X120E w/o any special precautions.

2) It doesn't, or if it does, those for whom it does have better things to do than weigh in on this thread.

3) There are viable work-arounds suggested in this thread, but for me personally, they seem so complicated, convoluted or otherwise obscure as to make me continue my back bencher status for a bit longer. I don't want to find myself frantically trying to repair my MBR after my system fails to boot to either Ubuntu OR Windows.

***The above said, I'm still hoping someone who owns an X120E and has come up with a straight-forward and replicable install procedure will step forward, expose my ignorance, and bless us with their knowledge.***

Until then...cheers!

---

### Post by oldfred on 2011-09-04
How many partitions are used. Most new Windows7 systems use all 4 partitions just to make it difficult to install another system. Post this:

```

sudo fdisk -lu
```

You need to make a Windows repair CD.

Make your own Windows recoveryCD/repair:
[http://forums.techarena.in/guides-tutorials/1114725.htm](http://forums.techarena.in/guides-tutorials/1114725.htm)

Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)

Then if need be you can easily reinstall Windows boot loader to the MBR from Windows command line with BootRec.exe /fixMBR .

---

### Post by RMOP on 2011-09-04
Not booted to Ubuntu right now. The Windows Disk management tool shows FOUR (4) NTFS partitions, one of which I created as a data drive after shrinking the large "C" partition on which W7 is installed. The other two are a 1.7gb SYSTEM_DRV and a 9.7gb LENOVO_RECOVERY partition. The data drive "D" is logical, whilst the other three are primary. SYSTEM_DRV is showing as "active."

Hope this helps.

---

### Post by oldfred on 2011-09-04
If your D: drive is a logical drive inside an extended it makes it a bit easier as you do not have to delete anything, but you will have to move things around depending on where you want to shrink and make room for Ubuntu. Also may make a difference which partitions are next to each other.

Have you made the recovery DVDs? That is also suggested as well as the windows repair CD. And it is always a good idea to have full backups as the recover DVD restores to as purchased and any updates, reboots, and all your data is not restored.

Backups ---------
The vendor recovery DVDs are just an image of your drive as purchased. If you have housecleaned a lot of cruft normally included, run many updates with many reboots, and added software you may want a full back up.
Backup windows before install - post by Mark Phelps
[http://ubuntuforums.org/showthread.php?t=1626990](http://ubuntuforums.org/showthread.php?t=1626990)
[http://www.macrium.com/reflectfree.asp](http://www.macrium.com/reflectfree.asp)
Another suggestion by srs5694
[http://www.runtime.org/driveimage-xml.htm](http://www.runtime.org/driveimage-xml.htm)

---

### Post by RMOP on 2011-09-04
Thanks. No vendor supplied DVDs w this machine. I'll make my own, don't worry there. I'll do a further reduction on the current "C" drive to make room for another logical partition, which is where I'll put Ubuntu. Plenty of room on this HD for that. Correct if I'm mistaken, but it appears that Grub should be installed to the current "active" partition, the small 1.7gb SYSTEM_DRV. It should be easy enough to spot from the Ubuntu partition utility.

Will hopefully get to all this later this week.

---

### Post by oldfred on 2011-09-05
NO!! Do not install grub2's boot loader to any windows partition. 

In MBR the windows boot partition is unique to windows and grub will damage it. Only in efi partition do both boot loaders exist. With MBR you can only boot one system that is in the MBR or grub2 is recommended as it will then let you boot multiple systems. If you have windows in the MBR then you can only boot windows. The MBR is the first sector of a hard drive and is not part of any partition.

---

### Post by joris1977 on 2011-09-08
> **Hakunka-Matata said:**
> You do not have grub installed. 

Ah... Damn! That is weird, because I saw Grub getting installed when I installed ubuntu... But now I fixed it. I first tried with the graphical tool from a live cd mentioned on the community wiki, but that didn't work. Than I tried the cli way. "Copy LiveCD Files" on the wiki. And that worked!

So it wasn't such a difficult thing to solve after all. Thanks Hakunka-Matata for pointing me in the right direction and good luck OP with installing ubuntu!

---

### Post by RMOP on 2011-09-08
Good news, Joris, and encouraging. So, the whole thing was a problem getting Grub to install. I'll look at the wiki and hope for the same good outcome.

Might I ask WHERE you told Grub to place itself when it finally did so, successfully? Thanks.

---

### Post by joris1977 on 2011-09-08
> **RMOP said:**
> 
Might I ask WHERE you told Grub to place itself  

/dev/sda

I followed these instructions: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

As you can see from the results from the boot info script. My linux partition is on /dev/sda5

So I did from the natty live usb: 

```
sudo mount /dev/sda5 /mnt
```

Than I installed grub:

```
sudo grub-install --root-directory=/mnt /dev/sda
```

Than I did a reboot and grub showed up and ubuntu was working as expected.

---

### Post by RMOP on 2011-09-09
Well, this makes it all look straight-forward. Grub installed to the MBR of sda and not to any of the partitions, which makes sense. When I get back from travel, I'll give it a try. Thanks for reporting.

---

### Post by Hakunka-Matata on 2011-09-09
> **joris1977 said:**
> /dev/sda

I followed these instructions: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

As you can see from the results from the boot info script. My linux partition is on /dev/sda5

So I did from the natty live usb: 

```
sudo mount /dev/sda5 /mnt
```Than I installed grub:

```
sudo grub-install --root-directory=/mnt /dev/sda

[COLOR=Red]In Grub 1.99, introduced with Ubuntu 11.04, Natty Narwhal, a new switch is available which more clearly defines where the *grub* folder is placed. The command above will still work with Grub 1.99, but the following command is preferred by the developers.

[/COLOR]sudo grub-install --boot-directory=/mnt/boot /dev/sdX
```Than I did a reboot and grub showed up and ubuntu was working as expected.


@joris;

Good to know you got grub installed in the proper MBR.  After rebooting into your working system, (that would be /dev/sda5, yes?), do run 
```
sudo update-grub
```that will pick up and add an entry in your grub menu, for any other OSes found on your hard drives.

---

### Post by RMOP on 2011-09-21
Well, this was embarassingly easy. After moving my existing W7 install to a new, larger HD, I was able to create the necessary partitions AFTER the not-to-be-moved Windows Recovery Partion. Then I decided to try a routine Ubuntu 11.04 64-bit install. No problem with the install at all, and Grub 2 placed itself properly and both Ubuntu and Windows boot fine. No special intervention necessary at all. Now, to get the install tweaked...

---

### Post by ashishjain on 2012-02-23
I bought a x130e recently. I installed Ubuntu properly but it wouldn't show. I spent more than 12-15 hours on this. And finally I tried Joris1977's suggestions. And the system just worked. Wow. Thanks quite a bunch.

---

