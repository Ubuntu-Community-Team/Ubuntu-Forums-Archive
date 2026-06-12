---
title: "I cannot figure out how to install!"
date: 2017-03-14
forum: Installation &amp; Upgrades
---

### Post by partial2 on 2017-03-14
I am running Ubuntu Studio 16.04 LTS via a USB stick.

It works, but every single time I try to install it I get a box with only question marks in it. I'd take a screenshot of it if I hadn't closed it, but it was only question marks anyway, so. After this message appears, my installation does not seem to do anything at all. I've made multiple attempts at installing and had this same thing happen every time.

I also got a message (for the first time) saying there was a problem with the system, which resulted in this:
[IMG]http://i.imgur.com/ruVf6To.png[/IMG]

I am trying to replace Windows 10 entirely, with Ubuntu. If this is not enough information, please let me know what else to include.

I am* not *tech savvy and I have never touched ubuntu before, so please try to walk me through any answers. Sorry for the trouble.

---

### Post by gdesilva on 2017-03-14
Perhaps some issue with your LiveUSB? I would recreate another LiveUSB and give it a try.

---

### Post by partial2 on 2017-03-15
Thank you for your answer.

I have tried that, and got no different result.

What is the installation page supposed to look like? Is it supposed to have a list of languages on the very left, and just a cancel and continue button? The window is large enough I feel like there should be options....but I don't see anything for a dual boot, nor an option to install over windows. No options, really. Am I missing something?

I am using the x64 direct download version, mounted to a USB with Rufus.

I apologize for the double post but I've tried numerous things and still cannot install this. I'm on my last hopes, here.

I split my C: drive and made a D: drive, using partitions. (Perhaps this isn't the correct wording. I'm really not tech savvy...) Drive D: (The 310 GB volume) is where I want to install Ubuntu Studio. But I'm still having the same errors as before. Nothing is helping me, and I can't find anyone with similar problems!

This is what I see first thing, when trying to install.
[IMG]http://i.imgur.com/rvUU0yv.png[/IMG]

Hitting ok results in a waiting period, which seems indefinite. I have no idea if anything is happening.
 
 
 I am so very frustrated with this. All I want is to not have Win10, and have Ubuntu Studio instead, because it comes with applications I find highly interesting. I really don’t want to keep playing with this via USB forever.

---

### Post by flocculant on 2017-03-15
Boot the usb.

From the menu open gparted.

Screenshot gparted.

Post the result here.

---

### Post by partial2 on 2017-03-15
[IMG]http://i.imgur.com/vGn8cJm.png[/IMG]

So I created 300 or so GB of unallocated space, thinking this would be the fix. To my luck, nothing changed afterwards. Still getting the same internal error. Maybe this clearly isn't the fix, but I figured I would try it.

It makes me even more afraid to try on a new laptop....because I don't think I should struggle so much.

---

### Post by Bucky Ball on 2017-03-16
Can you please start attaching your large pics? 'Go Advanced' or 'Adv Reply' and the paperclip icon. Spare a thought for potential helpers with slow connections and/or vision issues. :)

If you want to get rid of Windows, why are you hanging on to any of those partitions? Boot a live session, launch Gparted, delete all the partitions on the drive (or 'Device> Create partition table' will obliterate everything), then go for it and see what you get.

Have you done any research into EFI and legacy installs? If not and you know nothing about them or don't know which you are using or intend to use, you are not ready to install. That could be at the root of the issue. You need to have some understanding of EFI and legacy modes and how to install in one or the other. :)

PS: I just saw one clue. You have the partition 'sda6' with the label 'Ubuntu'. That is an NTFS filesystem partition and if that was an attempt at an install, impossible dream. Ubuntu will not install on NTFS partitions. You need an EXT4 partition. You will also need a small 2Gb /swap partition. You can create partitions for your install with Gparted in a live sesssion prior to hitting the 'Install' icon. You then use 'Something Else' when you get to the partitioning section of the install and simply give them the default mountpoints.

