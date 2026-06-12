---
title: "New install not found"
date: 2020-05-11
forum: Installation &amp; Upgrades
---

### Post by triplemaya on 2020-05-11
Downloaded Ubuntu Mate 20.
Install on blank disk. No problem.
Install on partition on disk I actually want to use with /home partition. O/S  not found. Did the whole thing again just to make sure. No deal. 
In both cases the install insists on a small partition for grub which is therefore present on both disks.
It seems I am doing the same as I have done for years! Just installing a new version of the O/S on the / partition.
Please tell me what info to post so someone can help me with this.
Just to be clear the error message is please install an operating system, so posting fstab is obviously not going to help.
Screenshots of gparted for both drives uploaded. First one works, second one no. 
I do not understand why they are so different. I follow the instructions on the install page and get very different results when I try to use the existing /home partition.
Thanks

---

### Post by dino99 on 2020-05-11
Seems you have two disks; and installed Mate on one. I suppose there is already an other os on the other disk, with its own grub, which might be the master one; so needs to reinstall it for discovering the new Mate. If this is not the case, then give the details to help us understanding.

---

### Post by yancek on 2020-05-11
You need to provide more information if you want help.
You refer to 2 disks but make no mention of what they are used for or whether there is any other OS currently installed and, if so what that might be?
You need to indicate whether you are using UEFI/GPT or Legacy install.  If you have any other OS, which is it?

---

### Post by triplemaya on 2020-05-11
Hi. Thank you for your replies.
Deep apologies for lack of info. (I start getting into despair sometimes which is hugely unhelpful!)
I am using the two disks alternately in the same machine.
All very simple - supposedly!
Ordinary legacy boot.
No other os. Just trying to install ubuntu mate.
First image works, second does not.

---

### Post by triplemaya on 2020-05-11
I notice that the working disk when looked at with gparted when operating shows the first partition as boot/efi, but the laptop BIOS is set to legacy boot.
And the non working disk does not work when the pc is set to legacy or uefi - with or without CSM or whateer it is.

So it seems that for some reason the standard install produces a uefi boot, which works, on a legacy bios. 
And
That the install where I take over and ask the software to install the O'S to the first partion, and giving it the grub partition it wants, decides on legacy boot, which does not work no matter what.
Is that a correct reading? and if so WHY? WHY? WHY? WHY? WHY? WHY? WHY? !!!!!!!

wHAT IS going on?!

---

### Post by CelticWarrior on 2020-05-11
How it boots is how it installs. This is the first "rule" you need to understand.

Secondly, and at cursory glance, you have one UEFI installation in a MBR partitioned drive (should be GPT) because of the extended partition created along with the EFI partition -and- you have a Legacy installation in another GPT partitioned drive (should be MBR) because of the "bios_grub" partition. This is a truly upsidedown world only possible because Ubuntu and other Linux distros aren't as strict as Windows with the correlation between partitioning types and installation modes.

All of this stems from ignoring the situations/scenarios described above.

Please read [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) to understand UEFI, its requirements and how to proceed in case you want dual or multi-boot with Ubuntu/Windows, different 'Buntus or any other OSes combination.

Also please understand that any UEFI PC - anything from the last ~10 years - wants OSes in UEFI mode.
And, again, how it boots is how it installs. For better results disable Legacy/CSM as this assures the installation media will boot in the the proper UEFI mode. Please pay special attention when making the installation media: Tool like Rufus need GPT/UEFI settings before "burning", the default "MBR-UEFI/BIOS" actually boots in BIOS/Legacy mode only. Prefer simpler and "fool-proof" tools like Balena Etcher or any other tool available for Linux.
Prepare the installation drive accordingly: Make sure all are GPT before starting the installation (Gparted can be easily used for that). This will avoid the situation you're in now.

---

### Post by triplemaya on 2020-05-11
Hi Celtic Warrior
Thanks for your post. I am reading the link.
To be clear:
I am NOT trying to use these disks at the same time. 
These are two separate attempts to install Ubuntu 20 on a bare machine.
Both done with the same install medium, one at a time. 
So the problem I am having with understanding all this is why the results are so different.
This seems to me to go to the core of the problem!

---

### Post by CelticWarrior on 2020-05-11
The reason why the results are different should be easy to understand provided the information I gave previously has been properly digested. And that's nothing but the very basic knowledge required to safely install OSes, Ubuntu, other Linux and even Windows.

