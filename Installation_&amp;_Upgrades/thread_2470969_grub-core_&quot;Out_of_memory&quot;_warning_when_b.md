---
title: "grub-core &quot;Out of memory&quot; warning when booting USB Thumb drive for Install"
date: 2022-01-18
forum: Installation &amp; Upgrades
---

### Post by cubdukat1968 on 2022-01-18
I am trying to see if I can do a dual-boot install of Ubuntu 21.10 on my system after disabling Intel RST, but I can't even boot the thumb drive. I get the following error when I do:

"error: ../../grub-core/kern/mm.c:376:out of memory   Press any key to continue"

When I hit a key, it then goes to the motherboard's splash screen and makes no attempt to boot from anything, so I end up having to reboot.

There are two things I suspect would be at issue here:

1) A recent UEFI firmware update has disabled my ability to turn off Secure Boot, and
2) I have to boot the thumb drive manually from the UEFI menu, and it gives me three options : Generic USB Boot Device, (UEFI) Generic USB Boot Device and (UEFI) Generic USB Boot Device (partition 1). All three have the same file size, but either of the UEFI options produce the error message. The one not listed as UEFI boots into the thumb drive, but I have not attempted to install anything because I don't know if it will install correctly.

Has anyone else noticed this with booting on a secure boot system? If so, is there any way around it, as I can no longer turn off Secure Boot as I could before. My mobo vendor (ASUS) has chosen to lock that off, but Ubuntu is supposed to be Secure Boot friendly, so I should at least be able to boot into it, right?

---

### Post by MAFoElffen on 2022-01-18
Information needed, please... Make and model of computer. How much RAM is installed. How much RAM is being shown by the BIOS
 What was that UEFI firmware version number?

---

### Post by cubdukat1968 on 2022-01-18
It's a self-built system. The motherboard is an Asus Z370-A Prime, rev. x 0x, firmware version 3004 dated 7/21/21 (I believe this is the version that locked in Secure Boot), 32GB DDR4-2666. The computer had booted Linux perfectly in the past, and at one time was an Ubuntu dual-boot system. It's only recently after this firmware update that it has had issues booting into Linux. 

I believe that this may actually be a fault of the version of the kernel, since the same error message also pops up with two other live USB distros as well. Unfortunately, I do not have any blank DVDs to test if this error also comes up when booting from them. I'm not so sure that it will for some reason.

---

### Post by MAFoElffen on 2022-01-19
I would say to try to create an Ubuntu 20.04.3 LTS LiveCD USB to see if it will boot on that as a test... If it does, then there are a few things I would like you to test... And a few things to check.

If not, then send me a screen shot of the BIOS Firmware Setup General/Main page, where it shows the specs, and Memory that it see's. Then a screen shot of the RST settings... The Optane card is completely removed right? Have you tried to reset the BIOS to factory defaults?

EDIT:
If this BIOS Firmware update has problems where you lost functionality... If it were me, I would report the problem to ASUS, and re-flash the BIOS to the previous version to regain that functionality.

---

### Post by cubdukat1968 on 2022-01-19
I'm going to buy some blank DVDs so I can make some install discs. 

I haven't removed the Optane stick yet, but I have switched things back over to AHCI and unpaired it from the data drive it was "accelerating." It's way more trouble than it was worth. I had to switch over to AHCI in BIOS in order to be able to dual-boot because otherwise it wouldn't even see the Windows drive to be able to boot into Grub. I'll definitely be taking it out, though; I want to use the M.2 slot for the Ubuntu install.

---

### Post by MAFoElffen on 2022-01-19
Confused... You already have a few USB thumb drives right? That i what the thread title and your first post said... I would only be a short investment in time to create another test LiveCD, right? On of the things I'm wondering is the md5 checksum of the ISO you are trying. And if another ISO does boot without the memory error.

The cryptic contents of what you said were the boot menu entries, gives me pause. One is that it is listing to partitions of the USB drive, instead of just listing the USB Drive as "a device" to try to boot from.

---

### Post by cubdukat1968 on 2022-01-19
I'm actually getting ready to redo all of the thumb drives. The Ubuntu one was done with an older version of Rufus, while the Fedora (sorry) was done with their own Disk Writer program. 

