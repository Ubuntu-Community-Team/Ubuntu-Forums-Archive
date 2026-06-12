---
title: "Intalling Ubuntu to external drive by means of vmware"
date: 2023-06-25
forum: Installation &amp; Upgrades
---

### Post by send2 on 2023-06-25
I am getting my husband into using Linux (he is starting out with Ubuntu), and he brought up an interesting question. Now I mentioned that you can install Ubuntu with no problems to external drive with good speed specially if using USB 3.1 on a SSD with 1TB space and a recent machine. He brought up the question of could one install Ubuntu to external drive but instead of installing normally, format SSD with Windows partition and use VMware to install Ubuntu. (He would want to keep the SSD external drive formatted for Windows).

 I said that it is faster to just install Ubuntu directly to external drive instead of installing VMware and then installing Ubuntu. 

Has anyone tried this? I thought it was an interesting option, I have triple booted to external drive just directly installing Linux OS's unto external drives, but the method above would not be an efficient way to install Ubuntu, (I don't think), but interesting option.

---

### Post by TheFu on 2023-06-26
VMware makes 6 virtualization hypervisors.  Perhaps if you are most specific on which product will be used, an answer would be possible?

---

### Post by MAFoElffen on 2023-06-27
There are 2 VMware virtualization host product that run on Windows: VMware Player and VMware Workstation Pro. If his only concern is the storage space, that will work. Of those two, both allow you to store VM Guest files on external storage drives. 

But if he is worried about performance, make him aware that a VM will run faster on internal storage (Even if on an HDD) than on an external drive. SSD's are fast. Samsung 870 EVO is 550 MB/s. But USB speeds are slower, unless he has newer USB-C 3.x, which is 5 to 80 Gbps, depending on the Generation of.

In that case, wouldn't he be happier with an upgrade (bigger and faster) to his internal storage? Are you talking about a laptop or desktop?

---

### Post by ActionParsnip on 2023-06-27
You could make a LUN on the USB then use that storage to hold the virtual disks and config for the Ubuntu VM

---

### Post by TheFu on 2023-06-27
> **ActionParsnip said:**
> You could make a LUN on the USB then use that storage to hold the virtual disks and config for the Ubuntu VM

Or use a symbolic link.  MSFT has those now, right?

What ever happened to VMware Server?  I used that on MS-Windows and the CCNA course emulator used that for a long, long, time.

---

### Post by MAFoElffen on 2023-06-27
@TheFu

LOL! We're both showing our age now.

VMware Server 1.0 was released to replace VMware GSX in 2006 and discontinued in 2009. VMware Server 2.0 replaced it, but was discontinued in 2010. It was advertised that it only ran on a Windows Server Edition (2000, 2003, 2003R2, 2008) and Enterprise-class Linux Distro's... But it was found that it also ran on Windows 7 Enterprise.  General support for it ended in 2011. Nothing ever replaced it as a product.

VMware Workstation was introduced in 1999...

TheFu <-- If you want to play with it, I still have the tarball for the final release of VMware Server 2.0.2 and the Ubuntu patch for it in my library. The last version of Ubuntu that I tried to get it to run on was Ubuntu 11.04.

---

### Post by send2 on 2023-06-28
@TheFu,

thanks for your reply. He wants to use VMware player 17. It is the free player that VMware has for home users. Apologies for not being as precise. My mind I think is going :)

---

### Post by send2 on 2023-06-28
@MAFoElffen,

thank to you for your answer, 

he has USB 3.1 so the speed would not be too much of an issue running on a Lenovo Ideapad Flex 5 laptop. I think it still would be better to install Ubuntu alongside Windows for the moment, although personally for me I don't like to dual-boot, but he is just beginning his Linux journey and does not want to deal with Windows installation issues should he have any. Thank you for your advice on a VM running faster on internal storage. As far as upgrading his internal drive he could do that but a laptop now is so small in space it is not like a desktop being at least a bit easier to upgrade. He is wanting to use VMware Player, the free software. Thanks again for your help. Have a great day!