> **partial2 said:**
>  I don't think I should struggle so much.

Your struggle is probably a result of your newness. You're learning and, in honesty and no offence intended, are on a learning curve with few clues as to what you are doing at this point. In six months time, you'll be teaching us. We all started somewhere and probably took me a day to install the first time. Takes about half an hour now. The first time you installed Windows, if you have, did you jump on a computer, know what you were doing 'by osmosis', install Windows and know what was going on the first time you ever did that? Stick with it. All will (hopefully) become clear. :) 

PPS: Slightly unrelated, but are you sure Ubuntu Studio is right for what you are intending? You are going to get a LOT of audio/video/photography and other apps that you may not want/need/or ever use. UStudio is bloat-worthy if you are not intending to use 70% of the apps that come default with it. You may find it much better to install a lightweight install like Xubuntu or even Xubuntu-core and 'cherry pick' the apps you want/need. They're all available in the official repositories. 

You can even install specific UStudio 'bundles', like ubuntustudio-audio, ubuntustudio-video, ubuntustudio-photography, etc. Unless you are into pro-level video, audio, photography, graphics etc., which very few of us are, this might be a better way to go. Just a thought. :)

---

### Post by partial2 on 2017-03-16
I actually didn't realize I could delete everything from Gparted! Thank you!

I did look into EFI and legacy modes yesterday! It was actually the most helpful article I'd found so far, until this answer.
That partition named Ubuntu was just me trying to fiddle around with partitions in a Windows application. I thought it had to be NTFS, I had heard of ex4 but had no idea how to make one of that kind until using Gparted today!

The first experience I ever had installing Windows myself was with a preload Win8.1 laptop, haha. I just hit next, next, next...


I'm certain Ubuntu Studio is right for me! I actually want to try everything it has to offer, and if I don't like something I can uninstall it, right? (Not that I know how to, but...) I'm definitely not a pro, just an enthusiast!

Thanks for your answer! Very helpful, and I'm actually getting a successful install now! Thanks so much!

I got it installed, but now face "reboot or insert boot media" (or similar, just remembering off the top of my head) at start up. Is this thr time to try a boot repair?

Sorry for the double post.
 
I have managed to install, but I have another problem now. When I'm not booting from my USB stick, I get an error message saying "reboot and select proper boot device or insert boot media in selected boot device and press a key".

I have checked bios, and it is in UEFI mode. I also found a command to run in the terminal, which I did on my USB stick. It said that my Ubuntu was also EFI. I do have a partition that is FAT32 and is EFI, which I set as the boot in the drop-down list of the something else option during installation. It has flags "boot, esp".

I set my EXT4 partition to /.

I am not sure if this uses the coreect terminology. Sorry if it's hard to understand.

I also did install while connected to the internet. I received no errors before, during, or after installing.

I am completely out of ideas now. :/

---

### Post by Bucky Ball on 2017-03-16
If you have Ubuntu installed, why is the USB still in there and why are you booting from it? What happens when you switch off the machine, pull the USB, boot the machine to the BIOS and choose the hard drive you have just installed to? What error message do you get then, if you get one?

If you're installed on the hard drive, forget the USB for now and let us know the outcome of the above. We can take it from there with boot repair. You only have Ubuntu on there now, no Windows?