I'm coming back from a bit of a hardware setback. I removed the Optane stick, and the system wouldn't even boot, then somehow I got stuck in an ntfs.sys BSOD boot loop. I finally got the system back up and going, but as it turns out, removing the Optane stick didn't solve the problem. I'll try the DVDs later on tonight; I couldn't find image files small enough to fit on CDs for any of them, especially not Ubuntu. 

I don't know why they have to make it so damn hard to use Linux. All I can say is that me and ASUS are done professionally, and that goes for any mobo vendor that disables turning off Secure Boot. I'm seriously considering just building a dedicated Linux computer so that I don't have to deal with it, because I most definitely WILL have Linux on at least one computer in my home :)

---

### Post by MAFoElffen on 2022-01-20
Did you try to reset the BIOS to defaults? 

I know that you might be wondering why I am still asking you questions... And they may seem a bit unrelated, but...

- You had a BIOS firmware update, where you said there were problems... The problem you noted was that Secure Boot is enabled. I just can tell you that because that is enabled, That is not your problem.
> 
*"Modern versions of **Ubuntu, Fedora, openSUSE**, and Red Hat Enterprise Linux all &#8220;just work&#8221; without disabling or configuring Secure Boot."*
(PC Magazine)

[Ubuntu Wiki- SecureBoot]("https://wiki.ubuntu.com/UEFI/SecureBoot")

You did say you were having problems from RST and that the Optane Card is still physically in the slot... That is where I believe your problem is. I think if you remove it, reset your BIOS Firmware setting to default after that... Then try it.

Reasoning... Even if disabled, it is physically in the Bus and a hardware probe may see, it. I believe that is still might be a problem.

Just saying.

---

### Post by cubdukat1968 on 2022-01-20
I was finally able to take the Optane stick out. It turned out that somehow it had gotten corrupted and Windows was trying to salvage it, which was causing everything to hang. Once I did that, everything began working again. 

i wasn&#8217;t able to burn the live DVDs because I spent all my time trying to get the main system back, but I did redo the thumb drives with the latest version of Rufus, so after work I&#8217;ll see if can get them to boot. I haven&#8217;t reset the BIOS yet because the last time I did that, it took three days to get my Thunderbolt 3 card working again, but if it turns out that that&#8217;s the only way, then of course I&#8217;ll do it. 

i am aware that Ubuntu and Fedora claim to work with Secure Boot, but I have never trusted anything concerning that or UEFI in general. I have long been of the opinion that Microsoft is far too linked with it, and they&#8217;ve steered it less towards being an open standard and more towards being a way to lock Linux out of the desktop. 

sorry if it seems like I&#8217;m ranting, but the only time I&#8217;ve ever had problems setting up a dual-boot system was when I had to deal with UEFI.

---

### Post by cubdukat1968 on 2022-01-20
Welp, I'm not sure whether it was tinkering in UEFI or the reformatted thumb drives, but I managed to resolve the issue. 

Apparently my error is not an uncommon one, and a couple of different Google entries pointed to my CSM settings as a possible culprit. It said that it needed to be set to "UEFI and Legacy," and even though that setting was already correct, there were two other settings for booting from things like add-in PCIe devices or network devices, so I set those both to UEFI. I also discovered that that SATA SSD that was going to hold Ubuntu had also been unplugged during my first attempt to remove the Optane stick, so I plugged that back in. While in UEFI, I checked to see what the system was seeing as far as attached drives, since at the beginning of this meshiver, it was seeing the thumb drives as having two UEFI partitions, each the equivalent of the thumb drive's total size, then it also had what I presume was a MBR entry, again the size of the drive. This time around, it was just two entries, a UEFI one and an MBR one. I suspect it was the version of Rufus I used that did that. 

After a quick trip back to Win11 to see that it read the SSD correctly, I attempted to boot into Ubuntu. Success. It even saw the Windows SSD. After that I tried it again with Fedora. That also worked. I have yet to try it with Manjaro, as I thought I saw somewhere that none of the Arch-based distros like Secure boot, but I will do so later. 

But the short version is that Ubuntu does work, and I'm not going to ask too many more questions about what I did to get it to work. That being said, the two main culprits would be the Optane stick and/or the older version of Rufus I used to create the thumb drives. I still have to get another 1TB external SSD to back up Win11, but once that's done, Ubuntu 20.04 LTS is going back on my computer!