---

### Post by send2 on 2023-06-28
@MAFoElffen:

> **MAFoElffen said:**
> @TheFu

LOL! We're both showing our age now. 
Not to intrude on your reply, but I too am starting to feel my age, specially when mentioning Atari game consoles and Betamax video players :P. Just thought I would throw that out there!

---

### Post by TheFu on 2023-06-28
> **send2 said:**
> @MAFoElffen:


Not to intrude on your reply, but I too am starting to feel my age, specially when mentioning Atari game consoles and Betamax video players :P. Just thought I would throw that out there!

I kicked ass on the Atari 2600!  Combat #4, knew all the bugs to flip my tank to the other side of the board. Fake Space invaders ... play forever and Yars Revenge was stupid, but addictive.  Kids these days want photo-realistic games. They missed out on the stupid LED hand-held Coleco games. [https://www.handheldmuseum.com/Coleco/H2HFootball.htm](https://www.handheldmuseum.com/Coleco/H2HFootball.htm)

---

### Post by MAFoElffen on 2023-06-28
LOL! I spent so many hours on my father's Commodore 64 playing Battle Chess!!! He was an old COBOL programmer. Us kids felt sorry for him and bought him an IBM PS/2 because he would write programs on it, that ran for days before they finished. (He still has that Commodore 64...)

Back to the subject asked about... 
Option #2 -- Does he have Windows Pro Edition? If so, then why not enable Hyper-V and install a VM Guest through that? Same, you can create your VM Store anywhere to save the files. No sense in adding VMware Workstation if he already has Hyper-V capabilities to do that already. Right?

Or option #3, which is aligned what you are telling him and is sort of a hybrid solution... Install alongside Windows, but directly to an attached USB SSD drive. But from then on, it would have to be attached to his laptop when he booted, because the boot manager would be grub... Unless he pressed <F12> on boot to bring up the UEFI boot menu to select Windows. But installed that way, it makes no changes to the size and other things on his Laptop, except adding some EFI files and changing the EFI boot order.

---

### Post by send2 on 2023-06-29
@ActionParsnip,

thank you very much for your suggestion, I will look further into that. Do you have any links that might help? I will look on my own in the meantime. Thank you so much.

---

### Post by send2 on 2023-06-29
> **TheFu said:**
> I kicked ass on the Atari 2600!  Combat #4, knew all the bugs to flip my tank to the other side of the board. Fake Space invaders ... play forever and Yars Revenge was stupid, but addictive.  Kids these days want photo-realistic games. They missed out on the stupid LED hand-held Coleco games. [https://www.handheldmuseum.com/Coleco/H2HFootball.htm](https://www.handheldmuseum.com/Coleco/H2HFootball.htm)

@TheFu, 

Awesome! 
Oh wow! you take me back! LOL, I haven't thought of Space Invaders in years. Nowadays you can get all those games for PC updated, I think through Steam... I just checked...  There is Space Invaders Extreme and there also is a demo. Yar's Revenge is also on Steam. I played Pong a lot, but it has been so long ago! :). Pong is on there too but called Project Pong with new levels. I remember the Coleco games but never played one. It was hard for me to get my hands on any type of game. I remember Atari because when my brother brought it home we were mesmerized! LOL.

---

### Post by send2 on 2023-06-29
@MAFoElffen,

it is so cool that you had such experiences with gaming and computers. I got in to them in 80's. To answer your questions:

Option #2 No he does not have Windows Pro edition, just home edition. I see what you mean. I looked in BIOS to see if it was enabled but I don't remember now if it had Hyper-V enabled. I think I was looking for something else at the time and it has been a while back. 

Option #3 We could go for that solution, and it is the one I was thinking, but instead of a partition in Windows just install Ubuntu to an attached external drive like you are suggesting. I did that with Ubuntu, Mint and I can't remember what other Linux OS I used and Windows. This was before Windows 8, ah yes I was running Windows 7 at the time, so I had 3 Linux OS plus Windows at the time. Since then, some distro hopping :).