(As you mention you were online when you installed, I'm presuming you had 'Update during install' and 'Install third-party proprietary drivers' ticked? Please confirm. This is rarely the best way to go. You can update once installed and you may not need any third-party drivers. Those you do need can be found and installed later. Drivers for most things are included right there in the Ubuntu kernel. It is not like Win where you are chasing drivers around and needing to remember 25 digit authentication codes!)

And yes, posting a link to your bootinfo would be helpful, but let's see that error when you boot with no USB and the BIOS set to the Ubuntu drive. (Did you install grub to sda during the 'Something Else' section of the install, as advised?)

---

### Post by partial2 on 2017-03-16
I have only Ubuntu. No Windows.

It is when I boot with no USB that I get the error "reboot and select proper boot device or insert boot media in selected boot device and press a key". If I boot with USB in, it takes me to Try Ubuntu/Install Ubuntu/OEM and such.

I did not have update drivers nor install 3rd party software ticked during installation. Changing the drive to thr one Ubuntu is installed on does not change the boot mentioned before, with the reboot message.

I'm....fairly certain I installed Grub? I was honestly lost when it came to the partitioning there. I created a EFI FAT32 partition, with flags boot and esp, an EXT4 partition, mounted to /, and a swap partition. Maybe I did it wrong. But I'm incredibly lost. All the guides I find seem very advanced...

---

### Post by Bucky Ball on 2017-03-17
Boot Repair. Last blue link in my signature below. You have some options on the second tab (not the one with 'Recommended Repair' on it). One is 'reinstall grub'. Do so and install it to sda. Reboot and see what happens.

Failing this, please provide the bootinfo output. This can be done very easily from a live session of Ubuntu (Try Ubuntu) using Boot Repair. You will find instructions for how to use boot repair on a live session on that link. :)

You can also have a[ look here at 'Fixing a Broken System']("https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"). This also advises Boot Repair but offers a couple of other methods. One is to do it from a terminal which may be quicker, but not as straightforward.

---

### Post by partial2 on 2017-03-17
Thank you so much for continuing to help me despite my complete cluelessness about this! A boot repair worked! Thank you!!

Edit: nevermind....it booted once, never again. Back to the drawing board.

---

### Post by Bucky Ball on 2017-03-17
Ok. That's getting somewhere. What did you do to get it to boot once? Did you use boot repair to write grub to sda or did you do a recommended repair? 

Try this. If you can do what you did and get it to boot once again, when you are at the desktop, open a terminal and paste/type this in (pasting is better as you can't make a typo! :)):

sudo update-grub

You will be asked for your password. When typed in, it will be invisible. This is normal and a security thing. Once you've done that and you are back at the prompt again, close the terminal and reboot. Any different?

Just to confirm, you only have one hard drive in the machine and you do not have the USB in when you are trying to boot to your new install? Make sure the USB is out as it may cause confusion.

No problems with the help. That's what we do here. When I have no ideas left, I'll let you know, but by then someone who does may have jumped in. There are a few grub and boot gurus around here who are waaaay ahead of me. :)

PS: Further thought, but maybe for later. You could simply install Xubuntu (which is more or less what UStudio sits on) or even a Ubuntu minimal install then simply install ubuntustudio-desktop. The end result will be a complete Ubuntu Studio install. Let's keep going with this, though. Probably something we're missing. If you could provide the bootinfo (use boot repair to do that and post the link it gives you) that would help us.

Sounds like its getting close. If it booted once, then you've installed to the hard drive successfully and Ubuntu Studio is there so at least we have confirmed that much. Just a matter of tweaking the boot.

---

### Post by partial2 on 2017-03-17
I ran a recommended repair. Was that the wrong choice, or?

I have only one hard drive, and the USB is not plugged in when I try to boot.

Edit: after I've gotten some sleep I will try the terminal commands!

---

### Post by wildmanne39 on 2017-03-17
*Thread moved to **Installation & Upgrades**.*

---

### Post by Bucky Ball on 2017-03-17
> **partial2 said:**
> I ran a recommended repair. Was that the wrong choice, or?

Hmm. Well, not really. The only problem with that is that it can spit grubs on partitions where they are not required, but no harm. Amongst all that, it should have landed one on sda. 

> **partial2 said:**
> Edit: after I've gotten some sleep I will try the terminal commands!

That's a plan. Perhaps post the link to the bootinfo from Boot Repair when you can also and that will help helpers a lot.

---