> I am NOT trying to use these disks at the same time. 
These are two separate attempts to install Ubuntu 20 on a bare machine.

I'm perfectly aware of that and everything I wrote accounts for that as well. However, it must be said that although I understand your project its purpose eludes me by a mile, at least:

Why do you think you need two installations of the exact same Ubuntu release/version?
If it's for two separate work instances then perhaps a single installation with two (or more) users would be enough.

So, regardless of my personal considerations about the project, it's doable nonetheless. But you need to get out of that "drives mindset" because that's not how UEFI works. Only one EFI partition - in the drive with the first boot priority - is needed no matter how many OSes there are in total and no matter the physical location of their system partitions. Of course, you can have one EFI partition per drive but that is usually just additional complication for a meager gain which is the possibility of booting at least the second (or third or ...) OS directly from the second drive in case the first one fails for some reason. Doing that requires additional steps.

Please take your time to digest the information, think about what you want to do and then come back here with a detailed description of the project matching your final decision so I can help you with that.

---

### Post by triplemaya on 2020-05-12
Very grateful for your time.

The intent is to wind up with one working drive, with a separate home partition - which is already on the disk. (I set aside half an hour for this task which has now grown to a complexity threatening my sanity! I remember this being totally straightforward last time I did it. One of the reasons I grew to love linux.)

The only reason for the second attempt on the bare drive was to see if the system would in fact work with a bare install. And it did. And it is the standard install software that produced the first of the messes you describe - "one UEFI installation in a MBR partitioned drive (should be GPT) because of the extended partition created along with the EFI partition"

The first thing I glean from your information is that I ought to be aiming to use efi at all times. Point taken.
So it seems I need to setup the slash partition as gpt? But I don't see any way to do that, either in gparted or during the install. 
The two pictures of the different boots on the link you gave are extremely helpful. Nice simple info. 
But there is no nice simple blue list of efi and non efi options on this computer, sadly. I like that. 

So I have set the machine to boot only efi.
I set up a 1gb partition for the efi because it would not work with 1mb - 33mb used which seems a lot when the drive done by the standard install has a partiiont of 512 mib and uses just 1.02mib. 

Error messages:
System BootOrder not found 
Initializing defaults

But then it worked. Thank you again.

But it is giving the error message on each boot
System BootOrder not found 
Initializing defaults
How can I fix this? When I googled it I get information about setting up secure boot. But I seem to remember all kinds of horror stories about the bios getting locked if one does this. I seem to remember that the general horror of dealing with that stuff when it goes wrong are the main reason I would have wanted to use legacy. 

The one thing I am not clear about is the gpt partitioning. I have found instructions that require to erase teh entire disk in order to use a new partitioning table with gpt. But as this requires formatting the entire disk I assume that using an existing home partition is clearly not possible. Is this the only proper way to do it? I am very curious to know how and winy the current working installation is working if it should be gpt and it is not. Should I really start again having turned the whole disk into gpt?

BTW I now understand you when you say that "How it boots is how it installs. This is the first "rule" you need to understand." But the install medium booted legacy but then installed the efi on the bare drive. This is why I could not get my head around why the two different outcomes happened from doing the same procedure. Still don't!

---

### Post by yancek on 2020-05-12
The simplest and safest way to do two separate installs on 2 separate drives for an inexperienced user is to first physically dis-connect the 2nd hard drive (or disable it in the BIOS if possible) and install to the first drive.
Then reboot to test that the installation was successful.  If it was, shut down the computer and remove the first drive and install the second drive, boot the install media and install to the second drive, reboot to test.  This isn't the easiest but it is the safest but can be difficult particularly if you are using a laptop.

I'm not really clear on your current status.  Do you have one functioning install of Ubuntu and if so, what is it?  UEFI/GPT or Legacy install?

---

### Post by triplemaya on 2020-05-12
Hi yancek

I am only using one drive. The second drive was simply to see if the install medium would in fact work. 

I now have a working install but on each boot I get the error message:

System BootOrder not found
Initializing defaults

I am keen to know how to fix this.

The install is efi, but I don't think it is gpt, which concerns me as my previous advisor said it should be. The third image I have uploaded is the gparted of this disk.  [ATTACH=CONFIG]285838[/ATTACH]

---