Thank you so much for the memories and for your replies...

---

### Post by MAFoElffen on 2023-06-29
> **send2 said:**
> 
Option #2 No he does not have Windows Pro edition, just home edition. I see what you mean. I looked in BIOS to see if it was enabled but I don't remember now if it had Hyper-V enabled. I think I was looking for something else at the time and it has been a while back. 

Hyper-V will not show up in Windows Features unless the Edition is Professional Edition or higher. He would have to upgrade to Windows Pro to do that.

BTW- Hearing he has Windows Home... Just how much memory does his laptop have? That is going to affect if he can run a VM guest of any type efficiently, no matter what VM Host software he ends up running. Because, then you have the host memory requirement, plus what the guest is using. <-- That is not a factor if you are dual-booting. Because then it is only one OS at a time using the resources. You can 'sluff' that with a max sized Swap file, but then that affects the performance of, with it having to page from the swap file.

---

### Post by TheFu on 2023-06-30
Any computer with at least 4GB of RAM and an x86_64-bit CPU that has VT-x or AMDv virtualization support (and that support is enabled in the BIOS) can use virtualbox for running a VM.  I had a Core2 Duo with 16GB in 2010 using Xen to run 10 VMs concurrently supporting 2 businesses.  I quickly learned that VirtualBox isn't really meant for running servers, switched to Xen for a few years, before finally switching to KVM/QEMU on Linux after a year of testing VMware ESX and ESXi along with KVM/QEMU.  Alas, on MS-Windows, Virtualbox really is the best of bad choices for the situation you've described.  For learning Linux, it is fine. Running a single system 24/7 should work too.

As with all virtual machine installs, it is an exercise in learning to share the available hardware between all the running VMs and the host OS.  This is less hard these days since 16GB of DDR4 RAM is $30.

I'm not a fan of dual booting for a number of reasons, mainly because only one OS can be used at a time. That's just too limiting.

As for gaming, I won't use Steam. I think it is none of their business which games we play, what levels are achieved, how long we play, etc.  Plus, I don't want to pay for games that I already own.

