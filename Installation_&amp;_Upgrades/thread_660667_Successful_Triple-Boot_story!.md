---
title: "Successful Triple-Boot story!"
date: 2008-01-07
forum: Installation &amp; Upgrades
---

### Post by FireboltFred on 2008-01-07
Yes, you read that correctly: Successful ***Triple-Boot*** story. The three operating systems are Windows XP Pro (32-bit), Windows Vista Ultimate (32-bit - grr, wanted 64), and the brand-new Ubuntu 7.10 a.k.a. "Gutsy Gibbon" (64-bit). Oddly enough, I have found a fair amount of documentation on dualboot scenarios (everyone and their grandmother is dualbooting these days), but not one word about someone trying a tri-boot scenario. I'm sure there are plenty of people who have done it before, i just haven't read about it.

Anyway, moving on. This thread serves mainly to help out 1) People interested in triple-booting their systems, and 2) People interested in dual-booting or fixing their dual-boot scenarios. I also ran into a couple snags here and there, which is to be expected, and maybe by telling my solutions i might help some people.

I would say that the number one thing to remember when trying something like this can be taken from the Hitchhiker's Guide to the Galaxy: **DON'T PANIC**. You are definitely going to run into more than a couple snags, and you need to just stay calm and keep trying. Unless you do completely wipe your hard drive or something. Then you can be sad. I would also suggest planning ahead - this helped me greatly in the end. When i built my computer, i knew that one day i might install 3 operating systems, so i created 4 partitions, one of them being for all my data, and each of the rest for an operating system. As far as sizes go, I would recommend (for the OSs ONLY) 20GB for Windows XP, 25GB for Vista, and max 10GB for Ubuntu.

So on to the actual story. I started with Windows XP. As a rule of thumb, always start by installing the oldest operating system. I created all the partitions i was going to use, leaving Ubuntu's partition unformatted, but formatting Vista's partition once I got into XP. I have installed XP a number of times, and i didn't have any problem installing it this time (sorry i can't help here, but i'm sure there is a solution to your problem somewhere else if you have one). I got XP all set up and working for me, putting my data on the large 4th partition. I wasn't sure if i wanted Vista at the time, so next i actually installed Ubuntu 7.04. This was my first dual-boot experience, but, needless to say, it worked out in the end. The biggest problem I had was with the partitions - with my configuration, i had to select the "Manual" option and use Linux's partition manager to manage the partitions. Ubuntu actually needs two partitions - one is the "swap" partition, so i had to delete the partition i had created before and make two new ones, one with the ext3 file system and one for swap. Ubuntu installed fine, and in the process, it created the GRUB boot loader (Linux's boot manager). When i restarted, i could select from Ubuntu or Windows XP using GRUB.

Time passed. Like, 4 months. Ubuntu released a new version, 7.10, and so i decided to upgrade. However, through a series of unfortunate events, i had deleted my sudoers file and so i couldn't really do anything at all, let alone update the OS. I had also bought a few PC games that were compatible with DirectX 10, so i was interested in getting Vista for that purpose (despite its other inadequacies). I started doing research into different dual-boot scenarios, such as starting with Ubuntu and then installing Vista, as well as the other way around. I found this great site that has a collection of tutorials for all 6 different kinds of dual-boot. It can be found here: [http://apcmag.com/node/5162/]("http://apcmag.com/node/5162/"). The most important thing i got from that tutorial was how to manage the GRUB loader. Basically, use the command
sudo gedit /boot/grub/menu.lst
and change the various options in that file. I'll get back to this later.

So, as of this point in the story, i have Windows XP and a messed-up version of Ubuntu 7.04 installed on my system, and i want to have XP, Vista, and Ubuntu 7.10. From what i've read, the best way to go about this is to start by installing Vista (this turned out to be true). Booted to the install disk and went through the steps. The key moment here was at the partition manager - i needed to make sure i deleted the partition with Ubuntu on it so that it wouldn't interfere and i would have it available for later. Anyway, Vista (surprisingly) installed without a problem, and on reboot i was presented with Vista's boot loader, with that pleasant Coulibri font to greet me. I could choose from Windows Vista and "And older version of Windows." Great job Bill, can't even tell what version it is. Anyway, i eventually got Vista configured to my liking and was ready to install Ubuntu 7.10 64-bit, which i had downloaded and installed to a disk earlier.

I booted to the Ubuntu disk and selected "Install or run Ubuntu," or whatever that first choice is. For some reason, my screen would go blank for a really long time before finally booting up (it doesn't do it for very long anymore). Anyway, i clicked the "Install" icon from the desktop and clicked through the various steps until finally reaching that critical point once again, the partition manager. I selected "Manual" as usual and was presented with my list of partitions. As before, I created two new partitions for Ubuntu, one for the file system with the ext3 type, and one for swap. I went through the rest of the steps and clicked Install. Here is where i hit my only major snag - when going through the install process, it would always give me this error about bad CD-ROM drive or hard drive, and i couldn't figure out why. I finally decided to actually try what it suggested to do and burn the CD image at a lower speed. I restarted and went into XP and burned the disk at 16x instead of 40x. Voila, that did the trick. The next time i tried with the new CD, it worked no problem. So, now Ubuntu is installed as well as its GRUB boot loader. I install all updates for Ubuntu and restart. In GRUB, i'm given the option of the Ubuntu versions, or under "Other operating systems," only the option of "Windows Vista/Longhorn (loader)". I wonder to myself, "What happened to XP?", but i follow rule No. 1 and don't panic. I boot into Ubuntu and configure the GRUB menu.lst file so that the default is "saved" instead of 0, and that the Vista loader has savedefault. There is no mention of XP in the file, so i manually add an entry for it. When i restart and select it, however, it cannot find what i specified. So i try the Vista option, and (Duh...) it goes to Vista's *boot loader*, where i can choose from XP or Vista. All is well.

And so I am currently writing this from Ubuntu 7.10 Gutsy Gibbon. I hope I helped someone out there, or that you were at least in some way entertained by my lengthy story. Definitely check out that link i gave for more information and in-depth step-by-step tutorials for dual-booting. Within some of the tutorials should be a section on modifying your GRUB configuration. Thank you and good night.

---

### Post by stinger30au on 2008-01-07
awesome!!! what a great success story. thanks for the read

---

### Post by Chrisoldinho on 2008-01-07
I suppose in a sense I have a tri-boot.

I have Vista x64 & Ubuntu x86 but I also have Dell Media Direct (runs on XP Embedded) x86. Media Direct can be booted in 2 ways, either via it's own "ON" button or via GRUB.

:)

Chris.

---