### Post by partial2 on 2017-03-17
I ran boot repair again to get a link: [http://paste2.org/AIc0P0JI](http://paste2.org/AIc0P0JI)
I have no clue what it means, ehehhhh.......

I also got this under the link.
```
The boot files of [The OS now in use - Ubuntu 16.04.2 LTS] are far from the start of the disk. Your BIOS may not detect them. You may want to retry after creating a /boot partition (EXT4, >200MB, start of the disk). This can be performed via tools such as gParted. Then select this partition via the [Separate /boot partition:] option of [Boot Repair]. ([https://help.ubuntu.com/community/BootPartition](https://help.ubuntu.com/community/BootPartition))
```

I added an attachment of what gparted looks like.

This also probably a stupid question, but why isn't there a way to just create one huge unallocated partition and install the OS with the "erase disk" (maybe not the correct words, but) option  and have everything be done by default? I feel like I am really complicating everything here. I have no other OS on my disk anymore.... all this partition stuff has me in the dark, ahah.

---

### Post by Bucky Ball on 2017-03-17
It's probably as simple as this, first line of your output:

```
 => No boot loader is installed in the MBR of /dev/sda.
```

Your machine will not boot without one. I have mentioned it on numerous occasions and I'll mention it one more time ... second tab in Boot Repair you can install the grub wherever you like. Install it to sda and reboot. 

[QUOTE=partial2]why isn't there a way to just create one huge unallocated partition and install the OS with the "erase disk" (maybe not the correct words, but) option and have everything be done by default?[/QUOTE]

There is. It is one of the options at install ('Use whole disk' or something). You don't create any partitions. They will be obliterated by the Ubuntu install if you do. Ubuntu will wipe the drive and create its partitions where it wants them and at whatever size it sees fit. You have no control over this process and must be happy with what you are given (although you can resize partitions using a live session and gparted after the fact). 

PS: You only need a 2Gb /swap, incidentally.

---

### Post by partial2 on 2017-03-17
> **Bucky Ball said:**
> It's probably as simple as this, first line of your output:

```
 => No boot loader is installed in the MBR of /dev/sda.
```

Your machine will not boot without one. I have mentioned it on numerous occasions and I'll mention it one more time ... second tab in Boot Repair you can install the grub wherever you like. Install it to sda and reboot. 



There is. It is one of the options at install ('Use whole disk' or something). You don't create any partitions. They will be obliterated by the Ubuntu install if you do. Ubuntu will wipe the drive and create its partitions where it wants them and at whatever size it sees fit. You have no control over this process and must be happy with what you are given (although you can resize partitions using a live session and gparted after the fact). 

PS: You only need a 2Gb /swap, incidentally.
I'm honestly not sure where to find that option in the boot repair stuff. In the second tab of advanced options, I get this only: [IMG]http://imgur.com/rzpbtJxl.png[/IMG]

I cannot change the OS tab (obviously) and the only option I get when I hit the drop down list of separate boot/efi partition is sdb1.

edit: I unticked the separate boot/efi partition box, and selected sda, but got this:
[IMG]http://imgur.com/WNneMSal.png[/IMG]

EDIT: I hit yes on the image above, followed the steps, and got this: [http://paste2.org/Gat0dXNm](http://paste2.org/Gat0dXNm)

At this point would it be worth it to just start over?

---

### Post by Bucky Ball on 2017-03-17
You have a dodgy partition. sda2. See it in your screen shot? It is not free space, but the remnants of an NTFS partition by the looks of it with an exclamation mark (never a good sign). Sorry I missed that. You have this message to go with it:

```
NTFS signature is missing.
Failed to mount '/dev/sda2': Invalid argument
The device '/dev/sda2' doesn't seem to have a valid NTFS.
```

That's a problem. Boot to a live session> Gparted> delete sda2, whatever it is. It has 'bios, grub' next to it, so you tried to install grub there at one point? In any case, grub doesn't go there and that partition should be gone. You can leave as free space and create a partition of your choice there later.

I'm not sure what you did when you began the install, but as you weren't going with a dual-boot, you should have started by booting to a live session, launch gparted, delete all partitions (Device> Create partition table) and start with a clean disk, no partitions. Not sure if you did that or installed around existing partitions, the dodgy sda2 being one of the leftovers. :-k

---

### Post by partial2 on 2017-03-17
I deleted sda2. It's unallocated now.

Do I need to make a new partition now, or should I just try the boot repair again?

(Thank you for putting up with my cluelessness!)

---

### Post by Bucky Ball on 2017-03-17
Boot Repair. Recommended Repair. Reboot and see what happens. Post the link, please.

---

### Post by partial2 on 2017-03-17
I get this when running the recommended repair this time:
[IMG]http://imgur.com/rpdqfQ9l.png[/IMG]

Is this what I should do, or...?

edit: I did it. [http://paste2.org/vHKase5w](http://paste2.org/vHKase5w)
I'll restart now.

edit: rebooted, am still met with the same reboot error as before. :/

If I wipe everything and reinstall, how exactly to I go about that? Do I need to go to gparted and create a new partition table, and leave it unallocated first, or?

---

### Post by Bucky Ball on 2017-03-17
Boot the install media, when you get to the bit where you would choose 'Something Else' choose 'Use whole disk' (or words to that effect). I'll repeat this once more: this option will obliterate anything on the disk.

If that all works, let us know and please mark the thread as solved (Thread Tools at top right or see last link in my signature).

---

### Post by partial2 on 2017-03-17
My USB boots to a blue menu with "GNU/Linux", "System", and other operations. This is the USB I used to "Try Ubuntu". Now I can't reinstall? I cannot delete partitions with gparted either, because they are in use.

Is the USB booting my OS? My terminal shows the username I entered during installation....but, I want to boot the OS /without/ a USB stick. Now it doesn't even look like I can restart.

---

### Post by Bucky Ball on 2017-03-17
If your partitions are 'in use', then you have probably booted the installed system somehow. If you can't boot the USB, how can you be using Gparted unless you are using it from a live system?

If you can't boot the USB, but still are at Gparted with the partitions mounted it means you are probably on the installed OS. If you were running Gparted from a live session some of those partitions wouldn't be mounted. If you right click the / partition and try to unmount, does it give an error message that your OS partition is in use? If so, you are using the hard drive install.

Do another recommended repair as you have killed your EFI/boot partition by the looks of a previous post. Boot Repair may fix this. I don't know.

---

### Post by partial2 on 2017-03-17
No, what I am trying to say is that this specific USB was what I used to install, or try Ubuntu. But now when I have it plugged in, my OS boots. I'm not entirely sure why this is. It doesn't seem to be a live disc, it seems to be my actual operating system. I just don't really understand why. When I don't have a USB in nothing boots at all.

Well, not even a fresh install worked.

I give up. Maybe I need a supported brand like Dell rather than Toshiba. I'm so frustrated and confused with this whole experience, but thank you for your help regardless.

---

### Post by mörgæs on 2017-03-18
There is no indication that the hardware is failing.

I suggest that you try to widen out your attempts. Change stuff that has been constant until now. Have you tried a fresh install of 17.04 (beta)?   

Try a standard Ubuntu 17.04, not Studio to begin with.

---

### Post by Bucky Ball on 2017-03-18
As above, but I would stick with something that has been around for some time, is known to be stable and has longer support: 16.04 LTS. If your hardware came off the shelf within the last six months (very new model machine), then try 17.04. Up to you, naturally. (I did suggest install Ubuntu then install ubuntustudio-desktop in an earlier post.)

Also, I am typing to you from a Toshiba right now. Been using it for ages and no problems. Toshibas, on the whole, work absolutely fine with Ubuntu. On the other hand, some of the newer Dells, unless they have Ubuntu pre-installed, are known to be problematic to install on.

---

### Post by partial2 on 2017-03-18
My laptop is a few years old. Got it in 2013, maybe 2014?

I tried Xubuntu last night. I had no more luck making it bootable than I did with Studio.

It's like I just cannot install grub to sda. The only way I can get into my OS is if A USB stick is plugged in, almost like it's a key or something. Nothing has helped so far, and I feel like I'm working with few resources. It is like my laptop cannot boot from my hard drive at all, like it doesn't even detect anything to boot from.

Like I said, even a fresh install (the default option that writes over everything) didn't change my result at all. I wanted to try dban or something, and then reinstall, but dban won't boot from a usb stick for whatever reason.

I guess I can try an ubuntu iso, not Xubuntu or studio. But I can't really see why that would help. I also always get a message with boot repair about my boot sections not being at the top of my disk or something (just woke up, running off of memory here), even though sda1 in gparted is an EFI partition. (This install was the default install, I didn't make the partitions on my own.) I feel like I'm going crazy with the problems I have had.

---

### Post by Bucky Ball on 2017-03-18
I have a feeling there might be something going screwy with EFI and legacy modes during your install. Are you positively definitely sure you're installing in one or the other? If you have no Windows, there is no real reason for installing in EFI and you may as well use legacy. Less complicated.

The only limitation is you can only have four partitions per physical drive. That isn't an issue as you can have logical drives inside extended partitions. They are like containers. Another story.

Switch off all EFI related stuff in BIOS, boot the install media and choose 'Use Entire Disk' or whatever it's called in Ubuntu now.

---

### Post by partial2 on 2017-03-18
The only Legacy related thing in my bios is switching from UEFI to Legacy. Last time I tried that, Studio still wanted to force install into UEFI mode, but it wouldn't hurt to try again,

---

### Post by partial2 on 2017-03-18
Even weirder results now!

I made a live USB of Ubuntu 16.04.2 LTS. Loading it with UEFI mode set in my bios results in a grub menu. Writing exit results in "Reboot and Srlect proper Boot device
or Insert Boot Media in selected Boot device and press a key".

Running the USB with my bios in CSM mode results only in the error message above.

---

### Post by partial2 on 2017-03-18
I decided simply to use dban to wipe my hard drive, and start over from there.

---

### Post by Bucky Ball on 2017-03-18
You will probably need to write a partition table on it with Gparted in a live session after that. No partitions, just a partition table. DBan tends to obliterate everything on the drive. Everything.

---

### Post by partial2 on 2017-03-18
So create a new partition table, and then install? Do I need to restart after making a partition table, or can I continue right from there?

And, should I go ahead and install with my bios set to csm, or should I use uefi?

---

### Post by partial2 on 2017-03-19
New problem: CSM mode won't boot, only give me errors.

UEFI bios mode takes me to a black screen with grub> _ only.

---

### Post by partial2 on 2017-03-19
Alright! 
I wiped my whole hard drive using dban.

Instead of using Universal USB Installer to remake an install USB, I used Rufus, and this one worked! I successfully installed Ubuntu (Studio again).

However, it still will not boot. I have used the boot repair tool, and here is the report of that: [http://paste.ubuntu.com/24206540/](http://paste.ubuntu.com/24206540/)

I also get the message:
```
You can now reboot your computer.
Please do not forget to make your BIOS boot on sda1/EFI/ubuntu/shimx64.efi file!
```

But in my bios, the most advanced it gets is choosing from UEFI or CSM modes. I am not sure how to set a boot file (forgive my wording).
I am using a Toshiba Satellite C55-B5202, with a bios version of 1.30. Is there a way to set this file from the boot repair usb somehow?

I think if I can only set this as the boot, it will finally work for me.

---

### Post by Bucky Ball on 2017-03-19
* Edit: you ninja-ed me. Posted something else but then your post appeared.

You're in EFI mode. DO NOT CHANGE THAT IN THE BIOS. That has nothing to do with this. It is asking you to set the BIOS to boot from the EFI partition, sda1. _Nothing_ to do with changing your BIOS from EFI to legacy or anything related to that. If you do so you will completely break your system ... again. Read the messages _carefully_. 

Set your first boot device in BIOS to the EFI partition, sda1.

---

### Post by partial2 on 2017-03-19
> **Bucky Ball said:**
> * Edit: you ninja-ed me. Posted something else but then your post appeared.

You're in EFI mode. DO NOT CHANGE THAT IN THE BIOS. That has nothing to do with this. It is asking you to set the BIOS to boot from the EFI partition, sda1. _Nothing_ to do with changing your BIOS from EFI to legacy or anything related to that. If you do so you will completely break your system ... again. Read the messages _carefully_. 

Set your first boot device in BIOS to the EFI partition, sda1.
What I am trying to say is, the only boot-related things I can change are:
the modes (UEFI and CSM)
or
the boot order (HDD, USB, LAN, ODD).

That's literally all I can do. That's why I'm stuck here.

---

### Post by Bucky Ball on 2017-03-19
And I presume you have set the boot order to boot from the HDD? What mode did you install Ubuntu in? UEFI? If so, leave it there. Changing it from whatever Ubuntu was installed in and trying to boot will fail.

Is the bootinfo output in your post 37 the result of booting with boot order set to HDD and mode set to whatever mode you installed Ubuntu in? If not, set the BIOS this way, boot, tell us what happens and rerun boot repair posting only the boot info output (don't run the recommended repair again, please).

---

### Post by partial2 on 2017-03-19
I did set the boot order to boot from HDD right after I finished installing from my USB stick. I also did install Ubuntu in UEFI mode, because I couldn't even boot from my USB to install with CSM mode. The report in 37 is the way it was with no changes in BIOS (with the exception of putting HDD on top of the boot list before running boot repair).

---

### Post by Bucky Ball on 2017-03-19
You still have this in the first line of that output:

```
 => No boot loader is installed in the MBR of /dev/sda.
```

If you run Boot Repair> Advanced, can you 'Place the boot flag on: sda1' and then see if you can place grub on sda, not sda1 or a partition. If not, go with the other change and reboot with no USBs in the machine.

---

### Post by ubfan1 on 2017-03-19
I am a bit confused by this thread.
In a UEFI mode install, there is no bootloader put into the MBR, just the bootloader files in the EFI partition.   The nvram entries will pick out which one to boot.
A fallback bootloader may be put into /EFI/Boot/bootx64.efi, which may be invoked upon the failure of the first nvram entry, and before the second nvram entry is tried (like trying to boot grubx64 with secure boot enabled, or some vendor specific tweak that only boots files named bootmgfw.efi).  This "fallback" mechanism is used for removable media, like the install media.

For legacy mode, on a gpt disk, you will need a 1-2M partition flagged grub-bios (no filesystem needed, so Windows won't like it).  I've seen one of those, even though I also see an EFI partition which looks like it was set up correctly, although way too big (500M the usual max, but I see 5G).  Now maybe you wanted more FAT32 file space, so that would work, but I'd recommend a separate partition, and not mix data into the EFI partition.  Now there's nothing wrong with setting up both both boot partitions, but only one would be needed.  If you have a fresh msdos partitioned disk, I would set up an EFI partition for future use on an UEFI machine, but your disk is gpt.  Setting up both certainly will make it easier to switch UEFI to legacy.

I see no mention of what machine you have, so even after doing everything correctly for a UEFI boot, it may not work because the vendor did some non-UEFI modifications to the boot process.  This is why a legacy setup  is easier (no vendor stuff involved).  UEFI is the future, and what I'd generally recommend, but there seems to be some difficulty here before we even get to the hard part (vendor specific modifications).  I have a UEFI machine, but I default to running legacy, because creating USB install media is important to me, and there are still serious problem with doing that in UEFI mode.

---