Getting MAME working isn't too hard and the ROMs can be found online (of course, if you need to own the cartridge to legally use them).  There's also the 160 games from the Atari Game system(s) for $90. [https://www.amazon.com/Flashback-Anniversary-Controllers-Not-Machine-Specific/dp/B0BGYD6GM9](https://www.amazon.com/Flashback-Anniversary-Controllers-Not-Machine-Specific/dp/B0BGYD6GM9) - the main complaints are that the controller isn't as responsive, so getting a refurbished one is likely needed. Games: Adventure, Asteroids, Barnstorming, **Centipede** & Millipede, Circus Atari, **Chopper Command**, **Combat**, Crystal Castles, Demon Attack, Dragon Fire, Enduro, Freeway, Frogger (arcade repro), Frostbite, Grand Prix, HERO, Haunted House, Kaboom, Keystone Kapers, Laser Blast, Megamania, **Missile Command**, Pitfall 1 & 2, River Raid, Robot Tank, Skiing, **Space Invaders** (arcade repro), Spider Fighter, Stampede, **Yars Revenge**  More games can be added by using USB storage. Just place the ROMs onto the storage in a directory named "games/".  This version does composite (yellow cable) video output. A converter is $12.

There's a competitor with 600+ games for $25, but none are the original versions (all knock offs), which would matter to a connoisseur like myself. The games need to be exactly the same - bug for bug.  This version does 720p HDMI video output.

I'm much more likely to pull out the old 2600 from the attic and slap in some cartridges.  I have a video converter to change from yellow-cable composite 240i video, sVideo, component 1080i all into 1080p hdmi for our projectors.  Right now we are reliving our PS2 games on that console. Cleaning the joystick contacts with an eraser ... remember that?

---

### Post by send2 on 2023-06-30
> **MAFoElffen said:**
> Hyper-V will not show up in Windows Features unless the Edition is Professional Edition or higher. He would have to upgrade to Windows Pro to do that.

BTW- Hearing he has Windows Home... Just how much memory does his laptop have? That is going to affect if he can run a VM guest of any type efficiently, no matter what VM Host software he ends up running. Because, then you have the host memory requirement, plus what the guest is using. <-- That is not a factor if you are dual-booting. Because then it is only one OS at a time using the resources. You can 'sluff' that with a max sized Swap file, but then that affects the performance of, with it having to page from the swap file.

@MAFoElffen,

Hi again, I just checked the system info for his computer, (it is the same as mine). We are running Windows 11 and in the system info or specs we see the following:

Windows 11 Home, Processor: AMD Ryzen 7 5700 with Radeon Graphics, 1801 MHz, 8 cores, 16 logical processors.
Total physical memory 15.36 GB, Installed Physical Memory (RAM) 16 GB, total virtual memory 17.7 GB.
Hyper-V VM monitor mode extensions yes, Hyper-V Second Level address Translation Extensions yes, Hyper-V Virtualization Enabled in Firmware yes, Hyper-V Data Execution Protection yes. 

From this if I am not mistaken, the virtualization is on and capable for virtualization purposes. Thanks again for your help and time.

---

### Post by send2 on 2023-06-30
> **TheFu said:**
> Any computer with at least 4GB of RAM and an x86_64-bit CPU that has VT-x or AMDv virtualization support (and that support is enabled in the BIOS) can use virtualbox for running a VM.  I had a Core2 Duo with 16GB in 2010 using Xen to run 10 VMs concurrently supporting 2 businesses.  I quickly learned that VirtualBox isn't really meant for running servers, switched to Xen for a few years, before finally switching to KVM/QEMU on Linux after a year of testing VMware ESX and ESXi along with KVM/QEMU.  Alas, on MS-Windows, Virtualbox really is the best of bad choices for the situation you've described.  For learning Linux, it is fine. Running a single system 24/7 should work too.

As with all virtual machine installs, it is an exercise in learning to share the available hardware between all the running VMs and the host OS.  This is less hard these days since 16GB of DDR4 RAM is $30.

I'm not a fan of dual booting for a number of reasons, mainly because only one OS can be used at a time. That's just too limiting.

As for gaming, I won't use Steam. I think it is none of their business which games we play, what levels are achieved, how long we play, etc.  Plus, I don't want to pay for games that I already own.

Getting MAME working isn't too hard and the ROMs can be found online (of course, if you need to own the cartridge to legally use them).  There's also the 160 games from the Atari Game system(s) for $90. [https://www.amazon.com/Flashback-Anniversary-Controllers-Not-Machine-Specific/dp/B0BGYD6GM9](https://www.amazon.com/Flashback-Anniversary-Controllers-Not-Machine-Specific/dp/B0BGYD6GM9) - the main complaints are that the controller isn't as responsive, so getting a refurbished one is likely needed. Games: Adventure, Asteroids, Barnstorming, **Centipede** & Millipede, Circus Atari, **Chopper Command**, **Combat**, Crystal Castles, Demon Attack, Dragon Fire, Enduro, Freeway, Frogger (arcade repro), Frostbite, Grand Prix, HERO, Haunted House, Kaboom, Keystone Kapers, Laser Blast, Megamania, **Missile Command**, Pitfall 1 & 2, River Raid, Robot Tank, Skiing, **Space Invaders** (arcade repro), Spider Fighter, Stampede, **Yars Revenge**  More games can be added by using USB storage. Just place the ROMs onto the storage in a directory named "games/".  This version does composite (yellow cable) video output. A converter is $12.

There's a competitor with 600+ games for $25, but none are the original versions (all knock offs), which would matter to a connoisseur like myself. The games need to be exactly the same - bug for bug.  This version does 720p HDMI video output.

I'm much more likely to pull out the old 2600 from the attic and slap in some cartridges.  I have a video converter to change from yellow-cable composite 240i video, sVideo, component 1080i all into 1080p hdmi for our projectors.  Right now we are reliving our PS2 games on that console. Cleaning the joystick contacts with an eraser ... remember that?

@TheFu,

Hi again, 

Thanks for your reply, I have found out that for my computer running VMware works better than Virtualbox, at least for Ubuntu 22.04.2, I had a lot of problems with Virtualbox with that version of Ubuntu, although in the past I have run Ubuntu in Virtualbox with no problems, but the hardware and software were different. I want to learn how to use KVM/QMU but the documentation is to me a bit confusing. Will have to look at other sources for how to use the software. As far as RAM, we have 16 GB of RAM on our computers (we have the same Lenovo Ideapad Flex 5 with AMD Ryzen 7 and AMD Radeon Graphics. 

I too don't like dual booting either for the same reason you stated above, only being able to use one OS at the time, but prefer bare metal on all OS's I run.
 
As far as Steam, I understand very well what you mean, I guess I am with them for the convenience but prefer GOG for that reason. The games I already own I have running Windows 95 and 98 on Windows. I had to really mess with the installation of those from discs I already own. 

Thank you very much for the Amazon link, I will look into it further. I have Frogger which I run in Windows 95 I believe and have Fantasmagoria running for sure in Windows 95. 

Yes, I remember the eraser bit, just like cassettes where you used a pencil to straighten out the tape and wind it :). 

Thank you so much for letting me know about your experiences in gaming. Have a great day!

---

### Post by MAFoElffen on 2023-06-30
Interested in KVM? Now we are talking about something that can take you miles further.

Both TheFu and I switched over to KVM over a decade ago. Me in 2010 on Ubuntu 10.04 LTS. If you wanted to learn or ever need help with that, or just need help with 'any' Virtualization question involving Ubuntu on any Virtual Host, we both answer questions in the Forum's Virtualization Section. There is a good group of people that are very knowledgeable that answer questions in that section there.

In the past I used VirtualBox, VMware Workstation, etc... Then I migrated to XEN, VMware vSphere, Hyper-V, then KVM. Once I dug more into KVM, I was hooked. It has all the capabilities I use and need. I still beta-test and provide support for for MS Server Insider, and VMware vSphere, but I live on Ubuntu with KVM.

Running Ubuntu natively, KVM as a Virtual Host service manages resources "very, very, very well". And it is very flexible and adaptable. Most other Virtual hypervisors are just one archtecture and platform, and that is what you get, within that limited sandbox to play in. That is why most of the Virtual Hosts in the Cloud and used by Enterprises use some kind of KVM based hosting software. It is fairly simple to setup and use, once you pull back the veil and remove the mystique. 

What I like about it that, for me, I can replicate different Guest hardware platforms (x86, amd64, arm64, IBM360, pppc64, risc64) to test my scripts and applications on, to verify that things work on them. Most people do not need that, but for them, it has the capability for people to try things meant for those platforms, and explore.

We could both help you get started with that to explore on your own...

---

### Post by send2 on 2023-06-30
@MAFoElffen,

I will answer your post properly (post 19) later on today, time to make dinner! 
Thanks again for your help.

I will have to answer the post tomorrow, time has gotten away from me tonight, apologies.

---

### Post by TheFu on 2023-06-30
KVM/QEMU has one major drawback for most people.  KVM only works on Linux hosts.  QEMU can work on anything, because it is software only, but it is pretty slow without the KVM hardware extensions that x86-64 (most) and ARM64 platforms support.

I've been on Ryzen with KVM since the 2xxx series. It performs well.  I think it was faster than VMware ESXi too, but VMware doesn't allow people to publish proof of that.  I do know that of the 6 physical machines I had at the time, only 1 would load VMware ESXi - it was extremely picky about hardware. OTOH, KVM works with basically any x86_64 hardware that runs Linux. No limits on the SATA controllers or ethernet or chipsets supported like with VMware.

If you had issues with Virtualbox, I suspect it was lack of tuning. Virtualbox and VMware Player/Workstation are very similar.  I use VMware Workstation in the late 1990s where I worked. Mainly for testing, but also to compile our software using Asian character sets. This was before UTF8/Unicode.  We were using wide characters in our code back then and setting specific code pages to support Japanese and Korean customers.  Now that unicode exists, supported pretty much every language isn't nearly as hard.

---

### Post by send2 on 2023-07-01
> **MAFoElffen said:**
> Interested in KVM? Now we are talking about something that can take you miles further.

Both TheFu and I switched over to KVM over a decade ago. Me in 2010 on Ubuntu 10.04 LTS. If you wanted to learn or ever need help with that, or just need help with 'any' Virtualization question involving Ubuntu on any Virtual Host, we both answer questions in the Forum's Virtualization Section. There is a good group of people that are very knowledgeable that answer questions in that section there.

In the past I used VirtualBox, VMware Workstation, etc... Then I migrated to XEN, VMware vSphere, Hyper-V, then KVM. Once I dug more into KVM, I was hooked. It has all the capabilities I use and need. I still beta-test and provide support for for MS Server Insider, and VMware vSphere, but I live on Ubuntu with KVM.

Running Ubuntu natively, KVM as a Virtual Host service manages resources "very, very, very well". And it is very flexible and adaptable. Most other Virtual hypervisors are just one archtecture and platform, and that is what you get, within that limited sandbox to play in. That is why most of the Virtual Hosts in the Cloud and used by Enterprises use some kind of KVM based hosting software. It is fairly simple to setup and use, once you pull back the veil and remove the mystique. 

What I like about it that, for me, I can replicate different Guest hardware platforms (x86, amd64, arm64, IBM360, pppc64, risc64) to test my scripts and applications on, to verify that things work on them. Most people do not need that, but for them, it has the capability for people to try things meant for those platforms, and explore.

We could both help you get started with that to explore on your own...

@MAFoElffen,

thank you very much for your offer of help with KVM. Yes, I would be interested in reading about KVM  in order to understand it and use it. I am only running Ubuntu in VMware for windows with only 90GB so I would have to use another hard drive for that purpose. I have an older hard drive that I have Manjaro on with more hard drive space, but I can use it for virtualization and learning purposes. 

Thanks for mentioning other virtualization options and the details of each, I am only aware of Virtualbox and VMware as far as using them. Also I was not aware of how flexible KVM is compared to other virtualization software. 

I do also read the virtualization section of the forum just in case I run into something that I might want to know. Actually, I read most sections of this forum :P! 
Once again, I really appreciate your offer of help, that is very nice of you!

---

### Post by send2 on 2023-07-01
> **TheFu said:**
> KVM/QEMU has one major drawback for most people.  KVM only works on Linux hosts.  QEMU can work on anything, because it is software only, but it is pretty slow without the KVM hardware extensions that x86-64 (most) and ARM64 platforms support.

I've been on Ryzen with KVM since the 2xxx series. It performs well.  I think it was faster than VMware ESXi too, but VMware doesn't allow people to publish proof of that.  I do know that of the 6 physical machines I had at the time, only 1 would load VMware ESXi - it was extremely picky about hardware. OTOH, KVM works with basically any x86_64 hardware that runs Linux. No limits on the SATA controllers or ethernet or chipsets supported like with VMware.

If you had issues with Virtualbox, I suspect it was lack of tuning. Virtualbox and VMware Player/Workstation are very similar.  I use VMware Workstation in the late 1990s where I worked. Mainly for testing, but also to compile our software using Asian character sets. This was before UTF8/Unicode.  We were using wide characters in our code back then and setting specific code pages to support Japanese and Korean customers.  Now that unicode exists, supported pretty much every language isn't nearly as hard.

@TheFu,

thanks again for your reply. I was aware of KVM only working with Linux but did not know that QEMU also worked on other OS's. You have once again educated me on KVM and other virtualization options and this is so useful. Your explanations are why I love this forum. I learn something new everyday! Thanks for your explanation on Virtualbox. 

I don't have experience with the VMware workstation. Unfortunately, with the free player, I cannot save the vm, but the software is free. Can you save the vm in KVM? or QEMU? I am very interested to know about both KVM and QEMU. I have looked at their respective websites, but a lot of it has gone over my head.

---

### Post by send2 on 2023-07-06
To all of you who helped, thank you very much for your advice and thoughts. I am showing this thread to my husband. I will also post a new thread later asking about how to start with KVM/QEMU. I will also mark this tread as solved. Might ask other questions in the future if they arise.

---

### Post by TheFu on 2023-07-06
> **send2 said:**
>  
I don't have experience with the VMware workstation. Unfortunately, with the free player, I cannot save the vm, but the software is free. Can you save the vm in KVM? or QEMU? I am very interested to know about both KVM and QEMU. I have looked at their respective websites, but a lot of it has gone over my head.

I don't understand what you mean by "cannot save the vm".  

That really isn't how these things work.  Perhaps you are just using different terms?

Virtual hardware is setup, including virtual storage.  The OS is loaded into that virtual hardware/storage and run. It can run for 30 seconds or 5 yrs.  All the while, the OS is reading and writing from/to the virtual storage.  When the VM is shutdown, the virtual storage remains, as does the virtual hardware configuration.  It is there.  There's no "save".  Reboot the computer, come back in, restart the hypervisor, find the prior VM in the list of VMs and restart it.  The virtual machine starts up, boots, just like any other OS on physical hardware, just like when the power button is turned on. Any prior data, programs, whatever are still there.

If you want to move a VM to a different physical machine, then you'd "Export" it - at least for VirtualBox and VMware-Workstation.  I think they use the OVF format for that.  On the other side, use the VM-Import feature.

With KVM, I've moved VMs between physical systems a number of times.  Their may be easier ways, but I do it by exporting the virtual hardware configuration, then moving the storage to the new system.  KVM supports lots of different back-end storage types - probably 10-20 backends, so how to move it is different for each.

Different storage back-ends have different features, but most KVM users would start with qcow2. It is easy and reasonably fast.  I used it a few years before moving to LVM storage for my back-end.  LVM brings some enterprise storage features that other backends don't provide.  There are some back-ends that handle fault tolerance and spread the data across multiple nodes in a KVM cluster.  Just depends on what you need and how much complexity you can stand to get it.

---

### Post by MAFoElffen on 2023-07-07
On "not saving" confuses me as well... I have never ran into that with VMware products-- Their free or Full-blown. 

If you run into that, I would like to know of what is going on there and how I could help with that. Because that is not how it's supposed to work for that.

---

### Post by send2 on 2023-07-08
> **TheFu said:**
> I don't understand what you mean by "cannot save the vm".  

That really isn't how these things work.  Perhaps you are just using different terms?

Virtual hardware is setup, including virtual storage.  The OS is loaded into that virtual hardware/storage and run. It can run for 30 seconds or 5 yrs.  All the while, the OS is reading and writing from/to the virtual storage.  When the VM is shutdown, the virtual storage remains, as does the virtual hardware configuration.  It is there.  There's no "save".  Reboot the computer, come back in, restart the hypervisor, find the prior VM in the list of VMs and restart it.  The virtual machine starts up, boots, just like any other OS on physical hardware, just like when the power button is turned on. Any prior data, programs, whatever are still there.

If you want to move a VM to a different physical machine, then you'd "Export" it - at least for VirtualBox and VMware-Workstation.  I think they use the OVF format for that.  On the other side, use the VM-Import feature.

With KVM, I've moved VMs between physical systems a number of times.  Their may be easier ways, but I do it by exporting the virtual hardware configuration, then moving the storage to the new system.  KVM supports lots of different back-end storage types - probably 10-20 backends, so how to move it is different for each.

Different storage back-ends have different features, but most KVM users would start with qcow2. It is easy and reasonably fast.  I used it a few years before moving to LVM storage for my back-end.  LVM brings some enterprise storage features that other backends don't provide.  There are some back-ends that handle fault tolerance and spread the data across multiple nodes in a KVM cluster.  Just depends on what you need and how much complexity you can stand to get it.

@TheFu,

sorry for the confusion, to clarify, I am not running the VMware workstation, I am running the free VMware player. By using the free VMware player, version 17, I cannot save an instance of the created virtual machine. i.e. Ubuntu in this instance to have a copy of the OS to move elsewhere if I want. With the paid version of VMware there are more options to manipulate the created OS, in this instance Ubuntu. I am running Ubuntu 22.04.2 in VMware right now, but I am running it in the free VMware player. I have considered paying for it, but I am not sure if I will stay with VMware or go to another virtualization solution. I am checking what my options are. I will ultimately run Ubuntu on bare metal, but not at present. 

Thank you for your explanation and reply. They are always helpful.

---

### Post by send2 on 2023-07-08
> **MAFoElffen said:**
> On "not saving" confuses me as well... I have never ran into that with VMware products-- Their free or Full-blown. 

If you run into that, I would like to know of what is going on there and how I could help with that. Because that is not how it's supposed to work for that.

@MAFoElffen,

thanks again for your reply. Sometimes I hate trying to explain something in writhing when English is not my first language. Sorry for the confusion. I am running the free version of VMware, the player, version 17. Since I am not running the paid VMware workstation edition, I cannot save a copy of the created OS, in this case Ubuntu 22.04.2 to use elsewhere. I am running Ubuntu now in VMware player as guest with Windows as host. I hope I have clarified what I mean, if not I will be happy to explain further. Thanks again for your help and time.

---

### Post by MAFoElffen on 2023-07-10
The difference between VMware Workstation Pro and VMware Player, is with using Player: you cannot save SnapShots... And you can only run one VM at a time. Yes, VMware wants you to buy their product.

But (externally) you can copy the VM's virtual drive file, to save things at a certain point... As a work-around to that.

Also, in how you setup your VM guest, you can do backups and snapshots of a Volume Manager within that VM Guest, just as if it where a real machine. Just think of it as being another computer that lives within your host.

---

### Post by send2 on 2023-07-11
> **MAFoElffen said:**
> The difference between VMware Workstation Pro and VMware Player, is with using Player: you cannot save SnapShots... And you can only run one VM at a time. Yes, VMware wants you to buy their product.

But (externally) you can copy the VM's virtual drive file, to save things at a certain point... As a work-around to that.

Also, in how you setup your VM guest, you can do backups and snapshots of a Volume Manager within that VM Guest, just as if it where a real machine. Just think of it as being another computer that lives within your host.

@MAFoElffen,

Thanks again for your reply, you hit it right on the head, the word I was looking for was SnapShots. What do you mean by making backups and snapshots of a Volume Manager? Thanks for your pointers again.

---

### Post by MAFoElffen on 2023-07-11
In Linux, with LVM2, ZFS and BTRFS, you can take snapshots with those filesystems.

In Windows OS, you can setup Shadow Copy, which lets you restore previous versions of files in it's file history. That doesn't do that by default. You would have to enable and set that up to do that.

---

### Post by send2 on 2023-07-13
> **MAFoElffen said:**
> In Linux, with LVM2, ZFS and BTRFS, you can take snapshots with those filesystems.

In Windows OS, you can setup Shadow Copy, which lets you restore previous versions of files in it's file history. That doesn't do that by default. You would have to enable and set that up to do that.

Thanks very much for that info. I learn something new everyday! Two more topics I need to look into. Thanks!

---