---

### Post by MAFoElffen on 2022-01-21
Good to hear that this is solved. Please remember to go to the "Thread Tools"   link on the upper right of the page, to mark this as :Solved" so that other users can find your answer, to help them with their similar issues.

Yes. I had thought it was the Optane still being there "physically". It was enough for Windows to see it. And if Linux had booted, it might have seen it also in the hardware probes. As I remember on most motherboards, with Optane and Intel RST, there is one setting just for Optane itself, but usually 2-3 on RST... Which if your remove the Optane Card, then those setting revert to here they need to be without it. If it is physically still mounted, it is easy to have some it it partially configured.

Sounds like you are well on your way now. Good luck!

---

### Post by cubdukat1968 on 2022-01-21
I'm actually getting ready to install it now. I was going to do it last night, but since I'm installing on a drive other than the Windows drive, I wasn't sure if I should install GRUB to the Windows drive or to the SSD that Ubuntu's going onto. The previous install had GRUB on the Ubuntu drive, so I think I might do that again.

---

### Post by tea for one on 2022-01-21
> **cubdukat1968 said:**
> I'm actually getting ready to install it now. I was going to do it last night, but since I'm installing on a drive other than the Windows drive, I wasn't sure if I should install GRUB to the Windows drive or to the SSD that Ubuntu's going onto. The previous install had GRUB on the Ubuntu drive, so I think I might do that again.

I would isolate, de-activate or physically remove the Windows 11 drive during the Ubuntu installation.
If you only have the target drive accessible, then you will not inadvertently create any difficulty with your Windows OS.

You do not need Grub on the Windows drive  - you can always boot from the Windows Boot Manager.

If need be, you can then update Grub to include Windows - user choice, not essential.

---

### Post by cubdukat1968 on 2022-04-22
Well, it took me a while to get 20.04.3 installed, but I did. The thumb drive cooperated, but now I am in the unhappy position of having to do a clean install. There were too many broken things in it (build-essential, Steam, no thumbnails in the Software Store, etc.), so I figured I'd start again. Unfortunately, the same "out of memory" error came up again. I thought it might be a problem with the USB creation program I was using (Rufus), so I booted into the 20.04.3 install and used the Startup Disk Creator to make the thumb drive. Same thing. It appears to be something within the BIOS, so I am working with ASUS to figure it out. I suspect that I will be stuck with a wonky install; that BIOS update that caused the problem was the last one for my mobo, and it locked Secure Boot to always-on.

---

### Post by antiantagonist on 2022-05-17
Any luck with ASUS?  I'm having a similar issue trying to install Ubuntu & Fedora- Grub is showing an out of memory error.

I was able to get Fedora v32 to install, but it doesn't have the drivers for the network chipset. lol

---

### Post by cubdukat1968 on 2022-05-17
Unfortunately, no, but I was able to get it to work just once and I was able to install Ubuntu 20.04.3 again and then upgrade to 22.04 from there. I wasn't able to figure out why it worked, except that maybe you need to create the thumb drive using the program on the Ubuntu live disc. I found that it also affects DVDs burnt using the 20.04.3 iso, so unfortunately the only advice I can offer is stay away from ASUS. It would seem to be a firmware flaw that they have no intention of fixing because the mobo's so old. I can verify that by attempting to boot the Ubuntu thumb drive on my laptop, which is in a similar position, except that Secure Boot can be disabled. I will keep it enabled, though, to test the problem. 

If the laptop boots Ubuntu, then it's just a firmware flaw with the ASUS mobo. If not, it's in either the kernel or GRUB. I suspect it's the firmware, though; this problem also happens with other distros, and if it was something in the kernel and/or GRUB2, there'd be a lot more posts on it in other places, and there just isn't. Right now, it looks like the solution to this issue is just avoiding ASUS motherboards altogether or at least try to find which vendors lock Secure Boot and which ones don't. 

To be completely fair, I expect this kind of knee-jerk reaction from any motherboard vendor. Linux just isn&#8217;t where the tech world&#8217;s collective head is at. Should be, but it isn&#8217;t. I just have to work within that reality.

---

